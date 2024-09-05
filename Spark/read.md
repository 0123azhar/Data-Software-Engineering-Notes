```python
cases = spark.read.load("/home/rahul/projects/sparkdf/coronavirusdataset/Case.csv",
format="csv",
sep=",", 
inferSchema="true", 
header="true")
```