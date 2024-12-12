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
- [Orders](#Orders)
  - [Get all orders](#Get-all-orders)
  - [Get a single order](#Get-a-single-order)
  - [Create a new order](#Create-a-new-order)
  - [Update an order](#Update-an-order)
  - [Delete an order](#Delete-an-order)
- [API Authentication](#API-Authentication)
  - [Register a new API client](#Register-a-new-API-client)
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

1. Complete in "Query Params" with relevant info like in the photo below:
   
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
7. Should be displayed in "Body" a result like this example below:

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
4. Complete in "Path Variables" with relevant info like in the photo below:

| Name     | Type   | In   | Required | Description                                        |
| -------- | ------ | ---- | -------- | -------------------------------------------------- |
| `cartId` | string | path | Yes      | Specifies the id of the cart you wish to retrieve. |

4. Click on "Send";
5. Positive result: 200 OK
6. Should be displayed in "Body" a result like this example below:

<img align="center" alt="Status" width="1300" src="https://i.ibb.co/NVRCSS0/6-Get-A-Cart.png">

### C. Get cart items

1. Click on "Get cart items" request;
2. Select "Get" method;
3. Type in the empty field "{{baseURL}}/carts/:cartId/items";
4. Complete in "Path Variables" with relevant info like in the photo below:

 Name     | Type   | In   | Required | Description                                                            |
| -------- | ------ | ---- | -------- | ---------------------------------------------------------------------- |
| `cartId` | string | path | Yes      | Specifies the id of the cart for which you wish to retrieve the items. |

4. Click on "Send";
5. Positive result: 200 OK
6. Should be displayed in "Body" a result like this example below:

<img align="center" alt="Status" width="1300" src="https://i.ibb.co/yq1XJkw/6-Get-Cart-Items.png">

### D. Add an item to cart

1. Click on "Add an item to cart" request;
2. Select "POST" method;
3. Type in the empty field "{{baseURL}}/carts/:cartId/items";
4. Complete in "Path Variables" with relevant info like in the photo below:

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
9. Should be displayed the item created and the itemId like in the photo below.

<img align="center" alt="Status" width="1300" src="https://i.ibb.co/gwQmjGb/7-Add-an-Item-To-Cart-2.png">
