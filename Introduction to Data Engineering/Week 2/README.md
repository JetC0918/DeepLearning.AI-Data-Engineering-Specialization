## Data Engineering Lifecycle and Undercurrents 
### Overview

Dive deeper into the stages of the data engineering lifecycle and its key undercurrents. 
Build an end-to-end data pipeline on AWS that encompasses all the stages of the data engineering lifecycle.

### Learning Objectives

- Describe the structure of the data engineering lifecycle and its undercurrents, 
  and how to think about data engineering problems through this lens.
- Identify some of the key technologies in the AWS data engineering stack 
  that can be employed in different stages of the data engineering lifecycle.

### Outlines
1. [The Data Engineering Lifecycle](#data-generation-in-source-systems)
- 1.1 [Stage 1 - Data Generation & Source Systems](#data-generation-in-source-systems)
- 1.2 [Stage 2 - Data Ingestion](#ingestion)
- 1.3 [Stage 3 - Data Storage](#storage)
- 1.4 [Stage 4 - Data Transformation](#queries-modeling-and-transformation)
- 1.5 [Stage 5 - Serving Data](#serving-data)
2. [The Undercurrent of the Data Engineering Lifecycle](#the-undercurrent-of-the-data-engineering-lifecycle)
- 2.1 [Security](#security)
- 2.2 [Data Management](#data-management)
- 2.3 [Data Architecture](#data-architecture)
- 2.4 [DataOps](#dataops)
- 2.5 [Orchestration](#orchestration)
- 2.6 [Software Engineering](#software-engineering)
3. [Practical Examples on AWS](#pratical-example-on-aws)
- 3.1 [The Data Engineering Lifecycle on AWS](#the-data-engineering-lifecycle-on-aws)
- 3.2 [The Undercurrents on AWS](#the-undercurrents-on-aws)


## Data Generation in Source Systems 
 
1. **Consuming Data from Various Sources**: 
   - Data engineers work with different types of source systems that generate data, 
     often outside their control.
   - Common source systems include:
     - **Databases**: Relational (tables) and NoSQL (key-value, document stores, etc.).
     - **Files**: Text, audio, video files.
     - **APIs**: Allows web requests for data (e.g., JSON, XML).
     - **Data Sharing Platforms**: Facilitate internal/external data sharing.
     - **IoT Devices**: Devices generating real-time streaming data, often requiring aggregation.

2. **Unpredictability of Source Systems**: 
   - Source systems are subject to changes that can disrupt data pipelines:
     - Schema or format changes.
     - Data quality or availability issues.
     - System downtime.

3. **Importance of Relationships with Source System Owners**: 
   - Collaborating with the owners of source systems helps:
     - Understand how the systems work.
     - Anticipate potential changes in data or structure.
     - Minimize disruptions to downstream workflows.

#### Real-World Example:
- **Challenges with Unannounced Changes**: 
   - A software engineering team changed the columns in 
     an internal database without notifying the data engineer. 
     This caused significant disruption to downstream workflows, 
     highlighting the importance of proactive communication.
 
### Ingestion 
  
1. **Ingestion**:
   - Ingestion involves moving raw data from source systems 
     into the data pipeline for further processing.
   - Key bottleneck in data engineering due to variability in source systems.

2. **Frequency of Data Ingestion**:
   - **Batch Ingestion**:
     - Data is moved in large chunks on a time schedule 
       (e.g., hourly, daily) or when data reaches a threshold.
     - Suited for use cases like analytics and machine learning 
       (e.g., model training, reports).
   - **Streaming Ingestion**:
     - Data is ingested continuously and made available to downstream systems 
       in near real-time (e.g., less than one second delay).
     - Requires tools like event streaming platforms or message queues.

3. **Batch vs. Streaming**:
   - **Batch**: 
     - Practical for most use cases; simpler and cost-effective.
     - Ideal for scheduled tasks or large data analysis.
   - **Streaming**: 
     - Enables real-time use cases like anomaly detection.
     - More complex, higher costs, and often used alongside batch processing.
   
4. **Key Considerations for Streaming**:
   - Real-time improvements over batch data.
   - Costs of time, money, and maintenance.
   - Impact on the rest of the data pipeline.

5. **Batch & Streaming Coexistence**:
   - Streaming often works alongside batch processing.
   - E.g., machine learning models trained in batch, 
     but real-time data ingested via streaming for anomaly detection.

6. **Other Ingestion Nuances**:
   - **Change Data Capture (CDC)**: Trigger processes based on changes in source data.
   - **Push vs. Pull**: Decide whether source systems push data to you or if you pull data from them.
 
### Storage  

1. **Daily Interaction with Storage**:
   - You interact with various storage systems, like hard drives, 
     solid-state drives (SSDs), RAM, cloud storage, etc.
   - Performance and limitations depend on the storage solution setup.

2. **Raw Hardware Ingredients of Storage**:
   - **Magnetic Disk Storage**: Still widely used due to low cost.
   - **Solid State Drives (SSD)**: Faster than disks but more expensive (2-3x cost).
   - **RAM (Memory)**: Fastest but also volatile and the most expensive (30-50x SSD cost).

3. **Storage in Modern Architectures**:
   - Data moves between magnetic storage, SSDs, and RAM during different stages.
   - Distributed storage across multiple clusters/data centers; involves networking, 
     CPU, compression, and caching.

4. **Types of Storage Systems**:
   - **Database Management Systems (DBMS)**: Structured data storage.
   - **Object Storage Platforms**: E.g., Amazon S3 for unstructured data.
   - **Additional Systems**: Apache Iceberg, Hudi, in-memory caching, streaming storage.

5. **Storage Abstractions**:
   - High-level systems like **data warehouses**, **data lakes**, and **data lakehouses** 
     abstract away the complexity of raw storage.
   - Focus on system configuration for latency, scalability, and cost rather than low-level storage details.

6. **Storage Hierarchy**:
   - **Bottom Layer**: Raw storage ingredients (disks, RAM, SSDs, networking, etc.).
   - **Middle Layer**: Storage systems built from these raw ingredients (databases, object storage, etc.).
   - **Top Layer**: Storage abstractions (data warehouse, data lake, lakehouse).

7. **Importance of Understanding Storage Details**:
   - Effective data engineers understand the limitations, performance, and costs of storage systems.
   - Missteps, like inefficient data ingestion methods, can lead to high costs and wasted time.
   - Example: A team used row inserts for large datasets, which was slow and expensive, instead of bulk ingestion. 
 
### Queries, Modeling, and Transformation
 
1. **Adding Value through Transformation**:
   - **Purpose**: Convert raw data into a format that provides value 
                  to downstream stakeholders.
   - **Use Cases**: Business analysts need data in a query-friendly format; 
                    data scientists need transformed data for model training.

2. **Components of Data Transformation**:
   - **Queries**: Requesting and retrieving data from storage systems. 
     - **Languages**: SQL is commonly used.
     - **Potential Issues**: Poorly written queries can impact performance and cause issues like row explosion. 
     - **Learning**: Details on SQL and query performance will be covered in later courses.

   - **Data Modeling**: Structuring data to represent real-world relationships and meet business needs.
     - **Normalization**: Organizing data to reduce redundancy.
     - **Denormalization**: Combining data for efficient querying (e.g., integrating product info with sales data).
     - **Business Context**: Understanding stakeholders' terminology and requirements is crucial.

   - **Data Transformation**: Manipulating and enhancing data for downstream use.
     - **Pre-Ingestion**: Adding timestamps or basic transformations before data is ingested.
     - **In-Flight**: Applying transformations during data ingestion (e.g., mapping types, standardizing formats).
     - **Post-Ingestion**: Further transformations for reporting, aggregation, or machine learning 
        (e.g., schema changes, feature engineering).

3. **Learning Path**:
   - **Hands-On Exercises**: Expect practical work involving querying, modeling, and transforming data.
   - **Upcoming Focus**: The next stage is **serving data** for downstream use cases.

### Serving Data

Serving data is about more than just making data available—it's about enabling stakeholders to extract actionable business value. 
Different stakeholders have varying needs, which impacts how data should be served. 
Here’s an overview of common end use cases for data:

#### 1. **Analytics**:
   - **Purpose**: Identify insights and patterns within data.
   - **Forms of Analytics**:
     - **Business Intelligence (BI)**: Analyze historical and current data to make strategic decisions.
       - **Use Case**: Analysts use reports and dashboards for trend analysis, such as monitoring sales or campaign performance.
     - **Operational Analytics**: Monitor real-time data for immediate action.
       - **Use Case**: E-commerce teams track real-time performance metrics to quickly address issues like website outages.
     - **Embedded Analytics**: Provide data insights directly within applications for end users.
       - **Use Case**: Banks offering dashboards for personal spending trends; smart thermostats showing historical temperature data.

#### 2. **Machine Learning**:
   - **Purpose**: Support machine learning models with data.
   - **Components**:
     - **Feature Stores**: Provide structured data for model training.
     - **Real-Time Inference**: Serve data for immediate predictions.
     - **Metadata and Cataloging**: Track data history and lineage.
   - **Considerations**: Machine learning often involves additional complexities that will be detailed in later courses.

#### 3. **Reverse ETL**:
   - **Purpose**: Feed transformed data or model outputs back into source systems.
   - **Use Case**: Example includes taking transformed CRM data and enriching it with lead scoring model results, 
                    then pushing this enhanced data back into the CRM.

#### Summary of Data Engineering Lifecycle Phases:
1. **Source Systems**: Understanding data sources and their characteristics.
2. **Ingestion**: Moving raw data from sources into your data pipeline.
3. **Transformation**: Querying, modeling, and transforming data into valuable formats.
4. **Storage**: Managing how data is stored and accessed.
5. **Serving**: Providing data to stakeholders for analytics, machine learning, or other purposes. 

## The Undercurrent of the Data Engineering Lifecycle 

1. **Data Engineering Lifecycle**
   - **Ingestion**: Extracting data from source systems.
   - **Transformation**: Converting raw data into useful formats.
   - **Storage**: Saving data for future use.
   - **Serving**: Making data available for end-users.

2. **Evolution of Data Engineering**
   - The field has evolved from focusing solely on technology to encompassing broader practices.
   - Modern data engineering now integrates traditional and new practices, moving up the value chain.

3. **Undercurrents of Data Engineering**
   - **Security**: Protecting data with encryption, access controls, and compliance measures.
   - **Data Management**: Organizing and maintaining data quality and lifecycle.
   - **DataOps**: Applying DevOps principles to improve collaboration, automation, and monitoring.
   - **Data Architecture**: Designing scalable and integrated data systems.
   - **Orchestration**: Coordinating workflows, scheduling tasks, and handling errors.
   - **Software Engineering**: Ensuring code quality, testing, and version control.

### Security 

1. **Personal Data Security Analogies**
   - Just as you protect personal data (e.g., bank account info, passwords) 
        and physical assets (e.g., house keys), you must protect sensitive data in your role.

2. **Principle of Least Privilege**
   - **Definition**: Grant users and applications only the access necessary to perform their tasks, 
        and only for the time needed.
   - **Self-Application**: Avoid using administrator or superuser permissions unless absolutely necessary.

3. **Data Sensitivity and Access**
   - **Visibility**: Show sensitive data only when absolutely necessary.
   - **Prevention**: Avoid ingesting and storing sensitive data unless there's a clear purpose.

4. **Cloud Security Considerations**
   - Understand **Identity and Access Management (IAM)**, 
        **encryption methods**, and **networking protocols**.
   - Security is not only about principles but also about understanding 
        and applying these practices in a Cloud-centric environment.

5. **Defensive Mindset**
   - Be cautious with credentials and sensitive data.
   - Anticipate potential attack scenarios and design data pipelines with these risks in mind.

6. **Human Factor in Security**
   - Many breaches result from human error, such as sharing passwords 
        insecurely or falling victim to phishing attacks.
   - Ensure basic precautions and security practices are followed.

7. **Common Pitfalls**
   - Avoid exposing AWS S3 buckets, servers, or databases to the public internet unintentionally.
   - Apply security best practices diligently to prevent these issues.

8. **Security Culture**
   - True security emerges from a culture where protecting data is a priority 
        and everyone in the organization embraces security practices.
   - **Security Theater**: Beware of organizations with only superficial security 
        compliance rather than a genuine culture of security.
 
### Data Management

1. **Value of Data Management**
   - Proper data management is crucial for maximizing the value of data as a business asset.
   - DAMA (Data Management Association International) provides resources like the 
        Data Management Book of Knowledge (DMBOK) to guide effective data management.

2. **Data Management Definition**
   - **DMBOK Definition**: Data management involves the development, execution, 
        and supervision of plans, programs, and practices to deliver, control, protect, 
        and enhance the value of data and information assets throughout their life cycles.

3. **Key Data Management Areas**
   - **Facets and Disciplines**: Includes data governance, data modeling, data integration, 
        metadata, security, and more.
   - **Data Governance**: Oversees quality, integrity, security, and usability of data. 
        It touches all other areas of data management and interacts with them through governance practices.

4. **Focus on Data Quality**
   - **High Quality Data**: Accurate, complete, discoverable, timely, and adheres to 
        well-defined schemas and data definitions.
   - **Low Quality Data**: Inaccurate, incomplete, or unusable data can lead to 
        poor decision-making and wasted resources.

5. **Data Quality Importance**
   - High quality data supports effective decision-making and adds value to the organization.
   - Monitoring and ensuring data quality is essential for maintaining the usefulness and reliability of data.

### Data Architecture 

1. **Definition of Data Architecture**
   - Data architecture is the design of systems to support evolving data needs, 
        achieved through flexible and reversible decisions and careful evaluation of trade-offs.

2. **Principles of Good Data Architecture**

   1. **Choose Common Components Wisely**
      - Select components that are useful for multiple teams and projects while facilitating collaboration.

   2. **Plan for Failure**
      - Design architectures to handle both expected functionality and potential failures.

   3. **Architect for Scalability**
      - Build systems that can scale up with demand and scale down to optimize costs.

   4. **Architecture is Leadership**
      - While this principle may not directly apply, thinking like an architect 
        and seeking mentorship will help you lead and mentor others effectively.

   5. **Always Be Architecting**
      - Continuously evaluate and update your architecture to meet evolving organizational needs.

   6. **Build Loosely Coupled Systems**
      - Design systems with interchangeable components to make reversible decisions and adapt to changing requirements.

   7. **Prioritize Security**
      - Centralize security in your design, incorporating principles like least privilege and zero trust.

   8. **Embrace FinOps**
      - Integrate financial and operational priorities to optimize for cost and revenue generation in the Cloud.

3. **Flexibility in Modern Data Architectures**
   - Modern Cloud-based systems allow more flexibility and reversibility 
        in technology choices compared to traditional on-premises systems.
 
### DataOps 

1. **Origins and Purpose**
   - **DevOps Emergence**: In 2007, DevOps emerged to bridge the gap between software development 
        and deployment teams, borrowing from lean and agile methodologies to 
        enhance release cycles and software quality.
   - **DataOps Adoption**: DataOps, inspired by DevOps, aims to improve the development 
        and quality of data products. It focuses on similar cultural practices 
        and technical elements to optimize data workflows.

2. **Cultural Practices of DataOps**
   - **Communication and Collaboration**: Prioritize effective communication with business stakeholders.
   - **Continuous Learning**: Learn from both successes and failures.
   - **Rapid Iteration**: Implement iterative improvements in processes and systems.

3. **Technical Pillars of DataOps**
   - **Automation**
     - **Continuous Integration/Continuous Delivery (CI/CD)**: Automate data processing tasks 
        similar to CI/CD in software development.
     - **Manual vs. Automated Pipelines**: Transition from manual task execution 
        to automated scheduling and orchestration frameworks (e.g., Airflow).
   - **Observability and Monitoring**
     - **Importance**: Essential for detecting failures in data pipelines before stakeholders notice issues.
     - **Goal**: Prevent prolonged issues and maintain stakeholder trust.
   - **Incident Response**
     - **Approach**: Utilize monitoring data to quickly identify and resolve incidents.
     - **Communication**: Foster open and blameless coordination among team members.

4. **Practical Examples**
   - **Manual Execution**: Starting tasks manually can be inefficient and error-prone.
   - **Scheduling**: Automate task initiation based on time schedules.
   - **Orchestration Frameworks**: Use tools like Airflow for automated task management, 
        dependency checking, and error notifications. 

### Orchestration 

1. **Definition**: Orchestration in data engineering is akin to conducting an orchestra; 
    it involves coordinating and managing tasks within data pipelines to ensure smooth operation.

2. **Manual Execution**: Initially, data pipelines may be set up with manual execution of tasks. 
    This approach is suitable for prototyping but is not sustainable for long-term data processing.

3. **Scheduling vs. Orchestration**:
  - **Pure Scheduling**: Tasks are run automatically at predefined times or frequencies. 
        It may lead to issues if tasks fail or do not complete as expected.
  - **Orchestration Frameworks**: Modern frameworks automate and manage dependencies and 
        monitoring, enhancing reliability.

4. **Popular Orchestration Frameworks**:
  - **Apache Airflow**
  - **Dagster**
  - **Prefect**
  - **Mage**

5. **Directed Acyclic Graph (DAG)**:
  - **Definition**: A DAG represents the flow of data through a 
        pipeline with nodes (tasks) and edges (dependencies).
  - **Characteristics**: Data flows in one direction without loops.

6. **Features of Orchestration Frameworks**:
  - **Automation**: Automate task execution and manage dependencies.
  - **Event Triggers**: Start tasks based on specific events, like the availability of new data.
  - **Monitoring and Alerts**: Set up alerts for task failures and completion statuses.

7. **Role in Data Engineering**: Orchestration is a crucial component spanning 
        the entire data engineering lifecycle and DataOps practices.

### Software Engineering

1. **Importance of Coding**: As a data engineer, you must write 
        production-grade code that is clean, readable, testable, and deployable.

2. **Software Engineering**:
   - **Definition**: Involves designing, developing, deploying, 
        and maintaining software applications.
   - **Evolution**: Data engineering evolved from software engineering 
        roles that previously included data handling.

3. **Code Quality**:
   - **Core Skills**: Proficiency needed in SQL, Spark, Kafka, Python, 
        JVM languages (Java, Scala), and Bash.
   - **Flexibility**: Strong software engineering fundamentals make it easier 
        to work with various programming languages.

4. **Modern Data Engineering**:
   - **Managed Services**: Reduced need for direct coding due to 
        available managed services and applications.
   - **Open Source**: Opportunities to contribute to open source frameworks 
        and infrastructure as code solutions.

5. **Everyday Coding**:
   - **Routine**: Coding is a regular part of problem-solving throughout the 
        data engineering lifecycle.
   - **Collaboration**: Enhancing coding skills through interaction with 
        software engineers in your organization. 

## Pratical Example on AWS
1. **Cloud Providers**:
   - **AWS**: Leading cloud provider, with courses focusing on AWS tools and technologies.
   - **Others**: Microsoft Azure, Google Cloud Platform, 
        and smaller providers also offer relevant tools and concepts.

2. **Relevance Across Platforms**:
   - **Concepts**: The data engineering concepts are applicable across different cloud platforms, 
        though tools and implementation details may vary.

### The Data Engineering Lifecycle on AWS

1. **Source Systems on AWS**:
   - **Amazon RDS**: Provides managed relational databases (e.g., MySQL, PostgreSQL). 
        Simplifies operational tasks like patching and upgrading.
   - **Amazon DynamoDB**: Serverless NoSQL database with flexible schema, 
        suitable for low-latency access and evolving data models.
   - **Amazon Kinesis Data Streams**: Used for streaming real-time data.  
   - **Amazon SQS & Apache Kafka**: Used for message handling and streaming.
        Kafka can be run using Amazon MSK.

2. **Ingestion Tools**:
   - **AWS Glue ETL**: Main tool for data integration in the labs.
   - **Amazon Kinesis Data Firehose**: Used for streaming data ingestion in labs.
   - **Database Migration Service (DMS)**: Automates data migration and replication, useful outside the labs.

3. **Cloud Storage**:
   - **Amazon Redshift**: Data warehouse solution for structured data.
   - **Amazon S3**: Object storage for a data lake. Supports lakehouse architectures 
        combining structured and unstructured data.

4. **Transformation Tools**:
   - **AWS Glue**: ETL service used in labs.
   - **Apache Spark & DBT**: Tools for data transformation, either used with Glue or as alternatives.

5. **Serving Data**:
   - **Analytics**: Use Amazon Athena or Redshift for querying. Dashboard tools like Jupyter Notebook, 
        Amazon QuickSight, Apache Superset, and Metabase can also be used.
   - **AI & Machine Learning**: Batch data for model training and vector databases 
        for product recommenders and large language models. 

### The Undercurrents on AWS
1. **Security on AWS**:
   - **Shared Responsibility Model**: AWS secures the infrastructure; you secure your systems and data. 
        For instance, while AWS secures S3, you must manage access permissions.
   - **Identity and Access Management (IAM)**: Manages access permissions to AWS resources. 
        Use IAM roles for temporary credentials and appropriate API permissions.
   - **Network Security**: Utilize Amazon VPC and security groups (instance-level firewalls) 
        for securing data pipelines.

2. **Data Management on AWS**:
   - **AWS Glue Crawlers & Data Catalogs**: Discover, create, and manage metadata 
        for data in S3 or other storage systems.
   - **Lake Formation**: Manages and scales fine-grain data access permissions, 
        related to data privacy and discovery.

3. **Data Ops on AWS**:
   - **Amazon CloudWatch**: Monitors metrics and provides monitoring for resources and applications.
   - **Amazon CloudWatch Logs**: Stores and analyzes operational logs.
   - **Amazon SNS**: Sets up notifications triggered by system events.
   - **Open Source Tools**: Monte Carlo, Bigeye for observability.

4. **Orchestration on AWS**:
   - **Airflow**: An orchestration tool available as open source or managed service. 
        Alternatives include Dagster, Prefect, and Mage.

5. **Architecture on AWS**:
   - **AWS Well-Architected Framework**: Principles for building systems focusing on 
        operational efficiency, security, scalability, and sustainability.

6. **Software Engineering on AWS**:
   - **Amazon Cloud9**: IDE hosted on EC2 for development.
   - **CodeDeploy & CICD Tools**: Automate code deployment.
   - **Version Control**: Git and GitHub for version control.


