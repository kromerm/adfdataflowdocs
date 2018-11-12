
Azure Data Factory Data Flow has a debug mode which can be switched on from the Debug button at the top of the design surface.

<img src="../images/debugbutton.png" width="400">

## Overview
When Debug mode is on, you will interactively build your data flow with a running Azure Databricks interactive cluster. The session will close once you turn debug off in ADF. You should be aware of the hourly charges incurred by Azure Databricks during the time that you have the debug session turned on.

In most cases, it is a good practice to build your Data Flows in debug mode so that you can validate your business logic and view your data transformations before publishing your work in ADF.

## Debug Mode On
When you switch on debug mode, you will be prompted with a side-panel form that will request you to point to your interactive Azure Databricks cluster and select options for the source sampling. You must use an interactive cluster from Azure Databricks and select either a sampling size from each your Source transforms, or pick a text file to use for your test data.

<img src="../images/upload.png" width="800">

**NOTE: When running in Debug Mode in Data Flow, your data will not be written to the Sink transform. A Debug session is intended to serve as a test harness for your transformations. Sinks are not required during debug and are ignored in your data flow. If you wish to test writting the data in your Sink, execute the Data Flow from an ADF Pipeline and use the Debug execution from a pipeline.

## Debug Settings
Debug settings can be Each Source from your Data Flow will appear in the side panel and can also be edited by selecting "source settigns" on Data Flow design toolbar. You can select the limits and/or file source to use for each your Source transformation here. You can also select which Databricks cluster that you'd like to use for debug.

## Cluster status
There is a cluster status indicator at the top of the design surface that will turn green when the cluster is ready for debug. If your cluster is already warm, then the green indicator will appear almost instantly. If your cluster was not already running when you entered debug mode, then you will have to wait 5-7 minutes for the cluster to spin up. The indiciator light will be yellow until it is ready. Once your cluster is ready for Data Flow debug, the indicator light will turn green.

When you are finished with your debugging, turn the Debug switch off so that your Azure Databricks cluster can terminate.

<img src="../images/datapreview.png" width="400">

## Data Preview
With debug on, the Data Preview tab will light-up on the bottom panel. Without degub mode on, Data Flow will show you only the current metadata in and out of each of your transformations in the Inspect tab. The data preview will only query the number of rows that you have set as your limit in your source settings. You may need to click "Fetch data" to refresh the data preview.

<img src="../images/stats.png" width="400">

## Columns Stats
Selecting individual columns in your data preview tab will pop-up a chart on the far-right of your data grid with details about each field. ADF will make a determination based upon the data sampling of which type of chart to display. High-cardinality fields will default to NULL / NOT NULL charts while categorical and numeric data that has low cardinality will display bar charts showing data value frequency. You will also see max / len length of string fields, min / max values in numeric fields, standard dev, percentiles, counts and average. 

<img src="../images/chart.png" width="400">
