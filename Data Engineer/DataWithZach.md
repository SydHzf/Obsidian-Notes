____
 - Notes [Albert Campillo, MSc
](https://www.linkedin.com/in/albertcampillo/overlay/about-this-profile/?lipi=urn%3Ali%3Apage%3Ad_flagship3_profile_view_base%3BuElq%2FvTESoWCxuF1j3inJw%3D%3D)
- **Storage is cheaper than compute**.
* **Data Integrity ≠ Data Ingestion** (Data Integrity Ensures the accuracy, consistency, and reliability of data throughout its lifecycle.  Data Ingestion is a process of collecting, importing, and loading data into a system for further processing or storage.)
* **Schema ≠ Table** (schema is the structure; tables are part of it). Schema = blueprint database.
- **Dimension ≠ Column** (dimension represents attributes, often a combination of related columns).
- **Cardinality ≠ Unique Row** (cardinality is about unique values in a column).
- **Tradeoff**: refers to the balance or compromise between different desirable qualities or goals when managing, processing, or analyzing data.
- **Dimension data**: Describes things (who, what, where, when).
- **Fact data**: Measures things (how much, how many).
___
- ## **Dimensional Data Modeling** 
	[[Dimension Data Modelling PDFs]]
	 - [[OLTP (OnLine Transection Process)]]
	 - [[OLAP (OnLine Analytics Process)]]
	 - [[Commulative Table Design]]
	 - [[Master Data]]
			![[Pasted image 20241210112311.png]]
	- [[Compact Vs Usability Tradeoff]]
	- [[Temporal Cardinality Explosions Of Dimensions]]
	- [[Idempotent Pipeline]]
	- [[SCD]]
	- [[Addictive and Non-Addictive Dimension]]
	- [[Power of Enums]]
	- [[Flexible Data Type]]
	- [[Graph data Modelling]]
___
- ## Fact Data Modeling [[(summary)]]
	- [[What is Fact Data ]]
	- [[How fact modeling work]]
	- [[When Should you model in dimensions]] (denormalization)
	- [[Potential option while working with high volume fact data]]
	- [[Dedeplication of fact data]]
	- [[streaming to dedeplicate data]]
	- [[Hourly Microbactch Dedup]]
	- [[Understanding, is this fact or dimension]]
	- [[Date List data Structure]]
	- [[Shuffle bottle neck of Parallelism]]
	- [[Making group By more efficient]]
	- [[Reducing fact data modelling]]
- ## Spark + Iceburg
	- [[What is Apache Spark]]
	- [[Why spark is so good]]
	- [[When not so Good]]
	- [[How does spark work]]
	- [[The Stretagies of joins]]
	- [[How does shuffle work]]
	- [[Shuffle Partition And Shuffle Parallelism]]
	- [[how to minimize the shuffle at hight volumes]]
	- [[Shuffle and skew]]
	- [[Spark Server vs Notebook]]
	- [[Caching and Temporary View]]
	- [[caching and broadcast]]
	- [[UDF's vs UDAF's]]
	- [[DataFrames vs Datasets vs SparkSQL]]
## Applying Analytical Patterns
- [[Repeatable Analysis]]
- [[common pattern]]
- [[Data Funnel]]
- [[Grouping Set , cube and rollup]]
## Real-time pipelines with Flink and Kafka
- Streaming,real-time,near real-time and micro batch processing
- Sources (Kafka & Enriche dimensional sources i.e. side inputs)
- Compute Engines (Flink & Spark Structure Streaming)
- Sink (kafka ,Iceberg & Postgres)
- Streaming Architecture (Lambda Architecture and Kappa Architecture)
- [[ Flink's Windows]]
- Allowed Lateness & Watermark
micro batch = near real time = small batch
micro batch != near real time 
- **Streaming** = Continuous flow of data.
- **Real-time** = **Ultra-low latency** (milliseconds).
- **Near real-time** = **Slight delays** (seconds to minutes).
- **Micro-batch** = **Small chunks of data** processed at intervals.
