# What is Data Flow in Azure Data Factory?

Data Flow is a new feature inside of ADF that allows you to develop graphical data transformation logic that can be executed as activities within ADF Pipelines.

The intent of ADF Data Flow is to provide a fully visual experience with no coding required. Your Data Flows will execute on your own Azure Databricks cluster for scaled-out data processing using Spark. ADF handles all of the code translation, Spark optimization and execution of your data flow jobs.

Start by creating data flows, then add a Data Flow activity to your pipeline to execute and test your data flow in Debug mode in the pipeline or use "Trigger Now" in the pipeline to test your Data Flow from a pipeline Activity.

You will then operationalize your Data Flow by scheduling and monitoring your ADF pipeline that is executing the Data Flow activity.

