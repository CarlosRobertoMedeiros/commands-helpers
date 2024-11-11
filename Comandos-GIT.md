# COMANDOS GIT 📣


## DESCRICOES DIVERSAS
	
    NIVEIS DE CONFIGURACAO DO USUARIO GIT (Ordem hierarquica Local, Global, System)
		- SISTEMA(--system)					= Afeta todos os usuários e repositorios da maquina(/etc/gitconfig)
		- GLOBAL(--global)					= Afeta todos os repositórios para o usuario atual(.gitconfig) de cada usuario
		- LOCAL (--local)					= Afeta somente o repo git onde a configuracao e feita(.git/config)
	
	
	ETAPAS = Workspace "Codigo onde Trabalhamos" (git add) / 
			 Staging Area ou Index (git commit )/ 
			 Local Repository / (git push origin <branch>) 
			 Remote Repository
	
## CONFIGURACOES DIVERSAS
	git config --list						= Lista todas as configurações disponíveis no seu git, mostrando as cofigs(Local, Global e System)
	git config --system --edit					= Edita valores do arquivo de configuracao do sistema

	git config --global --edit					= Edita valores do arquivo .gitconfig de configuracao do usuario
	git config --global core.editor code				= Edita o arquivo .gitconfig do usuario informando que o editor sera o editor = code --wait
	git config --global core.editor code				= Edita o arquivo .gitconfig do usuario informando que o editor sera o editor = intellij-idea-community -w
	git config --local --edit					= Edita o arquivo .gitconfig do projeto local, normalmente pouco usado
	
	Criação de alias no arquio .gitconfig do usuario		= Exemplo [alias] logf = !git log --oneline --decorate --all --graph
	Criação de alias no arquio .gitconfig do usuario		= Exemplo [alias] commit = !git add --all & git commit -m
	Exemplo de alias para log					= llog = !git log --pretty=format:'%C(yellow)%h %C(red)%d %C(white)%s - %C(cyan)%cn, %C(green)%cr'
	
## COMANDOS GERAIS
	git version							= Verifica se o Git está instalado
	git config --global user.name <Nome>				= Configura para todos os repositórios criados localmente os dados do nome do usuário
	git config --global user.email <Email>				= Configura para todos os repositórios criados localmente os dados do email do usuário
	git config --global --edit					= Incluir no [core] editor = code, caso contrário a interface do vscode não interage com o git 
	git config user.name <Nome>					= Configura para o repositório específico localmente os dados do nome do usuário
	git config user.email <Email>					= Configura para o repositório específico localmente os dados do email do usuário

