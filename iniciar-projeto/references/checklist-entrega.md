# Checklist de entrega

- [ ] Repositório público e acessível; nenhum arquivo essencial barrado pelo `.gitignore`
- [ ] Nenhuma credencial no código **nem no histórico** do Git (`git log -p | grep -i -E "key|secret|token|password"`)
- [ ] Credenciais carregadas de variáveis de ambiente / `.env` (ignorado); `.env.example` presente
- [ ] Histórico com ≥ 5–10 commits significativos em Conventional Commits
- [ ] Arquivo de dependências completo com versões fixadas
- [ ] Testes automatizados presentes, executáveis e passando; instruções no README
- [ ] README com: título/descrição, tecnologias (incl. modelos e assistentes de IA), pré-requisitos, instalação, uso com exemplos (curl/CLI/prints/GIF), testes, estrutura, "Como a IA acelerou este projeto", "Limitações e Próximos Passos", créditos e licença
- [ ] Markdown do README renderizando corretamente no GitHub
- [ ] Branch `main` limpa (sem WIP nem arquivos temporários)
- [ ] `LICENSE` presente
- [ ] `CHANGELOG.md` atualizado
- [ ] Release/tag criada (ex.: `v1.0.0`)
