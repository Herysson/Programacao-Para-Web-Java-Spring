# Aula 09 - Prática MenuStream

Nesta atividade, os registros do sistema **MenuStream** devem ser cadastrados, alterados e removidos utilizando os dados abaixo.

## Produto

1. **Clássico Bacon**

```json
{
    "nome": "Clássico Bacon",
    "descricao": "Pão brioche, hambúrguer 180g, queijo cheddar, bacon crocante e maionese especial.",
    "preco": 29.90,
    "categoria": "Hambúrguer",
    "disponibilidade": true,
    "imagem": "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQNMEyVsK2Sb0hq8ZJDPBRQkKzwZ2lICuPAqw&s"
}
```

2. **Duplo Queijo**

```json
{
    "nome": "Duplo Queijo",
    "descricao": "Hambúrguer com queijo cheddar duplo, picles e molho especial.",
    "preco": 32.90,
    "categoria": "Hambúrguer",
    "disponibilidade": true,
    "imagem": "SUA IMAGEM AQUI"
}
```

3. **Frango Especial**

```json
{
    "nome": "Frango Especial",
    "descricao": "Peito de frango grelhado, alface, tomate e molho ranch.",
    "preco": 27.50,
    "categoria": "Hambúrguer",
    "disponibilidade": true,
    "imagem": "SUA IMAGEM AQUI"
}
```

4. **Vegetariano**

```json
{
    "nome": "Vegetariano",
    "descricao": "Hambúrguer artesanal de grão-de-bico, quinoa, alface, tomate e molho da casa.",
    "preco": 26.90,
    "categoria": "Hambúrguer",
    "disponibilidade": true,
    "imagem": "SUA IMAGEM AQUI"
}
```

5. **Picante**

```json
{
    "nome": "Picante",
    "descricao": "Hambúrguer com queijo pepper jack, jalapeños e maionese apimentada.",
    "preco": 30.00,
    "categoria": "Hambúrguer",
    "disponibilidade": true,
    "imagem": "SUA IMAGEM AQUI"
}
```

6. **BBQ Bacon**

```json
{
    "nome": "BBQ Bacon",
    "descricao": "Hambúrguer com bacon crocante, anéis de cebola e molho barbecue.",
    "preco": 34.90,
    "categoria": "Hambúrguer",
    "disponibilidade": true,
    "imagem": "SUA IMAGEM AQUI"
}
```

7. **Burger de Peixe**

```json
{
    "nome": "Burger de Peixe",
    "descricao": "Filé de peixe crocante com molho tártaro e alface.",
    "preco": 28.90,
    "categoria": "Hambúrguer",
    "disponibilidade": true,
    "imagem": "SUA IMAGEM AQUI"
}
```

8. **Refrigerante Cola**

```json
{
    "nome": "Refrigerante Cola",
    "descricao": "Refrigerante sabor cola gelado.",
    "preco": 7.00,
    "categoria": "Bebida",
    "disponibilidade": true,
    "imagem": "SUA IMAGEM AQUI"
}
```

9. **Limonada**

```json
{
    "nome": "Limonada",
    "descricao": "Limonada natural preparada com limões frescos.",
    "preco": 8.50,
    "categoria": "Bebida",
    "disponibilidade": true,
    "imagem": "SUA IMAGEM AQUI"
}
```

10. **Cerveja Artesanal**

```json
{
    "nome": "Cerveja Artesanal",
    "descricao": "Cerveja artesanal local com sabor encorpado e suave.",
    "preco": 13.90,
    "categoria": "Bebida",
    "disponibilidade": true,
    "imagem": "SUA IMAGEM AQUI"
}
```

11. **Burger Misterioso**

```json
{
    "nome": "Burger Misterioso",
    "descricao": "Você se arrisca? Toda semana, nosso chef cria um novo hambúrguer com ingredientes secretos.",
    "preco": 36.90,
    "categoria": "Hambúrguer",
    "disponibilidade": true,
    "imagem": "SUA IMAGEM AQUI"
}
```

### Alterando um registro

1. **Clássico Bacon**

```json
{
    "nome": "Clássico Bacon",
    "descricao": "Pão brioche, hambúrguer 180g, queijo cheddar, bacon crocante e maionese especial.",
    "preco": 24.90,
    "categoria": "Hambúrguer",
    "disponibilidade": true,
    "imagem": "SUA IMAGEM AQUI"
}
```

### Remova um registro (desativar o registro)

11. **Burger Misterioso**

```json
{
    "nome": "Burger Misterioso",
    "descricao": "Você se arrisca? Toda semana, nosso chef cria um novo hambúrguer com ingredientes secretos.",
    "preco": 36.90,
    "categoria": "Hambúrguer",
    "disponibilidade": false,
    "imagem": "SUA IMAGEM AQUI"
}
```

## Cliente

1. **Alice Johnson**

```json
{
    "nome": "Alice Johnson",
    "email": "alice.johnson@example.com",
    "enderecoEntrega": "Rua Maple, 1234, Springfield, IL",
    "preferenciaPagamento": "Cartão de Crédito"
}
```

2. **Bob Smith**

