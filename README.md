
# PizzaDemo - API RESTful

Projeto backend desenvolvido para a disciplina de Desenvolvimento Web com foco em APIs RESTful. O sistema simula uma pizzaria com funcionalidades de cadastro de usuários, login com autenticação JWT e pedidos.

## Tecnologias utilizadas

- Java 17
- Spring Boot 3.2.4
- Spring Security
- Spring Data JPA
- MySQL
- JWT (Json Web Token)
- Maven

## Como rodar o projeto

1. Clonar ou descompactar o projeto

2. Criar um banco de dados MySQL com o nome `pizzaria`:

```sql
CREATE DATABASE pizzaria;
```

3. Ajustar o arquivo `src/main/resources/application.properties` com as credenciais do banco:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/pizzaria
spring.datasource.username=pizzaiolo
spring.datasource.password=1q2w3e4r5t
```

4. No terminal, na raiz do projeto, executar:

```bash
mvn clean install
mvn spring-boot:run
```

A aplicação iniciará na porta `8081`.

## Endpoints disponíveis

### Usuários

- `POST /usuarios`  
  Cadastra um novo usuário  
  Corpo:
  ```json
  {
    "nome": "Theo",
    "email": "theo@email.com",
    "senha": "123456"
  }
  ```

- `POST /login`  
  Autentica o usuário e retorna um token JWT  
  Corpo:
  ```json
  {
    "email": "theo@email.com",
    "senha": "123456"
  }
  ```

### Pizzas

(necessário autenticação com token JWT no header `Authorization`)

- `GET /pizzas`  
  Lista todas as pizzas

- `GET /pizzas/{id}`  
  Detalha uma pizza

- `POST /pizzas`  
  Cadastra nova pizza

- `PUT /pizzas/{id}`  
  Edita uma pizza

- `DELETE /pizzas/{id}`  
  Remove uma pizza

## Testes

Os testes foram feitos usando o Postman:

1. Primeiro, cria-se o usuário com o endpoint `/usuarios`
2. Depois, realiza-se o login em `/login`
3. O token retornado é usado no header `Authorization` como:
   ```
   Bearer seu_token_aqui
   ```
4. Com isso é possível acessar os demais endpoints protegidos

## Observações

Este projeto foi baseado em um protótipo criado no Figma para a parte de front-end, mas aqui está focado apenas no backend. JWT foi implementado manualmente sem bibliotecas externas além do `jjwt`.
