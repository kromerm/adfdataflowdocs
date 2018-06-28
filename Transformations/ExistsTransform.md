# Azure Data Factory Data Flow Transformations

## Exists

The Exists transformation allows you to filter rows in your data stream that exists (SQL WHERE EXISTS) or do not exist (SQL WHERE NOT EXISTS). The resuling rows from your data stream after this transformation will either include all rows where column values from source 1 exist in source 2 or do NOT exist in source 2.

![Exists settings](../images/exsits.png "exists 1")

### Settings

#### Fed by
Choose the 2nd source for your Exists so that Data Flow can compare values from Stream 1 against Stream 2

Select the column from Source 1 and from Source 2 whose values you wish to check against for Exists or Not Exists.
