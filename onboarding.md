1. Provide your Subscription ID so we can whitelist Data Flow on your sub
2. There is 1 Azure region enabled with the new preview Data Flow ADF service: SE Asia
3. Create a new Data Factory in SE Asia with the ARM Template in the Samples folder. You may use either PowerShell or the Azure Portal to create the factory with this template. Note that there are a number of sample Data Flows in the ARM Template that will get generated in your factory.
4. For the current iteration of Data Flow, your data must be in Blob in order for Databricks to transform the data
5. If your data is not already staged in Blob, start with a Copy Activity in the Pipeline to copy the data you wish to transform into your Blob Store
6. Now create a new Data Flow to transform your data
7. In the Data Flow canvas, create a Linked Service for your Azure Databricks to use for Data Transformations
8. Create Linked Services for the Datasets that you will use for Data Transformation sources and sinks. The Datasets need to point to the Blob Store where your data is being staged.
9. Sink the data in Data Flow to a Blob folder in another Dataset
10. Create a new Data Factory in the ADF GA service with a Copy Activity to pick up that transformed data in Blob and load it into your target data store


Email bugs, requests, questions, etc. to: adfdataflowext@microsoft.com
