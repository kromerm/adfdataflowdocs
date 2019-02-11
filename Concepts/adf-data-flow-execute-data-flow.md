<img src="../images/redf001.png" width="400">

To build a logical data flow, you will use the Reource Explorer on the pipeline builder screen by clicking the plus (+) symbol to create a new Data Flow resource. Data Flows that you author will appear in the Resource Explorer in the Data Flows folder.

<img src="../images/cfdf001.png" width="400">

In order to schedule, manage, monitor and operationalize a Data Flow, you will first build a pipeline. Go to Resource Explorer to select the plus sign again, this time to create a new pipeline resource. Within that pipeline, add a Data Flow activity. Select the Data Flow that you have already built and choose that Data Flow for execution. When the pipeline executes, that Data Flow will execute within the pipeline sequence when the Data Flow activity is reached.

## Execute Data Flow Activity in Preview Service

When you add a Data Flow activity to your pipeline, you will be prompted to either select an existing Data Flow defintion or to create a new one. Then, within that activity properties, you must set the Linked Service to point to your Azure Databricks account.

Use the "Existing Cluster" for debugging / designing data flows for a quick and interactive experience. Use the "New Job Cluster" choice for operationalized pipelines that are executing pipelines on a schedule.

You will also need to point to an Azure Blob Storage that we can use as a staging area for data transformation. Use a Linked Service for Azure Blob and then enter your container/folder name for a staging location.

<img src="../images/newdataflowactivity.png" width="400">

## Execute Data Flow Activity in ADF V2

If you are using the public ADF V2 version of Data Flows, you will not require a Linked Service because ADF will execute the Data Flow on internal ADF-managed Azure Databricks clusters.

1. Select the Azure Integration Runtime to define the region location of the ADF compute you'd like to use for the data flow execution. Currently, only the auto-resolve IR is supported. This means that ADF will utilize the Databricks cluster in the same region as your Factory.

2. Choose the compute type. Choose Compute Optimized for large datasets, General Purpose for general workloads, or Memory Optimized for data flows that rely heavily on aggregations and computations.

3. Select the Core Count to determine how many scale-out cores of Spark that ADF should use to execute your Data Flow.

<img src="../images/azureir1.png" width="400">
