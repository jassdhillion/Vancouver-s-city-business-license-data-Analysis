
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
   
![image](https://github.com/user-attachments/assets/08647563-e3d3-4b20-88ae-1d87db9f1531)

 **Results**; there was significant changes in how licenses were distributed in the streamlined license category which can help with providing insights for future mitigations for licensing that would improve animal services
