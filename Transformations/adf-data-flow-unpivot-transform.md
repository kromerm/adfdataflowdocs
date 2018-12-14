# Azure Data Factory Data Flow Transformations

## Unpivot

Unpivot provides a mechansim to rotate column values from multiple columns in a single record into multiple records with the same values in a single column. For example, a dataset that lists customer names has one row for each customer, with the products and the quantity purchased shown in columns in the row. After the Unpivot transformation normalizes the data set, the data set contains a different row for each product that the customer purchased.

<img src="../images/pivot1.png" width="300">

### Group By

<img src="../images/pivot2.png" width="300">

First, set the columns that you wish to group by for your pivot aggregation. You can set more than 1 column here with the + sign next to the column list.

### Pivot Key

<img src="../images/pivot3.png" width="400">

The Pivot Key is the column that ADF will pivot from row to column. By default, each unqiue value in the dataset for this field will pivot to a column. However, you can optionally enter the values from the dataset that you wish to pivot to column values.

### Pivoted Columns

<img src="../images/pivot4.png" width="400">

Lastly, you will choose the aggregation that you wish to use for the pivoted values and how you would like the columns to be displayed in the new output projection from the transformation.

(Optional) You can set a naming pattern with a prefix, middle, and suffix to be added to each new column name from the row values.

For instance, pivoting "Sales" by "Region" would simply give you new column values from each sales value, i.e. "25", "50", "1000", etc. However, if you set a prefix value of "Sales " 

<img src="../images/pivot5.png" width="400">

Setting the Column Arrangement to "Normal" will group together all of the pivoted columns with their aggregated values. Setting the columns arrangment to "Lateral" will alternate between column and value.

#### Aggregation

To set the aggregation you wish to use for the pivot, click on the field at the bottom of the Pivoted Columns pane. You will enter into the ADF Data Flow expression builder where you can build an aggregation expression and optionally provide an alternate name for your new aggregated values.
