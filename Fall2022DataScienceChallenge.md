# Fall 2022 Data Science Intern Challenge 
## Steven Zuñiga


### Question 1.A

When giving the data a quick overlook using excel, I found that there are some orders that
are heavily skewing the data. Specifically, there seems to be several orders consisting of either
a single item order to the value of 25725 or a multiple item order of the same unit value.

In order to compensate for the outliers in the mean calculation, I would try to acquire the
AOV by measuring the median rather than the mean.

To double check this figure or to test this assertion I truncated the data by filtering out
data that was greater than 1.5 times the interquartile range. Using describe() of the truncated
data I came up with a mean of 283.814268, very close to the median of the data. 

### Question 1.B

I would use the median.

### Question 1.C

284


### Question 2.A

Answer: 54

```
SELECT COUNT(*)
FROM ORDERS
Inner JOIN Shippers ON ORDERS.ShipperID = Shippers.ShipperID
Having ShipperName = "Speedy Express"
```
### Question 2.B

Answer: Margaret Peacock

```

SELECT Employees.LastName, Employees.FirstName, COUNT(Orders.OrderID) AS NumberOfOrders
FROM (Orders
INNER JOIN Employees ON Orders.EmployeeID = Employees.EmployeeID)
GROUP BY LastName, FirstName
HAVING COUNT(Orders.OrderID) > 20;

```

### Question 2.C

Answer: Gorgonzola Telino

```
SELECT ProductName
FROM (((Orders INNER JOIN Customers ON Orders.CustomerID = Customers.CustomerID )
INNER JOIN OrderDetails ON Orders.OrderID = OrderDetails.OrderID )
INNER JOIN Products ON Products.ProductID = OrderDetails.ProductID )
WHERE Country='Germany'
ORDER BY ProductName DESC
```
