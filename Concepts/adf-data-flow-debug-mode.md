
Azure Data Factory Data Flow has a debug mode which can be switched on from the Debug button at the top of the design surface.

<img src="../images/schemadrift001.png" width="400">



<img src="../images/schemadrift001.png" width="400">

2. When you've selected this option, all incoming fields will be read from your source on every Data Flow execution and will be passed through the entire flow to the Sink.

3. Make sure to use "Auto-Map" to map all new fields in the Sink Transformation so that all new fields get picked-up and landed in your destination:

<img src="../images/automap.png" width="400">

4. Everything will work when new fields are introduced in that scenario with a simple Source -> Sink (aka Copy) mapping.

5. To add transformations in that workflow that handles schema drift, you can use pattern matching to match columns by name, type, and value.

6. Click on "Add Column Pattern" in the Derived Column or Aggregate transformation if you wish to create a transformation that understands "Schema Drift".

<img src="../images/columnpattern.png" width="400">

*NOTE* You need to make an architectural decision in your data flow to accept schema drift throughout your flow. When you do this, you can protect against schema changes from the sources. However, you will lose early-binding of your columns and types throughout your data flow. ADF treats schema drift flows as late-binding flows, so when you build your transformations, the column names will not be avaiable to you in the schema views throuhgout the flow.
