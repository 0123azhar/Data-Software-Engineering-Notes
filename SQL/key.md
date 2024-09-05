Primary Key / composite primary key - Explicitly defined with the PRIMARY KEY keyword. Is a single column / multiple columns uniquely identifying each row. One primary key pre table and value cannot be null. 

```sql
CREATE TABLE Employees ( 
    EmployeeID INT NOT NULL, 
    Name VARCHAR(100), 
    Email VARCHAR(100), 
    PRIMARY KEY (EmployeeID) 
); 
```

Foreign Key - Defined with the FOREIGN KEY keyword to establish relationships between tables. Primary key of another table. 

```sql
CREATE TABLE Departments ( 
    DepartmentID INT NOT NULL, 
    DepartmentName VARCHAR(100), 
    PRIMARY KEY (DepartmentID) 
); 
```
  ```sql
CREATE TABLE Employees ( 
    EmployeeID INT NOT NULL, 
    Name VARCHAR(100), 
    DepartmentID INT, 
    PRIMARY KEY (EmployeeID), 
    FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID) 
); 
```

Unique Key - Specified with the UNIQUE keyword to ensure all values in a column or a set of columns are unique. Can be multiple per table and allows nulls 

 

#### Conceptual Keys: 
Natural Keys - A key that is derived from data naturally occurring within the dataset, such as a Social Security Number or an email address. 

Surrogate Keys - Artificially created keys that have no business meaning (usually a sequence or auto-incremented number). 

Secondary Key - Often used interchangeably with indexes, these are not actual keys in the traditional sense but are fields used to speed up queries and are typically created with CREATE INDEX. 

Alternate Key - A candidate key that is not used as the primary key but ensures uniqueness and is often enforced using the UNIQUE keyword. 

Super Key - Any combination of columns that can uniquely identify rows in a table, which includes the primary key and possibly additional columns. 

Candidate Key - Any column or combination of columns that can qualify as a unique identifier for all rows in a table. These can potentially be used as primary keys. 

Composite Key - A key that consists of two or more columns that together create a unique identifier for each record. These can be specified using PRIMARY KEY or UNIQUE constraints across multiple columns. 