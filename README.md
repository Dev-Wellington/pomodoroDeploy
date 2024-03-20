# Pomodoro

O pomodoro é uma técnica que utiliza de loops de 25 minutos e intervalos de 5 minutos, para foco e estudo.




https://github.com/Dev-Wellington/pomodoroDeploy/assets/118689748/ac62d3f7-f9bb-4061-b946-3a41a52f43e5


## Instalação e configuração

### 1 - Clonar o repositóro
```
git clone link
```
### 2- Intalar o Node.js e o NPM 
Para instalar o Node é so seguir o passo a passo do site oficial.
``` 
https://nodejs.org/en
```
### Instalação do NPM 
Use o seguinte comando no terminal .
```
npm install 
```
## Iniciando o projeto de forma local
Utilize o comando para rodar de forma local.
```
npm run dev
```
## Usando o projeto pelo deploy

Acesse o link abaixo :

[Pomodoro](https://pomodorovue.netlify.app/)

## Desenvolvimento do projeto
Estrutura:
src/ : Codigo 
assets/ : Imagens e audios
components/ : Componentes do projeto

### Componentes

#### App.vue
Componente principal que agrupa todos os outros componentes.

#### Cabecalho.vue
Contém um cabeçalho com o título "Pomodoro" e uma imagem ilustrativa de um relógio.

#### Task.vue
Permite adicionar e remover tarefas.
Exibe um botão para abrir um formulário de adição de tarefas.
Apresenta as tarefas adicionadas, cada uma com um botão de remoção.

#### Pomodoro.vue
Exibe o tempo do temporizador em um título, onde o usuário pode visualizar o tempo restante.
Fornece botões para controlar o temporizador:
- Um botão que inicia ou para o temporizador, alternando entre "Start" e "Stop" dependendo do estado atual.
- Um botão para reiniciar o temporizador.
