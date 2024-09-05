#square_brackets
```python
import pandas as pd

data =  [['tom', 10, '1', 'C'], ['nick', 15, '2', 'B'], ['juli', 14, '4', 'B'], ['amal', 17, '3', 'B'], ['adam', 24, '5', 'A'], ['adam', 18, '3', 'F']]
df = pd.DataFrame(data, columns=['Name', 'Age', 'id', 'grade'])
print(df)
#----------------#
print(df[2:4])

print(df[-3:]) # when using -, imagin last row index as -1

print(df[1:6:2])
```