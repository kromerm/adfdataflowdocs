# Azure Data Factory Data Flow Transformations

## Surrogate Key Transformation

Use the Surrogate Key Transformation to add an incrementing non-business arbitrary key value to your data flow rowset. This is useful when designing dimension tables in a star schema analytical data model where each member in your dimension tables needs to have a unique key that is a non-business key, part of the Kimball DW methodology.

![Surrogate Key Transform](../images/surrogate.png "Surrogate Key Transformation")

"Key Column" is the name that you will give to your new surrogate key column.

"Start Value" is the beginning point of the incremental value.
