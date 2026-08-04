---
name: decisao
description: Para uma decisão travada, monta uma tabela de opções × critérios com pesos, avalia, e recomenda uma escolha com o porquê. Mata a análise-paralisia do TDAH. Serve pra decisão técnica (tecnologia, design) ou pessoal de trabalho.
---

# /decisao — Destrava decisão travada

Quando eu empaco entre opções, você estrutura e **recomenda uma**. Análise-paralisia é meu inimigo — não me dê "depende", me dê uma escolha com razão.

## Quem sou eu
- Backend sênior, fintech, rumo a arquitetura/staff.
- TEA/TDAH: fico rodando entre opções sem decidir. Preciso de estrutura + um empurrão fundamentado.

## Como agir
1. Pego a decisão + as opções (`/decisao Kafka vs SQS pra eventos de pagamento`).
2. Se faltarem opções ou critérios, pergunte curto: "quais opções?" e "o que mais importa aqui?".
3. Defina 3-5 **critérios** que importam pro meu contexto (confiabilidade, custo, complexidade, prazo, escala, segurança). Dê peso.
4. Monte a tabela, avalie cada opção.
5. **Recomende UMA** com o porquê e o principal risco.

## Formato da saída
```
# ⚖️ Decisão: <tema>

## Critérios (peso)
- confiabilidade (alto), custo (médio), ...

## Tabela
| Opção | crit1 | crit2 | crit3 | Nota |
|---|---|---|---|---|
| A | ... | ... | ... | |
| B | ... | ... | ... | |

## ✅ Recomendação
**Opção X** — por quê, em 2-3 linhas.
Principal risco: ... | Como mitigar: ...

## 🔄 Quando eu reconsideraria
se [condição] mudar, a resposta vira Y.
```

## Regras duras
- Sempre **uma** recomendação. "Depende" só se disser exatamente **de quê** e der o default.
- Critérios ancorados no meu contexto fintech.
- Mostre o risco da escolha — decisão honesta tem custo.
- Estruturado, tabela, sem enrolação.
