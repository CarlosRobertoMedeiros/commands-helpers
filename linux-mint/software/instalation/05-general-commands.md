# 📘 Comandos Clássicos do Linux vs Novos Comandos

**Autor:** Carlos Roberto  
**Referência:** Diolinux  
**Data de criação:** 09/11/2025  
**Última atualização:** 09/11/2025  
**Versão:** 1.0  
**Testado e homologado em:** Linux Mint 22.2 Zara x64  

---

## 🧭 Acesso rápido ao Terminal
**Atalho:** `Ctrl + Alt + T`

---

## 01️⃣ `man`, `help`, `tldr`
Tradicionalmente, os comandos `man` e `help` são usados para exibir manuais.  
O `tldr` é uma versão moderna e simplificada, mantida pela comunidade.

```bash
sudo apt install tldr        # Instala o tldr
man ls                       # Manual tradicional do comando ls
help ls                      # Manual detalhado
tldr ls                      # Manual resumido e com exemplos práticos
```

---

## 02️⃣ `ifconfig` → `ip a`
O comando `ifconfig` foi substituído por `ip`, que já vem por padrão nas distros modernas.

```bash
ip a                         # Lista as interfaces e endereços IP
tldr ip                      # Mostra as opções principais do comando ip
ip addr show                 # Mostra os endereços configurados
ip route                     # Exibe as rotas de rede
```

---

## 03️⃣ `apt-get` → `apt`
O `apt-get` ainda funciona, mas foi substituído pelo `apt`, que é mais simples e interativo.

```bash
apt update                   # Atualiza a lista de pacotes
apt upgrade                  # Atualiza os pacotes instalados
apt show <nomePacote>        # Mostra detalhes do pacote
apt search <nomePacote>      # Pesquisa por um pacote
```

---

## 04️⃣ `ls` → `exa` / `eza`
Os comandos `exa` (ou `eza` no Mint) trazem listagens mais coloridas, organizadas e modernas.

```bash
sudo apt install eza
eza -l                       # Substitui o ls -l
```

---

## 05️⃣ `df` → `ncdu`
O `ncdu` analisa o uso de disco de forma interativa e visual.

```bash
sudo apt install ncdu
ncdu                         # Analisa e lista diretórios por tamanho
```
💡 **Dica:** Execute na raiz `/` para ver todo o sistema — ótimo para liberar espaço em disco.

---

## 06️⃣ `df -h` → `duf`
O `duf` oferece uma visualização moderna e colorida dos pontos de montagem.

```bash
sudo apt install duf
duf
```

---

## 07️⃣ `nslookup` → `dig`
O `dig` é uma alternativa moderna para consultas DNS, com mais detalhes técnicos.

```bash
nslookup google.com
dig google.com
```
📝 **Observação:** o `dig` exibe mais informações, mas alguns usuários preferem a simplicidade do `nslookup`.

---

## 08️⃣ `find` → `fdfind`
O `fdfind` (ou `fd`) é uma alternativa mais rápida e intuitiva ao `find`.

```bash
sudo apt install fd-find
find ./ -name "*arch*"       # Tradicional
fdfind arch                  # Simplificado e mais eficiente
```

---

## 09️⃣ `top` → `bashtop`
O `bashtop` é uma interface visual e interativa para monitorar processos.

```bash
sudo apt install bashtop
bashtop                      # Abre a interface
# Pressione F para filtrar ou Ctrl + C para sair
```

---

## 🔟 `cat` → `batcat`
O `batcat` (do pacote `bat`) exibe arquivos com destaque de sintaxe e numeração de linhas.

```bash
sudo apt install bat
batcat arquivo.txt           # Exibe conteúdo de forma colorida e organizada
```

---

## 11️⃣ `grep` → `ripgrep (rg)`
O `ripgrep` (`rg`) é uma alternativa moderna ao `grep`, mais rápida e com melhor legibilidade.

```bash
sudo apt install ripgrep
ip a | grep inet             # Tradicional
ip a | rg inet               # Resultado mais limpo e colorido
```

---

## 12️⃣ `nano` → `micro`
O `micro` é um editor de terminal moderno, simples e com atalhos familiares.

```bash
sudo apt install micro
micro arquivo.txt
```

🧩 **Atalhos úteis:**
- **Ctrl + S:** Salvar  
- **Ctrl + Q:** Sair  

---

## 📎 Resumo Final

O Linux moderno vem substituindo ferramentas clássicas por alternativas:
- ⚡ **Mais rápidas**  
- 👀 **Mais legíveis**  
- 🧠 **Com melhor integração com sistemas atuais**  

Essas melhorias aumentam a produtividade e tornam a experiência de terminal mais agradável.

---

---

## 🔗 Referências úteis

- [Diolinux — Ferramentas modernas de terminal](https://diolinux.com.br/)
- [Ubuntu Packages — ripgrep](https://packages.ubuntu.com/search?keywords=ripgrep)
- [Ubuntu Packages — ncdu](https://packages.ubuntu.com/search?keywords=ncdu)
- [Ubuntu Packages — bashtop](https://packages.ubuntu.com/search?keywords=bashtop)
- [Ubuntu Packages — bat](https://packages.ubuntu.com/search?keywords=bat)
- [Ubuntu Packages — micro](https://packages.ubuntu.com/search?keywords=micro)
- [Ubuntu Packages — fd-find](https://packages.ubuntu.com/search?keywords=fd-find)
- [Ubuntu Packages — duf](https://packages.ubuntu.com/search?keywords=duf)
- [TLDR Pages — tldr.sh](https://tldr.sh/)



