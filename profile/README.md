
# E-commerce xyz

📚 Trabalho prático da Pós-Graduação em Arquitetura de Software Distribuído da PUC Minas, da matéria Arquitetura de Software com Framework Java mestrada pelo professor, Samuel Almeida Cardoso.


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
- 
- 
- 
- 
- 





## Chat Manager API
Explicação da API

## Instalação

Instale...

## Como executar

Execute...

### 1. Inicia uma conversa, e retorna o id dela

```http
  POST /api/chat/
```
**Conteúdo do *body*:**


**Retorna:**

| Parâmetro   | Tipo       | Descrição                                              |
| :---------- | :--------- | :------------------------------------------------------|
| `id`        | `string`   | Id da conversa gerado pela API, esse id é único para cada conversa iniciada.|

### 2. Continua uma conversa com o mesmo contexto histórico, baseado no id da conversa

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

### 3. Retorna uma string com o prompt para a chamada do DALL-E

```http
  POST /api/chat/prompt/:id
```
| Parâmetro   | Tipo       | Descrição                                                                                          |
| :---------- | :--------- | :--------------------------------------------------------------------------------------------------|
| `id`        | `string`   | **Obrigatório**, gera um prompt de texto em inglês com todo o contexto relacionado ao(s) produto(s) da conversa.|

## Image Generator API

## Instalação

Instale my-project com npm

```bash
  npm install my-project
  cd my-project
```

### 4. Retorna uma url de imagem

```http
  POST /api/generate/
```

**Retorna:**

Array de url de imagem baseada no prompt retornado pelo `POST /api/chat/prompt/:id`, gerada pelo DALL-E.
## Demonstração



## Melhorias


## Aprendizados

