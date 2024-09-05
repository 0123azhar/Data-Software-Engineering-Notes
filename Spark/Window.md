```python
from pyspark.sql.window import Window

windowSpec = Window().partitionBy(['province']).orderBy(F.desc('confirmed'))
cases.withColumn("rank",F.rank().over(windowSpec)).show() 
```

F.lag("confirmed", 7)
F.mean("confirmed") etc.,

```python
from pyspark.sql.window import Window

# confirmed cases past 7 days (including today i.e today + 6 passed days)
windowSpec = Window().partitionBy(['province']).orderBy('date').rowsBetween(-6,0)

df_WithRoll = df.withColumn("roll_7_confirmed",F.mean("confirmed").over(windowSpec))
```

