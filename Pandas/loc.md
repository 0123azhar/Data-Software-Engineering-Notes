==Label== is value of index when index is set to one of the columns. it can be numeric or alphabetic.
loc works with ==label based indexing==.

```python
import pandas as pd

data =  [['tom', 10, '1', 'C'], ['nick', 15, '2', 'B'], ['juli', 14, '4', 'B'], ['amal', 17, '3', 'B'], ['adam', 24, '5', 'A'], ['adam', 18, '3', 'F']]
df = pd.DataFrame(data, columns=['name', 'age', 'id', 'grade'])
#print(df, '\n')
#----------------#
df.set_index('grade', inplace = True)
print(df, '\n')

print(df.loc['F'], '\n')        # retuens series datatype
print(df.loc[['B']], '\n')      # retuens dataframe
print(df.loc[['A','F']], '\n')  # returns dataframe

print(df.loc['F','name'], '\n')                # returns string, adam
print(df.loc['B',['name', 'age']], '\n')       # retuens dataframe
print(df.loc[['A','F'],['name', 'age']], '\n') # retuens dataframe
```