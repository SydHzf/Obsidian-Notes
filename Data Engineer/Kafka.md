___
[Kafka And Zookeeper](https://youtube.com/playlist?list=PLxv3SnR5bZE82Cv4wozg2uZvaOlDEbO67&si=dzxDlANFtAeMpvJf)
**Definition:** Apache Kafka is an open-source distributed event streaming platform used for building real-time data pipelines and streaming applications.
						*Or*
Distributed publisher and subcriber system

Zookeeper is used to monitor the behavior of brokers also knows as Kafka servers
Clusters are used for replication and load balancing

**Partitioning** : Division of topics data
**Replicas** : How many replicas you want for each partition
**Leader** :  which broker has the main data  and responsible for read and write, other wil be follower
**ISR**: synchronized brokers with each other
**Controller Broker** : responsible for leader making , metadata(partition states,replica states, etc) broker failure , partitions reassignments, topic managing. Else this broker is treated similarly like other for partitions and replicas (leader or follower)


## **Offset** :
they like index in each partition
There are three type of offset
### 1. **Log-End Offset**

- The **log-end offset** is the **offset of the next message to be written** in a partition. It represents the highest offset in the partition, indicating the end of the log.
- For example, if a partition has messages with offsets 0, 1, and 2, the log-end offset would be 3, because the next message to be appended would get offset 3.
- This offset is used to track the current "end" of the partition and is essential for producers to know where to append new messages.

### 2. **Current Offset (or Consumer Offset)**

- The **current offset** is the **offset of the next message that a consumer will read** from the partition. It represents the position where the consumer is currently reading.
- When a consumer reads a message, it increments its current offset to point to the next message to be read.
- The current offset can vary among different consumers because each consumer keeps track of its own position independently.

### 3. **Committed Offset**

- The **committed offset** is the **last offset that a consumer has acknowledged as successfully processed**. This offset is stored in Kafka to ensure that, if the consumer restarts, it can resume reading from this position.
- Committing an offset indicates that all messages up to that offset have been processed, and the consumer can continue from the next offset.
- The committed offset is crucial for fault tolerance, allowing consumers to restart from a known position and avoid reprocessing or losing messages.

### How They Work Together:

- When a consumer reads from a partition, it starts at its committed offset and processes messages up to the log-end offset.
- The current offset keeps moving forward as messages are read.
- Once processing is complete, the consumer can commit the current offset to mark the messages as processed.

#### Topic Configuration:

- Topic Name: `orders`
- Partitions: 2
- Replication Factor: 3
- Brokers: 3 (Broker 1, Broker 2, Broker 3)

#### Partition Distribution:

- **Partition 0**:
    - Leader: Broker 1
    - Follower Replicas: Broker 2, Broker 3
- **Partition 1**:
    - Leader: Broker 2
    - Follower Replicas: Broker 1, Broker 3
![[Pasted image 20250213120256.png]]