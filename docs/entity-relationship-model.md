# Modelo Entidade Relacionamento (MER)
A seguir, apresenta-se o Modelo Entidade Relacionamento (MER) do sistema de contas digitais, que representa a estrutura do banco de dados relacional:

## Entidades
1. Customer (cliente)

- A entidade "Customer" armazena informações sobre os clientes do sistema.

| Atributo |   Tipo       | NotNull |
|:--------:|:------------:|:-------:|
| id (PK)  | bigint       | Sim     |
| name     | varchar(100) | Sim     |
| cpf      | varchar(100) | Sim     |
| email    | varchar(100) | Sim     |

2. Account (conta)
- A entidade "Account" representa as contas digitais dos clientes.

| Atributo         |   Tipo      | NotNull |
|:----------------:|:-----------:|:-------:|
| id (PK)          | bigint      | Sim     |
| account_type     | varchar(15) | Sim     |
| balance          | decimal     | Sim     |
| custumer_id (FK) | bigint      | Sim     |

3. Transaction (Movimentação)
- A entidade "Transaction" registra as operações de depósito e saque realizadas nas contas.

| Atributo        |   Tipo      | NotNull |
|:---------------:|:-----------:|:-------:|
| id (PK)         | bigint      | Sim     |
| type            | varchar(15) | Sim     |
| amount          | decimal     | Sim     |
| created_at      | timestamp   | Sim     |
| account_id (FK) | bigint      | Sim     |

## Relacionamentos
A entidade "Account" tem um relacionamento (N, 1) com a entidade "Customer", indicando que várias contas podem estar associadas a um único cliente.

A entidade "Transaction" tem um relacionamento (N, 1) com a entidade "Account", indicando que várias movimentações podem estar associadas a uma única conta.

## Chaves
- A chave primária da entidade "Customer" é o atributo "id".
- A chave primária da entidade "Account" é o atributo "id".
- A chave primária da entidade "Transaction" é o atributo "id".

## Chaves Estrangeiras
- O atributo "customer_id" na entidade "Account" é uma chave estrangeira referenciando a chave primária "id" da entidade "Customer".
- O atributo "conta_id" na entidade "Transaction" é uma chave estrangeira referenciando a chave primária "id" da entidade "Account".

## Observações
- O atributo "type" na entidade "Transaction" pode assumir os valores "DEPOSIT" ou "WITHDRAWAL" para representar o tipo de operação realizada.

- O atributo "created_at" na entidade "Transaction" representa a data em que a movimentação foi realizada.

- Os atributos "id" em todas as entidades são autoincrementáveis, ou seja, gerados automaticamente pelo banco de dados ao criar um novo registro.

Este é o Modelo Entidade Relacionamento (MER) que serve como base para a estrutura do banco de dados do sistema de contas digitais.