# Azure Data Factory Data Flow Transformations

## Conditional Split

The Conditional Split transformation can route data rows to different streams depending on the content of the data. The implementation of the Conditional Split transformation is similar to a CASE decision structure in a programming language. The transformation evaluates expressions, and based on the results, directs the data row to the specified strean. This transformation also provides a default output, so that if a row matches no expression it is directed to the default output.

![conditional split](../images/cd1.png "conditional split")

To add additioinal conditions, select "Add Stream" in the bottom configuration pane and click in the Expression Builder text box to build your expression.
