# Lab 8 - Review Exercise

Enda Lee 2023

## Quickstart

1. Create an empty folder whereever you keep you web apps. Name it `lab8`

2. The lab VM is not required, onnde Node JS and VS Code are installed on your system.
3. Open the (empty) `lab8` **folder** in VS Code.



## Introduction

This week's lab is a review of the topics covered in the labs so far.

You are required to build a Sveltekit application to display products and categories from a Supabase tables.



## 1. The Database

### 1.1. The tables

Create two new tables, `product` and `category` in Supabase, based on this ERD. 

Setup the Primary keys for each table, choose appropriate datatypes and setup the one-many relatonship between the tables.



![product_category_erd](./media/product_category_erd.png)

### 1.2. Sample data

Use the SQL below to insert sample data

```sql
-- sample data for product database- SQL inserts

-- category table data
INSERT INTO category(id, category_name, category_description) VALUES
(1, 'Books', 'Paper and hard cover, fiction and non-fiction');
INSERT INTO category(id, category_name, category_description) VALUES
(2, 'Computer', 'Desktop, laptops, and accessories');
INSERT INTO category(id, category_name, category_description) VALUES
(3, 'Entertainment', 'Home electronicsa, TV, HiFi, etc.');
INSERT INTO category(id, category_name, category_description) VALUES
(4, 'Kitchen', 'Kitchen + cooking appliances');
INSERT INTO category(id, category_name, category_description) VALUES
(5, 'Laundry', 'Clothes washers, dryers, and accesories');
INSERT INTO category(id, category_name, category_description) VALUES
(6, 'Mobile Devices', 'Mobile phones, tablets, and accessories');
INSERT INTO category(id, category_name, category_description) VALUES
(7, 'Furniture', 'Home and home office furniture');


-- the product table data
INSERT INTO product(id, category_id, product_name, product_description, product_stock, product_price) VALUES
(6, 4, 'Kettle', 'Steel Electric Kettle', 100, 55.00);
INSERT INTO product(id, category_id, product_name, product_description, product_stock, product_price) VALUES
(7, 4, 'Fridge freezer', 'Fridge + freezer large', 45, 799.00);
INSERT INTO product(id, category_id, product_name, product_description, product_stock, product_price) VALUES
(8, 2, 'Microsoft Surface Laptop 8', '16GB ram, 512GB SSD', 5, 1299.00);
INSERT INTO product(id, category_id, product_name, product_description, product_stock, product_price) VALUES
(9, 2, '14inch Laptop', 'HP laptop,16GB RAM,1TB SSD', 45, 1099.00);
INSERT INTO product(id, category_id, product_name, product_description, product_stock, product_price) VALUES
(10, 6, 'Samsung 10inch Tablet', 'Android6GB ram, 128GB storage, 10inch screen', 5, 99.00);
INSERT INTO product(id, category_id, product_name, product_description, product_stock, product_price) VALUES
(11, 3, '60inch TV', 'Sony 4K,OLED,Smart TV', 12, 1899.00);
INSERT INTO product(id, category_id, product_name, product_description, product_stock, product_price) VALUES
(12, 5, 'Clothes Washing Machine', '1600rpm spin,A+++ rated,10KG', 50, 699.00);
INSERT INTO product(id, category_id, product_name, product_description, product_stock, product_price) VALUES
(13, 6, 'iPhone 13', '128GB', 5, 850.00);
INSERT INTO product(id, category_id, product_name, product_description, product_stock, product_price) VALUES
(14, 1, 'Azure Web Apps', 'Paperback, January 2020, Cloud publishing', 50, 19.00);
INSERT INTO product(id, category_id, product_name, product_description, product_stock, product_price) VALUES
(16, 7, 'Bed', 'Super King size,super comfort mattress', 5, 899.00);
INSERT INTO product(id, category_id, product_name, product_description, product_stock, product_price) VALUES
(17, 2, 'Learning JavaScript', 'Become a JavaScript expert in 2 hours!', 10, 12.00);
INSERT INTO product(id, category_id, product_name, product_description, product_stock, product_price) VALUES
(18, 7, 'Desk', 'Small computer desk', 5, 99.00);
INSERT INTO product(id, category_id, product_name, product_description, product_stock, product_price) VALUES
(15, 1, 'SQL and No SQL for beginners', 'Paperback, Oct 2021, Cloud publishing', 10, 399.00);
INSERT INTO product(id, category_id, product_name, product_description, product_stock, product_price) VALUES
(20, 7, 'Table', 'A large kitchen table', 40, 800.00);
```



### 1.3. Reset the Identity sequence for both tables

Run the following SQL to avoid primary key errors when inserting new categories or products from the application

```sql
ALTER SEQUENCE category_id_seq RESTART WITH 10;
ALTER SEQUENCE product_id_seq RESTART WITH 25;
```



## 2. The Application

### 2.1. Setup

Create a new Supabase Application, following the lab examples. The application should connect to Supabase and use environment variables for secrets and other variables.

### 2.2. API routes

All database access should be via an API. Add the appropriate endpoints to `routes/api`. 

You will need endpoints for:

1. Getting all categories.
2. Getting all products.
3. Getting a single product by id.
4. Getting products in a particular categaory (referenced by the category_id).
5. Posting a new product.
6. Posting a new category.

### 2.3. The application pages

1. All pages should use a shared navigation menu defined in a `layout`.
2.  Add a page which lists all products and categories and allows products to be filtered by category.
3. When a Product is selected, open another page whichhs displays the product.
4. Add a page where new products can be added via a form (the form should be properly validated).
5. Add a page where new categories can be added via a form (the form should be properly validated).



------

Enda Lee 2023