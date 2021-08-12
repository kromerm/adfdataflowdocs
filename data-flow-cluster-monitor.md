# Data flows cluster report

The ADF Data Flows cluster report is a by-request feature that enables users to self-serve analyzing cluster utilization for their ADF data flow pipelines by presenting resource utilization via Azure Log Analytics. Analyzing the results of your data flow executions can help to right-size your Azure Integration Runtime data flow configurations.

##	Setup Log Analytics Workspace

* Via Portal: https://docs.microsoft.com/en-us/azure/azure-monitor/logs/quick-create-workspace
* ARM Template: https://docs.microsoft.com/en-us/azure/architecture/databricks-monitoring/dashboards#deploy-the-azure-log-analytics-workspace
* PS: Deploying log analytics workspace using the ARM template will include useful queries specific to spark-monitoring. These queries could be customized for specific business requirement.

##	Link Log Analytics Workspace with Data Factory
Under “diagnostic setting” property for Data Factory, link Log Analytics workspace
 
* PS: Spark monitoring expects only single log analytics workspace associated with the factory. If 0 or > 1 workspaces are linked to the factory, spark monitoring will not work.

Assign Factory managed identity permissions on log analytics workspace using built-in or custom RBAC role :

Option 1: Assign Built-in Monitoring contributor access on the workspace or the Resource group or subscription containing the workspace.
https://docs.microsoft.com/en-us/azure/azure-monitor//roles-permissions-security#monitoring-contributor

Option 2: Create custom Role with following permissions access on the workspace or the Resource group or subscription containing the workspace:
https://docs.microsoft.com/en-us/azure/role-based-access-control/custom-roles

```
"actions": [
 "*/read",
 "Microsoft.Insights/DiagnosticSettings/*",
 "Microsoft.OperationalInsights/workspaces/search/action",
 "Microsoft.OperationalInsights/workspaces/sharedKeys/action"
]
```

Sample query to correlate Activity Run id with cluster id to analyse cpuUsage:
```
ADFActivityRun
| where ActivityType contains 'ExecuteDataflow'
| where Status !in ('Queued', 'InProgress')
| where Status == 'Succeeded'
| extend output=parse_json(Output)
| extend clusterId=tostring(output["runStatus"]["ClusterId"])
| extend IRName=substring(EffectiveIntegrationRuntime, 0, indexof(EffectiveIntegrationRuntime, "(") - 1)
| project Status, ActivityRunId, IRName, output, clusterId
| join (
SparkMetric_CL
| where name_s contains "executor.cpuTime"
| extend sname=split(name_s, ".")
| extend executor=strcat(sname[0],".",sname[1])
| project TimeGenerated, cpuTime=count_d/1000000, executor, name_s, clusterId_s
| join kind=inner (
SparkMetric_CL
| where name_s contains "executor.RunTime"
| extend sname=split(name_s, ".")
| extend executor=strcat(sname[0],".",sname[1])
| project TimeGenerated, runTime=count_d, executor, name_s, clusterId_s
) on executor, TimeGenerated
| extend cpuUsage=(cpuTime/runTime)*100
//| summarize cpuUsage by bin(TimeGenerated, 1ms), clusterId_s
) on $left.clusterId == $right.clusterId_s
| summarize max(cpuUsage) by bin(TimeGenerated, 1ms), strcat(ActivityRunId, '-', clusterId)
| render timechart
```

This query can be customized to visualize cpu/memory usage per Activity/Integration Runtime/etc.

Further References:
* https://spark.apache.org/docs/latest/monitoring.html#metrics
* https://docs.microsoft.com/en-us/azure/architecture/databricks-monitoring/dashboards

