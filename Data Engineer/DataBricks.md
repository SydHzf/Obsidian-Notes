___
**Definition:** Databricks is an integrated data analytics platform that simplifies big data and machine learning workflows. It combines the power of Apache Spark with collaborative tools, making it easier for data engineers, data scientists, and business analysts to work together on a unified analytics platform.

`dbutils` → to interact with Databricks
# Basic Components
### 1. Workspace (Simple folder)
The **Workspace** in Databricks is like a shared online office where you can store and organize all your data-related projects. It holds your notebooks, libraries, and other data assets in a structured way, making it easy for team members to collaborate and access the necessary resources.

### 2. Notebook (Coding file)
A **Notebook** is an interactive document where you can write and run code, visualize data, and document your analysis. Think of it as a digital notebook where you can combine code, text, and visualizations. Databricks notebooks support multiple languages like Python, SQL, Scala, and R.

### 3. Library 
A **Library** is a collection of code, typically packaged in a way that makes it reusable. In Databricks, libraries are like toolboxes that contain functions, classes, and other useful code. You can import and use these libraries in your notebooks to perform various tasks without writing everything from scratch.

### 4. Databricks File System (DBFS)
The **Databricks File System (DBFS)** is a distributed file system that’s integrated with Databricks. It provides a way to store and access files (like datasets, scripts, or logs) in your Databricks environment. You can think of DBFS as a cloud-based storage drive that is easily accessible from within your notebooks and clusters.

### 5. Cluster
A **Cluster** in Databricks is a group of virtual machines that work together to process your data. Clusters are the computing resources you use to run your notebooks and jobs. You can configure clusters based on your computing needs, such as the number of machines(Driver Node and Workers Nodes), their specifications, and how long they should run.
- All-purpose cluster which are created and managed by us.
- Job cluster are manage by jobs.

### 6. Pool
A **Pool** is a way to manage and optimize the creation of clusters in Databricks. It’s a set of ready-to-use virtual machines that can be quickly attached to a cluster, reducing the time it takes to start a new cluster. Pools help save time and cost by reusing idle virtual machines instead of creating new ones from scratch each time.

### 7. Job
A **Job** in Databricks is a way to automate the execution of notebooks or workflows. You can schedule jobs to run at specific times or in response to certain triggers. Jobs are useful for performing regular data processing tasks, running ETL (Extract, Transform, Load) processes, or generating reports automatically.

# Architecture
Azure Databricks operates out of a control plane and a data plane.

-> The **control plane** includes the backend  services that Azure Databricks manages in its own Azure account. Notebook commands and many other workspace configurations are stored in the control plane and encrypted at rest.

-> The **data plane** is managed by your Azure account and is where your data resides. This is also where data is processed. You can use Azure Databricks connectors so that your clusters can connect to external data sources outside your Azure account to ingest data or for storage. You can also ingest data from external streaming data sources, such as events data, streaming data, loT data, and more.

![[Pasted image 20240610184703.png]]


This is the best way to learn Data Engineering on Databricks 👇  

1. Introduction & Fundamentals  
✅ Why Databricks  
✅ Understand the Databricks pricing  
  
2. Databricks Setup  
✅ Create yor Databricks Account & Workspace  
✅ Understand the AWS Resources created by Databricks  
✅ Experience the Databricks UI & Compute Cluster  
  
3. Data & Code  
✅ Take a simple dataset like a e-commerce one  
✅ Set goals for an ETL & Visualization pipeline  
✅ Import Data in Databricks UI  
✅ Find the Databricks Data in S3  
✅ Create code Repos  
  
4. Processing & Visualization  
✅ Run your ETL job  
✅ Explore Data Tables in AWS folders  
✅ Explore data with databricks notebooks  
  
5. External Data Access & BI  
✅ Why: Compute Cluster vs Databricks SQL Warehouse  
✅ Run Power BI queries through computer cluster  
✅ Run Power BI queries through Databricks SQL Warehouse