# API de Gerenciamento de Clientes e Endereços

Este projeto é uma API RESTful desenvolvida em Spring Boot para gerenciar clientes e seus endereços. A API permite criar, atualizar, buscar e deletar clientes e seus respectivos endereços, utilizando listas estáticas para armazenamento de dados.

# Funcionalidades
## Clientes:

- Criar um novo cliente.
- Buscar todos os clientes.
- Buscar um cliente específico por CPF.
- Atualizar um cliente existente por CPF.
- Deletar um cliente por CPF.

 
## Endereços:

- Adicionar um novo endereço a um cliente específico.
- Buscar todos os endereços de um cliente.
- Atualizar um endereço específico de um cliente por CEP.
- Deletar um endereço de um cliente por CEP.

  
# Estrutura da API
A API está estruturada em dois principais recursos: **Clientes** e **Endereços**. Todos os endpoints estão sob o prefixo `http://localhost:8080/api`.

# Endpoints

## Clientes

### 1. Listar Todos os Clientes
- **Método**: `GET`
- **Endpoint**: `/api/cliente`
- **Descrição**: Retorna uma lista de todos os clientes.

### 2. Buscar Cliente por CPF
- **Método**: `GET`
- **Endpoint**: `/api/cliente/buscar/{cpf}`
- **Descrição**: Busca um cliente específico pelo CPF.
- **Resposta**: 
  - **200 OK**: Retorna o cliente encontrado.
  - **404 NOT FOUND**: Se o cliente não for encontrado.

### 3. Adicionar Novo Cliente
- **Método**: `POST`
- **Endpoint**: `/api/cliente`
- **Descrição**: Adiciona um novo cliente.
- **Body**:
  ```json
  {
    "nome": "Anonimo",
    "email": "email@exemplo.com",
    "cpf": "710.721.210-93",
    "dataNascimento": "YYYY-MM-DD",
    "telefone": "(21)99999-9999"
  }
  
Resposta:
201 CREATED: Retorna o cliente criado.
400 BAD REQUEST: Se CPF ou e-mail já existirem.

### 4. Atualizar Cliente
- **Método**: `PUT`
- **Endpoint**: `/api/cliente/atualizar/{cpf}`
- **Descrição**: Atualiza os dados de um cliente existente pelo CPF.
- **Body**: (mesmo formato do POST)
```json
  {
    "nome": "Anonimo",
    "email": "email@exemplo.com",
    "cpf": "710.721.210-93",
    "dataNascimento": "YYYY-MM-DD",
    "telefone": "(21)99999-9999"
  }
  ```
  
Respostas:
200 OK: Retorna o cliente atualizado.
404 NOT FOUND: Se o cliente não for encontrado.

### 5. Remover Cliente
- **Método**: `DELETE`
- **Endpoint**: `/api/cliente/{cpf}`
- **Descrição**: Remove um cliente pelo CPF.
  
Respostas:
204 NO CONTENT: Se removido com sucesso.
404 NOT FOUND: Se o cliente não existir.

## Endereços

###1. Adicionar um novo endereço a um cliente

- **URL**: `/api/cliente/{cpf}/endereco`
- **Método**: `POST`
- **Descrição**: Adiciona um endereco e vincula a um cpf de cliente cadastrado.
  
### Parâmetros:

- `{cpf}`: CPF do cliente.

### Corpo da Requisição:

```json
{
  "cep": "string",
  "rua": "string",
  "bairro": "string",
  "cidade": "string",
  "estado": "string",
  "numero": "string"
}
```

### 2. Buscar todos os endereços de um cliente
- **URL**: `/api/cliente/{cpf}/endereco`
- **Método**: `GET`
- **Descrição** : Retorna uma lista com todos os endereços vinculados ao cliente.
  
### Parâmetros:
{cpf}: CPF do cliente.

Respostas:
200 OK: Retorna a lista de endereços do cliente.
404 Not Found: Nenhum endereço encontrado para o cliente.

## 3. Atualizar um endereço de um cliente por CEP
- **URL**: `/api/cliente/{cpf}/endereco/{cep}`
- **Método**: `PUT`
  
### Parâmetros:

{cpf}: CPF do cliente.
{cep}: CEP do endereço a ser atualizado.

### Corpo da Requisição:

```json
{
  "cep": "string",
  "rua": "string",
  "bairro": "string",
  "cidade": "string",
  "estado": "string",
  "numero": "string"
}

```

## 4. Deletar um endereço de um cliente por CEP
- **URL**: `/api/cliente/{cpf}/endereco/{cep}`
- **Método**: `DELETE`
- 
### Parâmetros:
{cpf}: CPF do cliente.
{cep}: CEP do endereço a ser deletado.

Respostas:
204 No Content: Endereço deletado com sucesso.
404 Not Found: Endereço ou cliente não encontrado.

# Modelo de Dados

## Cliente 

json 
```
{
  "cpf": "string",
  "nome": "string",
  "email": "string",
  "telefone": "string",
  "dataNascimento": "YYYY-MM-DD"
}

```


## Endereço

json
```
{
  "cep": "string",
  "rua": "string",
  "bairro": "string",
  "cidade": "string",
  "estado": "string",
  "numero": "string",
  "cpfCliente": "string"
}

```
