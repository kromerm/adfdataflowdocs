The concept of Schema Drift is the case where your sources often change metadata. Fields, columns, types, etc. can be added, removed or changed on the fly. Without handling for Schema Drift, your Data Flow becomes vulnerable to changes in upstream data source changes. When incoming columns and fields change, typical ETL patterns fail because they tend to be tied to those source names.

In order to protect against Schema Drift, it is important to have the facilities in a Data Flow tool to allow you, as a Data Engineer, to:

1. Define sources that have mutable field names, data types, values and sizes
2. Define transformation parameters that can work with data patterns instead of hard-coded fields and values
3. Define expressions that understand patterns to match incoming fields, instead of using named fields

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

*NOTE* You need to make an architectural decision in your data flow to accept schema drift throughout your flow. When you do this, you can protect against schema changes from the sources. However, you will lose early-binding of your columns and types throughout your data flow. ADF treats schema drift flows as late-binding flows, so when you build your transformations, the column names will not be avaiable to you in the schema views throuhgout the flow.

## Example

<img src="../images/taxidrift1.png" width="400">

In the Taxi Demo sample Data Flow, there is a sample Schema Drift in the bottom data flow with the TripFare source. In the Aggregate transformation, notice that we are using the "column pattern" design for the aggregation fields. Instead of naming specific columns, or looking for columns by position, we assume that the data can change and may not in the ordera

<img src="../images/taxidrift2.png" width="400">
