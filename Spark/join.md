```python
cases = cases.join(regions, ['province','city'],how='left')
```
broadcast
```python
from pyspark.sql.functions import broadcast
cases = cases.join(broadcast(regions), ['province','city'],how='left')
```
