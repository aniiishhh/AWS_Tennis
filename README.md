# AWS Tennis Analysis Data Pipeline Project

## Introduction

In this project, I built an automated ETL pipeline to extract, transform, and load tennis data from the web, process it using AWS services, and visualize it with Tableau. The goal was to create a robust, scalable, and efficient data pipeline that can handle regular updates and provide actionable insights through an **Interactive Dashboard** ([Dashboard sample from data extract](https://public.tableau.com/app/profile/anish.pravin.kulkarni/viz/ATPTennisDashboard_17192883856510/Dashboard1)). 

## [Data Architecture Diagram](aws_tennis_data_architecture.pdf)

![Data Architecture Diagram](aws_tennis_data_architecture.jpg)

## Step-by-Step Implementation

### 1. Data Extraction with AWS Lambda

**Objective**: Automate the extraction of raw data from [tennis-data.co.uk](http://tennis-data.co.uk/) and store it in an S3 bucket.

- **Serverless Execution with AWS Lambda**: AWS Lambda allows for the serverless execution of code, eliminating the need for infrastructure management. It provides a cost-effective and scalable solution that adjusts automatically based on demand.
  
- **Scheduling with Amazon EventBridge**: Amazon EventBridge is utilized to schedule the Lambda function to run weekly. This automation ensures the pipeline's regular and consistent updating without manual intervention.

AWS Lambda and EventBridge offer a seamless, automated solution for regularly extracting raw tennis data from the web. This setup leverages AWS's serverless architecture to provide a cost-effective and scalable way to keep the data pipeline up-to-date.

### 2. Storing Raw Data in S3

**Objective**: Store the raw data in an S3 bucket for further processing.

- **AWS S3**: S3 is chosen for its scalability, durability, and seamless integration with other AWS services. It serves as a reliable storage solution for both raw and processed data.
  
- **Efficient Data Management**: S3's capabilities ensure that raw data is stored securely and is readily accessible for subsequent processing steps.

Using S3 for raw data storage leverages its robust, scalable infrastructure, ensuring that the data is securely stored and easily accessible for further processing.

### 3. Triggering ETL with S3 Event Notifications

**Objective**: Automatically trigger the ETL process when new data arrives in the raw S3 bucket.

- **S3 Event Notifications**: Configured S3 to send notifications to a Lambda function whenever a new object is created in the raw data bucket. This function then triggers the AWS Glue ETL job.

S3 event notifications provide a seamless method to automate the ETL process, ensuring that data transformation begins immediately after new raw data is available.

### 4. Data Transformation with AWS Glue

**Objective**: Transform raw CSV data into a structured format and store it in a processed S3 bucket as Parquet files.

- **AWS Glue**: Selected for its serverless ETL capabilities, AWS Glue handles provisioning, managing ETL jobs, and scaling as needed.
  
- **Glue Crawler**: Used to create a data catalog for the raw data, simplifying the querying and transformation process.
  
- **Transformations**:Implemented schema changes, custom transformations in Glue using PySpark to clean and preprocess the data for better visualization capabilities.

AWS Glue offers a robust platform for ETL operations, with its serverless nature ensuring scalability and ease of use. Custom transformations ensure that the data is clean and optimized for further analysis.

### 5. Storing Processed Data in S3

**Objective**: Store the processed data in an S3 bucket in Parquet format.

- **Parquet Format**: Chosen for its efficient storage and query performance. Parquet format significantly reduces storage costs and improves query speeds.
  
- **Data Overwrite Strategy**: Implemented a strategy to delete existing parquet files before writing new ones to avoid data duplication and ensure the table reflects the most recent data.

Using the Parquet format and an effective overwrite strategy ensures that the processed data is stored efficiently, with each ETL run providing the most up-to-date dataset.

### 6. Querying Data with AWS Athena

**Objective**: Enable querying of the processed data using AWS Athena.

- **AWS Athena**: Used for running SQL queries directly on data stored in S3. Athena provides a cost-effective and powerful way to analyze large datasets without needing complex ETL pipelines.

Athena's serverless architecture and SQL capabilities provide a straightforward and efficient method to query processed data stored in S3, enabling easy data analysis and integration with visualization tools.

### 7. Visualizing Data with Tableau

**Objective**: Create interactive dashboards to visualize the processed data.

- **Tableau Integration**: Connected AWS Athena with Tableau using the JDBC driver, enabling dynamic visualizations and interactive dashboards.
  
- **Interactive Dashboards**: Designed to display various statistics, charts, and heatmaps, providing deep insights into tennis player performance.

Integrating Tableau with AWS Athena allows for the creation of rich, interactive dashboards. This setup transforms processed data into actionable insights, facilitating better decision-making and data exploration.

## Conclusion

This project showcases the power of AWS services in building a robust and scalable data pipeline. By leveraging serverless architecture, automated scheduling, efficient data storage, and powerful visualization tools, I created a comprehensive solution for extracting, transforming, and analyzing tennis data. The decisions made throughout the project follow best practices, ensuring an efficient, cost-effective, and maintainable pipeline.

Feel free to reach out if you have any questions or would like to discuss the project in more detail!
