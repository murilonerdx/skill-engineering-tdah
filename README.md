# skill-engineering-tdah

🌐 🇬🇧 **English** · 🇧🇷 [Português](README.pt-BR.md)

![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)
![Claude Code](https://img.shields.io/badge/Claude%20Code-skills-8A63D2)
![Skills](https://img.shields.io/badge/skills-30-blue)
![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)
![Neurodivergent friendly](https://img.shields.io/badge/neurodivergent-friendly-ff69b4)

**[Claude Code](https://docs.anthropic.com/claude-code) skills for neurodivergent software engineers.**

Built for people with **ADHD, autism (ASD) or dyslexia** who work in software engineering — especially backend/Java/Spring and fintech, but useful for any stack. Every skill produces **structured, scannable, direct** output: lists and headings, never walls of text.

> 30 skills that target where neurodivergence hits the technical day hardest: **starting a task, holding focus, organizing your head, communicating, deciding and remembering.**

> **Language note:** the skill content is currently written in **Portuguese (PT-BR)** — that's the persona/instructions Claude follows. The commands and the ideas work in any language, and English translations are very welcome (see [Contributing](CONTRIBUTING.md)).

---

## Who it's for

- A dev/engineer with **ADHD** who freezes before starting, drowns in long lists, or underestimates time.
- Someone with **autism** who finds the tone/subtext of messages ambiguous.
- Someone with **dyslexia** who gets worn down by walls of text.
- A mid/senior engineer heading toward **architect/staff** who wants routine support and technical tools in one place.

---

## The 30 skills

### 🧭 Routine & focus

| Command | What it does |
|---|---|
| `/planodia` | Your day in 3 blocks by energy level |
| `/foco` | From a chaotic list to a single next action |
| `/quebra` | A big task into tiny steps |
| `/retomar` | "Where was I" after an interruption |
| `/descarrega` | Organized brain-dump |
| `/notas` | Dated external memory |
| `/resumo` | TL;DR of long text |

### 🗣️ Communication

| Command | What it does |
|---|---|
| `/traduz` | Makes my text clear |
| `/decodifica` | Decodes a received message (tone/intent) |
| `/standup` | Daily standup update |
| `/explica-pra` | Adapts a topic to the audience |
| `/1on1` | Prepares the 1:1 |

### 💡 Thinking & decisions

| Command | What it does |
|---|---|
| `/brainstorm` | Thinks with you through questions |
| `/rubberduck` | Socratic rubber duck |
| `/decisao` | Options table + recommendation |
| `/estimativa` | Realistic estimate (fights time blindness) |

### 🏛️ Engineering & architecture

| Command | What it does |
|---|---|
| `/analisa` | Dissects a technical doc |
| `/revisa` | Critical review of what I wrote |
| `/pr` | PR review (fintech checklist) |
| `/adr` | Architecture Decision Record |
| `/case` | LLM take-home guide |
| `/estudo` | Guided lesson + quiz |

### 📡 Staying current

| Command | What it does |
|---|---|
| `/engenheiro` | Tech radar (free-form topic) |
| `/brief` | Weekly briefing |
| `/ia` | Trending AI tools |
| `/radar` | Source discipline |

### 🏆 Career & rhythm

| Command | What it does |
|---|---|
| `/conquistas` | Brag doc for promotion |
| `/semana` | Weekly review (zoom-out) |

### 🧭 Meta

| Command | What it does |
|---|---|
| `/qualskill` | Router — recommends the right skill for your situation |
| `/comecar` | Onboarding — where to start |

📖 Full usage guide with examples: **[GUIDE.md](GUIDE.md)** (EN) · **[GUIA.md](GUIA.md)** (PT-BR).

---

## Installation

### Via marketplace (recommended)
In an interactive Claude Code session, **in the chat** (not the terminal):
```
/plugin marketplace add murilonerdx/skill-engineering-tdah
/plugin install skill-engineering-tdah@skill-engineering-tdah
```
Restart Claude Code.

### Local (clone)
```bash
git clone https://github.com/murilonerdx/skill-engineering-tdah.git
```
In the Claude Code chat:
```
/plugin marketplace add /path/to/skill-engineering-tdah
/plugin install skill-engineering-tdah@skill-engineering-tdah
```

### Alternative: personal skills (no plugin)
Copy the `skills/` folder into `~/.claude/skills/` and restart:
```bash
cp -r skill-engineering-tdah/skills/* ~/.claude/skills/
```

> Slash commands (`/plugin`, `/foco`, ...) run **in the Claude Code chat**, never in the terminal/PowerShell.

---

## Customize

The skills ship with a default persona (backend Java/Spring engineer, fintech, heading to staff). Adapt it to your context:

1. Edit the **"Quem sou eu"** (About me) section in each skill's `SKILL.md` (stack, domain, goal).
2. Adjust the `/pr` checklist for your domain (if not fintech).
3. Reinstall/re-sync and restart.

The style (structured, visual, direct) and the skill logic work for any stack.

---

## Maintenance

- **Cleanup:** a skill costs context (tokens) even when it doesn't fire. Remove the ones you haven't used in 30 days.
- **Edited a skill installed as personal?** Re-sync: `cp -r skills/* ~/.claude/skills/` and restart.

---

## Contributing

PRs welcome — new skills, structure improvements, translations (EN), fixes.
Guideline: every skill must be **structured, scannable and direct** (the opposite of a wall of text) and explain the "why it matters".

See the [contributing guide](CONTRIBUTING.md) for how to add a skill and the project standards.

---

## License

[MIT](LICENSE).
