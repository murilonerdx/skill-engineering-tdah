---
name: pr
description: Revisa meu pull request contra um checklist de fintech — correção, segurança, idempotência, confiabilidade, testes, observabilidade. Aponta o que falta antes de eu abrir/mergear. Feedback direto e priorizado, com o porquê de cada item.
---

# /pr — Revisão de PR com checklist fintech

Reviso meu PR (diff, arquivos, ou descrição) contra um **checklist de fintech** antes de abrir ou mergear. Objetivo: pegar o que eu esqueci, especialmente risco de dinheiro.

## Quem sou eu
- Backend sênior, fintech: pagamentos, escala, **confiabilidade e segurança pesam**.
- TEA/TDAH: checklist fixo evita que eu esqueça o de sempre.

## Entrada
- `/pr` num repo git → analise o diff da branch atual (`git diff`).
- Ou eu passo arquivos / colo o diff / dou a descrição do PR.
- Se não achar diff, pergunte o que revisar.

## Checklist (avalie cada, marque ✅ / ⚠️ / ❌ / n/a)

**Correção**
- Lógica certa? Casos-limite (null, vazio, zero, negativo, concorrência)?

**Segurança (fintech)**
- Dado sensível em log? Authz checada? Injeção? Validação de entrada?
- Valor/saldo manipulado com segurança? Race em transação?

**Confiabilidade**
- Idempotência (retry não duplica cobrança)? Timeouts? Retry com backoff?
- Falha parcial tratada? Transação/consistência? Rollback?

**Testes**
- Cobre caminho feliz + erro + limite? Teste de idempotência/concorrência?

**Observabilidade**
- Log estruturado? Métrica/trace no caminho crítico? Erro rastreável?

**Qualidade**
- Nomes claros? Sem código morto? Migração reversível? Breaking change sinalizado?

## Formato da saída
```
# 🔍 Review PR — <branch/título>

## Veredito: pronto ✅ / precisa ajustes ⚠️ / não mergear ❌
1 linha.

## 🔴 Bloqueadores (resolver antes de mergear)
- [arquivo:linha] problema — por quê — fix.

## 🟡 Deveria arrumar
- ...

## 🔵 Nits (opcional)
- ...

## ✅ Checklist
idempotência ✅ · segurança ⚠️ · testes ❌ · observabilidade ✅ ...
```

## Regras duras
- Prioridade: **dinheiro e segurança** primeiro. Idempotência em pagamento é bloqueador, não nit.
- Todo achado com local + porquê + fix.
- Não invente problema; se tá bom, diga "pronto pra mergear".
- Direto e priorizado. Bloqueador != nit.
