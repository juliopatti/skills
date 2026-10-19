# {{NOME}}

Briefing: `docs/BRIEF.md` · Arquitetura: `docs/ARCHITECTURE.md`

## Comandos
- `make install` · `make run` · `make test` · `make format`

## Convenções de código
- {{linguagem/versão}}, {{guia de estilo}}, tipagem estática, docstrings {{formato}}.
- Camadas: {{controller → service → repository}}. Uma responsabilidade por função/classe (SRP).
- DRY: extraia lógica duplicada para utilitários; nomes semânticos e consistentes.
- Configuração e segredos apenas por variáveis de ambiente (12-Factor). Nunca commitar `.env`.

## Fluxo de trabalho
- Novas funcionalidades em TDD: teste falhando (red) → código mínimo (green) → refatorar mantendo testes verdes.
- Rode `make test` antes de cada commit.
- Commits em Conventional Commits (`feat`, `fix`, `docs`, `chore`, `refactor`, `test`), pequenos e frequentes.
- Atualize `CHANGELOG.md` e a seção "Como a IA acelerou este projeto" do README conforme o projeto evolui.

## Revisão de código gerado por IA
Antes de considerar uma mudança pronta, verifique:
1. Entendo cada linha? Se não, explique antes de seguir.
2. Atende aos requisitos funcionais e não funcionais do briefing?
3. Segurança: injeção (SQL/prompt), XSS, credenciais expostas, validação de entrada, dependências desatualizadas (OWASP Top 10 para LLM).
4. Segue as convenções acima?
5. Foi executado e testado?

## Debugging
Diante de um erro: use a mensagem completa e o stack trace, explique a causa raiz primeiro, depois proponha a correção.

## Não fazer
- Inventar bibliotecas, métodos ou versões — confirme na documentação.
- Ampliar o escopo além do MVP; registre ideias em "Limitações e próximos passos".
