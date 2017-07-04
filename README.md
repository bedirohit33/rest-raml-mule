**Outline**
----
	This is a Mulesoft project defining restful webservice for customers, orders and products using RAML.
	RAML api files -  src/main/api.
	Mule fow - src/main/app(Flows).

	I have also published this service on Anypoint Mulesoft Exchange. You can access the below link and check directly as well. 
	portal URL  - https://anypoint.mulesoft.com/apiplatform/not-employed/#/portals/organizations/8b4ea1ee-302d-411e-bcb9-93cebec9acb1/apis/23208096/versions/847172


**customer**
----
  1. Returns json data about all existing customers.
  2. Create a single new customer.
  3. Returns json data about a specific customer given {customerId}.
  4. Update a single existing customer given {customerId}. 
  5. Delete a single existing customer given {customerId}.

* **URL**
  
  /customers
  /customers/{customerId}

* **Fields**
    `customerId -  The unique ID associated with each customer 
    firstName - First name 
    lastName - Last name
    address - List of addresses  associated with each customer`
    
* **Methods:**

  `GET` | `POST` | `PLACE` | `DELETE`
  
**order**
----  
  1. Returns json data about all orders 
  2. Returns json data about all orders for a given customer with {customerId}.

* **URL**
  
  /customers/{customerId}/orders
  /customers/{customerId}/orders/{orderId}

* **Fields**
    `orderId - The unique ID associated with each order
     name -  Name associated with each order
     date -  Specifies the date on which the order is placed
     products -  Lists all products associated with this order(HATEOAS)`
    
* **Methods:**

  `GET` | `POST` | `PLACE` | `DELETE`
  
* **Explanation:**
The reason I have designed it like this because only a 'customer' can place 'orders'. In other words, you cannot create any order without having  a customer for it.
 No delete functionality has been provided for orders separately since it is tightly coupled with customer.
 Also, you cannot modify an order.

**product**
----  
  1. Returns json data about all existing products.
  2. Create a single new product.
  3. Returns json data about a specific product given {productId}.
  4. Update a single existing product given {productId}. 
  5. Delete a single existing product given {productId}.

* **URL**
  
  /products
  /products/{productId}

* **Fields**
    `productId - The unique ID associated with each product
     name -  Name associated with each product
     price -  Price associated with each product
     customers -  Lists all customers who bought this product(HATEOAS)`
    
* **Methods:**

  `GET` | `POST` | `PLACE` | `DELETE`
  
* **Explanation:**
The reason I have designed it like this because you can add products to your system independently.
Each product has a list of customers associated with it which you can use for various purposes.
