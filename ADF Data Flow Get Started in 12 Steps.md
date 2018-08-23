by balakreshnan <https://github.com/balakreshnan>

Here’s how to get started using Azure Data factory Data Flow in 12 Steps
========================================================================

This guide is for private preview customers to get started with Azure data factory v2 with data flow
----------------------------------------------------------------------------------------------------

1.  To build you first Data Flow Data Factory [CLICK HERE](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fkromerm%2Fadfdataflowdocs%2Fmaster%2Fsamples%2Fcurrent_df_arm_template.json)

2. Then click on the Purchase button. Your Data Factory with Data Flow will deploy in less than 5 minutes.

3. Once deployed go the resource group that you specified and then click on the
    azure data factory

    ![](media/a51be05cea35390eb8052f25fb152eef.png)

Now you should see the Data factory Pane and click on author

4. Click on author & Monitor

    ![](media/09b0f0e02aaede3d38acf46a6dcb8644.png)

That should take you to a new window which is azure data factory author main page

5. On the main page click on the left hand side menu there should be pencil

    ![](media/f3a2eff81e3af2a1775407d2c410b71f.png)

6. Click on Connections in the left bottom of the page to edit the Azure Databricks Linked Service

    ![](media/d242a4c1928463417119ab08248e1e37.png)

7. Click on the Edit button as highlighted with black arrow

    ![](media/af068303e7906e297c666307bf12d39b.png)

8. Now here you need to change the Azure databricks cluster to existing if you
    want to use existing running clusters

    ![](media/adb1.png)

9. Make sure Select Existing Cluster

10. Then Get the cluster ID from the Azure Data bricks URL

11. Would be numbers and letters combined. If you go to azure Databricks
    workbench and select the cluster, you will see the Cluster ID in the Tags
    section at the bottom of the cluster page:

    ![](media/c6511f8763cfc590a0e2262cdc960442.png)

12. Now copy that and paste that in the configuration page and then click on
    Test Connection

Now the Data factory is ready for submitting the jobs with data transformaions via Data Flow.
