# COMANDOS GIT 📣


## DESCRICOES DIVERSAS
	
**NIVEIS DE CONFIGURACAO DO USUARIO GIT** (Ordem hierarquica Local, Global, System):
- **SISTEMA(--system)** : Afeta todos os usuarios e repositorios da maquina(/etc/gitconfig).
- **GLOBAL(--global)** : Afeta todos os repositorios para o usuario atual(.gitconfig) de cada usuario.
- **LOCAL (--local)** :	Afeta somente o repo git onde a configuracao e feita(.git/config).
	
	
**ETAPAS**:
1. Workspace "Codigo onde Trabalhamos" (`git add`). 
2. Staging Area ou Index (`git commit`).
3. Local Repository / (`git push origin <branch>`). 
4. Remote Repository.
	
## CONFIGURACOES DIVERSAS
```bash
git config --list   # Lista todas as configuracoes disponiveis no seu git, mostrando as cofigs(Local, Global e System)
git config --system --edit  # Edita valores do arquivo de configuracao do sistema

git config --global --edit  # Edita valores do arquivo .gitconfig de configuracao do usuario
git config --global core.editor code --wait # Edita o arquivo .gitconfig do usuario usando o editor vscode = code --wait
git config --global core.editor /<path>/idea.sh --wait  # Edita o arquivo .gitconfig do usuario usando o editor Intelij = /opt/intellij-idea/bin/idea.sh --wait
git config --local --edit   # Edita o arquivo .gitconfig do projeto local, normalmente pouco usado
```

**CRIACAO DE ALIAS**:
```bash
logf = !git log --oneline --decorate --all --graph  # Cria a ref [alias] no arquivo .gitconfig onde ao chamar logf ele emula todo o comando
commit = !git add --all & git commit -m	    # Cria a ref [alias] no arquivo .gitconfig onde ao chamar commit ele emula todo o comando
llog = !git log --pretty=format:'%C(yellow)%h %C(red)%d %C(white)%s - %C(cyan)%cn, %C(green)%cr'    # Monta uma visualizacao mais elegante no arquivo .gitconfig
```

## COMANDOS GERAIS
```bash
git version     # Verifica se o Git esta instalado

git config --global user.name <Nome>    # Configura para todos os repositorios criados localmente os dados do nome do usuario
git config --global user.email <Email>  # Configura para todos os repositorios criados localmente os dados do email do usuario
git config --global --edit      # Incluir no [core] editor = code, caso contrario a interface do vscode nao interage com o git 
git config user.name <Nome>     # Configura para o repositorio especifico localmente os dados do nome do usuario
git config user.email <Email>   # Configura para o repositorio especifico localmente os dados do email do usuario
```

## COMANDOS LOCAIS
```bash
git init    # Cria um repositorio local vazio em um diretorio no seu computador

git add     # Adiciona o arquivo na stage area
git add <file-name>     # Adiciona o arquivo com filename <filename> na stage area
git add .   # Adiciona todos os arquivo na stage area
										
git status      # Mostra o status do repositorio local
git status -s   # Mostra o status do repositorio local resumido
```

### Link para Doc de Commits: https://www.conventionalcommits.org/en/v1.0.0/
  
