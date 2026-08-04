# Dimensões de análise — perguntas-guia

Percorra cada dimensão. Não precisa responder tudo; use como rede pra não deixar buraco.

## 1. Correção & completude
- A proposta resolve o problema que ela mesma declara?
- Que casos ficaram de fora? (erro, borda, concorrência, migração de dados existentes)
- Que premissas ela assume sem dizer? Elas se sustentam no nosso contexto?
- Há contradição interna (uma seção nega outra)?

## 2. Trade-offs (o coração da análise)
- O que se **ganha** e o que se **perde** em cada decisão-chave.
- Que trade-off a doc **não menciona**? (é o que separa análise sênior de resumo)
- A doc escolheu consistência forte onde eventual bastaria — ou o contrário?
- Complexidade proporcional ao problema, ou engenharia demais/de menos?

## 3. Confiabilidade
- Falha parcial: se o passo 3 de 5 falha, o que acontece? Há compensação/saga?
- Idempotência onde há retry ou entrega at-least-once?
- Timeouts, retry com backoff, circuit breaker nas dependências?
- Consistência entre stores (banco + cache + broker)? Outbox/inbox?
- Recuperação após queda: reprocessa? Perde dado?

## 4. Escala & performance
- Onde está o gargalo quando o volume 10x? (banco, lock, rede, single-writer)
- Hot path: quantas chamadas de rede/DB por request?
- Alta cardinalidade (por usuário/conta) explode índice/cardinalidade de métrica?
- Custo em alta carga (compute, storage, egress) — cresce linear ou pior?
- Estado: onde vive? Dá pra escalar horizontal ou tem ponto único?

## 5. Segurança (fintech)
- Dado sensível (PAN, token, PII, saldo) — onde trafega, onde repousa, como é logado?
- Autorização: quem pode fazer o quê? Confia no cliente em algum ponto?
- Superfície de ataque nova? Entrada validada?
- Auditoria/rastreabilidade de operação financeira.
- Race em saldo/transação que permita gastar duas vezes.

## 6. Operação
- Observabilidade: dá pra ver que quebrou e por quê? Métrica/trace/log no ponto certo?
- Deploy: precisa downtime? Migração compatível com rolling? Rollback existe?
- Complexidade operacional: quantas peças novas o time passa a manter?
- Custo de manutenção e de plantão (quem é acordado às 3h e por quê?).

## 7. Alternativas
- Que abordagem diferente resolveria o mesmo problema?
- Em que condição a alternativa venceria a proposta?
- A doc considerou e descartou alternativas — com bons motivos, ou por omissão?

## Marcar lacunas
Se a doc **não fala** de algo crítico (ex: nada sobre falha parcial), isso é um achado: marque como **lacuna 🔴**, não invente o que ela teria dito.
