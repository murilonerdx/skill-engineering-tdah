# Checklist de review — fintech / pagamentos

Aplique cada item que se encaixa no diff. Marque ✅ ok · ⚠️ dúvida · ❌ problema · n/a.

## 1. Correção
- [ ] Lógica faz o que a descrição do PR promete.
- [ ] Casos-limite: `null`, vazio, zero, negativo, valor máximo, coleção de 1 item.
- [ ] Off-by-one em loops/paginação/ranges.
- [ ] Comparação de valores monetários **não usa `float`/`double`** (usar `BigDecimal`/inteiro de centavos).
- [ ] Arredondamento de dinheiro definido e consistente (modo e escala).
- [ ] Timezone/`Instant` correto em datas; sem `LocalDateTime` ambíguo em evento financeiro.
- [ ] Enum/switch cobre todos os casos + default explícito.

## 2. Idempotência & duplicação (crítico em pagamento)
- [ ] Operação que move dinheiro é **idempotente** (mesma requisição 2x = 1 efeito).
- [ ] Idempotency key persistida e checada **antes** de executar, não depois.
- [ ] Retry (do cliente, do gateway, do broker) não duplica cobrança/estorno.
- [ ] Consumo de mensagem trata **entrega duplicada** (at-least-once é o padrão).
- [ ] Dedup tem janela/TTL definido e sobrevive a restart.

## 3. Concorrência & consistência
- [ ] Race em saldo/estoque: usa lock otimista (version) ou pessimista, ou update atômico condicional.
- [ ] `check-then-act` (ex: "se saldo >= X, debita") é atômico, não duas queries.
- [ ] Transação cobre o conjunto certo; nada de commit parcial deixando estado inconsistente.
- [ ] Sem chamada de rede/externa dentro de transação de banco longa.
- [ ] Ordem de aquisição de locks consistente (evita deadlock).

## 4. Confiabilidade & falha
- [ ] Timeout explícito em toda chamada externa (HTTP, DB, broker).
- [ ] Retry com backoff + jitter; teto de tentativas; só em erro retriável.
- [ ] Circuit breaker / fallback onde a dependência pode cair.
- [ ] Falha parcial tratada (ex: debitou mas não creditou → compensação/saga).
- [ ] Outbox/inbox ou 2-phase evita "salvou no banco mas não publicou evento".
- [ ] Degradação graciosa: o que acontece se a dependência X estiver fora?

## 5. Segurança
- [ ] Nenhum dado sensível em log: PAN, CVV, token, senha, chave, CPF/documento completo.
- [ ] PII/segredo mascarado ou fora do log.
- [ ] Autorização checada no servidor (não confia no cliente); usuário só acessa o que é dele.
- [ ] Validação/sanitização de toda entrada externa.
- [ ] Sem SQL/command injection (query parametrizada).
- [ ] Segredo não hardcoded; vem de vault/env.
- [ ] Valores de entrada com limite (evita overflow/DoS por payload gigante).

## 6. Dados & migração
- [ ] Migração de schema é reversível ou tem plano de rollback.
- [ ] Migração compatível com deploy sem downtime (expand/contract; não quebra versão antiga em execução).
- [ ] Índice pra query nova em tabela grande.
- [ ] Sem `SELECT *` em caminho quente; sem N+1.
- [ ] Nullable/constraint corretos; default não corrompe linhas existentes.

## 7. Testes
- [ ] Caminho feliz + erro + limite.
- [ ] Teste de **idempotência** (executa 2x, verifica 1 efeito).
- [ ] Teste de **concorrência** onde há race (2 threads no mesmo saldo).
- [ ] Teste de falha de dependência (timeout, exceção, resposta inválida).
- [ ] Asserções sobre valor monetário exato, não aproximado.
- [ ] Sem teste flaky (sleep fixo, dependência de relógio/ordem).

## 8. Observabilidade
- [ ] Log estruturado com correlação (traceId/requestId) no caminho crítico.
- [ ] Métrica de negócio/erro no ponto que importa (taxa de falha, latência, valor processado).
- [ ] Erro rastreável até a causa (não engole exceção; não `catch` vazio).
- [ ] Alarme/limite pensado pra falha silenciosa (ex: fila de estorno crescendo).

## 9. Qualidade & manutenção
- [ ] Nomes claros; sem comentário que explica código confuso que devia ser reescrito.
- [ ] Sem código morto / flag/branch nunca usados.
- [ ] Breaking change de API/contrato sinalizado e versionado.
- [ ] Sem TODO crítico deixado pra trás.
- [ ] Complexidade proporcional ao problema (não engenharia demais).
