# WSL, Oh-my-zsh, asdf e intellij
Guia para instalação e configuração do wsl2, oh-my-zsh, asdf e intellij
### WSL

#### Instalar wsl
```
wsl --install
```
Obs: O wsl está disponível no windows 10 ou superior a partir da Build 19041, é preciso que o suporte a virtualização esteja habilitado o comando acima deve funcionar na maioria das máquinas em caso de problemas consulte o site https://learn.microsoft.com/pt-br/windows/wsl/install

#### Para ver distros disponíveis para instalação consulte
```
wsl --list -o
```
![image](https://user-images.githubusercontent.com/17283891/194427233-0dfafb56-bd09-4cfb-bf13-9df75e9335b4.png)

#### Para remover uma distro
```
wsl --unregister Ubuntu-20.04
```
![image](https://user-images.githubusercontent.com/17283891/194427277-6172dc9b-989b-4f92-a756-91f7e7be8dab.png)

#### Para instalar uma distro
```
wsl --install -d Ubuntu-20.04
```
![image](https://user-images.githubusercontent.com/17283891/194427311-fa5c9d1a-9971-4d2a-8e7b-08a7a0a578f3.png)

Após a instalação será exibida o sheel do ubuntu solicitando um usuário e senha

![image](https://user-images.githubusercontent.com/17283891/194427349-a2efaee8-44ba-4ed4-8618-42a62d62bca6.png)
 
#### Para desligar todas as instâncias do wsl
```
wsl --shutdown
```
Isso é útil para reiniciar sua distro, após a execução desse comando ela sobe novamente assim que for requisitada

### Instalando e configurando o Windows Terminal
Acesse a loja de aplicativos, pesquise por 'terminal' e clique em **Adquirir**
![image](https://user-images.githubusercontent.com/17283891/194427396-c1e0e6b0-eb68-441d-9f70-99f892df744e.png)
 
#### Instalando a fonte FiraCode<br>
Acesse o site <br>
https://github.com/tonsky/FiraCode/releases
Baixe a última versão, descompacte<br>
Acesse a pasta ttf dentro do diretório descompactado<br>
Selecione todas as fontes, clique com o botão direito e depois em **Instalar**
![image](https://user-images.githubusercontent.com/17283891/194427451-650bef33-5f2d-46c0-bf7f-d9be46dd0987.png)

 
#### Configurando perfil padrão

Pressione <kbd>Iniciar</kbd> digite ‘terminal’ e pressione <kbd >Enter</kbd>

![image](https://user-images.githubusercontent.com/17283891/194427683-c2ad8466-b93c-488b-91bd-9dab57595917.png)
 
Pressione <kbd >Ctrl</kbd> + <kbd >+</kbd>  + <kbd >,</kbd><br>
Em **Perfil Padrão** troque para Ubuntu<br>

![image](https://user-images.githubusercontent.com/17283891/194427721-3fb2dd44-569b-4b0d-acef-183197cbdc05.png)

#### Incluindo o tema drácula e o colocando como default
Clique em **Abrir Arquivo JSON** e siga as instruções do site https://draculatheme.com/windows-terminal

![image](https://user-images.githubusercontent.com/17283891/194428003-4f76dcc7-925e-4016-9bcd-3c23a73219ef.png)
 
Clique em **Ubuntu-20.04** e selecione a fonte **Fira Code** e clique em **Salvar**
![image](https://user-images.githubusercontent.com/17283891/194428022-3b5c0dfe-fe29-456f-b8c1-d7c919b26703.png)

 
### Oh-my-zsh
Clique para abrir uma nova aba no Windows Terminal, ou se estiver fechado abra o programa novamente, como definimos<br>
o ubuntu como padrão qualquer uma das duas opções irá abrir o shell do Linux
#### Instalar o zsh
```
sudo apt install zsh
```

#### Instalar o  curl e (ou) wget e git

```
sudo apt install curl wget git
```

Obs: caso não queira instalar um dos 2 é só removê-lo do comando

#### Continuando com o curl
```
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
#### Continuando com o wget
```
sh -c "$(wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"
```
![image](https://user-images.githubusercontent.com/17283891/194428405-f16b1172-5da6-49fc-8c8c-a09f4fe30276.png)

#### Baixando plugins de autocomplete e highlihting
```
git clone https://github.com/zsh-users/zsh-autosuggestions.git $ZSH_CUSTOM/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git $ZSH_CUSTOM/plugins/zsh-syntax-highlighting
```
![image](https://user-images.githubusercontent.com/17283891/194428452-292ef741-637b-464b-9660-b24d44a39935.png)
 
#### Trocando o tema para o spaceship e adicionando os plugins
```
git clone https://github.com/denysdovhan/spaceship-prompt.git "$ZSH_CUSTOM/themes/spaceship-prompt"
ln -s "$ZSH_CUSTOM/themes/spaceship-prompt/spaceship.zsh-theme" "$ZSH_CUSTOM/themes/spaceship.zsh-theme"
```
![image](https://user-images.githubusercontent.com/17283891/194428492-1b1b8e8d-ed8e-4ff1-a956-41861c04ec02.png)

#### Abrir o .zshrc para alterar o tema usando o editor 'vi', o .zshrc fica na pasta do usuário
```
vi .zshrc
```
#### Pressione <kbd >Esc</kbd> + <kbd >I</kbd>, para trocar para o modo de inserção, procure por 'ZSH_THEME' e troque por spaceship
```
ZSH_THEME="spaceship"
```
![image](https://user-images.githubusercontent.com/17283891/194428537-83647979-aada-4c71-8b8e-106c185a97c8.png)

#### Procure por plugins e adicione os separando com espaços
```
plugins=(git vi-mode zsh-autosuggestions zsh-syntax-highlighting)
```
![image](https://user-images.githubusercontent.com/17283891/194428668-075f2a3a-c979-4be2-96b7-5f6247d94dd0.png)

Obs: O git já vêm incluído por padrão <br>
No final do arquivo incluir a configuração abaixo:
```
SPACESHIP_PROMPT_ORDER=(
  user          # Username section
  dir           # Current directory section
  host          # Hostname section
  git           # Git section (git_branch + git_status)
  hg            # Mercurial section (hg_branch  + hg_status)
  exec_time     # Execution time
  line_sep      # Line break
  jobs          # Background jobs indicator
  exit_code     # Exit code section
  char          # Prompt character
)
SPACESHIP_USER_SHOW=always
SPACESHIP_PROMPT_ADD_NEWLINE=false
SPACESHIP_CHAR_SYMBOL="❯"
SPACESHIP_CHAR_SUFFIX=" "
```
![image](https://user-images.githubusercontent.com/17283891/194428754-6ec27ba0-e748-454f-b021-d7bee33bd4f7.png)

Obs: Atenção  a tag # de comentário pode ser adicionada ao pular linha, remova antes de colar<br>
Após as alterações pressione <kbd >Esc</kbd> + <kbd >:</kbd><br>
Digite wq + Enter para salvar e sair, reinicie seu terminal
![image](https://user-images.githubusercontent.com/17283891/194428789-87e5203b-5725-485d-b50d-73d42e389d72.png)
 
Exemplo zsh-autosuggestions zsh-syntax-highlighting 
Comando incorreto

![image](https://user-images.githubusercontent.com/17283891/194428834-d92f6489-a91c-499f-8e7f-3c1503f4452c.png)

Obs como o comando ainda não foi digitado completamente mostrar o gi em vermelho, para aceitar a sugestão<br> 
basta apertar <kbd>Right</kbd> ou <kbd>Tab</kbd> também é possível trocar o comando com <kbd>Up</kbd> e <kbd>Down</kbd><br>
Comando correto

![image](https://user-images.githubusercontent.com/17283891/194428900-965953ae-2ff3-4128-8b33-06682b022898.png)
 
### Instalando asdf

Faça o clone do repositório
```
git clone https://github.com/asdf-vm/asdf.git ~/.asdf --branch v0.10.2
```
![image](https://user-images.githubusercontent.com/17283891/194428935-198c9529-9783-4952-b4dd-919228fd9e25.png)

adicione a config no arquivo .zshrc
```
. $HOME/.asdf/asdf.sh
```
![image](https://user-images.githubusercontent.com/17283891/194428951-66459714-3ddd-4d65-a8b5-926aed2661e2.png)
 
 
#### Instalando o plugin java para asdf
```
asdf plugin add java
```
![image](https://user-images.githubusercontent.com/17283891/194429142-e4cfcbf2-156b-47e3-ac88-3efcbc910b23.png)

#### Listando versões disponiveis 
```
asdf list-all java
```
![image](https://user-images.githubusercontent.com/17283891/194429166-a8e6c6bc-ea86-4ce5-a1e2-a7f0093d29f1.png)

#### Filtrando lista de versões disponiveis 
```
asdf list-all java open
```
![image](https://user-images.githubusercontent.com/17283891/194728408-f880e45d-837b-4cb4-90d1-8617df2e95a4.png)

#### Instalando uma versão
```
asdf install java openjdk-11
```
![image](https://user-images.githubusercontent.com/17283891/194429192-81047928-4b8a-4e31-b01d-43e322cb15ed.png)

 
#### Listando versões instaladas
```
asdf list java
```
![image](https://user-images.githubusercontent.com/17283891/194429215-8a8fc4db-a5b6-49a4-9d90-e9f2fdf89b8e.png)
 
#### Escolhendo uma versão como default
```
asdf global java openjdk-11
```
![image](https://user-images.githubusercontent.com/17283891/194429247-00fafa7d-6ea2-4786-937a-1bf71773dc7c.png)


#### Instalando maven com asdf
```
asdf install maven 3.9.0-SNAPSHOT
asdf global maven 3.9.0-SNAPSHOT
mvn --version
```
![image](https://user-images.githubusercontent.com/17283891/194728050-cc3f0a03-9b9e-445c-8cd1-f6ddb019b22b.png)

#### Escolhendo uma versão local
Entre na pasta do projeto
```
asdf local java openjdk-17
```
![image](https://user-images.githubusercontent.com/17283891/194727894-9f744b93-4f0d-4aa0-a9f4-334ba4ed43cb.png)


#### Removendo uma vec com o asdf
```
asdf uninstall maven 3.8.0-SNAPSHOT
```
![image](https://user-images.githubusercontent.com/17283891/194728053-ebba9c41-cce9-4020-b4ec-c3f348e54b40.png)

Obs: Os comandos de definir como local e remoção de uma vec foram utilizados somente para ilustrar
 
### Adicionando exceção no Windows Defender
O Windows Defender pode atrapalhar o IntelliJ a conseguir fazer o processo de build e execução<br> 
da aplicação<br>
Pressione <kbd>Iniciar</kbd>, digite ‘prote’, selecione **Proteção contra vírus e ameaças** e pressione <kbd>Enter</kbd>
![image](https://user-images.githubusercontent.com/17283891/194429635-09e89f1b-1346-40af-ba73-4d63da98a41d.png)
 
Clique em **Gerenciar configurações**<br>
![image](https://user-images.githubusercontent.com/17283891/194430451-c5706acc-a631-4ef8-9b61-09db0bd245c4.png)
 
Clique em **Adicionar ou remover exclusões**<br>
![image](https://user-images.githubusercontent.com/17283891/194430526-2b66cd4c-9dcd-4605-adf1-2901d4423c20.png)
 
Clique em **Adicionar uma exclusão** e depois em **Pasta**<br>
![image](https://user-images.githubusercontent.com/17283891/194429720-5379a60b-2418-4492-9d10-eec3cbd3ae5d.png)

Inclua o caminho da pasta do seu usuário no wsl ou um nível abaixo<br>
```
\\wsl$\Ubuntu-20.04\home\vinicius
```
ou
```
\\wsl$\Ubuntu-20.04\home
```
![image](https://user-images.githubusercontent.com/17283891/194430604-19c88f97-e23e-48fe-9d52-b79d50577de7.png)


Obs: Caso esteja utilizando outro antivírus e o IntelliJ esteja travando é provável que seja por isso,<br>
nesse caso procure como remover um diretório da análise do seu antivírus

### Instalando o JetBrainsToolBox
Vamos reiniciar o wsl, para evitar possíveis problemas no Intellij
```
wsl --shutdown
```
Para evitar problemas de permissão no IntelliJ vamos criar uma pasta para colocar nossos projetos,<br>
criando e importando novos projetos para dentro dessa pasta não teremos problemas!
```
mkdir projetos
```

<br>Acesse o site e baixe e instale https://www.jetbrains.com/toolbox-app/<br>
Apos executar o arquivo de instalação basta clicar em **Instalar** e **Concluir** ao final <br>
![image](https://user-images.githubusercontent.com/17283891/194430980-c5157b92-d8a6-4c3b-903f-743c2ca0895c.png)
 
<br>Após a instalação abra o ToolBox<br>
Clique em **Continuar**, **Aceitar Contrato de Licença** escolha o tema e clique em **Começar**<br>
![image](https://user-images.githubusercontent.com/17283891/194431173-92b284f6-837b-4437-b361-c4c179a1f9e0.png)
   
###Instale o IntelliJ Community 
Clique em **Instalar**<br>
![image](https://user-images.githubusercontent.com/17283891/194431360-e20b6552-a7e1-44f0-bf51-3f043b19dc48.png)
<br>Aceite os termos de uso e marque para não enviar dados, ou enviar de forma anônima para prosseguir<br>
![image](https://user-images.githubusercontent.com/17283891/194431587-527e2b24-117c-453e-bc61-8f29205f1caf.png)
<br>Após o IntelliJ ser aberto clique em **New Project...**<br>
![image](https://user-images.githubusercontent.com/17283891/194722496-66b38327-6704-4d7c-ba35-2b28ff124bde.png)
<br>Coloque um nome para o projeto e selecione o caminho criado anteriormente<br>
Clique em **JDK** e depois em **Add JDK...**
![image](https://user-images.githubusercontent.com/17283891/194719758-91d9c7bb-cb60-4b8d-a78a-8c4a03ba3287.png)
<br>Selecione o caminho de onde o jdk está instalado  e clique em **OK**
```
\\wsl$\Ubuntu-20.04\home\vinicius\.asdf\installs\java\openjdk-11
```
![image](https://user-images.githubusercontent.com/17283891/194719820-c2b92128-e08d-4e5d-aded-f96135c6375a.png)
<br>Clique em **Create** para prosseguir
![image](https://user-images.githubusercontent.com/17283891/194719846-d1ae45ad-4074-43e5-b825-e6ba1bdb7fe7.png)
<br>O projeto criado será aberto, abra o arquivo Main e aguarde a indexação da jdk concluir, após clique na seta verde para executar<br>
![image](https://user-images.githubusercontent.com/17283891/194719894-36b276ed-81fa-497d-a25b-68ae59e9753e.png)
<br>Acesse o site https://start.spring.io/ marque a opção **Java 11** clique em **GENERATE**<br>
![image](https://user-images.githubusercontent.com/17283891/194720057-111fd0d1-92e1-4e85-a802-ab825dc016b1.png)
<br>Descompacte o zip <kbd>Windows</kbd> + <kbd>R</kbd> coloque o caminho da sua pasta e pressione <kbd>Enter</kbd>
``` 
\\wsl$\Ubuntu-20.04\home\vinicius\projetos
```
Cole o projeto descompactado na pasta
No IntelliJ clique em **Open** ou **File** => **Open** selecione a pasta do projeto e clique em **OK**<br>
![image](https://user-images.githubusercontent.com/17283891/194720177-f6fda147-6735-439d-a60e-8db030692206.png)
<br>Clique em **Trust Project**<br>
![image](https://user-images.githubusercontent.com/17283891/194720191-a73b2ec6-b948-475b-b7b7-beb1db2d5902.png)
<br>Pressione <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>A</kbd>, digite maven e clique em **Maven Settings**<br>
![image](https://user-images.githubusercontent.com/17283891/194720244-759643b3-10c7-4465-8da5-a68a79d9defb.png)
<br>Em **Maven home** path: Selecione **Bundled (Maven 3)** e clique em **OK**
![image](https://user-images.githubusercontent.com/17283891/194720266-80d2238b-1305-4a60-85d2-5024e894e0e8.png)
<br>Clique em **Maven** no canto superior direito da tela, clique em demo e **Lifecylce** para expandir
Após duplo clique em **Install**
![image](https://user-images.githubusercontent.com/17283891/194720304-5e21c229-7c50-4fc0-8753-dd0a1eef9821.png)
<br>Será realizado o build do projeto
![image](https://user-images.githubusercontent.com/17283891/194720323-3d18f1af-bb49-4ed5-beb8-98d283ad96b1.png)
<br>Na estrutura do projeto clique em src, main, java e com.example.demo para expandir e abra o arquivo DemoApplication, após clique na seta verde para executar
![image](https://user-images.githubusercontent.com/17283891/194720348-ff173fb5-5972-4752-868d-599c3185ee61.png)
<br>Assim concluímos a config, lembro que é possível instalar outras ferramentas para trabalhar com outras linguagens usando o asdf e instalar também outras ides da JetBrains as que terminam com Community no nome são gratuitas!


## Agradecimento

Vlw Rocketseat oh-my-zsh
[Rocketseat](https://rocketseat.com.br/)

Vlw Fabio Akita asdf e wsl
[Akita](https://www.youtube.com/c/FabioAkita1990)

Vlw DevSuperior intelliJ
[DevSuperior](https://www.youtube.com/c/DevSuperior)

Vlw a mim mesmo
[Vinicius Moreira](https://www.youtube.com/user/ViniciusJoseMoreira)
