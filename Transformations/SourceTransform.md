# Azure Data Factory Data Flow Transformations

## Source

The Source transformation configures a data source that you wish to use to bring data into your data flow. You may have more than 1 Source transform in a single Data Flow.

** NOTE: Every Data Flow requires at least 1 Source Transformation (i.e. 1 to n) **

![Scource Transformation options](../images/source.png "source 1")

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

For source file types that are not strongly types (i.e. flat files as opposed to Parquet files) you should define the data types for each field here in the Source transformation as opposed to in the Dataset.

Here in the "Define Schema" tab on the Source transformation is where you can set the data types and formats:

![Scource Transformation](../images/source003.png "data types")
