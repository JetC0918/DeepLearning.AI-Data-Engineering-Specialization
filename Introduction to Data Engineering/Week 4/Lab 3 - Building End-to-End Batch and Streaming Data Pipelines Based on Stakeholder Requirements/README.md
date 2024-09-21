1. **Lab Objectives**:
   - Implement the batch pipeline to prepare training data for the recommender system.
   - Set up a vector database for storing output embeddings.
   - Implement a streaming pipeline for real-time product recommendations based on user browsing.

2. **Batch Pipeline Implementation**:
   - Use an RDS MySQL database containing classic models data and user ratings.
   - Transform the data using **AWS Glue ETL** and store the results in 
        an **S3 bucket** labeled as Data Lake. 

3. **Database Connection**:
   - Retrieve the database endpoint and connect using MySQL commands.
   - Explore the ratings table to understand its structure 
        (customer number, product code, product rating).

4. **Terraform Setup**:
   - Install Terraform and define environmental variables using a 
        provided `setup.sh` script.
   - Organize Terraform files into modules for Glue and S3, modifying the main 
        Terraform file to declare these modules.
   - Run Terraform commands: `terraform init`, `terraform plan`, 
        and `terraform apply` to create resources.

5. **Glue Job Execution**:
   - Start the Glue job to transform data into the desired format.
   - Monitor the Glue job status and verify completion.

6. **Data Verification**:
   - Check the S3 bucket (Data Lake) for the transformed training data, which is 
        organized in a partitioned structure for easy access.
