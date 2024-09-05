Compression in spark: When reading spark automatically detect compression codec from the file extension and decompresses on the fly to read in memory. After processing allows to specify compressions codec when writing to storage. Supports: bzip2, gzip, lz4, snappy, and deflate etc. 
#### Pros and cons

| File Format  | Advantages                                             | Disadvantages                             | When to Use                                                       |
| ------------ | ------------------------------------------------------ | ----------------------------------------- | ----------------------------------------------------------------- |
| CSV          | Simple, widely supported, human-readable.              | No schema, inefficient for large data.    | Simple data exchanges with low performance requirements.          |
| JSON         | Flexible, hierarchical data, human-readable.           | Verbose, resource-intensive.              | Web applications, nested data structures.                         |
| Avro         | Schema evolution, compact, binary.                     | Not human-readable, schema management.    | Systems requiring schema evolution, binary efficiency.            |
| Parquet      | Efficient compression, schema evolution, columnar.     | Complex, high write overhead.             | Analytical queries on large datasets in data analytics platforms. |
| ORC          | Optimized for reading, indexing, good compression.     | Limited flexibility, high write overhead. | Hadoop environments for large-scale processing.                   |
| SequenceFile | Binary format, integrates well with Hadoop, key-value. | Limited use outside Hadoop.               | Intermediate data storage in Hadoop MapReduce jobs.               |
#### Properties

| File Format  | Compression                        | Format Type | Serialization    | Mechanism                            | Ideal for                                     |
| ------------ | ---------------------------------- | ----------- | ---------------- | ------------------------------------ | --------------------------------------------- |
| CSV          | External (gzip)                    | Row-based   | Text-based       | Delimited text                       | Simple flat data, small-scale imports/exports |
| JSON         | External (gzip)                    | Row-based   | Text-based       | Hierarchical, attribute-value pairs  | Web data, configurations, small documents     |
| Avro         | Native (Snappy, Deflate, Bzip2)    | Row-based   | Binary           | Schema-descriptive, binary           | Big data transactions, event logging          |
| Parquet      | Native (Snappy, GZIP, LZO, Brotli) | Columnar    | Binary, columnar | Columnar storage, efficient indexing | Large-scale analytics, complex queries        |
| ORC          | Native (Snappy, ZLIB, LZO)         | Columnar    | Binary, columnar | Columnar storage, stripe indexing    | Hadoop environments, heavy-read operations    |
| SequenceFile | Native (Block compression)         | Row-based   | Binary           | Sequential key-value pairs           | Intermediate data storage in Hadoop           |
