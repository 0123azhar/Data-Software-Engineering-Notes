2024-08-24 03:32
# update

#loc 
```python
import pandas as pd

data =  [['tom', 10, '1', 'C'], ['nick', 15, '2', 'B'], ['juli', None, '4', 'B'], ['amal', 17, '3', 'B'], ['adam', 24, '5', 'A'], ['adam', 18, '3', 'F']]
df = pd.DataFrame(data, columns=['name', 'age', 'id', 'grade'])
print(df)
#----------------#
df.loc[df.age.isna() == True, 'age'] = df.age.mean()
print(df)

df.loc[df.grade == 'B', 'grade'] = 'BelowAverage'
print(df)
```

