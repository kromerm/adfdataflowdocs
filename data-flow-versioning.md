# ADF Data Flows Versioning

### This is a feature that will allow you to test your data factory data flows by executing your factory on a version that only updates on a monthly basis, as opposed to the live service which is updated weekly.

#### JSON ARM Template config

"properties": {
"globalConfigurations": {
dataFlowRuntimeVersion: "Candidate"
}
}

#### Valid values for Runtime Version are:
* Candidate (this build is updated on the 15th of every month and becomes "Stable" on the 1st of the next month)
* Stable (this build is updated on the 1st of every month and is the previous Candidate build)
* Live (this is the current live service version of ADF Data Flows)
* If you leave the property set to blank, the default value will be "Live"

#### Recommended use of Data Flow versioning

If you wish to switch to versioned Data Flows, we recommend that you use "Stable" for the live production version of your factories and "Candidate" for your dev/test environment. You can also optionally maintain an "experimental" factory that is using the "Live" version that is the version of ADF data flows that is used by all general ADF customers. This would give you an opportuntity to experiment with the features in ADF that are deployed on a weekly cadence.
