Q: Which ADF version do I use to create Data Flows?

Use the ADF V2 version to create Data Flows
  
Q: I was a previous private preview customer using Data Flows and I used the ADF V2 w/Data Flows preview version

This version is now obsolete. Use ADF V2 for Data Flows
  
Q: What has changed from private preview to limited public preview in Data Flows?

You will no longer have to bring your own Databricks clusters. ADF will manage cluster creation and tear-down. Blob datasets and ADLS datasets are separated into Delimited Text and Parquet datasets. You can still use ADLS & Blob Store to store those files. Use the appropriate Linked Service for those storage engines.

Q: Can I migrate my private preview factories to ADF V2?

[Yes, follow the instructions here](https://www.slideshare.net/kromerm/adf-mapping-data-flow-private-preview-migration)

Q: I need help troubleshooting my data flow logic, what do you need?

When Microsoft provides help or troubleshooting with Data Flows, please provide the "DSL Code Plan". To do this, follow these steps:

* From the Data Flow Designer, click "Code" in the top-right corner. This will display the editable JSON code for the data flow.
* From the code view, click "Plan" on the top-right corner. The Plan swtich from JSON to the formatted DSL script plan.
* Copy & paste this script or save it in a text file.

Q: How do I access data using the other 80 dataset types in ADF?

Data Flow currently allows Azure SQL DB, Azure SQL DW, Delimited Text files from Blob or ADLS, and Parquet files from Blob or ADLS natively for Source and Sink. Use the Copy Activity to stage data from any of the other connectors and then execute a Data Flow activity to transform data after it's been staged. For example, your pipeline will first Copy into Blob and then a Data Flow activity will use a dataset in Source to transform that data.
