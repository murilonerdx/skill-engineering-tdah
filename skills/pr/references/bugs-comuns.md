# Catálogo de bugs sutis — fintech / backend

Padrões que passam em review superficial e explodem em produção. Procure ativamente por cada um.

## Dinheiro
- **Float em dinheiro** — `double saldo` acumula erro (`0.1 + 0.2 != 0.3`). Fix: `BigDecimal` ou `long` de centavos.
- **Arredondamento indefinido** — `setScale` sem `RoundingMode`, ou modos diferentes em pontos diferentes. Cria divergência de centavos que auditoria pega.
- **Sinal trocado** — débito/crédito com sinal invertido em um branch. Teste com valor negativo e estorno.
- **Conversão de moeda com precisão perdida** — taxa aplicada e depois truncada cedo demais.

## Idempotência & duplicação
- **Idempotency key checada depois de executar** — janela entre executar e gravar a key permite duplicar em retry concorrente.
- **Key só em memória** — perde no restart; retry após deploy duplica.
- **Retry do gateway não considerado** — o provedor reenvia webhook; sem dedup, credita 2x.
- **Consumer sem dedup** — Kafka/SQS entregam at-least-once; reprocessar mensagem duplica efeito.

## Concorrência
- **Check-then-act não atômico** — `if (saldo >= valor) { debita(); }` com duas queries: duas requisições passam no `if` antes de qualquer débito → saldo negativo.
- **Lost update** — dois `read-modify-write` sem version/lock sobrescrevem um ao outro.
- **Faltou `@Transactional`** ou propagação errada — parte grava, parte não.
- **Lock só num nó** — `synchronized`/lock local não protege em ambiente com N instâncias; precisa lock distribuído ou constraint no banco.

## Falha parcial
- **Debitou e não creditou** — transferência em duas chamadas sem compensação/saga; falha no meio deixa dinheiro sumido.
- **Salvou no banco mas não publicou evento** — sem outbox, a falha entre commit e publish perde o evento (ex: notificação, ledger).
- **Efeito colateral antes do commit** — envia email/cobra e depois a transação faz rollback.

## Resiliência
- **Sem timeout** — chamada externa pendura a thread; pool esgota; serviço inteiro cai por causa de 1 dependência lenta.
- **Retry em erro não-retriável** — repete um `400`/validação eternamente, ou retrica cobrança que já passou.
- **Retry sem idempotência** — amplifica duplicação.

## Segurança
- **Log vazando dado** — `log.info("req: " + request)` despeja PAN/token/CPF. Grave em log estruturado com campos mascarados.
- **Authz ausente** — endpoint confia no `userId` do corpo/cliente; permite acessar conta alheia (IDOR).
- **Segredo hardcoded** — chave/token commitado.

## Dados
- **Migração quebra deploy rolling** — coluna renomeada/removida derruba a versão antiga ainda em execução. Use expand/contract.
- **Query nova sem índice** — table scan em tabela de milhões; lento e trava.
- **N+1** — laço que consulta o banco por item.
- **Timezone** — mistura `LocalDateTime` e `Instant`; corte de dia/juros no fuso errado.

## Como usar este catálogo
Pra cada arquivo do diff que toca dinheiro, concorrência ou dependência externa, percorra a seção correspondente e pergunte "esse padrão pode estar aqui?". Achou → vira bloqueador com fix.
