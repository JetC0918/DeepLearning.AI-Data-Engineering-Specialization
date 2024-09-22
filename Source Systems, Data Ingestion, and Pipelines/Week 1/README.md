## Working with Source Systems
Lesson 1 introduces various source systems that are commonly used in data engineering, 
including databases, object storage, and streaming platforms. The focus is on understanding
these systems and how they function within data pipelines. Lesson 2 covers the process of 
establishing connections to these source systems, addressing common connectivity challenges, 
and offering solutions for troubleshooting.

### Learning Objectives:

1. **Identify Data Formats**: Learn about different data formats (structured, unstructured, etc.) 
        and determine the appropriate source systems for generating each type of data.
2. **Relational vs. NoSQL Databases**: Understand the key differences between relational databases 
        (SQL) and NoSQL databases, and when to use each.
3. **ACID Compliance**: Explore the principles of ACID (Atomicity, Consistency, Isolation, Durability) 
        and how they apply to database transactions.
4. **CRUD Operations**: Practice performing basic CRUD (Create, Read, Update, Delete) operations on 
        both relational and NoSQL databases.
5. **Object Storage**: Interact with object storage systems (such as AWS S3) and understand their usage 
        for unstructured data.
6. **Message Queues vs. Streaming Platforms**: Explain the difference between message queues (e.g., RabbitMQ) 
        and streaming platforms (e.g., Kafka) and their use cases.
7. **Cloud Networking Basics**: Gain a foundational understanding of cloud networking, including VPCs, subnets, 
        and security groups.
8. **Troubleshooting**: Learn how to troubleshoot common database connection errors when connecting to source systems.

