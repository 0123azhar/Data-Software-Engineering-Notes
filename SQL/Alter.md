```sql
ALTER TABLE Orders 
ADD DeliveryDate DATE; 
 
-- from FLOAT to DECIMAL(10, 2) 
ALTER TABLE Orders 
MODIFY OrderAmount DECIMAL(10, 2); 
 
ALTER TABLE Orders 
RENAME COLUMN OrderAmount TO TotalAmount; 
 
ALTER TABLE Orders 
DROP COLUMN OrderPriority; 
 
ALTER TABLE Orders 
ADD CONSTRAINT PK_OrderID PRIMARY KEY (OrderID); 
 
ALTER TABLE Orders 
ADD CONSTRAINT FK_CustomerID FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID); 
 
ALTER TABLE Orders 
ALTER COLUMN OrderStatus SET DEFAULT 'Pending'; 
 
ALTER TABLE Orders 
ADD CONSTRAINT UC_OrderNumber UNIQUE (OrderNumber); 
 
ALTER TABLE Orders 
DROP CONSTRAINT UC_OrderNumber; 
 
ALTER TABLE Orders 
RENAME TO CustomerOrders; 
```

