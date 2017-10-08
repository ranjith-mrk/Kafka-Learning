##### Apache Kafka is a distributed storage platform

Kafka used for:-

1. Building realtime streaming data pipelines
2. Building realtime streaming applications for transforming data

#### Kafka Basics:

* Kafka is run as a cluster on multiple servers
* It stores streams of records in categories(topics)
* Each record consists of key, value and timestamp as its properties

#### Kafka Core Apis:

1. **Producer Api** - Publish stream of records to kafka topics
2. **Consumer Api** - Subscripe to one or more topics and process stream of records
3. **Streams Api** - Allows an application fo function as a stream processor. It is used for transforming data in between the streams
4. **Connector Api** - Reusable components for producer or consumer to connect to existing applications.

#### Topics and Logs

**Topic** Is the feed name for records. It is always multi subscriber allowing multiple consumers. Structure of a topic is as below, 

![Image of Apache Topic](https://kafka.apache.org/0110/images/log_anatomy.png)

Each topic can have multiple partitions as shown above. Each partition is ordered with each record having a sequential id, which is identified with the help of offset. All records exist in kafka despite being consumed or not, based on the retention policy. Beyond the retention policy the records are cleared.

For each consumer only it's metadata is stored based on which the record is identified in the stream. The metadata contains information like offset to identify the location.

#### Distribution

Partition of log id distributed across servers. This increases fault tolerance. The world load is handled by a "leader". If it goes offline, another leader is selected.

#### Producers

Producers publish data to topics.

#### Consumers

Consumers within consumer group receive records. Consumer group is a logical collection of consumers within which the records are consumed to increase performance within the group by sharing the load between the various consumers. The messages will be broadcast to different consumer groups.

The process of membership if handled by kafka protocol.

![Consumer group](https://kafka.apache.org/0110/images/consumer-groups.png)

#### Guarantees

* Maintain order of records within a partition
* Fault tolerance based on replication factor

#### Kafka as a Messaging System

Kafka manages between queueing system and publish and subscribe model. In queueing system data is read by multiple systems, enhancing fault tolerance. But it has a limitation.  When one consumer reads the message, it is gone permanently. In case of publish subscriber model, each message is replicated across to various subscribers.

Kafka offers a middle ground by maintaining a queueing system which is associated to a consumer group. Within which the messages are distributed to different consumers. It follows publish subscriber pattern by publishing messages across various consumer groups


#### Kafka as a Storage System

Messages are not dependent on their usage based on consumption. This enhances fault tolerance based on replication. 

#### Kafka for Stream Processing

Kafka handles input streams and performs processing and transforms them to the output stream. 
