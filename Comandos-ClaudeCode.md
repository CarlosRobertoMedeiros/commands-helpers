# Guia de comandos - Claude Code

> Referência prática para usar o **Claude Code** no terminal e manter no repositório Git privado.
>
> **Importante:** os comandos disponíveis podem variar conforme a versão instalada, o sistema operacional e as configurações do projeto. Confira sempre `claude --help` no terminal e `/help` dentro de uma sessão.

## 1. Instalação e primeiros passos

Instale o Claude Code seguindo as instruções oficiais:
- Documentação: https://docs.anthropic.com/en/docs/claude-code/overview
- Configuração: https://docs.anthropic.com/en/docs/claude-code/setup

Depois da instalação, confira a versão e a ajuda:

```bash
claude --version
claude --help
```

Entre na pasta do projeto e inicie uma sessão:

```bash
cd caminho/do/repositorio
claude
```

Na primeira utilização, siga o fluxo de autenticação apresentado pelo programa.

## 2. Comandos de terminal (CLI)

Estes são exemplos comuns. Use `claude --help` para confirmar opções suportadas pela sua versão.

| Comando | Para que serve |
|---|---|
| `claude` | Inicia uma sessão interativa. |
| `claude "explique a arquitetura deste projeto"` | Inicia uma sessão com uma solicitação inicial. |
| `claude --help` | Exibe opções e ajuda da CLI. |
| `claude --version` | Mostra a versão instalada. |
| `claude -p "resuma este projeto"` | Executa uma solicitação em modo não interativo e imprime a resposta. |
| `claude -c` | Tenta continuar a conversa mais recente no diretório atual. |
| `claude -r` | Abre o fluxo para retomar uma conversa anterior. |
| `claude update` | Atualiza a instalação, quando esse comando estiver disponível no método de instalação utilizado. |

> Consulte a ajuda local antes de usar opções adicionais ou automatizar comandos em scripts.

## 3. Comandos de barra dentro da sessão

Digite os comandos abaixo **dentro da sessão do Claude Code**, geralmente começando com `/`. A lista é uma referência; alguns comandos podem mudar entre versões ou depender de recursos habilitados.

| Comando | Uso típico |
|---|---|
| `/help` | Mostra os comandos e a ajuda disponíveis. |
| `/clear` | Limpa o contexto da conversa atual e inicia uma nova conversa na sessão. |
| `/compact` | Resume/compacta o contexto para liberar espaço, quando disponível. |
| `/config` | Abre ou altera configurações interativas. |
| `/doctor` | Ajuda a diagnosticar problemas de instalação/configuração, se disponível. |
| `/cost` | Exibe informações de uso/custo quando suportado pelo ambiente. |
| `/status` | Mostra informações de estado da sessão e do ambiente. |
| `/model` | Consulta ou seleciona o modelo, conforme as opções disponíveis. |
| `/permissions` | Consulta ou gerencia permissões de ferramentas, se disponível. |
| `/memory` | Ajuda a consultar ou gerenciar instruções/memória do projeto, conforme a versão. |
| `/login` | Inicia ou atualiza a autenticação, se disponível. |
| `/logout` | Encerra a autenticação da sessão, se disponível. |
| `/review` | Solicita uma revisão de código, quando disponível. |
| `/pr-comments` | Trabalha com comentários de pull request em ambientes compatíveis, se disponível. |
| `/ide` | Gerencia integração com IDE, quando suportada. |
| `/terminal-setup` | Ajuda a configurar recursos de terminal, se disponível. |
| `/vim` | Alterna um modo de edição estilo Vim, quando suportado. |

**Como conferir a lista exata:** inicie `claude` e execute `/help`.

## 4. Exemplos de solicitações úteis

Estas frases são **prompts**, não comandos de barra. Digite-as normalmente na conversa.

### Entender um repositório

```text
Analise a estrutura deste repositório e explique os principais módulos,
as dependências e o fluxo principal da aplicação. Não altere arquivos.
```

### Criar documentação

```text
Analise o projeto e proponha um README.md com pré-requisitos,
configuração local, execução, testes e estrutura de diretórios.
Antes de editar, apresente um plano.
```

### Implementar uma funcionalidade

```text
Analise os padrões arquiteturais existentes e implemente [funcionalidade].
Respeite o estilo do projeto, adicione ou atualize testes e explique
quais arquivos serão alterados antes de começar.
```

