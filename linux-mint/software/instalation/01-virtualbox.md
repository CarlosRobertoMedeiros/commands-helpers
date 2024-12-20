#Autor: Carlos Roberto<br>
#Referencia: Bora para Prática: http://boraparapratica.com.br<br>
#Data de criação: 06/11/2024<br>
#Data de atualização: 06/11/2024<br>
#Versão: 1.0<br>
#Testado e homologado no Linux Mint 22 Wilma x64<br>

#Instalação do VirtualBOX no Linux Mint 22 Wilma x64<br>

Site Oficial do VirtualBOX: https://www.virtualbox.org/<br>
Lançamento da versão 7.0 do VirtualBOX: https://www.virtualbox.org/wiki/Changelog-7.0#v02<br>
Atualização da versão 7.0 do VirtualBOX: https://www.virtualbox.org/wiki/Changelog-7.0#v4

O QUE É E PARA QUE SERVER O ORACLE VIRTUALBOX: VirtualBox é um software de virtualização de código aberto desenvolvido pela Oracle, que permite criar e executar máquinas virtuais em um computador físico. Assim, o software emula um computador completo, incluindo sistemas operacionais e aplicativos.

#Tecnologias de Virtualização dos Processadores AMD e Intel<br>
```bash
#Tecnologias de Virtualização Intel e AMD
1) vmx...: Intel VT-x, suporte a virtualização ativada na BIOS.
2) svm...: AMD SVM, suporte a virtualização ativada na BIOS.

#AES dos Processadores da AMD e Intel
01) aes...: Aplicativos que executam criptografia e descriptografia usando o Advanced
            Encryption Standard em processadores Intel e AMD.

#Flags dos Processadores da Intel
01) ept.....: Suporte de tabela de páginas estendidas da Intel habilitado para tornar
              mais rápida a emulação de tabelas de páginas de convidados.
02) vpid....: ID do processador virtual da Intel. Faça descargas de TLB caras
              desnecessárias quando alternar o contexto entre os convidados.
03) vnmi....: O Intel Virtual NMI ajuda com eventos de interrupção selecionados em 
              convidados.
04) tpr_shadow e flexpriority..: Recurso da Intel que reduz as chamadas para o hypervisor 
                                 ao acessar o Registro de prioridade de tarefas, o que ajuda 
                                 na execução de determinados tipos de convidados do SMP.

#Flags dos Processadores da AMD
01) npt...........: Tabelas de Páginas Aninhadas AMD, semelhantes ao Intel EPT.
02) lbrv..........: Suporte de virtualização da AMD LBR.
03) svm_lock......: MSR de bloqueio AMD SVM.
04) nrip_save.....: AMD SVM next_rip salvar.
05) tsc_scale.....: Suporte de dimensionamento do AMD TSC.
06) vmcb_clean....: Suporte para bits limpos AMD VMCB.
07) flushbyasid...: Suporte para AMD flush-by-ASID.
08) decodeassists.: AMD Decode Assistir ao suporte.
09) pausefilter...: Interrupção de pausa filtrada AMD.
10) pfthreshold...: AMD pausa o limite do filtro.
```

#00_ Verificando as Informações do Sistema Operacional do Linux Mint<br>
```bash
#atalho para acessar o Terminal
Terminal: Ctrl + Alt + T
	
#verificando as versões e codinome do sistema operacional
#OBSERVAÇÃO IMPORTANTE: Linux Mint 22.x é derivado do Ubuntu Desktop 24.04.x Noble Numbat
sudo cat /etc/os-release
sudo cat /etc/lsb-release

#verificando as informações de hardware e processador
#opções do comando inxi: -C (cpu), -M (machine), -S (system), -f (flags), -xxx (extra 3)
sudo inxi -CMSfxxx
sudo lscpu

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

#02_ Adicionando o Repositório do Oracle VirtualBOX no Linux Mint<br>
```bash
#OBSERVAÇÃO IMPORTANTE: CUIDADO COM A VERSÃO DO LINUX MINT QUE VOCÊ ESTÁ USANDO,
#OS COMANDOS DE ADICIONAR REPOSITÓRIO NÃO MOSTRA RESULTADO NA TELA, CUIDADO PARA
#NÃO EXECUTAR MAIS DE UMA VEZ O COMANDO PARA NÃO ADICIONAR MÚLTIPLAS ENTRADAS NO
#ARQUIVO EM: /etc/apt/sources.list.d/virtualbox.list.

