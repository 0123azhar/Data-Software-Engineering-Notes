# Slowly changing dimensions

Type 1: Overwrite the old data with new data. No history is kept.

| CustomerID | Name       | Address       |
| ---------- | ---------- | ------------- |
| 1          | John Doe   | 123 Main St   |
| 2          | Jane Smith | 456 Maple Ave |
| 3          | Bob Brown  | 789 Elm St    |

| CustomerID | Name       | Address       |
| ---------- | ---------- | ------------- |
| 1          | John Doe   | 321 Oak St    |
| 2          | Jane Smith | 456 Maple Ave |
| 3          | Bob Brown  | 789 Elm St    |

Type 2: Create a new record for each change, preserving history. Typically includes start and end dates for each record.


| CustomerID | Name       | Address       | StartDate  | EndDate    | CurrentFlag |
| ---------- | ---------- | ------------- | ---------- | ---------- | ----------- |
| 1          | John Doe   | 123 Main St   | 2020-01-01 | 2022-01-01 | 0           |
| 1          | John Doe   | 321 Oak St    | 2022-01-01 | NULL       | 1           |
| 2          | Jane Smith | 456 Maple Ave | 2021-01-01 | NULL       | 1           |
| 3          | Bob Brown  | 789 Elm St    | 2021-06-01 | NULL       | 1           |

| CustomerID | Name       | Address       | StartDate  | EndDate    | CurrentFlag |
| ---------- | ---------- | ------------- | ---------- | ---------- | ----------- |
| 1          | John Doe   | 123 Main St   | 2020-01-01 | 2022-01-01 | 0           |
| 1          | John Doe   | 321 Oak St    | 2022-01-01 | 2024-05-01 | 0           |
| 1          | John Doe   | 987 Pine St   | 2024-05-01 | NULL       | 1           |
| 2          | Jane Smith | 456 Maple Ave | 2021-01-01 | NULL       | 1           |
| 3          | Bob Brown  | 789 Elm St    | 2021-06-01 | NULL       | 1           |
Type 3: Add new columns to store previous values. Limited history is kept.

| CustomerID | Name       | CurrentAddress | PreviousAddress | AddressChangeDate |
| ---------- | ---------- | -------------- | --------------- | ----------------- |
| 1          | John Doe   | 123 Main St    | NULL            | NULL              |
| 2          | Jane Smith | 456 Maple Ave  | NULL            | NULL              |
| 3          | Bob Brown  | 789 Elm St     | NULL            | NULL              |



| CustomerID | Name       | CurrentAddress | PreviousAddress | AddressChangeDate |
| ---------- | ---------- | -------------- | --------------- | ----------------- |
| 1          | John Doe   | 321 Oak St     | 123 Main St     | 2024-05-25        |
| 2          | Jane Smith | 456 Maple Ave  | NULL            | NULL              |
| 3          | Bob Brown  | 789 Elm St     | NULL            | NULL              |




| CustomerID | Name       | CurrentAddress | PreviousAddress | AddressChangeDate |
| ---------- | ---------- | -------------- | --------------- | ----------------- |
| 1          | John Doe   | 987 Pine St    | 321 Oak St      | 2024-05-25        |
| 2          | Jane Smith | 456 Maple Ave  | NULL            | NULL              |
| 3          | Bob Brown  | 789 Elm St     | NULL            | NULL              |
