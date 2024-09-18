# DataAnalyst-SaraswathiJinka

## _Project 1 Title: Data Analytical Platform for City of Vancouver Property Tax Report_

### Objective

&nbsp;&nbsp;&nbsp;The objective of this project was to analyze property tax data from the City of Vancouver for the years 2023 and 2024. The project aimed to derive insights regarding year-over-year trends, the impact of zoning classifications, regional differences, and comparisons across property types (e.g., strata and land).

![image](https://github.com/user-attachments/assets/4756bdac-ca40-417e-b293-260b43fe8179)

*Fig 1: Data Anlytical Platform*

### Dataset

**_Source:_** Property tax datasets for 2023 and 2024 were downloaded from the City of Vancouver Open Data Portal.

![image](https://github.com/user-attachments/assets/d4209943-51b0-4268-aeb4-030589f643e6)

*Fig 2: Data Source and collecting from City of Vancouver Dashboard*


**_Fields:_** Key fields included are

- Property Type: Residential, strata, land, etc.

- Zoning Classification: Associated zoning codes.

- Tax Values: Assessed tax values for each property.

![image](https://github.com/user-attachments/assets/08afd87b-2a32-4570-a611-eab3d6cecfb4)

*Fig 3: Analysing Trends of Prooperty Tax Data*

### Methodology

#### 1. Data Collection and Storage

**_Data Acquisition:_** The datasets for 2023 and 2024 were downloaded in Excel format from the City of Vancouver Open Data Portal.

![image](https://github.com/user-attachments/assets/08fe0240-1054-46e7-b562-2ac74b03d2b2)

*Fig 3: Downloaded Excel Data*

**_Storage Solution:_**

- The Excel files were uploaded to AWS S3.

- Datasets were organized into S3 landing zones for both years.

![image](https://github.com/user-attachments/assets/72e69aa1-e4c2-4a97-8aa3-d5772157b91a)

*Fig 4: Storing in AWS S3 bucket(Landing Zone)*

**_Security:_** KMS encryption was applied to secure the data at rest.

![image](https://github.com/user-attachments/assets/0210b121-1420-4f24-9eef-2062f4db4b44)

*Fig 5: Encrypted with KMS*

#### 2. Data Cleaning and Transformation

**_Data Preparation Using AWS Glue DataBrew:_**

- The data was cleaned, correcting any inconsistencies and handling missing values.

- A "Year" column was added to facilitate comparisons between 2023 and 2024 datasets.

- Cleaned datasets were stored in the Raw S3 bucket.

![image](https://github.com/user-attachments/assets/3bcfcf55-fc64-467b-ad3e-93cb7d4570db)

*Fig 6: Cleaning Data through AWS Glue DataBrew*

![image](https://github.com/user-attachments/assets/77b888fd-6c39-4399-afa4-6dbbc8425ce0)

*Fig 7: Storing Cleaned Data in Raw Zone*

#### 3. ETL Pipeline Design

**_ETL Pipeline Design:_**

- An ETL (Extract, Transform, Load) pipeline was designed using Draw.io to map the data flow from the Landing S3 bucket to the Curated S3 bucket.

- Key transformations included renaming columns for consistency, filtering out unnecessary data, and aggregating the tax levy datasets.

![image](https://github.com/user-attachments/assets/45b4bfc3-b07a-48c1-9569-a164ffa6a579)

*Fig 8: ETL Pipeline Design for Property Tax report using Draw.io*

**_ETL Implementation Using AWS Glue:_**

- The ETL pipeline was implemented in AWS Glue to extract data from the Raw S3 bucket, transform it, and load it into the Curated S3 bucket.

![image](https://github.com/user-attachments/assets/5ccee685-c8eb-43c6-adab-f6a9bf246746)

*Fig 9: Implementing designed ETL pipeline in AWS Glue*

![image](https://github.com/user-attachments/assets/6aacb856-7d51-4596-8f30-57acce8b8b17)

*Fig 10: Storing Implemented Data in Curated zone of S3 bucket in CSV form*

#### 4. Data Analysis

**Amazon Athena was used for creating external tables:**

**_SQL Queries:_** SQL was utilized only for creating tables to organize the datasets in Athena and point to the curated data stored in S3.

![image](https://github.com/user-attachments/assets/1eaa4f38-1693-4431-8f1c-017f245e8481)
 
*Fig 11: Dataset preparation using AWS Anthena*

![image](https://github.com/user-attachments/assets/6b415adf-8112-460a-bbad-71c9b50545af)

*Fig 12: Data Table preparation using SQL query in AWS Anthena*

![image](https://github.com/user-attachments/assets/5e157205-e042-4460-80e3-f645dd6098a9)

*Fig 13: Soring Database in Dataproducts of S3 bucket*

#### 5. Data Protection and Governance:

**_Data Encryption:_** KMS keys were used to encrypt all data stored in S3.

**_Backup and Replication:_**

- A backup S3 bucket was created to ensure data availability in case of failures.

- Replication rules were applied to securely transfer data between the primary and backup S3 buckets using the same KMS encryption.

- Automated Data Governance: AWS Glue was used to conduct regular data quality checks, with a scheduled automation process ensuring data consistency and accuracy.

![image](https://github.com/user-attachments/assets/9dcbadfb-e7d7-4861-8e62-5ac5c8ffb169)

*Fig 14: Data Encryption with KMS*

![image](https://github.com/user-attachments/assets/8893d8f2-c736-4782-8e90-7f868a5b31d4)

*Fig 15: Back up for Property Tax Data*

![image](https://github.com/user-attachments/assets/dcc9e319-a044-4d56-8503-33b374c0a0f7)

*Fig 16: Replicated Rules for Property Tax Data*

![image](https://github.com/user-attachments/assets/74e36e9e-0aae-40ab-bbed-1c5b9811ea8b)

*Fig 17:QRPR ETL*

![image](https://github.com/user-attachments/assets/a737a685-aab1-4b13-97c4-3b47d1380b3d)

*Fig 18: Data Quality Schedule*

![image](https://github.com/user-attachments/assets/1986141a-d7f8-46a4-b8bb-16b437710612)

*Fig 19: Workflow for ETL job*

#### 6. Data Monitoring

- Amazon CloudWatch and AWS CloudTrail were employed for continuous monitoring and tracking:

- CloudWatch was used to monitor key metrics such as resource consumption and cost estimations.

- CloudTrail tracked all user activities and API calls, storing the logs in S3 for audit purposes.

![image](https://github.com/user-attachments/assets/8cd12d07-72d7-4248-8fac-a54056fa0b04)

*Fig 20: Cloud Watch Data Monitoring*

![image](https://github.com/user-attachments/assets/4e596c76-c57b-428d-8816-577ce8cd293d)

*Fig 21: Cloud Watch Dashboard for Data Monitoring and Controlling*

![image](https://github.com/user-attachments/assets/73139cac-d158-47a9-ae0f-da829885e20f)

*Fig 22: Created Alarm In CloudWatch*

![image](https://github.com/user-attachments/assets/ea876419-14ce-436a-9ec8-cb2a3272eea4)

*Fig 23: Cloud Trial*

![image](https://github.com/user-attachments/assets/ff60f3fb-2a2e-4d96-96e5-77ec8c5cbd33)

*Fig 24: AWS User logs In S3 Bucket*

#### 7. Data  Visualization

**_Visualization Tools:_**

- Excel was utilized to create interactive charts such as pie, bar, and line graphs.

- A dashboard was prepared using Excel, highlighting key insights such as year-over-year trends, zoning impacts, and regional tax differences.

![image](https://github.com/user-attachments/assets/85349db2-8e4f-4614-9f38-70ec0a23d76d)

*Fig 25: Preparing Data Charts in EXCEL Dashboard*

#### 8. Data Publishing:

**_Server Setup:_**

- EC2 Instances were configured to host and publish the processed data and visualizations.

- The processed datasets were made accessible to stakeholders via a web interface hosted on the EC2 instances.

![image](https://github.com/user-attachments/assets/81d2c721-bcb8-4707-95b0-b513a3fb7c16)

*Fig 26: Creating EC2 Instances in AWS cloud*

![image](https://github.com/user-attachments/assets/78a60aab-7155-4bd2-965a-e046e219bde7)

*Fig 27: Storing Database in Back End Servers*

![image](https://github.com/user-attachments/assets/15dd8700-386e-4083-97c4-03cd4faf18b5)

*Fig 28: Visualizing Data Base in back-end*

![image](https://github.com/user-attachments/assets/f236074f-eff4-4dc8-82a8-67b96100381d)

*Fig 29: Auto-assigned Public IP address of Web Server(Front end)*

![image](https://github.com/user-attachments/assets/75f08bb6-7d1a-4850-af78-bcdd836c7e2f)

*Fig 30: Visualizing Data Base in remote access(front-end for the client)*

**_Data Storage:_** The transformed data and visual reports were uploaded to Remote access, allowing for easy access and sharing among stakeholders.

### Tools and Technologies

**_AWS Services:_**

- S3: Data storage and management.

- AWS Glue: Data cleaning, transformation, and ETL pipeline implementation.

- Amazon Athena: SQL queries for table creation and dataset management.

- Amazon CloudWatch: System monitoring.

- AWS CloudTrail: Audit logs and user activity tracking.

- KMS Encryption: Data security.

- EC2 Instances: Web hosting and report publishing.
  
**_Data Visualization:_**

- Excel: Used to generate interactive visualizations such as charts and dashboards.

- Draw.io: Used for visualizing the ETL pipeline workflow.

### Deliverables

- A fully functioning ETL pipeline implemented using AWS Glue to process property tax data.

- Interactive Excel dashboards to visualize property tax trends, zoning impacts, and regional differences.

- Web-accessible reports and visualizations hosted on EC2 instances for stakeholder access.

- A comprehensive report summarizing the data analysis, findings, and key insights.

### Outcomes and Insights

*1. Year-Over-Year Trends:* Notable changes in tax values across various property types were identified between 2023 and 2024.

*3. Zoning Impact:* The impact of zoning classifications on property tax assessments was clearly demonstrated.

*4. Regional Differences:* Variations in tax values across different regions were identified, offering insights into potential policy adjustments.
   
*5. Recommendations:* Data-driven suggestions were provided to inform future decisions related to zoning and taxation policies.
   
### Conclusion

&nbsp;&nbsp;&nbsp;This project successfully leveraged AWS cloud services to handle, process, and analyze the City of Vancouver’s property tax data. The implemented ETL pipeline, combined with detailed data analysis and insightful visualizations, provided stakeholders with actionable insights. These insights can be used to guide future decisions regarding property tax policies and zoning regulations.






## _Project 2 Title: Professional Development Data Analysis Platform for UCW HR Office_

### Objective

&nbsp;&nbsp;&nbsp;The objective of this project was to analyze and manage professional development data for UCW HR Office. The project involved creating a data platform that stores, processes, and provides insights into the university’s professional development activities, tracking employee participation, costs, and compliance with UCW policies.

### Dataset

**_Source:_** Professional Development datasets were downloaded from the ChatGPT.

*Employee IDs:* Unique identifiers for staff.

*Professional Development Activities:* Conferences, courses, and workshops attended.

*Costs:* Costs associated with professional development activities.

*Approval Status:* Whether activities were approved or pending.

*Completion Records:* Proof of completed activities and expenses.

### Methodology

#### 1. Data Collection and Storage

**_Data Acquisition:_** Professional development activity data was collected from UCW HR’s internal systems.

**_Storage Solution:_**

- The dataset was uploaded and stored in AWS S3.

- Data was organized into S3 landing zones, categorized by year and employee department.

- Security: KMS encryption was applied to protect sensitive employee data.

#### 2. Data Cleaning and Transformation

**_Data Preparation Using AWS Glue DataBrew:_**

- Fields like Employee IDs, Professional Development Type, and Costs were standardized.

- A "Year" column was added to facilitate comparisons between 2023 and 2024 datasets.

- Cleaned data was stored in the Raw S3 bucket.

#### 3. ETL Pipeline Design

**_ETL Pipeline Design:_**

- An ETL (Extract, Transform, Load) pipeline was designed using Draw.io to map the data flow from the Landing S3 bucket to the Curated S3 bucket.

- Key transformations included renaming columns for consistency, filtering out unnecessary data, and aggregating the tax levy datasets.

**_ETL Implementation Using AWS Glue:_**

- The ETL pipeline was implemented in AWS Glue to extract data from the Raw S3 bucket, transform it, and load it into the Curated S3 bucket.

#### 4. Data Analysis

**Amazon Athena was used for creating external tables:**

**_SQL Queries:_** SQL was utilized only for creating tables to organize the datasets in Athena and point to the curated data stored in S3.

**_Data Analysis:_**

- Excel was used to analyze trends in professional development activities, costs, and approval rates across departments.

- This analysis allowed UCW HR to identify key areas of spending, compliance, and professional growth for employees.

#### 5. Data Protection and Governance:

**_Data Encryption:_** KMS keys were used to encrypt all data stored in S3.

**_Backup and Replication:_**

- A backup S3 bucket was created to ensure data availability in case of failures.

- Replication rules were applied to securely transfer data between the primary and backup S3 buckets using the same KMS encryption.

- Automated Data Governance: AWS Glue was used to conduct regular data quality checks, with a scheduled automation process ensuring data consistency and accuracy.

#### 6. Data Monitoring

- Amazon CloudWatch and AWS CloudTrail were employed for continuous monitoring and tracking:

- CloudWatch was used to monitor key metrics such as resource consumption and cost estimations.

- CloudTrail tracked all user activities and API calls, storing the logs in S3 for audit purposes.

#### 7. Data  Visualization

**_Visualization Tools:_**

- Excel was utilized to create interactive charts such as pie, bar, and line graphs.

- A dashboard was created to present insights, including professional development costs and trends.

#### 8. Data Publishing:

**_Server Setup:_**

- EC2 Instances were configured to host and publish the processed data and visualizations.

- The processed datasets were made accessible to stakeholders via a web interface hosted on the EC2 instances.

**_Data Storage:_** The transformed data and visual reports were uploaded to Remote access, allowing for easy access and sharing among stakeholders.

### Tools and Technologies

**_AWS Services:_**

- S3: Data storage and management.

- AWS Glue: Data cleaning, transformation, and ETL pipeline implementation.

- Amazon Athena: SQL queries for table creation and dataset management.

- Amazon CloudWatch: System monitoring.

- AWS CloudTrail: Audit logs and user activity tracking.

- KMS Encryption: Data security.

- EC2 Instances: Web hosting and report publishing.
  
**_Data Visualization:_**

- Excel: Used to generate interactive visualizations such as charts and dashboards.

- Draw.io: Used for visualizing the ETL pipeline workflow.

### Additional Tools

**Amazon SageMaker:**

- Used for processing emails and extracting relevant data for table creation.

- SageMaker's machine learning capabilities were applied to identify and structure key information from emails related to professional development activities.

**DynamoDB**

- Structured tables were created in DynamoDB from the extracted email data, allowing for seamless integration into the overall analysis pipeline.

-These tables contained structured data, such as employee professional development requests and related approvals.

### Deliverables

- A complete ETL pipeline implemented using AWS Glue, enabling automated data processing for professional development tracking.

- Interactive Excel dashboards displaying trends in employee participation, professional development costs, and approval status.

- Web-accessible reports hosted on EC2 instances, allowing stakeholders easy access to data insights.

- A comprehensive report summarizing trends, costs, and compliance with professional development policies.

- Tables generated from email data using Amazon SageMaker and DynamoDB, providing an automated method of capturing and organizing professional development requests from employee communications.


### Outcomes and Insights

*_1. Participation Trends:_* Analyzed professional development participation rates by department, identifying areas with higher engagement.

*_Cost Breakdown:_* Provided detailed insights into the financial resources allocated for professional development across different departments and activities.

*_Approval Status:_* Tracked the approval process for professional development requests, offering data-driven suggestions to streamline approvals.

*_Email Data Integration:_* Using Amazon SageMaker and DynamoDB, employee emails related to professional development were automatically processed, structured, and included in the overall analysis, improving the efficiency of data collection and organization.

*_Recommendations:_* Suggested improvements to professional development policies based on the analysis, aimed at increasing engagement and optimizing costs.

### Conclusion

&nbsp;&nbsp;&nbsp;This project successfully built a data platform for the UCW HR Office, enabling the team to track, analyze, and report on professional development activities. By automating data processing and utilizing machine learning through Amazon SageMaker and DynamoDB, the platform delivered improved efficiency in managing professional development requests. Key insights derived from the analysis will help UCW make informed decisions about professional growth, budget optimization, and employee development strategies.


