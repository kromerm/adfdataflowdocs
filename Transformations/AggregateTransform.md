# Azure Data Factory Data Flow Transformations

## Aggregate

The Aggregate transformation is where you will define aggregations of columns in your data streams. In the Expression Builder, you can define different types of aggregations (i.e. SUM, MIN, MAX, COUNT, etc ...) and create a new field in your output that includes these aggregations with optional group-by fields.

![Scource Transformation options](../images/agg.png "agg 1")

### Options

#### Allow schema drift
Select Allow Schema Drift if the source columns will change often. This setting will allow all incoming fields from your source to flow through the transformations to the Sink.

#### Fail if columns in the dataset are not found
Choose this option to enforce a Source schema validation that will fail your Data Flow if columns that are expected from your source are not present.

#### Sampling
Use Sampling to limit the number of rows from your Source.  This is useful when you need just a sample of your source data for testing and debugging purposes.

### Define Schema

![Scource Transformation](../images/source.png "source 2")

#### You can modify the name of the source columns and their associated data types
