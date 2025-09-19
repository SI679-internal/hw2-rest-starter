# HW 2 - Build a Basic REST API

## Instructions
1. Clone this repo to your development machine. Use NPM to install the dependencies.
2. Work on it, solve the problems.
3. Add, commit, and push frequently.
4. Be sure to push your final submission before the deadline.
5. Also submit the assignment on Canvas, including your repo link and a statement about your use of AI.

## About
This starter repo contains implementations for the routes we did in class during week 4. Refer to the lecture notes for details, seed data for your database, and the JSON format for each model. The already implemented routes are crossed out below, and your job is to implement the rest of them.

- `/customers`
    - GET: get all customers
    - POST: create new customer
- `/customers/:id`
    - GET: get the customer with `id`
    - PATCH: update the customer with `id` using provided fields
    - DELETE: delete the customer with `id`
- `/products`
    - ~~GET: get all products~~
    - ~~POST: create new product~~
- `/products/:id`
    - ~~GET: get product with id `id`~~
    - PATCH: update the product with `id` using provided fields
    - ~~DELETE: delete product with `id`~~
- `/customers/:id/orders`
    - GET: get all orders for customer with `id`
    - ~~POST: create new order for customer with `id`~~
- `/customers/:customerId/orders/:orderId`
    - GET: get the specified order
    - PATCH: update the specified order with the fields provided
    - DELETE: delete the specified order

| Requirement | Description | Points |
| :------- | :------ | :------- |
| 1-9     | Each route | 10    |
| 10   | Appropriate use of each layer  | 30 |
| | TOTAL | 120 |


## Extra Credit

1. Without changing the structure of any Mongo documents, modify both GET routes for customer orders (both with and without `:orderId`) so that the JSON returned to the client includes product details, like so:

```{
  "customerId": "68c97e1f66193b427809baa9",
  "status": "started"
  "items": {
    "68c9b15da3fee3a2a1721c00": {
      "quantity": "1",
      "modelName": "BrewSense 12 Cup Drip Coffee Maker",
      "modelNumber": "KF7150BK",
      "manufacturer": "Braun",
      "color": "Stainless Steel and Black",
      "price": 129.95,
      "quantityInStock": 78
    },
  },
},
```

2. (Can only be done after #1) Modify `PATCH /customers/:customerId/orders/:orderId` so that any "extra" product fields (anything other than `quantity`) are kept out of the `orders` collection in MongoDB. So a `PATCH` that provides this JSON in the body:

```{
  "customerId": "68c97e1f66193b427809baa9",
  "status": "started"
  "items": {
    "68c9b15da3fee3a2a1721c00": {
      "quantity": "5",
      "modelName": "BrewSense 12 Cup Drip Coffee Maker",
      "modelNumber": "KF7150BK",
      "manufacturer": "Braun",
      "color": "Stainless Steel and Black",
      "price": 129.95,
      "quantityInStock": 78
    },
  },
},
```

Should result in a Document in MongoDB like this:

```{
  "customerId": "68c97e1f66193b427809baa9",
  "status": "started"
  "items": {
    "68c9b15da3fee3a2a1721c00": {
      "quantity": "1",
    },
  },
},
```

| Requirement | Description | Points |
| :------- | :------ | :------- |
| XC1    | Modify GET routes for `.../orders/*` | 2    |
| XC2   | Fix PATCH route for `.../orders/*` | 2 |
| | TOTAL | 4 |