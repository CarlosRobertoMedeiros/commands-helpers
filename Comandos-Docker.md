# 🐳 Comandos Docker — Guia Prático

Este documento reúne os principais comandos utilizados no **Docker**, organizados por contexto e função, com exemplos comentados.

---

## 🔐 Comandos no Repositório

Login e manipulação de imagens no Docker Hub:

```bash
docker login
docker search ubuntu                          # Procura uma imagem
docker search ubuntu --filter is-official=true # Mostra apenas imagens oficiais
docker commit <id|apelido> nomeimagem          # Cria imagem a partir de um container
docker pull ubuntu                             # Baixa uma imagem
docker push carlosmedeiroslima/hello-docker:0.0.1-SNAPSHOT  # Envia imagem para o Docker Hub
docker image history <ID_ou_NomeDaImagem>      # Exibe histórico de camadas da imagem
```

---

## 🏗️ Construção de Builds e Tags

```bash
docker build --tag=carlosroberto/wildfly-18-admin .      # Cria imagem a partir do Dockerfile
docker tag hello-docker:0.0.1-SNAPSHOT carlosmedeiroslima/hello-docker:latest  # Cria nova tag
```

---

## ⚙️ Comandos Básicos

### ▶️ Executar Containers

```bash
docker run --rm -it --name test alpine:latest /bin/sh       # Executa container interativo
docker run -it -p 8080:8080 nginx                           # Roda Nginx na porta 8080
docker run -d -p 8080:8080 minhaapp                         # Roda em background
docker run nome_da_imagem                                   # Cria container padrão
docker run -it ubuntu /bin/bash                             # Acessa bash no Ubuntu
docker run --name ubuntinho ubuntu                          # Cria container com nome específico
docker run -d -p 8080:80 nginx /usr/sbin/nginx -g           # Configuração customizada
docker run -p 80:80 -d --restart=always carlosmedeiroslima/hello-docker:0.0.1-SNAPSHOT  # Reinício automático
```

---

### 📋 Listar Containers

```bash
docker container ps          # Lista containers ativos
docker container ls -a       # Lista todos os containers (ativos e parados)
```

---

### 🗑️ Remover Containers e Imagens

```bash
docker image rmi -f <ID_ou_NomeDaImagem>     # Remove imagem
docker rm $(docker ps -qa)                   # Remove todos os containers
docker rmi $(docker images -q)               # Remove todas as imagens
```

---

### ⏯️ Inicializar e Parar Containers

```bash
docker start <id_ou_apelido>                 # Inicia container
docker container stop <id_ou_apelido>        # Para container
docker container kill <id_ou_apelido>        # Interrompe forçadamente
```

---

## ℹ️ Informações do Container

```bash
docker inspect <id_ou_apelido>               # Exibe detalhes do container
docker container logs -f <container_id>      # Logs em tempo real
docker container pause <container_id>        # Pausa execução
docker container unpause <container_id>      # Retoma execução
docker container prune                       # Remove containers inativos
```

---

## 📊 Estatísticas e Diagnóstico

```bash
docker events                                # Monitora eventos em tempo real
docker top <ID_Container>                    # Processos dentro do container
docker stats <id_ou_apelido>                 # Exibe consumo de CPU e memória
docker run -p 81:80 -d -m 512m --cpu-quota 5000 carlosmedeiroslima/hello-docker:latest  # Limita recursos
docker system df                             # Mostra uso de disco e cache
```

---

## 🌐 Criação e Associação de Redes

```bash
docker network create wildfly
docker run -d --rm --name postgres -p 5432:5432 --net=wildfly   -e POSTGRES_USER=myapp -e POSTGRES_PASSWORD=my-password postgres:9.6.1

docker run -d --rm --name wildfly -p 8080:8080 -p 9990:9990 --net=wildfly   -e DB_HOST=postgres -e DB_NAME=myapp -e DB_USER=myapp -e DB_PASS=my-password   tonda100/wildfly-postgresql
```

---

## 🧩 Docker Compose

### 📦 Status Codes

| Código | Descrição                       |
|---------|---------------------------------|
| 0       | Container encerrado com sucesso |
| 1,2,3…  | Container encerrado com erro    |

### 🔁 Políticas de Reinício

| Política        | Descrição                                                                 |
|-----------------|---------------------------------------------------------------------------|
| `no`            | Nunca reinicia o container                                                |
| `always`        | Reinicia sempre que o container parar                                     |
| `on-failure`    | Reinicia apenas se houver erro                                            |
| `unless-stopped`| Reinicia sempre, exceto se parado manualmente                             |

### 🧰 Comandos

```bash
docker-compose -f docker-compose-local.yml up     # Sobe containers com arquivo customizado
docker-compose -f docker-compose-local.yml down   # Derruba containers definidos no arquivo
```

---

## 🗄️ Configurações de Banco de Dados

### Oracle Database

```text
hostname: localhost
port: 1521
sid: xe
username: system
password: oracle
```

### Subindo o Banco MariaDB

```bash
docker run --rm -p 3306:3306 --name mysql-mariadb   -v /home/roberto/eclipse-workspace-microservices/SistemaA/Backend/bancodedados/:/var/lib/mysql   -e MYSQL_DATABASE=app -e MYSQL_ROOT_PASSWORD=root -d mariadb
```

Acessar terminal dentro do container:

```bash
docker exec -it <container_id> bash
```

---

## 💻 Configurações de Multi-Terminal (Windows / ConEmu)

```bash
cmd.exe /k "%ConEmuBaseDir%\CmdInit.cmd" -new_console::t:"docker-compose"  -new_console:d:"C:\Desenvolvimento\sistemas\study-spring-security-with-keycloak"
cmd.exe /k "%ConEmuBaseDir%\CmdInit.cmd" -new_console::t:"docker-comandos" -new_console:d:"C:\Desenvolvimento\sistemas\study-spring-security-with-keycloak"
cmd.exe /k "%ConEmuBaseDir%\CmdInit.cmd" -new_console::t:"professor-app"  -new_console:d:"C:\Desenvolvimento\sistemas\study-spring-security-with-keycloak\professor-app"
cmd.exe /k "%ConEmuBaseDir%\CmdInit.cmd" -new_console::t:"student-app"    -new_console:d:"C:\Desenvolvimento\sistemas\study-spring-security-with-keycloak\student-app"
cmd.exe /k "%ConEmuBaseDir%\CmdInit.cmd" -new_console::t:"general-comandos" -new_console:d:"C:\Desenvolvimento\sistemas\study-spring-security-with-keycloak"
```

---

📘 **Autor:** Carlos Roberto  
🕓 **Última atualização:** Novembro de 2025  
