# devkit

Repositório de skills, agents e plugins para desenvolvimento de software. As skills seguem a estrutura do repositório [anthropics/skills](https://github.com/anthropics/skills) e podem ser instaladas como plugins no Claude Code.

## Estrutura

```
devkit/
├── skills/                  # Uma pasta por skill, cada uma com SKILL.md
│   ├── code-review/
│   ├── unit-test-generator/
│   ├── commit-message/
│   ├── dockerfile-review/
│   └── owasp-check/
├── agents/                  # Agentes que orquestram múltiplas skills
│   ├── code-reviewer/
│   ├── test-generator/
│   └── doc-writer/
├── plugins/                 # Integrações com ferramentas externas
│   ├── vscode/
│   └── mcp/
├── templates/               # Templates para criar novos itens
└── .claude-plugin/
    └── marketplace.json     # Registro para uso como plugin no Claude Code
```

## Skills disponíveis

| Skill | Categoria | Descrição |
| ----- | --------- | --------- |
| [`code-review`](skills/code-review/SKILL.md) | development | Revisão de código com foco em bugs, segurança, performance e legibilidade |
| [`unit-test-generator`](skills/unit-test-generator/SKILL.md) | testing | Geração de testes unitários cobrindo caminho feliz, borda e erros |
| [`commit-message`](skills/commit-message/SKILL.md) | writing | Mensagens de commit seguindo Conventional Commits |
| [`dockerfile-review`](skills/dockerfile-review/SKILL.md) | devops | Revisão de Dockerfiles com foco em segurança e boas práticas |
| [`owasp-check`](skills/owasp-check/SKILL.md) | security | Análise de vulnerabilidades baseada no OWASP Top 10 |

## Como usar

### Como plugin no Claude Code

Registre o repositório como plugin para ter acesso às skills diretamente no Claude Code:

```bash
# Instalar todas as skills como plugin
claude mcp add devkit /caminho/para/devkit
```

### Como contexto manual

Copie o conteúdo de um `SKILL.md` e use como contexto em qualquer LLM:

```bash
# Exibir uma skill
cat skills/code-review/SKILL.md
```

### Agents

Os agents combinam múltiplas skills para tarefas complexas. Cada um tem seu próprio `README.md` com instruções detalhadas:

- [`code-reviewer`](agents/code-reviewer/README.md) - Revisão completa: qualidade + segurança
- [`test-generator`](agents/test-generator/README.md) - Geração de suite de testes para um módulo
- [`doc-writer`](agents/doc-writer/README.md) - Geração de documentação técnica

## Como contribuir

1. Use os templates em `templates/` como ponto de partida
2. Toda nova skill vai em `skills/<nome>/SKILL.md`
3. O frontmatter do `SKILL.md` deve ter `name` e `description` em inglês
4. O corpo pode ser em pt-BR; exemplos de código devem estar em inglês
5. Registre a nova skill em `.claude-plugin/marketplace.json`
6. Siga `kebab-case` para nomes de arquivos e diretórios
