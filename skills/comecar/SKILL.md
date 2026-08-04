---
name: comecar
description: Onboarding do kit. Explica em 2 minutos o que cada grupo de skills faz, ajuda a personalizar a persona (stack, domínio) e sugere por onde começar. Feito pra não sobrecarregar um usuário novo — 26 skills assustam, isto reduz à primeira ação.
---

# /comecar — Comece aqui (onboarding)

Primeira vez ou se perdeu no meio das skills. 26 é muito — vou reduzir ao que importa pra você **agora**, sem despejar tudo.

## Como agir
1. Dê as boas-vindas curto e pergunte (1 de cada vez, ou aceite se já vier):
   - Sua stack/domínio? (ex: backend Java, front, dados)
   - O que mais te atrapalha hoje: **começar tarefa**, **foco**, **organização**, ou **comunicação**?
2. Com base na resposta, aponte **2-3 skills** pra começar já — não a lista toda.
3. Explique como **personalizar**: editar a seção "Quem sou eu" nos `SKILL.md` pro contexto da pessoa.
4. Sugira **1 ação agora** (rodar uma skill de verdade).

## Mapa por dor (use pra rotear)
- **"Travo pra começar"** → `/quebra` (decompõe) + `/foco` (1 ação)
- **"Perco o foco / muitas tarefas"** → `/planodia` + `/foco`
- **"Cabeça bagunçada"** → `/descarrega` + `/notas`
- **"Volto de interrupção perdido"** → `/retomar`
- **"Comunicação trava"** → `/traduz` (envio) + `/decodifica` (recebo)
- **"Não sei qual usar"** → `/qualskill <situação>`

## Grupos (resumo de 1 linha)
- 🧭 **Rotina/foco:** planodia, foco, descarrega, notas, resumo, retomar, quebra
- 🗣️ **Comunicação:** traduz, decodifica, standup, explica-pra, 1on1
- 💡 **Pensamento:** brainstorm, rubberduck, decisao, estimativa
- 🏛️ **Engenharia:** analisa, revisa, pr, adr, case, estudo
- 📡 **Atualização:** engenheiro, brief, ia, radar
- 🏆 **Carreira:** conquistas
- 🧭 **Meta:** qualskill, comecar, semana

## Formato da saída
```
## 👋 Bem-vindo
1 linha do que o kit faz.

## 🎯 Comece com estas
- /skill — por quê (ligado à sua dor)
- /skill — ...

## ⚙️ Personalize (opcional)
edite "Quem sou eu" em skills/<nome>/SKILL.md.

## 👉 Agora: rode isto
`/skill` — a primeira ação concreta.
```

## Regras duras
- Não liste as 26. Escolha 2-3 pela dor da pessoa.
- Termine com **uma** ação concreta, não com teoria.
- Curto, acolhedor, sem jargão de setup.
