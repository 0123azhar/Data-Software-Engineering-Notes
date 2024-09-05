2024-08-24 10:30
# Optimization Techniques

### Salt Key
```python
same key (here infection_case) is assigned for a lot of rows in our data. same for count, min, max

cases = cases.withColumn("salt_key", F.concat(F.col("infection_case"), 
F.lit("_"), 
F.monotonically_increasing_id() % 10))

cases_temp = cases.groupBy(["infection_case","salt_key"]).agg(F.sum("confirmed"))

cases_ans = cases_temp.groupBy(["infection_case"]).agg(F.sum("confirmed"))
```


```python
df.write.parquet("data/df.parquet")

df.unpersist()

spark.read.load("data/df.parquet")
```


```python
df.cache().count()
```


```python
df = df.repartition('cola', 'colb','colc','cold')
df = df.repartition(1000)
df.rdd.getNumPartitions()

# check out the distribution of records in a partition
df.glom().map(len).collect()
```



```python
from glob import glob

def load_df_from_parquet(parquet_directory):
    df = pd.DataFrame()
    for file in glob(f"{parquet_directory}/*"):
        df = pd.concat([df,pd.read_parquet(file)])
    return df
```


Avoid multiple executors on a single node
![[IMG_0065.jpeg]]


1. **Data Partitioning:** chatEnsures data is evenly distributed across the cluster to balance the workload and reduce shuffling.

2. **Caching/Persistence:** Reuse intermediate results by caching datasets in memory or on disk when they're used multiple times.

3. **Broadcast Variables:** Use for small datasets to avoid sending data to all nodes repeatedly.

4. **Avoiding Shuffle Operations:** Minimize operations like `reduceByKey`, `groupBy`, or `join` that cause data shuffling across nodes, as they are expensive.

5. **Filter Early:** Apply filters as early as possible to reduce the data size before performing heavy transformations.

6. **Use DataFrames and Datasets:** Leverage DataFrames and Datasets APIs for built-in optimization with Catalyst Optimizer and Tungsten Execution Engine.

7. **Speculative Execution:** Enable speculative execution to rerun slow tasks in parallel, potentially finishing faster.

8. **Tuning Resource Allocation:** Adjust the amount of memory and number of cores per executor for optimal performance based on your workload.

  

Focus on data partitioning, caching, minimizing shuffles, and leveraging Spark's built-in optimizations for the best performance.