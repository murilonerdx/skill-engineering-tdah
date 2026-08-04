# 📘 skill-engineering-tdah — Usage guide

🌐 🇬🇧 **English** · 🇧🇷 [Português](GUIA.md)

How to use the 30 skills. Built to be **scannable** — jump straight to the section you need.

> **Forgot which one to use?** Run `/qualskill <situation>` and it points you to the right one.

> **Language note:** the skills themselves respond in **Portuguese (PT-BR)** for now. Commands and structure are universal; EN translations welcome.

---

## ⚡ Quick start

1. Skills live in `~/.claude/skills/` (global, valid in every project).
2. Versioned source: the repo folder `skill-engineering-tdah/`.
3. Use them by typing `/` + name **in the Claude Code chat** (never in PowerShell).
4. Edited a skill? Re-sync (see [Maintenance](#-maintenance)).

---

## 🗺️ Quick map (stick this on the wall)

| Situation | Command |
|---|---|
| Don't know which skill to use | `/qualskill <situation>` |
| Start the day | `/planodia` |
| Stuck, where do I begin | `/foco` |
| Big/scary task | `/quebra` |
| Back from an interruption, lost | `/retomar` |
| Head exploding | `/descarrega` |
| Long doc/text to read | `/resumo <doc>` |
| Got a confusing message | `/decodifica` |
| About to send a message/email/PR | `/traduz` |
| Prep the daily | `/standup` |
| Prep the 1:1 | `/1on1` |
| Stuck decision | `/decisao` |
| Estimate effort | `/estimativa` |
| Evaluate a technical doc | `/analisa <doc>` |
| Review what I wrote | `/revisa` |
| Review a PR | `/pr` |
| Document an arch decision | `/adr` |
| Learn a topic | `/estudo <topic>` |
| Industry news | `/engenheiro` |
| Log a win | `/conquistas` |
| Close the week | `/semana` |

---

## 🧭 Routine & focus

### `/planodia`
Structures the day into 3 blocks by energy + "the one thing today".
```
/planodia
```

### `/foco`
Chaotic list → **one next action**. Kills paralysis.
```
/foco I need to finish the PR, answer Slack, review the risk doc, update the ticket
```

### `/quebra`
A big/vague task → 5-8 tiny concrete steps (< 30 min each). Fights initiation paralysis.
```
/quebra integrate the new payment gateway
```

### `/retomar`
Rebuilds "where was I" after an interruption.
```
/retomar salvar ...   ← save your state before switching
/retomar              ← resume: rebuilds context + next step
```

### `/descarrega`
Brain-dump with zero loss. Empties your head.
```
/descarrega I've got a million things: the idempotency bug, that cache idea, deadline fear...
```

### `/notas`
Dated external memory (`notas/YYYY-MM-DD.md`).
```
/notas decided to use outbox for the payment event because direct retry double-charged
/notas buscar idempotency   ← retrieve later
```

### `/resumo`
Long doc/thread → scannable TL;DR (dyslexia-friendly).
```
/resumo ./docs/gateway-spec.md
```

---

## 🗣️ Communication

### `/traduz`
Text **I'm about to send** → clear, short, keeps my voice.
```
/traduz maybe we could sort of look at the balance service since it's kinda slow sometimes
```

### `/decodifica`
Message **I received** → what they want, tone, ready-made reply.
```
/decodifica boss wrote: "can we talk about yesterday's deploy when you get a chance?"
```

### `/standup`
Loose notes → daily update.
```
/standup yesterday worked on outbox and got stuck on the concurrency test, today continuing
```

### `/explica-pra`
Adapts a topic to the audience.
```
/explica-pra manager: why we need to refactor the balance service
/explica-pra junior: what idempotency is
```

### `/1on1`
1:1 script + career angle.
```
/1on1
```

---

## 💡 Thinking & decisions

### `/brainstorm`
Explores the problem **through questions**, in layers. Doesn't dump an answer.
```
/brainstorm how to version the API without breaking current clients
```

### `/rubberduck`
Socratic rubber duck. Questions so you find it yourself. Only gives the answer if you ask.
```
/rubberduck my Kafka consumer is processing the same message twice
```

### `/decisao`
Stuck options → table + recommendation.
```
/decisao Kafka vs SQS for payment events
```

### `/estimativa`
Realistic range estimate (fights time blindness).
```
/estimativa integrate new gateway into the billing service
```

---

## 🏛️ Engineering & architecture

### `/analisa`
An **external** technical doc → trade-offs, problems, solutions.
```
/analisa ./docs/antifraud-design.md
```

### `/revisa`
Critical review of **what I wrote** (code/ADR/text).
```
/revisa            ← paste the code/text, or pass the file
```

### `/pr`
PR review against a fintech checklist (idempotency, security, tests).
```
/pr                ← analyzes the current branch diff
```

### `/adr`
Architecture Decision Record skeleton.
```
/adr use the outbox pattern to publish payment events
```

### `/case`
Guides the LLM Engineering take-home step by step.
```
/case
```

### `/estudo`
Guided lesson + exercise + quiz. Connects to your context.
```
/estudo idempotency
```

---

## 📡 Staying current

### `/engenheiro`
Tech radar. **Free-form topic** or general sweep.
```
/engenheiro                 ← sweeps 10 areas of your stack
/engenheiro spring ai       ← deep dive on one topic
```

### `/brief`
Lean weekly briefing (5 areas).

### `/ia`
Trending AI tools only, with hype/adopted rating.

### `/radar`
Source discipline (rule of 3x, fixed time).
```
/radar event sourcing
```

---

## 🏆 Career & rhythm

### `/conquistas`
Accumulated brag doc (`conquistas.md`) for promotion.
```
/conquistas cut balance service p99 from 800ms to 120ms
/conquistas resumo          ← pull for review/1:1
```

### `/semana`
Weekly review (zoom-out). Closes the week, opens the next with 1-3 focuses.
```
/semana
```

---

## 🔁 Daily combos

**Morning**
```
/planodia → structure the day
```
**Stuck mid-task**
```
/quebra (break it down) then /foco (one action)
```
**Head full / anxious**
```
/descarrega → empty it
```
**Before the daily**
```
/standup
```
**End of day**
```
/notas (what I learned/decided) + /conquistas (what I shipped)
```
**Don't know what to use**
```
/qualskill <situation>
```

---

## 🛠️ Maintenance

**Edited a skill (at the source) and want it active:**
```bash
cp -r skills/* ~/.claude/skills/
```
Then restart Claude Code.

**Version a change:**
```bash
git add . && git commit -m "description of the change"
```

**Monthly cleanup:** delete skills unused for 30 days. A skill costs context even when it doesn't fire.

---

## ❓ Common problems

| Symptom | Cause | Fix |
|---|---|---|
| `/skill` doesn't show up | Claude didn't rescan | Close and reopen Claude Code |
| `/plugin not recognized` | Ran it in PowerShell | Slash commands go in the **chat**, not the terminal |
| Edited and nothing changed | Edited source, not the global copy | Re-sync (see Maintenance) |
| Wrong skill fires | Ambiguous description | Call it by the exact `/name` |

---

## 📂 Structure

```
skill-engineering-tdah/
├── .claude-plugin/
│   ├── plugin.json
│   └── marketplace.json
├── skills/            ← 30 skills (source)
├── README.md          ← index (EN)
├── README.pt-BR.md    ← index (PT-BR)
├── GUIDE.md           ← this guide (EN)
└── GUIA.md            ← this guide (PT-BR)
```
Active in: `~/.claude/skills/` (synced copy).
