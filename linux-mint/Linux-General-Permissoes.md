# 🛡️ Permissões de Arquivos e Diretórios no Linux

No Linux, as permissões de acesso a **arquivos** e **diretórios** são fundamentais para manter a **segurança**, **privacidade** e **controle** do sistema.  
Elas determinam **quem pode ler, modificar ou executar** um arquivo e **quem pode acessar** um diretório.

---

## 📂 Estrutura das Permissões

As permissões são organizadas em **três grupos de usuários**:

| Grupo | Descrição |
|--------|------------|
| **Usuário (Owner)** | É o dono do arquivo ou diretório. |
| **Grupo (Group)** | Representa usuários pertencentes ao mesmo grupo do arquivo. |
| **Outros (Others)** | Todos os demais usuários do sistema. |

Cada grupo pode possuir **três tipos de permissões**:

| Permissão | Letra | Descrição |
|------------|--------|------------|
| **Leitura** | `r` | Permite visualizar o conteúdo de um arquivo ou listar os itens de um diretório. |
| **Escrita** | `w` | Permite modificar o arquivo ou adicionar/remover arquivos em um diretório. |
| **Execução** | `x` | Permite executar o arquivo (se for um programa/script) ou acessar o diretório. |

---

## 🔍 Visualizando Permissões

As permissões podem ser visualizadas com o comando:

```bash
ls -l
```

Exemplo de saída:

```text
-rwxr-xr--
```

Explicação:

| Posição | Significado | Exemplo |
|----------|-------------|----------|
| 1º caractere | Tipo de arquivo (`-` = arquivo, `d` = diretório) | `-` |
| 2º–4º | Permissões do usuário | `rwx` |
| 5º–7º | Permissões do grupo | `r-x` |
| 8º–10º | Permissões de outros | `r--` |

Nesse exemplo:
- **Usuário:** `rwx` → leitura, escrita e execução  
- **Grupo:** `r-x` → leitura e execução  
- **Outros:** `r--` → apenas leitura  

---

## ⚙️ Alterando Permissões com `chmod`

O comando **`chmod`** (change mode) é usado para modificar permissões.  
Existem **dois modos** principais de uso:

---

### 🔤 Modo Simbólico

Permite ajustar permissões usando **letras**.

**Sintaxe:**
```bash
chmod [ugoa][+-=][rwx] arquivo_ou_diretório
```

**Significados:**
- `u`: usuário (owner)
- `g`: grupo
- `o`: outros
- `a`: todos (user + group + others)
- `+`: adiciona permissão
- `-`: remove permissão
- `=`: define permissão exata

**Exemplos:**
```bash
chmod u+x script.sh    # adiciona execução ao dono
chmod g-w relatorio.txt # remove escrita do grupo
chmod o=r dados.log     # apenas leitura para outros
```

---

### 🔢 Modo Octal (Numérico)

Cada permissão recebe um **valor numérico**:

| Permissão | Valor |
|------------|--------|
| Leitura (`r`) | 4 |
| Escrita (`w`) | 2 |
| Execução (`x`) | 1 |

A soma define as permissões de **usuário**, **grupo** e **outros**, nesta ordem.

**Exemplo:**
```bash
chmod 755 script.sh
```

Significa:
- Usuário: `7 = 4 + 2 + 1` → `rwx`
- Grupo: `5 = 4 + 0 + 1` → `r-x`
- Outros: `5 = 4 + 0 + 1` → `r-x`

---

## ⭐ Permissões Especiais

Além das permissões básicas, há **três bits especiais**:

| Bit | Nome | Efeito | Uso Comum |
|------|------|---------|------------|
| **Setuid (s)** | Executa o programa com as permissões do dono. | Binários de sistema, como `/usr/bin/passwd` |
| **Setgid (s)** | Arquivos herdam o grupo do diretório. | Diretórios compartilhados |
| **Sticky bit (t)** | Impede que usuários removam arquivos de outros. | Diretórios como `/tmp` |

Exemplo:
```bash
chmod +t /public
```

---

## 🧩 Exemplos Comuns de Permissões

| Comando | Descrição |
|----------|------------|
| `chmod 644 arquivo` | Dono pode ler e escrever; grupo e outros apenas ler. |
| `chmod 755 script.sh` | Dono pode ler, escrever e executar; grupo e outros podem ler e executar. |
| `chmod 777 arquivo` | Todos podem ler, escrever e executar (**não recomendado**). |

---

## 🧠 Conclusão

O modelo de permissões do Linux é a **base da segurança do sistema**.  
Ele garante que apenas **usuários autorizados** possam acessar, alterar ou executar arquivos, protegendo o sistema contra falhas e acessos indevidos.

> 🔒 **Dica:** Use permissões restritivas sempre que possível e evite o uso de `chmod 777`, pois ele remove todas as barreiras de segurança.

---
