# Azure Data Factory Data Flow Concepts

## Column Patterns

Several ADF Data Flow transformations support the idea of "Columns Patterns" so that you can create template columns based on patterns instead of hard-coded column names. You can use this feature within the Expression Builder to define patterns to match columns for transformation instead of requiring you to pick exact, specific field names. This is very useful when your incoming source fields change often, particularly in the case of changing columns in text files or NoSQL databases. This is sometimes referred to as "Schema Drift".

![column patterns](../images/columnpattern2.png "Column Patterns")

This is very useful for handling Schema Drift scenarios or general scenarios where you are not able always fully know or assume each column name. You can pattern match on column name and column data type and build an expression for transformation that will perform that operation against any field in the data stream that matches your `name` & `type` patterns.

When adding an expression to a transform that accepts patterns instead of only exact field name matches, pick "Add Column Pattern" in order to utlize schema drift column matching patterns.

When building template column patterns, you can use `$$` in the expression to represent a reference to each matched field from the input data stream.

If you utilize one of the Expression Builder regex functions, you can then subsequently use $1, $2, $3 ... to reference the sub-patterns matched from your regex expression.

An example of using Column Patterns is to SUM a series of incoming fields for an Aggregate calculations in the Aggregate transformation. You can then SUM on every match of field types that match "integer" and then use $$ to reference each match in your expression.
