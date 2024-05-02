# AZ-104

## Azure Monitor Capabilities

- Provides you with a solution for collecting, analyzing, and responding to telemetry data from your on prem and cloud environments.
- Azure monitor provides features and capabilities in three areas:
    - **Monitor and visualize metrics:**
        - Gathers numerical metric values from your resources. Offers different methods for viewing your metric data to help you understand the health, operation, and performance of you system
    - **Query and analyze logs:**
        - Generates activity logs, diagnostic logs, and telemetry information from your monitoring solutions.
    - **Set up alerts and actions:**
        - Lets you set up alerts for your gathered data to notify you when critical conditions arise. You can configure actions based on the alert conditions, and take automated corrective steps based on triggers from your metrics or logs
- Monitoring and diagnostic services offered in Azure are divided into broad categories such as:
    - Core
    - Application
    - Infrastructure
    - Shared Capabilities
- Data stores in Azure Monitor hold your metrics and logs.
- **Azure Monitor Insights** performs different functions with the collected data, including analysis, alerting, and streaming to external systems.
    - Access Azure App insights extension to Azure Monitor to use the **Application Performance Monitoring (APM) features**. You can use APM tools to monitor your app performance and gather trace logging data. Application insights are available for many Azure services, such as Azure VM and Azure VM Scale Sets, Azure Container instances, Azure Cosmos DB, and Azure IoT Edge
    - **View and interpret** your gathered metrics and logs with Azure Monitor. Use Power BI with Azure Workbooks feature to access configurable dashboards and views
    - Use Azure Monitor Logs (Log Analytics) to **write log queries for your data**. You can interactively analyze your log data by using Azure Monitor Metrics and the powerful analysis engine
    - Set up **log alert rules** to receive notifications about your app performance. You can configure it to take automated action when an alert matches condition or result
    - **Ingest and export log query results** from Azure CLI, Powershell cmdlets, and various APIs. Set up automated export of your log data to your Azure Storage account or Azure Event Hubs.  
        <br/>

## Metrics and Logs

- All data collected in Azure Monitor falls into:
    - **Metrics**:
        - Numerical values that describe some aspect of a system at a point in time. They are lightweight and capable of supporting near real-time scenarios
    - **Logs**:
        - Contain different kinds of data organized into records with different sets of properties for each type. Data like events and traces are stores as logs along with performance data so all the data can be combined for analysis  
            <br/>

## Things to know about Azure Monitor Metrics

- metrics are displayed on a overview page for the resource.
- Use Azure Monitor metrics explorer to view the metrics for your resources and services
- Metrics have charts that you can interact with or pin them to a dashboard to view them with other visualizations  
    <br/>

## Things to know about Azure Monitor Logs

- Log data collected is stored in Log Analytics
- Includes rich query language (KQL or Kusto Query Language) to help you quickly retrieve, consolidate, and analyze your collected data
- Work with Log Analytics to create and test queries.
- Azure uses a Data Explorer query language (KQL). Suitable for simple log queries, but also includes advanced functionality like aggregations, joins, and smart analytics  
    <br/><br/>You can use Azure Monitor Agent to compute resources and extend your data sources, by extending you can collect data for the internal operation of the resources  
    <br/><br/>Azure Monitor can collect log data from any REST client by using the **Data Collector API**. This lets you create custom monitoring scenarios and extend monitoring to resources that dont expose data through other sources  
    <br/>

## Monitoring data tiers

- Collected data by Azure Monitor are categorized by tiers. Tiers can include data collected for many sources, such as:  
    <br/>

![Screenshot 2024-05-01 184645.png](../../_resources/Screenshot%202024-05-01%20184645.png)  
<br/>

## Azure Activity Log

- Can narrow down to the specific VM or on prem service running in your infrastructure
- Can also view a while resource groups activity log
- Activity log is a subscription log that provides insight into subscription-level events. Can be a range of data from ARM (Azure Resource Manager) operational data to updates on Azure service health events
- Can help you determine the "what, who, when" for any write operation (PUT, POST, DELETE) performed on a resource
- Activity logs are kept for 90 days