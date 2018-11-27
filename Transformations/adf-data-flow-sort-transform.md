
# Azure Data Factory Data Flow Transformations

## Sort

![Sort settings](../images/sort.png "Sort")

The Sort transformation allows you to sort the incoming rows on the current data stream. The outcoming rows from the Sort Transformation will subsequently follow the ordering rules that you set. You can choose invidual columns and sort them ASC or DEC, using the arrow indicator next to each field. If you need to modify the column before applying the sort, click on "Computed Columns" to launch the expression editor. This will provide with an opportunity to build an expression for the sort operation instead of simply applying a column for the sort.

You can turn on "Case insensitive" if you wish to ignore case when sorting string or text fields.

"Sort Only Within Partitions" leverages the Spark data partitioning capability to sort incoming data only within each partition as opposed to the entire data stream.

Each of the sort conditions in the Sort Transformation can be re-arranged. So if you need to move a column higher in the sort precendence, grab that row with your mouse and move it higher or lower in the sorting list.

## Partitioning effects on Sort

ADF Data Flow is executing on big data Spark clusters in the backend that distributes data across multiple nodes and multiple data partitions. It is important to keep this in mind when architecting your data flow in ADF where you are depending on the Sort transform to keep data in that same order. If you choose repartition your data in a subsequent transformation, you may lose your sorting due to that reshuffling of data.
