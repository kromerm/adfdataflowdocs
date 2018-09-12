# Azure Data Factory Data Flow Transformations

## Lookup

Use Lookup to add reference data from another source to your Data Flow. Add the Join transform with the Plus icon on the data stream where you would like to join and then inside the transform you will select the 2nd Join stream.

![Join Transformation](../images/join.png "Join")

### Join types

Selecting Join Type is required for the Join transformation

#### Inner Join

Inner join will pass through only rows that match the column conditions from from both tables

#### Left Outer

All rows from the left stream not meeting the join condition are passed through, and output columns from the other table are set to NULL in addition to all rows returned by the inner join.

#### Right Outer

All rows from the right stream not meeting the join condition are passed through, and output columns that correspond to the other table are set to NULL, in addition to all rows returned by the inner join.

#### Full Outer

Full Outer produces all columns and rows from both sides with NULL values for columns that are not present in the other table

#### Cross Join

Specific the cross product of the 2 streams with an expression

### Specify Join Conditions

The Left Join condition is from the data stream connected to the left of your Join. The Right Join condition is the second data stream connected to your Join on the bottom, which will either be a direct connector to another stream or a reference to another stream.

You are required to enter at least 1 (1..n) join conditions. They can be either directly-referenced fields selected from the drop-down menu, or expressions.

