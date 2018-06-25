1. Provide your Subscription ID so we can whitelist Data Flow on your sub
2. If your data is not already staged in Blob, create a new Data Factory from the GA service with a Copy Activity to copy your data into Blob
3. Create a new Data Factory in the SE Asia region using the preview ADF service with Data Flow <-- in the template
-- Create Linked Service for Azure Databricks
-- Create Linked Serivce for Azure Blob Storage
4. Transform your data with a Data Flow activity
5. In the Data Flow, create a new Dataset to point to the Blob folder you landed your data into in step #2 (possibly in template)
-- Samples with "happy path" datasets
-- Samples with parameterized Linked Services
6. Sink the data in Data Flow to a Blob folder in another Dataset
7. Create a new Data Factory in the ADF GA service with a Copy Activity to pick up that transformed data in Blob and load it into your target data store
8. Create triggers on the 1st pipeline to schedule the Blob load
9. Create triggers on the preview pipeline using File Arrival trigger when the blob is landed
10. Create triggers on the 3rd pipeline using File Arrival trigger to load data into DW when blob is landed from transformation

Email bugs, requests, questions, etc. to: adfdataflowext@microsoft.com

No AKV Linked Services



