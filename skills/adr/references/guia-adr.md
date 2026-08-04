# Guia rápido de ADR

## O que é
Architecture Decision Record: um registro curto e datado de **uma** decisão de arquitetura significativa, seu contexto e suas consequências. É imutável — se a decisão muda, cria-se um novo ADR que substitui o anterior.

## Quando escrever um ADR
Escreva quando a decisão:
- É cara ou difícil de reverter (escolha de banco, padrão de integração, fronteira de serviço).
- Afeta múltiplos times ou o contrato entre eles.
- Tem trade-off não óbvio que alguém vai questionar depois ("por que não usaram X?").
- Envolve confiabilidade, segurança ou regulação.

**Não** escreva ADR pra: escolha trivial, detalhe de implementação local, algo facilmente reversível.

## Statuses
- **proposto** — em discussão.
- **aceito** — decidido e em vigor.
- **descartado** — considerado e rejeitado (ainda vale registrar por quê).
- **substituído por ADR-XXX** — havia um ADR, uma decisão nova o troca. Nunca edite o antigo; aponte pro novo.
- **obsoleto** — não se aplica mais, sem substituto.

## Erros comuns (evite)
- **Só a decisão, sem alternativas** — vira anotação, não ADR. As opções descartadas são metade do valor.
- **Vender a decisão** — esconder as consequências negativas destrói a confiança no documento. Seja honesto sobre o custo.
- **Contexto raso** — sem as restrições/requisitos, o leitor futuro não entende por que a escolha fazia sentido.
- **Editar ADR aceito** — decisão mudou? Novo ADR. O histórico é o ponto.
- **ADR gigante** — se passa de 1-2 telas, provavelmente são várias decisões; separe.

## Marcas de um bom ADR
- Dá pra ler em 2 minutos daqui a 1 ano e entender o "porquê".
- Um cético consegue ver que as alternativas foram consideradas de verdade.
- Diz o que **monitorar** e **quando revisitar** — liga a decisão à realidade de produção.

## Numeração e local
- Sequencial: ADR-001, ADR-002...
- Local convencional: `docs/adr/ADR-NNN-titulo-em-kebab.md`.
- Um índice em `docs/adr/README.md` ajuda (lista + status).
