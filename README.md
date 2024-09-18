
# Vancouver's City License issuing services Data Analysis; 
1. **Descriptive Analysis**: this project provides insights concerning the current state of business licenses in Vancouver city under the new streamlined categories. The scope involved examining the number of licenses that are in old and new category and evaluate the impacts of each category changes on the businesses and their license renewals. 
2. **Aims**: the aim of the project was to improve animal services and its composed of two key dataset; a. from 2023( before new categories were introduced) and b. from 2024( after introduction of the streamlining category). 
3. **Project's goal(s)**: the goal of the project was to discover how the new categories impacted license distribution in Vancouver and to also offer new insights to the stakeholders.
4. **Objectives**; to examine the transition of license category from old to the new version, to analyze the distribution of licenses in the new category, and to provide insights on how businesses adopted to the new category of business licensing.
## The following steps were involved in the project;
1. **Data collection and storage**: this step entailed collecting data from open portal from Vancouver city and storing the data in AWS S3 bucket and cleaning it
   + data were gathered from Vancouver city in an open data portal
   + Data on business license ofr 2023 and 2024 was downloaded
   + the dataset were uploaded to AWS using the standard storage level
   + The data was secured in a folder structure that hold raw, cleaned and processed data
3. **Data ingestion**: it is a procedure used in the project to help in uploading the dataset for 2023 and 2024 regarding business licenses to AWS S3 bucket. I used AWS Glue Databrew to process data files for further analysis
4. **Data cleaning and structuring**:this step entailed cleaning data through different procedures such as;
   - for example filling missing value
   - converting data formats,
   - data correction,
   - and renaming collumns
     
