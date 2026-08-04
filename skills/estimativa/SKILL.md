---
name: estimativa
description: Sanity-check de estimativa de tempo/esforço de uma tarefa. Quebra em partes, considera incerteza e o que costumo esquecer (testes, review, deploy, imprevisto), e dá uma faixa realista. Compensa a "cegueira temporal" do TDAH que me faz subestimar.
---

# /estimativa — Estimativa realista

Me ajuda a estimar tempo/esforço sem cair na cegueira temporal do TDAH (sempre acho que é rápido). Quebra, adiciona o que eu esqueço, e dá uma **faixa**, não um número mágico.

## Quem sou eu
- Backend sênior, fintech, rumo a arquitetura/staff.
- TDAH: subestimo tempo cronicamente. Esqueço testes, review, deploy, imprevisto, context-switch.
- Preciso dar estimativa em sprint/planning sem me enrolar depois.

## Como agir
1. Pego a tarefa (`/estimativa integrar gateway X no serviço de pagamento`).
2. **Quebre** em sub-partes (implementação, testes, review, integração, deploy, doc).
3. Some o que costumo esquecer:
   - ⏱️ testes (unit + integração)
   - 👀 code review + ajustes
   - 🚀 deploy + validação
   - 🔀 context-switch / interrupções
   - ❓ incerteza / imprevisto (buffer)
4. Dê **faixa** (otimista → realista → pessimista), não ponto único.
5. Liste as **premissas** e o que aumentaria o prazo.

## Formato da saída
```
# ⏳ Estimativa: <tarefa>

## Quebra
| Parte | Esforço |
|---|---|
| implementação | ... |
| testes | ... |
| review + ajuste | ... |
| deploy + validação | ... |
| buffer incerteza | ... |

## 🎯 Faixa
Otimista: X · **Realista: Y** · Pessimista: Z

## 📌 Premissas
- ... (se furarem, o prazo muda)

## 🚩 O que pode estourar o prazo
- dependência externa, ambiguidade, aprovação, etc.

## 💬 O que comunicar no planning:
a faixa + a maior incerteza. Nunca só o número otimista.
```

## Regras duras
- Sempre **faixa**, nunca número único — incerteza é honestidade.
- Sempre inclua testes/review/deploy/buffer — é o que TDAH esquece.
- Aponte a maior fonte de incerteza explicitamente.
- Comunique realista, não otimista. Subestimar quebra confiança.
