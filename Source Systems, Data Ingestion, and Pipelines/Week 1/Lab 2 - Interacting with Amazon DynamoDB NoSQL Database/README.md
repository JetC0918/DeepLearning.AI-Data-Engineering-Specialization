**Lab 2: Interacting With Amazon DynamoDB NoSQL Database**

1. **DynamoDB Overview**: DynamoDB is a key-value database that stores items in tables, 
where each item is uniquely identified by a primary key. The primary key can be a simple 
key or a composite key consisting of a partition key and a sort key.

2. **Primary Key Types**: A simple primary key uses a single key, while a composite primary 
key combines two keys (partition key and sort key) to uniquely identify items. This allows for 
multiple items with the same partition key, differentiated by their sort keys.

3. **Schema-less Design**: DynamoDB tables are schema-less, meaning you don't need to define 
attributes in advance, offering flexibility in how data is stored.

4. **CRUD Operations**: The lab involves using Boto3, the AWS SDK for Python, to perform CRUD 
operations with methods like `create_table`, `put_item`, `update_item`, `scan`, `get_item`, 
`query`, and `delete_item`.

5. **Data Files**: Four JSON files will be used to load data into DynamoDB tables: product catalog, 
forum data, thread information, and replies. Each file contains items defined by key-value pairs 
with type descriptors (e.g., 'N' for number, 'S' for string).

6. **Creating Tables**: You'll create tables using the `create_table` method of Boto3, specifying 
the table name and primary key definitions through provided dictionaries without needing to code 
the arguments manually.
 