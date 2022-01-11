# json-server-base

Esse é o repositório com a base de JSON-Server + JSON-Server-Auth já configurada, feita para ser usada no desenvolvimento de um sistema que integra empresas a usuários. E que usuários podem solicitar a entrega dos produtos disponibilizados pelas empresas.

## Endpoints

Assim como a documentação do JSON-Server-Auth traz (https://www.npmjs.com/package/json-server-auth), existem 3 endpoints que podem ser utilizados para cadastro e 2 endpoints que podem ser usados para login.
<br><br>

# Users

<br>

### <strong> \* CADASTRO \*</strong>

- POST /register <br/>
- POST /signup <br/>
- POST /users

<pre>
Formato da Requisição - 

{<br>
    "email": "fulano@mail.com",<br>
    "password": "123456",<br>
    "nome": "Fulano",<br>
    "age": 40<br>
}

Formato da Resposta - 

{<br>
    "accessToken": "token",<br>
    "user": {<br>
        "email": "fulano@mail.com",<br>
        "nome": "Fulano",<br>
        "age": 40,<br>
        "id": 3<br>
    }
}
</pre>

Qualquer um desses 3 endpoints irá cadastrar o usuário na lista de "Users", sendo que os campos obrigatórios são os de email e password.
Você pode ficar a vontade para adicionar qualquer outra propriedade no corpo do cadastro dos usuários.<br><br><br>

### <strong> \* LOGIN \*</strong>

- POST /login <br/>
- POST /signin

Qualquer um desses 2 endpoints pode ser usado para realizar login com um dos usuários cadastrados na lista de "Users"<br><br><br>

# Empresas<br>

### <strong> \* CADASTRO \*</strong>

- POST /empresas <br/>

<pre>
Formato da Requisição - 

{<br>
    "name": "Empresa Fulano",<br>
    "description": "Essa empresa é boa",<br>
    "produtos": [
        {
            "name": "gás",
            "price": 200.00
        }
    ],<br>
    "userId": número de id do usuário que quer cadastrar essa empresa
}

Formato da Resposta - 

{<br>
    "name": "Empresa Fulano",<br>
    "description": "Essa empresa é boa",<br>
    "produtos": [
        {
            "name": "gás",
            "price": 200.00
        }
    ],<br>
    "userId": "número do id do usuário que quer cadastrar essa empresa",
    "id": 1
}
</pre>

Esse endpoint pode ser usado para realizar o registro de uma nova empresa com um dos usuários cadastrados na lista de "Users"<br><br>

### <strong> \* LISTAR TODAS EMPRESAS \*</strong>

- GET /empresas <br/>

Esse endpoint listará todos as empresas cadastradas no sistema<br><br><br>

# Produtos<br>

### <strong> \* CADASTRO \*</strong>

- POST /produtos <br/>

<pre>
Formato da Requisição - 

{
    "name": "água mineral",
}

Formato da Resposta - 

{
    "name": "Empresa Fulano",<br>
    "userId": número do id do usuário que quer cadastrar esse produto,
    "id": 1
}
</pre>

Esse endpoint pode ser usado para realizar o registro de um novo produto com um dos usuários cadastrados na lista de "Users"<br><br>

### <strong> \* LISTAR TODOS OS PRODUTOS \*</strong>

- GET /produtos <br/>

Esse endpoint listará todos os produtos, mas é necessário que o usuário esteja logado para visualizar.
