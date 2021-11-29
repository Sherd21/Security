# Security

## Microsoft Sentinel

### Azure Firewall Log Parsers

Azure Firewall stores all logs for Application, Network, DNAT, DNS etc in a single table **AzureDiagnostics**. To make it easier to use these logs in hunting queries and Analytic rules, several parsers were created based on workbook queries, supplied with a Azure Firewall Data Connector for Sentinel.

##### Parsers
There are two parsers available at the moment:
* [Network Logs](./AzFirewallNetLogs.csl)
* [Application Logs](./AzFirewallAppLogs.csl)

##### Usage

Parsers can be used as regular tables, for example query:
```sql
AzFirewallNetLogs
| where Protocol == "TCP"

AzFirewallAppLogs
| where FQDN !contains "bing.com"
```

##### Deployment
Parsers can be saved as Functions using query text or deployed using ARM template by clicking "Deploy" button:

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FSherd21%2FSecurity%2Fmain%2FARM%2Fazfirewallparsers.json)
<br>