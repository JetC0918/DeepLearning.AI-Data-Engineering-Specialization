## Data Engineering Lifecycle and Key Concepts

Week 1 provides a high-level overview of the data engineering lifecycle, the key undercurrents in the field, and how data engineers contribute to adding business value within organizations. The focus is on developing a mental framework for thinking like a data engineer, starting from gathering stakeholder needs and translating them into actionable system requirements. 

### Overview

The course covers foundational principles of data engineering, including the stages of the data engineering lifecycle and how to apply these in real-world scenarios. It also provides insights into working with cloud infrastructure, particularly using AWS, for building scalable data pipelines.

### Learning Objectives

- Identify key upstream and downstream collaborators and stakeholders for data engineers
- Identify the stages of the data engineering lifecycle and key undercurrents
- Articulate a mental framework for building data engineering solutions
- Identify some of the necessary considerations for requirements gathering at the start of a new project / role as data engineer 

### Outlines
1. [Introduction to Data Engineering](#introduction-to-data-engineering)
2. [Data Engineering on the Cloud](#data-engineering-on-the-cloud)

## Introduction to Data Engineering

* **Growing Demand for Data Engineers**: As industries become increasingly digital, the demand for data engineers to handle large volumes of data and build efficient data pipelines is skyrocketing

* **Importance of Data Engineering for Data Science**: Data engineers provide the infrastructure, data quality, and support needed for data scientists to be successful in their roles. Fast access to data enables rapid development and decision-making

* **Data-Centric AI**: The concept emphasizes the importance of systematically engineering data to build successful AI systems. With the rise of AI, focusing on the quality and structure of data is more critical than ever

### Course 1 Overview

- **Common Data Science Pitfalls**: Companies often hire data scientists without realizing they lack the necessary data infrastructure. This leads to inefficiencies and the need to hire data engineers, which is a growing trend in industry

- **Core Skills of Data Engineering**: The foundational skills for building data systems apply across various tasks such as data science, machine learning, and analytics. These skills form the essence of data engineering

- **Big Picture Focus**: Before jumping into implementation, it’s important to understand how your data systems will deliver value to the organization. The first course emphasizes forming a mental framework for successful data engineering

### Data Engineering Defined

- **Evolution of Data Engineering**: Initially, software engineers treated data as a byproduct (exhaust) of software applications. Over time, data became recognized for its intrinsic value, leading to the rise of data engineering as a key function for building systems to ingest, store, transform, and serve data.

- **Definition of Data Engineering**: According to [Fundamentals of Data Engineering](https://www.oreilly.com/library/view/fundamentals-of-data/9781098108298/), data engineering involves developing, implementing, and maintaining systems that convert raw data into high-quality, consistent information for downstream use cases such as analytics and machine learning.

- **Data Engineering Life Cycle**: The life cycle includes stages like data generation, ingestion, transformation, storage, and serving. Storage plays a role in every stage, and end-use cases include analytics, machine learning, and reverse ETL.

- **Data Pipeline**: The data pipeline is a collection of architectures, systems, and processes that move data from its generation to its end-use cases. As a data engineer, your job is to manage this pipeline.

- **Undercurrents of Data Engineering**: Six key elements—security, data management, DataOps, data architecture, orchestration, and software engineering—span the entire data engineering life cycle and impact each stage.

- **Holistic Approach**: It's important to understand the entire data engineering life cycle and its undercurrents, focusing on how to deliver value for the organization, rather than jumping straight into tool implementation. 

### The Data Engineer Among Other Stakeholders

1. **Role of Data Engineers**
   - Data engineers transform raw data into valuable insights and make it available for downstream use cases like analytics and machine learning.

2. **Understanding Downstream Needs**
   - **Downstream Users**: Include analysts, data scientists, machine learning engineers, salespeople, product or marketing professionals, and executives.
   - **Example**: For a business analyst needing SQL queries, understand their requirements for query frequency, data retrieval needs, and acceptable latency.

3. **Aligning with Downstream Stakeholders**
   - Discuss the frequency of data updates and necessary data details.
   - Ensure alignment on data definitions (e.g., time zones, start and end times).

4. **Understanding Upstream Stakeholders**
   - **Upstream Stakeholders**: Include software engineers or developers of source systems from which data is ingested.
   - **Communication**: Understand data volume, frequency, format, and potential disruptions (e.g., outages, schema changes).

5. **Building Relationships**
   - Develop relationships with both upstream and downstream stakeholders.
   - Influence how data is served to you and manage expectations regarding data flow and system changes.

6. **Business Value**
   - Understand the overall strategy and how data contributes to business goals.
   - Ensure the data you provide aligns with the needs and objectives of downstream stakeholders.

7. **Next Steps**
   - Before diving into requirements gathering, consider the concept of business value as it relates to your role.

### System Requirements

#### Understanding Stakeholder Needs
- **Goal:** Deliver value by understanding and translating stakeholder needs into system requirements.
- **Process:** Start with gathering requirements before writing code or setting up resources.

#### Types of Requirements
1. **Business Requirements**
   - Define high-level business goals (e.g., increasing revenue, growing the user base).

2. **Stakeholder Requirements**
   - Needs of individuals within the organization (e.g., tools needed to perform their jobs effectively).

3. **System Requirements**
   - **Functional Requirements (What):**
     - What the system needs to do (e.g., regular updates to databases, alerting for anomalies).
   - **Non-Functional Requirements (How):**
     - How the system will perform these functions (e.g., technical specs for data ingestion, orchestration, storage).

#### Requirements Gathering Process
1. **Start with Conversations**
   - Engage with stakeholders to understand their business goals and translate these into system requirements.

2. **Consider All Aspects**
   - Include high-level business and stakeholder requirements, data product features, technical specs, cost constraints, security, and regulatory considerations.

3. **Tailor the Approach**
   - Adapt your requirements gathering approach based on stakeholders' technical knowledge and organizational roles.
 
### Requirements Gathering Conversation 
#### Introduction
- **Data Engineer:** New to the team, looking to understand how to support the data scientist.
- **Data Scientist (Colleen):** Senior technical manager with experience in marketing technologies, data engineering, and analytics.

#### Current Challenges
- **Data Delivery:**
  - **Current Process:** Receiving daily data dumps in CSV and JSON formats.
  - **Problems:** 
    - **Manual Handling:** Data is cumbersome and requires manual extraction and cleaning.
    - **Inconsistencies:** Processing scripts frequently crash due to anomalies or format changes.
    - **Latency:** Data is typically two days old, impacting real-time analysis needs.

- **Data Processing:**
  - **Time Spent:** 80% of time cleaning and processing data.
  - **Issues:** 
    - **Unnecessary Data:** 90% of the data received is not needed.
    - **Format Changes:** Frequent changes in data format require script refactoring.

#### Data Scientist’s Needs
- **Real-Time Analysis:** Marketing team needs up-to-date metrics for product sales by region.
- **Use Cases:**
  - **Dashboards:** Current dashboards show sales trends and metrics but are delayed.
  - **Recommendation Engine:** Training a model for personalized product recommendations, but requires more data and a system to deploy the model.

#### Key Points from Conversation
- **Immediate Needs:**
  - **Data Ingestion:** Improve data ingestion to be more direct and timely.
  - **Automation:** Automate data transformation and orchestration to streamline processing.

- **Marketing Goals:**
  - **Current Data Use:** Targeting ad campaigns based on up-to-date metrics.
  - **Actionable Insights:** Need clarity on whether current means "real-time" or within a specific recent timeframe.

#### Next Steps
- **Follow-Up:** Check in with the marketing team to clarify their needs regarding data timeliness and actions based on current data.
- **Potential Solutions:** Focus on automating data ingestion and processing to reduce manual work and improve data availability.

#### Summary
- **Goal:** Enhance the efficiency of data processing and reduce latency to meet real-time analytics needs.
- **Outcome:** Streamlined data ingestion and automated processing will aid the data scientist in focusing more on analysis rather than data cleaning.

### Translate Stakeholder Needs into Specific Requirements 

#### 1. **Understand Existing Systems and Pain Points**
   - **Current Situation:** 
     - Marketing team needs real-time analysis of product sales.
     - Receiving daily data dumps from the software team.
   - **Challenges:**
     - Manual extraction and cleaning of data.
     - Schema changes and anomalies causing issues.
   - **Action:** 
     - Explore solutions for direct and timely data ingestion.
     - Communicate with source system owners to understand disruptions and changes.

#### 2. **Determine Actions Based on Data**
   - **Key Insight:**
     - Understand what actions stakeholders will take with the data.
   - **For Dashboards:**
     - Clarify what "real-time" means to the marketing team.
   - **For Recommender System:**
     - Data needs to be provided in near real-time (seconds or less).

#### 3. **Confirm Understanding**
   - **Action Steps:**
     - Repeat what you’ve learned back to the stakeholders to confirm accuracy.
     - Ensure you have a clear understanding of their needs and requirements.

#### 4. **Identify Additional Stakeholders**
   - **Additional Conversations:**
     - Talk to the marketing team for detailed use cases.
     - Engage with the software engineering team to improve data ingestion processes.

#### Summary
- **Key Takeaways:**
  - Identify existing systems and their issues.
  - Understand the actions stakeholders plan to take based on the data.
  - Confirm your understanding of requirements.
  - Identify and engage with additional stakeholders as needed. 

### Framework for Thinking Like a Data Engineer

#### 1. **Identify Business Goals and Stakeholder Needs**
   - **Business Goals:**
     - Understand the high-level objectives of the company.
   - **Stakeholder Identification:**
     - Determine who the stakeholders are and how their needs align with business goals.
   - **Current Systems:**
     - Learn about existing systems and their limitations.
   - **Stakeholder Conversations:**
     - Discuss what actions stakeholders plan to take with the data products.
     - Extract functional and non-functional requirements from these conversations.

#### 2. **Define Requirements**
   - **Functional Requirements:**
     - Describe what the system needs to do to meet stakeholder needs.
   - **Non-Functional Requirements:**
     - Specify how the system will perform its functions (e.g., technical specifications, latency).
   - **Documentation and Confirmation:**
     - Document the requirements.
     - Confirm with stakeholders that the documented system will meet their needs.

#### 3. **Choose Tools and Technologies**
   - **Tool Selection:**
     - Identify tools and technologies that can meet the system requirements.
   - **Cost-Benefit Analysis:**
     - Evaluate trade-offs including licensing fees, cloud resources, and other costs.
   - **Prototype Testing:**
     - Develop and test a prototype to ensure it meets expectations.
     - Iterate based on feedback to refine the prototype.

#### 4. **Build, Deploy, and Maintain the System**
   - **Build and Deploy:**
     - Develop and deploy the full data system based on the validated prototype.
   - **Continuous Monitoring:**
     - Monitor system performance.
   - **Iterative Improvement:**
     - Continuously update and improve the system based on evolving needs and emerging technologies.

#### **Ongoing Process**
   - **Cyclical Nature:**
     - The process is iterative and cyclical as business goals and stakeholder needs evolve.
   - **Communication and Adaptation:**
     - Continuously engage with stakeholders, reassess requirements, and update the system as necessary.
 
 ## Data Engineering on the Cloud 

- **Overview**: The specialization focuses on data engineering, starting with high-level concepts and progressing to practical applications.
  
- **Cloud vs. On-Premises**:
  - **Historical Context**: Data systems were once built and maintained in-house (on-premises). 
  - **Current Trend**: Many companies now prefer cloud-based systems due to flexibility and advanced tools.
  - **Future Focus**: The specialization will use a cloud-first approach, primarily focusing on AWS.

- **Specialization Details**:
  - **Cloud Tools**: The course will cover AWS tools and technologies used by companies worldwide.
  - **Lab Exercises**: You’ll build data pipelines and architectures on AWS.
  - **Learning Approach**: A "just-in-time" method, learning specific tools as needed, with no prior cloud computing knowledge required.

- **Preparation**:
  - **Familiarity with Cloud Basics**: Some background knowledge of cloud computing concepts and terminology will be helpful. 

 ### Introduction to AWS Cloud

- **Definition**: 
  - On-demand delivery of IT resources over the Internet with pay-as-you-go pricing.
  - Resources are provided instantly and you pay only for what you use.

- **Types of Resources**:
  - **Compute**: Virtual machines, container hosting services, serverless functions.
  - **Storage**: Amazon S3, Amazon Elastic Block Store (EBS), relational, NoSQL, and graph databases.
  - **Networking**: Amazon Virtual Private Cloud (VPC) for private networking.

- **Advantages**:
  - **Scalability and Elasticity**: Automatically adjusts capacity as needed; no need to predict and manage capacity.
  - **Cost Efficiency**: Pay for what you use, similar to electricity billing.

- **Infrastructure**:
  - **AWS Regions**: Geographic areas with multiple data centers (e.g., US East Northern Virginia, Asia Pacific Mumbai).
  - **Availability Zones (AZs)**: Data centers within a region, designed for high availability and fault tolerance.

- **Global Network**:
  - Data centers and AZs are connected via AWS’s global network of fiber cables for low latency and reliability.

- **Services**:
  - AWS offers over 200 services, including general-purpose and specific-use services.

### AWS Regions and Availability Zones

#### AWS Regions
- **Overview**: AWS has 33 regions globally, each containing a cluster of data centers.
- **Naming and Codes**:
  - Regions are named geographically (e.g., Northern Virginia) and have region codes (e.g., us-east-1).
  - Example: Northern Virginia Region is `us-east-1`, the first region in the eastern US.
- **Factors for Choosing a Region**:
  - **Latency**: Select a region close to your end users to reduce latency.
  - **Cost**: Costs may vary between regions.
  - **Compliance**: Regulations may require data to be hosted in specific regions.
  - **Service Availability**: Not all AWS services are available in every region.

#### Availability Zones (AZs)
- **Overview**: Each region has at least 3 isolated and physically separated availability zones.
- **Code Naming**:
  - AZs have codes combining the region code and a letter (e.g., `us-east-1a`).
- **Purpose**:
  - AZs are designed for high availability and fault tolerance.
  - They contain discrete data centers with redundant power, networking, and physical security.
  - AZs within a region are interconnected with high-speed, low-latency links.
- **High Availability**:
  - Hosting applications across multiple AZs ensures your work remains unaffected if one AZ experiences issues. 

### Intro to AWS Core Services 

#### 1. Compute
- **Amazon EC2 (Elastic Compute Cloud)**:
  - Provides virtual machines (VMs) on AWS.
  - Allows full control over the operating system, applications, and configurations.
  - Supports various use cases like web servers, containers, and development environments.
- **Other Compute Services**:
  - **AWS Lambda**: Serverless functions that run code in response to events.
  - **Amazon ECS**: Container hosting service.
  - **Amazon EKS**: Kubernetes container hosting service.

#### 2. Networking
- **Amazon Virtual Private Cloud (VPC)**:
  - Creates and controls private networks in the cloud.
  - Isolated from other AWS networks, with customizable IP space and subnets.
  - Spans all availability zones within a region but cannot span regions.

#### 3. Storage
- **Object Storage**:
  - Used for unstructured data like documents, logs, photos, and videos.
  - **Amazon S3 (Simple Storage Service)** is a primary service for object storage.
- **Block Storage**:
  - Suitable for database storage and virtual machine file systems.
  - **Amazon EBS (Elastic Block Store)** provides block storage volumes for EC2 instances.
- **File Storage**:
  - Organizes data into files and directories.
  - **Amazon EFS (Elastic File System)** offers scalable file storage that can be accessed by multiple systems.

#### 4. Databases
- **Amazon RDS (Relational Database Service)**:
  - Managed cloud-based relational database service.
- **Amazon Redshift**:
  - Data warehouse service for storing, transforming, and serving data.
- Other database services are also available, but RDS and Redshift are prominently featured in these courses.

#### 5. Security
- **Shared Responsibility Model**:
  - AWS is responsible for the security **of** the cloud (physical infrastructure, hypervisor).
  - You are responsible for the security **in** the cloud (guest operating system, software updates, networking, data encryption).

#### Additional Notes
- **AWS Global Infrastructure**:
  - Services are available in regions and availability zones.
  - Regions are geographical areas, and each contains multiple availability zones for high availability and fault tolerance.
 
### Amazon Elastic Compute Cloud (EC2) Overview

#### What is a Server?
- **Server**: A physical computer or a set of computers that hosts and runs applications.
  - **Components**: Physical hardware (CPU, RAM, storage), an operating system, and applications.

#### Virtual Servers vs. Regular Servers
- **Virtual Server**: A software-based emulation of a physical server.
  - **Components**: Virtual hardware, operating system, and applications.
  - **Virtualization**: Multiple virtual servers share the same physical hardware via a hypervisor.
  - **Hypervisor**: Software that manages and allocates physical resources to virtual servers.

#### Amazon EC2
- **Definition**: Virtual machines or servers provided by AWS for running applications.
- **Elasticity**: Ability to scale compute resources up or down based on needs.
- **Instance Types**: Varied by use case:
  - **General Purpose**
  - **Compute Optimized**
  - **Memory Optimized**
  - **Storage Optimized**
  - **Accelerated Computing**

#### Instance Naming Convention
- **Example**: t3a.micro
  - **t**: Family name
  - **3**: Generation
  - **a**: Optional capabilities
  - **micro**: Size

#### Purchasing Options
- **On-Demand Instances**: Flexible compute capacity without long-term commitments.
- **Spot Instances**: Discounted, unused compute resources with potential interruptions.

### Networking - Virtual Private Cloud (VPC) & Subnets

#### What is a Network?
- **Network**: A collection of connected devices that communicate via requests and responses.

#### What is an IP Address?
- **IP Address**: A unique identifier for each device on a network.
  - **IPv4**: Most common format; a 32-bit number in the format `x.x.x.x` (e.g., `192.101.0.2`).
  - **CIDR Notation**: Represents a range of IP addresses; e.g., `192.101.0.0/24` includes addresses from `192.101.0.0` to `192.101.0.255`.

#### What is a VPC (Virtual Private Cloud)?
- **VPC**: An isolated private network within an AWS region.
  - **Purpose**: Protects and organizes your resources (e.g., EC2 instances).
  - **Features**: 
    - **IP Range**: Defined by CIDR block.
    - **Isolation**: Resources within a VPC can communicate with each other but not with resources outside the VPC or the internet unless explicitly configured.

#### What is a Subnet?
- **Subnet**: A smaller network within a VPC.
  - **Purpose**: Provides control over resource access.
  - **Types**:
    - **Public Subnet**: Allows outside traffic to access resources.
    - **Private Subnet**: Does not allow outside traffic.
  - **CIDR Block**: Each subnet is assigned a subset of the VPC’s CIDR block.

#### Summary
- **VPC**: Think of it as a protected box within which you launch and manage your AWS resources.
- **Subnets**: Smaller divisions within a VPC to control traffic and resource access.

### Security - AWS Shared Responsibility Model

#### Overview
When using AWS, the responsibility for security is divided between AWS and you, the customer. This division is known as the **Shared Responsibility Model**.

#### AWS Responsibilities: Security of the Cloud
- **Physical Security**: AWS manages the security of physical facilities where hardware is housed.
- **Infrastructure Security**: AWS protects the global infrastructure, including the cables connecting regions and the hardware and software running AWS services.

#### Customer Responsibilities: Security in the Cloud
- **Data Protection**: You are responsible for securing your data at rest and in transit.
- **Access Management**: You must manage access controls, determining who can access your data and resources and for how long.
- **Service Configuration**: Depending on the AWS services used, additional configurations for security may be required.

#### Key Points
- **Data Ownership**: You own your data and must ensure its security.
- **Access Controls**: It's up to you to manage who can access and interact with your cloud resources.
- **Service Configurations**: Properly configure your services to ensure they meet your security needs.

#### Summary
- **AWS**: Secures the underlying physical infrastructure and global network.
- **Customer**: Secures the data and manages access within the cloud environment.
