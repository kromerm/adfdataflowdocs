# Azure Data Factory Data Flow Transformations

## Pivot

Use Pivot in ADF Data Flow as an aggregation where one or more grouping columns has its distinct row values transformed into individual columns.

<img src="../images/pivot1.png" width="300">

### Group By

<img src="../images/pivot2.png" width="300">

First, set the columns that you wish to group by for your pivot aggregation. You can set more than 1 column here with the + sign next to the column list.

#### Pivot Key

<img src="../images/pivot3.png" width="300">

The Pivot Key is the column that ADF will pivot from row to column. By default, each unqiue value in the dataset for this field will pivot to a column. However, you can optionally enter the values from the dataset that you wish to pivot to column values.

#### Pivoted Columns

<img src="../images/pivot4.png" width="300">

Lastly, you will choose the aggregation that you wish to use for the pivoted values and how you would like the columns to be displayed in the new output projection from the transformation.

(Optional) You can set a naming pattern with a prefix, middle, and suffix to be added to each new column name from the row values.

For instance, pivoting "Sales" by "Region" would simply give you new column values from each sales value, i.e. "25", "50", "1000", etc. However, if you set a prefix value of "Sales " 

<img src="../images/pivot5.png" width="300">
