If you are using an Azure Subscription that is a trial subscription or has low quotas on cores / vCPUs, you may run into a situation where you do not have enough cores available in your subscription to run Azure Databricks. In that case, you must request additional cores.

You can do this from the Azure Portal. Find the "subscriptions" resource and select your subscription. You will then see a category on the subscriptions blade for "Usage & quotas". Select that and you will then open a blade with a button at the top right for "Request Increase".

Select vCPUs as the quote type and the VM types that you are using with Azure Databricks, most likely the DS3 series.

From there, select the region where your Azure Databricks is stood up and increase the number of cores. After submitting your request, you should receive and email confirmation that your subscription has had the vCPU / cores limit increased based on your request.

[The detailed documentation for requesting these increases is here](https://docs.microsoft.com/en-us/azure/azure-supportability/resource-manager-core-quotas-request)

