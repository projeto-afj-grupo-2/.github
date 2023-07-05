## Chat Manager API
Explicação da API


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


### 4. Retorna uma url de imagem

```http
  POST /api/generate/
```

**Retorna:**

Array de url de imagem baseada no prompt retornado pelo `POST /api/chat/prompt/:id`, gerada pelo DALL-E.
