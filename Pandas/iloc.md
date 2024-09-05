iloc works with ==position based indexing== irrespective of what index is set to a column or not.
iloc is followed by ==**square brackets**== and one square brackets inside or two separated by coma.
```python
import pandas as pd

data =  [['tom', 10, '1', 'C'], ['nick', 15, '2', 'B'], ['juli', 14, '4', 'B'], ['amal', 17, '3', 'B'], ['adam', 24, '5', 'A'], ['adam', 18, '3', 'F']]
df = pd.DataFrame(data, columns=['Name', 'Age', 'id', 'grade'])
print(df)
#----------------#
print(df.iloc[[1,3,4]])
print(df.iloc[[1,3,4],[1,2]])
```