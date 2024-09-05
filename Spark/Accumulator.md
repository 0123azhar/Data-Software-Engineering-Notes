# Create an accumulator for the record count
It can only be used on RDDs mostly along with foreach()
```python
record_count_accumulator = spark.sparkContext.accumulator(0)
```