### Execution Order :
- order by can use columns other than in select clause
![[sql_execution.gif|300]]
### Groupings:
- group by
- rollup
- cube
- grouping set
### Joins:
[Sql Joins Part1](https://youtu.be/0OQJDd3QqQM?si=xPtovN_A9zw8jq8f)
[Sql Joins Part2](https://www.youtube.com/watch?v=RehbnzKHS28&list=PLavw5C92dz9Ef4E-1Zi9KfCTXS_IN8gXZ&index=7&ab_channel=techTFQ)
- *Inner Join* : retrieve only those record which are true on the given condition 
- *Left Join*: Inner Join + remaining records of left table.
- *Right Join*: Inner Join + remaining records of right table.
- *Outer Join*: Right Join + Left Join.
- *Cross Join* : multiplication of left table records to each right table record.
- *Natural Join* : check if there is any similar column name in both tables (otherwise cross product them)
- *Self Join*: It is a self joining technique on a particular condition.
### Indexing:
Indexes in databases can significantly improve query performance but also come with trade-offs. Here are the advantages and disadvantages:

### **Advantages of Indexes**

1. **Faster Query Performance**
    
    - Indexes speed up `SELECT` queries by allowing the database to find rows more efficiently rather than scanning the entire table.
2. **Efficient Sorting and Filtering**
    
    - `ORDER BY`, `GROUP BY`, and `WHERE` clauses benefit from indexes since they reduce the need for sorting and filtering on large datasets.
3. **Improved Joins**
    
    - When joining tables, indexes help in quickly locating matching rows, optimizing performance.
4. **Optimized Searching**
    
    - Searching for records using indexed columns (`WHERE` conditions) is significantly faster.
5. **Uniqueness Enforcement**
    
    - Unique indexes ensure that duplicate values are not inserted into a column (e.g., primary keys).

### **Disadvantages of Indexes**

1. **Increased Storage Requirements**
    
    - Indexes take up additional disk space, which grows as the dataset expands.
2. **Slower Write Operations (`INSERT`, `UPDATE`, `DELETE`)**
    
    - Every time a row is added, deleted, or modified, indexes must be updated, which can slow down write operations.
3. **Complexity in Maintenance**
    
    - More indexes mean more maintenance, such as rebuilding or reorganizing indexes to prevent fragmentation.
4. **Potential Overhead for Small Tables**
    
    - For small datasets, full table scans might be as fast or even faster than using an index.
5. **Possibility of Wrong Index Usage**
    
    - If an index is not designed correctly, the database may not use it effectively, leading to suboptimal performance.

Would you like specific indexing strategies or best practices for data engineering use cases

*Gate smasher* 93~99 [Indexing and Its types](https://youtube.com/playlist?list=PLxCzCOWd7aiFAN6I8CuViBuCdJgiOkT2Y&si=YjgUYxxClrh5rNji)
- *Indexing* : A way to optimize i/o cost by creating a separate index table which points towards the location of block of that specific record.
![[Pasted image 20240729155920.png]]
- *Index Table* : it is the logical location in HD where key of the records are saved with their block location. Table can be Dense or Sparse (means might have all the keys of unordered records or some keys of ordered records)
- *Types Of indexing*:
	![[Screenshot 2024-07-29 151548 1.png]]
	
**Sparse**
- *Primary Index*: have ordered and unique key, so each key in table will be anchored of its block. 
```SQL
		CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    FirstName VARCHAR(50),
    LastName VARCHAR(50),
    Department VARCHAR(50)
);
```
- *Cluster Index*: have ordered but not-unique . so we create it using block hanker
```SQL
CREATE CLUSTERED INDEX idx_Employees_Department
ON Employees (Department);
```

**Dense**
- *Secondary*: have unordered but;
	- unique key, so all the keys in table will be sorted
	- not unique, so we will use a intermediate layer (table -> layer -> Record)
		- At intermidiate layer there are one pointer block for each value
```Sql
CREATE NONCLUSTERED INDEX idx_Employees_LastName
ON Employees (LastName);
```
![[Pasted image 20240729162721.png]]
### Constrains:
- *Check*: control values inserting into column.
- *Not Null* : Can be anything except null in a column.
- *Unique*: control every row need to be unique , one null is allow.
- *Primary Key* : each table has only one  PK,  it can be a single column or combination of multiple columns, No null values.
- *Foreign Key*: similar column between Parent and child to build relation.
### Keywords:
- distinct -> return unique values from a column
- union -> combine and return unique sorted records of two columns atleast (atmost two tables)
### Some extra content :
- sql optimization -> [[SQL Optimization.pdf]] 
- sql commands -> [[SQL COMMAND .pdf]]
- major topics -> [[Masters SQL in 16 Pages.pdf]]
- practice questions -> [[SQL Questions.pdf]]
### Why We Use Views

1. **Simplicity**:
   - **Simplified Queries**: Views can encapsulate complex queries involving joins, aggregations, and subqueries, allowing users to query a simpler "virtual table" without dealing with complex SQL syntax repeatedly.
   
2. **Security**:
   - **Access Control**: Views can restrict access to sensitive data by exposing only specific columns or rows to users, without granting them direct access to the underlying tables.
   
3. **Consistency**:
   - **Data Consistency**: Views can present a consistent interface to the data, even if the underlying schema changes. The view definition can remain the same, shielding users from changes in the table structure.

4. **Reusability**:
   - **Reusable Logic**: Views allow you to encapsulate and reuse SQL logic. This can reduce redundancy and improve maintainability, as changes in business logic only need to be updated in the view definition.

5. **Abstraction**:
   - **Abstraction Layer**: Views provide an abstraction layer, hiding the complexity of the database schema and allowing users to interact with a simplified representation of the data.

### How to Use Views

#### Creating a View

You can create a view using the `CREATE VIEW` statement. Here’s a basic example:

```sql
CREATE VIEW view_name AS
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

#### Example

Consider a database with the following `Employees` table:

| EmployeeID | FirstName | LastName | Department | Salary |
|------------|-----------|----------|------------|--------|
| 1          | John      | Doe      | HR         | 60000  |
| 2          | Jane      | Smith    | IT         | 80000  |
| 3          | Mike      | Brown    | Finance    | 75000  |
| 4          | Sue       | Green    | IT         | 82000  |

You want to create a view that shows only IT department employees with their names and salaries:

```sql
CREATE VIEW IT_Employees AS
SELECT FirstName, LastName, Salary
FROM Employees
WHERE Department = 'IT';
```

#### Using the View

Once created, you can query the view just like a regular table:

```sql
SELECT * FROM IT_Employees;
```

This query would return:

| FirstName | LastName | Salary |
|-----------|----------|--------|
| Jane      | Smith    | 80000  |
| Sue       | Green    | 82000  |

#### Updating a View

If you need to modify a view, you can use the `ALTER VIEW` statement (in some databases) or drop and recreate the view:

```sql
ALTER VIEW IT_Employees AS
SELECT FirstName, LastName, Salary
FROM Employees
WHERE Department = 'IT' AND Salary > 75000;
```

Or:

```sql
DROP VIEW IT_Employees;

CREATE VIEW IT_Employees AS
SELECT FirstName, LastName, Salary
FROM Employees
WHERE Department = 'IT' AND Salary > 75000;
```

#### Dropping a View

If you no longer need a view, you can drop it:

```sql
DROP VIEW view_name;
```

### Important Considerations

1. **Performance**:
   - **Materialized Views**: Some databases support materialized views, which store the result set of the view physically. This can improve performance for complex queries but requires managing the view's data refresh.

2. **Read-Only Views**:
   - **Update Limitations**: Standard views are usually read-only. To allow updates through a view, you may need to create an `INSTEAD OF` trigger or use updatable views if your DBMS supports them.

3. **Schema Dependencies**:
   - **Dependency Management**: Views depend on the underlying tables. Changes to the table schema (like renaming columns) can invalidate views.

By using views, you can abstract complex queries, enhance security, and simplify data access for users. Views provide a flexible way to present data without altering the underlying table structure.