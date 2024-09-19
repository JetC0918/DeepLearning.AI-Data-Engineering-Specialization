## Lab 1: An Example of the Data Engineering Lifecycle
1. **Overview**:
   - **Scenario**: Build an end-to-end data pipeline on AWS for a retailer's database.
   - **Tasks**: Ingest data from an RDS MySQL database, transform it, 
        and store it in S3 for analysis.

2. **Data Pipeline Stages**:
   - **Source System**: Relational database with tables like Customers, Products, Orders, etc.
   - **Ingestion & Transformation**: Use AWS Glue to extract data, transform it into a star schema, 
        and load it into S3.
   - **Data Modeling**: Transform data into a star schema with a fact table and dimension tables.

3. **Architecture Components**:
   - **AWS Glue**: For ETL (Extract, Transform, Load) operations.
   - **S3**: Storage for transformed data.
   - **Glue Crawler**: Infers data structure and updates Glue Data Catalog.
   - **Amazon Athena**: For querying the data stored in S3 using SQL.

4. **Lab Setup**:
   - **Terraform**: Use this Infrastructure as Code tool to programmatically create resources.
   - **AWS Cloud9**: IDE hosted on EC2 for development, used to set up the environment 
        and launch Jupyter Notebook.

5. **Hands-On Experience**:
   - **Programmatic Resource Creation**: Use Terraform code provided in the lab.
   - **Analytical Queries**: Act as the data analyst to run queries on transformed data 
        using Amazon Athena and Jupyter Notebook.
 