# Exemplo de review (formato e profundidade alvo)

Diff fictício: endpoint que debita saldo e publica evento de pagamento.

```java
@PostMapping("/pay")
public ResponseEntity<Void> pay(@RequestBody PayRequest req) {
    Account acc = repo.findById(req.getAccountId());
    if (acc.getBalance() >= req.getAmount()) {
        acc.setBalance(acc.getBalance() - req.getAmount());
        repo.save(acc);
        kafka.send("payments", new PaymentEvent(req));
    }
    log.info("pay request: " + req);
    return ResponseEntity.ok().build();
}
```

---

# 🔍 Review PR — feature/pay-endpoint

## Veredito: não mergear ❌
Risco de saldo negativo, cobrança duplicada, evento perdido e vazamento de dado. Vários bloqueadores.

## 🔴 Bloqueadores (resolver antes de mergear)
- **[PayController:4] `balance` é `double`** — dinheiro em ponto flutuante acumula erro de arredondamento. Fix: `BigDecimal` ou `long` de centavos em todo o fluxo.
- **[PayController:4-7] check-then-act não atômico** — duas requisições concorrentes leem o mesmo saldo, ambas passam no `if`, ambas debitam → saldo negativo. Fix: update atômico condicional (`UPDATE ... SET balance = balance - :amt WHERE id = :id AND balance >= :amt`) e checar linhas afetadas; ou lock otimista com `@Version`.
- **[PayController] sem idempotência** — retry do cliente/gateway debita e publica de novo. Fix: exigir `Idempotency-Key`, persistir e checar antes de executar.
- **[PayController:6-7] salvou e publicou sem outbox** — se o `kafka.send` falhar após o `save`, dinheiro debitado sem evento (ledger/notificação perdidos); se a transação der rollback depois do send, evento sem débito. Fix: outbox pattern (grava evento na mesma transação, publica depois).
- **[PayController:9] log vazando dado sensível** — `"pay request: " + req` despeja o corpo inteiro (possível PAN/token/valor/conta). Fix: log estruturado com campos mascarados.

## 🟡 Deveria arrumar
- **[PayController:3] `findById` sem tratar ausência** — se a conta não existe, `acc` nulo → NPE. Fix: `orElseThrow` com erro 404 claro.
- **[PayController] sem timeout no `kafka.send`** — pode pendurar a thread. Defina timeout e trate falha.
- **Falta validação** de `amount` (negativo/zero permite débito/estorno indevido).

## 🔵 Nits
- Retornar um id de transação no corpo ajuda o cliente a rastrear/idempotência.

## ✅ Checklist (resumo)
dinheiro-tipo ❌ · idempotência ❌ · concorrência ❌ · falha-parcial ❌ · segurança-log ❌ · validação ⚠️ · testes ❌ (nenhum) · observabilidade ⚠️
