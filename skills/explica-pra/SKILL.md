---
name: explica-pra
description: Adapta um assunto técnico para o público certo — gestor, dev júnior, outro time, ou não-técnico. Ajusta profundidade, jargão e foco. Me ajuda a comunicar bem em qualquer nível, habilidade-chave pra evoluir a arquiteto/staff.
---

# /explica-pra — Adapta a mensagem ao público

Pego um assunto técnico e adapto pro **público-alvo**. Comunicar no nível certo é habilidade de staff — e reduz meu esforço de "traduzir na hora".

## Quem sou eu
- Backend sênior, fintech, rumo a arquitetura/staff.
- TEA/TDAH/dislexia: quero estrutura clara pra cada público, não improvisar.

## Como agir
1. Pego o assunto + o público (`/explica-pra gestor: por que precisamos refatorar o serviço de saldo`).
2. Se o público não veio, pergunte: "pra quem? gestor / júnior / outro time / não-técnico".
3. Adapte:
   - **Gestor** → impacto, risco, custo, prazo. Menos jargão. "por que importa pro negócio".
   - **Júnior** → conceito passo a passo, analogia, sem assumir contexto.
   - **Outro time** → interface/contrato, o que muda pra eles, o que precisam fazer.
   - **Não-técnico** → analogia do mundo real, zero jargão.

## Formato da saída
```
## 🎯 Para: [público]

[versão adaptada — estruturada, no tom certo]

## 💡 Ponto-chave a enfatizar
1 linha: o que ELE precisa levar embora.

## ⚠️ Evitar
o que confunde esse público (jargão X, detalhe Y).
```

## Regras duras
- Mesma verdade técnica, embalagem diferente. Não simplifique a ponto de mentir.
- Gestor quer impacto, não implementação. Júnior quer o caminho, não a resposta pronta.
- Sempre entregue o "ponto-chave a enfatizar".
