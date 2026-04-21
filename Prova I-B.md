# Avaliação Prática – Programação para Web (Java + Spring Boot + JPA + MySQL)

## Enunciado

Você deverá desenvolver uma API utilizando **Java com Spring Boot, JPA e MySQL**, simulando um **sistema de gerenciamento de pedidos de uma lanchonete/restaurante**.

O sistema deverá permitir o cadastro de **produtos**, **clientes** e o **registro de pedidos**, com cálculo automático do valor total do pedido.

A entrega consiste no desenvolvimento do backend completo com as funcionalidades descritas abaixo.

---

## Funcionalidades

1. **Cadastro de Produtos**
2. **Cadastro de Clientes**
3. **Registro de Pedidos**

Cada pedido deve conter:

* um cliente
* uma lista de itens
* cada item deve possuir:

  * produto
  * quantidade
  * valor unitário
* um campo calculado com o **valor total do pedido**
* um status do pedido, por exemplo:

  * `ABERTO`
  * `FINALIZADO`
  * `CANCELADO`

---

## Tecnologias obrigatórias

* Java + Spring Boot
* Spring Web
* Spring Data JPA
* MySQL
* Utilização de DTOs (`record` recomendado)
* Camadas bem definidas:

  * Controller
  * Service
  * Repository
  * Entity
  * DTO

---

## Critérios de Avaliação (Total: 10,0 pontos)

| Critério                                                                          |    Peso |
| --------------------------------------------------------------------------------- | ------: |
| CRUD completo e funcional de uma entidade (Cliente ou Produto)                    | 5,0 pts |
| Registro funcional de um pedido com cálculo correto do total                      | 2,0 pts |
| Criação do banco na integra                                                       |  1,0 pt |
| Uso de DTOs organizados e bem estruturados                                        |  1,0 pt |
| Camada de serviço com regras de negócio aplicadas corretamente                    |  1,0 pt |

---

## Regras de Negócio

* O valor total do pedido deve ser calculado com base na soma dos subtotais dos itens:

```text
total = soma(preço_unitário * quantidade) de cada item - desconto (se houver)
```

* Não deve ser permitido adicionar ao pedido uma quantidade de produto maior do que a disponível em estoque.
* Ao registrar um pedido, a quantidade do produto em estoque deve ser atualizada.
* O valor total deve ser retornado no DTO de resposta do pedido.
* Um pedido cancelado não deve alterar o estoque novamente, caso você opte por implementar cancelamento.

---

## Estrutura sugerida das entidades

<img width="388" height="507" alt="image" src="https://github.com/user-attachments/assets/9def30c8-780d-4fbf-83cd-3749ac8fcdb6" />

---

## Exemplos de Requisições em JSON

### Produto – Criar (POST)

```json
{
  "name": "X-Burger",
  "price": 18.50,
  "quantity": 20
}
```

### Cliente – Criar (POST)

```json
{
  "name": "Maria Oliveira",
  "email": "maria@email.com",
  "cpf": "123.456.789-00"
}
```

### Pedido – Criar (POST)

```json
{
  "clientId": 1,
  "items": [
    {
      "productId": 1,
      "quantity": 2,
      "unitPrice": 18.50
    },
    {
      "productId": 2,
      "quantity": 1,
      "unitPrice": 7.00
    }
  ]
}
```

### Pedido – Resposta (GET)

```json
{
  "id": 1,
  "client": {
    "id": 1,
    "name": "Maria Oliveira",
    "cpf": "123.456.789-00"
  },
  "items": [
    {
      "productId": 1,
      "productName": "X-Burger",
      "quantity": 2,
      "unitPrice": 18.50,
      "subTotal": 37.00
    },
    {
      "productId": 2,
      "productName": "Refrigerante Lata",
      "quantity": 1,
      "unitPrice": 7.00,
      "subTotal": 7.00
    }
  ],
  "status": "ABERTO",
  "total": 44.00,
  "createdAt": "2026-04-21T19:30:00"
}
```

---

## Entrega

* Suba o projeto no GitHub pessoal e compartilhe o link.
* O repositório deve conter:

  * código-fonte organizado
  * `README.md` com instruções para rodar o projeto
  * exemplos de endpoints e JSONs de teste

---

## Observações

* Você pode utilizar o Postman ou Insomnia para testar os endpoints.
* A implementação deve funcionar corretamente mesmo que o front-end não seja desenvolvido.
* A organização do código e a separação de responsabilidades entre as camadas também serão consideradas.

---