#ADICIONANDO O REPOSITÓRIO NO LINUX MINT 22.x
#opção do comando sh: -c (Read commands from the command_string operand in‐stead of from the standard input)
#opção do redirecionador >>: Redireciona a saída padrão, anexando
sudo sh -c 'echo "deb [arch=amd64 signed-by=/usr/share/keyrings/virtualbox.gpg] https://download.virtualbox.org/virtualbox/debian noble contrib" >> /etc/apt/sources.list.d/virtualbox.list'
```

#03_ Baixando e Instalando as Chaves de Autenticação GPG do Oracle VirtualBOX no Linux Mint<br>
```bash
#OBSERVAÇÃO IMPORTANTE: CUIDADO COM A VERSÃO DO LINUX MINT QUE VOCÊ ESTÁ USANDO,
#OS COMANDOS DE ADICIONAR OU CONVERTER AS CHAVES GPG NO LINUX MINT NÃO MOSTRA NA
#TELA O RESULTADO.

#BAIXANDO A CHAVE DO REPOSITÓRIO DO VIRTUALBOX NO LINUX MINT 21.x E 22.x
#opções do comando wget: -q (quiet)
wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc

#CONVERTENDO E INSTALANDO A CHAVE DO REPOSITÓRIO DO VIRTUALBOX NO LINUX LINUX MINT 22.x
#opção do redirecionador |: Conecta a saída padrão com a entrada padrão de outro comando
#opção do redirecionador >: Redireciona a saída padrão (STDOUT)
#opção do redirecionador 2>&1: Conecta a saída de erro na saída padrão
cat oracle_vbox_2016.asc | gpg --dearmor | sudo tee /usr/share/keyrings/virtualbox.gpg > /dev/null 2>&1
```

#04_ Instalando o Oracle VirtualBOX no Linux Mint<br>
```bash
#OBSERVAÇÃO IMPORTANTE: recomendo fazer a instalação da nova versão do VirtualBOX 7.1.x
Mais informações acesse: https://www.virtualbox.org/wiki/Changelog

#atualizando as lista do Apt com o novo repositório do VirtualBOX
sudo apt update

#OBSERVAÇÃO IMPORTANTE: UTILIZAR SOMENTE A VERSÃO DO VIRTUALBOX 6.1.X SE FOR REALMENTE
#NECESSÁRIO, EM ALGUNS CASOS A VERSÃO ANTIGA RESOLVER PROBLEMAS DE SOFTWARE OU SISTEMA
#OPERACIONAL OBSOLETOS, HOJE EM DIA NÃO É MAIS INDICADO USAR ESSA VERSÃO.

#procedimento de instalação no Linux Mint 22.x
#INSTALANDO O VIRTUALBOX VERSÃO 7.1.x (RECOMENDADO A SUA INSTALAÇÃO)
sudo apt install virtualbox-7.1 cpu-checker libvirt-clients git vim python3
```

#05_ Verificando as Informações do suporte a Virtualização no Linux Mint<br>
```bash
#verificando as informações de KVM (Kernel Virtual Machine)
sudo kvm-ok

#verificando as informações de validação do host da Biblioteca LibVirt
sudo virt-host-validate

#OBSERVAÇÃO IMPORTANTE: conforme relatos no Canal do YouTUBE do Bora para Prática, no 
#Linux Mint versão 21.x é mostrado a seguinte mensagem de falha quando você utiliza o 
#comando: sudo virt-host-validate. Conforme vários relatos nos fórum do Linux Mint e 
#do Ubuntu esse erro está associado a versão do Cgroup utilizado no Ubuntu 22.04.x que 
#é a base do Linux Mint 21.x. e do Ubuntu 24.04.x que é a base do 22.x

#LXC: Checking for cgroup 'freezer' controller support FAIL (Enable 'freezer' in kernel 
#Kconfig file or mount/enable cgroup controller in your system)

#QEMU: Checking for secure guest support: WARN (Unknown if this platform has Secure Guest 
#support: essa mensagem faz referência ao suporte a processadores Intel com tecnologias 
#VT-x e VT-d, caso a sua CPU não tenha suporte ao VT-d essa mensagem e apresentada, você 
#pode ignorar essa mensagem.

#CORREÇÃO PARA O LINUX MINT 21.x e 22.x REFERENTE AO ERRO DO FREEZER DO COMANDO: sudo virt-host-validate

#OBSERVAÇÃO IMPORTANTE: MUITO CUIDADO NA HORA DE ATUALIZAR OS ARQUIVOS DE CONFIGURAÇÃO 
#DO GRUB DO LINUX MINT, QUALQUER FALHA NA DIGITAÇÃO PODE ACARRETAR A FALHA DE INICIALIZAÇÃO 
#DO SISTEMA. CUIDADO!!!!!!!!!

