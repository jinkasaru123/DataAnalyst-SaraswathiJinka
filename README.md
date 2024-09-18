# DataAnalyst-SaraswathiJinka


Project Title: Data Analytical Platform for City of Vancouver Property Tax Report

Objective
The objective of this project was to analyze property tax data from the City of Vancouver for the years 2023 and 2024. The project aimed to derive insights regarding year-over-year trends, the impact of zoning classifications, regional differences, and comparisons across property types (e.g., strata and land).

Dataset
•	Source: Property tax datasets for 2023 and 2024 were downloaded from the City of Vancouver Open Data Portal.
•	Fields: Key fields included:
o	Property Type: Residential, strata, land, etc.
o	Zoning Classification: Associated zoning codes.
o	Tax Values: Assessed tax values for each property.

Methodology
1. Data Collection and Storage:
•	Data Acquisition: The datasets for 2023 and 2024 were downloaded in Excel format from the City of Vancouver Open Data Portal.
•	Storage Solution:
o	The Excel files were uploaded to AWS S3.
o	Datasets were organized into S3 landing zones for both years.
o	Security: KMS encryption was applied to secure the data at rest.
2. Data Cleaning and Transformation:
•	Data Preparation Using AWS Glue DataBrew:
o	The data was cleaned, correcting any inconsistencies and handling missing values.
o	A "Year" column was added to facilitate comparisons between 2023 and 2024 datasets.
o	Cleaned datasets were stored in the Raw S3 bucket.
3. ETL Pipeline Design:
•	ETL Pipeline Design:
o	An ETL (Extract, Transform, Load) pipeline was designed using Draw.io to map the data flow from the Landing S3 bucket to the Curated S3 bucket.
o	Key transformations included renaming columns for consistency, filtering out unnecessary data, and aggregating the tax levy datasets.
•	ETL Implementation Using AWS Glue:
o	The ETL pipeline was implemented in AWS Glue to extract data from the Raw S3 bucket, transform it, and load it into the Curated S3 bucket.
4. Data Analysis:
•	Amazon Athena was used for creating external tables:
o	SQL Queries: SQL was utilized only for creating tables to organize the datasets in Athena and point to the curated data stored in S3.
•	Data Visualization:
o	Analysis of tax trends, zoning impacts, and regional differences was conducted through visualizations created in Excel.
5. Data Protection and Governance:
•	Data Encryption: KMS keys were used to encrypt all data stored in S3.
•	Backup and Replication:
o	A backup S3 bucket was created to ensure data availability in case of failures.
o	Replication rules were applied to securely transfer data between the primary and backup S3 buckets using the same KMS encryption.
•	Automated Data Governance: AWS Glue was used to conduct regular data quality checks, with a scheduled automation process ensuring data consistency and accuracy.
6. Data Monitoring:
•	Amazon CloudWatch and AWS CloudTrail were employed for continuous monitoring and tracking:
o	CloudWatch was used to monitor key metrics such as resource consumption and cost estimations.
o	CloudTrail tracked all user activities and API calls, storing the logs in S3 for audit purposes.
7. Data Visualization:
•	Visualization Tools:
o	Excel was utilized to create interactive charts such as pie, bar, and line graphs.
o	A dashboard was prepared using Excel, highlighting key insights such as year-over-year trends, zoning impacts, and regional tax differences.
8. Data Publishing:
•	Server Setup:
o	EC2 Instances were configured to host and publish the processed data and visualizations.
o	The processed datasets were made accessible to stakeholders via a web interface hosted on the EC2 instances.
•	Data Storage: The transformed data and visual reports were uploaded to S3, allowing for easy access and sharing among stakeholders.

Tools and Technologies

•	AWS Services:
1. S3: Data storage and management.
2. AWS Glue: Data cleaning, transformation, and ETL pipeline implementation.
3. Amazon Athena: SQL queries for table creation and dataset management.
4. Amazon CloudWatch: System monitoring.
5. AWS CloudTrail: Audit logs and user activity tracking.
6. KMS Encryption: Data security.
7. EC2 Instances: Web hosting and report publishing.
   
•	Data Visualization:
1. Excel: Used to generate interactive visualizations such as charts and dashboards.
2. Draw.io: Used for visualizing the ETL pipeline workflow.

Deliverables
•	A fully functioning ETL pipeline implemented using AWS Glue to process property tax data.
•	Interactive Excel dashboards to visualize property tax trends, zoning impacts, and regional differences.
•	Web-accessible reports and visualizations hosted on EC2 instances for stakeholder access.
•	A comprehensive report summarizing the data analysis, findings, and key insights.

Outcomes and Insights
•	Year-Over-Year Trends: Notable changes in tax values across various property types were identified between 2023 and 2024.
•	Zoning Impact: The impact of zoning classifications on property tax assessments was clearly demonstrated.
•	Regional Differences: Variations in tax values across different regions were identified, offering insights into potential policy adjustments.
•	Recommendations: Data-driven suggestions were provided to inform future decisions related to zoning and taxation policies.

Conclusion
This project successfully leveraged AWS cloud services to handle, process, and analyze the City of Vancouver’s property tax data. The implemented ETL pipeline, combined with detailed data analysis and insightful visualizations, provided stakeholders with actionable insights. These insights can be used to guide future decisions regarding property tax policies and zoning regulations.





