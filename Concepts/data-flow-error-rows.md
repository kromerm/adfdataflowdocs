# Enable error row handling on Azure SQL DB sink types

Add this string to the end of your ADF URL: ```&feature.errorrowhandling=true```

# Sink settings

In the 

https://github.com/kromerm/adfdataflowdocs/blob/master/images/errors1.png



## Create and update columns

When creating a derived column, you can either generate a new column or update an existing one. In the **Column** textbox, enter in the column you are creating. To override an existing column in your schema, you can use the column dropdown. To build the derived column's expression, click on the **Enter expression** textbox. You can either start typing your expression or open up the expression builder to construct your logic.

![Derived column settings](media/data-flow/create-derive-column.png "Derived column settings")

To add more derived columns, click on **Add** above the column list or the plus icon next to an existing derived column. Choose either **Add column** or **Add column pattern**.

![New derived column selection](media/data-flow/add-derived-column.png "New derived column selection")

### Column patterns

In cases where your schema is not explicitly defined or if you want to update a set of columns in bulk, you will want to create column patters. Column patterns allow for you to match columns using rules based upon the column metadata and create derived columns for each matched column. For more information, learn [how to build column patterns](concepts-data-flow-column-pattern.md#column-patterns-in-derived-column-and-aggregate) in the derived column transformation.

![Column patterns](media/data-flow/column-pattern-derive.png "Column patterns")

## Building schemas using the expression builder

When using the mapping data flow [expression builder](concepts-data-flow-expression-builder.md), you can create, edit, and manage your derived columns in the **Derived Columns** section. All columns that are created or changed in the transformation are listed. Interactively choose which column or pattern you are editing by clicking on the column name. To add an additional column select **Create new** and choose whether you wish to add a single column or a pattern.

![Create new column](media/data-flow/derive-add-column.png "Create new column")

When working with complex columns, you can create subcolumns. To do this, click on the plus icon next to any column and select **Add subcolumn**. For more information on handling complex types in data flow, see [JSON handling in mapping data flow](format-json.md#mapping-data-flow-properties).

![Add subcolumn](media/data-flow/derive-add-subcolumn.png "Add Subcolumn")

For more information on handling complex types in data flow, see [JSON handling in mapping data flow](format-json.md#mapping-data-flow-properties).

![Add complex column](media/data-flow/derive-complex-column.png "Add columns")

