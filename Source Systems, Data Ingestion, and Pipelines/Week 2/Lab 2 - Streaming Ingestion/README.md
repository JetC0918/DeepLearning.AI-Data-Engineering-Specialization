Lab 2: Streaming Ingestion
1. **Lab Overview**: The lab focuses on interacting with Amazon Kinesis Data Streams to 
    understand the streaming ingestion process.

2. **Part One**: 
   - Work with a Kinesis Data Stream to act as a router between a simple producer and a consumer.
   - Manually generate data using the producer application and write it to the Kinesis Data Stream.
   - Consume the generated data from the stream.

3. **Part Two**: 
   - Perform a streaming ETL process by consuming data from the Kinesis Data Stream.
   - Apply simple transformations to the consumed data.
   - Send the transformed data into one of two new data streams.

4. **Data Delivery**: From each of the two new data streams, data will be delivered to respective 
    S3 buckets using Kinesis Firehose.
