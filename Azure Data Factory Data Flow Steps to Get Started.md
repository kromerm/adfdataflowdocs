by @balakreshnan

Here’s how to get started using Azure Data factory Data Flow
============================================================

This guide is for private preview customers to get started with Azure data factory v2 with data flow
----------------------------------------------------------------------------------------------------

1.  Submit your subscription ID for whitelisting

2.  Go to: <https://github.com/kromerm/adfdataflowdocs/tree/master/samples>

3.  Download the file: “current_df_arm_template.json” and save it in local drive

4.  Now to go to Azure portal and then click new and search “Template
    deployment”

5.  Then select Template Deployment

![](media/b682cdfd3971c23f096c21f194defe81.png)

1.  Click on Template deployment

2.  Then Select create on the page

    ![](media/7f882e627a336827d8890f3fa71110df.png)

3.  Then Click on Build your own template in the editor

    ![](media/9e9d9af6ef098ed75b62f96211dcf313.png)

4.  Now you should see a screen where you can upload the JSON file

5.  Now Click on Load File

    ![](media/9904436a39ba0b54a6e030eb7ad0540f.png)

6.  Open current_df_arm_template.json

    ![](media/eba63d158e958a245b6686819ba0d5ac.png)

7.  Now you should see the content of the file in the right side window

![](media/fb18c5028f040939979273b045c5ca5a.png)

1.  Now Click Save

2.  Type in a New resource group name “adfdataflow”

3.  Select the region as southeast asia

4.  Now fill the Datafactory Name with the name you wish call your data flow

5.  Now go to the blob account and get the storage connection string

    ![](media/3bd6be2be665dff8a97d48df4fd1326b.png)

6.  Now go to Azure data bricks workspace.

7.  Go to clusters and then go to User Settings on the right top corner

    ![](media/2da2e7aee362dad223964fd741982505.png)

8.  Now click User Settings and then click Generate New Token. Make sure to save
    the key because if you didn’t then you have to create a new key again

9.  Now you can paste the Token in the Azure portal

    ![](media/a35981c95cd51d0b13ecd090b3b97cfe.png)

10. In the above picture you should be able to see the Blob connection string
    and also the Databricks linked services access

11. Then click on the Purchase button and sit and wait for few minutes to deploy

12. Once deployed go the resource group that you specified and then click on the
    azure data factory

    ![](media/a51be05cea35390eb8052f25fb152eef.png)

13. Now you should see the Data factory Pane and click on author

14. Click on author & Monitor

    ![](media/09b0f0e02aaede3d38acf46a6dcb8644.png)

15. That should take you to a new window which is azure data factory author main
    page

16. On the main page click on the left hand side menu there should be pencil

    ![](media/f3a2eff81e3af2a1775407d2c410b71f.png)

17. That should open the authoring canvas

18. Click on Connections in the left bottom of the page

    ![](media/d242a4c1928463417119ab08248e1e37.png)

19. Edit the Azure databricks Linked service

20. Click on the Edit button as highlighted with black arrow

    ![](media/af068303e7906e297c666307bf12d39b.png)

21. Now here you need to change the Azure databricks cluster to existing if you
    want to use existing running clusters

    ![](media/a0b2dbe0b01e1a3f4a9a6b17ab57bbe2.png)

22. Make sure Select Existing Cluster

23. Then Get the cluster ID from the Azure Data bricks URL

24. Would be numbers and letters combined. If you go to azure Databricks
    workbench and select the cluster, you will see the Cluster ID in the Tags
    section at the bottom of the cluster page:

    ![](media/c6511f8763cfc590a0e2262cdc960442.png)

25. Now copy that and paste that in the configuration page and then click on
    Test Connection

26. Then Click Finish

27. And now the Data factory is ready for submitting the jobs.
