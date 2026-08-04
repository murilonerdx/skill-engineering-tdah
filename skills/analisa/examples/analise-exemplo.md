# Exemplo de análise (formato e profundidade alvo)

Doc analisada (resumo fictício): "Design: notificação de pagamento via chamada HTTP síncrona do serviço de Pagamentos para o serviço de Notificações, logo após confirmar a transação. Retry 3x se falhar."

---

# 🔬 Análise: Design de Notificação de Pagamento — 2026-08-03

## 📌 Resumo em 3 linhas
Propõe notificar o cliente chamando o serviço de Notificações por HTTP síncrono, no mesmo fluxo da confirmação de pagamento, com 3 retries. Resolve "avisar o cliente", mas acopla o caminho crítico de pagamento a um serviço secundário.

## ⚖️ Trade-offs
| Decisão | Ganha | Perde | Comentário |
|---|---|---|---|
| HTTP síncrono no fluxo de pagamento | Simplicidade, notificação imediata | Pagamento fica refém da disponibilidade de Notificações | Inverte a criticidade: o secundário derruba o crítico |
| Retry 3x inline | Recupera falha transitória | Aumenta latência do pagamento; retry pode duplicar notificação | Sem idempotência, cliente recebe aviso repetido |

## 🐞 Problemas & riscos
- 🔴 **Acoplamento de disponibilidade** (seção "fluxo") — se Notificações está fora/lento, o pagamento trava ou falha. O caminho de dinheiro não pode depender de aviso. **Lacuna:** a doc não fala de timeout nem circuit breaker.
- 🔴 **Sem idempotência na notificação** (seção "retry") — retry reenvia; cliente recebe o mesmo push/email várias vezes.
- 🟡 **Latência no caminho crítico** — 3 retries síncronos podem somar segundos ao pagamento.
- 🟡 **Falha parcial não tratada** — se pagamento confirma mas as 3 tentativas de notificar falham, a notificação se perde silenciosamente (**lacuna**: nada sobre isso).

## 🛠️ Soluções propostas
- Acoplamento → **desacoplar via evento**: Pagamentos publica `PaymentConfirmed` (com outbox); Notificações consome de forma assíncrona. Pagamento não depende mais da disponibilidade de Notificações. Trade-off: notificação passa a ser eventual (ms a s), aceitável aqui.
- Idempotência → notificação carrega `paymentId`; consumidor deduplica por ele. Trade-off: precisa store de dedup com TTL.
- Latência → sai do caminho crítico ao virar assíncrono; resolve junto com o item 1.
- Falha silenciosa → com evento + consumidor, retry/DLQ ficam do lado de Notificações, com métrica de lag.

## 🔁 Alternativas a considerar
- **Evento assíncrono (recomendado)** — desacopla, resiliente; custo: eventual + infra de mensageria (já existe).
- **HTTP síncrono só com timeout curto + fire-and-forget** — mais simples que evento, mas ainda perde notificação em falha e não dá rastreabilidade. Só se mensageria não estivesse disponível.

## 💡 Ângulos de case (nível staff)
- "Criticidade invertida": por que o caminho de dinheiro nunca deve depender sincronicamente de um serviço secundário.
- Outbox + consumidor idempotente como padrão de notificação confiável.
- Como medir sucesso: taxa de notificação entregue vs pagamentos, e lag do consumidor.

## 🎯 Veredito
**Repensar.** Gap #1: desacoplar a notificação do caminho de pagamento (evento assíncrono) — resolve acoplamento, latência e perda silenciosa de uma vez.
