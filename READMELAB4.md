Post-Tutorial Questions:

1. Why is it important to create separate databases for each microservice (e.g., product_service, order_service, inventory_service)?

There are several reasons why this might have been chosen. It makes sure that the microservices are not tightly coupled, so if one database fails, the rest are still fine. Our microservices are also able to use the database that best suits the task. Our product-service microservice uses mongoDB, while the others make use of mysql. 

2. What role does Flyway play in managing the database schema, and how does it ensure consistency across environments?

Flyway serves as both a kind of version control as well as eliminating the chance of duplicate data

By tracking changes in the database. It basically ensures that even when using different database schemas, the databases information still remains effectively the same (consistent).



3. How does Spring Data JPA simplify working with databases in each of the microservices?

	The JPA is nice because it automatically maps java objects to tables and allows us to access the database without manually writing out SQL queries.

4. In the InventoryService, why did we use the @Transactional(readOnly = true) annotation, and what is its significance?

We only have a GET endpoint on the InventoryService: we just want to read from its database. In order to ensure that we don't accidentally write something, we make sure that readOnly is set to true.



5. In a microservices architecture, what are some challenges when ensuring communication between the Product, Order, and Inventory Services?

The main challenge that arises here is keeping the databases consistent with each other. Because each microservice has its own database, we need to carefully make sure that each database stays consistent with the others, without introducing too tight of coupling.



6. What are the advantages of using TestContainers for integration testing with MySQL in this lab?

They are fairly easy to set up, lightweight, and they serve to mock a real environment to catch bugs before full integration with production 