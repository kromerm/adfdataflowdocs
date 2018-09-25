The concept of Schema Drift is the case where your sources often change metadata. Fields, columns, types, etc. can be added, removed or changed on the fly. Without handling for Schema Drift, your Data Flow becomes vulnerable to changes in upstream data source changes. When incoming columns and fields change, typical ETL patterns fail because they tend to be tied to those source names.

In order to protect against Schema Drift, it is important to have the facilities in a Data Flow tool to allow you, as a Data Engineer, to:

1. Define sources that have mutable field names, data types, values and sizes
2. Define transformation parameters that can work with data patterns instead of hard-coded fields and values
3. Define expressions that understand template patterns

In ADF Data Flow, those facilities are surfaced through this worflow:

1. Choose "Allow Schema Drift" in your Source Tranformation

<img src="../images/schemadrift001.png" width="400">

2. When you've selected this option, all incoming fields will be read from your source on every Data Flow execution and will be passed through the entire flow to the Sink.

3. Make sure to use "Auto-Map" to map all new fields in the Sink Transformation so that all new fields get picked-up and landed in your destination:

<img src="../images/automap.png" width="400">

4. Everything will work when new fields are introduced in that scenario with a simple Source -> Sink (aka Copy) mapping.

5. To add transformations in that workflow that handles schema drift, you can use pattern matching to match columns by name, type, and value.

6. Click on "Add Column Pattern" in the Derived Column or Aggregate transformation if you wish to create a transformation that understands "Schema Drift".

<img src="../images/columnpattern.png" width="400">

7. 
