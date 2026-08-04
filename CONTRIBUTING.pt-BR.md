# Contribuindo

🌐 🇬🇧 [English](CONTRIBUTING.md) · 🇧🇷 **Português**

Obrigado por querer ajudar! Este kit existe pra tornar o dia de engenharia mais leve pra quem é neurodivergente (TDAH, TEA, dislexia). Contribuições são bem-vindas — skills novas, melhorias, traduções, correções.

## Princípio central

Toda skill deve ser **estruturada, escaneável e direta** — o oposto de parede de texto. Se a saída da skill cansaria alguém com dislexia ou faria alguém com TDAH perder o foco, ela precisa melhorar.

Regras de estilo pra qualquer skill:
- Títulos + listas, **nunca** parágrafos longos.
- Sempre explicar o **"por que importa"**, não só o "o quê".
- Terminar com **uma** ação concreta quando fizer sentido.
- Reduzir carga cognitiva e paralisia de decisão — menos opções, mais clareza.

## Como adicionar uma skill

1. Crie a pasta `skills/<nome>/` com um arquivo `SKILL.md`.
2. O `SKILL.md` começa com frontmatter YAML:
   ```yaml
   ---
   name: nome-da-skill
   description: Uma frase clara e específica (até ~200 caracteres). É o que dispara a skill e vira o comando /nome-da-skill.
   ---
   ```
3. No corpo, escreva as instruções que o Claude deve seguir. Inclua:
   - **Quem sou eu** (persona/contexto — mantenha genérico e editável)
   - **Como agir** (passos)
   - **Formato da saída** (estruturado)
   - **Regras duras** (o que nunca fazer)
4. Teste localmente copiando pra `~/.claude/skills/` e reiniciando o Claude Code.
5. Atualize a contagem e a lista no `README.md` e no `GUIA.md`.

## Padrões

- **Sem dados pessoais.** Nada de nomes reais, empresas, emails, caminhos absolutos de máquina, tokens ou senhas. Use persona genérica e caminhos como `~/.claude/...`.
- **Persona editável.** A seção "Quem sou eu" tem um padrão (engenheiro backend), mas deixe claro que o usuário adapta pro contexto dele.
- **Idioma.** O kit é PT-BR hoje. Traduções (EN) são muito bem-vindas — mantenha a estrutura.
- **Uma skill = uma capacidade.** Não empacote cinco coisas numa skill só.

## Fluxo de PR

1. Fork + branch (`feat/nome-da-skill` ou `fix/...`).
2. Faça a mudança seguindo os padrões acima.
3. Rode uma verificação rápida de dados pessoais antes de commitar:
   ```bash
   grep -rni "seu-nome\|sua-empresa\|@gmail\|C:/Users" .
   ```
4. Abra o PR descrevendo **qual dor de neurodivergência** a mudança ataca.

## Ideias de contribuição

- Tradução EN das skills.
- Skills novas pra outras dores (ex: transição de hiperfoco, gestão de energia).
- Variantes de persona pra outras stacks (front, dados, mobile, SRE).
- Exemplos e templates de saída.

## Código de conduta

Seja gentil. Este projeto lida com neurodivergência — respeito e acessibilidade vêm primeiro, em código e em conversa.
