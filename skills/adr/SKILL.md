---
name: adr
description: Gera um Architecture Decision Record (ADR) completo a partir de uma decisão que eu descrever — contexto, opções com prós/contras, decisão justificada, consequências e trade-offs. Carrega template, exemplo preenchido e guia de boas práticas sob demanda. Documentar decisão é marca de arquiteto/staff.
---

# /adr — Architecture Decision Record

Gero um **ADR** a partir da decisão que eu descrever. Documentar decisão é marca de arquiteto/staff — e minha memória externa de "por que fizemos assim".

## Quem sou eu
- Backend sênior, fintech, rumo a arquitetura/staff.
- TEA/TDAH/dislexia: preciso de template fixo pra não travar em "como escrever". Preencho a substância, você dá a estrutura.
- (Adapte a persona/domínio ao seu contexto.)

## Como agir
1. **Carregue o apoio conforme precisa** (progressive disclosure):
   - `templates/adr-template.md` — o template completo a preencher.
   - `examples/adr-exemplo.md` — um ADR real preenchido, pra calibrar profundidade.
   - `references/guia-adr.md` — quando escrever, statuses, erros comuns, dicas de qualidade.
2. Pego a decisão (`/adr usar outbox pattern pra publicar eventos de pagamento`).
3. Se faltar contexto, faça **1-3 perguntas curtas**: qual problema forçou isto? quais alternativas reais? restrições (escala, prazo, regulação)?
4. Preencha o template. O valor está em **opções descartadas + consequências negativas + trade-offs** — não pule.
5. Numere (próximo ADR-NNN) e sugira caminho `docs/adr/ADR-NNN-titulo.md`.

## Regras duras
- Sempre inclua **opções descartadas** com prós/contras — ADR sem alternativa é só anotação.
- **Consequências negativas explícitas.** Honestidade > vender a decisão.
- Diga **quando revisitar** (a condição que invalidaria a escolha).
- Ótica fintech: cite impacto em confiabilidade/segurança/regulação quando couber.
- Estruturado e escaneável; o ADR é pra ser lido rápido daqui a 1 ano.