## COMANDOS LOCAIS
	git init							= Cria um repositório local vazio em um diretório no seu computador
	
	git add								= Adiciona o arquivo na stage área do repositório local
	git add <file-name>						= Adiciona o arquivo com filename <filename> na stage área do repositório local
	git add .							= Adiciona todos os arquivo na stage área do repositório local
	    									
	git status							= Mostra o status entre o repositório local e remoto
	git status -s							= Mostra o status entre o repositório local e remoto de maneira resumida

	### Link: https://www.conventionalcommits.org/en/v1.0.0/
  
	git commit -m "chore: add Oyster build script"			= Salva as alterações no repositório local
	git commit -m "docs: explain hat wobble"			= Salva as alterações no repositório local
	git commit -m "feat: add beta sequence"				= Salva as alterações no repositório local
	git commit -m "fix: remove broken message"			= Salva as alterações no repositório local
	git commit -m "refactor: share logic between XX"		= Salva as alterações no repositório local
	git commit -m "style: convert tabs to spaces"			= Salva as alterações no repositório local
	git commit -m "test: ensure Lay retains clothing"		= Salva as alterações no repositório local
	git commit -ammend "test: ensure Lay retains clothing"		= Substitui localmente o ultimo commit, permitindo a edição da mensagem em caso de erro
	git commit -ammend --no-edit					= Substitui localmente o ultimo commit, sem permitir a edição da última mensagem

	git log								= Mostra o Log Comparando o repositório local com o repositório remoto
	git log --oneline --decorate --all--graph			= Mostra o Log Comparando o repositório local com o repositório remoto em visão de árvore

	git branch							= Visualizar todas as branches
	git branch -d <nome>						= Exclui uma branch local
	git push origin --delete <remote-branch>			= Exclui uma branch remota no repositorio

	git checkout <branch_name>					= Navega entre as Branches
	git checkout -b <branch_name>					= Cria uma nova branch (feature/release/fix) a partir da Branch que está
	git checkout -b <branch_name> origin/<branch_name>		= Cria uma nova branch (<branch_name>) a partir da branch no repo remoto
	git checkout <file-name> .					= Em um arquivo trackeado, na workspace ele desfaz a mudança
	git checkout <hash-commit>					= Investiga o código em uma branch DESCONECTADA para aquele commit a partir do Hash se precisar resolver tem que criar um branch a partir dessa
	git checkout <tag-name>						= Investiga o código em uma branch DESCONECTADA para aquele commit a partir da Tag se precisar resolver tem que criar um branch a partir dessa
	
	git clean -n							= Lista os arquivos na Workspace que vão ser removidos
	git clean							= Remove Arquivos na Workspace não traqueados porém da erro devido a segurança do git
	git clean -f							= Remove os arquivos na Workspace que vão ser removidos
	git clean -nd							= Lista os arquivos na Workspace que estão dentro de diretórios para remoção
	git clean -d							= Remove os arquivos na Workspace que estão dentro de diretórios recursivamente
	
	git rm								= Apaga arquivos já trackeados pelo git localmente e ao realizar o push exclui no repo remoto, criando uma nova linha no flow
	git rm <diretorio> -f						= Apaga o diretorio com todos os arquivos já trackeados pelo git localmente e ao realizar o push exclui no repo remoto, criando uma nova linha no flow
	git rm <file-name> --cached					= O arquivo vai passar a não ser mais traqueado(o <file> foi incluido no .gitIgnore)
	
	git diff origin <remote-repo>					= Demonstra a diferença entre o repositório local e o repositório remoto
	
	git merge origin <repo-feature-implementada>			= Mescla para o repositorio que está os códigos do repositório de feature implementada

	git reset --soft						= Desfaz as mudanças em um repo git, mudando o histórico do commit. Obs: Não cria commits novos, apenas retorna os commits que foram alterados Mantém o histórico dos arquivos no staging e no workspace
	git reset --mixed						= Desfaz as mudanças em um repo git, mudando o histórico do commit. Obs: Não cria commits novos, apenas retorna os commits que foram alterados Remove os arquivos do staging area, mas mantém as alterações no worskpace
	git reset --hard						= Desfaz as mudanças em um repo git, mudando o histórico do commit. Obs: Não cria commits novos, apenas retorna os commits que foram alterados Apaga as alterações do staging e do workspace
	git reset HEAD~1 --soft  <HEAD~1 um hash-commit anterior> 	= Remove o Commit e volta os arquivos para a staging
	git reset HEAD~1 --mixed <HEAD~1 um hash-commit anterior> 	= Remove o Commit e volta os arquivos para a worskpace
	git reset HEAD~1 --hard  <HEAD~1 um hash-commit anterior> 	= Desfaz completamente o commit e suas mudanças
 	git reset <hash-commit> --soft
	git reset <hash-commit> --mixed(default)
	git reset <hash-commit> --hard
	
	git revert <hash-commit>					= Desfazer um commit no Git, criando um novo commit, mantendo o histórico, OBS Os arquivos com conflito ficam com UU no seu status
	git revert HEAD~1
	git revert HEAD~1 --no-edit					= Desfez criando um novo commit, aproveitando a mensagem anterior com revert no inicio 
	git revert HEAD~1 --no-commit					= Desfez e coloca na staging area para eu digitar a mensagem do novo commit, fazendo com que eu mantenha o padrão de nomes
	
	git cherry-pick <commit-hash>					= "Copiar" um commit específico de um branch e aplica ele em outro, sem precisar fazer um merge completo
		
	git reflog							= Mostra todas as alterações no projeto

	Stash(Esconderijo)						= Área de armazenamento de código local fora do git flow, para momentaneamente resolver outros problemas
	git stash clear							= Limpar o stash 
	git stash save							= Criar uma entrada no stash de arquivos
	git stash apply* Olhar o pop					= Trazer de volta os arquivos
	git stash apply stash@{1}					= Trazer de volta os arquivos da referência daquele stash
	git stash list							= Lista os arquivos no Stash 
	git stash drop							= Exclui o stash
	git stash pop							= Aplicar o stash e remover o valor que estava no stash(esconderijo)
	git stash branch						= Criar uma branch a partir do stash
	
    Tags Anotadas(Tem descrição) e Tags Leves(Apenas marcam)
	
	git tag -a v1.0.0 -m "feat: Func Implementadas"			= Gera a Tag, lembrando que o rotuno tem que ser a partir de uma branch
	git tag								= Mostra todas as tags
	git show v1.0.0							= Mostra detalhes da tag
	git tag -a "0.1.beta" -m "release 0.1.beta" <idCommit>		= Cria o rótulo para a verssão 0.1 realizada no commit <idCommit>
	git push origin v1.0.0						= Envia a tag local para o repositorio remoto
	git tag -d "v1.0.0"						= Remove a Tag Localmente
	git push --delete origin tag -d "v1.0.0"			= Remove a Tag Remotamente
	
