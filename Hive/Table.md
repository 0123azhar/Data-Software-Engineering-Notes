#### Hive table

```sql
CREATE TABLE IF NOT EXISTS database_name.table_name ( 
    id INT, 
    name STRING, 
    date_of_birth DATE, 
    salary DECIMAL(10,2), 
    department STRING, 
    comments STRING 
) 
COMMENT 'Employee details' 
PARTITIONED BY (department STRING) 
CLUSTERED BY (id) INTO 10 BUCKETS 
ROW FORMAT DELIMITED 
    FIELDS TERMINATED BY ',' 
    COLLECTION ITEMS TERMINATED BY '|' 
    MAP KEYS TERMINATED BY ':' 
STORED AS ORC 
LOCATION '/mnt/path/to/hive/tables/table_name' 
TBLPROPERTIES ('orc.compress' = 'SNAPPY', 'creator' = 'admin', 'created_at' = '2024-04-29'); 
```
- Internal table: managed by hive so if table is deleted data at the hdfs location is also deleted. Also called managed table. 
- External table: not managed by hive so data at hdfs location is not deleted when table is deleted 
- Hive Meta store: It is a component of Apache Hive that stores metadata about structures of Hive tables, like schemas and location. It's a relational database containing definitions of Hive tables, databases, columns in tables, data types, and table properties. 
- Compression: Hive supports a variety of file formats that have built-in compression capabilities, such as Parquet, ORC, and Avro. 
- Snappy: Fast compression and decompression, less CPU-intensive. 
- Gzip (Deflate): Provides a higher compression ratio than Snappy, useful for storage-bound cases but is slower. 
- Bzip2: Offers the highest compression ratio among the common codecs but is very slow in terms of performance. 
- ZLIB: A balance between size and performance, better compression ratio than Snappy but slower. 

#### Delta lake 

It is storage format and internally it uses parquet files to store actual data and json files to store metadata in a directory structure that it can use to provide ACID, time travel, CDF etc capabilities.  
Delta table is the key feature of delta lake. 
creating delta table .format(“delta”) in spark. 
Merge, update and delete operations  
Delta table Time travel 
version column in history table     
delta table history 
    
```sql
delta.enableChangeDataFeed = true 
```    

```sql
SELECT * FROM table_name VERSION AS OF 123 CHANGEFEED 
```

```sql
SELECT * FROM table_name CHANGEFEE 
```
\_commit_version, _change_type - insert, delete, update_preimage, update_postimage columns in above table 

history table  
```sql
DESCRIBE HISTORY delta_table_name 
```

```sql
DESCRIBE HISTORY 'path/to/your/delta/table' 
```
Registering a Delta table in the context of Apache Spark and Databricks involves creating a catalog entry for the table, which allows you to refer to it by name rather than by its storage path like above query. linking example:
```sql
CREATE TABLE my_delta_table 
USING delta 
LOCATION '/path/to/delta/table' 
```
version, timestamp and operation are few columns in describe history table.