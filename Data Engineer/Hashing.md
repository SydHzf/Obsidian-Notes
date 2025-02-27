___
**Definition:** We calculate the location of data block instead of using index table, where we have to write or read our record.
**Types:** 
- Static → Where we get same address again and again (103 mod 5 = 3 block)
	- Problem 
		- Getting same location for different record (Overflow), can be solved using Linear Probing
- Dynamic →  it is also called extensible, where hashing method is applied and answer prefix is check into directory table which points to actual data block. (00,01,10,11 if data increase then 000,001,0010,.....)
	- Same Problem which is solved by re-hashing.

## Applications of Hashing
In SQL databases, **hash tables** are used in various ways to optimize operations, particularly when dealing with joins, indexing, and lookups. The purpose of a hash table is to enable efficient data retrieval by mapping keys (like values from a column) to associated data. Here's how SQL databases use hash tables in different contexts:

### 1. **Hash Joins**
A **hash join** is a technique used by SQL query optimizers to join two tables efficiently, especially when there are no indexes on the columns being joined. In a hash join, hash tables are used to perform the join operation by creating a mapping between the rows of the two tables.

#### How a Hash Join Works:
1. **Build Phase**:
   - The database first creates a **hash table** on the smaller of the two tables (often called the **build input**).
   - It hashes the values of the join key (e.g., `customer_id` in the `customers` table) and stores them in the hash table.

2. **Probe Phase**:
   - The database then scans the second (larger) table (called the **probe input**) and checks for matching values in the hash table.
   - For each row in the probe table, the hash function is applied to the join key, and the hash table is checked for matches.

Since hash lookups are efficient (constant time complexity on average), **hash joins** are particularly useful for joining large datasets where nested loops or sorting might be too slow.

#### Example: 
Suppose you want to join two large tables, `Customers` and `Orders`, based on the `customer_id`.

```sql
SELECT *
FROM Customers c
JOIN Orders o
ON c.customer_id = o.customer_id;
```

If neither table has an index on `customer_id`, the database engine might decide to use a **hash join** to execute this query. It will:
1. Build a hash table on the smaller table (`Customers` or `Orders`, depending on size).
2. Probe the larger table by checking the hash table for matching `customer_id` values.

---

### 2. **Hash-Based Indexes**
A **hash index** is another use case where hash tables are employed. Instead of storing data in a sorted order (as in **B-tree indexes**), hash indexes use a hash table to map indexed values to the rows where they are located.

#### Key Features of Hash Indexes:
- **Efficient equality lookups**: Hash indexes are extremely efficient for exact match queries (e.g., `=` or `IN` conditions) because they offer constant time lookups.
- **Not suitable for range queries**: Unlike B-trees, hash indexes cannot efficiently handle range queries (e.g., `BETWEEN`, `<`, `>`) because hash functions scramble the order of values.

#### Example:
Consider a table `Employees` with a hash index on the `employee_id` column:

```sql
CREATE TABLE Employees (
    employee_id INT PRIMARY KEY,
    name VARCHAR(100),
    department VARCHAR(100)
);

CREATE INDEX hash_index ON Employees USING HASH (employee_id);
```

- When you run a query like `SELECT * FROM Employees WHERE employee_id = 123;`, the hash index will compute a hash of `123` and directly retrieve the corresponding row(s) without scanning the entire table.
- For a query like `SELECT * FROM Employees WHERE employee_id BETWEEN 100 AND 200;`, however, a hash index would not be useful, and the database would fall back to a different access method (like a full table scan).

Hash indexes are commonly used in databases like **PostgreSQL** or **MySQL** for cases where equality searches on specific columns are frequent and important.

---

### 3. **Hash Aggregation**
In SQL databases, **hash tables** are often used to perform aggregation operations (e.g., `GROUP BY`) efficiently. This is known as **hash aggregation**.

#### How Hash Aggregation Works:
- When performing an aggregation like `GROUP BY`, the database engine might use a hash table to group rows.
- As it scans the input data, the engine computes a hash for each row based on the `GROUP BY` columns and places the rows into different buckets in the hash table.
- For each group, it computes the aggregation (e.g., `SUM`, `COUNT`, `AVG`) and stores the result.

#### Example:
```sql
SELECT department, COUNT(*)
FROM Employees
GROUP BY department;
```

- The database might use a **hash table** where each unique department is a key, and the count is the value.
- As it scans through the `Employees` table, it hashes the `department` field, and for each match, it increments the count in the corresponding hash bucket.

Hash aggregation is very efficient for large datasets where the number of distinct groups is relatively small compared to the total number of rows.

---

### 4. **Hash Partitioning**
**Hash partitioning** is a technique used by databases to distribute data across multiple partitions or nodes in a distributed system. It uses a hash function to determine the partition or node where a particular row should be stored.

#### How Hash Partitioning Works:
- The hash function is applied to one or more columns (often the primary key) to compute a hash value.
- The result of the hash function determines which partition or node stores the row.

This technique helps evenly distribute data, which improves load balancing and query performance in distributed or sharded databases.

#### Example:
If you have a large distributed table `Customers` and you use hash partitioning on the `customer_id`, the database will use a hash function to assign each customer to a specific partition. Queries can then be routed to the appropriate partition, reducing the need to scan the entire dataset.

---

### 5. **Temporary Hash Tables**
In some cases, databases will create **temporary hash tables** in memory to speed up certain operations, like sorting or complex joins, particularly when the dataset is too large to fit in memory.

- Temporary hash tables are often created by the SQL query optimizer to handle subqueries, intermediate results, or complex calculations.
- These tables are usually discarded once the query execution is complete.

---

### Key Advantages of Hash Tables in SQL:
- **Speed**: Hash tables provide **constant time complexity** on average for lookups, making them fast for equality checks and joins.
- **Efficiency**: They reduce the need for full table scans or nested loops, improving performance in many scenarios.
- **Scalability**: Hash tables allow for efficient partitioning and sharding, especially in distributed database systems.

### Limitations:
- **Range Queries**: Hash tables are not efficient for **range-based** queries (e.g., `BETWEEN`, `<`, `>`), as the hashed values do not maintain any order.
- **Memory Usage**: Large hash tables can consume significant memory, especially for hash joins and aggregations on large datasets.

---
### Summary of Use Cases for Hash Tables in SQL:
1. **Hash Joins**: Used to join large tables when no suitable indexes are present.
2. **Hash-Based Indexes**: Used for fast lookups on equality conditions.
3. **Hash Aggregation**: Used in `GROUP BY` operations for efficient grouping and aggregation.
4. **Hash Partitioning**: Used to distribute data across partitions or nodes in a distributed database.
5. **Temporary Hash Tables**: Used for intermediate calculations during query execution.

By using hash tables, SQL databases can significantly optimize performance, particularly for joins, aggregations, and partitioning tasks.