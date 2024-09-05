#### Broadcast join 
```python
from pyspark.sql.functions import broadcast

# Assume we have the following datasets
transactions = spark.read.csv("transactions.csv")  # Large dataset
userDetails = spark.read.csv("user_details.csv")   # Smaller dataset

# Perform a join without broadcast
enrichedTransactions = transactions.join(userDetails, "user_id")

# Perform the join using the broadcasted dataset
enrichedTransactions = transactions.join(broadcast(userDetails), "user_id")
```
#### Broadcast variable
```python
from pyspark.sql import SparkSession
from pyspark.sql.functions import col, udf

# Create a Spark session
spark = SparkSession.builder.appName("BroadcastExample").getOrCreate()

# Sample transaction data
transaction_data = [
    (1, 100.0),
    (2, 150.0),
    (3, 200.0),
    (4, 250.0),
]

# Create a DataFrame
transactions = spark.createDataFrame(transaction_data, ["transaction_id", "amount"])

# Define the discount rate
discount_rate = 0.10

# Broadcast the discount rate to all worker nodes
broadcast_discount_rate = spark.sparkContext.broadcast(discount_rate)

# Apply the discount using the broadcasted discount rate
discounted_transactions = transactions.withColumn(
    "discounted_amount", 
    col("amount") * (1 - broadcast_discount_rate.value)
)

# Show the results
discounted_transactions.show()
```

