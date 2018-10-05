# Azure Data Factory Data Flow

## Monitoring Data Flows

After you have completed building and debugging your data flow, you will want to schedule your data flow to execute on a schedule within the context of a pipeline. You can schedule the pipeline from ADF using Triggers. Or you can use the Trigger Now option from the ADF Pipeline Builder to execute a single-run execution to test your data flow within the pipeline context.

When you execute your pipeline, you will be able to monitor the pipeline and all of the activities contained in the pipeline including the Data Flow activity. Click on the monitor icon in the left-hand ADF UI panel. You will see a screen similar to the one below. The highlighted icons will allow you to drill into the activities in the pipeline, inlcuding the Data Flow activity.

<img src="images/mon001.png" width="800">

You will see stats at this level as well inculding the run times and status. The Run ID at the activity level is different that the Run ID at the pipeline level. The Run ID at the previous level is for the pipeline. Clicking the eyeglasses will give you deep details on your data flow execution.

<img src="images/mon002.png" width="800">

When you are in the graphical node monitoring view, you will see a simplified view-only version of your data flow graph.

<img src="images/mon003.png" width="800">

When your Data Flow is executed in Databricks, ADF determines optimal code paths based on the entirity of your data flow. Additionally, the execution paths may occur on different scale-out nodes and data partitions. Therefore, the monitoring graph represents the design of your flow, taking into account the execution path of your transformations. When you click on individual nodes, you will see "groupings" that represent code that was executed together on the cluster. The timings and counts that you see represent those groups as opposed to the individual steps in your design.

<img src="images/mon004.png" width="800"> 



<img src="images/mon005.png" width="800"> 

