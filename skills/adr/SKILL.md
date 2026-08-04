---
name: adr
description: Gera o esqueleto de um Architecture Decision Record (ADR) no padrão, a partir de uma decisão que eu descrever. Estrutura contexto, opções, decisão, consequências e trade-offs. Me ajuda a documentar decisões de arquitetura de forma consistente, rumo a staff.
---

# /adr — Architecture Decision Record

Gero um **ADR** estruturado a partir da decisão que eu descrever. Documentar decisão é marca de arquiteto/staff — e minha memória externa de "por que fizemos assim".

## Quem sou eu
- Backend sênior, fintech, rumo a arquitetura/staff.
- TEA/TDAH/dislexia: preciso de template fixo pra não travar em "como escrever". Preencho a substância, você dá a estrutura.

## Como agir
1. Pego a decisão (`/adr usar outbox pattern pra publicar eventos de pagamento`).
2. Se faltar contexto, pergunte curto: qual problema forçou a decisão? quais alternativas? restrições?
3. Preencha o template. Puxe **trade-offs e consequências** — é o que dá valor ao ADR.
4. Numere e sugira nome de arquivo.

## Template
```
# ADR-<NNN>: <título curto da decisão>

- **Status:** proposto | aceito | substituído por ADR-XXX
- **Data:** <data>
- **Decisores:** <eu / time>

## Contexto
Que problema/força motivou isto? Restrições (escala, prazo, regulação fintech).

## Opções consideradas
1. **Opção A** — resumo | prós | contras
2. **Opção B** — ...

## Decisão
Escolhemos **X** porque ...

## Consequências
- ✅ Positivas: ...
- ⚠️ Negativas / custos: ...
- 🔭 O que passa a ser possível / impossível.

## Trade-offs & riscos
o que sacrificamos, o que monitorar, quando revisitar.
```

## Regras duras
- Sempre inclua **opções descartadas** — ADR sem alternativa é só anotação.
- Consequências negativas explícitas. Honestidade > vender a decisão.
- Ótica fintech: cite impacto em confiabilidade/segurança/regulação quando couber.
- Sugira `docs/adr/ADR-NNN-titulo.md` como caminho.
