# CO-STAR e técnicas de prompting para código

## CO-STAR

| Letra | Campo | Pergunta-guia | Exemplo |
|---|---|---|---|
| C | Contexto | Qual o ambiente, stack, arquitetura e propósito do módulo? | "Backend Python 3.11 com FastAPI e Pydantic; API RESTful de usuários." |
| O | Objetivo | Qual a tarefa exata, sem ambiguidade? | "Função `is_valid_email(str) -> bool`." |
| S | Estilo | Que padrões, convenções e princípios seguir? | "PEP 8, tipagem estática, docstrings Google." |
| T | Tom | Como devem soar mensagens e documentação? | "Mensagens de erro amigáveis ao usuário final." |
| A | Audiência | Quem vai ler/usar? | "Revisado por devs júnior → autoexplicativo." |
| R | Resposta | Qual o formato da saída? | "Apenas o código e um exemplo de uso." |

Prompt fraco: "Melhore este código."
Prompt forte: Contexto + Objetivo + Estilo + Resposta explícitos, com o código anexado.

## Técnicas complementares

- **Few-shot**: dê pares exemplo entrada → saída do padrão desejado.
- **Chain-of-thought**: peça o raciocínio em passos ("1. identifique responsabilidades; 2. separe em funções; 3. refatore; 4. gere o código final").
- **Otimização da janela de contexto**: forneça só os arquivos relevantes para a tarefa.
- **Prompting iterativo**: rascunho → revisão → feedback → refinamento, em etapas pequenas.

## Prompts-modelo por etapa

**Arquitetura (Mermaid)**
> Contexto: [stack e componentes]. Objetivo: diagrama de componentes em Mermaid mostrando frontend, backend (controller/service/repository) e banco. Estilo: identifique as setas de comunicação. Resposta: apenas o código Mermaid.

**Testes**
> Contexto: [função]. Objetivo: suíte pytest cobrindo caso válido, zeros/limites, entradas inválidas que devem levantar `ValueError`. Estilo: nomes descritivos, asserções claras. Resposta: apenas o código dos testes.

**Debugging**
> Recebi `[erro completo + stack trace]` na linha N de `arquivo`. Cenário: [o que levou ao erro]. Explique a causa raiz provável e como depurar; depois sugira uma correção.

**Commit**
> Contexto: alterei [arquivos] para [mudanças]. Objetivo: mensagem em Conventional Commits. Resposta: apenas a mensagem.
