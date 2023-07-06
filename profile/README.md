# 🛒 E-commerce xyz

📚 Trabalho prático da Pós-Graduação em Arquitetura de Software Distribuído da PUC Minas, da matéria Arquitetura de Software com Framework Java mestrada pelo professor, Samuel Almeida Cardoso.

## Integrantes:

- Augusto Custodio Vicente
- Brayan Patrick Jardim Farias
- Carolina Fernandes Serrano Lopes
- Celso Henrique Alvarenga Barros
- Luiz Gabriel Santos Fernandes
- Savastane Santana de Andrade

## 🎯 Objetivos 

- Objetivo Geral: Construir um chatbot de assistente pessoal que utiliza a API OpenAI para responder perguntas e realizar tarefas específicas.

- Objetivo Específico: Construir um chatbot que utiliza a API OpenAI para guiar o cliente à construção de um estilo de roupa para a compra, incluindo demonstração por imagens (Integração com o DALL-E).

## 💻 Funcionalidades

- Iniciar uma conversa com o contexto de um assistente de chat de um e-commerce
- Questionar o cliente sobre o estilo e informações pessoais
- Geração de imagem de manequim, utilizada para a melhor visualização do produto

## Stacks utilizadas

**Front-end:** React-js, Node 18, Vite

**Chat Manager API:** Spring 3.1, Java 17

**Image Generator API:** Spring 3.1, Java 17

## Documentos e links apoio

- OpenAI: https://platform.openai.com/docs/introduction/overview
- DALL-E: https://platform.openai.com/docs/guides/images/introduction

## C4-Model

[Insert image](https://miro.com/app/board/uXjVM6VZXiw=/)

### Chat Web Interface 
Explicação 

#### Instalação e execução

[README Interface](https://github.com/projeto-afj-grupo-2/shop-assitant-webapp#readme)

### Chat Manager API
Explicação da API

#### Instalação e execução

[README Chat Manager](https://github.com/projeto-afj-grupo-2/gptprojectdemo#readme)

#### Descrição dos Endpoints

##### 1. Inicia uma conversa, e retorna o id dela

```http
  POST /api/chat/
```
**Conteúdo do *body*:**


**Retorna:**

| Parâmetro   | Tipo       | Descrição                                              |
| :---------- | :--------- | :------------------------------------------------------|
| `id`        | `string`   | Id da conversa gerado pela API, esse id é único para cada conversa iniciada.|

##### 2. Continua uma conversa com o mesmo contexto histórico, baseado no id da conversa

```http
  POST /api/chat/:id
```
| Parâmetro   | Tipo       | Descrição                                                                                          |
| :---------- | :--------- | :--------------------------------------------------------------------------------------------------|
| `id`        | `string`   | **Obrigatório**, Id único da conversa, gerado pela chamada `POST /api/chat/`|

**body:**

| Parâmetro   | Tipo       | Descrição                                                                                          |
| :---------- | :--------- | :------------------------------------------------------------|
| `context`       | `string`| **Obrigatório**, Resposta do usuário em texto livre|
| `role`          | `string`| **Obrigatório**, Tipo de usuário (system \| assistant \| user)|
| `interationType`| `string`| **Obrigatório**, Tipo de interação () (predefinida pelas regras de negócio)|

##### 3. Retorna uma string com o prompt para a chamada do DALL-E

```http
  POST /api/chat/prompt/:id
```
| Parâmetro   | Tipo       | Descrição                                                                                          |
| :---------- | :--------- | :--------------------------------------------------------------------------------------------------|
| `id`        | `string`   | **Obrigatório**, gera um prompt de texto em inglês com todo o contexto relacionado ao(s) produto(s) da conversa.|

### Image Generator API

#### Instalação e execução

[README Image Generator](https://github.com/projeto-afj-grupo-2/ai-request-generator#readme)

#### Descrição dos Endpoints

##### 4. Retorna uma url de imagem

```http
  POST /api/generate/
```

**Retorna:**

Array de url de imagem baseada no prompt retornado pelo `POST /api/chat/prompt/:id`, gerada pelo DALL-E.

## Problemas

- Entender o contexto correto de assistente virtual de uma loja de camiseta, blusa e calça, em certos momentos ele gerava uma simulação de conversa entre um vendendor e um cliente

- Lidar com a continuidade de contexto, visto que precisamos de um certo passo-a-passo para que seja realizada a venda de cada tipo de produto

- Manter o entendimento de cada passo-a-passo (em certos momentos o chat oferecia produtos que o contexto não apontou disponibilidade. Ex.: Acessórios, brincos, etc.)

- Problemas de conexão com a API da OpenAI

## Soluções

- Enviar um contexto inicial, com um enunciado bem escrito, usando a `role = system`

- Criar um passo-a-passo de perguntas restritas e lineares, para cada caso, que chamamos de `interactionType`

- Melhorar o enunciado (tentativa e erro)

- ¯\_(ツ)_/¯ (Aqui poderiam ser feitos tratamentos de conexão nos casos de 500, ou até usar o próprio ChatGPT para checar se a resposta dele fez sentido ou não, além disso tratamentos de acordo com o `finish_reason` que a própria API retorna. (FYK - [Documentação OpenAI > Finish Reason](https://platform.openai.com/docs/guides/gpt/chat-completions-response-format))

## Demonstração


## Melhorias


## Aprendizados

