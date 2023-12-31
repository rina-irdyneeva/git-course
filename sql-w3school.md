#### SQL-SELECT

1. Insert the missing statement to get all the columns from the Customers table.
```bash
  SELECT  * FROM Customers;
```
2. Write a statement that will select the City column from the Customers table.
```bash
`SELECT city FROM Customers;
```
3. Select all the different values from the Country column in the Customers table.
```bash
SELECT DISTINCT Country FROM Customers;
```
#### SQL-WHERE

1. Select all records where the City column has the value "Berlin".
```bash
SELECT * FROM Customers WHERE city = 'Berlin';
```
2. Use the NOT keyword to select all records where City is NOT "Berlin".
```bash
SELECT * FROM Customers WHERE NOT city = 'Berlin';
```
3. Select all records where the CustomerID column has the value 32.
```bash
SELECT * FROM Customers WHERE CustomerID = 32;
```
4. Select all records where the City column has the value 'Berlin' and the PostalCode column has the value 12209.
```bash
SELECT * FROM Customers WHERE City = 'Berlin'AND PostalCode = 12209;
```
5. Select all records where the City column has the value 'Berlin' or 'London'.
```bash
SELECT * FROM Customers WHERE City = 'Berlin'OR City = 'London';
```
#### SQL-ORDER BY

1. Select all records from the Customers table, sort the result alphabetically by the column City.
```bash
  SELECT  * FROM Customers ORDER BY city;
```
2. Select all records from the Customers table, sort the result reversed alphabetically by the column City.
```bash
`SELECT * FROM Customers ORDER BY city DESC;
```
3. Select all records from the Customers table, sort the result alphabetically, first by the column Country, then, by the column City.
```bash
SELECT * FROM Customers ORDER BY country, city;
```
#### SQL-INSERT

1. Insert a new record in the Customers table.
```bash
INSERT INTO Customers (CustomerName, Address, City, PostalCode, Country) VALUES ('Hekkan Burger','Gateveien 15','Sandnes','4306', 'Norway');
```
#### SQL-NULL

1. Insert a new record in the Customers table.
```bash
SELECT * FROM Customers WHERE PostalCode IS NULL;
```
2. Select all records from the Customers where the PostalCode column is NOT empty.
```bash
SELECT * FROM Customers WHERE PostalCode IS NOT NULL;
```
#### SQL-UPDATE

1. Update the City column of all records in the Customers table.
```bash
UPDATE Customers SET City = 'Oslo';
```
2. Set the value of the City columns to 'Oslo', but only the ones where the Country column has the value "Norway".
```bash
UPDATE Customers SET City = 'Oslo' WHERE Country = 'Norway';
```
3. Update the City value and the Country value.
```bash
UPDATE Customers SET City = 'Oslo', Country = 'Norway' WHERE CustomerID = 32;
```
#### SQL-DELETE

1. Delete all the records from the Customers table where the Country value is 'Norway'.
```bash
DELETE FROM Customers WHERE Country = 'Norway';
```
2. Delete all the records from the Customers table.
```bash
DELETE FROM Customers;
```
#### SQL-FUNCTIONS

1. Use the MIN function to select the record with the smallest value of the Price column.
```bash
SELECT MIN(Price) FROM Products;
```
2. Use an SQL function to select the record with the highest value of the Price column.
```bash
SELECT MIN(Price) FROM Products;
```
3. Use the correct function to return the number of records that have the Price value set to 18.
```bash
SELECT COUNT(*) FROM Products WHERE Price = 18;
```
4. Use an SQL function to calculate the average price of all products.
```bash
SELECT AVG(Price) FROM Products;
```
5. Use an SQL function to calculate the sum of all the Price column values in the Products table.
```bash
SELECT SUM(Price) FROM Products;
```
#### SQL-LIKE

1. Select all records where the value of the City column starts with the letter "a".
```bash
SELECT * FROM Customers WHERE City LIKE 'a%';
```
2. Select all records where the value of the City column ends with the letter "a".
```bash
SELECT * FROM Customers WHERE City LIKE '%a';
```
3. Select all records where the value of the City column contains the letter "a".
```bash
SELECT * FROM Customers WHERE City LIKE '%a%';
```
4. Select all records where the value of the City column starts with letter "a" and ends with the letter "b".
```bash
SELECT * FROM Customers WHERE City LIKE 'a%b';
```
5. Select all records where the value of the City column does NOT start with the letter "a".
```bash
SELECT * FROM Customers WHERE City NOT LIKE 'a%';
```
#### SQL-WILDCARDS

