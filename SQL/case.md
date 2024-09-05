```sql
CASE  
WHEN OrderStatus = 'Cancelled' THEN 'No' 
WHEN OrderStatus = 'Pending' AND OrderAmount > 500 THEN 'High' 
WHEN OrderStatus = 'Pending' AND OrderAmount <= 500 THEN 'Medium' 
WHEN OrderStatus = 'Shipped' AND OrderAmount > 1000 THEN 'High' 
WHEN OrderStatus = 'Shipped' AND OrderAmount BETWEEN 500 AND 1000 THEN 'Medium' 
WHEN OrderStatus = 'Shipped' AND OrderAmount < 500 THEN 'Low Priority'  
WHEN OrderStatus = 'Delivered' THEN 'Completed' ELSE 'Unknown'  
END AS OrderPriority, 
order_id
from orders;
```