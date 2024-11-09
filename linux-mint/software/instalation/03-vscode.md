#Autor: Carlos Roberto<br>
#Referencia: Bora para Prática: http://boraparapratica.com.br<br>
#Data de criação: 07/11/2024<br>
#Data de atualização: 07/11/2024<br>
#Versão: 1.0<br>
#Testado e homologado no Linux Mint 22 Wilma x64<br>

#Instalação do Microsoft Visual Studio Code VSCode no Linux Mint 22 Wilma<br>


Site Oficial do Visual Studio Code: https://code.visualstudio.com/<br>
Site Oficial do Visual Studio Code Web: https://vscode.dev/<br>
Link do Marketplace: https://marketplace.visualstudio.com/VSCode

O QUE É E PARA QUE SERVER O VSCODE: O Visual Studio Code é um editor de código-fonte desenvolvido pela Microsoft para Windows, Linux e macOS. Ele inclui suporte para depuração, controle de versionamento Git incorporado, realce de sintaxe, complementação inteligente de código, snippets e refatoração de código.

#00_ Verificando as Informações do Sistema Operacional do Linux Mint<br>
```bash
#atalho para acessar o Terminal
Terminal: Ctrl + Alt + T

#verificando as versões e codinome do sistema operacional
#OBSERVAÇÃO IMPORTANTE: Linux Mint 20.x é derivado do Ubuntu Desktop 20.04.x Focal Fossa
#OBSERVAÇÃO IMPORTANTE: Linux Mint 21.x é derivado do Ubuntu Desktop 22.04.x Jammy Jellyfish
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

#02_ Instalando as Dependências do Microsoft Visual Studio Code VSCode no Linux Mint<br>
```bash
#instalando as dependências do VSCode no Linux Mint 20.x e 21.x
sudo apt install vim git python2 python3 pip cloc

#instalando as dependências do VSCode no Linux Mint 22.x
sudo apt install vim git python3 python3-pip cloc
```

#03_ Baixando o Microsoft Visual Studio Code VSCode para o Linux Mint<br>
```bash
#link de download oficial do VSCode
Link de download: https://code.visualstudio.com/download
  Versão: .deb (Debian, Ubuntu 64 Bits)
    Salvar aquivo
```

#04_ Instalando o Microsoft Visual Studio Code VSCode utilizando o Gdebi-Gtk no Linux Mint<br>
```bash
#instalação em modo gráfico (indicado)
Arquivos
  Download
    code_1.*_amd64
      Instalar Pacote
    <Fechar>
```

#05_ Verificando o novo repositório do Microsoft Visual Studio Code VSCode no MintUpdate<br>
```bash
#verificando o novo repositório no Linux Mint
Menu
  MintUpdate
    Editar
      Fontes de Programas
        (Digite a senha do seu usuário)
          Repositórios Adicionais
            Habilitado: Microsoft / Stable - code
          Chaves de Autenticação
            Microsoft (Release signing)
      <Fechar>
  <Fechar>
```

#06_ Iniciando o Microsoft Visual Studio Code VSCode no Linux Mint<br>
```bash
#iniciando o VSCode no Linux Mint
Menu
  Busca Indexada
    vscode
      Dark Theme
      Notifications: Pacote PT-BR
      Disable: Mostrar página inicial na inicialização
```

#07_ Configurando o Microsoft Visual Studio Code VSCode como Aplicativo de Preferência no Linux Mint<br>
```bash
#configuração básica do VSCode no Linux Mint
Menu
  Busca Indexada
    Aplicativos de Preferencias
      Texto puro: Visual Studio Code
      Código fonte: Visual Studio Code
    <Fechar>
```

