# Conventional Commits Guide

## Visão Geral

O Conventional Commits é uma especificação para adicionar significado legível por humanos e máquinas às mensagens de commit.

**Formato:** `<type>[optional scope]: <description>\n\n[optional body]\n\n[optional footer(s)]`

## Tipos de Commit

| Tipo | Descrição | Exemplo |
|------|-----------|---------|
| `feat` | Uma nova funcionalidade | `feat: add color setting` |
| `fix` | Correção de bug | `fix: correct typo in README` |
| `docs` | Apenas mudanças na documentação | `docs: update installation instructions` |
| `style` | Mudanças que não afetam o significado do código (espaços em branco, formatação, ponto e vírgula ausente, etc) | `style: format code with prettier` |
| `refactor` | Uma mudança de código que não corrige um bug nem adiciona uma funcionalidade | `refactor: simplify function logic` |
| `perf` | Uma mudança de código que melhora a performance | `perf: optimize database query` |
| `test` | Adicionando testes ausentes ou corrigindo testes existentes | `test: add unit tests for user authentication` |
| `build` | Mudanças que afetam o sistema de build ou dependências externas | `build: update webpack configuration` |
| `ci` | Mudanças nos arquivos de configuração e scripts do CI | `ci: add new GitHub Actions workflow` |
| `chore` | Outras mudanças que não modificam arquivos src ou test | `chore: update .gitignore` |

## Escopo (Scope)

O escopo fornece informações contextuais adicionais sobre as mudanças.

### Exemplos de Escopo:
- `feat(api): add rate limiting`
- `fix(ui): resolve button alignment issue`
- `docs(auth): update login flow documentation`

## Descrição

### Regras para Descrição:
- Use o modo imperativo na descrição
- Comece com letra minúscula
- Não termine com ponto
- Mantenha curto e conciso

### Exemplos:
| ✅ Bom | ❌ Ruim |
|---------|---------|
| `add new user authentication` | `added new user authentication` |
| `fix button alignment issue` | `Fixed button alignment issue.` |

## Corpo (Body)

O corpo fornece uma explicação detalhada das mudanças.

### Regras para o Corpo:
- Separe da descrição com uma linha em branco
- Use o modo imperativo
- Quebre texto em 72 caracteres
- Explique o problema e a solução

## Rodapé (Footer)

Usado para informações adicionais como mudanças que quebram compatibilidade ou referências de issues.

### Regras para o Rodapé:
- Separe do corpo com uma linha em branco
- Pode incluir múltiplos rodapés
- Rodapés comuns: BREAKING CHANGE, closes #issue-number, etc.

### Exemplos de Rodapé:
- `BREAKING CHANGE: The user API has been completely restructured`
- `closes #1234`
- `fixes #5678`

## Mudanças que Quebram Compatibilidade (Breaking Changes)

### Formato:
- `BREAKING CHANGE: <description>`
- Ou use `!` após o tipo/escopo: `feat!: change API structure`

### Exemplos:
- `feat(api)!: change authentication method`
- `BREAKING CHANGE: Users must now provide API key`

## Exemplos Práticos

### Simples:
- `feat: add new user authentication`
- `fix: resolve login issue`
- `docs: update installation guide`

### Com Escopo:
- `feat(api): add rate limiting`
- `fix(ui): resolve button alignment issue`
- `docs(auth): update login flow documentation`

### Com Breaking Change:
- `feat(api)!: remove deprecated methods`
- `BREAKING CHANGE: removes support for v1 API`

### Com Referência de Issue:
```
fix: resolve memory leak in data processing

closes #1234
```

## Benefícios

- ✅ Gerar changelogs automaticamente
- ✅ Determinar mudanças de versão semântica automaticamente
- ✅ Comunicar a natureza das mudanças para colegas de equipe
- ✅ Disparar processos de build e publicação

## Ferramentas Recomendadas

- **commitizen** - Ferramenta para commits padronizados
- **cz-cli** - Interface de linha de comando para commitizen
- **husky + @commitlint** - Hooks de Git para validação de commits
- **standard-version** - Geração automática de changelogs e versionamento

## Aplicação no Projeto IoT Volkswagen

Para o projeto Atlas da Volkswagen, recomenda-se o uso de escopos específicos:

- `feat(iot): add sensor data collection`
- `fix(dashboard): resolve real-time data display`
- `docs(architecture): update IoT system documentation`
- `test(sensors): add unit tests for data validation`

---

*Este guia garante que todos os commits do projeto sigam um padrão consistente e profissional, facilitando a manutenção e colaboração da equipe.*
