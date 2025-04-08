[Colab Notebook](https://colab.research.google.com/drive/1V99NYVEn6WN7ElL9m0NIZbbfFOk4b-op?usp=sharing)
___

**Definition**: "Apache Spark is a powerful parallel data processing backend engine that can quickly analyze large datasets by distributing the work across many computers."
- Best with batch data.
- Use cluster of machine to break large task in small once.
- In each cluster there is always a Driver machine, which control everything telling executer machines what to do. (1 -> deriver , atmost 200 executer)
___
## Spark Ecosystem
![[SPARK ECOSYSTEM.canvas|SPARK ECOSYSTEM|3000]]


![[Pasted image 20250102225352.png]]
**Cluster Manager** : It is also a computer which assign driver and executors
**Driver**: The driver is the machine in which application runs. It is responsible for 3 main things:
    - Maintaining information about the spark application
    - Responding to user's program
    - Analyzing, distributing and scheduling work across the executors
    
**Executors** Each executor will hold the chunk of the data to be processed. This chunk is called partition. It is a collection of rows that sits on one physical machine in the cluster. The executors are responsible for carrying out the work assigned by the driver. Each executor is responsible for 2 things:
      - Execute the code assigned by driver
      - Report the state of the computation back to the driver

**Task**
Tasks are created by the driver and assigned a partition of data to process. A partition is a collection of rows. Then sits on one physical machine in your cluster. Then tasks are assigned to slots for parallel execution. Once started each task will fetch its assigned partition from the original data source
___
## Transformation and Actions in Spark.
- Data transformation is called **Transformation**
	- narrow transformation is independant
	- wide transformation is dependant
- To see the progress and other thing is **Action**.
	- When action is hit, a job is created with a DAG
	- output come to driver
	The code we write is either transformation or action
Fault Tolerance is handle by DAG, calculating process again if its data failed.
___
## Spark SQL Engine Compiler(Catalyst Optimizer)
![[Pasted image 20250311232705.png]]
 convert our code into RDD(Java Bytes code)
 - It Works in 4 phases
	 1. **Analysis Phase**: convert our unresolved logical plan into resolved logical plan checking catalog (metadata). checking did the file name , table name , column name exist or not
	 2. **Logical Planning**: do optimization on resolved logical plan (lazy evaluation)
	 3. **Physical Planning or Spark planning**: create multiple plans and find the best physical plan (joins etc) by cost_modeling
	 4. **Code generation**: each executor gets this code to execute it.
 ___
## RDD (Data Structure)
- Immutable
- Are rdd self-created??
	![[Pasted image 20250123162637.png]]
	
___
## Repartition vs Coalesce
___
- Repartition
	- increase or decrease no of partition
	- shuffling occur
	- can be done on number or column or on both (eg : .reparttion(8,column_name))
- Coalesce
	- only decrease no of partition
	- very small shuffling
	- only on number (eg : .coalesce(8))
## Spark Optimization Techniques
https://luminousmen.com/post/the-5-minute-guide-to-using-bucketing-in-pyspark
![[spark_optimization.pdf]]
