---
name: retomar
description: Recupera o contexto de "onde eu parei" depois de uma interrupção ou troca de tarefa. Eu descrevo o que estava fazendo (ou passo minhas notas) e ele reconstrói: objetivo, o que já fiz, o próximo passo exato, e o que eu tinha na cabeça. Cura a perda de fio do TDAH ao trocar de contexto.
---

# /retomar — Onde eu parei

Depois de interrupção/troca de contexto, TDAH perde o fio: "o que eu tava fazendo mesmo?". Eu te passo os cacos, você reconstrói o estado e me devolve o **próximo passo exato**.

## Quem sou eu
- Engenheiro backend sênior. TEA/TDAH/dislexia.
- Interrupção apaga meu contexto de trabalho. Volto e fico perdido, às vezes recomeço do zero. Preciso de reentrada rápida.

## Dois modos

### Guardar antes de sair (`/retomar salvar ...`)
Antes de trocar de tarefa, capturo o estado pra retomar depois. Registre em `retomar.md` (append):
```
## <tarefa> — HH:MM
- objetivo: ...
- já fiz: ...
- próximo passo: ...
- na cabeça: (a dúvida/ideia que eu tava segurando)
- arquivos: ...
```

### Retomar (`/retomar` ou `/retomar <tarefa>`)
1. Se existe `retomar.md`, leia a última entrada da tarefa. Senão, me pergunte 2-3 coisas rápidas (o que fazia? último passo que lembra?).
2. Reconstrua o estado e me dê o **próximo passo único** pra voltar ao ritmo.

## Formato da saída (retomar)
```
## 🔄 Você estava: <tarefa>
- **Objetivo:** ...
- **Já feito:** ...
- **Você tinha na cabeça:** ... (a dúvida/ideia pendente)

## 👉 Próximo passo (volte por aqui)
[ação única, pequena, pra reentrar no fluxo]

## 📂 Contexto
arquivos / links / onde estava.
```

## Regras duras
- Devolva **um** próximo passo, pequeno — reentrada, não o plano todo.
- Recupere "o que eu tinha na cabeça" — é o que mais se perde e trava a volta.
- Se não há registro nem memória, ofereça `/quebra` pra reconstruir do zero.
- Curto e direto. Objetivo: voltar ao trabalho em <2 min.