![image](https://github.com/user-attachments/assets/3c92f29b-a25f-4f1e-bb21-cbfeb18da4d5)

 **Data pipeline design**: extract, transform, and load (ETL)pipeline was used to merge data from both years and group the licenses. This also helps to filter unnecessary data
   
![image](https://github.com/user-attachments/assets/3710ef2e-3fd1-4989-9a11-e9f8ffa36c38), 

 **Data Analysis**: this was the fifth step in the project and because Athena had issues, analysis was done through excel. The CSV files were downloaded for analysis and trends were shown through graphs
   
![image](https://github.com/user-attachments/assets/ab44f174-8a60-4257-9627-4e70c9670b95)

![image](https://github.com/user-attachments/assets/2cb6785e-aed3-473e-891b-27c1760f29e5)

 **Data publishing**:this was the final step in this project which entailed hosting the dataon AWS EC2 to display the analysis output. 
 **Tools used**; ASW S3 was used to retrieve and store data, AWS Glue Databrew was used to prepare and clean data, Excel was used to generate graphs and data visualization, AWS EC2 was used for web server setup to help in the publication of the project, and Python/SQL was used for scripting and processing data where applicable

   ![image](https://github.com/jassdhillion/Vancouver-s-city-business-license-data-Analysis/blob/main/Screenshot%202024-08-24%20204933.png)
![image](https://github.com/user-attachments/assets/08647563-e3d3-4b20-88ae-1d87db9f1531)

**Data Protection** 
Ensuring the security of the business license dataset is crucial, given the sensitive nature of the information, such as business addresses and license numbers. The following key components were implemented to guarantee data confidentiality, integrity, and availability:
1.	Data Confidentiality and Integrity
To protect sensitive business information, all data is encrypted in transit and at rest using AWS Key Management Service (KMS). The encryption of data stored in S3 buckets ensures that unauthorized access is prevented, including from the cloud service provider’s personnel.
•	Symmetric Encryption: Symmetric encryption has been selected to streamline the process for authorized users. This eliminates the need for separate private key management while ensuring secure data access for City of Vancouver employees.  the default encryption enabled for the dataset stored in the S3 bucket, which is used to store business license records.
![image](https://github.com/user-attachments/assets/08647563-e3d3-4b20-88ae-1d87db9f1531)
•	Custom Encryption Key: A custom encryption key was created to protect the dataset instead of using AWS’s default encryption. This key is restricted to authorized DAP users (City employees managing the dataset) and cannot be accessed by unauthorized individuals. This is critical for ensuring that only the City of Vancouver employees responsible for data management have control over encryption processes, further reducing the risk of data breaches. the custom encryption key used for the dataset.
![image](https://github.com/user-attachments/assets/08647563-e3d3-4b20-88ae-1d87db9f1531)
2.	Data Availability
To ensure data availability in case of accidental deletion, unauthorized modification, or data corruption, the following strategies were implemented:
•	Data Replication and Versioning: The business license data is automatically replicated into a separate backup S3 bucket. Versioning is enabled to store multiple versions of each data object, meaning that each time a data object is updated, a new version is created and stored. This ensures that previous versions of the dataset can be retrieved if needed. Figure 3 shows the replication rules applied to the main S3 bucket, ensuring that all data changes are backed up automatically.
•	Backup Encryption: To ensure that the replicated backup data is secure, the backup S3 bucket is also encrypted using the same encryption key as the primary data bucket. This measure ensures that backup data is protected from unauthorized access in the same way as the primary data.  the encryption settings for the backup bucket, demonstrating that the backup is equally secure.
By implementing encryption, replication, and versioning, the business license data is fully protected from both internal and external threats. This ensures that the dataset remains secure, accessible, and reliable always.
![image](https://github.com/user-attachments/assets/08647563-e3d3-4b20-88ae-1d87db9f1531)
![image](https://github.com/user-attachments/assets/08647563-e3d3-4b20-88ae-1d87db9f1531)
**Data Governance**  
Data governance is essential for ensuring the privacy, quality, and regulatory compliance of the business license data, particularly after the City of Vancouver’s May 6, 2024, update, which streamlined business license categories into fewer than 100. The following processes were implemented to maintain the integrity and usability of the dataset:
1.	Privacy Management
Given the inclusion of sensitive data (e.g., business addresses for home-based businesses), it is crucial to ensure that private information is protected:
•	Data Anonymization: The ETL pipeline built with AWS Glue automatically scans the dataset for sensitive data, such as personal business addresses, which are excluded from public view to comply with privacy regulations. The ETL process replaces sensitive values with anonymized data (e.g., "***" in place of private addresses). This ensures that the data remains compliant with data privacy laws, such as Canada’s Personal Information Protection and Electronic Documents Act (PIPEDA).
•	Regular Privacy Audits: The ETL job is scheduled to run weekly and scan the data for sensitive information to ensure that any new entries meet privacy criteria.
the ETL pipeline configured to perform data anonymization tasks, ensuring that sensitive business information is protected.
![image](https://github.com/user-attachments/assets/08647563-e3d3-4b20-88ae-1d87db9f1531)

3.	Data Quality Management
Maintaining high-quality data is essential for ensuring accurate reporting and decision-making by City officials. The following quality checks are automated through the ETL pipeline:
•	Completeness: The ETL pipeline ensures that critical fields, such as Business Type, License Number, and Issue Date, are populated. A completeness rule checks that no more than 5% of these fields contain null values. Data records that do not meet this threshold are flagged for review or excluded from further processing.
•	Freshness: Business licenses should be relevant and up to date. The ETL job checks the freshness of records by verifying that license data from 2024 is no older than 365 days up to 720 days. Records outside this range are flagged for further inspection, ensuring that only current business licenses are used in decision-making processes.
•	Validity: Fields like Business Type are validated to ensure they correspond to the new streamlined categories introduced post-May 6, 2024. This ensures that all business licenses are classified correctly under the new system, preventing errors in the dataset.
•	Uniqueness: License numbers should be unique. The ETL checks for any duplicate license numbers to avoid duplication and confusion in the dataset. Any identified duplicates are reported for manual investigation.
the data quality rules applied to the 2023 and 2024 datasets, respectively. Data that passes these quality checks is stored in the trusted zone, while any data that fails is excluded from further analysis.
•	Automated Governance: To ensure that privacy and quality checks are consistently applied, these ETL jobs are automatically executed every Monday at 23:59.
 the workflow schedule for these ETL jobs, ensuring the city has high-quality, anonymized data available always.
![image](https://github.com/user-attachments/assets/08647563-e3d3-4b20-88ae-1d87db9f1531)
![image](https://github.com/user-attachments/assets/08647563-e3d3-4b20-88ae-1d87db9f1531)
![image](https://github.com/user-attachments/assets/08647563-e3d3-4b20-88ae-1d87db9f1531)
![image](https://github.com/user-attachments/assets/08647563-e3d3-4b20-88ae-1d87db9f1531)
![image](https://github.com/user-attachments/assets/08647563-e3d3-4b20-88ae-1d87db9f1531)
![image](https://github.com/user-attachments/assets/08647563-e3d3-4b20-88ae-1d87db9f1531)
**Data Monitoring**
Effective data monitoring ensures that the DAP is running smoothly, costs are controlled, and any issues with usage or user activity are detected promptly. Monitoring is divided into three key aspects:
1.	Usage and Cost Monitoring
AWS CloudWatch is used to monitor the platform’s resource usage and associated costs. A custom CloudWatch dashboard tracks the following:
•	S3 and Glue Costs: The dashboard provides a breakdown of costs associated with data storage in S3 and data processing via AWS Glue. This allows the City to track monthly spending trends and optimize resource allocation as needed.
 the CloudWatch dashboard monitoring costs.
![image](https://github.com/user-attachments/assets/08647563-e3d3-4b20-88ae-1d87db9f1531)

•	Data Storage Usage: The dashboard also tracks the size of the S3 buckets, providing insight into how much data is being stored and the rate at which the dataset is growing. This helps the City manage its storage resources efficiently.
•	Alarms for Cost Control: An alarm is set to trigger an SNS notification when the DAP’s monthly costs exceed $35. This alarm sends an email to the City’s data manager, enabling prompt action if spending increases unexpectedly. 
the configuration of the SNS alarm.
![image](https://github.com/user-attachments/assets/08647563-e3d3-4b20-88ae-1d87db9f1531)
2.	User Activity Monitoring
AWS CloudTrail is configured to log user activity across the DAP, ensuring that all actions—such as data uploads, license updates, and configuration changes—are tracked. The following activities are monitored:
•	Read and Write Operations: CloudTrail logs any read or write operations performed on the business license dataset, ensuring that all data access is recorded for audit purposes.
•	Management Events: CloudTrail also logs all management events, such as creating or deleting resources, to ensure full visibility into the platform’s operations.
the CloudTrail configuration.
![image](https://github.com/user-attachments/assets/08647563-e3d3-4b20-88ae-1d87db9f1531)
•	Log Storage and Encryption: CloudTrail logs are stored in a dedicated, encrypted S3 bucket. The logs are critical for tracking user behavior and ensuring compliance with regulatory requirements. 
the S3 bucket where these logs are securely stored.
![image](https://github.com/user-attachments/assets/08647563-e3d3-4b20-88ae-1d87db9f1531)

