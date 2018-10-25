
Azure Data Factory Data Flow has a debug mode which can be switched on from the Debug button at the top of the design surface.

<img src="../images/debugbutton.png" width="400">

## Overview
When Debug mode is on, you will interactively build your data flow with a running Azure Databricks interactive cluster. The session will close once you turn debug off in ADF. You should be aware of the hourly charges incurred by Azure Databricks during the time that you have the debug session turned on.

## Debug Mode On
When you switch on debug mode, you will be prompted with a side-panel form that will request you to point to your Azure Databricks cluster and select options for the source sampling

## Debug Settings


## Cluster status
There is a cluster status indicator at the top of the design surface that will turn green when the cluster is ready for debug. If your cluster is already warm, then the green indicator will appear almost instantly. If your cluster was not already running when you entered debug mode, then you will have to wait 5-7 minutes for the cluster to spin up. The indiciator light will be yellow until it is ready. Once your cluster is ready for Data Flow debug, the indicator light will turn green.

