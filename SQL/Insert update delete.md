### Insert
```sql
INSERT INTO Orders (OrderID, CustomerID, OrderDate, OrderAmount, OrderStatus) 
VALUES (1001, 10, '2024-05-25', 150.00, 'Pending')
VALUES (1002, 11, '2024-05-25', 200.00, 'Pending'); 
```

```sql
INSERT INTO Orders 
VALUES (1002, 11, '2024-05-25', 200.00, 'Pending', NULL, 'GOOD'); 
```

```sql
INSERT INTO Orders (OrderID, CustomerID, OrderDate, OrderAmount, OrderStatus) 
SELECT OrderID, CustomerID, OrderDate, OrderAmount, OrderStatus 
FROM OldOrders 
WHERE OrderDate > '2023-01-01'; 
```

```sql
INSERT INTO Orders
SELECT OrderID, CustomerID, OrderDate, OrderAmount, OrderStatus 
FROM OldOrders 
WHERE OrderDate > '2023-01-01'; 
```
### Update
```sql
UPDATE Orders_table 
SET  
    OrderStatus = 'Shipped', 
    OrderPriority =  
        CASE WHEN OrderAmount BETWEEN 300 AND 700 THEN 'Medium Priority' 
        ELSE OrderPriority 
        END 
WHERE  
    OrderStatus = 'Pending'  
    AND OrderAmount BETWEEN 300 AND 700; 
```

orders which are pending and whose amount is b/w 300 - 700 will be updated
all statuses will change to Shipped
Order priority will be changed to medium for records with order amount b/w 300 -700

Delete
```sql
DELETE FROM Orders
WHERE OrderStatus = 'Cancelled' 
AND OrderDate < DATEADD(year, -1, GETDATE()); 
```