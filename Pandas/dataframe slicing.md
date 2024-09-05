can be done using loc, iloc and square brackets
#square_brackets 
```python
import pandas as pd

data = { 'A': [1, 2, 3, 4, 5], 'B': [10, 20, 30, 40, 50], 'C': [100, 200, 300, 400, 500] }
df = pd.DataFrame(data)
print(df)

# loc_slice = df.loc[1:2, ['A', 'B']] # valid
loc_slice = df.loc[1:2, 'A': 'B'] # will select all columns b/w A and B if any
print(loc_slice)

iloc_slice = df.iloc[1:3, 0:2] # will fail if A:B is passed instead of 0:2
print(iloc_slice)

bracket_slice = df[1:3][['A','B']]
print(bracket_slice)
```
- iloc index starts with 0 and 'to' value is excluded in slicing 
- loc includes both 'from' and 'to' value in slicing

Slicing with loc does not consider positions instead it picks all rows b/w 'from' and 'to' values 
also it throws an error if index is not integer when slicing.
Therefore, slicing in iloc is a bad idea
#loc
```python
import pandas as pd

data = { 'A': [1, 2, 3, 4, 5], 'B': [10, 20, 30, 40, 50], 'C': [100, 200, 300, 400, 500], 'ID': [1,4,3,2,5]} # ID list is not in order
df = pd.DataFrame(data)
df.set_index('ID', inplace = True)
print(df)

loc_slice = df.loc[1:2, ['A', 'B']]
print(loc_slice) # incorrect slicing
```

