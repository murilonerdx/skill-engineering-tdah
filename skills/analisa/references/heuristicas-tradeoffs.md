# Heurísticas de trade-off por tipo de doc

Identifique o tipo da doc e aplique a seção correspondente. Uma doc pode ser mais de um tipo.

## Tipo: Design de API (REST/gRPC/contrato)
- **Versionamento:** como evolui sem quebrar cliente? Campo novo é opcional? Breaking change tem plano?
- **Idempotência:** operações de escrita aceitam idempotency key? POST que cria recurso é seguro em retry?
- **Contrato de erro:** erros são tipados e estáveis? Cliente distingue retriável de fatal?
- **Paginação/limites:** listagem é paginada? Há limite pra evitar payload gigante?
- **Acoplamento:** o contrato vaza detalhe interno (schema do banco) pro cliente?
- ⚖️ Trade-off comum: flexibilidade (campos genéricos) vs clareza/validação (contrato estrito). Em fintech, prefira estrito.

## Tipo: Modelo de dados / schema
- **Dinheiro:** tipo correto (`decimal`/inteiro de centavos, nunca float)? Moeda junto do valor?
- **Integridade:** constraints (FK, unique, not null) no banco, não só na aplicação?
- **Migração:** compatível com deploy sem downtime (expand/contract)? Reversível?
- **Cardinalidade & índice:** queries do caminho quente têm índice? Tabela cresce sem bound?
- **Histórico/auditoria:** operação financeira é append-only/imutável ou dá pra sobrescrever?
- ⚖️ Trade-off comum: normalização (integridade) vs desnormalização (leitura rápida). Decida por caso de uso.

## Tipo: Integração / mensageria (Kafka, fila, webhook)
- **Garantia de entrega:** at-least-once (precisa idempotência) / at-most-once (pode perder) / exactly-once (caro/ilusório)?
- **Ordenação:** precisa ordem? Como garante (partição por chave)?
- **Dedup:** consumidor trata duplicata? Janela de dedup?
- **Outbox:** publica evento na mesma transação do estado, ou tem janela de perda?
- **Poison message / DLQ:** mensagem que sempre falha vai pra onde?
- **Backpressure:** consumidor lento derruba o produtor ou acumula?
- ⚖️ Trade-off comum: acoplamento síncrono (simples, mas frágil) vs assíncrono (resiliente, mas complexo e eventual).

## Tipo: Arquitetura de serviço (novo serviço, split, padrão)
- **Fronteira:** o corte de responsabilidade faz sentido? Vai gerar chatter (muitas chamadas entre serviços)?
- **Consistência:** transação que antes era local virou distribuída? Como lida (saga/outbox)?
- **Dono do dado:** cada dado tem um dono claro, ou dois serviços escrevem o mesmo?
- **Falha em cascata:** dependência síncrona nova propaga queda? Tem isolamento (timeout, breaker, bulkhead)?
- **Custo operacional:** monólito modular resolveria com menos complexidade? (2026: recuo do "microserviço por default")
- ⚖️ Trade-off comum: autonomia/escala independente (microserviço) vs simplicidade operacional (monólito modular). Justifique o distribuído, não assuma.

## Tipo: Caching / performance
- **Invalidação:** como e quando o cache invalida? Stale aceitável por quanto tempo?
- **Consistência:** dado financeiro pode servir stale? (geralmente não pra saldo)
- **Stampede:** expiração simultânea derruba o backend? Tem lock/jitter?
- ⚖️ Trade-off comum: latência (cache agressivo) vs correção (dado fresco). Em saldo/valor, correção ganha.

## Sinais de alerta transversais (qualquer tipo)
- Doc silencia sobre falha, retry ou concorrência → provável lacuna grave.
- "Vamos garantir consistência" sem dizer **como** → hand-waving.
- Nenhum número (volume, latência, tamanho) → decisão sem base.
- Nenhuma alternativa considerada → decisão não amadurecida.
