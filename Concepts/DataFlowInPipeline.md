<img src="../images/redf001.png" width="400">

To build a logical data flow, you will use the Reource Explorer on the pipeline builder screen by clicking the plus (+) symbol to create a new Data Flow resource. Data Flows that you author will appear in the Resource Explorer in the Data Flows folder.

<img src="../images/cfdf001.png" width="400">

In order to schedule, manage, monitor and operationalize a Data Flow, you will first build a pipeline. Go to Resource Explorer to select the plus sign again, this time to create a new pipeline resource. Within that pipeline, add a Data Flow activity. Select the Data Flow that you have already built and choose that Data Flow for execution. When the pipeline executes, that Data Flow will execute within the pipeline sequence when the Data Flow activity is reached.

## Data Flows Execute in Azure Databricks

When you add a Data Flow activity to your pipeline, you will be prompted to either select an existing Data Flow defintion or to create a new one. Then, within that activity properties, you must set the Linked Service to point to your Azure Databricks account.

Use the "Existing Cluster" for debugging / designing data flows for a quick and interactive experience. Use the "New Job Cluster" choice for operationalized pipelines that are executing pipelines on a schedule.
