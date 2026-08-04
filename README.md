# skill-engineering-tdah

![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)
![Claude Code](https://img.shields.io/badge/Claude%20Code-skills-8A63D2)
![Skills](https://img.shields.io/badge/skills-30-blue)
![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)
![Neurodivergent friendly](https://img.shields.io/badge/neurodivergent-friendly-ff69b4)

**Kit de skills do [Claude Code](https://docs.anthropic.com/claude-code) para engenheiros de software neurodivergentes.**

Feito para quem tem **TDAH, TEA (autismo) ou dislexia** e trabalha com engenharia de software — especialmente backend/Java/Spring e fintech, mas útil pra qualquer stack. Todas as skills entregam saída **estruturada, visual, escaneável e direta**: listas e títulos, nada de parágrafo longo.

> 30 skills que atacam os pontos onde a neurodivergência mais atrapalha o dia técnico: **iniciar tarefa, manter foco, organizar a cabeça, comunicar, decidir e lembrar.**

---

## Pra quem é

- Dev/engenheiro com **TDAH** que trava pra começar, se perde em lista longa, ou subestima prazo.
- Com **TEA** que acha ambíguo o tom/subtexto de mensagens.
- Com **dislexia** que cansa em parede de texto.
- Sênior/pleno rumo a **arquitetura/staff** que quer apoio de rotina + ferramentas técnicas no mesmo lugar.

---

## As 30 skills

### 🧭 Rotina & foco

| Comando | O que faz |
|---|---|
| `/planodia` | Dia em 3 blocos por energia |
| `/foco` | De lista caótica a uma única ação |
| `/quebra` | Tarefa grande em micro-passos |
| `/retomar` | "Onde eu parei" após interrupção |
| `/descarrega` | Brain-dump organizado |
| `/notas` | Memória externa datada |
| `/resumo` | TL;DR de texto longo |

### 🗣️ Comunicação

| Comando | O que faz |
|---|---|
| `/traduz` | Deixa meu texto claro |
| `/decodifica` | Decodifica mensagem recebida (tom/intenção) |
| `/standup` | Update de daily |
| `/explica-pra` | Adapta ao público |
| `/1on1` | Prepara o 1:1 |

### 💡 Pensamento & decisão

| Comando | O que faz |
|---|---|
| `/brainstorm` | Pensa junto por perguntas |
| `/rubberduck` | Pato de borracha socrático |
| `/decisao` | Tabela de opções + recomendação |
| `/estimativa` | Estimativa realista (anti-cegueira temporal) |

### 🏛️ Engenharia & arquitetura

| Comando | O que faz |
|---|---|
| `/analisa` | Disseca doc técnica |
| `/revisa` | Revisão crítica do que escrevi |
| `/pr` | Review de PR (checklist fintech) |
| `/adr` | Architecture Decision Record |
| `/case` | Guia de take-home de LLM |
| `/estudo` | Aula guiada + quiz |

### 📡 Atualização

| Comando | O que faz |
|---|---|
| `/engenheiro` | Radar de tecnologia (tema livre) |
| `/brief` | Briefing semanal |
| `/ia` | Ferramentas de IA em alta |
| `/radar` | Disciplina de fontes |

### 🏆 Carreira & ritmo

| Comando | O que faz |
|---|---|
| `/conquistas` | Brag doc pra promoção |
| `/semana` | Revisão semanal (zoom-out) |

### 🧭 Meta

| Comando | O que faz |
|---|---|
| `/qualskill` | Roteador — recomenda a skill certa pra sua situação |
| `/comecar` | Onboarding — por onde começar |

📖 Guia de uso completo com exemplos: **[GUIA.md](GUIA.md)**.

---

## Instalação

### Via marketplace (recomendado)
Numa sessão interativa do Claude Code, **no chat** (não no terminal):
```
/plugin marketplace add murilonerdx/skill-engineering-tdah
/plugin install skill-engineering-tdah@skill-engineering-tdah
```
Reinicie o Claude Code.

### Local (clonando)
```bash
git clone https://github.com/murilonerdx/skill-engineering-tdah.git
```
No chat do Claude Code:
```
/plugin marketplace add /caminho/para/skill-engineering-tdah
/plugin install skill-engineering-tdah@skill-engineering-tdah
```

### Alternativa: skills pessoais (sem plugin)
Copie a pasta `skills/` para `~/.claude/skills/` e reinicie:
```bash
cp -r skill-engineering-tdah/skills/* ~/.claude/skills/
```

> Slash commands (`/plugin`, `/foco`, ...) rodam **no chat do Claude Code**, nunca no terminal/PowerShell.

---

## Personalizar

As skills têm uma persona padrão (engenheiro backend Java/Spring, fintech, rumo a staff). Adapte pro seu contexto:

1. Edite a seção **"Quem sou eu"** no `SKILL.md` de cada skill (stack, domínio, objetivo).
2. Ajuste o checklist do `/pr` pro seu domínio (se não for fintech).
3. Reinstale/re-sincronize e reinicie.

O estilo (estruturado, visual, direto) e a lógica das skills valem pra qualquer stack.

---

## Manutenção

- **Faxina:** skill custa contexto (tokens) mesmo sem disparar. Remova as que não usar em 30 dias.
- **Editou uma skill instalada como pessoal?** Re-sincronize: `cp -r skills/* ~/.claude/skills/` e reinicie.

---

## Contribuir

PRs bem-vindos — novas skills, melhorias de estrutura, traduções (EN), correções.
Diretriz: toda skill deve ser **estruturada, escaneável e direta** (o oposto de parede de texto) e explicar o "por que importa".

Veja o [guia de contribuição](CONTRIBUTING.md) pra como adicionar uma skill e os padrões do projeto.

---

## Licença

[MIT](LICENSE).
