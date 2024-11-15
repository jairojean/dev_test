# API de cadastro de usuários e de postagens
Esta API permite criar novos usuários e postagens associadas a esses usuários.

## Endpoints

#### POST /users
Esse endpoint é responsável por inserir novos usuários no banco de dados.

#### Corpo da requisição
```
{
  "firstName": "Nome do Usuário",
  "lastName": "Sobrenome do Usuário",
  "email": "email@exemplo.com"
}
```
#### Respostas
##### OK 201
Caso essa resposta aconteça, o usuário foi cadastrado com sucesso no banco de dados.

Exemplo de resposta:
```
{
  "id": 1,
  "firstName": "Nome do Usuário",
  "lastName": "Sobrenome do Usuário",
  "email": "email@exemplo.com"
}
```

##### Falha na autenticação!400
Essa falha ocorre quando algum campo obrigatório está ausente ou contém valores inválidos.
Exemplo de resposta:
```
{
  "error": "Campos obrigatórios ausentes ou inválidos"
}
```

#### POST /post
Esse endpoint é responsável por inserir novas postagens no banco de dados, associando-as a um usuário existente.

#### Corpo da requisição
```
{
  "title": "Título da Postagem",
  "description": "Descrição da Postagem",
  "userId": 1
}
```
#### Respostas
##### OK 201
Caso essa resposta aconteça, a postagem foi cadastrada com sucesso no banco de dados.

Exemplo de resposta:
```
{
  "title": "Título da Postagem",
  "description": "Descrição da Postagem",
  "user": {
    "id": 1,
    "firstName": "Nome do Usuário",
    "lastName": "Sobrenome do Usuário",
    "email": "email@exemplo.com"
  }
}
```
##### Falha na autenticação!400
Essa falha ocorre quando algum campo obrigatório está ausente ou contém valores inválidos.
Exemplo de resposta:
```
{
    "message": "Campos obrigatórios não preenchidos"
}
```