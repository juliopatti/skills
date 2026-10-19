---
name: iniciar-projeto
description: Inicia um novo projeto de software assistido por IA seguindo as boas práticas do laboratório AKCIT — briefing CO-STAR, MVP enxuto, arquitetura mínima com Mermaid, Git com .gitignore e Conventional Commits, scaffold testável (Makefile, testes, README completo) e um CLAUDE.md que mantém as convenções vivas durante todo o projeto. Use quando o usuário pedir para criar, iniciar, começar ou montar um projeto novo.
argument-hint: "[ideia do projeto em uma frase]"
disable-model-invocation: true
---

# Iniciar projeto (padrão AKCIT)

Ideia inicial informada: $ARGUMENTS

Siga as fases **em ordem**. Não pule para código antes de concluir as fases 1 e 2.
Ao fim de cada fase, mostre ao usuário o que foi produzido e só avance após confirmação.

## Fase 1 — Briefing CO-STAR e validação do MVP

1. Monte o briefing preenchendo os 6 campos do CO-STAR (detalhes em `references/co-star.md`).
   Pergunte apenas o que não puder ser inferido da ideia inicial — no máximo uma rodada de perguntas:
   - **C**ontexto: domínio, stack, arquitetura geral, propósito
   - **O**bjetivo: o que o MVP faz (funcionalidades em verbos, sem ambiguidade)
   - **S**tyle: linguagem/versão, guia de estilo (ex.: PEP 8), formato de docstring, princípios (SOLID)
   - **T**om: tom de mensagens de erro e documentação
   - **A**udiência: quem usa e quem mantém o código (ex.: devs júnior → código autoexplicativo)
   - **R**esposta: entregáveis esperados (API, CLI, UI, relatório...)
2. Valide o escopo contra os critérios de MVP e aponte os que falham:
   - Escopo limitado e claro (cabe em ~30h de trabalho)
   - Potencial de uso de IA em várias etapas (código, testes, docs, refatoração)
   - Stack com a qual o usuário já tem familiaridade
   - Relevância pessoal
   - Testável automaticamente
3. Escreva `docs/BRIEF.md` a partir de `templates/BRIEF.md`.

## Fase 2 — Arquitetura mínima

1. Defina módulos, dependências e fluxo de dados (entrada → processamento → saída).
   Para back-ends, prefira camadas `controller` → `service` → `repository`.
2. Gere um diagrama **Mermaid** de componentes e uma árvore de pastas proposta.
3. Liste dependências essenciais **com versão fixada**. Verifique versões reais
   (registro de pacotes / documentação) — nunca invente versões ou bibliotecas.
4. Registre tudo em `docs/ARCHITECTURE.md`, incluindo uma seção "Decisões" com
   alternativas consideradas e o motivo da escolha.

## Fase 3 — Repositório Git

Ordem obrigatória:
1. `git init` e `git branch -M main`.
2. Criar `.gitignore` **antes** de qualquer `git add`, organizado por seção
   (linguagem, ferramentas, IDE `.vscode/ .idea/`, `.env`/`.env.*`, arquivos do SO).
3. Criar `.env.example` com as variáveis necessárias (sem valores reais).
   Segredos sempre via variáveis de ambiente.
4. Primeiro commit: `feat: estrutura inicial do projeto e setup básico`.
5. Daqui em diante, todo commit segue **Conventional Commits**:
   `<tipo>[escopo]: <descrição imperativa>` — tipos `feat`, `fix`, `docs`, `chore`,
   `refactor`, `test`. Commits pequenos e frequentes contam a evolução do projeto.
6. Não criar repositório remoto nem dar push sem o usuário pedir.

## Fase 4 — Scaffold

Crie o esqueleto respeitando a árvore da fase 2:
- Arquivo de dependências (`requirements.txt`/`pyproject.toml`, `package.json`...).
- `Makefile` (ou scripts equivalentes) com no mínimo: `install`, `run`, `test`, `format`.
- Pasta de testes com **um teste real passando** (ex.: um teste de fumaça do núcleo).
- Modelos de entrada/saída do núcleo (ex.: Pydantic / interfaces TypeScript) com tipagem e docstrings.
- `README.md` a partir de `templates/README.md` (seções vazias marcadas com TODO, nunca inventadas).
- `LICENSE` (pergunte qual; sugira MIT se não houver preferência).
- `CHANGELOG.md` no formato Keep a Changelog.
- `CLAUDE.md` do projeto a partir de `templates/CLAUDE.md`, preenchido com a stack e comandos reais.

Rode `make install` e `make test` e mostre a saída. Faça commits por bloco lógico
(`chore: adiciona Makefile`, `test: adiciona teste de fumaça`, `docs: adiciona README inicial`...).

## Fase 5 — Entrega da fase de setup

Mostre ao usuário:
- Árvore final de arquivos.
- Resultado de `make test`.
- `git log --oneline`.
- Próximo passo sugerido: primeira funcionalidade do núcleo via TDD (red → green → refactor).

Lembre que `references/checklist-entrega.md` deve ser revisado antes da submissão final.

## Regras gerais (valem para todas as fases)

- IA acelera, não substitui revisão humana: explique decisões não óbvias, não despeje código sem contexto.
- Nunca use bibliotecas, métodos ou versões sem confirmar que existem.
- Nunca grave segredos no código, em commits ou em exemplos.
- Prefira simplicidade: só o necessário para o MVP. Registre ideias extras em "Limitações e Próximos Passos".
