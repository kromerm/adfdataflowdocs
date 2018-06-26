# Azure Data Factory Data Flow Transformations

## Aggregate

The Aggregate transformation is where you will define aggregations of columns in your data streams. In the Expression Builder, you can define different types of aggregations (i.e. SUM, MIN, MAX, COUNT, etc ...) and create a new field in your output that includes these aggregations with optional group-by fields.

![Agg Transformation options](../images/agg.png "agg 1")

### Options

#### Group By
(Optional) Choose a Group-by clause for your aggregation and use either the name of an existing column or a new name. Use "Add Column" add more group-by clauses and click on the text box next to the column name to launch the Expression Builder to either select just an existing column, combination of columns or expressions for your grouping.

#### The Aggregate Column tab 
(Optional) Choose a Group-by clause for your aggregation and use either the name of an existing column or a new name. Use "Add Column" add more group-by clauses and click on the text box next to the column name to launch the Expression Builder. You can select your aggregation types and functions in the Expression Builder and save your expression.

![Agg Transformation options](../images/agghead.png "aggregator header")

### Define Schema

![Scource Transformation](../images/source.png "source 2")

#### You can modify the name of the source columns and their associated data types
