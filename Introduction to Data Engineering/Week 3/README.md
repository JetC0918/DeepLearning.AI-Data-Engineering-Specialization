## Data Architecture

### Overview

Define data architecture and how it fits within the larger enterprise architecture. 
Examine the principles of good data architecture and how these principles inform tools 
and technology choices. Evaluate and optimize the security, performance, reliability, 
cost-efficiency, and scalability of a web application hosted on AWS.

### Learning Objectives
- Think critically about the components of an end-to-end data architecture that satisfies 
    requirements, but is also flexible for the future
- Evaluate technologies and tools against the context of requirements and good data architecture.

### Outlines
1. [Data Architecture](#data-architecture-1)
- 1.1 [What is Data Architecture](#what-is-data-architecture)
- 1.2 [Conway's Law](#conways-law)
- 1.3 [Principles of Good Data Architecture](#principles-of-good-data-architecture)
- 1.4 [Always Architecting](#always-architecting)
- 1.5 [When your Systems Fail](#when-your-systems-fail)
- 1.6 [Batch Architectures](#batch-architectures)
- 1.7 [Streaming Architectures](#streaming-architectures)
- 1.8 [Architecting for Compliance](#architecting-for-compliance)
2. [Choosing the Right Technique](#choosing-the-right-technique)
- 2.1 [Choosing Tools and Technologies](#choosing-tools-and-technologies)
- 2.2 [Location](#location)
- 2.3 [Monolith vs Modular Systems](#monolith-vs-modular-systems)
- 2.4 [Cost Optimization and Business Value](#cost-optimization-and-business-value)
- 2.5 [Build vs Buy](#build-vs-buy)
- 2.6 [Server, Container, and Serverless Compute Options](#server-container-and-serverless-compute-options)
- 2.7 [How the Undercurrent Impact Your Decision](#how-the-undercurrent-impact-your-decision)



## Data Architecture  
### What is Data Architecture

1. **Enterprise Architecture Definition**: 
   - The design of systems that support change in an organization through flexible 
        and reversible decisions by evaluating trade-offs.

2. **Data Architecture vs. Enterprise Architecture**:
   - Data architecture is a subset of enterprise architecture focused on the 
        evolving data needs of the organization.
   - Both involve making flexible, reversible decisions based on trade-offs to support change.

3. **Four Key Domains of Enterprise Architecture**:
   1. **Business Architecture**: Focuses on product/service strategy and business models.
   2. **Application Architecture**: Covers the structure and interaction of applications 
        to meet business needs.
   3. **Technical Architecture**: Deals with the software and hardware required 
        for business systems and applications.
   4. **Data Architecture**: Supports the evolving data requirements of the organization.

4. **Change Management**:
   - Organizations evolve, and so must their data architecture. Adapting to changes 
        is essential for success.

5. **One-Way and Two-Way Doors (Decision-Making)**:
   - **One-Way Door**: A decision that is difficult or impossible to reverse (e.g., selling AWS).
   - **Two-Way Door**: A reversible decision that allows flexibility (e.g., switching S3 storage classes).

6. **Flexible Architecture**:
   - Aim for two-way door decisions whenever possible to maintain flexibility in your data architecture.
   - If a one-way door decision seems necessary, break it down into smaller, reversible decisions.

7. **Architects' Role**:
   - Architects must actively solve business problems and create opportunities through technical solutions.
   - Good architecture directly supports business goals, rather than existing for its own sake.

8. **Conway's Law (Optional)**:
   - A phenomenon that can influence the systems you build by shaping the structure of your 
        architecture based on organizational communication.

### Conway's Law 

1. **Conway's Law Defined**:
   - Melvin Conway's Law states that "Any organization that designs a system will produce a design 
        whose structure is a copy of the organization's communication structure."

2. **Practical Example**:
   - If departments (e.g., sales, marketing, finance, operations) work in silos, their communication 
        will be isolated, leading to siloed, disconnected data systems.
   - Conversely, if departments collaborate and communicate cross-functionally, their data systems 
        will reflect this integration and cooperation.

3. **Key Takeaway**:
   - As a data engineer, understanding your organization's communication structure is critical 
        for designing effective data architecture.
   - Building systems that align with how your company communicates will lead to better success. 
        Attempting to design systems that clash with this structure can lead to failure.

4. **Impact on Data Architecture**:
   - Organizational communication patterns directly influence the architecture and design of the systems built.
   - Systems will mirror the level of collaboration and integration present in the company.

5. **Additional Learning**:
   - A link to further resources on Conway's Law will be provided in the course for those 
        interested in exploring the concept further.

### Principles of Good Data Architecture 

1. **Choose Common Components Wisely**:
   - Selecting common components (e.g., object storage, version control, monitoring systems) 
        that can be used broadly across your organization fosters collaboration.
   - Cloud platforms are particularly effective at facilitating shared data access, allowing 
        different teams to query the same data for varied use cases.
   - The goal is to strike a balance: adopt shared tools where appropriate but avoid a 
        one-size-fits-all approach that could hinder productivity.

2. **Architecture is Leadership**:
   - A key role for data architects and data engineers is identifying and implementing 
        common components that unify teams and improve collaboration.
   - Leadership also involves mentoring others and ensuring proper training for the 
        selected components, helping the organization use them effectively.
   - As you gain experience, mentoring or consulting with data architects can help you 
        grow into an architecture role, guiding the organization’s technology decisions. 

### Always Architecting

1. **One-Way and Two-Way Doors**: 
   - One-way doors represent decisions that are difficult or impossible to reverse.
   - Two-way doors are reversible decisions, allowing for flexible and 
        continuous architectural improvements.

2. **Amazon's API Mandate**: 
   - In 2002, Jeff Bezos mandated all teams at Amazon to use service interfaces 
        (APIs) to communicate, ensuring stable, predictable interactions.
   - APIs allowed teams to function as loosely coupled systems, enabling independence 
        and adaptability without affecting others.

3. **Build Loosely Coupled Systems**: 
   - Loosely coupled components can be swapped out without redesigning the entire system.
   - This structure allows for flexibility and adaptability as your architecture evolves.

4. **Always Be Architecting**: 
   - Data architecture must continuously evolve with changing business and technology needs.
   - As a data engineer, you must plan for future adaptability in your systems.

### When your Systems Fail

1. **Plan for Failure**:
   - Systems will fail, so it's crucial to plan for failure modes.
   - Consider metrics like **availability** (uptime), **reliability** 
        (performance within a time interval), and **durability** (data resilience to loss).
   - Define **Recovery Time Objective (RTO)** – the maximum acceptable outage time, 
        and **Recovery Point Objective (RPO)** – the acceptable data loss after recovery.

2. **Prioritize Security**:
   - Security breaches are a significant failure mode.
   - Move from **hardened perimeter security** (trusted inside, untrusted outside) to 
        **zero trust security** (no default trust; every action requires authentication).
   - Limit access strictly by necessity, even internally.

3. **Architect for Scalability**:
   - Design your system to scale up quickly to meet demand without crashing.
   - Be prepared for unexpected spikes in traffic or usage by utilizing scalable cloud infrastructures.

4. **Embrace FinOps**:
   - Cloud services are pay-as-you-go, making cost management dynamic.
   - Balance cost and performance through efficient resource use (e.g., on-demand vs. spot instances).
   - Avoid unforeseen expenses, such as running expensive services unintentionally, 
        by managing budgets and priorities effectively.

### Batch Architectures

1. **Batch Processing Overview**:
   - Batch architectures involve **ingesting, transforming, and storing data** in chunks over 
        fixed time periods (e.g., daily).
   - Ideal for scenarios where **real-time data processing** isn't critical, like 
        analyzing e-commerce sales history once a day.
  
2. **ETL and ELT Patterns**:
   - **ETL (Extract, Transform, Load)**: Data is transformed before loading into a data warehouse.
   - **ELT (Extract, Load, Transform)**: Data is loaded into the warehouse first and transformations 
        happen there, popular due to cloud warehouses' computational power.

3. **Data Marts**:
   - A **data mart** is a refined subset of a data warehouse designed for a specific department 
        (e.g., sales, marketing).
   - It improves access for analysts and may include additional transformations for **performance optimization**.

4. **Architectural Considerations**:
   - **Common components**: Facilitate collaboration across teams using shared pipelines and data warehouses.
   - **Planning for failure**: Prepare for source system outages or data schema changes by 
        collaborating with system owners.
   - **Flexibility**: Build the system to handle future changes in data volume or ingestion frequency.

5. **Cost and Performance Trade-offs (FinOps)**:
   - Perform a **cost-benefit analysis** for the different components of your architecture.
   - Balance **performance** against costs while focusing on delivering value to the business.


### Streaming Architectures

1. **Streaming Data Pipelines**:

   - In streaming architectures, data is ingested and processed **continuously in near real-time**.
   - A typical streaming system consists of a **producer**, a **consumer**, and a **streaming broker** 
        coordinating data between them.

2. **Popular Streaming Technologies**:
   - Platforms like **Kafka**, **Apache Storm**, and **Samza** enabled new real-time data analytics 
        and modeling (e.g., user aggregation, recommendations) in the early 2010s.

3. **Lambda Architecture**:
   - Combines **batch and streaming** systems that operate independently but provide a **combined view** 
        by aggregating results.
   - Though influential, it has challenges like managing parallel systems with different codebases.

4. **Kappa Architecture**:
   - Proposed as an alternative to Lambda, it uses a **stream processing platform** (like Kafka) 
        as the backbone for all data handling.
   - Allows real-time event processing while also supporting **batch-like processing** by retaining 
        and replaying historical data.

5. **Modern Approaches**:
   - **Apache Beam** and the **Dataflow model** unify batch and streaming data processing by 
        treating all data as **event streams**, with real-time data being unbounded 
        and batches as bounded streams.
   - Tools like **Apache Flink** implement this philosophy, treating batch processing 
        as a **special case of streaming**.

6. **Key Considerations**:
   - Engineers today focus on **flexibility, scalability**, and handling **failure modes** 
        while unifying batch and streaming pipelines.
   - **Compliance** is crucial, ensuring systems adhere to regulations, privacy agreements, 
        and terms of service policies.

### Architecting for Compliance

1. **Importance of Compliance**: Regulatory compliance is crucial for data engineers, 
        as failing to adhere to laws can lead to lawsuits and significant fines.

2. **Key Regulations**: The General Data Protection Regulation (GDPR) is a major regulation focused 
        on privacy and personal data protection, requiring consent and the ability to delete data 
        upon request.

3. **Global Applicability**: Compliance with regulations like GDPR applies not only to EU-based companies 
        but also to organizations in other countries, as many have adopted similar laws.

4. **Future-Proofing Systems**: Data engineers should build flexible and loosely coupled systems 
        that comply with current regulations and can adapt to future changes.

5. **Industry-Specific Regulations**: Different industries have specific regulations, such as 
        HIPAA for healthcare data and the Sarbanes-Oxley Act for financial data, which must be considered.

6. **Value Delivery**: By ensuring compliance, data engineers can help organizations avoid 
        legal issues and enhance their value.

## Choosing the Right Technique 
### Choosing Tools and Technologies

1. **Designing Good Data Architecture**: Focus on creating flexible, loosely coupled systems that can 
        adapt to the evolving data needs of your organization.

2. **Choosing the Right Tools**: Consider various options for tools and technologies for ingestion, storage, 
        transformation, and serving, including open source, managed services, and proprietary solutions.

3. **End Goals Matter**: Keep in mind the ultimate objective of delivering high-quality data products 
        that meet user requirements, which informs your choice of technologies.

4. **Avoiding Common Pitfalls**: Be aware of potential missteps in tool selection and implementation, 
        ensuring your decisions align with business needs.

5. **Location Trade-offs**: Evaluate the benefits and drawbacks of building systems on-premises, 
        in the cloud, or using a hybrid approach.

6. **Cost Optimization**: Assess whether to build custom tools or purchase off-the-shelf solutions 
        based on your team's capabilities and business value drivers.

7. **Future Needs**: Plan for current requirements while considering potential future demands to 
        ensure longevity and adaptability in your architecture. 

### Location
1. **Historical Context**: For the past two decades, on-premises data systems were the primary option 
        for data storage and processing, as modern cloud platforms were not yet available.

2. **On-Premises Systems**: Companies that build on-premises systems own and maintain all hardware and 
        software, taking on full operational responsibility for updates, scaling, and maintenance.

3. **Cloud Data Systems**: Today, many companies opt for cloud data systems, where providers like AWS 
        handle hardware and infrastructure, allowing companies to rent compute and storage resources.

4. **Benefits of Cloud**: Cloud computing offers significant advantages, including easy scalability to 
        meet demand, reduced maintenance burdens, and flexibility in choosing tools and technologies.

5. **Industry Trends**: The trend is clearly shifting toward cloud solutions, with more companies either 
        adopting cloud systems or migrating from on-premises to cloud environments.

6. **Hybrid Systems**: Some companies may still maintain on-premises systems due to business needs, 
        regulations, or security concerns, but the momentum favors cloud adoption. 


### Monolith vs Modular Systems
1. **Monolithic Architecture**: Monolithic systems are self-contained with tightly coupled components. 
        They offer simplicity by having all functionality in one place, making them easy to understand and manage.

2. **Challenges of Monoliths**: As monolithic systems grow, they become harder to maintain. Updating 
        one component often requires changes to others, and in some cases, the entire application may need to 
        be rewritten. This can lead to significant downtime and suboptimal performance.

3. **Modular Architecture**: In contrast, modular systems consist of loosely coupled components. 
        They break the application into self-contained areas of concern, promoting flexibility and easier 
        maintenance.

4. **Rise of Microservices**: The modular approach aligns with the microservices architecture, 
        where each service is deployed as a separate unit, allowing for independent updates and deployments.

5. **Interoperability in Data Engineering**: Modern data processing technologies support interoperability, 
        meaning tools can easily integrate with each other. For example, data stored in a standard format like 
        Parquet can be processed by any compatible tool.

6. **Flexibility and Continuous Improvement**: The modular model allows for the easy swapping of tools and 
        technologies as needed, fostering flexibility, reversible decisions, and continuous improvement 
        in data architecture.  

### Cost Optimization and Business Value

1. **Cost Considerations in Data Engineering**: Data engineers must consider multiple costs 
        beyond just software pricing, including implementation costs, maintenance costs, and 
        opportunity costs associated with technology choices.

2. **Total Cost of Ownership (TCO)**: TCO encompasses all direct and indirect costs over 
        a project’s lifecycle, including hardware/software acquisition, management, maintenance, 
        training, and costs from downtime or lost productivity.

3. **Direct vs. Indirect Costs**: Direct costs are easily identifiable and linked to project 
        development (e.g., salaries, cloud service fees). Indirect costs, or overhead, include 
        expenses not directly attributed to the development, like IT support or productivity loss.

4. **Capital Expenses (CapEx) vs. Operational Expenses (OpEx)**: CapEx refers to large, upfront investments 
        for fixed assets, common in on-premises systems. OpEx covers ongoing operational costs, often 
        associated with cloud systems that offer pay-as-you-go models.

5. **Total Opportunity Cost of Ownership (TOCO)**: TOCO represents the lost opportunities when 
        choosing one technology over others. This cost can be difficult to quantify but is crucial 
        as technology choices evolve.

6. **Flexibility in Technology Choices**: To minimize TCO and TOCO, build flexible and loosely coupled 
        systems that can be easily updated. Identify immutable technologies (e.g., object storage, SQL) 
        versus transitory technologies (e.g., stream processing) to inform decisions.

7. **FinOps Concept**: FinOps focuses on minimizing TCO and TOCO while maximizing revenue opportunities, 
        advocating for cloud services that support an OpEx-first approach and modular options for quick 
        iteration and growth. 

### Build vs Buy
1. **Cloud Services Preference**: Generally, using cloud services like Amazon S3 for object storage is 
        recommended over building custom solutions, as it provides better scalability and reduces 
        maintenance overhead.

2. **Custom Solutions Consideration**: While many teams opt for open-source frameworks for customization, 
        building from scratch should only be considered if there are no existing solutions available, 
        as this can lead to unnecessary complexity and effort.

3. **Avoiding Undifferentiated Heavy Lifting**: The term "undifferentiated heavy lifting" refers to the
        hard work of developing custom solutions that do not add unique value to the organization, 
        akin to reinventing the wheel.

4. **Options Overview**: Data engineers can choose from fully open-source tools, managed open-source services, 
        and proprietary software. Each option comes with its own advantages and challenges.

5. **Team Capabilities**: Consider your team's bandwidth and expertise when choosing an open-source solution. 
        Smaller teams might benefit more from managed services to avoid being bogged down in maintenance.

6. **Total Cost of Ownership (TCO)**: Building or maintaining an open-source solution may seem cost-effective 
        at first due to the absence of licensing fees, but TCO includes many factors, such as the costs of 
        implementation and maintenance.

7. **Value Assessment**: Evaluate whether building or using an open-source solution provides real advantages 
        over managed services, or if it simply constitutes additional work without added value.

8. **Recommended Approach**: Start with open-source or commercial open-source solutions, and if those 
        don’t meet your needs, consider proprietary options. This strategy allows teams to focus on high-value tasks.

9. **Next Steps**: The next lesson will explore the differences between serverless and traditional 
        server-based options for tools and technologies. 

### Server, Container, and Serverless Compute Options
1. **Server Basics**: A server is a computer or collection of computers that provides the necessary resources 
        (CPU, RAM, disk storage, etc.) to host software applications over a network, typically via the Internet.

2. **Three Computing Options**: When using cloud tools, you often choose between three options for running 
        applications: **server**, **container**, and **serverless**.

3. **Server Option**: With a server-based solution, you must manage the server setup, including operating 
        system updates, software installations, networking, scaling, and security.

4. **Container Option**: Containers package your code and dependencies into a lightweight unit that runs on 
        a server, requiring you to manage the application’s essentials without handling the underlying operating system.

5. **Serverless Concept**: The term "serverless" means you don't manage the servers yourself. It abstracts 
        server management, allowing you to focus on application development while the provider handles scaling and dependencies.

6. **Serverless Advantages**: Serverless technologies typically run on containers and offer automatic scaling, 
        built-in availability, fault tolerance, and a pay-as-you-go billing model, which can lead to cost savings.

7. **When to Use Serverless**: Serverless options are best for simple, discrete tasks. However, they can become 
        costly in high-frequency environments, so understanding cloud pricing is crucial.

8. **Monitoring Costs**: It's essential to monitor usage metrics such as event rates and duration to accurately 
        predict costs for serverless services compared to traditional server options.

9. **Execution Limits**: Serverless platforms have constraints on execution limits, concurrency, and duration. 
        If your application exceeds these limits, consider a container-based approach with orchestration 
        tools like Kubernetes.

10. **Recommendation**: Start with serverless options for most modern data engineering applications. 
        Move to containers and orchestration as your needs grow beyond what serverless can support.  

### How the Undercurrent Impact Your Decision
1. **Security**: Choose tools with strong security features. Ensure they are developed by reputable 
        organizations and trusted open-source communities. Verify the code of open-source tools to 
        understand their implementation.

2. **Data Management**: Inquire about data governance practices of tools. Understand how they 
        protect data against breaches, comply with regulations like GDPR, and ensure data quality verification.

3. **Data Ops**: Select tools that offer automation and monitoring features. For managed services,
        review the service level agreement (SLA) for reliability and availability guarantees.

4. **Data Architecture**: Prioritize tools that provide modularity and interoperability, 
        allowing for flexibility and loose coupling between components.

5. **Orchestration**: Consider orchestration tools like Apache Airflow, Prefect, Dagster, and Mage. 
        Stay informed about the evolving landscape to find the best fit for your architecture goals.

6. **Software Engineering**: Assess your team's capabilities and determine whether to build, 
        use open-source, or choose proprietary solutions. Avoid undifferentiated heavy lifting—focus 
        on tasks that add value to your organization.
