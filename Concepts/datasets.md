Datasets are an ADF construct that define the data that you are working with in your pipeline.

In Data Flow, row & column level data requires a much more finely-grained definition than is required by Datasets within ADF pipeline control flow requirements.

Therefore, you use ADF Datasets in Source & Sink transforms to define the basic data location and connection (as part of the associated Linked Service).

But to define granular data types and formats, use the "Define Schema" tab in the Source transformation.

**NOTE: Not all properties from the Data Set definitions in ADF are currently honored by Data Flow. The UI will make an attempt to notify you of configuration differences between Copy & Data Flow interpretation of generic Dataset properties.**
