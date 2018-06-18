Here is how to build your first Data Flow:

1. Load the Blob Store with your Data for Transformation. Go to your live ADF service and build a pipeline with a Copy Activity to load data from your sources into Blob Store that you will use for data transformation with Databricks from Data Flow. Schedule the data loading with clock scheduler.

![alt text](https://github.com/kromerm/adfdataflowdocs/blob/master/images/dafl1.png "Step 1")

2. Transform your data in Data Flow from the ADF Preview Service with a new Dataset. In the new ADF Preview Service, build a Data Flow. Create a new Dataset for your source that points to the Blob Store folder and files that you landed from Step 1

3. Graphically build your logical data flow in the data flow designer. For the Sink, land the data back into the Blob Store folders so that you can then load your ADW from this location.

4. Go back to your original V2 factory on the GA service and design a pipeline to load your ADW. Create a Dataset that points to the folder of PART files that were output from your Dataflow execution. Now load your ADW from this folder using Polybase with the Copy Activity.. Execute this pipeline with a file arrival trigger to execute when the blob file from the Data Flow once execution is completed.

