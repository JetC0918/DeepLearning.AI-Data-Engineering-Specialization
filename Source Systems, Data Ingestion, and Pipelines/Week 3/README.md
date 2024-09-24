## Dataops
In the first lesson, you will explore DataOps automation practices, including 
applying CI/CD to both data and code, and using infrastructure as code tools like 
Terraform to automate the provisioning and management of your resources. 
Then in lesson 2, you will explore DataOps observability and monitoring practices, 
including using tools like Great Expectation to monitor data quality, and using 
Amazon CloudWatch to monitor your infrastructure.

### Learning Objectives
- Explain how the DevOps automation concepts such as Continuous Integration 
    Continuous Delivery (CI/CD) are applied within DataOps
- Define Infrastructure as Code and how it relates to the automation pillar of DataOps
- Use Terraform to provision AWS resources
- Differentiate between DevOps observability and DataOps observability
- Apply data quality tests using Great Expectations
- Identify and monitor relevant data quality metrics

### Outlines
1. [DataOps - Automation]()
- 1.1 [Introduction to DataOps](#introduction-to-dataops)
- 1.2 [Interview with Chris Berg: Understanding DataOps](#interview-with-chris-berg-understanding-dataops)
- 1.3 [DataOps Automation](#dataops-automation)
- 1.4 [Infrastructure as Code](#infrastructure-as-code)
- 1.5 [Terraform - Creating an EC2 Instance](#terraform---creating-an-ec2-instance)
- 1.6 [Terraform - Defining Variables and Outputs](#terraform---defining-variables-and-outputs)
- 1.7 [Terraform - Defining Data Sources and Modules](#terraform---defining-data-sources-and-modules)
- 1.8 [Lab 1 - Implementing DataOps with Terraform](./Lab%201%20-%20Implementing%20DataOps%20with%20Terraform/)

2. [DataOps - Observability](#dataops---observability)
- 2.1 [Data Observability](#data-observability)
- 2.2 [Conversation with Barr Moses](#conversation-with-barr-moses)
- 2.3 [Key Takeaways From the Conversation with Barr Moses](#key-takeaways-from-the-conversation-with-barr-moses)
- 2.4 [Monitoring Data Quality](#monitoring-data-quality)
- 2.5 [Conversation with Abe Gong](#conversation-with-abe-gong)
- 2.6 [Great Expectations - Core Components](#great-expectations---core-components)
- 2.7 [Great Expectations - Workflow Example](#great-expectations---workflow-example)
- 2.8 [Lab 2 - Testing Data Quality with Great Expectations](./Lab%202%20-%20Testing%20Data%20Quality%20with%20Great%20Expectations/)
- 2.9 [Conversation with Chad Sanderson](#conversation-with-chad-sanderson)
- 2.10 [Amazon CloudWatch](#amazon-cloudwatch)
- 2.11 [Lab 3 -  Implementing Monitoring with Amazon CloudWatch](./Lab%203%20-%20%20Implementing%20Monitoring%20with%20Amazon%20CloudWatch/)

## Dataops - Automation S
### Introduction to DataOps
1. **Focus of the Week**: 
   - This week emphasizes **DataOps**, specifically the three pillars: 
    **automation**, **observability and monitoring**, and **incident response**.
   - DataOps evolves from **DevOps** and applies the same practices to data systems, 
    ensuring high-quality data products.

2. **Three Pillars of DataOps**:
   - **Automation**: Efficient deployment and integration of data infrastructure 
    using CI/CD and Infrastructure as Code (IaC).
   - **Observability and Monitoring**: Tracking data quality and metrics to 
    ensure system health.
   - **Incident Response**: While not heavily focused on this week, it involves 
    managing and responding to data pipeline issues.

#### Key Topics for the Week
1. **Automation**:
   - Revisiting **Continuous Integration and Continuous Delivery (CI/CD)**.
   - Deep dive into **Infrastructure as Code (IaC)** using tools like 
    **Terraform** and **CloudFormation**.
   - Hands-on experience with **Terraform** to deploy infrastructure 
    resources for data pipelines.

2. **Observability and Monitoring**:
   - Importance of tracking **data quality** and key **observability metrics**.
   - Monitoring your infrastructure after deployment to ensure reliable and accurate data flow.

3. **Incident Response**:
   - Understanding the cultural aspects of DataOps that help teams effectively 
    respond to incidents, even though there are fewer practical exercises on this topic.

#### Industry Insights
- **Interviews with Industry Experts**:
   - Insights on **data quality** and **observability** from professionals 
    building tools for data engineers.
   - Features an interview with **Chris Berg**, co-author of the 
    **DataOps Manifesto** and CEO of **DataKitchen**.

#### Hands-On Learning
- **Lab Exercises**:
   - First lab: Write code using **Terraform** to deploy infrastructure for your data pipeline.
   - Follow-up labs: Implement monitoring and observability features for your pipeline. 

### Interview with Chris Berg: Understanding DataOps

**Chris Berg** is the co-author of the DataOps Manifesto and CEO of DataKitchen. 
In this interview, Chris shares his experiences in the data field and provides insights into 
DataOps—what it is, why it’s important, and how to apply its principles. 

#### 1. Chris Berg’s Journey:
- Transitioned from software engineering to managing data teams in 2005.
- Struggled with delivering high-quality data products quickly while dealing with technical 
    and operational challenges.
- Realized the problem wasn’t the team’s skill but the **management of data systems**.

#### 2. What is DataOps?
- DataOps is a **methodology** aimed at enabling teams to deliver data insights 
    **quickly** and with **high quality**.
- It’s about creating a data factory that produces reliable data products quickly 
    while allowing **rapid changes** to the pipeline when necessary.
- Inspired by **Lean manufacturing principles**, DataOps focuses on 
    **improving efficiency**, **reducing errors**, and **delivering value** faster.

#### 3. Challenges in Data Engineering:
- Data engineering is a tough career due to high demands from stakeholders 
    and messy data infrastructures.
- Many data engineers feel stressed and overwhelmed due to the pressure to 
    deliver quickly and fix issues in real-time, leading to burnout.

#### 4. Automation and Testing:
- A key part of DataOps is building automated systems that support your code, 
    such as **testing**, **monitoring**, and **observability**.
- These systems ensure that as data changes, problems can be detected and 
    resolved **before** they become serious issues.
- Automated tests are a "gift to your future self," allowing teams to avoid 
    rework and reduce the need for constant intervention.

#### 5. Lessons for New Data Engineers:
- Avoid the "hero mentality" of trying to fix everything yourself—focus 
    on **building systems** that prevent problems.
- Incorporate practices like **continuous testing** and **monitoring** 
    to keep your data pipeline robust and reliable.
- Deliver insights iteratively. Instead of spending months on a project, 
    deliver small parts of the solution quickly and **iterate** based on feedback.

#### 6. Differences Between DataOps and DevOps:
- While similar, DataOps focuses on **data workflows** while DevOps 
    focuses on **software**.
- Both emphasize **short cycle times**, **automation**, and **error reduction**, 
    but DataOps deals with the additional complexity of **data quality** and **governance**.
- The goal in both methodologies is to **deliver value faster** with **high quality** and **low risk**.

### DataOps Automation 

1. **CI/CD (Continuous Integration and Continuous Delivery):**
   - In software engineering, CI/CD automates the review, testing, and deployment of new code.
   - In **DataOps**, CI/CD applies not only to code but also to the **data** within your data pipelines.
   - This includes **data transformations**, **database population**, and the data itself, treated as 
    code to be versioned and managed.
   - Automation can range from running processes manually to using orchestration tools like **Airflow** 
    to define pipelines as **Directed Acyclic Graphs (DAGs)**.

2. **Version Control for Code and Data:**
   - Version control, commonly done with platforms like **GitHub**, tracks changes in code and allows 
    reverting to previous versions if necessary.
   - In DataOps, **version control extends to data** itself. You can track changes in data within your 
    pipelines and **roll back** to earlier versions if problems occur.

3. **Infrastructure as Code:**
   - DataOps borrows the DevOps practice of treating **infrastructure as code**.
   - This involves writing code that defines the **resources** required to run your data 
    pipelines (e.g., cloud resources).
   - By maintaining infrastructure as code, you can:
     - Deploy infrastructure by running the code.
     - Modify the code to update infrastructure.
     - Use **version control** to revert to previous infrastructure setups when needed.

4. **Automation in DataOps Practices:**
   - DataOps automation spans multiple areas of the data engineering lifecycle:
     - **Orchestration** of pipelines.
     - **Testing** and **deployment** of data processes.
     - Ensuring **data quality** and **observability**.
   - Automation supports overlap between **DataOps**, **software engineering**, and 
    **data management**, enhancing control and data value throughout its lifecycle.
    
### Infrastructure as Code
1. **Infrastructure as Code (IaC)**: Allows for programmatic definition, deployment, and maintenance 
    of cloud infrastructure resources for data pipelines, including networking, security, computing, 
    storage, and data management.

2. **Historical Roots**: IaC originated from configuration management practices in the 1970s, where 
    engineers used BASH scripts to manage physical machines. 

3. **Cloud Computing and IaC**: AWS EC2's launch in 2006 enabled scalable cloud resources. In the 2010s, 
    tools like Terraform, CloudFormation, and Ansible were developed to provision infrastructure through code.

4. **Terraform & CloudFormation**: Terraform supports multiple cloud providers, whereas CloudFormation 
    is native to AWS. Both tools are widely supported and documented.

5. **Terraform Example - S3 Bucket Setup**: Terraform uses the `resource` keyword to define infrastructure. 
    The structure includes specifying the provider (`aws_s3_bucket`), naming the resource (`data_lake`), 
    and configuration options with key-value pairs.

6. **HashiCorp Configuration Language (HCL)**: Terraform uses HCL, a declarative language, meaning you 
    only need to declare the desired end-state of the infrastructure, and Terraform will handle the 
    necessary steps to achieve it.

7. **Idempotency in Terraform**: Terraform ensures idempotency, meaning it will only make changes to the 
    infrastructure if the desired state does not match the current state.

8. **Imperative vs Declarative**: Unlike imperative languages like BASH, where exact sequences are specified, 
    HCL is declarative, focusing on the desired end-state without detailing how to achieve it.
 
### Terraform - Creating an EC2 Instance
1. **Terraform Workflow**: The Terraform workflow involves writing configuration files to define resources, 
    initializing the workspace, creating an execution plan, and applying the plan to provision infrastructure.

2. **Setting Up EC2 Instance**: 
   - Example provided demonstrates setting up an EC2 instance in the default VPC of a region (e.g., us-east-1).
   - IDE like Cloud 9 is used for writing configuration files (e.g., `main.tf`).
   
3. **Terraform Configuration File Structure**: Configuration files typically have five sections: 
   - Terraform settings 
   - Providers 
   - Resources 
   - Input variables (optional)
   - Output values (optional)

4. **Terraform Code Block**: 
   - JSON-like structure.
   - Code blocks are categorized by keywords like `resource`, `provider`, etc., and can include 
    labels and block arguments within curly braces.

5. **Providers**: 
   - Providers in Terraform refer to plugins that allow Terraform to interact with external 
        resources (e.g., AWS, GCP).
   - Example: AWS provider (`hashicorp/aws`) enables interaction with AWS services.

6. **Declaring AWS Provider**: 
   - AWS provider is declared with local name (`aws`), source (`hashicorp/aws`), and optionally, 
        a version constraint.
   - A provider block is used to configure provider-specific settings (e.g., region).

7. **Creating an EC2 Instance**: 
   - Use `resource` keyword and specify `aws_instance` as the resource type.
   - Required arguments: AMI ID (Amazon Machine Image) and instance type (e.g., `t2.micro`).
   - Example tags and other optional arguments can also be included.

8. **Terraform Commands**:
   - `terraform init`: Installs necessary providers (e.g., AWS) based on the configuration file.
   - `terraform plan`: Generates an execution plan that details what will be created, updated, or destroyed.
   - `terraform apply`: Applies the execution plan and provisions the resources.

9. **Terraform Output**: 
   - After `terraform apply`, the EC2 instance is created based on the configuration file.
   - Terraform outputs the execution plan for approval before provisioning the resources.

### Terraform - Defining Variables and Outputs

1. **Input Variables**: Replace hard-coded values with input variables to 
    parameterize configurations.
   - Use the `variable` keyword to declare variables.
   - Example:
     ```hcl
     variable "region" {
       description = "AWS region"
       type        = string
       default     = "us-east-1"
     }
     
     variable "server_name" {
       description = "Server name"
       type        = string
     }
     ```

2. **Using Variables**: Use `var.variable_name` to reference variables inside blocks.
   - Example:
     ```hcl
     provider "aws" {
       region = var.region
     }
     
     resource "aws_instance" "webserver" {
       ami           = "ami-0c55b159cbfafe1f0"
       instance_type = "t2.micro"
       tags = {
         Name = var.server_name
       }
     }
     ```

3. **Assigning Variable Values**: Use a `.tfvars` file to automatically assign values to variables.
   - Example (`terraform.tfvars`):
     ```hcl
     server_name = "example-server"
     ```

4. **Output Values**: Export resource attributes like `id` and `arn` using the `output` block.
   - Example:
     ```hcl
     output "server_id" {
       value = aws_instance.webserver.id
     }

     output "server_arn" {
       value = aws_instance.webserver.arn
     }
     ```

5. **Accessing Outputs**: Use `terraform output` to query output values.
   - Command:
     ```bash
     terraform output        # Show all outputs
     terraform output server_id  # Show specific output
     ```

6. **Organizing Files**: Split configuration into multiple files for better organization:
   - `variables.tf` for variables.
   - `outputs.tf` for output values.
   - `providers.tf` for provider configurations.
   - `main.tf` for resource definitions.

### Terraform - Defining Data Sources and Modules

1. **Data Blocks**: Use data blocks in Terraform to reference resources created outside 
    of Terraform or in another workspace.
   - Declare a data block using:
     ```hcl
     data "aws_subnet" "selected_sub" {
       id = "subnet-0123456789abcdef0"
     }
     ```
   - Access attributes using:
     ```hcl
     subnet_id = data.aws_subnet.selected_sub.id
     ```

2. **Using Data Sources**: Automatically retrieve information such as the latest 
    Amazon Machine Image (AMI) for EC2 instances.
   - Example for finding the latest Linux AMI:
     ```hcl
     data "aws_ami" "latest_linux" {
       most_recent = true
       owners      = ["amazon"]

       filter {
         name   = "architecture"
         values = ["x86_64"]
       }
     }
     ```
   - Access the AMI ID using:
     ```hcl
     ami = data.aws_ami.latest_linux.id
     ```

3. **Modules**: Group related resources in Terraform using modules, which are 
    sub-directories that package resources together.
   - Create a module by moving relevant files (e.g., `main.tf`, `variables.tf`, `outputs.tf`) 
    into a sub-directory (e.g., `website`).

4. **Declaring a Module Block**: In the root directory, declare a module block to call 
    the module and pass input variables.
   - Example module block:
     ```hcl
     module "website" {
       source       = "./website"
       server_name  = var.server_name_root
     }
     ```

5. **Exporting Module Outputs**: To access outputs from a module in the root directory, 
    declare outputs in the outputs file.
   - Example output declaration:
     ```hcl
     output "server_id" {
       value = module.website.server_id
     }

     output "server_arn" {
       value = module.website.server_arn
     }
     ```

6. **Initialization and Updates**: Whenever you add, remove, or modify modules, run 
    `terraform init` to adjust the installed modules, then run `terraform apply` to apply changes.

## DataOps - Observability
### Data Observability
1. **DataOps and Observability**: DataOps incorporates principles of automation, observability, 
    and monitoring from software development, enhancing data engineering practices.

2. **Importance of Observability Tools**: Observability tools help teams monitor system health 
    by tracking metrics like CPU and RAM usage, allowing for quick detection of anomalies and prevention of downtime.

3. **Data Quality Metrics**: High-quality data is defined as being accurate, complete, discoverable, and timely. 
    It should match stakeholder expectations regarding schema and definitions.

4. **Consequences of Low-Quality Data**: Providing low-quality data can be more detrimental than providing no data 
    at all, leading to costly business decisions and undermining stakeholder trust in the data team.

5. **Challenges in Data Systems**: Data systems may appear healthy while delivering low-quality data. For instance, 
    a system might still function but serve inaccurate outputs due to upstream changes.

6. **Hypothetical Scenario**: A data engineer faces issues when a transactional database changes the sales price currency, 
    resulting in misleading analytics despite the system's operational status, highlighting the need for data quality vigilance.

7. **Responsibility for Data Quality**: Data engineers must ensure the quality of the data, even if upstream systems 
    change unexpectedly. Understanding and monitoring data quality is crucial for maintaining stakeholder trust.

8. **Role of Data Observability and Monitoring**: Data observability and monitoring are essential for quickly identifying 
    disruptions in data systems and understanding their impacts.

### Conversation with Barr Moses
1. **Introduction to Barr Moses**:  
   Barr Moses is the CEO and co-founder of Monte Carlo, credited as the leader in the data observability category, 
   with a background in math and statistics.

2. **What is Data Observability?**:  
   Data observability helps data teams regain confidence in their data by understanding the health and quality of 
   data systems, akin to software observability.

3. **Impact of Data Quality Issues**:  
   Data quality problems can lead to significant operational disruptions, such as Netflix experiencing 
   a 45-minute outage due to bad data.

4. **Three Core Components of Data State**:  
   - **Data**: The actual content ingested into the system.  
   - **Code**: The scripts that transform the data, written by engineers.  
   - **Systems**: The infrastructure running the data processes.  
   Problems can arise in any of these areas.

5. **Key Metrics for Observability**:  
   - **Number of Incidents**: Track how many data issues occur.  
   - **Time to Detection**: Measure how quickly issues are identified.  
   - **Time to Resolution**: Understand how long it takes to resolve issues.

6. **Success Stories**:  
   JetBlue measures internal team Net Promoter Scores (NPS) to assess satisfaction with data reliability, 
   improving their operations and support systems.

7. **Engaging with Stakeholders**:  
   Barr emphasizes the importance of communicating with stakeholders to understand their pain points and needs, 
   and testing ideas directly with them.

8. **Continuous Learning and Flexibility**:  
   Barr advises learners to remain curious and flexible, finding their own paths based on customer feedback, 
   as the data landscape is continually evolving.

9. **Encouragement for Learners**:  
   Barr expresses enthusiasm for the course and encourages learners to engage actively with the material and 
   stay curious about data observability.

### Key Takeaways From the Conversation with Barr Moses

1. **Inevitability of Data Issues**:  
   Data issues can occur at any stage of the data pipeline. Early detection is crucial to 
   minimize organizational damage.

2. **Choosing Metrics for Data Quality**:  
   Metrics that assess data quality should be chosen, similar to how software teams monitor their infrastructure's health.

3. **Key Questions for Data Quality**:  
   In her book, **Data Quality Fundamentals**, Barr Moses suggests starting with the following questions:
   - Is the data up-to-date?
   - Is the data complete?
   - Are fields within expected ranges?
   - Is the null rate higher or lower than it should be?
   - Has the schema changed?

4. **5 Pillars of Data Observability**:  
   Barr Moses formulated these questions into five pillars for data observability to fully 
   describe the state of the data:
   - **Distribution/Internal Quality**: Checks metrics like the percentage of NULL elements, 
   unique elements, summary statistics, and expected ranges to ensure data trustworthiness.
   - **Freshness**: Refers to how up-to-date the data is within the final asset, such as when 
   it was last updated and the frequency of updates. Stale data can waste time and resources.
   - **Volume**: Involves monitoring the amount of ingested data for unexpected spikes or drops, 
   which could indicate lost data, system outages, or surges in usage.
   - **Lineage**: Helps trace the data journey from its source to its destination, allowing 
   identification of errors or anomalies by visualizing data transformations and storage.
   - **Schema**: Involves monitoring changes in data structure or types to prevent data pipeline failures.

### Monitoring Data Quality
# Key Takeaways on Starting Data Observability and Monitoring

1. **Importance of Stakeholder Needs**:  
   Data observability begins with understanding what stakeholders need. Identifying key 
   metrics relevant to their use cases is crucial.

2. **Focus on Important Metrics**:  
   Rather than monitoring every conceivable metric, focus on the most important aspects to 
   avoid confusion and alert fatigue. 

3. **Examples of Metrics to Monitor**:  
   - Total number of records adjusted in batches or over time.
   - Range of values in specific columns.
   - Total number of null values in tables.
   - Time difference between now and the timestamp of the most recent record.

4. **Understanding Data Freshness**:  
   Stakeholders may prioritize fresh data, so monitoring the recency of data ingestion 
   (e.g., data not older than 24 hours) is essential.

5. **Critical vs. Non-Critical Data Components**:  
   Identify which components of the data are critical for monitoring (e.g., accuracy of sales records) 
   versus those that are less important (e.g., matching product SKU numbers to descriptions).

6. **Communication with Source System Owners**:  
   Good communication with source system owners is vital for understanding changes and anticipating 
   issues in data quality.

7. **Building in Checks and Tests**:  
   Implement checks or tests in your data monitoring to verify schema and data types remain consistent, 
   helping identify problems early.

8. **Manual vs. Automated Monitoring**:  
   While manual checks and custom code may be appropriate initially, leveraging tools designed for 
   data quality monitoring can simplify the process and reduce effort.

9. **Introduction to Great Expectations**:  
   The upcoming conversation with Abe Gong will provide context on **Great Expectations**, an open-source tool 
   for testing data quality, which will be useful in practical applications.

### Conversation with Abe Gong 

1. **Inspiration for Great Expectations**:  
   - The idea for Great Expectations emerged from personal experiences dealing with data quality issues.
   - Abe Gong and co-founder James Campbell independently came to a meeting with the same idea: to create 
    an open-source project that allows testing of data pipelines like software testing.

2. **Foundational Philosophy of Data Quality**:  
   - Data quality is fundamentally about being "fit for purpose." 
   - It involves ensuring that data meets the needs of the specific tasks or analyses it is being used for, 
    whether it’s for dashboards or machine learning models.

3. **Different Aspects of Data Quality**:  
   - Data quality considerations can vary widely depending on the use case:
     - For dashboards, focus on data logging, aggregation, and time lag.
     - For machine learning, emphasize data distributions and bias.

4. **Great Expectations as a Solution**:  
   - Great Expectations applies software testing philosophies to data pipelines, creating assertions 
    about data states at specific points in the pipeline.
   - It emphasizes the necessity of automated testing for reliable data workflows.

5. **Flexibility and Use Cases**:  
   - Great Expectations is versatile and can be deployed in various contexts, but users need clear 
    documentation to find and implement the right use cases effectively.

6. **Key Questions for Implementation**:  
   - When getting started, consider who will work with the data expectations and requirements.
   - Determine whether the tool should be tightly integrated with your existing systems or if it 
    should facilitate collaboration with other stakeholders.

7. **Great Expectations Cloud**:  
   - An upcoming launch, Great Expectations Cloud, will offer improved functionality for team 
    collaboration and ease of use.

8. **Importance of Data Quality**:  
   - Abe emphasizes the critical nature of data quality; neglecting it can lead to significant 
    issues down the line.
   - Newcomers in the data field should take data quality seriously from the outset to avoid 
    future complications.

### Great Expectations - Core Components  

1. **Starting the Workflow**:  
   - Specify the data to be tested.
   - Define expectations (tests) to be performed on the data.
   - Validate the data against these expectations.

2. **Core Components**:
   - **Data Context**:  
     - Serves as the entry point for the Great Expectations API.
     - Used to configure and access properties and metadata of your 
        Great Expectations project.
   - **Data Source**:  
     - Specifies where to retrieve data (e.g., SQL database, local file system, 
        S3 bucket, or pandas DataFrame).
   - **Data Asset**:  
     - A collection of records within a data source (e.g., a table, a file, 
        or a query joining multiple tables).
     - Can be partitioned into batches for validation (e.g., by month, store ID, 
        or as one complete set).
   - **Batch Request Object**:  
     - The primary method to retrieve data from the data asset for further processing.

3. **Defining Expectations**:  
   - Expectations are statements to verify conditions in the data (e.g., checking for null values).
   - Can use built-in expectations from the expectation gallery or define custom ones.
   - Expectations are collected in an expectation suite object.

4. **Data Validation**:  
   - **Validator Object**:  
     - Combines a batch request and its corresponding expectation suite for manual validation.
   - **Checkpoint Object**:  
     - Streamlines validation by automatically providing a batch request and expectation 
        suite to a validator, generating validation results.

5. **Metadata Storage**:  
   - Metadata generated during validation is stored in various backend stores:
     - **Expectation Store**: Contains expectation suites.
     - **Validation Store**: Contains validation results information.
     - **Checkpoint Store**: Contains checkpoint configurations.
     - **Data Docs Store**: Contains reports on expectations, checkpoints, and validation results.

6. **Typical Workflow Steps**:  
   - Instantiate a data context.
   - Declare the data source.
   - Define data assets and partition if necessary.
   - Create batch request objects.
   - Define expectations and collect them in an expectation suite.
   - Validate data using a validator or checkpoint.
 
### Great Expectations - Workflow Example 
1. **Overview of Application**:
   - Applying Great Expectations to the DVD rental Database, focusing on the payment table.
   - Expectations to check:
     - Payment ID column contains unique IDs.
     - Customer ID column does not contain null values.
     - Amount column contains non-negative values.

2. **Setting Up Great Expectations**:
   - Install Great Expectations using `pip install great expectations`.
   - Initialize the project with `great expectations init` to set up the data context, 
        project folder structure, and backend stores.

3. **Creating a Jupyter Notebook**:
   - Launch a Jupyter notebook in the root directory.
   - Import Great Expectations and get the context object using `get_context()`.

4. **Connecting to the Data Source**:
   - Create a data source object using `context.sources.add_sql()`.
   - Provide a connection string with database details (username, password, hostname, port, database name).

5. **Creating Data Asset**:
   - Create a data asset using `add_table_asset()` for the payment table.
   - Use `add_splitter_datetime_part()` to partition the data by payment date (monthly).

6. **Building Batch Request**:
   - Create a batch request object using `build_batch_request()`.

7. **Defining Expectations**:
   - Create an expectation suite using `add_or_update_expectation_suite()` named "mysuite".
   - Use a validator to define expectations:
     - Check payment ID uniqueness: `expect_column_values_to_be_unique()`.
     - Check customer ID for null values: `expect_column_values_to_not_be_null()`.
     - Check amount for non-negativity: `expect_column_min_to_be_between()`.

8. **Saving Expectations**:
   - Save the expectation suite using `save_expectation_suite()` to retain it for future sessions.

9. **Creating a Checkpoint**:
   - Automate validation using a checkpoint object with `add_or_update_checkpoint()`.
   - Specify validations as pairs of data batches and their corresponding expectation suites.

10. **Running the Checkpoint**:
    - Execute the checkpoint using `run()`, confirming that all tests passed.

11. **Viewing Validation Results**:
    - Generate data docs using `build_data_docs()` to review validation results.
    - Access detailed statistics about evaluated expectations and results for each batch.

### Conversation with Chad Sanderson
1. **Introduction to Data Contracts**
   - Data contracts serve as an interface for data, similar to an API.
   - They establish expectations between data producers and consumers, helping prevent 
        data quality issues.

2. **Problems Without Data Contracts**
   - Lack of communication between data producers and consumers leads to chaos and data quality problems.
   - Downstream teams often have to build extensive validations and trace issues back to the source.

3. **Structure of Data Contracts**
   - A data contract consists of a specification (spec) and enforcement mechanisms.
   - The spec includes:
     - **Structure**: Schema, column names, and business logic.
     - **Content**: Data quality rules, SLAs, and compliance policies.

4. **Nature of Data Contracts**
   - Data contracts are not legally binding but serve to facilitate communication and enforcement.
   - Enforcement can include integration tests and alerts for contract breaches.

5. **Collaboration vs. Technology**
   - While technology aids in implementation and enforcement, the success of data contracts relies 
        heavily on collaboration between teams.

6. **Implementation Tips**
   - Avoid creating overly complex contracts that overwhelm engineering teams.
   - Focus on high-impact data pipelines for initial implementations.
   - Begin with simple conversations and awareness initiatives to demonstrate the impact of data on business outcomes.

7. **Starting with Data Contracts**
   - Engage with data producers to clarify how their data is used within the organization.
   - Select key pipelines to start implementing contracts where data quality significantly impacts operations.


### Amazon CloudWatch

1. **Importance of Monitoring**
   - Ensures data system components operate as expected.
   - Alerts to problems as they arise and anticipates issues.

2. **Automatic Metrics with AWS**
   - Many AWS resources automatically send metrics to CloudWatch.
   - Common metrics include CPU utilization, disk I/O, network traffic, and memory usage.

3. **Custom Metrics**
   - Allow monitoring of specific application aspects not covered by default metrics.
   - Examples include transactions processed, API response times, and active users.

4. **CloudWatch Dashboards**
   - Visualize and monitor important metrics.
   - Aggregate metrics for a unified view to identify and diagnose issues over time.

5. **CloudWatch Alarms**
   - Create alarms for metrics to receive alerts when thresholds are breached.
   - Establish reasonable thresholds based on baseline performance measurements.

6. **Common RDS Metrics to Monitor**
   - **CPU Utilization**: High values (>80-90%) indicate heavy load or need for optimization.
   - **RAM Consumption**: High usage may require scaling to a larger instance type.
   - **Disk Space**: Consistently above 85% may necessitate data deletion or archiving.
   - **Database Connections**: Monitor active connections to avoid reaching maximum limits.

7. **Third-Party Monitoring Tools**
   - Other services like DataDog and Splunk can be used alongside CloudWatch.

8. **Conclusion**
   - Different AWS services post various metrics; identify which are relevant to your use case.
