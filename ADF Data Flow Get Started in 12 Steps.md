by balakreshnan <https://github.com/balakreshnan>

Here’s how to get started using Azure Data factory Data Flow
============================================================

This guide is for private preview customers to get started with Azure data factory v2 with data flow
----------------------------------------------------------------------------------------------------

1. To build your first Data Flow Data Factory, use the Azure Portal to create "Azure Data Factory" and select "V2 with data flow (preview)"

<img src="images/portal.png" width="400">

2. That will create your new Data Factory with Data Flows in the SE Asia region

3. Click on author & Monitor

    ![](media/09b0f0e02aaede3d38acf46a6dcb8644.png)

That should take you to a new window which is azure data factory author main page

4. On the main page click on the left hand side menu there should be pencil

    ![](media/f3a2eff81e3af2a1775407d2c410b71f.png)

5. Click on Connections in the left bottom of the page to edit the Azure Databricks Linked Service

    ![](media/d242a4c1928463417119ab08248e1e37.png)

6. Click on the Edit button as highlighted with black arrow

    ![](media/af068303e7906e297c666307bf12d39b.png)

7. Now here you need to change the Azure databricks cluster to existing if you
    want to use existing running clusters

    ![](media/adb1.png)

8. You will need to provide the access token key for your Azure Databricks account. [Here is more information on how to obtain that.](https://docs.databricks.com/api/latest/authentication.html#generate-token)

9. Make sure Select Existing Cluster

10. Then Get the cluster ID from the Azure Data bricks URL

11. Would be numbers and letters combined. If you go to azure Databricks
    workbench and select the cluster, you will see the Cluster ID in the Tags
    section at the bottom of the cluster page:

    ![](media/c6511f8763cfc590a0e2262cdc960442.png)

12. Copy and paste that in the configuration page.

You're done! Now the Data factory is ready for submitting the jobs with data transformaions via Data Flow.
