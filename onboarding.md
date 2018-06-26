1. Provide your Subscription ID so we can whitelist Data Flow on your sub
2. There is 1 Azure region enabled with the new preview Data Flow ADF service: SE Asia
3. Create a new Data Factory in SE Asia with the ARM Template in the Samples folder. You may use either PowerShell or the Azure Portal to create the factory with this template.
3. For the current iteration of Data Flow, your data must be in Blob in order for Databricks to transform the data
4. If your data is not already staged in Blob, create a new Data Factory from the GA service with a Copy Activity to copy your data into Blob
3. Create a new Data Factory in the SE Asia region using the preview ADF service with Data Flow. For now, new factories in the Data Flow preview service must be created from PowerShell or ARM Template. Please find an ARM Template that you can use in the samples directory.
4. Create a Linked Service for your Azure Databricks to use for Data Transformations
5. Create Linked Services for the Datasets that you will use for Data Transformation sources and sinks
6. Transform your data with a Data Flow activity
7. In the Data Flow, create a new Dataset to point to the Blob folder you landed your data into in step #2 (possibly in template)
8. You will find samples in the ARM Template for Data Flows that you can start from
9. Sink the data in Data Flow to a Blob folder in another Dataset
10. Create a new Data Factory in the ADF GA service with a Copy Activity to pick up that transformed data in Blob and load it into your target data store
11. Create triggers on the 1st pipeline to schedule the Blob load
12. Create triggers on the preview pipeline using File Arrival trigger when the blob is landed
13. Create triggers on the 3rd pipeline using File Arrival trigger to load data into DW when blob is landed from transformation

Email bugs, requests, questions, etc. to: adfdataflowext@microsoft.com
