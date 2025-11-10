# COMANDOS Para Serem Usados no Terminal Linux📣

## COMANDOS VI - Editor Linux e Nano📣
	
**NIVEIS DE CONFIGURACAO DO USUARIO GIT** (Ordem hierarquica Local, Global, System):
- **SISTEMA(--system)** : Afeta todos os usuarios e repositorios da maquina(/etc/gitconfig).
- **GLOBAL(--global)** : Afeta todos os repositorios para o usuario atual(.gitconfig) de cada usuario.
- **LOCAL (--local)** :	Afeta somente o repo git onde a configuracao e feita(.git/config).
	
	
**Comandos do Vi Agrupados por Categoria**:
1. Navegacao. 
2. Insercao de Texto.
3. Edicao de Texto. 
4. Pesquisa e Substituicao.
5. Salvar e Sair
6. Modos Visuais


## Comandos para Navegacao

Comando	Descrição	Exemplo de Uso
h	Move o cursor para a esquerda	Pressione h várias vezes para mover o cursor para trás.
l	Move o cursor para a direita	Pressione l várias vezes para mover o cursor para frente.
j	Move o cursor para baixo	Pressione j para descer uma linha.
k	Move o cursor para cima	Pressione k para subir uma linha.
0	Move para o início da linha	Em qualquer posição, pressione 0 para ir ao início da linha.
^	Move para o primeiro caractere não vazio da linha	Pressione ^ para ignorar espaços em branco e ir ao primeiro caractere.
$	Move para o final da linha	Pressione $ para ir ao final da linha.
gg	Move para o início do arquivo	Digite gg para ir à primeira linha.
G	Move para o final do arquivo	Digite G para ir à última linha do arquivo.
Ctrl + d	Rola metade da tela para baixo	Use Ctrl + d para avançar rapidamente.
Ctrl + u	Rola metade da tela para cima	Use Ctrl + u para retroceder rapidamente.



	
## UTILIZACAO DO VI CONFIGURACOES MODO INSERCAO
```bash
vi # Comando utilizado para acessar o editor
digitar i # Dentro do editor de texto a letra i coloca o editor de texto em modo de insercao para escrever o que for necessario
tecla esc # Sai do modo edicao
digita :w <filename> # Salva o texto que foi inserido no editor exemplo :w arquivo.txt
digita :q # Sai do editor 
digita :q! # Sai do editor sem salvar
vi <filename> # Abre o editor com o arquivo indicado ex: vi arquivo.txt
digita A # No texto ao posicionar em uma linha essa letra move para o ultimo caractere da linha

pressiona yy # Copia a linha do cursor que esta piscando
pressiona o # Cria uma nova linha
pressiona p # Cola a linha que foi copiada

pressiona dd # Recorta a linha do cursor que esta piscando

Esc :/Windows # Pesquisa dentro do arquivo a palavra Windows e posiciona o cursor na primeira ocorrencia
Esc :s/Windows/Unix/ # Substitui todas as ocorrencias dentro do arquivo da palavra Windows por Unix
Esc :s/Cachorro/Cao/g :x # Substitui todas as ocorrencias dentro do arquivo da palavra Cachorro por Cao de maneira global em seguida salva  e sai

```

## CONFIGURACOES MODO NAO INSERCAO
```bash
wc <filename> # Exibe algumas estatisticas do arquivo Ex: 13 32 230  = 13 linhas, 32 palavras, 230 caracteres 
uniq <filename> # Exibe o conteudo do arquivo removendo as duplicidades dentro das linhas
uniq -D <filename> # Exibe o conteudo do arquivo que e duplicado
uniq -c <filename> # Exibe o conteudo do arquivo e cria um contador dizendo quantas vezes cada linha foi encontrada
unique --help # Qualquer comando podemos usar o help para listar tudo

sort <filename> # Ordena pra mim em ordem alfabetica o conteudo do arquivo
head -c 200 <filename> # Lista os 200 primeiros caracteres para o filename
tail -n 2 <filename> # Mostras as ultimas 2 linhas do arquivo
tail -c 100 <filename> # Mostras os ultimos 100 caracteres do arquivo 
```

## COMPACTACAO DE ARQUIVOS
```bash
zip -r directory.zip directory # Compacta com zip o diretorio com todos os arquivos(r - recursive) e coloca em um arquivo chamado diretory.zip
less directory.zip # Permite verificar detalhes do do directory.zip
unzip directory.zip # Descompacta os arquivos dentro do diretorio atual
unzip -q directory.zip # Descompacta os arquivos dentro do diretorio atual sem mostrar nada no prompt


tar -czf directory directory.tar.gz # Compacta com o tar o diretorio com todos os arquivos e voloca em um arquivo chamado direcoty.tar.gz Create Zip File(czf)
less directory.tar.gz # Permite verificar detalhes do directory.tar.gz
tar -xzf directory.tar.gz # Descompacta os arquivos dentro do diretorio atual Extract Zip File(xzf)
tar -xzf relatorio.tar.gz && ls # Descompacta o arquivo e lista os arquivos no diretorio atual
```

## ESCREVENDO UM SCRIPT AUTOMATIZACAO DE TAREFAS
```bash
touch filename.sh     # Criar um Script o nome deve ser 
chmod +x filename.sh  # Dar a permissao de Execucao para os U/G/Others
./filename.sh         # Executar o que o arquivo script faz
bash filename.sh      # Executar o que o arquivo script faz mesma coisa do ./filename.sh
```

## VARIAVEIS DE AMBIENTE NO Linux
```bash
echo $PATH  # Lista todos os arquivos que estao na variavel de ambiente
export PATH=$PATH:/home/roberto # Adiciono ao Path do Linux uma variavel que aponta para home/roberto
```

## INSTALACAO DE AMBIENTES
```bash
sudo apt install mysql-server # Instala o mysql-server no seu linux
systemctl status mysql # Verifica status do servico
```