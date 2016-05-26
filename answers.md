# Warm up 

- Retrieve all columns from the `Customers` table

```sql
SELECT *
FROM Customers
```

- Print the Customer Name and Address of all customers from Mexico

```sql
SELECT CustomerName
FROM Customers
WHERE Country = 'Mexico'
```

- Print an alphabetically sorted list of all countries of all customers

```sql
SELECT DISTINCT Country
FROM Customers
ORDER BY Country
```

- Which employees have a BA degree?

```sql
SELECT * FROM [Employees]
WHERE Notes LIKE "% BA %"
```

- Which products cost between $25 and $30?

```sql
SELECT *
FROM Products
WHERE Price >= 25
    AND Price =< 30
```

- Print a list of the 20 cheapest products

```sql
SELECT ProductName, Price
FROM Products
ORDER BY Price
LIMIT 20
```

- Which customers have a postal box as address?

```sql
SELECT *
FROM Customers
WHERE Address LIKE "P.O. Box%"
```

# Aggregation

- How many orders were there in July 1996?

```sql
SELECT Count(*)
FROM Orders
WHERE OrderDate LIKE "1996-07%"
```

- How many countries did we sell to?

```sql
SELECT Count(DISTINCT Country)
FROM Customers
```

- Print the minimum, average and maximum price of our assortment

```sql
SELECT
    Round(Min(Price), 2) AS "minimum",
    Avg(Price) AS "average",
    Max(Price) AS "max"
FROM Products
```

- How many customers do we have per country?

```sql
SELECT Country, Count(*)
FROM Customers
GROUP BY Country
```

- Create a table with columns 'Country' and 'Number of customers', sorted from most to least number of customers.

```sql
SELECT Country, Count(*) AS "Number of customers"
FROM Customers
GROUP BY Country
ORDER BY "Number of customers" DESC
```

- Give employee IDs for those who sold at least 20 orders.

```sql
SELECT EmployeeID, COUNT(OrderID) AS NumberOfOrders
FROM Orders
GROUP BY EmployeeID
HAVING NumberOfOrders >= 20
```


# `JOIN`

- Which employees sold at least 20 orders?

```sql
SELECT LastName, FirstName, COUNT(OrderID) AS NumOrders
FROM Employees
INNER JOIN Orders
ON Employees.EmployeeID = Orders.EmployeeID
GROUP BY LastName, FirstName
HAVING NumOrders >= 20
```

- What is the name of the customer who has the most orders?

```sql
SELECT CustomerName, Count(*) AS "NumOrders"
FROM Customers
INNER JOIN Orders
ON Customers.CustomerID = Orders.CustomerID
GROUP BY CustomerName
ORDER BY 2 DESC
LIMIT 1
```

- What supplier has the highest product price?

```sql
SELECT SupplierName, Price
FROM Suppliers
INNER JOIN Products
ON Suppliers.SupplierID = Products.SupplierID
ORDER BY 2 DESC
LIMIT 1
```

- What employee made the most sales (by number of orders)?

```sql
SELECT LastName, FirstName, Count(OrderID)
FROM Employees
INNER JOIN Orders
ON Employees.EmployeeID = Orders.EmployeeID
GROUP BY LastName, FirstName
ORDER BY 3 DESC
```

- What employee made the most sales (by number of products)?

```sql
SELECT LastName, FirstName, Sum(Quantity)
FROM Employees
INNER JOIN Orders
ON Employees.EmployeeID = Orders.EmployeeID
JOIN OrderDetails
ON Orders.OrderID = OrderDetails.OrderID
GROUP BY LastName, FirstName
ORDER BY 3 DESC
```

- What employee made the most sales (by value of sales)?

```sql
SELECT LastName, FirstName, Round(Sum(Quantity * Price), 2) AS "Sales"
FROM Employees
INNER JOIN Orders
ON Employees.EmployeeID = Orders.EmployeeID
INNER JOIN OrderDetails
ON Orders.OrderID = OrderDetails.OrderID
JOIN Products
ON OrderDetails.ProductID = Products.ProductID
GROUP BY LastName, FirstName
ORDER BY 3 DESC
```

# Creating, Updating, Deleting

- Create a database called `sql_bootcamp` and show the tables in it.

```sql
CREATE DATABASE sql_bootcamp;
USE sql_bootcamp;
SHOW TABLES
```

- Create a table called `students` with the first name, last name, and favorite color of each student in our class. Note: answer below will vary

```sql
CREATE TABLE students (
    id INT NOT NULL AUTO_INCREMENT,
    first_name VARCHAR(20) NOT NULL,
    last_name VARCHAR(30) NOT NULL,
    favorite_color VARCHAR(10),
    PRIMARY KEY (id)
    );
INSERT INTO students (first_name, last_name, favorite_color)
VALUES
("Mason", "Gallo", "Green")
```

- What's the most popular favorite color? Note: answer below will vary

```sql
SELECT favorite_color, count(*)
FROM students
GROUP BY 1
ORDER BY 2 DESC
```

- Add a column for the color of their shoes. Note: answer below will vary

```sql
ALTER TABLE students
ADD shoe_color VARCHAR(10);
UPDATE students
SET shoe_color = 'Red' WHERE favorite_color = 'Black';
```

- Remove a column from the table


```sql
ALTER TABLE students
DROP favorite_color
```

- Delete the table and delete the database

```sql
DROP TABLE students
DROP DATABASE sql_bootcamp
```

