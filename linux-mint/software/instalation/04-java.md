#Autor: Carlos Roberto<br>
#Referencia: Bora para Prática: http://boraparapratica.com.br<br>
#Data de criação: 10/11/2024<br>
#Data de atualização: 10/11/2024<br>
#Versão: 1.0<br>
#Testado e homologado no Linux Mint 22 Wilma x64<br>

#Instalação do Java e Kotlin no Linux Mint 22 Wilma com diferentes versões<br>


Site Oficial do Visual Studio Code: https://code.visualstudio.com/<br>
Site Oficial do Visual Studio Code Web: https://vscode.dev/<br>
Link do Marketplace: https://marketplace.visualstudio.com/VSCode

O QUE É E PARA QUE SERVER O JAVA E O KOTLIN: Linguagens de programação amplamente utilizadas para desenvolver uma variedade de aplicações

#00_ Verificando as Informações do Sistema Operacional do Linux Mint<br>
```bash
#atalho para acessar o Terminal
Terminal: Ctrl + Alt + T

#verificando as versões e codinome do sistema operacional
#OBSERVAÇÃO IMPORTANTE: Linux Mint 22.x é derivado do Ubuntu Desktop 24.04.x Noble Numbat
sudo cat /etc/os-release
sudo cat /etc/lsb-release

#modo gráfico para verificar as informações de sistema operacional e hardware
Menu
  Informações do Sistema
```

#01_ Atualização do Sistema Operacional Linux Mint<br>
```bash
#atualizando o sistema operacional via MintUpdate (Recomendado)
A) Atualização do sistema utilizando o MintUpdate;
B) Atualização do sistema utilizando o Apt;

#atualizando o sistema operacional via Terminal
#atalho para acessar o Terminal
Terminal: Ctrl + Alt + T

#recomendo utilizando o comando: apt - o comando: apt-get e considerado obsoleto
sudo apt update
sudo apt upgrade
sudo apt full-upgrade
sudo apt dist-upgrade
sudo apt autoremove
sudo apt autoclean
sudo apt clean
```


#02_ Instalando as Dependência do Java e Kotlin no Linux Mint<br>
```bash
#instalação das dependências básicas do Java e Kotlin
#Instalando o git
#https://git-scm.com/downloads/linux
sudo add-apt-repository ppa:git-core/ppa
apt update
apt install git
#para conferir
git --version


#Instalando o curl (Já vem Instalado na Versão, Basta Conferir)
sudo apt update && sudo apt upgrade
sudo apt install curl
#para conferir
curl --version

#Instalando o SDKMan para Escolher as versões das JDKs e Sdks
#https://sdkman.io/
curl -s "https://get.sdkman.io" | bash
#Em um outro terminal execute
source "/home/roberto/.sdkman/bin/sdkman-init.sh"
#para conferir
sdk version

```


#03_ Como instalar o Java e o Maven no Linux Mint através do sdkman<br>
```bash
#instalação das dependências básicas do Java e Kotlin
#Instalando o git
#https://git-scm.com/downloads/linux
sudo add-apt-repository ppa:git-core/ppa
apt update
apt install git
#para conferir
git --version


#Instalando o curl (Já vem Instalado na Versão, Basta Conferir)
sudo apt update && sudo apt upgrade
sudo apt install curl
#para conferir
curl --version

#Instalando o SDKMan para Escolher as versões das JDKs e Sdks
#OBS: O SDKMan salva todos os arquivos em um diretório oculto .sdkman do <usuario> na pasta candidates
#https://sdkman.io/
curl -s "https://get.sdkman.io" | bash
#Em um outro terminal execute
source "/home/roberto/.sdkman/bin/sdkman-init.sh"
#para conferir
sdk version

#Comandos
# sdk list <java>    
# sdk list <kotlin> 
# sdk install java <java.version>
#para conferir
# java --version
sdk install java 17.0.13-amzn

#Instalando o Maven
sdk install maven

#sdk install kotlin <kotlin.version>
sdk install kotlin 1.9.24
#para conferir
# kotlin --version

#Instalando o Gradle
sdk install gradle

#Para alternar uma versão específica
# sdk list <nome-do-sdk>
# sdk use <nome-do-sdk><versao-identifer>
sdk use java 23.0.1-amzn

#Para apontar uma versão com padrão
sdk default java 17.0.13-amzn

#Para Remover um SDK
sdk uninstall <nome-do-sdk> <versao>

#Para atualizar o sdkman
sdk selfupdate

#Para atualizar multiplos sdks
sdk install java 17.0.8-tem maven 3.8.4

```

#04_Como instalar a IDE Intelij atualizada <br>
 
  ```bash
  1- Baixe o IntelliJ IDEA Comunity Edition em https://www.jetbrains.com/idea/download/.
  2- Extraia o arquivo baixado, substituia ideaIC-2023.2.2.tar.gz ou o nome-do-seu-arquivo.tar.gz pelo nome do arquivo real que você baixou:
  
  #Extraindo o arquivo
  tar -xzf ideaIC-2023.2.2.tar.gz
  ```
  3- Mova o diretório extraído para o diretório /opt, substituindo idea-IC-232.9921.47 ou o nome-do-seu-arquivo.tar.gz pelo nome real do diretório:
  ```bash
  #Movendo o diretorio
  sudo sudo mv <intelij-folder-name> /opt/intellij-idea
  ```

  4- Crie um link de acesso fácil para facilitar a execução do IntelliJ IDEA a partir do terminal:
```bash
  #Criando Link de acesso
  sudo ln -s /opt/intellij-idea/bin/idea.sh /usr/local/bin/idea
  ```

  5- Agora você pode iniciar o IntelliJ IDEA digitando no terminal: idea
  6- Crie um atalho na área de trabalho, abra o terminal e crie um novo arquivo de entrada na área de trabalho:
```bash
  #Criando o atalho na área de trabalho
  sudo nano /usr/share/applications/intellij-idea.desktop

  #Colocar o texto abaixo no documento criado
  [Desktop Entry]
  Name=IntelliJ IDEA
  Comment=Edição Comunitária do IntelliJ IDEA
  Exec=/opt/intellij-idea/bin/idea.sh
  Icon=/opt/intellij-idea/bin/idea.png
  Terminal=false
  Type=Application
  Categories=Desenvolvimento;IDE;
  StartupWMClass=jetbrains-idea
 ```

   7- Salve e feche o editor<br>
   8 - Atualize o banco de dados da área de trabalho para registrar a nova entrada
```bash
sudo update-desktop-database
 ```
