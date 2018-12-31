# Azure Data Factory Data Flow Transformations

## Window Aggregations

The Window transformation is where you will define window-based aggregations of columns in your data streams. In the Expression Builder, you can define different types of aggregations that are based on data or time windows (aka SQL OVER clause) such as LEAD, LAG, NTILE, CUMEDIST, RANK, etc ...) and create a new field in your output that includes these aggregations with optional group-by fields.

![Window Transformation](../images/windows1.png "windows 1")

### Over
This where you will set the partitioning of column data for your window transformation. This is equivalent to the Partition By in the Over clause in SQL. If you wish to create a calculation or create an expression to use for the partitioning, you can do that by hovering over the column name and select "computed column".

<img src="../images/windows4.png" width="300">

### The Aggregate Column tab 
(Required) Choose the Aggregate Column tab to build the aggregation expressions. You can either choose an existing column to overwrite the value with the aggregation, or create a new field with the new name for the aggregation. The expression that you wish to use for the aggregation will be entered in the right-hand box next to the column name selector. Clicking on that text box will open up the Expression Builder.

Use the ADF Data Flow Expression Language to describe the column transformations in the Expression Builder: https://aka.ms/dataflowexpressions.

![Agg Transformation options](../images/agg2.png "aggregator")

