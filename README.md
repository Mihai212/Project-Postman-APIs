# <h1 align="center">Postman API Project</h1>
<h3 align="center">Documentation here 👉: <a href="https://github.com/vdespa/Postman-Complete-Guide-API-Testing/blob/main/simple-grocery-store-api.md">API Documentation</a></h3>

<h3 align="center"> "This API allows you to place a grocery order which will be ready for pick-up in the store." </h1>



## Endpoints
- [Status](#Status)
- [Products](#Products)
  - [Get all products](#Get-all-products)
  - [Get a product](#Get-a-product)
- [Cart](#Cart)
  - [Create a new cart](#Create-a-new-cart)
  - [Get a cart](#Get-a-cart)
  - [Get cart items](#Get-cart-items)
  - [Add an item to cart](#Add-an-item-to-cart)
  - [Modify an item in the cart](#Modify-an-item-in-the-cart)
  - [Replace an item in the cart](#Replace-an-item-in-the-cart)
  - [elete an item in the cart](#Delete-an-item-in-the-cart)
- [API Authentication](#API-Authentication)
  - [Register a new API client](#Register-a-new-API-client)
- [Orders](#Orders)
  - [Get all orders](#Get-all-orders)
  - [Get a single order](#Get-a-single-order)
  - [Create a new order](#Create-a-new-order)
  - [Update an order](#Update-an-order)
  - [Delete an order](#Delete-an-order)





#
## Status

1. Click on "Status" folder;
2. Click on "Status" request;
3. Select "GET" method;
4. Type in the empty field "{{baseURL}}/status";
5. Click on "Send" to send the request;
6. Positive result: 200 OK.
   
<img align="center" alt="Status" width="1300" src="https://i.ibb.co/K6n12K0/1-Status.png">






## Products
### A. Get all products

1. Click on "Get all products" folder;
2. Click on "Get all products" request;
3. Select "GET" method;
4. Type in the empty field "{{baseURL}}/products"
6. Click on "Send" to send the request;
7. Positive result: 200 OK
8. Should be displayed the id, category, name and valability of all the products from the grocery store.
   
<img align="center" alt="Status" width="1300" src="https://i.ibb.co/TM0fs0D/2-Get-all-products-1.png">





### B. Get all products

1. Complete in "Query Params" with relevant info like in the photo bellow:
   
| Name        | Type    | In    | Required | Description                                                                                                                                          |
| ----------- | ------- | ----- | -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| `category`  | string  | query | No       | Specifies the category of products you want to be returned. It can be one of: meat-seafood, fresh-produce, candy, bread-bakery, dairy, eggs, coffee. |
| `results`   | integer | query | No       | Specifies the number of results you want. Must be number between 1 and 20. By default, only 20 products will be displayed.                           |
| `available` | boolean | query | No       | Specifies the availability of the products. By default, all products will be displayed.                                                              |

2. Click on "Send" to send the request;
3. Positive result: 200 OK;
4. Should be displayed the just the "meat-seafood" products, the number and the availability of products selected.
   
<img align="center" alt="Status" width="1300" src="https://i.ibb.co/VJ5Xtq0/3-Get-all-products-2.png">





## C. Get a product

1. Click on "Get a product" request;
2. Select "GET" method;
3. Type in the empty field "{{baseURL}}/products/:productId";
4. Complete in "Query Params" and "Path Variables" with relevant info like in the photo below:

| Name            | Type    | In    | Required | Description                                      |
| --------------- | ------- | ----- | -------- | ------------------------------------------------ |
| `productId`     | integer | path  | Yes      | Specifies the product's id you wish to retrieve. |
| `product-label` | boolean | query | No       | Returns the product label in PDF format.         |
   
5. Positive result: 200 OK
6. Should be displayed the product with its data: Id, Category, Name, Manufacturer, Price, Current-Stock, InStock.
   
<img align="center" alt="Status" width="1300" src="https://i.ibb.co/DbJTLyj/4-Get-a-product.png">





## Cart
### A. Create a new Cart

1. Click on "Create a new cart" folder;
2. Click on Create a new cart" request;
3. Select "POST" method;
4. Type in the empty field "{{baseURL}}/carts";
5. Click on "Send";
6. Positive result: 201 Created
7. Should be displayed in "Body" a result like this example bellow:

```
{
   "created": true,
   "cartId": "bx0-ycNjqIm5IvufuuZ09"
}
```
   
<img align="center" alt="Status" width="1300" src="https://i.ibb.co/wZqKDb8/5-Create-A-New-Cart.png">






### B. Get a cart

1. Click on "Get a cart" request;
2. Select "GET" method;
3. Type in the empty field "{{baseURL}}/carts/:cartId";
4. Complete in "Path Variables" with relevant info like in the photo bellow:

| Name     | Type   | In   | Required | Description                                        |
| -------- | ------ | ---- | -------- | -------------------------------------------------- |
| `cartId` | string | path | Yes      | Specifies the id of the cart you wish to retrieve. |

4. Click on "Send";
5. Positive result: 200 OK
6. Should be displayed in "Body" a result like this example bellow:

<img align="center" alt="Status" width="1300" src="https://i.ibb.co/NVRCSS0/6-Get-A-Cart.png">






### C. Get cart items

1. Click on "Get cart items" request;
2. Select "Get" method;
3. Type in the empty field "{{baseURL}}/carts/:cartId/items";
4. Complete in "Path Variables" with relevant info like in the photo bellow:

 Name     | Type   | In   | Required | Description                                                            |
| -------- | ------ | ---- | -------- | ---------------------------------------------------------------------- |
| `cartId` | string | path | Yes      | Specifies the id of the cart for which you wish to retrieve the items. |

4. Click on "Send";
5. Positive result: 200 OK
6. Should be displayed in "Body" a result like this example bellow:

<img align="center" alt="Status" width="1300" src="https://i.ibb.co/yq1XJkw/6-Get-Cart-Items.png">




### D. Add an item to cart

1. Click on "Add an item to cart" request;
2. Select "POST" method;
3. Type in the empty field "{{baseURL}}/carts/:cartId/items";
4. Complete in "Path Variables" with relevant info like in the photo bellow:

| Name        | Type    | In   | Required | Description                                         |
| ----------- | ------- | ---- | -------- | --------------------------------------------------- |
| `cartId`    | string  | path | Yes      | Specifies the cart id.                              |
| `productId` | integer | body | Yes      | Specifies the product id                            |
| `quantity`  | integer | body | No       | If no quantity is provided, the default value is 1. |

<img align="center" alt="Status" width="1300" src="https://i.ibb.co/spTL7S0/7-Add-an-Item-To-Cart-1.png">

5. Click On "Body"-> raw-> JSON;
6. Complete with data required in tabel above; an example:

```
{
   "productId": 4646
   "quantity": 2
}
```
7. Click on "Send";
8. Positive result: 201 Created;
9. Should be displayed the item created and the itemId like in the photo bellow.

<img align="center" alt="Status" width="1300" src="https://i.ibb.co/gwQmjGb/7-Add-an-Item-To-Cart-2.png">






### E. Modify an item

1. Click on "Modify an item" request;
2. Select "PATCH" method;
3. Type in the empty field "{{baseURL}}/carts/:cartId/items/:itemId";
4. Complete in "Path Variables" with relevant info like in the photo bellow:

| Name       | Type    | In   | Required | Description            |
| ---------- | ------- | ---- | -------- | ---------------------- |
| `cartId`   | string  | path | Yes      | Specifies the cart id. |
| `itemId`   | string  | path | Yes      | Specifies the item id. |
| `quantity` | integer | body | Yes      | Quantity               |

<img align="center" alt="Status" width="1300" src="https://i.ibb.co/qJpJJ7g/8-Modify-An-Item-In-The-Cart-1.png">

4. Complete in "Body" with relevant info like in the photo bellow:
4. Click on "Send";
5. Positive result: 204 No Content
6. Should be displayed in "Body" a result like this example bellow:

<img align="center" alt="Status" width="1300" src="https://i.ibb.co/Chydj4Z/8-Modify-An-Item-In-The-Cart-2.png">





### F. Replace an item in the cart

1. Click on "Replace an item in the cart" request;
2. Select "PUT" method;
3. Type in the empty field "{{baseURL}}/carts/:cartId/items/:itemId";
4. Complete in "Path Variables" and "Body" with relevant info like in the photo bellow:

| Name        | Type    | In   | Required | Description               |
| ----------- | ------- | ---- | -------- | ------------------------- |
| `cartId`    | string  | path | Yes      | Specifies the cart id.    |
| `itemId`    | string  | path | Yes      | Specifies the item id.    |
| `productId` | integer | body | Yes      | Specifies the product id. |
| `quantity`  | integer | body | No       | Quantity                  |

<img align="center" alt="Status" width="1300" src="https://i.ibb.co/r3XzxYC/Replace-an-item-in-the-cart.png">

4. Complete in "Body" (JSON format) with relevant info like in the photo bellow:
5. Click on "Send";
6. Positive result: 204 No Content
7. Should be displayed in "Body" a result like this example bellow:

<img align="center" alt="Status" width="1300" src="https://i.ibb.co/Xkzdfhd/Replace-an-item-in-the-cart-2.png">





### G. Delete an item in the cart

1. Click on "Delete an item in the cart" request;
2. Select "DELETE" method;
3. Type in the empty field "{{baseURL}}/carts/:cartId/items/:itemId";
4. Complete in "Path Variables" with relevant info like in the photo bellow.
5. Positive result: 204 No Content
6. Should be displayed in "Body" a result like this example bellow;
7. 5. Click on "Send";
6. Positive result: 204 No Content

| Name        | Type   | In   | Required | Description             |
| ----------- | ------ | ---- | -------- | ----------------------- |
| `cartId`    | string | path | Yes      | Specifies the cart id.  |
| `itemId`    | string | path | Yes      | Specifies the item id.  |


<img align="center" alt="Status" width="1300" src="https://i.ibb.co/gdpD0pz/Delete-an-item-in-the-cart.png">




## API Authentification
### Register a new API

1. Click on "API Authentification" folder;
2. Click on "Register a new APIt" request;
3. Select "POST" method
4. Type in the empty field "{{baseURL}}/api-clients";
5. Go to "Body"-> raw-> JSON
6. Type in "Body" relevant data like in the photo bellow.
7. Click on "Send";
8. Positive result: 201 Created
9. Should be displayed in "Body" a result like this example bellow:

| Name          | Type   | In   | Required | Description                            |
| ------------- | ------ | ---- | -------- | -------------------------------------- |
| `clientName`  | string | body | Yes      | The name of the API client.            |
| `clientEmail` | string | body | Yes      | The email address of the API client. * |
   
<img align="center" alt="Status" width="1300" src="https://i.ibb.co/T2QPtB4/9-Register-A-New-API.png">


## Orders
### A. Create a new order

1. Click on "Orders" folder;
2. Click on "Create a new order" request;
3. Select "POST" method;
4. Type in the empty field "{{baseURL}}/orders";
5. Go to "Body"-> raw-> JSON
6. Type in "Body" relevant data like in the photo bellow.
7. Click on "Send";
8. Positive result: 201 Created
9. Should be displayed in "Body" a result like this example bellow:

| Name            | Type   | In     | Required | Description                          |
| --------------- | ------ | ------ | -------- | ------------------------------------ |
| `Authorization` | string | header | Yes      | The bearer token of the API client.  |
| `cartId`        | string | body   | Yes      | The cart id                          |
| `customerName`  | string | body   | Yes      | The name of the customer.            |
| `comment`       | string | body   | No       | A comment associated with the order. |
   
<img align="center" alt="Status" width="1300" src="https://i.ibb.co/hRNhKbv/10-Create-A-New-Order.png">



### B. Get a single order

2. Click on "Get a single order" request;
3. Select "GET" method;
4. Type in the empty field "{{baseURL}}/orders";
5. Complete the "Path"Body"-> raw-> JSON
6. Complete in "Path Variables" with relevant data like in the photo bellow.

| Name            | Type    | In     | Required | Description                         |
| --------------- | ------- | ------ | -------- | ----------------------------------- |
| `Authorization` | string  | header | Yes      | The bearer token of the API client. |
| `orderId`       | string  | path   | Yes      | The order id.                       |
| `invoice`       | boolean | query  | No       | Show the PDF invoice.               |
   
<img align="center" alt="Status" width="1300" src="https://i.ibb.co/sVGJkLr/11-Get-A-Single-Order.png">

7. Complete in "Headers" with relevant data like in the photo bellow.
6. Click on "Send";
7. Positive result: 200 OK
8. Should be displayed in "Body" a result like this example bellow.

<img align="center" alt="Status" width="1300" src="https://i.ibb.co/BzpsjMZ/12-Get-A-Single-Order.png">



### C. Get all orders

2. Click on "Get all orders" request;
3. Select "GET" method;
4. Type in the empty field "{{baseURL}}/orders";
5. Complete in "Headers" with relevant data like in the photo bellow.
6. Click on "Send";
7. Positive result: 200 OK
8. Should be displayed in "Headers" a result like this example bellow.

| Name            | Type    | In     | Required | Description                         |
| --------------- | ------- | ------ | -------- | ----------------------------------- |
| `Authorization` | string  | header | Yes      | The bearer token of the API client. |
| `orderId`       | string  | path   | Yes      | The order id.                       |
| `invoice`       | boolean | query  | No       | Show the PDF invoice.               |
   
<img align="center" alt="Status" width="1300" src="https://i.ibb.co/zW3TV5H/13-Get-All-Orders.png">



### C. Update an order

2. Click on "Update an order" request;
3. Select "PATCH" method;
4. Type in the empty field "{{baseURL}}/orders/:orderId";
5. Complete in "Headers", "Path Variables" and "Body" with relevant data like in the photo bellow.

| Name            | Type   | In     | Required | Description                          |
| --------------- | ------ | ------ | -------- | ------------------------------------ |
| `Authorization` | string | header | Yes      | The bearer token of the API client.  |
| `orderId`       | string | path   | Yes      | The order id.                        |
| `customerName`  | string | body   | No       | The name of the customer.            |
| `comment`       | string | body   | No       | A comment associated with the order. |

<img align="center" alt="Status" width="1300" src="https://i.ibb.co/WKhRxbB/14-Update-An-Order-1.png">
<img align="center" alt="Status" width="1300" src="https://i.ibb.co/ZzsLwSJ/14-Update-An-Order-2.png">

6. Click on "Send";
7. Positive result: 200 OK
8. Should be displayed in "Headers" a result like this example bellow.

<img align="center" alt="Status" width="1300" src="https://i.ibb.co/b73XQTw/14-Update-An-Order-3.png">
