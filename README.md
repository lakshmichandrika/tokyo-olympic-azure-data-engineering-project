# Tokyo-olympic-azure-data-engineering-project
Project Overview:


This is an end-to-end data engineering project on the Azure cloud. Where I did data ingestion from GITHUB to Azure Data Lake using Data Factory to transformation using Databricks loading to Synapse, and reporting using Power BI. 

Based on the data source from Kaggle for the 2021 Olympics in Tokyo¹, here is a business requirement outline:

### Business Requirements

1. **Athlete Performance Analysis**:
   - **Objective**: Analyze the performance of athletes across different sports and events.
   - **Metrics**: Medals won, personal bests, and records set.

2. **Country Performance Comparison**:
   - **Objective**: Compare the performance of different countries.
   - **Metrics**: Total medals, gold medals, and overall ranking.

3. **Event Popularity**:
   - **Objective**: Determine the popularity of various sports and events.
   - **Metrics**: Number of participants, audience size, and social media mentions.

4. **Gender Participation**:
   - **Objective**: Analyze gender participation across different sports.
   - **Metrics**: Number of male and female athletes, medals won by gender.

5. **Historical Comparison**:
   - **Objective**: Compare the 2021 Olympics data with previous Olympics.
   - **Metrics**: Improvement in performance, changes in participation, and medal trends.

### Non-Functional Requirements

1. **Data Aggregation**:
   - **Requirement**: Pre-aggregate data to improve performance.
   - **Implementation**: Aggregate data by year, month, and event.

2. **Efficient Data Retrieval**:
   - **Requirement**: Enable efficient reading of specific data subsets.
   - **Implementation**: Use indexing and partitioning strategies.

3. **Scalability**:
   - **Requirement**: Ensure the system can handle large datasets.
   - **Implementation**: Use scalable storage and processing solutions.

4. **Data Visualization**:
   - **Requirement**: Provide intuitive and interactive visualizations.
   - **Implementation**: Use dashboards and visual analytics tools.

By focusing on these areas, the analysis can provide valuable insights and help improve the overall performance and engagement in future Olympic events.


Project Goals:


    •	Establish a connection between GITHUB and Azure cloud.

    •	Ingest tables into the Azure Data Lake Storage.

    •	Apply data cleaning and transformation using Azure Databricks.

    •	Utilize Azure Synapse Analytics for loading clean data.

    •	Create interactive data visualizations and reports with Microsoft Power BI.


Project Architecture:


You can find the detailed information on the diagram below:

