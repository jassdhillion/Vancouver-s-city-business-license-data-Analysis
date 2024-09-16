# Vancouver's City License issuing services Data Analysis; The project is composed of an analyses concerning business license issued to business owners in the Vancouver's License office. The aim of the project was to improve animal services and its composed of two key dataset; a. from 2023( before new categories were introduced) and b. from 2024( after introduction of the streamlining category). The goal of the project was to discover how the new categories impacted licnese distribution in Vancouver and to also offer new insights to the stakeholders.
Objectives; to examine the transition of license category from old to the new version, to analyze the distribution of licenses in the new category, and to provide insights on how businesses adopted to the new category of business licensing.
The following steps were involved in the project;
Data collection and storage, this step entailed collecting data from open portal from Vancouver city and storing the data in AWS S3 bucket and cleaning it
Data ingestion, this entailed uploading data for 2023 and 2024 using AWS glue databrew
Data cleaning and structuring, this step enated cleaning data, for example filling missing value, converting data formats, data correction, and renaming collumns
![image](https://github.com/user-attachments/assets/3c92f29b-a25f-4f1e-bb21-cbfeb18da4d5)
Data pipeline design, extract, transform, and load (ETL)pipeline was used to merge data from both years and group the licenses. This also helps to filter unnecessary data
![image](https://github.com/user-attachments/assets/3710ef2e-3fd1-4989-9a11-e9f8ffa36c38)
Data Analysis, this was the fifth step in the project and because Athena had issues, analysis was done through excel. The CSV files were downloaded for analysis and trends were shown through graphs
![image](https://github.com/user-attachments/assets/732cb374-5029-4e51-bdf9-08d1e22c2584)
Data publishing , this was the final step in this project which entailed hosting the dataon AWS EC2 to display the analysis output. 
Tools used; ASW S3 was used to retrieve and store data, AWS Glue Databrew was used to prepare and clean data, Excel was used to generate graphs and data visualization, AWS EC2 was used for web server setup to help in the publication of the project, and Python/SQL was used for scripting and processing data where applicable
Results; there was significant changes in how licenses were distributed in the streamlined license category which can help with providing insights for future mitigations for licensing that would improve animal services
