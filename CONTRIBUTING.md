# Contributing

🌐 🇬🇧 **English** · 🇧🇷 [Português](CONTRIBUTING.pt-BR.md)

Thanks for wanting to help! This kit exists to make the engineering day lighter for neurodivergent people (ADHD, autism, dyslexia). Contributions are welcome — new skills, improvements, translations, fixes.

## Core principle

Every skill must be **structured, scannable and direct** — the opposite of a wall of text. If the skill's output would tire someone with dyslexia or make someone with ADHD lose focus, it needs work.

Style rules for any skill:
- Headings + lists, **never** long paragraphs.
- Always explain the **"why it matters"**, not just the "what".
- End with **one** concrete action when it makes sense.
- Reduce cognitive load and decision paralysis — fewer options, more clarity.

## How to add a skill

1. Create the folder `skills/<name>/` with a `SKILL.md` file.
2. `SKILL.md` starts with YAML frontmatter:
   ```yaml
   ---
   name: skill-name
   description: A clear, specific sentence (up to ~200 chars). This is what triggers the skill and becomes the /skill-name command.
   ---
   ```
3. In the body, write the instructions Claude should follow. Include:
   - **About me** (persona/context — keep it generic and editable)
   - **How to act** (steps)
   - **Output format** (structured)
   - **Hard rules** (what never to do)
4. Test locally by copying it into `~/.claude/skills/` and restarting Claude Code.
5. Update the count and the list in `README.md` / `README.pt-BR.md` and the guide.

## Standards

- **No personal data.** No real names, companies, emails, absolute machine paths, tokens or passwords. Use a generic persona and paths like `~/.claude/...`.
- **Editable persona.** The "About me" section has a default (backend engineer), but make it clear the user adapts it to their own context.
- **Language.** The kit is PT-BR today, with English docs. Skill translations (EN) are very welcome — keep the structure.
- **One skill = one capability.** Don't pack five things into a single skill.

## PR flow

1. Fork + branch (`feat/skill-name` or `fix/...`).
2. Make the change following the standards above.
3. Run a quick personal-data check before committing:
   ```bash
   grep -rni "your-name\|your-company\|@gmail\|C:/Users" .
   ```
4. Open the PR describing **which neurodivergence pain point** the change addresses.

## Contribution ideas

- EN translation of the skills.
- New skills for other pain points (e.g. hyperfocus transitions, energy management).
- Persona variants for other stacks (frontend, data, mobile, SRE).
- Output examples and templates.

## Code of conduct

Be kind. This project deals with neurodivergence — respect and accessibility come first, in code and in conversation.
