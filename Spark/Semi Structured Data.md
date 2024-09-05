2024-09-03 15:51
# Semi Structured Data

Working with JSON is natively supported in Apache Spark, but working with XML is not natively supported. Requires the spark-xml package to read and write XML files.


### 1. **Loading Nested JSON Data**

Assume you have the following JSON file (`data.json`):

```json
{
  "store": {
    "book": [
      {
        "category": "reference",
        "author": "Nigel Rees",
        "title": "Sayings of the Century",
        "price": 8.95
      },
      {
        "category": "fiction",
        "author": "Evelyn Waugh",
        "title": "Sword of Honour",
        "price": 12.99
      }
    ],
    "bicycle": {
      "color": "red",
      "price": 19.95
    }
  }
}
```

### 2. **Reading the JSON Data**

Load the JSON file into a Spark DataFrame:

```python
from pyspark.sql import SparkSession

spark = SparkSession.builder.appName("NestedJSON").getOrCreate()

# Load JSON into a DataFrame
df = spark.read.json("data.json")
df.printSchema()
df.show(truncate=False)
```

### 3. **Understanding the Schema**

The schema will look something like this:

```
root
 |-- store: struct (nullable = true)
 |    |-- book: array (nullable = true)
 |    |    |-- element: struct (containsNull = true)
 |    |    |    |-- author: string (nullable = true)
 |    |    |    |-- category: string (nullable = true)
 |    |    |    |-- price: double (nullable = true)
 |    |    |    |-- title: string (nullable = true)
 |    |-- bicycle: struct (nullable = true)
 |    |    |-- color: string (nullable = true)
 |    |    |-- price: double (nullable = true)
```

### 4. **Flattening the Nested JSON**

To work with the nested data, you often need to flatten it. You can do this by selecting individual fields using dot notation.

#### Flattening the `book` array using Explode:

```python
from pyspark.sql.functions import explode

# Explode the book array to flatten it
books_df = df.select(explode("store.book").alias("book"))
books_flat_df = books_df.select("book.author", "book.category", "book.title", "book.price")
books_flat_df.show(truncate=False)
```

**Output:**

```
+-------------+---------+----------------------+-----+
|author       |category |title                 |price|
+-------------+---------+----------------------+-----+
|Nigel Rees   |reference|Sayings of the Century|8.95 |
|Evelyn Waugh |fiction  |Sword of Honour       |12.99|
+-------------+---------+----------------------+-----+
```

#### Flattening the `bicycle` struct:

```python
bicycle_df = df.select("store.bicycle.color", "store.bicycle.price")
bicycle_df.show(truncate=False)
```

**Output:**

```
+-----+-----+
|color|price|
+-----+-----+
|red  |19.95|
+-----+-----+
```

### 5. **Combining Flattened Data**

You can combine the flattened data from different parts of the JSON structure into a single DataFrame if needed.
**X_df.unionByName(Y_df):** unions two dataframes by selecting only commons which have same names in both dataframes X_df & Y_df. Hence ignoring colour column
```python
from pyspark.sql import functions as F

combined_df = books_flat_df.withColumn("type", F.lit("book")).unionByName(
    bicycle_df.withColumn("author", F.lit(None))
              .withColumn("category", F.lit(None))
              .withColumn("title", F.lit("bicycle"))
              .withColumn("type", F.lit("bicycle"))
)

combined_df.show(truncate=False)
```

**Output:**

```
+-------------+---------+----------------------+-----+--------+
|author       |category |title                 |price|type    |
+-------------+---------+----------------------+-----+--------+
|Nigel Rees   |reference|Sayings of the Century|8.95 |book    |
|Evelyn Waugh |fiction  |Sword of Honour       |12.99|book    |
|null         |null     |bicycle               |19.95|bicycle |
+-------------+---------+----------------------+-----+--------+
```


