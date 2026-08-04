# skill-engineering-tdah

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

**🧭 Rotina & foco**
`/planodia` dia em 3 blocos por energia · `/foco` lista caótica → 1 ação · `/quebra` tarefa grande → micro-passos · `/retomar` "onde eu parei" após interrupção · `/descarrega` brain-dump organizado · `/notas` memória externa datada · `/resumo` TL;DR de texto longo

**🗣️ Comunicação**
`/traduz` meu texto claro · `/decodifica` decodifica msg recebida (tom/intenção) · `/standup` update de daily · `/explica-pra` adapta ao público · `/1on1` prepara o 1:1

**💡 Pensamento & decisão**
`/brainstorm` pensa junto por perguntas · `/rubberduck` pato socrático · `/decisao` tabela + recomendação · `/estimativa` estimativa realista (anti-cegueira temporal)

**🏛️ Engenharia & arquitetura**
`/analisa` disseca doc técnica · `/revisa` revisão crítica · `/pr` review de PR (checklist fintech) · `/adr` Architecture Decision Record · `/case` guia de take-home de LLM · `/estudo` aula guiada + quiz

**📡 Atualização**
`/engenheiro` radar de tecnologia (tema livre) · `/brief` briefing semanal · `/ia` ferramentas de IA em alta · `/radar` disciplina de fontes

**🏆 Carreira & ritmo**
`/conquistas` brag doc pra promoção · `/semana` revisão semanal (zoom-out)

**🧭 Meta**
`/qualskill` roteador — descreve a situação e ele recomenda a skill certa (inclusive de outros plugins instalados) · `/comecar` onboarding (por onde começar)

Guia de uso completo com exemplos: [GUIA.md](GUIA.md).

---

## Instalação

### Via marketplace (recomendado)
Numa sessão interativa do Claude Code, **no chat** (não no terminal):
```
/plugin marketplace add <seu-usuario>/skill-engineering-tdah
/plugin install skill-engineering-tdah@skill-engineering-tdah
```
Reinicie o Claude Code.

### Local (clonando)
```bash
git clone https://github.com/<seu-usuario>/skill-engineering-tdah.git
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

---

## Licença

[MIT](LICENSE).
