# Azure Data Factory Data Flow Concepts

## Column Patterns

Several ADF Data Flow transformations support the idea of "Columns Patterns" so that you can create template columns based on patterns instead of hard-coded column names. You can use this feature within the Expression Builder to define patterns to match columns for transformation instead of requiring you to pick exact, specific field names.

![derive column template columns](../images/dc.png "Template Column")

This is very useful for handling Schema Drift scenarios or general scenarios where you are not able always fully know or assume each column name. You can pattern match on column name and column data type and build an expression for transformation that will perform that operation against any field in the data stream that matches your `name` & `type` patterns.

When building template column patterns, you can use `$1` in the expression to represent a reference to each matched field from the input data stream.