```bash
git commit -m "chore: add Oyster build script"  # Salva as alteracoes no repositorio local
git commit -m "docs: explain hat wobble"    # Salva as alteracoes no repositorio local
git commit -m "feat: add beta sequence"     # Salva as alteracoes no repositorio local
git commit -m "fix: remove broken message"  # Salva as alteracoes no repositorio local
git commit -m "refactor: share logic between XX"    # Salva as alteracoes no repositorio local
git commit -m "style: convert tabs to spaces"   # Salva as alteracoes no repositorio local
git commit -m "test: ensure Lay retains clothing"   # Salva as alteracoes no repositorio local
git commit --amend -m "test: change clothing"   # Substitui localmente o ultimo commit, permitindo a edicao da mensagem em caso de erro na escrita da mensagem
git commit --amend --no-edit    # Substitui localmente o ultimo commit, sem permitir a edicao da ultima mensagem

git log     # Mostra o Log Comparando o repositorio local com o repositorio remoto
git log --oneline --decorate --all--graph   # Mostra o Log Comparando o repositorio local com o repositorio remoto em visao de arvore

git branch  # Visualizar todas as branches no repositorio local
git branch -a   # Visualizar todas as branches no repositorio local e no repositorio remoto
git branch -d <nome>    # Exclui uma branch no repositorio local
git push origin --delete <remote-branch>    # Sample feat/xxxx Exclui uma branch no repositorio remoto

git checkout <branch_name>  # Navega entre as Branches
git checkout -b <branch_name>   # Cria uma nova branch (feature/release/fix) a partir da Branch que esta
git checkout -b <branch_name> origin/<branch_name>  # Cria uma nova branch (<branch_name>) a partir da branch no repo remoto
git checkout <file-name> .  # Em um arquivo trackeado, na workspace ele desfaz a mudanca
git checkout <hash-commit>  # Investiga o codigo em uma branch DESCONECTADA para atualizar tem que criar uma nova branch a partir desta
git checkout <tag-name>     # Investiga o codigo em uma branch DESCONECTADA para atualizar a Tag tem que criar uma nova branch a partir desta

git clean -n    # Lista os arquivos na Workspace que podem ser removidos
git clean       # Remove Arquivos na Workspace nao traqueados porem da erro devido a seguranca do git
git clean -f    # Remove os arquivos na Workspace que vao ser removidos
git clean -nd   # Lista os arquivos na Workspace que estao dentro de diretorios para remocao
git clean -d    # Remove os arquivos na Workspace que estao dentro de diretorios recursivamente

git rm          # Apaga arquivos na stage area e ao realizar o push exclui no repo remoto, criando uma nova linha no flow
git rm <diretorio> -f   # Apaga o diretorio na stage area e ao realizar o push exclui no repo remoto, criando uma nova linha no flow
git rm <file-name> --cached # O arquivo vai passar a nao ser mais gerenciado pelo git (o <file> foi incluido no .gitIgnore)
git rm -r --cached <diretorio>  # O diretorio vai passar a nao ser mais gerenciado pelo git (o <diretorio> foi incluido no .gitIgnore) apagando do repositorio remoto

git diff origin <remote-repo>   # Demonstra a diferenca entre os arquivos do repositorio local e o repositorio remoto

git restore . # Restaura todos os arquivos que se encontram na workspace ao estado inicial antes de qualquer alteracaoo no o (.) indica o ctrl+z no diretorio atual
git restore --staged <filename> # Restaura todos os arquivos que se encontram na stage ao estado da workspace

git blame <filename> # Mostra a sequencia de quem realizou as ultimas alteracoes no arquivo
```	

### Tipos de Merge


| Tipos de Merge            | Historico     | Cenario Ideal  							  			|
|---------------------------|---------------|-------------------------------------------------------|
|1. Fast-Forward			| Linear		| Quando a branch de destino esta "a frente" 			|
|2. Commit de Merge			| Nao Linear	| Mesclar branches divergentes com historico completo 	|
|3. Squash Merge			| Linear		| Manter o historico limpo com um unico commit 			|
|4. Merge Manual			| Depende		| Resolver conflitos manualmente 						|
|5. Rebase Merge			| Linear		| Historico linear e limpo sem commits de merge			|
|6. Octopus Merge			| Nao Linear	| Mesclar multiplas branches simultaneamente			|

```bash
git merge <repo-feature-implementada>   # Mescla para o repositorio que se encontra os codigos do repositorio da feature implementada

git reset --soft    # Desfaz as mudancas em um repo git, mantendo os arquivos na stage area ou index
git reset --mixed   # Desfaz as mudancas em um repo git, mantendo os arquivos na workspace "Esse e o default"
git reset --hard    # Desfaz as mudancas em um repo git, sem manter arquivos na workspace nem na stage area ou index

git reset HEAD~1 --soft     # Desfaz as mudancas em um repo git voltando um HASH do git log, mantendo os arquivos na stage area ou index  
git reset HEAD~1 --mixed    # Desfaz as mudancas em um repo git voltando um HASH do git log, mantendo os arquivos na workspace "Esse e o default"
git reset HEAD~1 --hard     # Desfaz as mudancas em um repo git voltando um HASH do git log, sem manter arquivos na workspace nem na stage area ou index

git reset <hash-commit> --soft      # Desfaz as mudancas em um repo git voltando para o HASH-COMMIT do git log, mantendo os arquivos na stage area ou index  
git reset <hash-commit> --mixed     # Desfaz as mudancas em um repo git voltando para o HASH-COMMIT do git log, mantendo os arquivos na workspace "Esse e o default"
git reset <hash-commit> --hard      # Desfaz as mudancas em um repo git voltando para o HASH-COMMIT do git log, sem manter arquivos na workspace nem na stage area ou index

git revert <hash-commit>    # Desfazer um commit no Git, criando um novo commit, mantendo o historico, OBS Os arquivos com conflito ficam com UU no seu status
git revert HEAD~1
git revert HEAD~1 --no-edit		# Desfez criando um novo commit, aproveitando a mensagem anterior com revert no inicio 
git revert HEAD~1 --no-commit	# Desfez e coloca na staging area para eu digitar a mensagem do novo commit, fazendo com que eu mantenha o padrao de nomes

git cherry-pick <commit-hash>	# "Copiar" um commit especifico de um branch e aplica ele em outro, sem precisar fazer um merge completo
	
git reflog  # Mostra todas as alteracoes no projeto
```

