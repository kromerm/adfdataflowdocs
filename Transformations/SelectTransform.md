# Azure Data Factory Data Flow Transformations

## Select

The Select transform allows you to alias an entire stream or columns in that stream toBy sassign different names and then reference those new names later in your data flow. This is very useful for self-join scenarios.

## Options

The default setting for "Select" is to include all incoming columns and keep those original names. You can alias the stream by setting the name of the Select transform.

To alias individual columns, deselect "Select All" and use the column mapping at the bottom.


