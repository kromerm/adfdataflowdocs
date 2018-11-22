# What is Data Flow in Azure Data Factory?

Data Flow is a new feature, currently in limited preview, that sits inside of ADF and allows you to develop graphical data transformation logic that can be executed as activities within ADF Pipelines at scale using Spark.

The intent of ADF Data Flow is to provide a fully visual experience with no coding required. Your Data Flows will execute on your own Azure Databricks cluster for scaled-out data processing using Spark. ADF handles all of the code translation, Spark optimization and execution of your data flow jobs.

Start by creating data flows, then add a Data Flow activity to your pipeline to execute and test your data flow in Debug mode in the pipeline or use "Trigger Now" in the pipeline to test your Data Flow from a pipeline Activity.

You will then operationalize your Data Flow by scheduling and monitoring your ADF pipeline that is executing the Data Flow activity.

There is also a Debug Mode toggle switch on the Data Flow design surface to allow you to interactively build your data transformations in an interative data prep environment.

ADF Data Flow has line-of-sight to 5 primary "staging" areas within Azure to perform your data transformations: Azure Blob, ADLS Gen 1, ADLS Gen 2, Azure SQL DB and Azure SQL DW. ADF has access to nearly 80 different native connectors, so to include those other sources of data into your Data Flow, first stage that data into one of those 5 primary Data Flow staging areas using the Copy Activity:

* [ADF Data Flow: Staging Data](https://www.youtube.com/watch?v=zukwayEXRtg)
