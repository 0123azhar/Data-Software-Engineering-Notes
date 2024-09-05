```python
cases.groupBy(["province","city"]).agg(
    F.sum("confirmed").alias("TotalConfirmed"),\
    F.max("confirmed").alias("MaxFromOneConfirmedCase")\
    ).show()
```

#### Reduce by
It is RDD specific operation it is not applicable to dataframe.

#### What is the difference between group by and reduce by in RDD?
In Apache Spark, `groupByKey` and `reduceByKey` are two different methods used to aggregate data, particularly when working with key-value pairs in RDDs. They both serve similar purposes but operate differently in terms of performance and efficiency.

### 1. **groupByKey:**

- **Functionality:**
  - `groupByKey` groups all the values associated with each key into a single list. For example, if you have an RDD of pairs `(K, V)`, `groupByKey` will produce a new RDD of type `(K, Iterable[V])`.

- **Behavior:**
  - This method simply groups the values by key and then collects all values for each key into a collection. 
  - No aggregation or reduction is done at this stage; it just groups the data.

- **Performance:**
  - **Shuffling:** `groupByKey` involves a lot of shuffling because it requires all the values for each key to be sent across the network to a single node that collects them. This can lead to a significant performance hit, especially if the data is large.
  - **Memory Usage:** Since all the values for a key are collected on a single node, it can lead to high memory usage and potentially cause memory-related issues (like running out of memory) if a key has many associated values.

- **Use Case:** Use `groupByKey` when you need to gather all values for a key without performing any intermediate aggregation or when the total size of the values is relatively small.

```python
rdd = sc.parallelize([('a', 1), ('b', 1), ('a', 2)])
grouped_rdd = rdd.groupByKey()
print(grouped_rdd.collect())  # Output: [('a', [1, 2]), ('b', [1])]
```

### 2. **reduceByKey:**

- **Functionality:**
  - `reduceByKey` combines the values for each key using a specified associative and commutative reduce function (like summation, multiplication, etc.). For example, it will take an RDD of pairs `(K, V)` and produce a new RDD of type `(K, V)` where the values are aggregated by the reduce function.

- **Behavior:**
  - This method performs the aggregation in a distributed manner. Spark first applies the reduce function locally on each partition (combining values for each key within the partition) and then shuffles the intermediate results across the network to further reduce them to a final value for each key.

- **Performance:**
  - **Efficiency:** `reduceByKey` is generally much more efficient than `groupByKey` because it reduces the amount of data shuffled across the network by combining values within each partition before shuffling. This leads to significantly less data being transferred across the network.
  - **Scalability:** Because of its efficient shuffling and reduction, `reduceByKey` scales better with large datasets.

- **Use Case:** Use `reduceByKey` when you want to perform an aggregation operation on the values associated with each key, such as summing them up, finding the maximum, etc. It is typically the preferred method when aggregating data by key.

```python
rdd = sc.parallelize([('a', 1), ('b', 1), ('a', 2)])
reduced_rdd = rdd.reduceByKey(lambda x, y: x + y)
print(reduced_rdd.collect())  # Output: [('a', 3), ('b', 1)]
```

### **Key Differences:**

1. **Aggregation:**
   - `groupByKey` groups all values associated with each key without performing any aggregation.
   - `reduceByKey` aggregates the values for each key using a specified reduce function.

2. **Shuffling:**
   - `groupByKey` shuffles all the data across the network, leading to higher overhead.
   - `reduceByKey` performs some local aggregation before shuffling, reducing the amount of data shuffled and thus being more efficient.

3. **Performance:**
   - `groupByKey` can be less efficient and may cause memory issues if the grouped values are large.
   - `reduceByKey` is more memory-efficient and performs better on large datasets.

4. **Use Cases:**
   - Use `groupByKey` when you need to collect all the values for each key without any reduction or aggregation.
   - Use `reduceByKey` when you need to aggregate or reduce the values for each key, such as summing, counting, or finding the maximum.
