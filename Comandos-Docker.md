Comandos no Repositório
  docker login 
  docker search ubuntu  -- comando para procurar uma imagem
  docker search ubuntu --filter is-official=true -- procura imagens oficiais
  docker commit id/apelido nomeimagem -- enviar para o docker hub a imagem
  docker pull ubuntu    -- comando para baixar a imagem
  docker push carlosmedeiroslima/hello-docker:0.0.1-SNAPSHOT –gerar o push
  docker image history ID_ouNomeDaImagem
  
Construção de Builds e Tags
  docker build --tag=carlosroberto/wildfly-18-admin . --Cria um container
  docker tag hello-docker:0.0.1-SNAPSHOT carlosmedeiroslima/hello-docker:latest

Comandos Básicos
Executar Container
  docker run --rm -it --name test alpine:latest /bin/sh --caso precise usar dentro do container
  docker run -it -p 8080:8080 nginx -- roda em modo iterativo mapeando a porta 8080
  docker run -d -p 8080:8080 minhaapp -- caso eu rode o container e detache do terminal
  docker run nome da imagem -- cria um container
  docker run -it ubuntu /bin/bash -- executa o bash dentro de uma imagem ubuntu
  docker run --name ubuntinho ubuntu -- cria um container com um apelido
  docker run -d -p 8080:80 nginx /usr/sbin/nginx -g
  docker run -p 80:80 -d --restart=always carlosmedeiroslima/hello-docker:0.0.1-SNAPSHOT  -- Quando o docker iniciar ele vai iniciar
  
Listar Container
  docker container ps ou ls -- lista os processos
  docker container ls -a --lista todos os containers que foram parados

Remover Container
  docker image rmi -f ID_ouNomeDaImagem -- exclui a Imagem
  docker rmi -f ID_ouNomeDaImagem -- exclui a Imagem
  docker rm $(docker ps -qa) -- remove todos os containers e --imagens com id do ps
  docker rmi $(docker images -q) -- remove imagens
  

Inicializar e parar Container
  docker start id_ou_apelido
  docker container stop id_ou_apelido --para o container
  docker container kill id_ou_apelido --para abruptamente o container

Informações Gerais do Container
  docker inspect id_ou_apelido -- verifica detalhes da container image
  docker container logs -f container_id -- verifica em tempo real os logs
  docker container pause container_id --usado para teste
  docker container unpause container_id --usado para teste
  docker container prune --limpa os containers que não estão em execução
  
Ferramentas de Estatísticas do Container 
  docker events -- acompanha o que está acontecendo DEBUG inteligente
  docker top ID_Container -- verifica processo que está executando no container 
  docker stats id_ou_apelido -- verifica estatísticas do Hardware importante
  docker run -p 81:80 -d -m 512m --cpu-quota 5000 carlosmedeiroslima/hello-docker:latest -- Limito o container a 512mb e 5% do cpu
  docker system df --Lista a estatística do sistema

Criando Rede e Associando ao container
  docker network create wildfly
  docker run -d --rm --name postgres -p 5432:5432 --net=wildfly -e POSTGRES_USER=myapp -e POSTGRES_PASSWORD=my-password postgres:9.6.1
  docker run -d --rm --name wildfly -p 8080:8080 -p 9990:9990 --net=wildfly -e DB_HOST=postgres -e DB_NAME=myapp -e DB_USER=myapp -e DB_PASS=my-password tonda100/wildfly-postgresql

DOCKER-COMPOSE
  Status Code do Container para o Ciclo de Vida
  0: Container encerrado com sucesso
  1,2,3 etc: Container encerrado com erro

  Restart Policies
	no: nunca tenta reiniciar este container se ele parar ou travar
	always: container parou por qq motivo, tenta reiniciar
	on-failure: Reinicia apenas se o container parar com código de erro
	unless-stopped: sempre reinicia, a menos que o dev force a parada

  docker-compose -f docker-compose-local.yml up   --arquivo com padrão de nome dif
  docker-compose -f docker-compose-local.yml down --arquivo com padrão de nome dif










Demais Opções
Connect database with following setting:

hostname: localhost
port: 1521
sid: xe
username: system
password: oracle
Password for SYS & SYSTEM

oracle


subindo o banco mariadb
docker run --rm  -p 3306:3306 --name mysql-mariadb -v -v /my/own/datadir:/var/lib/mysql -e MYSQL_DATABASE=app -e  MYSQL_ROOT_PASSWORD=root -d mariadb

container que funciona
docker run --rm  -p 3306:3306 --name mysql-mariadb -v /home/roberto/eclipse-workspace-microservices/SistemaA/Backend/bancodedados/:/var/lib/mysql -e MYSQL_DATABASE=app -e  MYSQL_ROOT_PASSWORD=root -d mariadb

docker exec -it containerid bash --entrei no bash dentro do container


Configurações do multiterminal
cmd.exe /k "%ConEmuBaseDir%\CmdInit.cmd" -new_console::t:"docker-compose"  -new_console:d:"C:\Desenvolvimento\sistemas\study-spring-security-with-keycloak"

cmd.exe /k "%ConEmuBaseDir%\CmdInit.cmd" -new_console::t:"docker-comandos"  -new_console:d:"C:\Desenvolvimento\sistemas\study-spring-security-with-keycloak"

cmd.exe /k "%ConEmuBaseDir%\CmdInit.cmd" -new_console::t:"professor-app"  -new_console:d:"C:\Desenvolvimento\sistemas\study-spring-security-with-keycloak\professor-app"

cmd.exe /k "%ConEmuBaseDir%\CmdInit.cmd" -new_console::t:"student-app"  -new_console:d:"C:\Desenvolvimento\sistemas\study-spring-security-with-keycloak\student-app"

cmd.exe /k "%ConEmuBaseDir%\CmdInit.cmd" -new_console::t:"general-comandos"  -new_console:d:"C:\Desenvolvimento\sistemas\study-spring-security-with-keycloak"