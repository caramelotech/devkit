# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## O que é este repositório

Coleção de **skills**, **agents** e **plugins** reutilizáveis para desenvolvimento de software. As skills seguem o padrão do repositório [anthropics/skills](https://github.com/anthropics/skills) e podem ser registradas como plugins no Claude Code.

## Estrutura

- `skills/` - Cada skill em sua própria pasta com um arquivo `SKILL.md`. O frontmatter YAML declara `name` (kebab-case) e `description` (inglês, usado para triggering).
- `agents/` - Orquestradores que combinam múltiplas skills. Cada agente tem seu próprio `README.md` descrevendo fluxo de execução, inputs e outputs.
- `plugins/` - Integrações com ferramentas externas (`vscode/`, `mcp/`). Cada plugin tem seu próprio `README.md` com instruções de instalação.
- `templates/` - Templates base para criar novos itens (`skill.md`, `agent.md`, `plugin.md`).
- `.claude-plugin/marketplace.json` - Registro das skills como plugins para o Claude Code.

## Convenções

- Nomes de arquivos e diretórios em `kebab-case`.
- Toda nova skill fica em `skills/<nome-da-skill>/SKILL.md`.
- O frontmatter de cada `SKILL.md` deve ter `name` (kebab-case em inglês) e `description` (inglês).
- O corpo do `SKILL.md` pode estar em pt-BR; exemplos de código devem estar em inglês.
- Agents devem declarar: tipo (autônomo ou assistido), skills utilizadas, ferramentas necessárias, fluxo de execução e tabela de inputs/outputs.
- Plugins devem declarar: plataforma, versão mínima, dependências, instalação e configuração.
- Ao adicionar uma nova skill, registre-a também em `.claude-plugin/marketplace.json`.

## Relação entre itens

Agents orquestram skills - ao criar ou modificar um agent, verifique quais skills ele referencia em `skills/`. O agent `code-reviewer` combina `skills/code-review` com `skills/owasp-check` como exemplo de composição.