### Stash **Área de armazenamento de codigo local fora do Git flow, para momentaneamente resolver outros problemas**
```bash
git stash clear     # Limpar o stash 
git stash save      # Criar uma entrada no stash cotendo os arquivos
git stash push -m "Mensagem" # Cria uma entrada no stash com uma mensagem personalizada
git stash apply* Olhar o pop    # Traz de volta os arquivos
git stash apply stash@{1}       # Traz de volta os arquivos da referencia daquele stash
git stash list      # Lista os arquivos no Stash 
git stash drop      # Exclui o stash
git stash pop       # Aplicar o stash e remover o valor que estava no stash(esconderijo)
git stash branch    # Criar uma branch a partir do stash
```

### Tags **Tags Anotadas(Tem descricao) e Tags Leves(Apenas marcam)**
### Link para Doc de Semantic Version: https://semver.org/
```bash
git tag -a v1.0.0 -m "feat: Func Implementadas" # Gera a Tag, lembrando que o rotuno tem que ser a partir de uma branch
git tag     # Mostra todas as tags
git show v1.0.0     # Mostra detalhes da tag
git tag -a "0.1.beta" -m "release 0.1.beta" <hash-commit>	# Cria o rotulo para a versao 0.1 realizada no commit <hash-commit>
git push origin v1.0.0  # Envia a tag local para o repositorio remoto
git push origin --tags # Envia todas as tags do repo local para o repo remoto
git tag -d "v1.0.0"     # Remove a Tag Localmente
git push --delete origin tag -d "v1.0.0"    # Remove a Tag Remotamente
git tag -v v1.0.0 # Mostra as informacoes dessa tag especificamente somente para tags anotadas
```
	
## COMANDOS REMOTOS
```bash
git remote add origin <url>	# Adiciona url do repositorio Remoto no diretorio local
git remote -v   # Lista a Url do repositorio Remoto
git clone <remote-repo> # Clona o repositorio remoto

git fetch       # Atualizar sua copia do repo com as mudancas do repo remoto, sem mesclar as alteracoes com sua branch local
git fetch --all     # Atualizar toda sua copia com todas as branches do repo com as mudancas do repo remoto, sem mesclar as alteracoes com sua branch local
git pull origin <remote-branch>     # Como git fetch, porem mescla as alteracoes com sua branch local
git pull --rebase origin <remote-branch>    # Como git fetch, porem mescla as alteracoes do repo remoto primeiro depois as minhas em caso de conflito
git rebase -- continue  # Ao resolver o conflito continue para evoluir na solucao
```
###	Rebase Iterativo **Muito Util**
```bash
git rebase -i HEAD~4    # Retorna 4 commits Mantem o Pick com o commit que vai prevalecer e os outros 3 com squash, na proxima tela eu edito a mensagem
git rebase -i HEAD~4    # Retorna 4 commits Mantem o Pick com o commit que vai prevalecer e os outros 3 com fixedUp, nao edita a mensagem 	

git push origin --delete <remote-branch>    # Exclui uma branch remota no repositorio
git push origin <remote-branch> # Enviar as alteracoes a partir do seu repositorio local para o repositorio remoto

git merge <repo-feature-implementada>   # Mescla para o repositorio que se encontra os codigos do repositorio da feature implementada
```

## Git Flow Exemplo de Utilizacao
### Link https://medium.com/trainingcenter/utilizando-o-fluxo-git-flow-e63d5e0d5e04
```bash    	
git checkout -b feat/<feature-name> # Cria a feature branch a partir da developer

git checkout developer  # Troco para a branch developer
git merge feat/<feature-name>   # Realiza o merge da feat/<feature-name> na developer (Olhar depois casos de PR)

git checkout developer  # Cria a release a partir da developer  
git checkout -b release/1.0.0
git push origin release/1.0.0

git tag -a v1.0.0 -m "feat: Func Implementadas"
git push origin v1.0.0  # Cria a Tag

git checkout main
git merge release/1.0.0 # Realiza o Merge da Tag na Main
```

## Demonstrar o ChangeLog

### Link: https://github.com/CarlosRobertoMedeiros/commands-helpers/blob/main/Changelog.md