```json
{
    "nome": "Bob Smith",
    "email": "bob.smith@example.com",
    "enderecoEntrega": "Rua Oak, 5678, Springfield, IL",
    "preferenciaPagamento": "Cartão de Débito"
}
```

3. **Carol White**

```json
{
    "nome": "Carol White",
    "email": "carol.white@example.com",
    "enderecoEntrega": "Rua Pine, 91011, Springfield, IL",
    "preferenciaPagamento": "Dinheiro"
}
```

4. **David Brown**

```json
{
    "nome": "David Brown",
    "email": "david.brown@example.com",
    "enderecoEntrega": "Rua Elm, 1213, Springfield, IL",
    "preferenciaPagamento": "PayPal"
}
```

5. **Eva Green**

```json
{
    "nome": "Eva Green",
    "email": "eva.green@example.com",
    "enderecoEntrega": "Rua Cedar, 1415, Springfield, IL",
    "preferenciaPagamento": "Apple Pay"
}
```

6. **Maxwell Mystery**

```json
{
    "nome": "Maxwell Mystery",
    "email": "max.mystery@example.com",
    "enderecoEntrega": "Rua Baker, 221B, Springfield, IL",
    "preferenciaPagamento": "Criptomoeda"
}
```

### Alterando registro

1. **Alice Johnson**

```json
{
    "nome": "Alice Johnson",
    "email": "alice.johnson@example.com",
    "enderecoEntrega": "Rua Maple, 1234, Springfield, IL",
    "preferenciaPagamento": "Cartão de Débito"
}
```

### Remova um Registro

6. **Maxwell Mystery**

```json
{
    "nome": "Maxwell Mystery",
    "email": "max.mystery@example.com",
    "enderecoEntrega": "Rua Baker, 221B, Springfield, IL",
    "preferenciaPagamento": "Criptomoeda"
}
```

## Pedido

1. **Pedido 1**

```json
{
    "clienteId": 1,
    "itensPedido": [
        {
            "produtoId": 1,
            "quantidade": 2
        },
        {
            "produtoId": 3,
            "quantidade": 1
        }
    ],
    "valorTotal": 96.03,
    "status": "concluido",
    "dataPedido": "2024-04-01T12:30:00Z",
    "dataEntrega": "2024-04-01T15:00:00Z"
}
```

2. **Pedido 2**

```json
{
    "clienteId": 2,
    "itensPedido": [
        {
            "produtoId": 2,
            "quantidade": 1
        },
        {
            "produtoId": 4,
            "quantidade": 3
        }
    ],
    "valorTotal": 124.96,
    "status": "em andamento",
    "dataPedido": "2024-04-02T13:00:00Z",
    "dataEntrega": null
}
```

3. **Pedido 3**

```json
{
    "clienteId": 3,
    "itensPedido": [
        {
            "produtoId": 5,
            "quantidade": 1
        },
        {
            "produtoId": 6,
            "quantidade": 2
        }
    ],
    "valorTotal": 109.78,
    "status": "concluido",
    "dataPedido": "2024-04-03T16:45:00Z",
    "dataEntrega": "2024-04-03T19:30:00Z"
}
```

4. **Pedido 4**

```json
{
    "clienteId": 4,
    "itensPedido": [
        {
            "produtoId": 7,
            "quantidade": 2
        },
        {
            "produtoId": 8,
            "quantidade": 1
        }
    ],
    "valorTotal": 71.28,
    "status": "pendente",
    "dataPedido": "2024-04-04T17:00:00Z",
    "dataEntrega": null
}
```

5. **Pedido 5**

```json
{
    "clienteId": 5,
    "itensPedido": [
        {
            "produtoId": 1,
            "quantidade": 3
        },
        {
            "produtoId": 9,
            "quantidade": 2
        }
    ],
    "valorTotal": 115.39,
    "status": "concluido",
    "dataPedido": "2024-04-05T20:30:00Z",
    "dataEntrega": "2024-04-05T23:00:00Z"
}
```

6. **Pedido 6**

```json
{
    "clienteId": 3,
    "itensPedido": [
        {
            "produtoId": 1,
            "quantidade": 50
        },
        {
            "produtoId": 10,
            "quantidade": 100
        }
    ],
    "valorTotal": 3185.00,
    "status": "concluido",
    "dataPedido": "2024-06-15T18:00:00Z",
    "dataEntrega": "2024-06-15T20:00:00Z"
}
```

Regra de negócio: cada pedido deve ter o valor `valorTotal` calculado com base no valor dos itens multiplicado pela quantidade, acrescido de 10% referente ao garçom.

Modifique o código para que funcione desta maneira.

Exemplo:

```text
valorTotal = soma(precoProduto * quantidade) + 10%
```

Ou seja:

```text
valorTotal = soma(precoProduto * quantidade) * 1.10
```

### Altere o pedido

1. **Pedido 1**

```json
{
    "clienteId": 1,
    "itensPedido": [
        {
            "produtoId": 1,
            "quantidade": 4
        },
        {
            "produtoId": 3,
            "quantidade": 1
        }
    ],
    "valorTotal": 161.81,
    "status": "concluido",
    "dataPedido": "2024-04-01T12:30:00Z",
    "dataEntrega": "2024-04-01T15:00:00Z"
}
```
