# Data Flow Script (DFS)
## What is DFS?
The data flow script (DFS) is the underlying text, similar to a coding language, that is used to execute the transformations that are included in a mapping data flow. Every transformation is represented by a series of properties that provide the necessary information to run the job properly. For instance, 

## Use cases
The DFS is usually hidden from users and is automatically produced by the user interface. As a result, most of the time reading or editing the DFS directly is unnecessary. There are some cases, though, where it can be helpful or necessary to have an understanding of the script to help with debugging and producing data flows.

Here are a few examples:
- Programatically producing many data flows that are fairly similar
- Complex expressions that are difficult to manage in the UI or are resulting in validation issues
- Debugging and better understanding various errors returned during execution

## How do I add transforms
Adding transformations requires three basic steps: adding the core transformation data, rerouting the input stream, and then rerouting the output stream. This can be seen easiest in an example.
Let's say we start with a simple source to sink data flow like the following:

<pre>
source(output(
		movieId as string,
		title as string,
		genres as string
	),
	allowSchemaDrift: true,
	validateSchema: false) ~> source1
source1 sink(allowSchemaDrift: true,
	validateSchema: false) ~> sink1
</pre>

If we decide to add a derive transformation, first we need to create the core transformation text, which has a simple expression to add a new uppercase column called `upperCaseTitle`:
<pre>
derive(upperCaseTitle = upper(title)) ~> deriveTransformationName
</pre>

Then, we take the existing DFS and add the transformation:
<pre>
source(output(
		movieId as string,
		title as string,
		genres as string
	),
	allowSchemaDrift: true,
	validateSchema: false) ~> source1
<b>derive(upperCaseTitle = upper(title)) ~> deriveTransformationName</b>
source1 sink(allowSchemaDrift: true,
	validateSchema: false) ~> sink1
</pre>

And now we reroute the incoming stream by identifying which transformation we want the new transformation to come after (in this case, `source1`) and copying the name of the stream to the new transformation:
<pre>
source(output(
		movieId as string,
		title as string,
		genres as string
	),
	allowSchemaDrift: true,
	validateSchema: false) ~> source1
<b>source1</b> derive(upperCaseTitle = upper(title)) ~> deriveTransformationName
source1 sink(allowSchemaDrift: true,
	validateSchema: false) ~> sink1
</pre>

Finally we identify the transformation we want to come after this new transformation, and replace its input stream (in this case, `sink1`) with the output stream name of our new transformation:
<pre>
source(output(
		movieId as string,
		title as string,
		genres as string
	),
	allowSchemaDrift: true,
	validateSchema: false) ~> source1
source1 derive(upperCaseTitle = upper(title)) ~> deriveTransformationName
<b>deriveTransformationName</b> sink(allowSchemaDrift: true,
	validateSchema: false) ~> sink1
</pre>

## What are top level constructs
All transformations other than sources have the same basic construction:
<pre>
<b>name_of_incoming_stream</b> transformation_type(
  <i>properties</i>
) ~> <b>new_stream_name</b>
</pre>
For example, a simple derive transformation that takes a column and overwrites it with an uppercase version would be as follows:
<pre>
source1 derive(
  column1 = upper(column1)
) ~> derive1
</pre>
