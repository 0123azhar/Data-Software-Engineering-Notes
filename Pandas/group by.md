```python
import pandas as pd

df = pd.DataFrame({
    'Category': ['A', 'B', 'A', 'B', 'A'],
    'Value1': [10, 20, 30, 40, 50],
    'Value2': [5, 10, 15, 20, 25]
})

grouped = df.groupby('Category').agg(
    total_value=('Value1', 'sum'),
    avg_value=('Value2', 'mean')
)

print(grouped)
```
