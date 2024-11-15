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

## EndPoints Extras

#### GET /users
 Esse endpoint é responsável por buscar e retornar todos os usuários cadastrados no banco de dados.

#### Corpo da requisição
Nenhum corpo é necessário para essa requisição.

#### Respostas
##### OK 200
Caso essa resposta aconteça, todos os usuários foram recuperados com sucesso do banco de dados.

Exemplo de resposta:
```
[
  {
    "id": 1,
    "firstName": "Nome do Usuário",
    "lastName": "Sobrenome do Usuário",
    "email": "email@gmail.com"
  },
  {
    "id": 2,
    "firstName": " Nome2",
    "lastName": "Sobrenome2",
    "email": "email2@gmail.com"
  }
]
```
##### Erro interno 500
Essa falha ocorre quando há um problema ao tentar recuperar os dados do banco de dados.

Exemplo de resposta:
```
{
  "message": "Erro ao buscar usuários",
  "error": "Detalhes do erro"
}
```

#### GET /users/:id
 Esse endpoint é responsável por buscar e retornar um usuário específico com base no id fornecido como parâmetro de rota.
#### Parâmetros de Rota
id (número): O identificador único do usuário que será buscado.

#### Respostas
##### OK 200
Caso essa resposta aconteça, o usuário foi encontrado com sucesso e retornado.

Exemplo de resposta:
```
{
  "id": 1,
  "firstName": "Nome do Usuário",
  "lastName": "Sobrenome do Usuário",
  "email": "email@exemplo.com"
}
```
##### Falha na requisição 400
Essa falha ocorre quando o id fornecido não é um número válido.

Exemplo de resposta:
```
{
  "message": "ID inválido"
}
```
##### Usuário não encontrado 404
Essa falha ocorre quando não existe um usuário com o id fornecido.

Exemplo de resposta:
```
{
  "message": "Usuário não encontrado"
}
```
##### Erro interno do servidor 500
Essa falha ocorre quando há um problema ao tentar recuperar os dados do banco de dados.
Exemplo de resposta:
```
{
  "message": "Erro ao buscar usuário",
  "error": "Detalhes do erro"
}
```

#### DELETE /users/:id
 Esse endpoint é responsável por deletar um usuário específico com base no id fornecido como parâmetro de rota.

#### Parâmetros de Rota
id (número): O identificador único do usuário que será deletado.

#### Respostas
##### OK 200
Caso essa resposta aconteça, o usuário foi deletado com sucesso.

Exemplo de resposta:
```
{
  "message": "Usuário deletado com sucesso"
}
```
##### Falha na requisição 400
Essa falha ocorre quando o id fornecido não é um número válido.

Exemplo de resposta:
```
{
  "message": "ID inválido"
}
```
##### Usuário não encontrado 404
Essa falha ocorre quando não existe um usuário com o id fornecido.

Exemplo de resposta:
```
{
  "message": "Usuário não encontrado"
}
```
##### Erro interno do servidor 500
Essa falha ocorre quando há um problema ao tentar deletar o usuário no banco de dados.

Exemplo de resposta:
```
{
  "message": "Erro ao deletar usuário",
  "error": "Detalhes do erro"
}
```

#### PUT /users/:id
Esse endpoint é responsável por atualizar as informações de um usuário específico com base no id fornecido como parâmetro de rota. Os campos a serem atualizados são enviados no corpo da requisição.

#### Parâmetros de Rota
id (número): O identificador único do usuário que será atualizado.
#### Parâmetros de Rota
```
{
  "firstName": "Novo Nome",
  "lastName": "Novo Sobrenome",
  "email": "novoemail@exemplo.com"
}
```
Os campos no corpo da requisição são opcionais. Caso algum campo não seja fornecido, o valor atual do usuário será mantido para aquele campo.

#### Respostas
##### OK 200
Caso essa resposta aconteça, o usuário foi atualizado com sucesso.

Exemplo de resposta:
```
{
  "message": "Usuário atualizado com sucesso",
  "user": {
    "id": 1,
    "firstName": "Novo Nome",
    "lastName": "Novo Sobrenome",
    "email": "novoemail@exemplo.com"
  }
}
```
##### Falha na requisição 400
Essa falha ocorre quando o id fornecido não é um número válido.
Exemplo de resposta:
```
{
  "message": "ID inválido"
}
```
##### Usuário não encontrado 404
Essa falha ocorre quando não existe um usuário com o id fornecido.

Exemplo de resposta:
```
{
  "message": "Usuário não encontrado"
}
```
##### Erro interno do servidor 500
Essa falha ocorre quando há um problema ao tentar atualizar o usuário no banco de dados.

Exemplo de resposta:
```
{
  "message": "Erro ao atualizar usuário",
  "error": "Detalhes do erro"
}
```
