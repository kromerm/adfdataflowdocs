# Azure Data Factory Data Flow Transformations

## UnPivot

Use UnPivot in ADF Data Flow as a way to turn an unnormalized dataset into a more normalized version by expanding values from multiple columns in a single record into multiple records with the same values in a single column.

<img src="../images/unpivot1.png" width="300">

### UnGroup By

<img src="../images/unpivot5.png" width="300">

First, set the columns that you wish to group by for your pivot aggregation. You can set more than 1 column here with the + sign next to the column list.

### UnPivot Key

<img src="../images/unpivot6.png" width="400">

The Pivot Key is the column that ADF will pivot from row to column. By default, each unqiue value in the dataset for this field will pivot to a column. However, you can optionally enter the values from the dataset that you wish to pivot to column values.

### UnPivoted Columns

<img src="../images/unpivot4.png" width="400">

Lastly, you will choose the aggregation that you wish to use for the pivoted values and how you would like the columns to be displayed in the new output projection from the transformation.

(Optional) You can set a naming pattern with a prefix, middle, and suffix to be added to each new column name from the row values.

For instance, pivoting "Sales" by "Region" would simply give you new column values from each sales value, i.e. "25", "50", "1000", etc. However, if you set a prefix value of "Sales " 

<img src="../images/unpivot3.png" width="400">

Setting the Column Arrangement to "Normal" will group together all of the pivoted columns with their aggregated values. Setting the columns arrangment to "Lateral" will alternate between column and value.

<img src="../images/unpivot7.png" width="600">

The final unpivoted data result set shows the column totals now unpivoted into separate row values.