1. Select all records where the second letter of the City is an "a".
```bash
SELECT * FROM Customers WHERE City LIKE '_a%';
```
2. Select all records where the first letter of the City is an "a" or a "c" or an "s".
```bash
SELECT * FROM Customers WHERE City LIKE '[acs]%';
```
3. Select all records where the first letter of the City starts with anything from an "a" to an "f".
```bash
SELECT * FROM Customers
WHERE City LIKE '[a-f]%';
```
4. Select all records where the first letter of the City is NOT an "a" or a "c" or an "f".
```bash
SELECT * FROM Customers
WHERE City LIKE '[!acf]%';
```
#### SQL-IN

1. Use the IN operator to select all the records where Country is either "Norway" or "France".
```bash
SELECT * FROM Customers WHERE Country IN ('Norway', 'France');
```
2. Use the IN operator to select all the records where Country is NOT "Norway" and NOT "France".
```bash
SELECT * FROM Customers WHERE Country NOT IN ('Norway', 'France');
```
#### SQL-ALIAS

1. When displaying the Customers table, make an ALIAS of the PostalCode column, the column should be called Pno instead.
```bash
SELECT CustomerName, Address, PostalCode AS Pno FROM Customers;
```
2. When displaying the Customers table, refer to the table as Consumers instead of Customers.
```bash
SELECT FROM Customers AS Consumers;
```
#### SQL-BETWEEN

1. Use the BETWEEN operator to select all the records where the value of the Price column is between 10 and 20.
```bash
SELECT * FROM Products WHERE Price BETWEEN 10 AND 20;
```
2. Use the BETWEEN operator to select all the records where the value of the Price column is NOT between 10 and 20.
```bash
SELECT * FROM Products WHERE Price NOT BETWEEN 10 AND 20;
```
3. Use the BETWEEN operator to select all the records where the value of the ProductName column is alphabetically between 'Geitost' and 'Pavlova'.
```bash
SELECT * FROM Products WHERE ProductName BETWEEN 'Geitost' AND 'Pavlova';
```
#### SQL-JOIN

1. Insert the missing parts in the JOIN clause to join the two tables Orders and Customers, using the CustomerID field in both tables as the relationship between the two tables.
```bash
SELECT * FROM Orders LEFT JOIN Customers ON Orders.CustomerID=Customers.CustomerID;
```
2. Choose the correct JOIN clause to select all records from the two tables where there is a match in both tables.
```bash
SELECT * FROM Orders INNER JOIN Customers ON Orders.CustomerID=Customers.CustomerID;
```
3. Choose the correct JOIN clause to select all the records from the Customers table plus all the matches in the Orders table.
```bash
SELECT * FROM Orders RIGHT JOIN Customers ON Orders.CustomerID=Customers.CustomerID;
```
#### SQL-GROUP BY

1. List the number of customers in each country.
```bash
SELECT COUNT(CustomerID), Country FROM Customers GROUP BY Country;
```
2. List the number of customers in each country, ordered by the country with the most customers first.
```bash
SELECT COUNT(CustomerID), Country FROM Customers GROUP BY Country ORDER BY COUNT(CustomerID) DESC;
```
#### SQL-DATABASE

1. Write the correct SQL statement to create a new database called testDB.
```bash
CREATE DATABASE testDB;
```
2. Write the correct SQL statement to delete a database named testDB.
```bash
DROP DATABASE testDB;
```
3. Write the correct SQL statement to create a new table called Persons.
```bash

CREATE TABLE Persons
 (
  PersonID int,
  LastName varchar(255),
  FirstName varchar(255),
  Address varchar(255),
  City varchar(255) 
  );
```
4. Write the correct SQL statement to delete a table called Persons.
```bash
DROP TABLE Persons;
```
5. Use the TRUNCATE statement to delete all data inside a table.
```bash
TRUNCATE TABLE Persons;
```
6. Add a column of type DATE called Birthday.
```bash
ALTER TABLE Persons ADD Birthday DATE;
```
7. Delete the column Birthday from the Persons table.
```bash
ALTER TABLE Persons DROP COLUMN Birthday;
```







