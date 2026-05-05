## Product

1. **Classic Burger**
```json
{
    "name": "Classic Burger",
    "description": "Burger with beef patty, lettuce, tomato, and our special sauce.",
    "price": 8.99,
    "category": "Burger",
    "availability": true
}
```

2. **Cheese Lover's Burger**
```json
{
    "name": "Cheese Lover's Burger",
    "description": "Burger with double cheese, pickles, and mustard.",
    "price": 9.99,
    "category": "Burger",
    "availability": true
}
```

3. **Chicken Burger**
```json
{
    "name": "Chicken Burger",
    "description": "Grilled chicken breast with avocado and ranch dressing.",
    "price": 10.50,
    "category": "Burger",
    "availability": true
}
```

4. **Veggie Burger**
```json
{
    "name": "Veggie Burger",
    "description": "Made with a homemade patty of quinoa, beans, and sun-dried tomatoes.",
    "price": 9.50,
    "category": "Burger",
    "availability": true
}
```

5. **Spicy Burger**
```json
{
    "name": "Spicy Burger",
    "description": "Burger with jalapenos, pepper jack cheese, and spicy mayo.",
    "price": 10.00,
    "category": "Burger",
    "availability": true
}
```

6. **BBQ Bacon Burger**
```json
{
    "name": "BBQ Bacon Burger",
    "description": "Burger topped with crispy bacon, onion rings and BBQ sauce.",
    "price": 11.99,
    "category": "Burger",
    "availability": true
}
```

7. **Fish Burger**
```json
{
    "name": "Fish Burger",
    "description": "Crispy fish fillet with tartar sauce and lettuce.",
    "price": 9.99,
    "category": "Burger",
    "availability": true
}
```

8. **Coke**
```json
{
    "name": "Coke",
    "description": "Classic Coca-Cola, chilled.",
    "price": 1.99,
    "category": "Beverage",
    "availability": true
}
```

9. **Lemonade**
```json
{
    "name": "Lemonade",
    "description": "Freshly squeezed lemonade made with real lemons.",
    "price": 2.50,
    "category": "Beverage",
    "availability": true
}
```

10. **Craft Beer**
```json
{
    "name": "Craft Beer",
    "description": "Local craft beer with a rich and smooth taste.",
    "price": 3.99,
    "category": "Beverage",
    "availability": true
}
```

11. **Mystery Burger**
```json
{
    "name": "Mystery Burger",
    "description": "Dare to try it? Each week, our chef creates a new burger that keeps its ingredients a secret until you bite into it!",
    "price": 12.99,
    "category": "Burger",
    "availability": true
}
```

### Alterando um registro

1. **Classic Burger**
   
```json
{
    "name": "Classic Burger",
    "description": "Burger with beef patty, lettuce, tomato, and our special sauce.",
    "price": 6.99,
    "category": "Burger",
    "availability": true
}
```

### Remova um registro

11. **Mystery Burger**
```json
{
    "name": "Mystery Burger",
    "description": "Dare to try it? Each week, our chef creates a new burger that keeps its ingredients a secret until you bite into it!",
    "price": 12.99,
    "category": "Burger",
    "availability": true
}
```

## Customer

1. **Alice Johnson**
```json
{
    "name": "Alice Johnson",
    "email": "alice.johnson@example.com",
    "deliveryAddress": "1234 Maple St, Springfield, IL",
    "paymentPreferences": "Credit Card"
}
```

2. **Bob Smith**
```json
{
    "name": "Bob Smith",
    "email": "bob.smith@example.com",
    "deliveryAddress": "5678 Oak St, Springfield, IL",
    "paymentPreferences": "Debit Card"
}
```

3. **Carol White**
```json
{
    "name": "Carol White",
    "email": "carol.white@example.com",
    "deliveryAddress": "91011 Pine St, Springfield, IL",
    "paymentPreferences": "Cash"
}
```

4. **David Brown**
```json
{
    "name": "David Brown",
    "email": "david.brown@example.com",
    "deliveryAddress": "1213 Elm St, Springfield, IL",
    "paymentPreferences": "PayPal"
}
```

