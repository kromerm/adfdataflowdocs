# Azure Data Factory Data Flow Transformations

## Join

The Aggregate transformation is where you will define aggregations of columns in your data streams. In the Expression Builder, you can define different types of aggregations (i.e. SUM, MIN, MAX, COUNT, etc ...) and create a new field in your output that includes these aggregations with optional group-by fields.

![Join Transformation](../images/join.png "Join")

### Join types

Selecting Join type is required for the Join transformation

#### Inner



#### Left Outer

#### Right Outer

#### Full Outer

#### Cross Join


### Specific Join Conditions

The Left Join condition is from the data stream connected to the left of your Join. The Right Join condition is the second data stream connected to your Join on the bottom, which will either be a direct connector to another stream or a reference to another stream.

You are required to enter at least 1 (1..n) join conditions. They can be either directly-referenced fields selected from the drop-down menu, or expressions.

