## Data Ingestion
This week you will dive deep into the batch and streaming ingestion patterns. 
You will identify use cases and considerations for each, and then build a batch and a 
streaming ingestion pipeline. When looking at batch ingestion, you will compare and 
contrast the ETL and ELT paradigms. You will also explore various AWS services for batch 
and streaming ingestion.

### Learning Objectives
1. **Batch vs. Streaming Ingestion**: Learn the differences between batch and streaming ingestion, 
    their use cases, and how they vary based on ingestion frequency.

2. **Ingestion Methods**: Identify different methods to ingest data from various source systems 
    depending on the specific use cases.

3. **ETL vs. ELT**: Understand and differentiate between the Extract-Transform-Load (ETL) and 
    Extract-Load-Transform (ELT) paradigms in data processing.

4. **API Data Ingestion**: Learn to interact with REST APIs and create scripts to ingest data from the API.

5. **Event-Streaming Platforms**: Describe the components of an event-streaming platform 
    (topics/streams, partitions/shards) and understand how to interact with it as both a source system 
    and an ingestion tool.
 
### Outlines
1. [Data Ingestion Overview](#data-ingestion-overview)
- 1.1 [Data Ingestion on a Continuum](#data-ingestion-on-a-continuum)
- 1.2 [Batch and Streaming Ingestion Tools](#batch-and-streaming-ingestion-tools)
2. [Batch Ingestion](#batch-ingestion)
- 2.1 [Conversation with a Marketing Analyst](#conversation-with-a-marketing-analyst)
- 2.2 [ETL vs. ELT](#etl-vs-elt)
- 2.3 [Summary of the Differences: ETL vs. ELT](#summary-of-the-differences-etl-vs-elt)
- 2.4 [REST API](#rest-api)
- 2.5 [Lab 1 - Batch Data Processing from an API](./Lab%201-%20Batch%20Data%20Processing%20from%20an%20API/)
3. [Streaming Ingestion](#streaming-ingestion)
- 3.1 [Conversation with a Software Engineer](#conversation-with-a-software-engineer)
- 3.2 [Streaming Ingestion Details](#streaming-ingestion-details)
- 3.3 [Kinesis Data Streams Details](#kinesis-data-streams-details)
- 3.4 [Change Data Capture (CDC)](#change-data-capture-cdc)
- 3.5 [Summary: General Considerations for Choosing Ingestion Tools]()
- 3.5 [Lab 2 - Streaming Ingestion](./Lab%202%20-%20Streaming%20Ingestion/)

## Data Ingestion Overview
### Data Ingestion on a Continuum
1. **Data as a Continuous Stream**: All data can be viewed as a continuous stream of events, 
    whether it's stock price changes, user clicks, or sports scores. Ingestion involves capturing this data.

2. **Stream vs. Batch Ingestion**: 
   - **Stream ingestion** processes events individually as they happen.
   - **Batch ingestion** groups and processes data in bounded chunks 
        (e.g., time-based, size-based, or record-count-based).
   
3. **Ingestion Continuum**: 
   - As batch ingestion becomes more frequent, it approaches real-time stream ingestion. 
   - Batch and streaming exist along a continuum rather than being entirely separate concepts.

4. **Ingestion Tools**: Depending on the source system, different tools and methods are used:
   - **Databases**: JDBC/ODBC connectors or tools like AWS Glue for regular ingestion.
   - **APIs**: Custom connections or API-specific client libraries, but subject to API limitations and constraints.
   - **Files**: SFTP, SCP, or manual ingestion from object storage.
   - **Streaming Systems**: Message queues or tools like AWS Kinesis for streaming data (e.g., IoT devices).

5. **Use Cases**: This week focuses on practical ingestion examples:
   - **Batch ingestion** from an API.
   - **Streaming ingestion** using a Kinesis Data Stream.

### Batch and Streaming Ingestion Tools  

#### Batch Ingestion Tools:
1. **AWS Glue ETL**:
   - **Function**: Extract, transform, and load data from sources like Amazon RDS, S3, Redshift, and DynamoDB.
   - **Technology**: Uses Apache Spark to distribute workloads.
   - **Environment**: Serverless, code-based solutions for ingestion and transformation.

2. **Amazon EMR**:
   - **Function**: Managed platform to run big data frameworks like Apache Hadoop and Spark for 
   large-scale data ingestion and transformation.
   - **Modes**: Serverless or provisioned mode with configurable compute resources.

3. **AWS DMS (Data Migration Service)**:
   - **Function**: Syncs or migrates data between databases or from databases to other AWS services without transformation.
   - **Modes**: Serverless or provisioned.

4. **AWS Snow Family**:
   - **Function**: Transfers large-scale data (e.g., 100TB+) from on-premise systems to AWS using physical devices like Snowmobile.
   - **Use Case**: Offline migration of large datasets.

5. **AWS Transfer Family**:
   - **Function**: Transfers files into and out of Amazon S3 using SFTP/FTP protocols.

6. **Non-AWS Tools**:
   - **Examples**: 
     - **Airbyte**, **Matillion**, **Fivetran**: Connectors for ingesting data from various sources into different 
     target systems across cloud platforms.

#### Streaming Ingestion Tools:
1. **Amazon Kinesis Data Streams**:
   - **Function**: Real-time data streaming for data analytics and ingestion.
   
2. **Amazon MSK (Managed Streaming for Apache Kafka)**:
   - **Function**: Managed Kafka service for real-time data ingestion and stream processing.

#### Key Considerations for Batch vs. Streaming Ingestion:
1. **Use Cases**: Can real-time data improve actions compared to periodic batch updates?
2. **Machine Learning**: Use batch for model training or explore continuous training if necessary.
3. **Dashboards/Reporting**: Evaluate if real-time data adds value over periodic updates.
4. **Latency**: Determine if real-time data is needed or if micro-batching is sufficient.
5. **Cost**: Streaming may be more complex and costly than batch ingestion.
6. **Team Skills**: Assess your team's ability to manage and troubleshoot a streaming platform.
7. **System Impact**: Consider the impact of streaming ingestion on source and destination systems.
8. **Reliability**: Streaming systems require high availability; batch systems do not.
9. **Hybrid Approaches**: Consider using both batch and streaming for certain use cases 
    (e.g., lambda architecture). 

## Batch Ingestion
### Conversation with a Marketing Analyst

1. The conversation focuses on gathering insights from external factors that may influence 
    customer purchasing habits, such as regional music trends.
2. The marketing analyst suggests using Spotify's public API to pull data on trending music and 
    compare it with product sales data.
3. The data engineer agrees to investigate Spotify's API and discuss further details on the specific 
    information needed.
4. The main task is to ingest data from a third-party API and eventually figure out storage and 
    serving of the data.
5. Batch ingestion is the likely approach, and tradeoffs between ETL (Extract, Transform, Load) and ELT 
    (Extract, Load, Transform) will be explored in subsequent videos.

### ETL vs. ELT

1. The project involves incorporating external data from a third-party API into an analysis of product sales.
2. The data ingestion process will be batch-based, due to API limitations on request frequency.
3. ETL (Extract, Transform, Load) transforms data before storage, optimizing for storage constraints 
    and specific use cases.
4. ELT (Extract, Load, Transform) loads raw data directly into storage, allowing flexibility 
    in future transformations.
5. ELT is faster to implement, as it doesn't require detailed planning upfront, but can lead to 
    disorganized data if not managed properly.
6. ELT is suitable for this project because the marketing analyst aims to perform exploratory analysis 
    and cannot define specific data transformations upfront. 

### Summary of the Differences: ETL vs. ELT
| Feature                       | ETL                                                                                     | ELT                                                                                   |
|-------------------------------|-----------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|
| **History**                   | - Developed in the 80s/90s due to high data warehouse costs.                          | - Emerged with cloud data warehouses reducing costs significantly.                    |
|                               | - Data volume was manageable.                                                          | - Data volume exploded.                                                                |
| **Processing (Transformation)**| - Data transformed into a predetermined format before loading.                         | - Raw data loaded first, then transformed just before analytics.                      |
|                               | - Transformation relies on processing tool, not destination.                          | - Transformation relies on the processing power of the data repository.              |
| **Maintenance Time**          | - Requires re-loading if transformation is inadequate.                                 | - Original data intact; less time for maintenance.                                   |
| **Load & Transformation Time**| - Longer load time due to staging area; variable transformation time.                  | - No transformation during load, making it faster; relies on data warehouse power.   |
| **Flexibility (Data Types)**  | - Typically handles structured data.                                                   | - Can handle structured, unstructured, and semi-structured data.                     |
| **Cost**                      | - Varies by tool and target system; depends on data volume.                            | - Varies by tool and target system; depends on data volume.                          |
| **Scalability**               | - Most cloud tools are scalable, but complex with many sources/targets.                | - Leverages scalable processing power of data warehouse for large-scale transformations. |
| **Data Quality/Security**     | - Ensures quality by cleaning data first; can mask personal information.                | - Quality/security enhancements applied post-transfer; sub-pattern EtLT for limited transformations. |

### REST API
1. **API Mandate**: In 2002, Jeff Bezos mandated that all Amazon teams use APIs for data and functionality 
    exchange to enhance communication and efficiency.

2. **Stable Interfaces**: The introduction of APIs provided a consistent way for teams to share data and 
    services, regardless of their internal systems.

3. **Public-Facing APIs**: APIs were required to be built to eventually be accessible to external developers, 
    laying the groundwork for Amazon Web Services (AWS).

4. **Definition of API**: An API is a set of rules for programmatically exchanging data with applications, 
    allowing software development and integration.

5. **Common API Types**: REST APIs, which use HTTP methods, are the most common type of API for data communication.

6. **Usage in Data Engineering**: Data engineers use APIs to extract data from various sources by sending requests 
    and receiving responses in standardized formats.

7. **Practical Application**: Engaging directly with APIs through practical exercises is crucial for understanding 
    data ingestion from source systems.

## Streaming Ingestion
### Conversation with a Software Engineer
1. **Introduction**: The section presents a conversation with a software engineer to understand how real-time data ingestion 
    works for a product recommender system.
   
2. **Event Logging**: 
   - The website continuously records events in the web server logs.
   - Events include internal metrics, errors, anomalies, and user activity 
    (such as button clicks, product views, cart additions).

3. **User Activity Data**: 
   - The focus is on ingesting user activity data, not internal metrics.
   - The suggestion is to push user activity messages to a Kafka topic or Kinesis stream.

4. **Ingestion via Kinesis**: 
   - Kinesis Data Stream was chosen as the method for ingestion to fit other parts of the pipeline 
    already utilizing Kinesis.

5. **Data Payload and Message Rate**:
   - The messages are in JSON format and contain details like session IDs, customer location, 
    and product interactions.
   - Message size: typically a few hundred bytes.
   - Message rate: up to 1000 events per second at peak times (~10,000 users).

6. **Capacity Estimation**: 
   - Estimated message rate: ~1000 events per second.
   - Total data ingestion: less than 1MB per second.
   - Kinesis capacity should easily handle this load, as it supports hundreds of MB per second.

7. **Message Retention**:
   - Messages are retained in the stream for one day.
   - This allows the ability to back up and replay messages in case of system failures.
   - Retention size estimation: ~100 GB per day.

### Streaming Ingestion Details
1. **Streaming Systems Recap**:
   - Previously discussed how your data pipeline can be a consumer of streaming systems 
        like message queues or event streaming platforms.
   - These systems can have multiple producers, brokers, and consumers upstream of your ingestion system.

2. **Message Queues**:
   - Operate on a first-in, first-out (FIFO) basis.
   - The consumer reads and deletes messages from the queue once consumed.
   - Used for asynchronous message delivery between producer and consumer.

3. **Event Streaming Platforms**:
   - Store messages in an append-only log, allowing consumers to replay or reprocess messages.
   - Messages are routed to subscribers, and this log persists data for a configurable period.

4. **Amazon Kinesis and Apache Kafka**:
   - Lab uses **Amazon Kinesis**, while the example here explains **Apache Kafka**.
   - Both platforms function similarly by routing, storing, and processing event streams, though Kinesis 
        uses "streams" and "shards," whereas Kafka uses "topics" and "partitions."

5. **Kafka Event Flow**:
   - Event producers send messages to a **Kafka Cluster** containing multiple servers (brokers).
   - The cluster routes messages into **topics** (categories of events), which are divided into 
        **partitions** (logs of ordered messages).
   - Partitions enable scalability, allowing multiple consumers to process messages efficiently.

6. **Producer Role**:
   - Producers decide which partition to send messages to using methods like round-robin or message 
        key-based computation.
   - In Kinesis, producers write to **streams** and shards.

7. **Consumers and Consumer Groups**:
   - Consumers in a group work together to consume messages from all partitions of a topic.
   - Each partition is assigned to only one consumer in a group, ensuring distributed processing of messages.
   - Kafka allows **message retention**, letting consumers replay messages as needed.

8. **Kinesis vs. Kafka**:
   - Kinesis parallels Kafka's structure, with the same core concepts but different terminology 
        (streams vs. topics, shards vs. partitions).

9. **Real-World Example (Web Server Logs)**:
   - In the previous conversation with a software engineer, user actions were logged and pushed to a Kinesis Data Stream.
   - Similarly, the same messages could have been sent to a Kafka topic, allowing consumption by subscribing to that topic.

10. **Potential Data Ingestion Scenarios**:
    - Monitoring a web server log directly to treat it as an event producer.
    - Ingesting events into Kafka or Kinesis as a step in your pipeline.
    - **Continuous Change Data Capture (CDC)**: Monitoring database activity to stream updates and keep your pipeline 
        in sync with source databases.

### Kinesis Data Streams Details 

1. **Producers and Consumers**: 
   - Producers send data to Kinesis streams, and consumers read data from those streams.

2. **Shards**: 
   - A stream is composed of shards, each with its own read/write capacity.
   - Each shard supports up to 5 read operations/sec (2 MB/sec) and 1,000 write records/sec (1 MB/sec).

3. **Scaling**: 
   - Increase shards to handle higher data throughput.
   - Use **Provisioned Mode** (manual scaling) or **On-Demand Mode** (automatic scaling).

4. **Partition Key and Sequence Number**: 
   - Each data record includes a partition key to determine the shard.
   - Kinesis assigns a sequence number to maintain order within a shard.

5. **Fan-Out**: 
   - **Shared Fan-Out**: Multiple consumers share a shard’s read capacity.
   - **Enhanced Fan-Out**: Provides dedicated 2 MB/sec per consumer, avoiding contention.

6. **Data Processing**: 
   - Consumers can use AWS services like Lambda, Managed Service for Apache Flink, or 
        custom apps via the Kinesis Client Library (KCL).

7. **Stream Composition**: 
   - Streams can act as inputs for other streams, allowing complex data workflows.

8. **Integration**: 
   - Easily integrate with AWS services like Amazon S3 via Amazon Kinesis Data Firehose.

### Change Data Capture (CDC)   

Change Data Capture (CDC) is a method for extracting change events (insert, update, delete) 
from a database and making them available for downstream systems. It helps keep data in sync 
between source databases and storage systems.

#### Data Update Strategies
1. **Full Load**: 
   - Ingests the entire dataset from the source, replacing old data.
   - Suitable for low-frequency updates but resource-intensive for high-volume data.

2. **Incremental Load**: 
   - Loads only changes since the last update.
   - Utilizes a `last_updated_at` column to identify modified rows, making it faster but more complex to implement.

#### Use Cases for CDC
1. **Data Synchronization**: 
   - Synchronizes changes across databases, enabling continuous replication.
   - Useful for data warehouses to enable analytics on the latest data.

2. **Historical Change Capture**: 
   - Maintains a complete history of changes for regulatory and auditing purposes.

3. **Microservices Integration**: 
   - Allows microservices to react to database changes, enhancing communication between services.

#### Approaches to CDC
1. **Push**: 
   - Source database pushes changes to the target system in near real-time.
   - Risk of losing updates if target systems are unreachable.

2. **Pull**: 
   - Target systems poll the source database for changes, introducing potential lag.

#### CDC Implementation Patterns
1. **Batch-oriented (Query-based) CDC**: 
   - Queries the database to identify changes using timestamps.
   - Can cause computational overhead on the source database.

2. **Continuous (Log-based) CDC**: 
   - Monitors the database log for changes, allowing real-time capture without overhead.
   - Tools like Debezium can be used for implementation.

3. **Trigger-based CDC**: 
   - Uses database triggers to notify CDC of changes.
   - Can impact write performance if too many triggers are implemented.

### Summary: General Considerations for Choosing Ingestion Tools 

When selecting an ingestion tool for your data systems, consider both the characteristics 
of the data and the reliability and durability of the tool.

#### Characteristics of the Data

1. **Data Type & Structure**: 
   - Understand if the data is structured, unstructured, or semi-structured (e.g., PNG images) to 
    identify appropriate ingestion tools and transformations.

2. **Data Volume**:
   - **Existing Data Size**: For batch ingestion, assess the total historical data size. Limited 
        bandwidth may require splitting data into smaller chunks.
   - **Future Data Size**: Anticipate growth in data volume (daily, monthly, yearly) to configure 
        tools and estimate costs accordingly.

3. **Latency Requirements**:
   - Determine acceptable delays for stakeholders. Assess whether data needs to be ingested 
        in batches (e.g., daily, weekly) or in near real-time (e.g., milliseconds). The velocity of
        incoming data will influence the choice between batch and streaming ingestion tools.

4. **Data Quality**:
   - Evaluate the condition of source data. Determine if post-processing is necessary to address 
        incomplete, inconsistent, or erroneous data. Some tools provide features for data 
        quality checks and corrections.

5. **Changes in Schema**:
   - Schema changes (e.g., new columns, type changes) can occur frequently. Choose tools 
        that can automatically detect schema changes, but maintain communication with 
        stakeholders about these changes.

#### Reliability and Durability

1. **Reliability**:
   - Ensure that the ingestion system performs its intended function consistently.

2. **Durability**:
   - Protect against data loss or corruption. Design a reliable system to enhance data durability, 
        especially in streaming scenarios where data may not be retained indefinitely (e.g., IoT devices).
