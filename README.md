# tokyo-olympic-azure-data-engineering-project
Project Overview:


This is an end-to-end data engineering project on the Azure cloud. Where I did data ingestion from GITHUB to Azure Data Lake using Data Factory to transformation using Databricks loading to Synapse, and reporting using Power BI. 

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

   • Create Azure Free Subscription acoount
  
   • Create a Resource Group 'tokyo-olympic-data' to house and manage all the Azure resources associated with this project.
  
   • Within the created resource group,set up a storage account. This is specifically configured to leverage Azure Data Lake Storage(ADLS) Gen2 capabilities.
  
   • Create a Container inside this storage account to hold the project's data. Two directories 'raw-data' and 'transfromed-data' are created to store raw data and transformed data.

![image](https://github.com/user-attachments/assets/4114dedb-d44f-44fc-9370-e3fb73c64c5e)


2.Data Ingestion using Azure Data Factory:

   • Begin by creating an Azure Data Factory workspace within the previously established resource group.
  
   • After setting up the workspace, launch the Azure Data Factory Studio.
  
   • Upload the Tokyo Olympics dataset from kaggle to GitHub.
  
   • Within the studio, initialize a new data integration pipeline. Now use the task Copy Data to move data efficiently between various supported sources and destinations.
  
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





    
