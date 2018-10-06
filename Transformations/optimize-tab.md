# Azure Data Factory Data Flow

## Transformation Optimize Tab

Each Data Flow transformation will have an "Optimize" tab which contains optional settings to configure your partitioning schemes for your data flow.

<img src="../images/opt001.png" width="800">

The default setting is "use current partitioning" which will instruct ADF to use the partitioning scheme native to Data Flows running on Spark in Azure Databricks. Generally, this is the recommended approach.

However, there are instances where you may wish to adjust the partitioning. For instance, if you want to output your transformations to a single file in the lake, then chose "single partition" on the Optimize tab for partitioning in the Sink Transformation.

If you wish to change partitioning on any transformation, simply click the Optimize tab and select the "Set Partitioning" radio button. You will then be presented with a series of options for partitioning:

1. Round Robin

2. Hash

3. Dynamic Range

4. Fixed Range

5. Key

<img src="../images/opt002.png" width="400">