### Outlines
1. [Introduction to Source Systems](#introduction-to-source-systems)
- 1.1 [Different Types of Source Systems](#different-types-of-source-systems)
- 1.2 [Relational Databases](#relational-databases)
- 1.3 [Lab 1 - Interacting With a Relational Database Using SQL](./Lab%201%20-%20Interacting%20With%20a%20Relational%20Database%20Using%20SQL/)
- 1.4 [NoSQL](#nosql)
- 1.5 [Database ACID Compliance](#database-acid-compliance) 
- 1.6 [Lab 2 - Interacting with Amazon DynamoDB NoSQL Database](./Lab%202%20-%20Interacting%20with%20Amazon%20DynamoDB%20NoSQL%20Database/)
- 1.7 [Object Storage](#object-storage)
- 1.8 [Lab 3 - Interacting With Amazon S3 Object Storage](./Lab%203%20-%20Interacting%20With%20Amazon%20S3%20Object%20Storage/)
- 1.9 [Logs](#logs)
- 1.10 [Streaming Systems](#streaming-systems)
2. [Connecting to Source Systems](#connecting-to-source-systems)
- 2.1 [Connecting to Source Systems in Data Engineering](#connecting-to-source-systems-in-data-engineering)
- 2.2 [Basics of IAM and Permissions]()
- 2.3 [Basics of Networking in the Cloud]()
- 2.4 [AWS Networking Overview - VPCs & Subnets]()
- 2.5 [AWS Networking - Internet Gateway & NAT Gateway]()
- 2.6 [AWS Networking - Route Tables]()
- 2.7 [AWS Networking - Network ACLs & Security Groups]()

## Introduction to Source Systems
### Different Types of Source Systems

#### Types of Data
1. **Structured Data**: Organized in tables of rows and columns 
        (e.g., relational databases, spreadsheets).
2. **Semi-Structured Data**: Not in tabular form but still has some structure (e.g., JSON, XML).
3. **Unstructured Data**: No predefined structure (e.g., text, video, audio, images).

#### Source Systems
1. **Databases**:
   - Store information in an organized manner for retrieval and manipulation.
   - CRUD operations: Create, Read, Update, Delete.
   - Types: 
     - **Relational Databases**: Use tables with rows and columns.
     - **NoSQL Databases**: Store non-tabular data.

2. **Files**:
   - Universal medium for data exchange; can be structured (spreadsheets), semi-structured (JSON, XML), 
        or unstructured (text, images).
   - Commonly accessed from file systems (Google Drive) or object storage (Amazon S3).

3. **Streaming Systems**:
   - Provide continuous data flow as messages about events (e.g., IoT device readings).
   - Examples include message queues and streaming platforms like Kinesis and Kafka.
   - Useful for real-time data processing and analytics. 

### Relational Databases 

#### Overview
1. **Prevalence**: Relational databases are widely used in web/mobile applications, corporate systems, 
        and OLTP (Online Transaction Processing) systems.
2. **Structure**: Data is organized across multiple related tables to minimize redundancy and manage 
        information efficiently.

#### Key Concepts
1. **Normalization**: 
   - Separates information into multiple tables (e.g., customers, products, orders) to avoid data duplication.
   - Changes (e.g., customer address) need to be updated in only one row, maintaining data integrity.

2. **Database Schema**:
   - Defines the organization of data within the database.
   - Uses **primary keys** (unique identifiers for rows) and **foreign keys** 
        (references to primary keys in related tables).

3. **CRUD Operations**: 
   - Fundamental operations for database management: Create, Read, Update, Delete.

#### Database Management
1. **RDBMS**: 
   - Relational Database Management Systems like MySQL, PostgreSQL, Oracle, and SQL Server 
        facilitate interaction with relational databases.
   - Support **SQL** (Structured Query Language) for database operations.

#### Considerations
1. **Performance vs. Integrity**: 
   - Normalized databases ensure data integrity but may be slower for queries.
   - Depending on use cases, some data engineers may use a **One Big Table (OBT)** approach for faster processing.

### NoSQL
1. **NoSQL Overview**: NoSQL databases emerged in the early 2000s as tech giants like Google and 
        Amazon needed to process large volumes of diverse data beyond the capabilities of relational databases. 

2. **Flexibility and Scalability**: NoSQL databases offer schema flexibility, horizontal scaling, 
        and prioritize speed over strong consistency, making them suitable for applications where 
        availability is critical, such as social media.

3. **Types of NoSQL Databases**: Key-value databases store data as key-value pairs for fast lookup, 
        while document databases store data in JSON-like documents, allowing for flexible schemas but 
        lacking support for joins.

4. **Eventual Consistency**: NoSQL databases operate under eventual consistency, allowing reads from 
        nodes that may not have the latest updates, contrasting with the strong consistency of relational databases.

5. **Data Integrity**: Not all NoSQL databases guarantee ACID compliance, meaning additional steps may be 
        needed to ensure data integrity when sourcing from them.

### Database ACID Compliance
1. **ACID Principles**: ACID stands for Atomicity, Consistency, Isolation, and Durability, ensuring 
        reliable and accurate transaction processing in online transaction processing (OLTP) systems, such as banking.

2. **Atomicity**: Ensures that a transaction is treated as a single unit. Either all operations in a transaction 
        are executed, or none are. For example, if a customer experiences a network error while placing an order, 
        the entire transaction will roll back.

3. **Consistency**: Changes within a transaction must adhere to the rules of the database schema, ensuring the 
        database transitions from one valid state to another. For instance, preventing stock levels from 
        going below zero during a sale.

4. **Isolation**: Guarantees that concurrent transactions operate independently, ensuring accurate results. 
        For example, if two customers order items at the same time, each transaction is processed sequentially 
        to reflect accurate inventory levels.

5. **Durability**: Once a transaction is completed, its effects are permanent and will survive system failures, 
        maintaining the reliability of the database during unexpected events.

6. **Strong Consistency**: In distributed systems, strong consistency ensures that all nodes provide the same 
        up-to-date data, critical for maintaining a consistent view of the database across servers.

7. **NoSQL Compliance**: Many NoSQL databases are not ACID compliant by default, but some can be configured to 
        meet these principles. Understanding the need for ACID compliance is crucial for data integrity and 
        preventing issues in applications.

### Object Storage
1. **Object Storage Overview**: Object storage treats data as individual objects in a flat structure, 
        differing from traditional file systems that use hierarchical organization. While interfaces 
        may display folders, the actual storage is flat, allowing for quick access to all objects.

2. **Versatile Data Types**: Objects in storage can include various formats such as CSV, JSON, text, video, images, 
        and binary data. This makes object storage ideal for semi-structured and unstructured data, supporting 
        applications like machine learning.

3. **Object Identifiers and Metadata**: Each object is assigned a Universal Unique Identifier (UUID) for management 
        and access. Objects come with metadata, detailing additional information such as creation date, file type, and owner.

4. **Immutability and Versioning**: Objects are immutable after initial writing, meaning they cannot be updated or appended. 
        To modify data, the full object must be rewritten under the same UUID. Object versioning allows retaining 
        multiple versions of an object instead of overwriting it.

5. **Benefits of Object Storage**: Object storage simplifies data management by eliminating complex folder structures. 
        It offers virtually limitless scalability, high durability (e.g., Amazon S3's 11 nines of data durability), 
        and is often more cost-effective for infrequently accessed data.

6. **Applications**: It is widely used in modern architectures like data lakes and data lake houses, providing flexibility, 
        scalability, and durability for various data types.
    
### Logs
1. **Definition of Logs**: Logs are append-only records of events that track the activity of a system or application, 
        often considered "application exhaust."

2. **Purpose and Uses**: Logs are primarily used for monitoring system health, triggering alerts, and debugging issues, 
        but they also serve as valuable data sources for analysis, machine learning, and automation.

3. **Structure of Log Data**: Each log entry typically includes a user/system identifier (e.g., user ID, IP address), 
        details of the event and its metadata, and a timestamp. Logs can be in various formats such as unstructured 
        text, JSON, or CSV.

4. **Log Levels**: Logs often include a tag that categorizes each event by its severity, with levels such as debug, 
        info, warn, error, and fatal, indicating the nature of the

### Streaming Systems
1. **Definition of Streaming Data**: Streaming data consists of events, which are occurrences or changes in state, 
        messages that contain information about those events, and streams that are sequences of messages over time.

2. **Components of Streaming Systems**: There are three main components: 
   - **Event Producer**: Generates messages (e.g., IoT devices, APIs).
   - **Event Consumer**: Processes messages (e.g., services reacting to events).
   - **Event Router (Streaming Broker)**: Routes messages from producers to consumers, allowing asynchronous communication.

3. **Types of Streaming Systems**: 
   - **Message Queues**: Accumulate messages in a FIFO order. Consumers read and acknowledge messages, which are then 
        deleted. Example: Amazon SQS.
   - **Streaming Platforms**: Store messages in a persistent log without deletion. Consumers read messages sequentially, 
        allowing for replaying events. Examples: Apache Kafka, Amazon Kinesis.

4. **Event-Driven Architecture**: This architecture enables decoupled communication between producers and consumers, 
        which helps manage message flow and ensures that events are not lost even if consumers are temporarily unavailable.

5. **Use Cases**: Streaming systems are vital for data ingestion, transformation, and serving in data engineering workflows, 
        allowing for real-time data processing and analysis.

## Connecting to Source Systems
1. **Common Issues in Data Engineering**: Data engineers often face unforeseen issues when connecting to source systems, 
        such as improper identity and access management (IAM), broken networking configurations, or incorrect access credentials. 
        These problems can significantly hinder data access.

2. **Importance of Troubleshooting Skills**: Solving connectivity issues is a crucial skill for data engineers. During interviews, 
        candidates are often tested on their ability to troubleshoot broken configurations to assess their preparedness for 
        real-world scenarios.

3. **Connecting to Source Systems**: The lesson will cover how to connect to different source systems, with a demonstration in AWS, 
        though the principles apply to other cloud platforms as well.

4. **IAM Roles and Permissions**: IAM is essential for managing access to cloud-based data sources and components in data pipelines. 
        Understanding IAM roles and permissions is key to ensuring security in the cloud.

5. **Networking Overview**: A high-level overview of networking concepts will be provided, followed by detailed coverage of 
        AWS networking elements such as VPCs, subnets, gateways, routing, and security groups. 

### Connecting to Source Systems in Data Engineering

1. **Establishing Connections**: Before ingesting data, it's essential to establish a connection to the data source and verify 
        authorization to read from it. Experience from previous labs includes using boto3 to connect to DynamoDB and Amazon RDS.

2. **Connection Information**: For resources in your AWS account, connection information (like endpoint and port) can be found 
        in the AWS management console. This can vary in appearance due to AWS updates, but the steps to locate the information 
        remain similar.

3. **Console Limitations**: While the AWS console is convenient for quick tasks, it is not repeatable or easily traceable. 
        Future changes to the console layout may complicate repeated tasks.

4. **Command Line Interface (CLI)**: Using the CLI allows data engineers to find connection information and connect to databases 
        using commands specific to the Database Management System (DBMS). This method is more manual and better suited for 
        simple workloads.

5. **SDKs and APIs**: For greater repeatability and automation, data engineers can use SDKs like boto3 in an IDE (e.g., Cloud9) 
        or Jupyter notebooks. API connectors like JDBC or ODBC can also facilitate database connections for querying.

6. **Further Learning**: Additional reading materials will provide more details on connection methods. The next video will 
        cover identity and access management and permissions.

### Basics of IAM and Permissions 

1. **Importance of IAM**: Identity and Access Management (IAM) is crucial for data engineers as it secures sensitive data 
        and helps prevent data breaches caused by human error.

2. **Principle of Least Privilege**: IAM allows you to grant users and applications access only to the resources they need, 
        minimizing risk and controlling costs.

3. **IAM Components**: Key IAM components include:
   - **Root User**: The account creator with unrestricted access.
   - **IAM Users**: Individuals with specific permissions.
   - **IAM Groups**: Collections of users assigned a policy for easier management.
   - **IAM Roles**: Temporary permissions for users or applications.

4. **Policies**: IAM policies are JSON documents defining permissions and actions for users or groups on AWS resources.

5. **Common Issues**: Data engineers often face access denied errors due to expired temporary role credentials, 
        emphasizing the need for understanding IAM configurations.

6. **Best Practices**: Following IAM best practices can help prevent costly data breaches and secure your company’s reputation.

### Basics of Networking in the Cloud  
1. **Network Configuration**: Building a data pipeline in the cloud involves configuring a network of 
        connected resources to ensure proper data flow.

2. **Cloud Infrastructure**: Cloud computing consists of physical data centers in regions, each with availability 
        zones that enhance redundancy and reliability.

3. **Choosing Regions**: When hosting resources, consider legal compliance, latency, availability, and cost variations 
        between regions.

4. **Virtual Private Clouds (VPCs)**: Create custom VPCs within regions to control access to resources. Each VPC can span 
        multiple availability zones.

5. **Subnets**: Divide VPC space into subnets (public and private) with specific security rules. Public subnets allow 
        Internet-facing resources, while private subnets protect internal resources.

6. **Security and Access Control**: Use network access control lists (ACLs) and security groups to manage traffic and protect resources.

7. **Complexity of Networking**: Connecting to databases and orchestrating data pipelines requires understanding multiple 
        layers of network configurations and IAM permissions.

 
### AWS Networking Overview - VPCs & Subnets
1. **Networking Overview**: As a data engineer, understanding cloud networking is essential for building effective 
        data pipelines. Key concepts include VPCs, subnets, gateways, and security groups.

2. **Creating a VPC**: Start by creating a custom VPC in AWS rather than using the default VPC, which is not recommended 
        for real-world applications. Define the VPC's name and private IP address range (CIDR block).

3. **Understanding CIDR Notation**: CIDR (Classless Inter-Domain Routing) specifies the IP address range for the VPC. 
        For example, `10.0.0.0/16` indicates that the first two octets are fixed for network identification, 
        allowing for host addresses in the last two octets.

4. **Subnets Creation**: Create subnets within the VPC, designating them as public or private based on their intended use. 
        Ensure subnets have CIDR ranges that are subsets of the VPC's IP range.

5. **Redundancy and Availability**: Deploy resources across multiple availability zones (AZs) for redundancy. 
        For instance, create two public and two private subnets across different AZs to enhance fault tolerance.

6. **Internet Connectivity**: After creating subnets, additional resources like Internet and NAT gateways will be 
        required to enable Internet access for the resources within the VPC.

### AWS Networking - Internet Gateway & NAT Gateway
1. **Internet Connectivity**: To enable Internet connectivity for a VPC with public and private subnets, 
        attach an Internet gateway. This allows resources in public subnets to communicate with the Internet.

2. **NAT Gateway Purpose**: Use NAT gateways to allow EC2 instances in private subnets to access the Internet 
        for updates while preventing external access to those instances.

3. **Application Load Balancer (ALB)**: The ALB serves as the entry point for external traffic, distributing 
        requests to EC2 instances in private subnets without exposing them directly to the Internet.

4. **Creating an Internet Gateway**: In the AWS Management Console, create an Internet gateway, name it, and 
        attach it to your VPC to establish outbound and inbound traffic flow.

5. **Setting Up NAT Gateways**: Create NAT gateways in each public subnet to provide private subnets with 
        Internet access for outgoing connections while keeping them secure from incoming Internet traffic. 

### AWS Networking - Route Tables
1. **Route Tables Function**: Direct network traffic within a VPC; each subnet can be associated with a 
        route table containing rules.

2. **Default Route Table**: Automatically created for each VPC; allows internal communication but lacks 
        Internet connectivity routes.

3. **Public Subnets**: Create a route table directing Internet-bound traffic (0.0.0.0/0) to the Internet 
        gateway for external access.

4. **Private Subnets**: Create a route table directing Internet-bound traffic (0.0.0.0/0) to the NAT gateway 
        for secure outbound connections.

5. **Creating Route Tables**: Use the AWS Management Console to create and associate route tables for 
        each subnet, adding necessary routes.

### AWS Networking - Network ACLs & Security Groups
