# ADF Data Flows Versioning

## This is a feature that will allow you to test your data factory data flows by executing your factory on a version that only updates on a monthly basis, as opposed to the live service which is updated weekly.

### JSON ARM Template config

"properties": {
"globalConfiguration": {
dataFlowRuntimeVersion: "Candidate"
}
}
