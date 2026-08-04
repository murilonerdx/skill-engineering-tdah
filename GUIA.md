# 📘 Guia do skill-engineering-tdah

🌐 🇬🇧 [English](GUIDE.md) · 🇧🇷 **Português**

Como usar as 30 skills. Feito pra ser **escaneável** — pula direto pra seção que precisa.

> **Esqueceu qual usar?** Roda `/qualskill <situação>` e ela te aponta a certa.

---

## ⚡ Início rápido

1. Skills ficam em `~/.claude/skills/` (globais, valem em todo projeto).
2. Fonte versionada: `./`.
3. Usa digitando `/` + nome **no chat do Claude Code** (nunca no PowerShell).
4. Mexeu numa skill? Re-sincroniza (ver [Manutenção](#-manutenção)).

---

## 🗺️ Mapa rápido (cola isto na parede)

| Situação | Comando |
|---|---|
| Não sei qual skill usar | `/qualskill <situação>` |
| Começar o dia | `/planodia` |
| Travado, por onde começo | `/foco` |
| Cabeça explodindo | `/descarrega` |
| Doc/texto longo pra ler | `/resumo <doc>` |
| Recebi msg confusa | `/decodifica` |
| Vou mandar msg/email/PR | `/traduz` |
| Preparar daily | `/standup` |
| Preparar 1:1 | `/1on1` |
| Decisão travada | `/decisao` |
| Estimar prazo | `/estimativa` |
| Avaliar doc técnica | `/analisa <doc>` |
| Revisar o que escrevi | `/revisa` |
| Revisar PR | `/pr` |
| Documentar decisão de arq | `/adr` |
| Aprender um tópico | `/estudo <tema>` |
| Novidades da área | `/engenheiro` |
| Registrar vitória | `/conquistas` |

---

## 🧭 Rotina & foco (TEA/TDAH)

### `/planodia`
Estrutura o dia em 3 blocos por energia + "a 1 coisa de hoje".
```
/planodia
```
→ pergunta o que precisa sair + tua energia; devolve blocos foco/ritmo/baixa energia.

### `/foco`
Lista caótica → **1 próxima ação**. Mata paralisia.
```
/foco preciso terminar o PR, responder o Slack, revisar doc do risco, atualizar o ticket
```
→ 1 ação AGORA + máx 3 depois + resto guardado.

### `/descarrega`
Brain-dump sem perder nada. Esvazia a cabeça.
```
/descarrega tô com mil coisas: o bug de idempotência, aquela ideia de cache, medo do prazo, ligar pro RH...
```
→ organizado em Projetos / Tarefas / Ideias / Preocupações.

### `/notas`
Memória externa datada (`notas/AAAA-MM-DD.md`).
```
/notas decidi usar outbox pro evento de pagamento porque retry direto duplicava cobrança
/notas buscar idempotência        ← recupera depois
```

### `/resumo`
Doc/thread longo → TL;DR escaneável (dislexia).
```
/resumo ./docs/spec-gateway.md
/resumo https://link-da-thread
```

---

## 🗣️ Comunicação

### `/traduz`
Texto **que eu vou mandar** → claro, curto, mantém minha voz.
```
/traduz acho q talvez a gente pudesse quem sabe mexer no serviço de saldo pq tá meio lento as vezes
```
→ versão pronta + o que mudou.

### `/decodifica`
Mensagem **que eu recebi** → o que querem, tom, resposta pronta.
```
/decodifica chefe mandou: "podemos conversar sobre o deploy de ontem quando puder?"
```
→ intenção real + urgência + 2 rascunhos de resposta.

### `/standup`
Notas soltas → update de daily.
```
/standup ontem mexi no outbox e travei no teste de concorrência, hoje continuo, tô preso numa dúvida do lock
```

### `/explica-pra`
Adapta assunto ao público.
```
/explica-pra gestor: por que precisamos refatorar o serviço de saldo
/explica-pra júnior: o que é idempotência
```

### `/1on1`
Roteiro do 1:1 + ângulo carreira staff.
```
/1on1
```
→ conquistas, bloqueios, o que pedir, perguntas pro líder.

---

## 💡 Pensamento & decisão

### `/brainstorm`
Explora problema **por perguntas**, em camadas. Não despeja resposta.
```
/brainstorm como versionar a API sem quebrar os clientes atuais
```

### `/rubberduck`
Pato socrático. Perguntas pra tu achar sozinho. Só dá resposta se pedir.
```
/rubberduck meu consumer Kafka tá processando a mesma mensagem duas vezes
```

### `/decisao`
Opções travadas → tabela + recomendação.
```
/decisao Kafka vs SQS pra eventos de pagamento
```

### `/estimativa`
Estimativa realista em faixa (anti-cegueira temporal).
```
/estimativa integrar gateway novo no serviço de cobrança
```

---

## 🏛️ Engenharia & arquitetura

### `/analisa`
Doc técnica **de fora** → trade-offs, problemas, soluções (ótica fintech).
```
/analisa ./docs/design-antifraude.md
/analisa https://spec-do-vendor
```

### `/revisa`
Crítica **do que eu escrevi** (código/ADR/texto).
```
/revisa            ← cola o código/texto depois, ou passa o arquivo
```

### `/pr`
Review de PR contra checklist fintech (idempotência, segurança, testes).
```
/pr                ← analisa o diff da branch atual
```

### `/adr`
Esqueleto de Architecture Decision Record.
```
/adr usar outbox pattern pra publicar eventos de pagamento
```

### `/case`
Guia o take-home de LLM Engineering por etapas.
```
/case
```

### `/estudo`
Aula guiada + exercício + quiz. Conecta ao teu contexto.
```
/estudo idempotência
/estudo consenso raft
```

---

## 📡 Atualização

### `/engenheiro`
Radar-canhão. **Tema livre** ou varredura geral.
```
/engenheiro                 ← varre 10 áreas da tua stack
/engenheiro spring ai       ← mergulho fundo num tema
```

### `/brief`
Briefing semanal enxuto (5 áreas).

### `/ia`
Só ferramentas de IA em alta, com selo hype/adotado.

### `/radar`
Disciplina de fontes (regra do 3x, tempo fixo).
```
/radar event sourcing
```

---

## 🏆 Carreira

### `/conquistas`
Brag doc acumulado (`conquistas.md`) pra promoção a staff.
```
/conquistas reduzi p99 do serviço de saldo de 800ms pra 120ms
/conquistas resumo          ← puxa pra avaliação/1:1
```

---

## 🔁 Combos do dia

**Manhã**
```
/planodia → estrutura o dia
```
**Travou no meio**
```
/foco → próxima ação
```
**Cabeça cheia / ansioso**
```
/descarrega → esvazia
```
**Antes da daily**
```
/standup
```
**Fim do dia**
```
/notas (o que aprendi/decidi) + /conquistas (o que entreguei)
```
**Não sei o que usar**
```
/qualskill <situação>
```

---

## 🛠️ Manutenção

**Editei uma skill (na fonte) e quero ativar:**
```bash
cp -r "./skills/"* "~/.claude/skills/"
```
Depois reinicia o Claude Code.

**Versionar mudança:**
```bash
cd "."
git add . && git commit -m "descrição da mudança"
```

**Faxina mensal:** apaga skill não usada em 30 dias. Skill custa contexto mesmo sem disparar. Remove a pasta em `~/.claude/skills/<nome>` + na fonte.

---

## ❓ Problemas comuns

| Sintoma | Causa | Fix |
|---|---|---|
| `/skill` não aparece | Claude não reescaneou | Fecha e reabre o Claude Code |
| `/plugin não reconhecido` | Rodou no PowerShell | Slash command é no **chat**, não no terminal |
| Editei e não mudou | Editou a fonte, não a global | Re-sincroniza (ver Manutenção) |
| Skill errada dispara | Descrição ambígua | Chama pelo `/nome` exato |

---

## 📂 Estrutura

```
skill-engineering-tdah/
├── .claude-plugin/
│   ├── plugin.json
│   └── marketplace.json
├── skills/            ← 30 skills (fonte)
├── README.md          ← índice curto
└── GUIA.md            ← este guia
```
Ativas em: `~/.claude/skills/` (cópia sincronizada).
