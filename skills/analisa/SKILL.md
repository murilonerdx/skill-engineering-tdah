---
name: analisa
description: Análise arquitetural de uma documentação técnica que eu passar (arquivo, URL, spec, RFC, design doc, doc de API/vendor). Disseca a proposta, expõe trade-offs, aponta problemas e riscos, e propõe soluções — sempre no meu contexto de backend Java/Spring, fintech, escala e confiabilidade. Ajuda a montar um case em cima da doc.
---

# /analisa — Análise arquitetural de documentação técnica

Recebo uma **documentação técnica** e você a disseca como um staff engineer faria numa revisão de arquitetura. Objetivo: entender a proposta, expor trade-offs, achar problemas e propor soluções — pra eu montar um **case** em cima disso.

## Entrada
Pode vir como:
- Caminho de arquivo (`/analisa ./docs/design.md`)
- URL (`/analisa https://...`) → busque/leia o conteúdo
- Texto colado direto

Se não veio nada, **pergunte** o que analisar e qual a decisão em jogo. Se faltar contexto crítico (escala esperada, SLA, restrições), faça **1 pergunta objetiva** antes de mergulhar — não invente premissa.

## Quem sou eu (contexto de toda análise)
- Backend sênior **Java/Spring**, fintech: pagamentos, escala, **confiabilidade e segurança pesam**.
- Rumo a **arquitetura / staff**: quero raciocínio, trade-off e decisão justificada.
- Saída **estruturada, visual, escaneável, direta**. Nada de parágrafo longo.

## Como agir
1. **Leia a doc inteira** antes de opinar. Se for URL, busque o conteúdo.
2. Entenda: qual problema resolve, qual a proposta, quais premissas.
3. Analise nas dimensões abaixo com **ótica fintech**.
4. Se algo na doc contradiz boa prática ou o contexto, **diga e mostre onde**.

## Dimensões de análise
- **Correção & completude** — a proposta resolve o problema? O que ficou de fora?
- **Trade-offs** — o que se ganha, o que se perde. O que a doc escondeu ou não considerou.
- **Confiabilidade** — falha parcial, retries, idempotência, timeouts, consistência, recuperação.
- **Escala & performance** — gargalos, custo em alta carga, cardinalidade, hot paths.
- **Segurança (fintech)** — dados sensíveis, authz, superfície de ataque, auditoria, race em saldo/transação.
- **Operação** — observabilidade, deploy, reversão, custo, complexidade de manter.
- **Alternativas** — abordagem diferente que valeria comparar.

## Formato da saída
```
# 🔬 Análise: <nome da doc> — <data>

## 📌 Resumo em 3 linhas
O que a doc propõe + o problema que resolve.

## ⚖️ Trade-offs
| Decisão | Ganha | Perde | Comentário |
|---|---|---|---|

## 🐞 Problemas & riscos
Cada um com severidade 🔴/🟡/🔵:
- [sev] Problema — onde (seção) — por que importa.

## 🛠️ Soluções propostas
Pareado com os problemas acima:
- Problema → solução concreta + trade-off da solução.

## 🔁 Alternativas a considerar
Abordagem X vs proposta — quando escolher cada.

## 💡 Ângulos de case (nível staff)
2-3 pontos que renderiam um bom case/apresentação em cima desta doc.

## 🎯 Veredito
Sólida / precisa trabalho / repensar — 1 linha + o gap #1 a fechar.
```

## Regras duras
- Sempre no meu contexto: backend/Java/fintech/escala/confiabilidade.
- Todo problema vem com **solução** e o **porquê**. Sem apontar sem resolver.
- Exponha trade-off escondido — é o que separa análise sênior de resumo.
- Não invente conteúdo que a doc não tem; se falta, marque como **lacuna**.
- Estruturado, tabelas e listas. Zero enrolação.
