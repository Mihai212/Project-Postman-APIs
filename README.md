# Postman-APIs

```json
{
	"info": {
		"_postman_id": "d4b878f2-4e21-4628-ae71-3ca2573c06a2",
		"name": "Endpoints",
		"schema": "https://schema.getpostman.com/json/collection/v2.1.0/collection.json",
		"_exporter_id": "31589930"
	},
	"item": [
		{
			"name": "Status",
			"item": [
				{
					"name": "Status",
					"request": {
						"method": "GET",
						"header": [],
						"url": {
							"raw": "{{baseURL}}/status",
							"host": [
								"{{baseURL}}"
							],
							"path": [
								"status"
							]
						}
					},
					"response": []
				}
			]
		},
		{
			"name": "Products",
			"item": [
				{
					"name": "Get all products",
					"event": [
						{
							"listen": "test",
							"script": {
								"exec": [
									"\r",
									"pm.test(\"Response status code is 200\", function () {\r",
									"    pm.expect(pm.response.code).to.equal(200);\r",
									"});\r",
									"\r",
									"\r",
									"pm.test(\"Response has the required fields - id, category, name, and inStock\", function () {\r",
									"    const responseData = pm.response.json();\r",
									"    \r",
									"    pm.expect(responseData).to.be.an('array');\r",
									"    responseData.forEach(function (product) {\r",
									"        pm.expect(product).to.include.all.keys('id', 'category', 'name', 'inStock');\r",
									"    });\r",
									"});\r",
									"\r",
									"\r",
									"pm.test(\"Category is a non-empty string\", function () {\r",
									"  const responseData = pm.response.json();\r",
									"  \r",
									"  pm.expect(responseData).to.be.an('array');\r",
									"  responseData.forEach(function(product) {\r",
									"    pm.expect(product.category).to.be.a('string').and.to.have.lengthOf.at.least(1, \"Category should not be empty\");\r",
									"  });\r",
									"});\r",
									"\r",
									"\r",
									"pm.test(\"Name is a non-empty string\", function () {\r",
									"  const responseData = pm.response.json();\r",
									"  \r",
									"  pm.expect(responseData).to.be.an('array');\r",
									"  responseData.forEach(function(product) {\r",
									"      pm.expect(product.name).to.be.a('string').and.to.have.lengthOf.at.least(1, \"Name should not be empty\");\r",
									"  });\r",
									"});\r",
									"\r",
									"\r",
									"pm.test(\"InStock is a boolean value\", function () {\r",
									"  const responseData = pm.response.json();\r",
									"  \r",
									"  pm.expect(responseData).to.be.an('array');\r",
									"  responseData.forEach(function(product) {\r",
									"    pm.expect(product.inStock).to.be.a('boolean');\r",
									"  });\r",
									"});\r",
									"\r",
									"pm.environment.get(\"variable_key\");"
								],
								"type": "text/javascript"
							}
						}
					],
					"request": {
						"method": "GET",
						"header": [],
						"url": {
							"raw": "{{baseURL}}/products",
							"host": [
								"{{baseURL}}"
							],
							"path": [
								"products"
							],
							"query": [
								{
									"key": "category",
									"value": "meat-seafood",
									"disabled": true
								},
								{
									"key": "results",
									"value": "20",
									"disabled": true
								},
								{
									"key": "available",
									"value": "true",
									"disabled": true
								}
							]
						}
					},
					"response": []
				},
				{
					"name": "Get a product",
					"request": {
						"method": "GET",
						"header": [],
						"url": {
							"raw": "{{baseURL}}/products/:productId?productId=4646&product-label=true",
							"host": [
								"{{baseURL}}"
							],
							"path": [
								"products",
								":productId"
							],
							"query": [
								{
									"key": "productId",
									"value": "4646"
								},
								{
									"key": "product-label",
									"value": "true"
								}
							],
							"variable": [
								{
									"key": "productId",
									"value": "4646"
								}
							]
						}
					},
					"response": []
				}
			]
		},
		{
			"name": "Cart",
			"item": [
				{
					"name": "Create a new cart",
					"request": {
						"method": "POST",
						"header": [],
						"url": {
							"raw": "{{baseURL}}/carts",
							"host": [
								"{{baseURL}}"
							],
							"path": [
								"carts"
							]
						}
					},
					"response": []
				},
				{
					"name": "Get a cart",
					"request": {
						"method": "GET",
						"header": [],
						"url": {
							"raw": "{{baseURL}}/carts/:cartId?cartId=zW_Avbf053WzQyj_XOfOy",
							"host": [
								"{{baseURL}}"
							],
							"path": [
								"carts",
								":cartId"
							],
							"query": [
								{
									"key": "cartId",
									"value": "zW_Avbf053WzQyj_XOfOy"
								}
							],
							"variable": [
								{
									"key": "cartId",
									"value": "zW_Avbf053WzQyj_XOfOy"
								}
							]
						}
					},
					"response": []
				},
				{
					"name": "Get cart items",
					"protocolProfileBehavior": {
						"disableBodyPruning": true
					},
					"request": {
						"method": "GET",
						"header": [],
						"body": {
							"mode": "raw",
							"raw": ""
						},
						"url": {
							"raw": "{{baseURL}}/carts/:cartId/items?cartId=zW_Avbf053WzQyj_XOfOy",
							"host": [
								"{{baseURL}}"
							],
							"path": [
								"carts",
								":cartId",
								"items"
							],
							"query": [
								{
									"key": "cartId",
									"value": "zW_Avbf053WzQyj_XOfOy"
								}
							],
							"variable": [
								{
									"key": "cartId",
									"value": "zW_Avbf053WzQyj_XOfOy"
								}
							]
						}
					},
					"response": []
				},
				{
					"name": "Add an item to cart",
					"request": {
						"method": "POST",
						"header": [],
						"body": {
							"mode": "raw",
							"raw": "{\r\n\"productId\": 8739,\r\n\"quantity\": 2\r\n}",
							"options": {
								"raw": {
									"language": "json"
								}
							}
						},
						"url": {
							"raw": "{{baseURL}}/carts/:cartId/items?cartId=2N4-Ps5b5NsReQY2hqPfk&productId=8739&quantity=2",
							"host": [
								"{{baseURL}}"
							],
							"path": [
								"carts",
								":cartId",
								"items"
							],
							"query": [
								{
									"key": "cartId",
									"value": "2N4-Ps5b5NsReQY2hqPfk"
								},
								{
									"key": "productId",
									"value": "8739"
								},
								{
									"key": "quantity",
									"value": "2"
								}
							],
							"variable": [
								{
									"key": "cartId",
									"value": "2N4-Ps5b5NsReQY2hqPfk"
								}
							]
						}
					},
					"response": []
				},
				{
					"name": "Modify an item In the cart",
					"request": {
						"method": "PATCH",
						"header": [],
						"body": {
							"mode": "raw",
							"raw": "{\r\n    \"quantity\": 3\r\n}",
							"options": {
								"raw": {
									"language": "json"
								}
							}
						},
						"url": {
							"raw": "{{baseURL}}/carts/:cartId/items/:itemId?cartId=2N4-Ps5b5NsReQY2hqPfk&itemId=992715279",
							"host": [
								"{{baseURL}}"
							],
							"path": [
								"carts",
								":cartId",
								"items",
								":itemId"
							],
							"query": [
								{
									"key": "cartId",
									"value": "2N4-Ps5b5NsReQY2hqPfk"
								},
								{
									"key": "itemId",
									"value": "992715279"
								}
							],
							"variable": [
								{
									"key": "cartId",
									"value": "2N4-Ps5b5NsReQY2hqPfk"
								},
								{
									"key": "itemId",
									"value": "992715279"
								}
							]
						}
					},
					"response": []
				},
				{
					"name": "Delete an item in the cart",
					"request": {
						"method": "DELETE",
						"header": [],
						"body": {
							"mode": "raw",
							"raw": "",
							"options": {
								"raw": {
									"language": "json"
								}
							}
						},
						"url": {
							"raw": "{{baseURL}}/carts/:cartId/items/:itemId?cartId=2N4-Ps5b5NsReQY2hqPfk&itemId=147368152",
							"host": [
								"{{baseURL}}"
							],
							"path": [
								"carts",
								":cartId",
								"items",
								":itemId"
							],
							"query": [
								{
									"key": "cartId",
									"value": "2N4-Ps5b5NsReQY2hqPfk"
								},
								{
									"key": "itemId",
									"value": "147368152"
								}
							],
							"variable": [
								{
									"key": "cartId",
									"value": "2N4-Ps5b5NsReQY2hqPfk"
								},
								{
									"key": "itemId",
									"value": "147368152"
								}
							]
						}
					},
					"response": []
				}
			]
		},
		{
			"name": "API authentification",
			"item": [
				{
					"name": "Register a new API",
					"request": {
						"method": "POST",
						"header": [],
						"body": {
							"mode": "raw",
							"raw": "{\r\n\"clientName\": \"Test\",\r\n\"clientEmail\": \"tester@test.com\"\r\n}\r\n",
							"options": {
								"raw": {
									"language": "json"
								}
							}
						},
						"url": {
							"raw": "{{baseURL}}/api-clients?clientName&clientEmail",
							"host": [
								"{{baseURL}}"
							],
							"path": [
								"api-clients"
							],
							"query": [
								{
									"key": "clientName",
									"value": null
								},
								{
									"key": "clientEmail",
									"value": null
								}
							]
						}
					},
					"response": []
				}
			]
		},
		{
			"name": "Orders",
			"item": [
				{
					"name": "Create a new order",
					"request": {
						"method": "POST",
						"header": [
							{
								"key": "Authorization",
								"value": "9d232d998ef50944aa5cb07908f58556500b536d85380fc06d454cb618a4de8c",
								"type": "text"
							}
						],
						"body": {
							"mode": "raw",
							"raw": "{\r\n    \"cartId\": \"4uKfe4EIwbrnCnPo5sYvO\",\r\n    \"customerName\": \"Mihai\"\r\n}",
							"options": {
								"raw": {
									"language": "json"
								}
							}
						},
						"url": {
							"raw": "{{baseURL}}/orders",
							"host": [
								"{{baseURL}}"
							],
							"path": [
								"orders"
							]
						}
					},
					"response": []
				},
				{
					"name": "Get a single order",
					"request": {
						"method": "GET",
						"header": []
					},
					"response": []
				},
				{
					"name": "Get all orders",
					"request": {
						"method": "GET",
						"header": [
							{
								"key": "Authorization",
								"value": "9d232d998ef50944aa5cb07908f58556500b536d85380fc06d454cb618a4de8c",
								"type": "text"
							}
						],
						"url": {
							"raw": "{{baseURL}}/orders",
							"host": [
								"{{baseURL}}"
							],
							"path": [
								"orders"
							]
						}
					},
					"response": []
				},
				{
					"name": "Update an order",
					"request": {
						"method": "PATCH",
						"header": [
							{
								"key": "Authorization",
								"value": "9d232d998ef50944aa5cb07908f58556500b536d85380fc06d454cb618a4de8c",
								"type": "text"
							}
						],
						"body": {
							"mode": "raw",
							"raw": "{\r\n    \"customerNName\":\"Michael\"\r\n}",
							"options": {
								"raw": {
									"language": "json"
								}
							}
						},
						"url": {
							"raw": "{{baseURL}}/orders/:orderId",
							"host": [
								"{{baseURL}}"
							],
							"path": [
								"orders",
								":orderId"
							],
							"variable": [
								{
									"key": "orderId",
									"value": "NIC1BVjsZrjcnlEDwyZYV"
								}
							]
						}
					},
					"response": []
				},
				{
					"name": "Delete an order",
					"request": {
						"method": "DELETE",
						"header": [
							{
								"key": "Authorization",
								"value": "9d232d998ef50944aa5cb07908f58556500b536d85380fc06d454cb618a4de8c",
								"type": "text"
							}
						],
						"url": {
							"raw": "{{baseURL}}/orders/:orderId",
							"host": [
								"{{baseURL}}"
							],
							"path": [
								"orders",
								":orderId"
							],
							"variable": [
								{
									"key": "orderId",
									"value": "NIC1BVjsZrjcnlEDwyZYV"
								}
							]
						}
					},
					"response": []
				}
			]
		}
	],
	"event": [
		{
			"listen": "prerequest",
			"script": {
				"type": "text/javascript",
				"exec": [
					""
				]
			}
		},
		{
			"listen": "test",
			"script": {
				"type": "text/javascript",
				"exec": [
					""
				]
			}
		}
	],
	"variable": [
		{
			"key": "baseURL",
			"value": "https://simple-grocery-store-api.glitch.me",
			"type": "string"
		}
	]
}
