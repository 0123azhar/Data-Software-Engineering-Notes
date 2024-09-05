# Common table expression
```sql
WITH FilteredEmployees AS ( 
    SELECT EmployeeID, FirstName, LastName, DepartmentID, Salary 
    FROM Employees 
    WHERE Salary > 50000 
), 
FilteredDepartments AS ( 
    SELECT DepartmentID, DepartmentName 
    FROM Departments 
    WHERE DepartmentName LIKE 'Sales%' 
) 
SELECT e.EmployeeID, e.FirstName, e.LastName, d.DepartmentName 
FROM FilteredEmployees e 
JOIN FilteredDepartments d ON e.DepartmentID = d.DepartmentID; 
```

Recursive with