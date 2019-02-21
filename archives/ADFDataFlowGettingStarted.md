# Getting Started with ADF Data Flows for Limited Preview Customers

* [Getting Started with ADF Data Flow ARM Template and Samples](https://www.youtube.com/watch?v=YhpHlyYWCyI)
* [Build your first ADF Data Flow](https://youtu.be/WQ1KqsRL9Bg)

Start by building a new Data Factory with Data Flows from the Azure Portal. Select V2 (data flow preview). Be sure to include the sample Data Flows by checking the "sample" checkbox:

<img src="images/portal.png" width="300">

Once you've gone through building a new Azure Data Factory with the new version that enables Data Flow (use the ARM Template in the Samples directory), you can begin by experimenting with the 3 samples that will be loaded in your Factory from the ARM Template: Taxi Demo, Currency Demo and Movies Demo.

To begin building your first Data Flow from scratch, begin by building a new ADF Pipeline in the Factory. From the Pipeline Builder UI, go to the left-hand resource explorer and click the + sign to build a new Data Flow.

<img src="images/resource1.png" width="400">

In the Data Flow canvas, give your Data Flow a name and start with a Source transform. Every Data Flow must have a least 1 Source to be a valid flow.

Follow the samples or experiment with the different data transformations in the Data Flow canvas. You can add transforms by clicking the + sign that is next to each transform.

End your Data Flow with a Sink to land your transformed data either back in Blob Storage or Azure Data Warehouse.

Click "Validate" to see if you have any configuration errors. If it all checks out clean, then you can either Save your Data Flow, if it is being designed in Git mode, or Publish the changes, if you are designing your work directly against the ADF Service.

Now you're ready to test your Data Flow. From the Pipeline view, add a new Data Flow activity. Select the name of the Data Flow that you just created and use your Azure Databricks account Linked Service. Instructions for how to configure Databricks can be found in the doc "First Data Flow" under Samples.

ADF Data Flow currently only supports Azure Databricks version 5.0

<img src="images/adb50.png" width="300">

<img src="images/pipe1.png" width="400">

You can test your Data Flow from this pipeline with either a Debug run or a Trigger-Now run from the pipeline. Once you are satisified with your results, save or publish the latest changes and you're ready to operationalize your Data Flow.

Scheduling, monitoring and source control is all the same process that ADF already supports. To view the results of Data Flow runs in the ADF Monitor view, be sure to click into the Data Flow activity from your pipeline run view.

<img src="images/mon1.png" width="400">
