# Database-Design-and-Implementation
This database Design project is from Introduction to Relational Databases (RDBMS) on Coursera.  It showcases my  understanding and working with relational databases with following skills:
 * Understanding of Data and Databases
 * Data Models and Relational Concepts
 * Entity Relationship Diagrams
 * Working Knowledge of DBMSes
 * Database Design
 * SQL Proficiency
 * Practical Application

-------------------------------------------------------------------------------Project details---------------------------------------------------------------------------------------------------
# Scenario
In this scenario, you have recently been hired as a data engineer by a New York-based coffee shop chain looking to expand nationally by opening several franchise locations. They want to streamline operations and revamp their data infrastructure as part of their expansion process.

Your job is to design their relational database systems for improved operational efficiencies and to make it easier for their executives to make data-driven decisions.

Currently, their data resides in several different systems: Accounting software, suppliers' databases, point of sales (POS) systems, and even spreadsheets. You will review the data in these systems and design a central database to house all of their data. You will then create the database objects and load them with source data. Finally, you will create subsets of data your business partners require, export them, and load them into staging databases using different RDBMS.

#Software used in this project
In this project, you will use PostgreSQL Database, IBM Db2 Database, and MySQL. These relational database management systems (RDBMS) are designed to store, manipulate, and retrieve data efficiently.
#Data used in this project
In this project, you will be working with a subset of data from the Coffee shop sample data.

You will use a modified version of the data for the project, so to succeed in the project, download the linked files when prompted in the instructions. You do not need to use any data from the source.

In your scenario, you will be working with data from the following sources:

Staff information held in a spreadsheet at headquarters (HQ)
Sales outlet information held in a spreadsheet at HQ
Sales data output as a CSV file from the POS system in the sales outlets
Customer data output as a CSV file from a bespoke customer relationship management system
Product information maintained in a spreadsheet exported from your suppliers' databases
Objectives
After completing this lab, you will be able to:

*Identify entities
*Identity attributes
*Create an entity relationship diagram (ERD) using the pgAdmin ERD Tool
*Normalize tables
*Define keys and relationships
*Create database objects by generating and running the SQL script from the ERD Tool
*Create a view and export the data
*Create a materialized view and export the data
*Import data into a Db2 database
*Import data into a MySQL database

#Task 1: Identify entities
The first step when designing a new database is to review any existing data and identify the entities for your new system.

The following image shows sample data from each source you will be working with to design your new central database.

sample data(find in my repository)

Note: You can download a copy of this image or open it in another browser tab for reference later in the lab.
Make a list of the entities you have identified. Take a screenshot and save it as Task1.jpg or Task1.png.

Solution
Task1: The entities are following:
Staff,
Sales outlet, 
Sale transaction, 
Customer, 
Product

#Task 2: Identify attributes
In this task, you will identify the attributes of one of the entities you plan to create.

Using the information from the sample data in the image from Task 1, identify the entity's attributes that will store the sales transaction data.

Make a list of the sales transaction attributes that you identified. Take a screenshot and save it as Task2.jpg or Task2.png.

Solution:
Task2: The attributes for sales transaction are following:

Transaction id
Date
Time
Sales outlet
Staff
Customer
Product
Quantity
Price

#Task 3: Create an ERD
Now that you have defined some of your attributes and entities, you can determine the tables and columns for them and create an ERD.

Open a new terminal from the side-by-side Cloud IDE.

Use the start_postgres command to start a PostgreSQL service session in the Cloud IDE.

Use the pgAdmin weblink to open pgAdmin in a new tab in your browser.

Create a new database named COFFEE, view the schemas in the new COFFEE database, then start a new ERD project.

Add a table to the ERD for the sale transactions entity using the information in the following table. Consider the naming convention to use so that your colleagues can understand your data and ensure that the names are valid in other RDBMS. Use the sample data shown in the image in Task 1 to determine appropriate data types for each column.

Sales transaction table

Take a screenshot of your ERD and save it as Task3A.png or Task3A.jpg.

solution
Check  the file: Task3A

Add a table to the ERD for the product entity using the information in the following table. Consider the naming convention to use so that your colleagues can understand your data and ensure that the names are valid in other RDBMS. Use the sample data shown in the image in Task 1 to determine appropriate data types for each column.

Product

Take a screenshot of your ERD and save it as Task3B.png or Task3B.jpg.

solution 
Check  the file: Task3B

#Task 4: Normalize tables
When reviewing your ERD, you notice it does not conform to the second normal form.

Review the data in the sales transaction table. Note that the transaction id column does not contain unique values because some transactions include multiple products.

Determine which columns should be stored in a separate table to remove the repeating rows and to put this table into second normal form.

Add a new table named sales_detail to the ERD, define the columns in the new table, and delete the moved columns from the sales transaction table, leaving a matching column in each of the two tables to to create a relationship between them later.

Take a screenshot of your ERD and save it as Task4A.png or Task4A.jpg.

solution
Check  the file: Task4A


Review the data in the product table. Note that the product category and product type columns contain redundant data.

