___
**Definition**:
	A data warehouse is a large, centralized storage system that collects, stores, and manages data from different sources within an organization. It is designed specifically for query and analysis, rather than for transaction processing. Here’s an easy definition:
`		"A data warehouse is like a big digital library where all the important data from different parts of a company is stored in an organized way. This makes it easy to find and analyze information to help make business decisions, like looking at sales trends, customer behavior, or financial performance. Unlike everyday databases, which handle lots of small updates and transactions quickly, a data warehouse is optimized for reading and summarizing large amounts of data to get meaningful insights."
`
A serverless service is a cloud computing model where the cloud provider automatically manages the infrastructure needed to run applications. This means that users do not have to worry about provisioning, scaling, or managing servers.

**Related Content**:
Here are the names of some famous data warehouses:

1. Some [[Famous Data warehouses]] are *Amazon Redshift,Google BigQuery,Snowflake,Microsoft Azure Synapse Analytics,Teradata,IBM Db2 Warehouse,Oracle Autonomous Data Warehouse,SAP Data Warehouse Cloud,Vertica,Cloudera Data Warehouse*.
* [[ETL]] will be applied to insert data into warehouse
* [[Star Schema]] and [[Snowflake Schema]] are the way to organized data in warehouse also called data modeling (as data represent in table in database).
- [[OLTP (OnLine Transection Process)]] is the process of transaction, it not include any relation with the warehouse and [[OLAP (OnLine Analytics Process)]] is the process of doing analysis


- ### Dimension Table
	A dimension table is a type of table in a data warehouse that contains descriptive attributes (or fields) that are typically textual or categorical and are used to describe objects in a fact table. These tables help in providing context to the facts (numeric measurements) stored in fact tables. Each dimension table contains a primary key that uniquely identifies each dimension record, which is then referenced in the fact table.

	For example, in a sales data warehouse, a dimension table might be "Customer" with attributes like CustomerID, CustomerName, Address, City, and Country.
	
 - ### ER Modeling (Entity-Relationship Modeling)
	ER modeling is a data modeling technique used to define and describe the relationships between different data entities in a database. It involves creating an ER diagram that visually represents the data entities, their attributes, and the relationships between them. Key components of ER modeling include:
	- **Entities**: Objects or things in the real world that have a distinct existence, such as Customer, Product, or Order.
	- **Attributes**: Characteristics or properties of an entity, like a Customer's name or address.
	- **Relationships**: Associations between entities, such as a Customer placing an Order.
	
	ER modeling is commonly used in the design phase of a database to ensure the logical structure of the database aligns with business requirements.
	
- ### Dimensional Modeling in Data Warehousing
	Dimensional modeling is a design technique used in data warehouses to make it easier to retrieve and analyze data. This modeling approach focuses on how the data will be queried and reported rather than on the operational processes. The main components of dimensional modeling are:
	- **Fact Tables**: Central tables in a star or snowflake schema that contain quantitative data (facts) for analysis, like sales amounts, quantities, or transaction counts. Each fact table record is associated with dimension table records through foreign keys.
	- **Dimension Tables**: Tables that contain descriptive attributes related to dimensions of the data, providing context for the facts. Examples include dimensions like Time, Product, and Customer.
	- **Star Schema**: A simple schema where a fact table is at the center, connected directly to multiple dimension tables.
	- **Snowflake Schema**: A more complex schema where dimension tables are normalized, splitting data into additional tables to reduce redundancy.
	
	Dimensional modeling helps in creating a data warehouse structure that supports efficient querying, reporting, and analysis, making it easier for end users to understand and use the data.
	
- ### SCD Type 1, 2, 3
	- changing time dependant attributes over time
### **Comparison of SCD Types**

|SCD Type|History Maintained?|Table Size Growth|Use Case|
|---|---|---|---|
|Type 1|No|No|Overwriting is acceptable (e.g., corrections).|
|Type 2|Full History Maintained|Yes (New rows)|Tracking detailed historical changes (e.g., addresses).|
|Type 3|Limited History|Minimal|Only a few changes need to be tracked (e.g., current/previous status).|
	**Slowly Changing Dimensions (SCD)**:
	- SCD refers to how data in a data warehouse changes over time.

	**Type 1**:
	- Overwrites the old data with new data.
	- No history is preserved.
	
	**Type 2**:
	- Adds new records with new data, preserving the historical data.
	- Each record has a unique identifier and validity dates.
	
	**Type 3**:
	- Adds new columns to store both the old and new values.
	- Limited historical data is preserved.
![[Pasted image 20240819153307.png]]