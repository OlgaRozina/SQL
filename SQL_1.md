
## To complete the task we have the following tables 
```
mysql> show tables;
+------------------+
| Tables_in_voodoo |
+------------------+
| Categories       |
| Customers        |
| Employees        |
| OrderDetails     |
| Orders           |
| Products         |
| Shippers         |
| Suppliers        |
| Z_Train          |
+------------------+
```
___

### 1.  Select all rows from the table with carriers
```
mysql> SELECT * FROM Shippers;
+-----------+------------------+----------------+
| ShipperID | ShipperName      | Phone          |
+-----------+------------------+----------------+
|         1 | Speedy Express   | (503) 555-9831 |
|         2 | United Package   | (503) 555-3199 |
|         3 | Federal Shipping | (503) 555-9931 |
+-----------+------------------+----------------+

```
___
### 2. Select the first 3 rows from the employee table
```

mysql> SELECT * FROM Employees limit 3;
+------------+-----------+-----------+------------+------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| EmployeeID | LastName  | FirstName | BirthDate  | Photo      | Notes                                                                                                                                                                                                                                                                                                                                                                                                                       |
+------------+-----------+-----------+------------+------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|          1 | Davolio   | Nancy     | 1968-12-08 | EmpID1.pic | Education includes a BA in psychology from Colorado State University. She also completed (The Art of the Cold Call). Nancy is a member of 'Toastmasters International'.                                                                                                                                                                                                                                                     |
|          2 | Fuller    | Andrew    | 1952-02-19 | EmpID2.pic | Andrew received his BTS commercial and a Ph.D. in international marketing from the University of Dallas. He is fluent in French and Italian and reads German. He joined the company as a sales representative, was promoted to sales manager and was then named vice president of sales. Andrew is a member of the Sales Management Roundtable, the Seattle Chamber of Commerce, and the Pacific Rim Importers Association. |
|          3 | Leverling | Janet     | 1963-08-30 | EmpID3.pic | Janet has a BS degree in chemistry from Boston College). She has also completed a certificate program in food retailing management. Janet was hired as a sales associate and was promoted to sales representative.                                                                                                                                                                                                          |
+------------+-----------+-----------+------------+------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
```
____
### 3. From the table of employees choose all names, surnames, birthdays in the following order: BirthDate, FirstName, LastName, number of rows in the sample limit to 3.
```
mysql> SELECT BirthDate, FirstName, LastName FROM Employees limit 3;
+------------+-----------+-----------+
| BirthDate  | FirstName | LastName  |
+------------+-----------+-----------+
| 1968-12-08 | Nancy     | Davolio   |
| 1952-02-19 | Andrew    | Fuller    |
| 1963-08-30 | Janet     | Leverling |
+------------+-----------+-----------+
```
____
### 4.  Select the names of the staff members born in 1958.
```
mysql> SELECT FirstName, LastName FROM Employees 
WHERE year (BirthDate)=1958;
+-----------+----------+
| FirstName | LastName |
+-----------+----------+
| Margaret  | Peacock  |
| Laura     | Callahan |
+-----------+----------+
```
___
### 5. Choose all products with a price from 23 to 25.
```
mysql> SELECT * FROM Products 
WHERE `price` between '23'and '25';
+-----------+------------------------------+------------+------------+-------------------+-------+
| ProductID | ProductName                  | SupplierID | CategoryID | Unit              | Price |
+-----------+------------------------------+------------+------------+-------------------+-------+
|         6 | Grandma's Boysenberry Spread |          3 |          2 | 12 - 8 oz jars    | 25.00 |
|        14 | Tofu                         |          6 |          7 | 40 - 100 g pkgs.  | 23.25 |
|        55 | Pbtu chinois                 |         25 |          6 | 24 boxes x 2 pies | 24.00 |
+-----------+------------------------------+------------+------------+-------------------+-------+
```
____
### 6.  Find goods with minimum price.
```
mysql> SELECT * FROM Products 
WHERE price=(SELECT MIN(price) FROM Products);
+-----------+-------------+------------+------------+-------+-------+
| ProductID | ProductName | SupplierID | CategoryID | Unit  | Price |
+-----------+-------------+------------+------------+-------+-------+
|        33 | Geitost     |         15 |          4 | 500 g |  2.50 |
+-----------+-------------+------------+------------+-------+-------+
```
___
### 7. Find goods with maximum price.
```
mysql> SELECT * FROM Products 
WHERE price=(SELECT MAX(price) FROM Products);
+-----------+---------------+------------+------------+--------------------+--------+
| ProductID | ProductName   | SupplierID | CategoryID | Unit               | Price  |
+-----------+---------------+------------+------------+--------------------+--------+
|        38 | Cute de Blaye |         18 |          1 | 12 - 75 cl bottles | 263.50 |
+-----------+---------------+------------+------------+--------------------+--------+
```
_____
### 8.  Select all products with Unit '10 pkgs.'
```
mysql> SELECT * FROM Products 
WHERE Unit = '10 pkgs.';
+-----------+-------------+------------+------------+----------+-------+
| ProductID | ProductName | SupplierID | CategoryID | Unit     | Price |
+-----------+-------------+------------+------------+----------+-------+
|        48 | Chocolade   |         22 |          3 | 10 pkgs. | 12.75 |
+-----------+-------------+------------+------------+----------+-------+
```
____
### 9. Choose suppliers' addresses that live in one of the cities: Tokyo, Frankfurt, Osaka.
```
mysql> SELECT Address FROM Suppliers 
WHERE City in ('Tokyo', 'Frankfurt', 'Osaka');
+---------------------------+
| Address                   |
+---------------------------+
| 9-8 Sekimai Musashino-shi |
| 92 Setsuko Chuo-ku        |
| Bogenallee 51             |
+---------------------------+
```
____
### 10. Choose the name of products starting with the letter "G" that have a price above 37. 
```
mysql> SELECT ProductName FROM Products 
WHERE ProductName LIKE 'G%' and Price > 37;
+------------------------+
| ProductName            |
+------------------------+
| Gnocchi di nonna Alice |
+------------------------+
```
____
### 11. Displays a list of countries starting with "S" and consisting of 5 letters, from which there are suppliers.
```
mysql> SELECT Country from Suppliers 
WHERE Country like 'S%' and length (Country) = 5;
+---------+
| Country |
+---------+
| Spain   |
+---------+
```
____
### 12. Print the sum of all goods whose name contains "od", the column name Summ.
```
mysql> SELECT SUM(Price) AS 'Summ' FROM Products 
WHERE ProductName like '%od%';
+--------+
| Summ   |
+--------+
| 131.00 |
+--------+
```
____
### 13. Print the average amount of goods delivered in bottles rounded to 2 digits after the decimal point, the column called Summ.
```
mysql> SELECT ROUND (AVG (Price),2) AS 'Summ' FROM Products 
WHERE Unit like '%bottles';
+-------+
| Summ  |
+-------+
| 38.75 |
+-------+
```
____
### 14.  Find the number of customers who DO NOT reside in France and Germany,  column name Countt. 
```

mysql> SELECT COUNT(CustomerName) AS 'Countt' FROM Customers 
WHERE Country not in ('France', 'Germany');
+--------+
| Countt |
+--------+
|     69 |
+--------+
```
____
### 15. Print the names of employees born after 01.01.1968. Sort the result by name.
```
mysql> SELECT FirstName FROM Employees 
WHERE DATE(BirthDate) > '1968-01-01' 
ORDER BY FirstName;
+-----------+
| FirstName |
+-----------+
| Anne      |
| Nancy     |
+-----------+
```
____
### 16. Select the names of the items with Price = 13 or 15 and sort by ascending, use "SELECT" commands with combining the results via "UNION".
```
mysql> SELECT ProductName FROM Products 
WHERE Price = '13.00' 
UNION SELECT ProductName FROM Products WHERE Price = '15.00' ORDER BY 'Price';
+---------------------------------+
| ProductName                     |
+---------------------------------+
| Original Frankfurter grine Soae |
| Outback Lager                   |
| Rud Kaviar                      |
+---------------------------------+
```
____
### 17. Show the names of the products in the name of which the third letter "m" and the names of their suppliers.
```
mysql> SELECT Products.ProductName, Suppliers.SupplierName 
FROM Products 
INNER JOIN Suppliers ON Products.SupplierID=Suppliers.SupplierID 
WHERE ProductName LIKE '__m%';
+---------------------------+-----------------------------------+
| ProductName               | SupplierName                      |
+---------------------------+-----------------------------------+
| Gumbur Gummiburchen       | Heli Swaren GmbH & Co. KG         |
| Camembert Pierrot         | Gai puturage                      |
| Wimmers gute Semmelknudel | Plutzer Lebensmittelgroumurkte AG |
+---------------------------+-----------------------------------+
```
____
### 18. Show the names of the employee who placed the order 1996-11-27 (write the request in two ways: via INNER JOIN, and using a subquery).
```
mysql> SELECT FirstName, LastName FROM Employees 
WHERE Employees.EmployeeID = (SELECT Orders.EmployeeID FROM Orders WHERE OrderDate = '1996-11-27');
+-----------+-----------+
| FirstName | LastName  |
+-----------+-----------+
| Janet     | Leverling |
+-----------+-----------+
mysql> SELECT Employees.FirstName, Employees.LastName FROM Employees 
INNER JOIN Orders ON Employees.EmployeeID = Orders.EmployeeID 
WHERE OrderDate = '1996-11-27';
+-----------+-----------+
| FirstName | LastName  |
+-----------+-----------+
| Janet     | Leverling |
+-----------+-----------+
```
____
### 19.  Choose all products from which «Grandma Kelly’s Homestead» supplier and price > 27. The result is 3 columns: Product, Supplier, Price.
```
mysql> SELECT P.ProductName, S.SupplierName, P.Price FROM Products AS P 
INNER JOIN Suppliers AS S on P.SupplierID = S.SupplierID 
WHERE S.SupplierName = 'Grandma Kelly''s Homestead' and P.price > 27;
+---------------------------------+---------------------------+-------+
| ProductName                     | SupplierName              | Price |
+---------------------------------+---------------------------+-------+
| Uncle Bob's Organic Dried Pears | Grandma Kelly's Homestead | 30.00 |
| Northwoods Cranberry Sauce      | Grandma Kelly's Homestead | 40.00 |
+---------------------------------+---------------------------+-------+
```
____
### 20.	 Print the total amount of the 'Queso Cabrales' product (the column name Summ) sent to all customers (write the query in two ways: via INNER JOIN, and using a subquery).
```
mysql> SELECT SUM(Quantity) AS Summ FROM Products AS P INNER JOIN OrderDetails ON P.ProductID=OrderDetails.ProductID WHERE ProductName LIKE 'Queso Cabrales';
+------+
| Summ |
+------+
|  182 |
+------+
mysql> SELECT SUM(Quantity) AS Summ FROM OrderDetails AS O WHERE O.ProductID = (SELECT ProductID FROM Products WHERE ProductName = 'Queso Cabrales');
+------+
| Summ |
+------+
|  182 |
+------+
```
____
### 21. Show all orders sent to «Ekergatan 24» with their customers and employees. As a result, withdraw 3 columns - order ID, customer’s name, employee’s name, employee’s name.
```
mysql> SELECT O.OrderID, C.CustomerName, E.FirstName, E.LastName 
FROM ((Orders AS O INNER JOIN Customers AS C ON O.CustomerID=C.CustomerID) 
INNER JOIN Employees AS E ON O.EmployeeID=E.EmployeeID) 
WHERE C.Address = 'Ekergatan 24';
+---------+----------------+-----------+-----------+
| OrderID | CustomerName   | FirstName | LastName  |
+---------+----------------+-----------+-----------+
|   10264 | Folk och fe HB | Michael   | Suyama    |
|   10327 | Folk och fe HB | Andrew    | Fuller    |
|   10378 | Folk och fe HB | Steven    | Buchanan  |
|   10434 | Folk och fe HB | Janet     | Leverling |
+---------+----------------+-----------+-----------+
```
____
### 22. Convert the previous query so that the same data is displayed in 3 columns - merge LastName and FirstName from Employees into one column across a space and call it EmployeeName (2 LEFT JOINS). 
```
mysql> SELECT O.OrderID, C.CustomerName, concat (E.FirstName, ' ', 'LastName') AS EmployeeName 
FROM ((Orders AS O 
LEFT JOIN Customers AS C ON O.CustomerID = C.CustomerID)
LEFT JOIN Employees AS E ON O.EmployeeID = E.EmployeeID) 
WHERE C.Address = 'Ekergatan 24';
+---------+----------------+------------------+
| OrderID | CustomerName   | EmployeeName     |
+---------+----------------+------------------+
|   10264 | Folk och fe HB | Michael LastName |
|   10327 | Folk och fe HB | Andrew LastName  |
|   10378 | Folk och fe HB | Steven LastName  |
|   10434 | Folk och fe HB | Janet LastName   |
+---------+----------------+------------------+
```
____