Determine which columns should be stored in a separate table to reduce redundant data and to put this table into a second normal form.

Add a new table named product_type to the ERD, define the columns in the new table, and delete the moved columns from the product table, leaving a matching column in each of the two tables to create a relationship between them later.

Take a screenshot of your ERD and save it as Task4B.png or Task4B.jpg.

solution
Check  the file: Task4B

#Task 5: Define keys and relationships
After normalizing your tables, you can define their primary keys and relationships between the tables in your ERD.

Identify an appropriate column in each table to be a primary key and create the primary keys in the tables in your ERD.

Take a screenshot of your ERD and save it as Task5A.png or Task5A.jpg.

solution
Check  the file: Task5A

Identify the relationships between the following pairs of tables and then create the relationships in your ERD:

sales_detail to sales_transaction
sales_detail to product
product to product_type
Take a screenshot of your ERD and save it as Task5B.png or Task5B.jpg.

solution
Check  the file: Task5B

#Task 6: Create database objects by generating and running the SQL script from the ERD tool
Now that your design is complete, you will generate an SQL script from your ERD, which you can use to create your database schema. For this project, you will then use a given SQL script to ensure that you can successfully load the sample data into the schema. Finally, you will load the existing data from various sources into your new database schema.

Use the Generate SQL functionality in the ERD tool to create an SQL script from your ERD.

Download the following GeneratedScript.sql file to your local computer.

GeneratedScript.sql( check my repository)

In pgAdmin, open the Query tool, upload and open the GeneratedScript.sql file from your local computer, and then execute the script to create the tables defined in the ERD. Verify that the tables exist in the COFFEE database's public schema now.

Take a screenshot of the tables shown in the tree-view pane on the left-hand side of the page and save it as Task6A.png or Task6A.jpg.

solution
Check the file: Task6A

Download the following CoffeeData.sql file to your local computer.

CoffeeData.sql
In pgAdmin, open another instance of the query tool, upload and open the CoffeeData.sql file from your local computer, and then run the script to populate the tables you just created.

In pgAdmin, view the first 100 rows of the sales_detail table.

Take a screenshot of the Data Output pane and save it as Task6B.png or Task6B.jpg.

solution
Check the file: Task6B

#Task 7: Create a view and export the data
The external payroll company have requested a list of employees and the locations at which they work. This list should not include the CEO or CFO who owns the company. In this task, you will create a view in your PostgreSQL database that returns this information and export the results to a CSV file.

In your COFFEE database, create a new view named staff_locations_view using the following SQL:

SELECT staff.staff_id,
staff.first_name,
staff.last_name,
staff.location
FROM staff
WHERE "position" NOT IN ('CEO', 'CFO');

View all the rows returned from the view.

Save the query results to a file named staff_locations_view.csv on your local computer.

Take a screenshot of the view shown in the tree-view pane on the left side of the page with the results in the Data Output pane, and save it as Task7.png or Task7.jpg.

solution
Check the file: Task7

#Task 8: Create a materialized view and export the data
A marketing consultant requires access to your product data in their MySQL database for a marketing campaign. You will create a materialized view in your PostgreSQL database that returns this information and export the results to a CSV file.

In your COFFEE database, create a new materialized view named product_info_m-view using the following SQL:

SELECT product.product_name, product.description, product_type.product_category
FROM product
JOIN product_type
ON product.product_type_id = product_type.product_type_id;

Refresh the materialized view with data.

View all the rows returned from the view.

Save the query results to a file named product_info_m-view.csv on your local computer storage.

Take a screenshot of the view shown in the tree-view pane on the left-hand side of the page alongside the results in the Data Output pane, and save it as Task8.png or Task8.jpg.

solution
Check the file: Task8


Task 9: Import data into a Db2 database
The external payroll company has asked you to upload the staff location information to their Db2 database.

In a new browser tab, go to cloud.ibm.com/login, log in using your credentials, and then open a console for your Db2 on the Cloud instance you created earlier in this course.

Use the Load Data feature to load a new table named STAFF_LOCATIONS with the staff location information saved in the staff_locations_view.csv file you exported from the view you created in Task 7.

Explore the new table and then view the data in it.

Take a screenshot of the contents of the new table and save it as Task9.png or Task9.jpg.

solution
Check the file: Task9

Task 10: Import data into a MySQL database
The marketing consultant has asked you to upload the product information to their MySQL database.

In the terminal from the side-by-side Cloud IDE, use the start_mysql command to start a My SQL service session in the Cloud IDE.

Use the browser weblink to open phpMyAdmin in a new tab in your browser.

In phpMyAdmin, create a new database named coffee_shop_products, and then import the product information saved in the product_info_m-view.csv file from your materialized view into a new table in the coffee_shop_products database.

Browse the contents of the new table.

Take a screenshot of the contents of the new table and save it as Task10.png or Task10.jpg.

solution
Check the file: Task10

Conclusion
In this project, you created a database structure and views, which you exported to DB2 and MySQL databases.



 