### Revisar código

```text
Revise as alterações atuais procurando bugs, riscos de segurança,
problemas de concorrência, tratamento de erros e falta de testes.
Priorize os achados por severidade e cite os arquivos/linhas.
Não modifique os arquivos.
```

### Investigar uma falha

```text
Investigue a causa provável de [erro]. Siga o fluxo de execução,
consulte os testes e logs disponíveis e apresente evidências.
Não aplique mudanças até explicar a causa e a correção proposta.
```

### Criar testes

```text
Identifique os cenários críticos de [classe/módulo] e proponha testes
unitários e de integração alinhados às convenções existentes.
Não reduza a cobertura nem remova testes para fazer a suíte passar.
```

## 5. Instruções persistentes do projeto: `CLAUDE.md`

O arquivo `CLAUDE.md` pode registrar contexto e regras que o Claude Code deve seguir ao trabalhar no projeto. Crie-o na raiz do repositório:

```text
meu-repositorio/
├── CLAUDE.md
├── README.md
├── src/
└── ...
```

Exemplo inicial:

```markdown
# Instruções do projeto

## Objetivo
Descreva aqui o propósito do sistema e seus principais domínios.

## Arquitetura
- Respeite a arquitetura e os padrões já adotados.
- Antes de introduzir uma biblioteca, explique a necessidade.
- Evite misturar regras de negócio com infraestrutura.

## Desenvolvimento
- Siga as convenções de nomenclatura e formatação existentes.
- Prefira mudanças pequenas e focadas.
- Não altere arquivos não relacionados à tarefa.

## Qualidade
- Adicione ou atualize testes para mudanças de comportamento.
- Execute os testes e verificações pertinentes antes de concluir.
- Nunca afirme que testes passaram sem executá-los.

## Segurança
- Nunca inclua tokens, senhas, chaves privadas ou dados pessoais nos arquivos.
- Não execute comandos destrutivos sem explicar o impacto e obter confirmação.
- Não desative controles de segurança para contornar falhas.

## Fluxo de trabalho
1. Inspecione o código relevante.
2. Explique o plano para mudanças significativas.
3. Implemente a solução.
4. Execute testes e verificações.
5. Resuma arquivos alterados, decisões e limitações.
```

Adapte esse exemplo ao seu stack, comandos de build, testes e padrões reais. Não coloque segredos no `CLAUDE.md`.

## 6. Configuração e personalização

O Claude Code oferece mecanismos de configuração e personalização, que podem incluir configurações de usuário/projeto, instruções `CLAUDE.md`, skills, hooks, agentes e integrações MCP. Os caminhos e recursos exatos dependem da versão.

Antes de editar configurações:
1. Consulte a documentação oficial atual.
2. Verifique quais arquivos já existem no repositório.
3. Evite sobrescrever configurações locais sem revisar as diferenças.
4. Não versione credenciais nem arquivos que contenham dados privados.

Documentação oficial: https://docs.anthropic.com/en/docs/claude-code

## 7. Boas práticas com Git

Antes de iniciar uma tarefa:

```bash
git status
git branch --show-current
git diff
```

Depois das alterações:

```bash
git diff --check
git diff
```

Execute os comandos de build, lint e teste definidos pelo próprio projeto. Revise o diff antes de criar um commit.

- Trabalhe em uma branch apropriada.
- Revise toda alteração gerada.
- Não compartilhe tokens, chaves ou arquivos `.env`.
- Não permita que uma ferramenta faça `push`, publique releases ou execute operações destrutivas sem revisão explícita.
- Um repositório privado não elimina a necessidade de proteger segredos e dados sensíveis.

## 8. Links oficiais

- Visão geral: https://docs.anthropic.com/en/docs/claude-code/overview
- Instalação: https://docs.anthropic.com/en/docs/claude-code/setup
- Comandos interativos: https://docs.anthropic.com/en/docs/claude-code/interactive-mode
- Configurações: https://docs.anthropic.com/en/docs/claude-code/settings
- Memória e `CLAUDE.md`: https://docs.anthropic.com/en/docs/claude-code/memory
- Segurança: https://docs.anthropic.com/en/docs/claude-code/security

---

**Manutenção deste guia:** valide a tabela de comandos com `claude --help` e `/help` após atualizações importantes do Claude Code.
