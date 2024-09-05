##### left
##### right
##### inner 
SQL default when not specified explicitly
##### full / outer
##### left anti join / anti join
```sql
select table_1.A, table_1.B,  table_2.C, table_2.D
from table_1
left join table_2 
on table_1.X = table_2.Y
where table_2.Y is Null
```

left semi join / semi join:
```sql
where table_2.Y is not Null
```

self join:
```sql
SELECT emp.employee_name AS employee, mng.employee_name AS manager 
FROM Employees emp 
JOIN Employees mng  
ON emp.manager_id = mng.employee_id
```

