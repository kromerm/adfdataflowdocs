* Azure Key Vault Not Supported for Linked Services
* Only SE Asia region is supported for Data Factory with Data Flow. This is for the metadata service only. Your data, resource groups, blob stores and Azure Databricks account can reside in any region.
* No portal support for creating factory. Use ARM Template or PowerShell to create factory.
* Blob Store is the only Source supported at this time
* Treat Blob Store as your "staging area" for cooking data in Databricks for transformation. Move your data into this blob staging area using Copy Activity first, if needed.
* Blob & Azure Data Warehouse are currently the only Sinks supported at this time
* Debug in Data Flow is not yet enabled. For now, Debug Data Flows by adding a Data Flow activity to a pipeline and debug from pipeline.
* Data Flow uses Azure Databricks as the execution engine. You must stand-up an Azure Databricks workspace first for Data Flow to work.
* The Microsoft Azure Data Factory team will push frequent updates to the service. This can result in interuptions in the service and can invalidate Data Factories that you've built with this ADF version.
* Factories built on this new ADF version with Data Flows enabled are NOT to be used in production environments.
* There is no Azure SLA associated with the prviate preview of Data Flow in ADF.
* All questions, requests and support must go through this email alias: adfdataflowext@microsoft.com 
