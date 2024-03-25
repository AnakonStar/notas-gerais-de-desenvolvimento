# Anotações gerais para arrumar problemas comuns e construir um ambiente de desenvolvimento

Apenas um passo a passo de como estar pronto para rodar aplicações baseadas em


![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)![React Native](https://img.shields.io/badge/React_Native-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)

## Sumário

1. [Instalação de dependências necessárias](#instalação-de-dependências-necessárias)

2. [Criar um novo ambiente para rodar React Native em aparelho físico](#criar-um-novo-ambiente-para-rodar-react-native-em-aparelho-físico)
   - [Configurar com Android Studio](#configurar-com-android-studio)
   - [Configurar com cmdline-tools](#configurar-com-cmdline-tools)

3. [Espelhar aparelho físico no computador](#espelhar-aparelho-físico-no-computador)
   - [Rodar por meio da conexão Wi-Fi](#rodar-por-meio-da-conexão-wi-fi)

## Instalação de dependências necessárias

Primeiro de tudo serão necessárias algumas dependências para começar o desenvolvimento, por isso vamos começar com o instalador de todos estes, conhecido como [Chocolatey](https://chocolatey.org/install)

1. Vá até o site da biblioteca Chocolatey e acesse a área de instalação ou apenas clique no link acima;

2. Execute todos os passos descritos;

---

### Descrição dos passos para não ter que acessar o site oficial

1. Abra o PowerShell do Windows como administrador (apenas pesquise por PowerShell na barra de pesquisa do Windows)

2. Rode o seguinte comando:

```
Get-ExecutionPolicy
```

Caso retorn como ```Restricted```, rode o seguinte comando

```
Set-ExecutionPolicy AllSigned
```

> [!NOTE]
> Lembre-se de após o processo de instalação (incluindo a instalação posterior a esta), retornar o ```Get-ExecutionPolicy``` para o padrão que estava, rodando o mesmo comando anterior, mas trocando de ```AllSigned``` para ```Restricted```

Em seguida rode o comando:

```
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

3. Assim que aparecer para ditar o aceite dos termos, aperte digite A e de Enter/Return e espere o download ser finalizado

4. Para verificar se está tudo instalado corretamente, rode o seguinte comando ```choco``` ou ```choco -?```, caso retorne o nome da dependência e a versão, está tudo certo

---

3. Dessa forma você já deve ser capaz de utilizar o Chocolatey para instalações de dependências globais em sua máquina

Após instalar o Chocolatey, já deve ser possível instalar o [Node](https://nodejs.org/en) e [OpenJDK](https://openjdk.org) que são extremamente necessárias para rodar um aplicativo em React Native ou qualquer outra framework baseada em -Javascript-

1. Abra o PowerShell do Windows como administrador

2. Rode o seguinte comando:

```
choco install -y nodejs-lts microsoft-openjdk17
```

3. Assim que aparecer para ditar o aceite dos termos, aperte digite A e de Enter/Return e espere o download ser finalizado

4. Para verificar a instalação, tente rodar ```node --version``` e ```java --version```, caso os dois retornem o nome da dependência e a versão, está tudo certo

Pronto, com isso feito, todas as dependências necessárias já foram instaladas para rodar soluções em seu ambiente

## Criar um novo ambiente para rodar React Native em aparelho físico

> [!NOTE]
> Caso opte por utilizar o emulador gerado pelo Android Studio, seguindo os passos em [Configurar com Android Studio](#configurar-com-android-studio), apenas abra o aplicativo que foi criado e acesse em "More Options" o item "AVD Manager", siga os passos de seleção do aparelho e pronto, apenas rode: ```npm run-android``` em seu projeto quando quiser que o emulador seja aberto automaticamente

Realize todos os passos da seção 

1. Vá no site do Android Studio e desça até a área de downloads;

---

### Configurar com Android Studio

> [!TIP]
> Acesse o site de configuração de ambiente do [React-Native](https://reactnative.dev/docs/environment-setup), abra a aba de ```React Native CLI Quickstart``` e siga os passos descritos

### Descrição para não ter de acessar o site oficial

1. Acesse os downloads do Android Studio e baixe a versão mais recente;
   
2. Abra o instalador e siga o padrão de todas as configurações que forem aparecendo

3. Após isso uma tela de Boas Vindas será aberta, na aba Projects, clique no botão More Actions e selecione ```SDK Manager```

4. Abra a aba de "SDK Platforms" e verifique se a caixa de Android SDK Platform 34 está marcada

5. Abra também, a aba de "SDK Tools", marque a caixa de "Show Package Details", desça e procure por Android SDK Build-Tools e verifique se a versão selecionada é a última lançada (atualmente 34.0.0)

6. Por fim, clique em "Apply" e espere a instalação finalizar

7. Caso não tenha feito nenhuma alteração de onde o SDK seria instalado, abra o "Explorador de Arquivos" e na barra de pesquisa digite:

```
%LOCALAPPDATA%\Android\Sdk
```

Copie o caminho até a pasta do SDK

8. Após isso, abra a barra de pesquisa do Windows e pesquise por "Variáveis de Ambiente"

9. Quando abrir, clique no botão "Variáveis de Ambiente";

10. Seja em sistema para geral ou usuário para mudar somente para o seu acesso, clique em Novo e digite as seguintes informações:

Nome da variável: ANDROID_HOME

Valor da variável: Cole o caminho para a pasta do SDK

Devendo estar algo semelhante a isto:

![image](https://github.com/AnakonStar/notas-gerais-de-desenvolvimento/assets/107694439/b0adece1-89be-4849-9e71-ee3cce2b5e25)

Dessa forma, clique em "OK" e verifique se ela apareceu na tabela em que foi inserida

11. Por fim, abra novamente o "Explorador de Arquivos" e digite na barra de pesquisa, caso também não tenha alterado a pasta da SDK, o seguinte comando:

```
%LOCALAPPDATA%\Android\Sdk\platform-tools
```

Copie o caminho até a pasta do SDK Platform-tools

13. Abra novamente as "Váriáveis de Ambiente" caso tenha fechado, procure o item Path/PATH, clique nele e vá em Editar

14. Clique na lateral em Novo e cole o caminho que você copiou para as platform-tools, clicando em "OK" assim que finalizar

---

### Configurar com cmdline-tools

1. Acesse os downloads do cmdline-tools e baixe a versão mais recente;

2. Descompacte o zip/rar dentro um diretório de sua preferência;

3. Abra a pasta do cmdline-tools e acesse a pasta bin;

4. Copie o caminho na barra de diretório do Explorador de Arquivos;

5. Agora, abra a barra de pesquisa do Windows e pesquise por "Variáveis de Ambiente";

6. Quando abrir, clique no botão "Variáveis de Ambiente";

7. Seja em sistema para geral ou usuário para mudar somente para o seu acesso, vá no item Path/PATH, clique nele e vá em Editar;

8. Clique em Novo e cole o caminho para a pasta bin dentro de cmdline-tools;

9. Abra o terminal/cmd e digite: 
```
$ sdkmanager --install "platforms;android-30" "build-tools;30.0.3" "platform-tools"
```
> [!NOTE]
> Caso de um erro dizendo que o arquivo sdkmanager, não está localizado dentro do diretório descrito no erro, va na pasta cmdline-tools, crie uma pasta com o nome de latest e coloque todos os arquivos além desta pasta, dentro; Por fim feche e tente rodar o install novamente.

10. Antes de começar a baixar, irá perguntar se aceita os termos, digite "y" ou apenas aperte Return/Enter (não aceitar os termos, irá finalizar o processo e não instalar nada, processo esse que geralmente é demorado, melhor não rodar o comando e esquecer la);

11. Com isso feito, irá ser gerado, alguns arquivos dentro de uma pasta chamada plataform-tools, da mesma forma que copiou o diretório de bin, copie o diretório desta pasta;

12. Acesse as "Variáveis de Ambiente" mais uma vez, acesse o mesmo Path/PATH que adicionou a pasta bin, clique em Novo e cole o diretório de plataform-tools e clique em "OK";

---

Com tudo isso feito, seu ambiente já estará adequado para rodar um aplicativo React Native dentro de um aparelho físico, que esteja conectado na mesma rede/IP em que o projeto está rodando;

> [!TIP]
> Caso deseje espelhar a tela do seu celular direto no computador, aconselho o uso do aplicativo Vysor, instale ele e faça todo o processo descrito em [Espelhar aparelho físico no computador](#espelhar-aparelho-físico-no-computador).

## Espelhar aparelho físico no computador

Antes de iniciar, certifique-se de ter feitos os passo em [Criar um novo ambiente para rodar React-Native em aparelho físico](#criar-um-novo-ambiente-para-rodar-react-native-em-aparelho-físico) antes de iniciar este.

1. Vá no site do software Vysor pelo seu computador, e siga os passos para baixá-lo;

2. Após terminar o download, vá em seu aparelho físico e libere o acesso de desenvolvedor e va na guia Opções de desenvolvedor dentro das configurações de acessibilidade (pode variar dependendo do aparelho, então pesquise para o seu em específico como liberar o acesso);

3. Dentro desta pasta, vá em Depuração por USB e ative essa opção, em seguida, conecte seu aparelho no computador por meio de um cabo USB;

4. Para verificar se ele está realmente conectado, abra o cmd e digite:
```
$ adb devices
```
Resposta ideal:
```
List of devices attached

... // Identificador do aparelho
```
Caso tenha recebido a resposta ideal citada acima, seu aparelho está conectado e pronto para ser usado dentro do Vysor;

> [!NOTE]
> Caso esteja vázio, verifique se o aparelho está realmente conectado em uma porta funcional USB e caso já não tenha permitido nenhuma vez antes, aperte no botão de Permitir acesso no seu aparelho, quando a caixa de pergunta aparecer perguntando se aceita a conexão

---

### Rodar por meio da conexão Wi-Fi:

1. Fazendo tudo até o passo anterior, acesse as Opções de desenvolvedor novamente no seu aparelho e procure pela opção Depurar via Wi-Fi e então abra ela na tela;

2. Ative esta opção e em seguida aceite todas as caixas de mensagem que aparecerem (caso não esteja usando, sempre lembre-se de desligar está opção, mantem seu aparelho seguro de acessos externos para depuração);

3. Feito isso, apenas olhe o IP e a porta que estarão descritos em baixo do switch de ativar;

4. Agora no seu computador, acesse o cmd e digite:
```
$ adb connect seu_ip:porta
```
Resposta ideal:
```
Device connected
```
E em seguida rode:
```
$ adb devices
```
Resposta ideal:
```
List of devices attached

... online/device // Hash do IP do seu aparelho, juntamente com o estado dele, caso desconecte, irá aparecer como offline, mas manter ali
```
> Com isso feito, apenas siga os passos comuns já citados, que tudo deverá rodar sem problemas e sem a necessidade de cabos conectados, apenas lembre-se que caso desligar a tela do celular, todo o processo terá de ser repetido, pois a porta muda sempre que o aparelho é desfocado, fazendo assim com que a porta determinada dentro deste comando, sejá inutilizada, irá aparecer como offline, mas manter ele na lista, caso queira que ele saia dali, rode o seguinte comando no cmd:
```
$ adb disconnect seu_ip:porta_antiga
```
Resposta ideal: 
```
Device disconnected
```
E em seguida rode:
```
$ adb devices
```
Resposta ideal:
```
List of devices attached

... online/device  // Deverá aparecer somente um item na listagem, com o hash do IP e a nova porta do seu aparelho
```
---

5. Abra o software Vysor no seu computador e clique no icone de play, no aparelho que estiver com o mesmo nome do seu;

6. Feito isso surgirá uma caixa de pergunta no seu aparelho, perguntando se deseja mesmo instalar o Vysor a partir da Conexão/Depuração USB/Wi-Fi, clique em Baixar/Sim e espere até que o processo sejá finalizado;

7. Com isso feito, clique novamente no botão de play e espere até abrir uma nova guia com o espelhamento em tempo real do seu aparelho.

> [!TIP]
> Vale notar que caso desligue a tela do aparelho, o Vysor ira desconectar, e terá de ser feita a tentativa de acessar a tela novamente na guia do espelhamento

