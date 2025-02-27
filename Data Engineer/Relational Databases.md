## 1. PostgresSQL:
- it has strong transactional support, so it mostly used in [[OLTP (OnLine Transection Process)]] (Online Transaction Processing).
- It is an object-oriented relational database.
```sql
-- Create a custom data type
CREATE TYPE address AS (
    street text,
    city text,
    zip_code text
);

-- Create a table using the custom data type
CREATE TABLE employees (
    employee_id serial PRIMARY KEY,
    first_name text,
    last_name text,
    emp_address address
);

-- Insert data into the table
INSERT INTO employees (first_name, last_name, emp_address)
VALUES
    ('John', 'Doe', ROW('123 Main St', 'Cityville', '12345')),
    ('Jane', 'Smith', ROW('456 Elm St', 'Townsville', '67890'));

```
- Work with *[[ACID]]*("Atomicity, Consistency, Isolation and  Durability") and also with its signature sauce *[[MUCC]]*("Multiple Unit Consistency Control.").
- If we want to make PostgreSQL fast we can use five things named ; [[prepare]], [[index]], [[partition]],[[copy]] and [[replica]]. [Youtube Video here](https://www.youtube.com/watch?v=YON9PliOYFk&ab_channel=DreamsofCode)
- There are several popular Python [[ORM]] libraries that support PostgreSQL, named [[SQLAlchemy]], DJango , Peewee etc.

# 2. MySql:       
    
6. Primary Keys and Indexes: Defining [[primary key | primary keys]] and [[index |indexes]] on your database tables helps speed up data retrieval and maintain data integrity.
    
7. Transactions: MySQL supports transactions, which allows you to group multiple SQL statements into a single unit of work. This ensures data consistency and integrity.
    
8. ACID Compliance: MySQL follows the [[ACID]] (Atomicity, Consistency, Isolation, Durability) properties, which ensure that database transactions are processed reliably and safely.
    
9. Storage Engines: MySQL offers different storage engines, such as InnoDB, MyISAM, and more. Each engine has its own strengths and weaknesses, making it suitable for different use cases.
    
10. Security: MySQL provides robust security features, including user authentication, encryption, and access control. It's essential to secure your MySQL installation to protect your data.
    
11. Replication: MySQL supports [[replication]], which allows you to create copies (replicas) of your database for load balancing, failover, and data redundancy.
    
12. High Availability: Various techniques and tools can be used to achieve high availability in MySQL, such as [[clustering]], [[load balancing]], and [[failover solutions]].
    
13. Backup and Recovery: Regularly backing up your MySQL databases is crucial to protect against data loss. MySQL provides tools and utilities for backup and recovery.

14. Performance Optimization: Optimizing MySQL performance involves factors like query optimization, indexing, proper configuration, and hardware resources. MySQL offers various tools for profiling and tuning.
    
15. Scalability: MySQL can be scaled vertically (adding more resources to a single server) or horizontally (distributing the load across multiple servers) to handle increased data and user loads.

    

