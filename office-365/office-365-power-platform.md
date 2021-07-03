# Office 365 Power Platform

Power Platform combines the power of PowerApps, Power BI, and Microsoft Flow into one business application platform. This enables quick and easy app building and data insights.

## Power Apps and Power Automate

Power App and Power Automate are Office 365 tools to develop and create cross platform applications with minimal amount of coding. These tools enable an organisation to create forms, capture information, automate business process and present it in a report to the Agency.

Power Apps and Power Automate is built with an underlying connector that allows application to consume to be displayed and business process to act on this information. These connectors provide ability to consume or leverage on existing business tools. Power Apps and Power Automate connectors can be categorised as:

* Office 365 Connectors – Office 365 Connectors provides data access to Office 365 applications \(e.g. SharePoint, Teams\)
* Azure Services Connectors – Azure services connector provides Power Apps and Power Automate access to consume Azure Services \(e.g. Azure Cosmos DB, Azure Computer Vision\).
* Third Party Connectors – Third Party Connectors allows external vendors to provide a service to Power Apps and Power Automate \(e.g. Adobe Reader Sign\).
* On-premises data connectors – On-premises data connectors allows Power Apps and Power Automate to consume data from a variety of sources.

The following image shows consideration required for authentication process and requirements for each generalised group of connectors. The cloud services connector is required to be registered in Azure platform before it can be consumed in Power App and Power Automate. On-premises data access requires a service account for network access and a database service account access for Power Apps and Power Automate to consume its data.

![Power Apps and Power Automate authentication flow](https://github.com/oobeDemo/NewBlueprint/tree/66fd6517c124f7a383765d0b482624e905d46e0c/assets/images/o365-power-authentication.png)

Power Apps and Power Automate Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Data Policies for Power Automate and Power Apps | Configured Access only to SharePoint, OneDrive for Business, Office 365 Users, Planner, Outlook for 365, and Teams | Data Lost Prevention configures the connectors that can be used in Power Apps and Power Automate  The Agency should evaluate the connectors to ensure it fits to the Agency's requirement. |
| Environment Administrator | Configured Access to Environment Administrator is assigned to a security group for Power App and Power Automate | Security group should be used to be assigned as Environment Administrator for PowerApps and Power Automate. Environment Administrator will be allowed to create additional environment and configure the connector policies. |

## Power BI

Power BI is a data visualisation tool which can be leveraged to provide interactive dashboards and reports. It integrates with a variety of data sources to enable the creation of dashboards and reports.

Power BI consists of five components:

* Power BI Desktop - Power BI desktop is a Windows desktop application which allows for the manipulation of data and the creation of reports and dashboards.
* Power BI Service - The Power BI service is a SaaS offering which allows the creation, modification, and sharing of reports and dashboards.
* Power BI Mobile - Power BI mobile is a mobile application which allows for the consumption of reports and dashboards.
* Power BI Report Server - The Power BI report server is an on-premises tool which enables reports to be distributed as required.
* Power BI Embedded – Power BI embedded allows organisation to publish Power BI report to be consumed in a public website.

Inside the Power BI Service, the creation of workspaces, content packs, custom visualisations, and data flows can be controlled both on an enterprise level and a group level. This simplifies management of the service.

Power BI also allows administrators to control the sharing of datasets, content, report publishing, and template apps. This ensures that the sharing of the Agency information is controlled.

Power BI Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Power BI Information Protection | Enabled | Power BI Information Protection leverages sensitive labels to label Power BI Reports |
| External Sharing | Disabled | External Sharing is disabled to reduce the risk of data spills. |
| Data Export | Disabled | Export of data is disabled to prevent unauthorised access to the underlying report information. |
| Third Party integration | Disable | Disable third party integration, such as ArcGIS. This should be evaluated by the Agency to ensure that the data stays within Australia. |

