---
name: qualskill
description: Roteador de TODAS as skills e plugins instalados no meu Claude Code. Descrevo uma situação, tarefa ou sentimento e ela escaneia tudo que está instalado (minhas 26 skills + plugins como caveman, superpowers, engineering-skills, anthropic-skills, etc), analisa meu contexto, e recomenda a melhor skill/comando para o momento. Cura o "tenho a ferramenta certa mas esqueci qual e onde".
---

# /qualskill — Qual skill/plugin usar agora (install inteiro)

Descrevo o que tá rolando; você recomenda **a ferramenta certa de TODO o meu Claude** — minhas skills + qualquer plugin instalado. Não só o meu toolkit. Muita coisa instalada = impossível lembrar. Isto roteia sobre tudo.

## Quem sou eu
- Backend sênior Java/Spring, fintech, rumo a staff. TEA/TDAH/dislexia.
- Resposta **curta e direta**: qual comando rodar, de qual origem, e por quê.

## Como agir

### 1. Descobrir o que está instalado (escaneie AO VIVO — não confie em lista fixa)
Fontes a ler:
- **Skills disponíveis nesta sessão** — a lista de skills injetada no contexto (via Skill tool) já traz nome + descrição de tudo carregado. Use como fonte primária.
- **Minhas skills pessoais** — `Glob` em `~/.claude/skills/*/SKILL.md` e no `.claude/skills/` do projeto atual. Leia o frontmatter (`name`, `description`).
- **Plugins instalados** — leia `~/.claude/plugins/installed_plugins.json` pra listar plugins (ex: caveman, superpowers, engineering-skills, anthropic-skills, code-review, feature-dev...). Skills deles ficam em `~/.claude/plugins/cache/<marketplace>/<plugin>/<versao>/skills/*/SKILL.md` — `Glob` + leia frontmatter se precisar de detalhe.

Prefira a lista já injetada no contexto (rápida); só leia disco se faltar detalhe ou o usuário pedir varredura completa.

### 2. Rotear
- Case a situação com o catálogo descoberto. Considere meu contexto (fintech, neurodivergência, carreira staff).
- **Prioridade:** minhas skills pessoais (feitas pra mim) primeiro; plugin externo quando cobre melhor.
- Se veio vago ("tô perdido"), 1 pergunta curta OU já sugira `/foco`/`/descarrega`.

### 3. Recomendar
1-3 opções, melhor primeiro. Diga a **origem** (minha skill vs plugin X).

## Formato da saída
```
## 👉 Use: /skill   (origem: minha skill | plugin <nome>)
por quê: 1 linha.
comando: `/skill <arg>`

## 🤔 Alternativas
- /outra (origem) — quando faria mais sentido

## 🧩 Não tem ferramenta boa?
diga direto "faço na mão" — não force.
```

## Atalho de contexto — minhas skills pessoais (toolkit)
Referência rápida (mas SEMPRE confirme contra o que está instalado de verdade):
- Rotina: `/planodia` `/foco` `/descarrega` `/notas` `/resumo`
- Comunicação: `/traduz` `/decodifica` `/standup` `/explica-pra` `/1on1`
- Pensamento: `/brainstorm` `/rubberduck` `/decisao` `/estimativa`
- Engenharia: `/analisa` `/revisa` `/pr` `/adr` `/case` `/estudo`
- Atualização: `/engenheiro` `/brief` `/ia` `/radar`
- Carreira: `/conquistas`

Plugins externos comuns no meu install (exemplos — confirme ao vivo): caveman, superpowers, engineering-skills, anthropic-skills, code-review, feature-dev, frontend-design, docker-development, agenthub.

## Regras duras
- Escaneie o que está instalado **de verdade**; não invente skill que não existe.
- Recomendação principal única e clara. Não despeje 5 opções.
- Sempre diga a **origem** (minha skill ou qual plugin).
- Sobrecarga emocional → `/foco` ou `/descarrega` antes de tarefa técnica.
- Curto, comando pronto pra colar.
