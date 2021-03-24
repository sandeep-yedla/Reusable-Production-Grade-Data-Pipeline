

####Adding this project again in a new repository


**Data Pipelines for Music Streaming Company**



#Project Description: 
created a reusable production-grade data pipeline that incorporates data quality checks and allows for easy backfills for a music streaming company for a purpose of automation and monitoring to their data warehouse ETL pipelines using Apache Airflow.  

#Data Description:
 The source data resides in S3 and needs to be processed in a data warehouse in Amazon Redshift. The source datasets consist of JSON logs that tell about user activity in the application and JSON metadata about the songs the users listen to.

#Data Pipeline design:
At a high-level the pipeline does the following tasks.
1. Extract data from multiple S3 locations.
2. Load the data into Redshift cluster.
3. Transform the data into a star schema.
4. Perform data validation and data quality checks.
5. Calculate the most played songs for the specified time interval.
6. Load the result back into S3.


#Design Goals:
Based on the requirements of our data consumers, our pipeline is required to adhere to the following guidelines:
* The DAG should not have any dependencies on past runs.
* On failure, the task is retried for 3 times.
* Retries happen every 5 minutes.
* Catchup is turned off.
* Do not email on retry. 

#Pipeline Implementation:

Apache Airflow is a Python framework for programmatically creating workflows in DAGs, e.g. ETL processes, generating reports, and retraining models on a daily basis. The Airflow UI automatically parses our DAG and creates a natural representation for the movement and transformation of data. A DAG simply is a collection of all the tasks you want to run, organized in a way that reflects their relationships and dependencies. A DAG describes how you want to carry out your workflow, and Operators determine what actually gets done. 