5. **Eva Green**
```json
{
    "name": "Eva Green",
    "email": "eva.green@example.com",
    "deliveryAddress": "1415 Cedar St, Springfield, IL",
    "paymentPreferences": "Apple Pay"
}
```

6. **Maxwell Mystery**
```json
{
    "name": "Maxwell Mystery",
    "email": "max.mystery@example.com",
    "deliveryAddress": "221B Baker Street, Springfield, IL",
    "paymentPreferences": "Cryptocurrency"
}
```

### Alterando registro

1. **Alice Johnson**
```json
{
    "name": "Alice Johnson",
    "email": "alice.johnson@example.com",
    "deliveryAddress": "1234 Maple St, Springfield, IL",
    "paymentPreferences": "Debit Card"
}
```

### Remova um Registro

6. **Maxwell Mystery**
```json
{
    "name": "Maxwell Mystery",
    "email": "max.mystery@example.com",
    "deliveryAddress": "221B Baker Street, Springfield, IL",
    "paymentPreferences": "Cryptocurrency"
}
```

## Order

1. **Order 1**
```json
{
    "customerId": 1,
    "orderDetails": [
        {
            "productId": 1,
            "quantity": 2
        },
        {
            "productId": 3,
            "quantity": 1
        }
    ],
    "totalAmount": 28.48,
    "status": "completed",
    "orderDate": "2024-04-01T12:30:00Z",
    "fulfillmentDate": "2024-04-01T15:00:00Z"
}
```

2. **Order 2**
```json
{
    "customerId": 2,
    "orderDetails": [
        {
            "productId": 2,
            "quantity": 1
        },
        {
            "productId": 4,
            "quantity": 3
        }
    ],
    "totalAmount": 45.00,
    "status": "in progress",
    "orderDate": "2024-04-02T13:00:00Z",
    "fulfillmentDate": null
}
```

3. **Order 3**
```json
{
    "customerId": 3,
    "orderDetails": [
        {
            "productId": 5,
            "quantity": 1
        },
        {
            "productId": 6,
            "quantity": 2
        }
    ],
    "totalAmount": 50.75,
    "status": "completed",
    "orderDate": "2024-04-03T16:45:00Z",
    "fulfillmentDate": "2024-04-03T19:30:00Z"
}
```

4. **Order 4**
```json
{
    "customerId": 4,
    "orderDetails": [
        {
            "productId": 7,
            "quantity": 2
        },
        {
            "productId": 8,
            "quantity": 1
        }
    ],
    "totalAmount": 35.90,
    "status": "pending",
    "orderDate": "2024-04-04T17:00:00Z",
    "fulfillmentDate": null
}
```

5. **Order 5**
```json
{
    "customerId": 5,
    "orderDetails": [
        {
            "productId": 1,
            "quantity": 3
        },
        {
            "productId": 9,
            "quantity": 2
        }
    ],
    "totalAmount": 76.20,
    "status": "completed",
    "orderDate": "2024-04-05T20:30:00Z",
    "fulfillmentDate": "2024-04-05T23:00:00Z"
}
```


6. **Order 6**

```json
{
    "customerId": 3,  
    "orderDetails": [
        {
            "productId": 1,  
            "quantity": 50 
        },
        {
            "productId": 10,  
            "quantity": 100 
        }
    ],
    "totalAmount": 1099.50,
    "status": "completed",
    "orderDate": "2024-06-15T18:00:00Z", 
    "fulfillmentDate": "2024-06-15T20:00:00Z"
}
```

Regra de negócio cada pedido deve ter o valor "totalAmount" calculado com base no valor dos itens * a quantidade + 10% do garçom.
Modifique o código para que funcione desta maneira.

### Altere o pedido


1. **Order 1**
```json
{
    "customerId": 1,
    "orderDetails": [
        {
            "productId": 1,
            "quantity": 4
        },
        {
            "productId": 3,
            "quantity": 1
        }
    ],
    "totalAmount": 38.46,
    "status": "completed",
    "orderDate": "2024-04-01T12:30:00Z",
    "fulfillmentDate": "2024-04-01T15:00:00Z"
}
```

