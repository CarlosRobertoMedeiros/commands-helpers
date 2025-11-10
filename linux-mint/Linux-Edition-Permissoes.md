# 🐧 Comandos Essenciais para o Terminal Linux

Este guia apresenta comandos úteis para o terminal Linux, incluindo o uso dos editores **Vi/Vim** e **Nano**, manipulação de arquivos, compressão, scripts e variáveis de ambiente.

---

## 📝 Editores de Texto no Linux: Vi/Vim e Nano

### 🧭 Comandos do Vi Agrupados por Categoria
1. **Navegação**  
2. **Inserção de Texto**  
3. **Edição de Texto**  
4. **Pesquisa e Substituição**  
5. **Salvar e Sair**  
6. **Modos Visuais**

---

## 🔍 Comandos de Navegação no Vi/Vim

| Comando | Descrição | Exemplo de Uso |
|----------|------------|----------------|
| `h` | Move o cursor para a esquerda | Pressione `h` várias vezes para mover o cursor para trás. |
| `l` | Move o cursor para a direita | Pressione `l` várias vezes para mover o cursor para frente. |
| `j` | Move o cursor para baixo | Pressione `j` para descer uma linha. |
| `k` | Move o cursor para cima | Pressione `k` para subir uma linha. |
| `0` | Vai para o início da linha | Pressione `0` para ir ao início da linha. |
| `^` | Vai ao primeiro caractere não vazio da linha | Pressione `^` para ignorar espaços e ir ao primeiro caractere. |
| `$` | Vai para o final da linha | Pressione `$` para ir ao final da linha. |
| `gg` | Vai para o início do arquivo | Digite `gg` para ir à primeira linha. |
| `G` | Vai para o final do arquivo | Digite `G` para ir à última linha. |
| `Ctrl + d` | Rola metade da tela para baixo | Use para avançar rapidamente. |
| `Ctrl + u` | Rola metade da tela para cima | Use para retroceder rapidamente. |

---

## ✍️ Uso do Vi – Modo Inserção

```bash
vi                  # Abre o editor Vi
i                   # Entra no modo de inserção para digitar texto
Esc                 # Sai do modo de inserção
:w <arquivo>        # Salva o texto inserido (exemplo: :w arquivo.txt)
:q                  # Sai do editor
:q!                 # Sai sem salvar
vi <arquivo>        # Abre um arquivo específico
A                   # Move o cursor para o final da linha para inserir texto
yy                  # Copia a linha atual
o                   # Cria uma nova linha abaixo
p                   # Cola a linha copiada
dd                  # Recorta (deleta) a linha atual

:/Windows           # Pesquisa a palavra "Windows"
:s/Windows/Unix/    # Substitui a primeira ocorrência de "Windows" por "Unix"
:s/Cachorro/Cao/g   # Substitui todas as ocorrências de "Cachorro" por "Cão" (global)
:x                  # Salva e sai do editor
```

---

## ⚙️ Comandos Úteis Fora do Modo de Inserção

```bash
wc <arquivo>          # Mostra estatísticas: linhas, palavras e caracteres
uniq <arquivo>        # Remove duplicidades no conteúdo
uniq -D <arquivo>     # Exibe apenas as linhas duplicadas
uniq -c <arquivo>     # Conta o número de ocorrências de cada linha
uniq --help           # Exibe ajuda sobre o comando uniq

sort <arquivo>        # Ordena o conteúdo em ordem alfabética
head -c 200 <arquivo> # Exibe os 200 primeiros caracteres
tail -n 2 <arquivo>   # Exibe as 2 últimas linhas
tail -c 100 <arquivo> # Exibe os 100 últimos caracteres
```

---

## 📦 Compactação e Descompactação de Arquivos

### ZIP
```bash
zip -r diretorio.zip diretorio  # Compacta um diretório completo (recursivo)
less diretorio.zip              # Exibe informações do arquivo compactado
unzip diretorio.zip             # Descompacta o conteúdo
unzip -q diretorio.zip          # Descompacta em modo silencioso
```

### TAR/GZ
```bash
tar -czf diretorio.tar.gz diretorio  # Compacta o diretório em formato .tar.gz
less diretorio.tar.gz                # Visualiza informações do arquivo compactado
tar -xzf diretorio.tar.gz            # Descompacta o conteúdo
tar -xzf relatorio.tar.gz && ls      # Descompacta e lista os arquivos
```

---

## ⚡ Automação com Scripts

```bash
touch script.sh       # Cria um novo script
chmod +x script.sh    # Concede permissão de execução
./script.sh           # Executa o script
bash script.sh        # Outra forma de executar o script
```

---

## 🌱 Variáveis de Ambiente

```bash
echo $PATH                         # Exibe os diretórios do PATH
export PATH=$PATH:/home/roberto    # Adiciona um novo caminho ao PATH
```

---

## 🛠️ Instalação de Ambientes e Serviços

```bash
sudo apt install mysql-server  # Instala o MySQL Server
systemctl status mysql         # Verifica o status do serviço MySQL
```

---

📚 **Dica:**  
Use o comando `man <comando>` (ex: `man tar`) para acessar o manual completo de cada utilitário Linux diretamente no terminal.

---

🧑‍💻 _Autor: Carlos Roberto_  
📅 _Atualizado em: Novembro de 2025_
