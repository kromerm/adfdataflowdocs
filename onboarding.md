1. Provide your Subscription ID so we can whitelist Data Flow on your sub
2. There is 1 Azure region enabled with the new preview Data Flow ADF service: SE Asia
3. Create a new Data Factory in SE Asia from the Azure Portal. Select the V2 with data flows (preview) version of ADF.
4. If your data is not already staged in Blob, start with a Copy Activity in the Pipeline to copy the data you wish to transform into your Blob Store
5. If you would like to use the Data Flow samples, you will need to upload the Movies, Currency and Taxi data from the sample data folder into a blob store container
5. For the samples, edit the Linked Service that points to the sample blob store folders.
7. Now create a new Data Flow to transform your data
8. In the Data Flow canvas, create a Linked Service for your Azure Databricks to use for Data Transformations
9. Create Linked Services for the Datasets that you will use for Data Transformation sources and sinks. The Datasets need to point to the Blob Store where your data is being staged.
10. Sink the data in Data Flow to a Blob folder in another Dataset
11. Create a new Data Factory in the ADF GA service with a Copy Activity to pick up that transformed data in Blob and load it into your target data store


Email bugs, requests, questions, etc. to: adfdataflowext@microsoft.com
