# Azure Data Factory Data Flow Transformations

## Exists

The Exists transformation allows you to filter rows in your data stream that exists (SQL WHERE EXISTS) or do not exist (SQL WHERE NOT EXISTS). The resuling rows from your data stream after this transformation will either include all rows where column values from source 1 exist in source 2 or do NOT exist in source 2.

![Exists settings](../images/exists.png "exists 1")

### Settings

#### Allow schema drift
Select Allow Schema Drift if the source columns will change often. This setting will allow all incoming fields from your source to flow through the transformations to the Sink.

#### Fail if columns in the dataset are not found
Choose this option to enforce a Source schema validation that will fail your Data Flow if columns that are expected from your source are not present.

#### Sampling
Use Sampling to limit the number of rows from your Source.  This is useful when you need just a sample of your source data for testing and debugging purposes.

### Define Schema

![Scource Transformation](../images/source.png "source 2")

#### You can modify the name of the source columns and their associated data types