#editar o arquivo de configuração do Grub
sudo vim /etc/default/grub
INSERT

  #alterar a linha: 10 das configurações padrão do GRUB do Linux Mint de:
  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

  #para: adicionando a opção da hierarquia do Cgroup
  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash systemd.unified_cgroup_hierarchy=0"

  #OBSERVAÇÃO IMPORTANTE: UTILIZAR AS OPÇÕES ABAIXO SOMENTE SE VOCÊ ESTÁ USANDO ESSES RECURSOS
  #NO LINUX MINT E SEU HARDWARE SUPORTA TAL TECNOLOGIA.

  #se estiver usando processadores Intel pode habilitar o IOMMU no GRUB adicionando a opção:
  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash systemd.unified_cgroup_hierarchy=0 intel_iommu=on"

  #se estiver usando processadores AMD pode habilitar o IOMMU no GRUB adicionando a opção:
  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash systemd.unified_cgroup_hierarchy=0 amd_iommu=on"

#salvar e sair do arquivo
ESC SHIFT :x <Enter>

#atualizar os arquivos de GRUB para aplicar as mudanças
sudo update-grub

#OBSERVAÇÃO IMPORTANTE: para aplicar as mudanças no GRUB e necessário reiniciar o sistema 
#operacional e checar novamente se a correção funcionou.
sudo reboot

#verificando novamente a validação da biblioteca LibVirt
sudo virt-host-validate
```

#06_ Baixando e Instalando o Pacote de Extensões do Oracle VirtualBOX 7.1<br>
```bash
#OBSERVAÇÃO: PROCEDIMENTO É IGUAL NAS VERSÕES DO VIRTUALBOX 6.1.x E 7.1.x

#download das extensões do site oficial do VirtualBOX 
Link para download: https://www.virtualbox.org/wiki/Downloads
  Opção: VirtualBox 7.x Oracle VM VirtualBox Extension Pack
    Clique em: All supported platforms

#Recomendo fazer a instalação do Pacote de Extensões do Oracle VirtualBOX via download do
#site Oficial. Após baixar o pacote, clicar duas vezes no mesmo e seguir os procedimentos
#que serão apresentados na tela.
<Instalar>
  Descer a barra de rolagem até o final
<Eu Concordo>
  Digite a senha do seu usuário clique em: <Autenticar>
```

#07_ Corrigindo a Falha do VirtualBOX 7.1 em relação ao Erro: Failed to enumerate host USB devices<br>
```bash
#adicionando o usuário no grupo do VirtualBOX Users
#opções do comando usermod: -a (append), -G (groups), $USER (variável de ambiente do nome do usuário)
sudo usermod -aG vboxusers $USER

#verificando se o usuário foi adicionado no grupo
sudo getent group vboxusers

#recomendo reiniciar a máquina para testar se a falha foi resolvida
sudo reboot
```

#08_ Corrigindo a Falha do VirtualBOX 7.1 em relação ao Erro: Kernel driver not installed (rc=-1908)<br>
```bash
#OBSERVAÇÃO IMPORTANTE: EXECUTAR ESSE PROCEDIMENTO SOMENTE SE O SEU VIRTUALBOX NA HORA DA
#INICIALIZAÇÃO ESTIVER APRESENTANDO ESSE MENSAGEM OU NÃO INICIANDO, NÃO EXECUTAR ESSES
#COMANDOS SEM ANTES VERIFICAR O MOTIVO DA FALHA.

#atualizando as listas do Apt
sudo apt update

#instalando os pacotes necessários para recompilar o módulo do Kernel do VirtualBOX
#opção do comando apt $(uname -r): $() (Executa comandos numa subshell)
#opção do comando uname: -r (kernel-release)
sudo apt-get install build-essential module-assistant dkms linux-headers-$(uname -r)

#preparando o processo de compilação dos módulos do Kernel do VirtualBOX
#opção do comando m-a: prepare (Tries to determine the name of the required linux-headers package)
sudo m-a prepare

#compilando o driver (módulos) do VirtualBOX
sudo /etc/init.d/vboxdrv setup

#recomendo reiniciar a máquina para testar se a falha foi resolvida
sudo reboot
```

#09_ Instalando o controlador VBoxGuestAdditions.iso para permitir a tela em full screen 
```bash
#OBSERVAÇÃO IMPORTANTE: Siga a ordem de execução abaixo
1. Vá em armazenamento na imagem do virtual box que pretende usar  
2. Em dispositivos adicione uma Controladora: SATA 
3. Ao clicar no (+) inclua VBoxGuestAdditions.iso e Ok 
4. Ao Carregar a máquina virtual Windows como no exemplo Execute o VBoxGuestAdditions.exe, pois ele vai informar se a máquina será 32 ou 64bits.  
5. Após a instalação remova do armazenamento o controlador sata referente ao VBoxGuestAdditions 
```

