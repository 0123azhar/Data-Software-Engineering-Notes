Fact table 

| SalesID | Date       | ProductID | CustomerID | Quantity | TotalAmount |
| ------- | ---------- | --------- | ---------- | -------- | ----------- |
| 1       | 2024-01-01 | 101       | 501        | 2        | 200         |
| 2       | 2024-01-02 | 102       | 502        | 1        | 100         |
| 3       | 2024-01-03 | 103       | 503        | 5        | 500         |
| 4       | 2024-01-04 | 101       | 504        | 3        | 300         |
Dimention tables 

| ProductID | ProductName | Category   |
| --------- | ----------- | ---------- |
| 101       | Product A   | Category 1 |
| 102       | Product B   | Category 2 |
| 103       | Product C   | Category 3 |

| CustomerID | CustomerName | Location   |
| ---------- | ------------ | ---------- |
| 501        | Alice        | Location 1 |
| 502        | Bob          | Location 2 |
| 503        | Charlie      | Location 3 |
| 504        | David        | Location 4 |


Star schema 
In a star schema, the fact table is centralized and connected directly to dimension tables, forming a star-like pattern 

snowflake schema: the dimension tables are normalized into multiple related tables, forming a snowflake-like pattern