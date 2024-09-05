
```python
from pyspark.sql.types import DoubleType, IntegerType, StringType
cases = cases.withColumn('confirmed', F.col('confirmed').cast(IntegerType()))
```

