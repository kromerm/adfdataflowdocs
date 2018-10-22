# Azure Data Factory Data Flow Transformations

## Extend Transformation

Use the Extend Transformation to add your own custom data transformation via Spark coed that you're built, which can be included in ADF's Data Flow by providing a JAR file that Data Flow will execute for you on your Azure Databricks cluster.

![Extend Transform](../images/extend.png "Extend Transformation")

To add additioinal conditions, select "Add Stream" in the bottom configuration pane and click in the Expression Builder text box to build your expression.

Below is a Java example that applies "lower" to the "title" column using a Spark custom transformation. The first parameter and return type is required.

```java
package com.microsoft.dataflow.javaExtension;

import org.apache.spark.sql.Dataset;
import org.apache.spark.sql.Row;
import org.apache.spark.sql.SparkSession;
import org.apache.spark.sql.functions;

public class ExtensionFrame {
	public static Dataset<Row> transform(Dataset<Row> df, SparkSession spark, String rowMarkerCol)  {
		return df.withColumn("shortTitle", functions.lower(df.apply("title")));
	}
}
```
In the transformation field "Method", enter "com.microsoft.dataflow.extension.transform".
 

