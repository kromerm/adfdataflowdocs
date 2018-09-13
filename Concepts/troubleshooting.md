  ADF Data Flow will execute your Data Flow activities on your Databricks cluster, that you've defined via Linked Service.
  
  When running Debug or Pipeline runs in ADF with Data Flows, you will be able to track the job execution on your Azure DAtabricks cluster.
  
  When troubleshooting Data Flow issues, the information that Microsoft will require for RCA and resolution include:
  
  1. Copy / sample of the source data
  2. Logs from the Azure Databricks cluster, look under "Jobs" in Azure Databricks workspace (Log4j output)
  3. The pipeline runID
  4. The Data Flow activity RunID
  5. The DSL from your Data Flow (show the DSL button on Data Flow canvas by adding "&feature.dataflow=true" to the end of the URL
  
**NOTE on Azure Databricks Capacity: If your Azure Databricks cluster is failing when running your cluster, check the cluster error logs to see if you do not have enough cores / vCPUs enabled on your subscription. [Click here for details on the Azure Databricks cores limitation](https://github.com/kromerm/adfdataflowdocs/blob/master/Help-Databricks-NoMoreCores.md)**
