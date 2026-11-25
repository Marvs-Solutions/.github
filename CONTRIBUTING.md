# Como trabalhamos na MARVS

Regras válidas para todos os repositórios da organização. Quem define e revisa estas regras é a área de Engenharia.

## Fluxo de código

Ninguém escreve direto nos repositórios da MARVS. Todo código entra por pull request vindo de um fork.

1. **Comece por uma issue.** Toda tarefa tem uma issue atribuída a você no quadro da MARVS. Sem issue atribuída, a tarefa não começa.
2. **Faça um fork** do repositório para a sua conta (só na primeira vez).
3. **Crie um branch** no seu fork a partir do `main` atualizado, com o nome `tipo/descricao-curta` (ex.: `feat/filtro-de-selecoes`, `fix/login-mobile`).
4. **Commits** no padrão Conventional Commits: tipo em inglês, descrição em português. Ex.: `feat(selecoes): adiciona filtro por status`.
5. **Abra o PR** do seu fork para o `main` do repositório da MARVS, preencha o template e cite a issue (`Closes #12`).
6. **CI** precisa passar. Workflows de PR vindo de fork só rodam depois da aprovação da Engenharia e não recebem secrets.
7. **Merge** é feito pela Engenharia depois da revisão.

### Manter o fork atualizado

```bash
git remote add upstream https://github.com/Marvs-Solutions/<repositorio>.git   # só na primeira vez
git fetch upstream
git switch main
git merge --ff-only upstream/main
git push origin main
```

## Agentes de IA

Usar agentes é permitido, dentro destas regras:

- O agente trabalha só em branch do seu fork e só abre PR. Nunca faz merge e nunca faz push no `main`.
- Um PR por issue, com até cerca de 400 linhas alteradas (sem contar lockfiles e arquivos gerados). Passou disso, divida em partes.
- Projeto novo ou mudança de arquitetura (banco, autenticação, infraestrutura, protocolo entre apps) só começa depois do desenho aprovado pela Engenharia.
- O agente não altera `.github/`, `CODEOWNERS`, `CLAUDE.md`, `AGENTS.md`, workflows de CI nem configurações de deploy, a menos que a issue peça isso.
- Quem abre o PR responde pelo código, escrito por pessoa ou por agente. Revise antes de pedir revisão.
- Informe no PR se houve uso de agente e em que parte.
- Segredos, senhas e dados de cliente nunca vão para código, prompt, log ou commit.

## Acessos

- Repositório novo é criado pela Engenharia. Peça abrindo uma issue ou no grupo.
- Tokens de acesso: só fine-grained, com prazo de validade e aprovação da Engenharia. Tokens clássicos não funcionam na organização.
- Autenticação em dois fatores é obrigatória.
