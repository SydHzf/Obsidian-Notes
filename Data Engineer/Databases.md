- # [[Relational Databases]]:
	- A Relational Database Management System, or RDBMS, is a type of database management system that is based on the relational model of data. In an RDBMS:
		
		1. Data is organized into tables: Data is stored in structured tables with rows and columns. Each table represents a specific entity or concept, and each row represents an individual record, while columns define the attributes or properties of the records.
		    
		2. Tables have defined schemas: RDBMS enforces a schema that defines the structure and data types of each column in a table. This schema ensures data consistency and integrity.
		    
		3. Data is related: RDBMS allows for the establishment of relationships between tables through keys (usually [[primary key| primary ]] and [[foreign key|foreign keys]]). This enables data retrieval and manipulation using [[SQL]] (Structured Query Language) to perform complex queries and operations.
		    
		4. [[Transaction|ACID]] properties: RDBMS systems are known for their support of ACID properties (Atomicity, Consistency, Isolation, Durability), which guarantee data integrity and reliability, even in the face of system failures.
		
- # [[Non-Relation Databases]]:
	- Non-RDBMS, often referred to as NoSQL databases, are a class of database management systems that do not strictly adhere to the traditional relational model. They are designed to handle large volumes of unstructured or semi-structured data and can be more flexible in their data model. Key characteristics of non-RDBMS databases include:
		
		1. Flexible data models: NoSQL databases can store data in various formats, including key-value, document, column-family, and graph. This flexibility allows them to handle diverse data types and structures.
		    
		2. Scalability: NoSQL databases are often designed to be distributed and horizontally scalable, making them suitable for managing big data and high-velocity data streams.
		    
		3. No fixed schema: NoSQL databases do not enforce a fixed schema, allowing for dynamic data changes and adaptation to evolving requirements.
		    
		4. Eventual consistency: Some NoSQL databases may prioritize availability and partition tolerance over strong consistency, which means they can provide "eventual consistency" in distributed environments.
