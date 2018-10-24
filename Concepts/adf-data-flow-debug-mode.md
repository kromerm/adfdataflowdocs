
Azure Data Factory Data Flow has a debug mode which can be switched on from the Debug button at the top of the design surface.

<img src="../images/debugbutton.png" width="400">

## Overview
When Debug mode is on, you will interactively build your data flow with a running Azure Databricks interactive cluster. The session will close once you turn debug off in ADF. You should be aware of the hourly charges incurred by Azure Databricks during the time that you have the debug session turned on.

## Debug Mode On
When you switch on debug mode, you will be prompted with a side-panel form that will request you to point to your Azure Databricks cluster and select options for the source sampling

## Cluster status
There is a cluster status indicator at the top of the design surface that will turn green when the cluster is ready for debug. If your cluster is already warm, then the green indicator will appear almost instantly. If your cluster was not already running when you entered debug mode, then you will have to wait 5-7 minutes for the cluster to spin up. The indiciator light will be yellow until it is ready.



## 
3. Make sure to use "Auto-Map" to map all new fields in the Sink Transformation so that all new fields get picked-up and landed in your destination:

<img src="../images/automap.png" width="400">

4. Everything will work when new fields are introduced in that scenario with a simple Source -> Sink (aka Copy) mapping.

5. To add transformations in that workflow that handles schema drift, you can use pattern matching to match columns by name, type, and value.

6. Click on "Add Column Pattern" in the Derived Column or Aggregate transformation if you wish to create a transformation that understands "Schema Drift".

<img src="../images/columnpattern.png" width="400">

*NOTE* You need to make an architectural decision in your data flow to accept schema drift throughout your flow. When you do this, you can protect against schema changes from the sources. However, you will lose early-binding of your columns and types throughout your data flow. ADF treats schema drift flows as late-binding flows, so when you build your transformations, the column names will not be avaiable to you in the schema views throuhgout the flow.
