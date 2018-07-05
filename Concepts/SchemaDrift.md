With Schema Drift, your Data Flow becomes vulnerable to changes in upstream data source changes. When incoming columns and fields change, typical ETL patterns fail because they tend to be tied to those source names.

In order to protect against Schema Drift, it is important to have the facilities in a Data Flow tool to allow you, as a Data Engineer, to:

1. Define sources that have mutable field names, data types, values and sizes
2. Define transformation parameters that can work with data patterns instead of hard-coded fields and values
3. Deinfe expressions that understand template patterns