![image](https://github.com/user-attachments/assets/3a18cc2d-d7c2-4325-b075-61ddeea9f5b8)


Dataset Used:


This contains the details of over 11,000 athletes, with 47 disciplines, along with 743 Teams taking part in the 2021(2020) Tokyo Olympics. This dataset contains the details of the Athletes, Coaches, Teams participating as well as the Entries by gender. It contains their names, countries represented, discipline, gender of competitors, name of the coaches.

Source(Kaggle): [2021 Olympics in Tokyo](https://www.kaggle.com/datasets/arjunprasadsarkhel/2021-olympics-in-tokyo)

Technologies Used:


    •	Data Source: GITHUB

    •	Orchestration: Azure Data Factory

    •	Transformation: Azure Databricks

    •	Security: App Registrations

    •	Storage: Azure Data Lake Gen2

    •	Analytics: Azure Synapse Analytics

    •	Data Visualization: PowerBI

Prerequisite:

    • Azure account with active subscription

    • Databricks community edition account

    • Knowledge about storage account, dataframe, azure data factory, sql stc.


1.Initial Set-up:

   • Create Azure account
  
   • Create a Resource Group 'tokyo-olympic-data' to house and manage all the Azure resources associated with this project.
  
   • Within the created resource group,set up a storage account. This is specifically configured to leverage Azure Data Lake Storage(ADLS) Gen2 capabilities.
  
   • Create a Container inside this storage account to hold the project's data. Two directories 'raw-data' and 'transfromed-data' are created to store raw data and transformed data.

![image](https://github.com/user-attachments/assets/4114dedb-d44f-44fc-9370-e3fb73c64c5e)


2.Data Ingestion using Azure Data Factory:

   • Begin by creating an Azure Data Factory workspace within the previously established resource group.
  
   • After setting up the workspace, launch the Azure Data Factory Studio.
  
   • Upload the Tokyo Olympics dataset from kaggle to GitHub.
  
   • Within the studio, initialize a new data integration pipeline. Now use the Copy Data activity to move data efficiently between various supported sources and destinations.
  
   • Configuring the Data Source with HTTP template as we are using http request to get the data from GitHub repo.
  
   • Establishing the Linked Service for source.
  
   • Configuring the File Format for and setting up the Linked Service Sink.
  
   • Repeat above steps to load all other datasets.
  
   • You can connect all the copy data activity together and run them all at once.
  
   • You can use Manual (or) Scheduled Trigger to run this Pipeline.

![image](https://github.com/user-attachments/assets/1319dad0-ea8f-4d59-983d-930b981dbf49)


3. After the pipeline completes its execution, navigate to your Azure Data Lake Storage Gen2. Dive into the "raw_data" folder and validate that the files, like "athletes.csv", "medals.csv", etc., are present and populated with the expected data.

4. Data Transformation using Azure Databricks:

   • Navigate to Azure Databricks within the Azure portal and create a workspace within the previously established resource group and launch it.
   
   • Configuring Compute in Databricks
   
   • Create a new notebook within Databricks and rename it appropriately, reflecting its purpose or the dataset it pertains to.
   
   • Establishing a Connection to Azure Data Lake Storage (ADLS)
   
   • Using the credentials (Client ID, Tenant ID, Secret), write the appropriate code in the Databricks notebook to mount ADLS.
   
   • Writing Data Transformations mount ADLS Gen2 to Databricks.
   
   • Writing Transformed Data to ADLS Gen2.

![image](https://github.com/user-attachments/assets/d77a625d-385e-42ef-822e-a6d0453e3f7b)


5.Setting Up and Using Azure Synapse Analytics:

   • Creating a Synapse Analytics Workspace.
   
   • Within Workspace navigate to the "Data" section , choose "Lake Database" and create a Database "TokyoOlympicDB"
   
   • Creating Table from Data Lake from the Transformed Data folder within your ADLS Gen2 storage.
   

![image](https://github.com/user-attachments/assets/1d3591a5-aae6-4fc8-94f4-e9429e3e42b5)


6.Performing Data Analysis on the Data:

Create SQL script to Perform Exploratory data analysis using SQL. You can aslo use PowerBI to generate your analysis reports.

![image](https://github.com/user-attachments/assets/f58dc9ad-cd09-40e7-a7c3-158415c95e51)


Power BI Dashboard:

![image](https://github.com/user-attachments/assets/4fec0f44-46b9-4da7-af4b-bb6506eb37b1)


### Conclusion

Based on the analysis of Olympics in Tokyo data, here are the key conclusions:

1. **Athlete Performance**:
   - The data reveals significant insights into athlete performance across various sports and events. By analyzing metrics such as medals won, personal bests, and records set, we can identify top-performing athletes and sports.

2. **Country Performance**:
   - Comparing the performance of different countries shows which nations excelled in specific sports. Metrics like total medals, gold medals, and overall ranking provide a clear picture of each country's success.

3. **Event Popularity**:
   - The popularity of different sports and events can be gauged by the number of participants, audience size, and social media mentions. This helps in understanding which sports attracted the most attention and engagement.

4. **Gender Participation**:
   - Analyzing gender participation highlights the distribution of male and female athletes across sports. This includes the number of athletes and medals won by gender, providing insights into gender equality in sports.

5. **Historical Comparison**:
   - Comparing the 2021 Olympics data with previous Olympics allows us to see trends and improvements in performance, participation, and medal counts over time.


By leveraging these insights, stakeholders can make informed decisions to enhance athlete performance, increase engagement, and promote equality in future Olympic events.




    
