1. Not all properties in the Dataset definitions will be supported by the Data Flow source & sink transforms
2. All data must first be landed in Blob Store
3. An early version of the ADW sink will support only mapping to existing tables as INSERT
4. For BYOC Databricks clusters: Frequent updates to the ADF Data Flow drivers on the Azure Databricks cluster will require cluster restarts
5. ADF will notify you when an update has been pushed to the Databricks driver, requiring a cluster restart
