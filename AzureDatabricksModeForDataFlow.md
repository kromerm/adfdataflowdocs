## There are 2 modes that ADF Data Flow will use to execute your Data Flows on Azure Databricks: New Job Cluster and Existing Cluster.

### New Job Cluster

Use this mode when you have completed building and testing your Data Flow. This mode directs ADF to spin-up a new Azure Databricks job cluster on every exeuction of your Data Flow. It works well in operationalized ADF pipelines where Data Flow is an activity within that pipeline which can be scheduled to run on a calendar or event. This way, you do not incur the costs of the Azure Databricks cluster running without activity since ADF only spins-up the job cluster on demand. However, you must allow the cluster to warm-up, which can take 5-7 minutes in most cases.

<img src="images/existingcluster.png" width="400">

### Existing Cluster

The spin-up time of the "New Job Cluster" mode above does not work well with debugging due to the spin-up delay. Therefore, we recommend using the "Existing Cluster" option when debugging, building, designing Data Flows.

#### Cluster ID

There is an additional option in the Azure Databricks Linked Service that you must set when using an existing cluster. You will need to point Data Flow to the cluster that you wish to use. For this, go to your Azure Databricks workspace in Azure and find the "Tags" section at the bottom of the page. There you will see a field called "Cluster ID". Copy and paste that into the Cluster ID field in the Linked Service.

<img src="images/tags1.png" width="400">

**NOTE: If your Azure Databricks cluster is failing when running your cluster, check the cluster error logs to see if you do not have enough cores / vCPUs enabled on your subscription. [Click here for details on the Azure Databricks cores limitation](https://github.com/kromerm/adfdataflowdocs/blob/master/Help-Databricks-NoMoreCores.md)**
