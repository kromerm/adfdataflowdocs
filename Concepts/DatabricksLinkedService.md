Before you can begin executing your Data Flows, you must link to your Azure Databricks account. The best way to configure the Azure Databricks account for your Data Flow is to first create a new pipeline. Drag a Data Flow activity onto the design canvas. Once you've selected a Data Flow, you can create a new Linked Service for Azure Databricks. This identifies the cluster compute environment where your Data Flows will execute.

![Azure Databricks](../images/adb.png "databricks")

Click New to create the new Linked Service.

<img src="../images/dbls001.png" width="200">

1. You must first create an Azure Databricks Workspace: https://docs.microsoft.com/en-us/azure/azure-databricks/quickstart-create-databricks-workspace-portal
2. In the Linked Service definition, either pick the Workspace from your Azure Subscription in the drop-down or manually enter the URL for the workspace
3. Now you must select whether you wish to have ADF Data Flow automatically start-up a job cluster on every Data Flow execution, or do you want to re-use an existing cluster.
4. If you select "New job cluster", Data Flow will startup a new Databricks job cluster on each execution of your data flow. You will incur a spin-up wait time in the neighborhood of 5-7 minutes before your data flow will execute.
5. If you select "Existing Cluster", Data Flow will utilize your existing cluster. For this option, you must provide the Cluster ID for your interactive cluster. In this case, you control the start/stop of your cluster to make it available for data flow.
6. When selecting "New job cluster", choose 4.1 for Cluster Version and Standard_DS4_v2 for Cluster Node type.
7. You can choose the min/max workers and Autoscaling based on your requirements.

**For designing, debugging Data Flows interactively, we suggest using the BYOC or "Existing Cluster" option. This way, the cluster is already warm and Data Flows can execute immediately. For operationalized, scheduled pipelines with Data Flows, the "New Cluster" option will work fine because you won't be impacted by the 5-7 minute spin-up time for a new job cluster when you schedule your Data Flow jobs nightly**
