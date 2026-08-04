# ADR-<NNN>: <título curto e afirmativo da decisão>

- **Status:** proposto | aceito | descartado | substituído por [ADR-XXX](ADR-XXX.md) | obsoleto
- **Data:** <AAAA-MM-DD>
- **Decisores:** <quem decidiu>
- **Consultados / informados:** <quem opinou / precisa saber> (opcional)

## Contexto e problema
Qual força/problema motivou esta decisão? O que está em jogo?
Restrições e requisitos que limitam o espaço de solução (escala esperada, SLA/latência, prazo, orçamento, regulação, segurança, time/skills).
Deixe explícito o que é **requisito** vs **preferência**.

## Direcionadores da decisão (critérios)
- <critério 1 — ex: não duplicar cobrança em falha>
- <critério 2 — ex: latência p99 < X>
- <critério 3 — ex: operável pelo time atual>

## Opções consideradas
### Opção A — <nome>
- Resumo: ...
- ✅ Prós: ...
- ❌ Contras: ...

### Opção B — <nome>
- Resumo: ...
- ✅ Prós: ...
- ❌ Contras: ...

### Opção C — <nome> (se houver)
...

## Decisão
Escolhemos a **Opção X**.
Justificativa: por que ela vence contra os critérios acima — e por que as outras não.

## Consequências
- ✅ **Positivas:** o que melhora / passa a ser possível.
- ⚠️ **Negativas / custos:** o que piora, o que aceitamos perder, dívida assumida.
- 🔭 **Impacto:** operação, custo, segurança, confiabilidade, time.

## Trade-offs, riscos e mitigação
- Risco: ... → mitigação: ...
- O que monitorar em produção pra saber se a decisão foi boa.

## Quando revisitar
A condição que invalidaria esta decisão (ex: "se o volume passar de N/s" ou "se X mudar").

## Referências
Links: PRs, benchmarks, docs, ADRs relacionados.
