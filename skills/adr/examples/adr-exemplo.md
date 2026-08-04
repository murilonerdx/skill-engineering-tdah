# ADR-007: Publicar eventos de pagamento via Outbox Pattern

- **Status:** aceito
- **Data:** 2026-08-03
- **Decisores:** time de Pagamentos
- **Consultados / informados:** Plataforma, SRE

## Contexto e problema
O serviço de pagamentos grava a transação no banco (Postgres) e precisa publicar um evento `PaymentConfirmed` no Kafka para o ledger, antifraude e notificações.

Hoje publicamos direto no Kafka logo após o commit. Isso cria uma janela de inconsistência:
- Se o `kafka.send` falha após o commit → transação existe, evento nunca sai (ledger fica dessincronizado).
- Se o processo cai entre commit e send → mesmo problema.

Requisitos:
- **Nenhum evento de pagamento pode ser perdido** (requisito — impacta ledger e conciliação regulatória).
- Consumidores já toleram duplicação (idempotentes) → entrega **at-least-once** é aceitável.
- Volume atual ~300 tx/s, pico ~1200 tx/s.

## Direcionadores da decisão
- Atomicidade entre "gravar transação" e "registrar intenção de publicar".
- Não introduzir dependência nova de infraestrutura pesada.
- Operável pelo time (já usamos Postgres + Kafka + Debezium em outro fluxo).

## Opções consideradas
### Opção A — Publicar direto no Kafka após commit (atual)
- Resumo: manter como está.
- ✅ Prós: simples, sem componente novo.
- ❌ Contras: perde evento em falha entre commit e send. **Fere o requisito de não perder evento.**

### Opção B — Outbox Pattern (tabela outbox + relay)
- Resumo: grava o evento numa tabela `outbox` **na mesma transação** da transação de pagamento; um relay lê a outbox e publica no Kafka, marcando como enviado.
- ✅ Prós: atomicidade garantida (mesma transação); at-least-once natural; usa infra que já temos.
- ❌ Contras: latência extra até o relay publicar; precisa de dedup no consumidor (já temos); tabela outbox cresce (precisa limpeza).

### Opção C — Transação distribuída (2PC entre banco e broker)
- Resumo: coordenar commit de banco e broker.
- ✅ Prós: consistência forte.
- ❌ Contras: Kafka não suporta bem XA; complexidade alta; acopla e reduz disponibilidade. Descartada.

## Decisão
Escolhemos a **Opção B — Outbox Pattern**, com relay via Debezium (CDC) lendo a tabela `outbox`.
Vence porque garante atomicidade sem 2PC, reaproveita Debezium+Kafka que o time já opera, e a duplicação que ela introduz já é tolerada pelos consumidores. A Opção A fere o requisito central; a C custa complexidade e disponibilidade demais.

## Consequências
- ✅ **Positivas:** evento de pagamento nunca se perde; desacopla publicação do caminho de request; relay reprocessa após queda.
- ⚠️ **Negativas / custos:** +latência (ms a poucos s) até publicação; tabela `outbox` precisa job de limpeza; consumidores obrigatoriamente idempotentes.
- 🔭 **Impacto:** conciliação com o ledger fica confiável; SRE ganha um relay a monitorar.

## Trade-offs, riscos e mitigação
- Risco: outbox cresce e degrada o banco → mitigação: job de purge + índice em `status, created_at`; alarme de tamanho.
- Risco: relay atrasado esconde problema → monitorar **lag** da outbox (idade do evento mais antigo não publicado); alarmar acima de N segundos.

## Quando revisitar
Se o volume passar de ~5k tx/s (o relay/tabela pode virar gargalo) ou se algum consumidor deixar de ser idempotente.

## Referências
- PR #482 (implementação da tabela outbox)
- Benchmark de lag do relay em pico: docs/benchmarks/outbox-lag.md
