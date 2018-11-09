# ADF Data Flow Linked Services

Before you can begin debugging or executing your Data Flows, you must link to your Azure Databricks account. You can create new Azure Databricks Linked Services from the Connections section in the ADF UI or when you add a Data Flow activity to the Pipeline canvas. Choose New > Linked Service.

## Azure Databricks Linked Service

<img src="../images/dbls001.png" width="400">

For designing, debugging Data Flows interactively, you must use the "Existing Cluster" option so that ADF can use an Azure Databricks interactive cluster. This way, the cluster is already warm and Data Flows can execute immediately. For operationalized, scheduled pipelines with Data Flows, the "New Cluster" option will work fine because you won't be impacted by the 5-7 minute spin-up time for a new job cluster when you schedule your Data Flow jobs nightly

In the Linked Service definition, either pick the Workspace from your Azure Subscription in the drop-down or manually enter the URL for the workspace.

You will need to provide the access token key for your Azure Databricks account so that we can connect to your clusters for execution of your Data Flows.

<img src="../images/accesstoken.png" width="400">

[Click here for more details on obtaining Azure Databricks access key tokens](https://docs.databricks.com/api/latest/authentication.html#generate-token)

You must then select whether you wish to have ADF Data Flow automatically start-up a job cluster on every Data Flow execution, or do you want to re-use an existing cluster.

If you select "New job cluster", Data Flow will startup a new Databricks job cluster on each execution of your data flow. You will incur a spin-up wait time in the neighborhood of 5-7 minutes before your data flow will execute.

If you select "Existing Cluster", Data Flow will utilize your existing cluster. For this option, you will choose the Cluster Name from the list. This is the name you gave to your interactive cluster. In this case, you control the start/stop of your cluster to make it available for data flow.

[This will walk you through creating a new Interactive Cluster on Azure Databricks to use as your execution environment for ADF Data Flow debug sessions] (https://docs.azuredatabricks.net/user-guide/clusters/create.html)
