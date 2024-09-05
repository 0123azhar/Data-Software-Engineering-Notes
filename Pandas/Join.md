##### common key
```python
import pandas as pd

df1 = pd.DataFrame({
    'key': ['A', 'B', 'C'],
    'value1': [1, 2, 3]
})
print(df1)
df2 = pd.DataFrame({
    'key': ['B', 'C', 'D'],
    'value2': [4, 5, 6]
})
print(df2)
# inner
result = pd.merge(df1, df2, on='key', how='inner')
print(result)
# left
result = pd.merge(df1, df2, on='key', how='left')
print(result)
# right
result = pd.merge(df1, df2, on='key', how='right')
print(result)
# outer
result = pd.merge(df1, df2, on='key', how='outer')
print(result)
# cross: every row from the first DataFrame is combined with every row from the second DataFrame.
result = pd.merge(df1, df2, how='cross')
print(result)

```

##### Joining on Different Column Names
```python
df1 = pd.DataFrame({
    'key1': ['A', 'B', 'C'],
    'value1': [1, 2, 3]
})

df2 = pd.DataFrame({
    'key2': ['B', 'C', 'D'],
    'value2': [4, 5, 6]
})

result = pd.merge(df1, df2, left_on='key1', right_on='key2', how='inner')
print(result)
```
##### Joining on Multiple Columns
```python
df1 = pd.DataFrame({
    'key1': ['A', 'B', 'C'],
    'key2': [1, 2, 3],
    'value1': [10, 20, 30]
})

df2 = pd.DataFrame({
    'key1': ['A', 'B', 'D'],
    'key2': [1, 2, 4],
    'value2': [100, 200, 400]
})

result = pd.merge(df1, df2, on=['key1', 'key2'], how='inner')
print(result)
```
##### Joining on Multiple Columns having different names
```python
import pandas as pd

df1 = pd.DataFrame({
    'key1': ['A', 'B', 'C'],
    'key2': [1, 2, 3],
    'value1': [10, 20, 30]
})

df2 = pd.DataFrame({
    'key3': ['A', 'B', 'D'],
    'key4': [1, 2, 4],
    'value2': [100, 200, 400]
})

# Merging on different column names
result = pd.merge(df1, df2, left_on=['key1', 'key2'], right_on=['key3', 'key4'], how='inner')
print(result)
```
