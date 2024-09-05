
```python
import pyspark.sql.functions as F
from pyspark.sql.types import *

def casesHighLow(confirmed):
    if confirmed < 50:
        return 'low'
    else:
        return 'high'

#convert above function to a UDF
casesHighLowUDF = F.udf(casesHighLow, StringType()

CasesWithHighLow = cases.withColumn("HighLow", casesHighLowUDF("confirmed"))
```