### 23. Show all products contained in 1997 orders and whose names are less than 5 letters. As a result, print OrderID, OrderDate, ProductName (write a query in two ways: via INNER JOINS, and using subtasks)
```
mysql> SELECT OD.OrderID, O.OrderDate, P.ProductName
    -> FROM((OrderDetails AS OD
    -> INNER JOIN Products AS P ON P.ProductID=OD.ProductID)
    -> INNER JOIN Orders AS O ON OD.OrderID=O.OrderID)
    -> WHERE O.OrderDate LIKE '1997%' and P.ProductName LIKE '____';
+---------+------------+-------------+
| OrderID | OrderDate  | ProductName |
+---------+------------+-------------+
|   10409 | 1997-01-09 | Tofu        |
|   10412 | 1997-01-13 | Tofu        |
|   10427 | 1997-01-27 | Tofu        |
+---------+------------+-------------+
```
____
### 24. Show the names of products and their categories that are used in orders from a customer named Blondel père et fils and whose categories consist of at least 2 words.
```
mysql> SELECT Customers.CustomerName,Products.ProductName
    -> FROM OrderDetails
    -> INNER JOIN Orders ON Orders.OrderID=OrderDetails.OrderID
    -> INNER JOIN Customers ON Orders.CustomerID=Customers.CustomerID
    -> INNER JOIN Products ON Products.ProductID=OrderDetails.ProductID
    -> INNER JOIN Categories ON Categories.CategoryID=Products.CategoryID
    -> WHERE Customers.CustomerName = 'Blondel pere et fils' AND Categories.CategoryName LIKE '% %';
+----------------------+------------------------+
| CustomerName         | ProductName            |
+----------------------+------------------------+
| Blondel pere et fils | Mozzarella di Giovanni |
+----------------------+------------------------+
```
____
### 25. Withdraw the number of customers (column name Buyers) who have made one of the products: «Queso Cabrales», «Gustaf’s Knäckebröd», «Louisiana Fiery Hot Pepper Sauce», «Schoggi Schokolade», «Gnocchi di na Alice».
```
mysql> SELECT count(DISTINCT Customers.CustomerName) as Buyers FROM Customers
    -> INNER JOIN Orders ON Customers.CustomerID = Orders.CustomerID
    -> INNER JOIN OrderDetails ON Orders.OrderID = OrderDetails.OrderID
    -> INNER JOIN Products ON OrderDetails.ProductID = Products.ProductID
    -> where Products.ProductName = "Queso Cabrales"
    -> or Products.ProductName = "Gustaf's Knäckebröd"
    -> or Products.ProductName = "Louisiana Fiery Hot Pepper Sauce"
    -> or Products.ProductName = "Schoggi Schokolade"
    -> or Products.ProductName = "Gnocchi di nonna Alice";
+--------+
| Buyers |
+--------+
|     25 |
+--------+
```
____
### 26. Find the cities to which the most orders were sent, withdraw the name of the city and the number of orders (column name Amount).
```
mysql> SELECT C.City, Count(*) AS Amount
    -> FROM Customers AS C
    -> INNER JOIN Orders AS O ON O.CustomerID = C.CustomerID
    -> GROUP BY C.City
    -> ORDER BY Amount DESC LIMIT 1;
+------+--------+
| City | Amount |
+------+--------+
| Graz |     10 |
+------+--------+
```
____
### 27. Find the city from which the most units of goods were delivered to London, output the city name and the number of units (column name Amount).
```
mysql> SELECT S.City, SUM(OD.Quantity) AS Amount
    -> FROM Orders AS O
    -> INNER JOIN OrderDetails AS OD ON O.OrderID = OD.OrderID
    -> INNER JOIN Customers AS C ON O.CustomerID = C.CustomerID
    -> INNER JOIN Products AS P ON P.ProductID = OD. ProductID
    -> INNER JOIN Suppliers AS S ON P.SupplierID = S.SupplierID
    -> WHERE C.City = 'London'
    -> GROUP BY S.City
    -> ORDER BY Amount DESC limit 2;
+---------+--------+
| City    | Amount |
+---------+--------+
| Ravenna |     80 |
| Annecy  |     80 |
+---------+--------+
```
____
### 28. Find carriers who have transported more than 30 different beverages (Beverages), deduct the names of carriers, the category of goods and the number of transported types of goods (column name Amount).
```
mysql> SELECT S.ShipperName, C.CategoryName, Count(O.ShipperID) AS Amount
    -> FROM Orders AS O
    -> INNER JOIN OrderDetails AS OD ON O.OrderID = OD.OrderID
    -> INNER JOIN Products AS P ON P.ProductID = OD.ProductID
    -> INNER JOIN Shippers AS S ON O.ShipperID = S.ShipperID
    -> INNER JOIN Categories AS C ON C.CategoryID = P.CategoryID
    -> WHERE C.CategoryName = 'Beverages'
    -> GROUP BY S.ShipperName, C.CategoryName
    -> HAVING Amount > 30;
+------------------+--------------+--------+
| ShipperName      | CategoryName | Amount |
+------------------+--------------+--------+
| Federal Shipping | Beverages    |     31 |
| United Package   | Beverages    |     37 |
+------------------+--------------+--------+
```
____
### 29. Find the average price of seasonings (Condiments) sent to the states ordered by Margaret Peacock, deduct the cost rounded to 2 decimal places (column name Average).
```
mysql> SELECT round(AVG(P.Price),2) AS Average
    -> FROM Orders AS O
    -> INNER JOIN Customers AS Cus ON O.CustomerID = Cus.CustomerID
    -> INNER JOIN Employees AS E ON O.EmployeeID = E.EmployeeID
    -> INNER JOIN OrderDetails AS OD ON OD.OrderID = O.OrderID
    -> INNER JOIN Products AS P ON P.ProductID = OD.ProductID
    -> INNER JOIN Categories AS C ON C.CategoryID = P.CategoryID
    -> WHERE E.FirstName = 'Margaret'
    -> and E.LastName = 'Peacock'
    -> and Cus.Country - 'USA'
    -> and C.CategoryName = 'Condiments';
+---------+
| Average |
+---------+
|    30,17 |
+---------+
```
____


