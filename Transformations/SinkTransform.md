# Azure Data Factory Data Flow Transformations

## Sink

![Sink settings 1](../images/sink1.png "Sink 1")

At the completion of your data flow transformation, you can sink your transformed data into a destination dataset. In the Sink transformation, you can choose the dataset definition that you wish to use for the destination output data.

A common practice to account for changing incoming data and to account for data drift is to sink the output data to a folder without a defined schema in the output dataset.

You can choose to overwrite, append, or fail the data flow when sinking to a dataset.

You can also choose "automap" to simply sink all incoming fields. If you wish to choose the fields that you want to sink to the destination, or if you would like to change the names of the fields at the destination, choose "Off" for "automap" and then click on the Mapping tab to map output fields:

![Sink settings 2](../images/sink2.png "Sink 2")
