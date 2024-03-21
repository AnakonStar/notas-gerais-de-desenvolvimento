# Anotações gerais para arrumar problemas comuns e construir um ambiente de desenvolvimento

## Criar um novo ambiente para rodar React Native em aparelho físico

1º Vá no site do Android Studio e desça até a área de downloads;

2º Baixe a versão mais recente do cmdline-tools (para não ter de baixar o editor, emulador e SDK do Android Studio);

3º Descompacte o zip/rar dentro um diretório de sua preferência;

4º Abra a pasta do cmdline-tools e acesse a pasta bin;

5º Copie o caminho na barra de diretório do Explorador de Arquivos;

6º Agora, abra a barra de pesquisa do Windows e pesquise por Variáveis de Ambiente;

7º Quando abrir, clique no botão Variáveis de Ambiente;

8º Seja em sistema para geral ou usuário para mudar somente para o seu acesso, vá no item Path/PATH, clique nele e vá em Editar;

9º Clique em Novo e cole o caminho para a pasta bin dentro de cmdline-tools;

10º Abra o terminal/cmd e digite: 
```
$ sdkmanager --install "platforms;android-30" "build-tools;30.0.3" "platform-tools"
```
NOTA: Caso de um erro dizendo que o arquivo sdkmanager, não está localizado dentro do diretório descrito no erro, va na pasta cmdline-tools, crie uma pasta com o nome de latest e coloque todos os arquivos além desta pasta, dentro; Por fim feche e tente rodar o install novamente.

11º Antes de começar a baixar, irá perguntar se aceita os termos, digite "y" ou apenas aperte Return/Enter (não aceitar os termos, irá finalizar o processo e não instalar nada, processo esse que geralmente é demorado, melhor não rodar o comando e esquecer la);

12º Com isso feito, irá ser gerado, alguns arquivos dentro de uma pasta chamada plataform-tools, da mesma forma que copiou o diretório de bin, copie o diretório desta pasta;

13º Acesse as Variáveis de Ambiente mais uma vez, acesse o mesmo Path/PATH que adicionou a pasta bin, clique em Novo e cole o diretório de plataform-tools, copiado;

14º Com tudo isso feito, seu ambiente já estará adequado para rodar um aplicativo React Native dentro de um aparelho físico, que esteja conectado na mesma rede/IP em que o projeto está rodando;

Adicional - Caso deseje espelhar a tela do seu celular direto no computador, aconselho o uso do aplicativo Vysor, instale ele e faça todo o processo descrito em [Espelhar aparelho físico no computador](#espelhar-aparelho-físico-no-computador).

## Espelhar aparelho físico no computador

Antes de iniciar, certifique-se de ter feitos os passo em [Criar um novo ambiente para rodar React-Native em aparelho físico](#criar-um-novo-ambiente-para-rodar-react-native-em-aparelho-físico) antes de iniciar este.

1º Vá no site do software Vysor pelo seu computador, e siga os passos para baixá-lo;

2º Após terminar o download, vá em seu aparelho físico e libere o acesso de desenvolvedor e va na guia Opções de desenvolvedor dentro das configurações de acessibilidade (pode variar dependendo do aparelho, então pesquise para o seu em específico como liberar o acesso);

3º Dentro desta pasta, vá em Depuração por USB e ative essa opção, em seguida, conecte seu aparelho no computador por meio de um cabo USB;

4º Para verificar se ele está realmente conectado, abra o cmd e digite:
```
$ adb devices
```
Resposta ideal:
```
List of devices attached

... // Identificador do aparelho
```
Caso tenha recebido a resposta ideal citada acima, seu aparelho está conectado e pronto para ser usado dentro do Vysor;

Nota: caso esteja vázio, verifique se o aparelho está realmente conectado em uma porta funcional USB e caso já não tenha permitido nenhuma vez antes, aperte no botão de Permitir acesso no seu aparelho, quando a caixa de pergunta aparecer perguntando se aceita a conexão

---

### Rodar por meio da conexão Wi-Fi:

1º Fazendo tudo até o passo anterior, acesse as Opções de desenvolvedor novamente no seu aparelho e procure pela opção Depurar via Wi-Fi e então abra ela na tela;

2º Ative esta opção e em seguida aceite todas as caixas de mensagem que aparecerem (caso não esteja usando, sempre lembre-se de desligar está opção, mantem seu aparelho seguro de acessos externos para depuração);

3º Feito isso, apenas olhe o IP e a porta que estarão descritos em baixo do switch de ativar;

4º Agora no seu computador, acesse o cmd e digite:
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
Com isso feito, apenas siga os passos comuns já citados, que tudo deverá rodar sem problemas e sem a necessidade de cabos conectados, apenas lembre-se que caso desligar a tela do celular, todo o processo terá de ser repetido, pois a porta muda sempre que o aparelho é desfocado, fazendo assim com que a porta determinada dentro deste comando, sejá inutilizada, irá aparecer como offline, mas manter ele na lista, caso queira que ele saia dali, rode o seguinte comando no cmd:
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

5º Abra o software Vysor no seu computador e clique no icone de play, no aparelho que estiver com o mesmo nome do seu;

6º Feito isso surgirá uma caixa de pergunta no seu aparelho, perguntando se deseja mesmo instalar o Vysor a partir da Conexão/Depuração USB/Wi-Fi, clique em Baixar/Sim e espere até que o processo sejá finalizado;

7º Com isso feito, clique novamente no botão de play e espere até abrir uma nova guia com o espelhamento em tempo real do seu aparelho.

Adicional - Vale notar que caso desligue a tela do aparelho, o Vysor ira desconectar, e terá de ser feita a tentativa de acessar a tela novamente na guia do espelhamento

