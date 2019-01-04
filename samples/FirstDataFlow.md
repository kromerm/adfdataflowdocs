Get started with your first ADF Data Flow by first building a new Factory in the SE Asia region using the ARM Template in the Samples folder.

The simplest way to do this is to [CLICK HERE](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fkromerm%2Fadfdataflowdocs%2Fmaster%2Fsamples%2Fcurrent_df_arm_template.json) to build your first sample ADF Data Flow Factory with our ARM Template.

You can use PowerShell or the Azure Portal Template Deploymnet mechanism to build the factory from the ARM Template. For Private Preview, use the "SE Asia" region, enter "southeastasia" for the Location field in the ARM Template parameters.

When filling-out the parameter fields for the ARM Template, you are only required to complete the Resource Group, Factory Name, Linked Services connection string and Azure Databricks key fields (i.e. all fields with a red \*). To generate a key for your Azure Databricks account, visit the Azure Databricks workspace page under "User Settings > Generate New Token":

<img src="../images/gentoken.png" width="400">

To get the Linked Service connection string for your Azure Blob storage, visit the "Access Keys" section in the Azure Portal for your Storage account. This is where you will store the sample data files.

<img src="../images/storeage.png" width="400">

The Sample Data folder here in this Github repo contains all of the data files for the demos. In your Azure Storage Account, make sure to first create a container called "demo". This ARM Template assumes that you have a container called "demo".

You will see a series of sample Pipeleines, Datasets, Linked Services and Data Flows to get you started:

<img src="../images/template1.png" width="400">

You will need to also configure your Azure Databricks account before you can submit Data Flows for execution. First, build an Azure Databrick workspace and then grab the Access Token to enter into the ADF Linked Service for Azure Databricks. If you choose "create new cluster", ADF will spin-up a new job cluster for every execution of your data flow. You will incur approximtely 5 minutes of start-up time for the cluster to become ready. If you choose "existing cluster", you can control the start/stop actions on your own Azure Databricks cluster. Copy the cluster ID from your cluster and paste it in the Cluster ID field in the Linked Service.
