# Azure Data Factory Mapping Data Flow: Overview

*NOTE: This overview of Mapping Data Flows is specific to the public preview version*

Mapping Data Flows in ADF provide a way to transform data at scale without any coding required. Design a data transformation job in the ADF Data Flow designer by constructing a series of Source Transformations, followed by data transformation steps, then sink your results in a Sink Transformation.

## Getting Started

Start by creating a new ADF V2 factory from Azure Portal

<img src="images/v2dataflowportal.png" width="500">

Once you are in the ADF UI, we have sample Data Flows available from the ADF Template Gallery. In ADF, create "Pipeline from Tempalte" and select the Data Flow category from the template gallery.

<img src="images/template.png" width="500">

You will be prompted to enter your Azure Blob Storage account information.

<img src="images/template2.png" width="500">

[The data used for these samples can be found here](https://github.com/kromerm/adfdataflowdocs/tree/master/sampledata). Download the sample data and store the files in your Azure Blob storage accounts so that you can execute the samples.

Use the Create Resource plus sign button in the ADF UI to create Data Flows

<img src="images/newresource.png" width="500">

