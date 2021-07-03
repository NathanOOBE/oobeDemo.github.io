---
layout: page
title: Platform
---

# Platform Introduction

The Blueprint includes guidance for cloud native and hybrid deployments of Microsoft 365 technologies, configured to meet PROTECTED standards. It is designed to also be used for staged deployments that leverage hybrid configurations as a transition step to cloud native transformation.

Each section of the document provides a description of the relevant technology component, including considerations, decisions and their applicability to cloud native implementations, hybrid configurations, or both.

It is important to consider that even if a product is licenced for use by Microsoft, it may not be included in this Blueprint if it is not required for all agencies. Additionally, an organisation may have requirements that will need to be considered outside of this Blueprint.

This document covers the following topics.

| Section | Description |
| :--- | :--- |
| Identity and Access Management | The Identity and Access Management section includes the authentication, authorisation methods and Conditional Access policies used within the Blueprint for Cloud and Hybrid solutions. |
| Security | The Security section details several cloud-based security components available within the Microsoft 365 suite to detect and monitor suspicious behaviour for Cloud and Hybrid solutions. |
| Client Configuration | The Client Configuration section details the Microsoft Endpoint Manager - Intune \(Intune\) management methods and design decisions for the client configuration. |
| Backup and Operational Management | The Backup and Operation Management section details the backup design decisions including RPO, RTO and Data Availability. |
| System Administration | The System Administration section details how the solution will be managed, the administrative consoles that will be used to administrator the various components, and how Role Based Access Control \(RBAC\) is implemented to control access. |

For each component within the document there is a brief description of the contents of the section, a commentary on the things that have been considered in determining the decisions and the design decisions themselves.

## Scope

The following tables in this section lists the components that are in scope for the Blueprint and the relevant design document that contains them.

### Platform design

| Component | Inclusions |
| :--- | :--- |
| Azure Active Directory | Domains User Accounts Agency Collaboration Multifactor Authentication Conditional Access |
| Active Directory | On premises for Hybrid solutions only |
| Security | Microsoft Cloud App Security Azure Advance Threat Protection Microsoft Defender Advanced Threat Protection Security Information and Event Management Monitoring |
| Client Configuration | Intune Microsoft Co-Management Group Policy Printing |
| Backup | Microsoft 365 Backup |
| System Administration | Administrative Consoles Role bases Access Control |

### Microsoft 365 design

| Component | Inclusions |
| :--- | :--- |
| Microsoft 365 Organisation | Residency License Self Service Purchase Themes Office 365 Services and Add-Ins Role Based Access Control Customer Lockbox |
| Microsoft 365 Connectivity | Mail Flow and Gateway Optimisation Exchange Hybrid Mail Exchange Records Mail Connectors Autodiscover SPF, DMARC, DKIM Accepted Domains Remote Domains Certificates |
| Exchange Online | Mail Migration User Mailbox Configuration Authentication Policies Outlook on the Web Policies Mailbox Archive Journaling Litigation Hold Shared Mailboxes Resource Mailboxes Distribution Lists Microsoft 365 groups Address Book / Address List |
| SharePoint Online | SharePoint Sites SharePoint Hybrid Application Management Web Parts Sharing and Access Controls Legacy Features |
| OneDrive for Business | Sharing Storage and Synchronisation Notifications Content Migration |
| Microsoft Teams | Access Dynamic Security Group Organisation Wide Configuration Policies & Settings Unified Communication Voice Calling |
| Power Platform | Power Apps and Power Automate Power BI |
| Security & Compliance | Alerts Classification Labels Retention Policies Data Loss Prevention Audit and Logging |
| Exchange Online Protection | Connection Filtering Anti-malware Policy Filtering Content Filtering |
| Microsoft Defender for Office 365 | Safe Links Safe Attachments Anti-Phishing |
| Microsoft Whiteboard | Diagnostic Data Enablement Connected Experience Easy Sharing |
| Microsoft Planner | iCalender Publishing |
| Microsoft Forms | External sharing Phishing Protection Bing and YouTube embedding |

### Client devices

| Component | Inclusions |
| :--- | :--- |
| Windows 10 | Hardware Deployment Customisations Security |
| iOS | Enrolment Security Remote Wipe |

## Assumptions

* Azure Multifactor Authentication \(MFA\) natively supports the OATH \(Open Authentication\) standard for selected hardware tokens. To use Azure MFA with OATH support, and to achieve an Essential 8 Maturity level of 3, hard tokens are required to be procured and deployed to all users. This Blueprint and associated security documentation assume the use of soft tokens and a level 2 maturity in this aspect of the Essential 8. 
* Microsoft 365 and Microsoft Azure solutions hold audit data for a period based on the service and the license level of the organisation. The time for most services is under 2 years. For organisations with a requirement to hold audit data past this period, Security Information and Event Management \(SIEM\) integration should be considered. Service audit data within the Microsoft 365 and Azure clouds is often housed in discrete systems and the opportunities to bring the data under a single pane is limited. Azure Monitor or Azure Sentinel are two Microsoft offerings which could be leveraged for this purpose however a holistic solution should be considered to ensure any legislative requirements are met.
* The Blueprint has been designed to cater for government organisations allowing end user devices internet access from anywhere \(head office, regional office or home\) direct connected and via proxy servers, VPN servers or Security Internet Gateways \(SIGs\). Where connected through a proxy server, rules will be configured to allow direct connection for some Microsoft 365 services. Mobile users will access Microsoft 365 services directly. These users will be subject to Conditional Access policies to reduce unauthorised access risk.
* The Intune Console is the preferred method to manage all settings regardless of Cloud native or Hybrid. Although a combination of the Microsoft Endpoint Configuration Manager \(MECM\) Console and Group Policy Objects \(GPOs\) would be able to achieve the same settings in a hybrid environment, this Blueprint does not include MECM and GPOs example configurations due to the level of dissimilarities and per agency customisation in existing MECM and GPOs configurations across Commonwealth entities.

