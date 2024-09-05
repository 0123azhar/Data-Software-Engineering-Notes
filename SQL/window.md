```sql
SELECT  
SalesID, 
EmployeeID, 
Amount, 
ROW_NUMBER() OVER (
	PARTITION BY EmployeeID 
	ORDER BY Amount DESC) AS RowNumber, 
LAG(Amount, 1) OVER (
	PARTITION BY EmployeeID 
	ORDER BY SaleDate) AS PrevAmount,  
LEAD(Amount, 1) OVER (
	PARTITION BY EmployeeID 
	ORDER BY SaleDate) AS NextAmount 
SUM(Amount) OVER (
	PARTITION BY EmployeeID 
	ORDER BY SaleDate 
	ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW) AS RunningTotal
FROM Sales; 
```

- CURRENT ROW, the current row
- UNBOUNDED PRECEDING, all rows before the current row -> fixed
- UNBOUNDED FOLLOWING, all rows after the current row -> fixed
- x PRECEDING, x rows before the current row -> relative
- y FOLLOWING, y rows after the current row -> relative