## COMANDOS REMOTOS
	git remote add origin <url>					= Adiciona url do repositorio Remoto no diretorio local
	git remote -v							= Lista a Url do repositorio Remoto
	git clone <remote-repo>						= Clona o repositório remoto

	git fetch							= Atualizar sua copia do repo com as mudanças do repo remoto, sem mesclar as alterações com sua branch local
	git fetch --all							= Atualizar toda sua copia com todas as branches do repo com as mudanças do repo remoto, sem mesclar as alterações com sua branch local
	git pull origin <remote-branch>					= Como git fetch, porém mescla as alterações com sua branch local
	git pull --rebase origin <remote-branch>			 Como git fetch, porém mescla as alterações do repo remoto primeiro depois as minhas em caso de conflito
	git rebase -- continue						= Ao resolver o conflito continue para evoluir na solução
	
	Rebase Iterativo
	git rebase -i HEAD~4						= Retorna os 4 últimos commits
	git rebase -i HEAD~4						= Volta 4 commits da fila de execução Altera a linha do pick para a que quer mudar a descrição escrevendo reword 	
	
	O git rebase abaixo é muito Util
	git rebase -i HEAD~4						= Volta 4 commits da fila de execução Mantem o Pick com o commit que vai prevalecer e os outros 3 com squash, na proxima tela eu edito a mensagem
	git rebase -i HEAD~4						= Volta 4 commits da fila de execução Mantem o Pick com o commit que vai prevalecer e os outros 3 com fixedUp, a mensagem vem automaticamente do que deixar
	
	git push origin --delete <remote-branch>			= Exclui uma branch remota no repositorio
	git push origin <remote-branch>					= Enviar as alterações a partir do seu repositório local para o repositorio remoto

	git merge <branch_com_a_mudanca>				= A partir da branch local, realiza uma mesclagem enviando os dados da branch com mudança para a que não tem

## GIT FLOW EXEMPLO DE UTILIZAÇÃO 
	Link: https://medium.com/trainingcenter/utilizando-o-fluxo-git-flow-e63d5e0d5e04
    	
	git checkout -b feat/<feature-name>				= Cria a feature branch a partir da developer
    
	git checkout developer
	git merge feat/<feature-name>					= Realiza o merge da feat/<feature-name> na developer (Olhar depois casos de PR)

	git checkout developer						= Cria a release a partir da developer  
	git checkout -b release/1.0.0
	git push origin release/1.0.0

  
	git tag -a v1.0.0 -m "feat: Func Implementadas"
	git push origin v1.0.0						= Cria a Tag

  
	git checkout main
	git merge release/1.0.0						= Realiza o Merge da Tag na Main
	
  ## OLHAR FUTURAMENTE O CHANGELOG
