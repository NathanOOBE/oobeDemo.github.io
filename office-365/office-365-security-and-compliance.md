# Office 365 Security and Compliance

Office 365 provides Security and Compliance tools which can be utilised to implement an organisation's Information Management Policy and to assist with information governance. The Office 365 Security and Compliance tools provides the ability to govern and monitor the following components:

* SharePoint Online
* OneDrive for Business
* Teams
* Exchange Online

## Alerts

Office 365 contains various out-of-the-box Alert Policies, some of which are dependent on the available Office 365 licence. Alert Policies can be configured to track administrative activities, malware threats, user actions and/or data loss incidents.

Each alert can be configured with the following settings:

* Tracked Activity - The activity that will cause the alert to be generated. For example, sharing a file with an external user, assigning access permissions, or creating an anonymous link
* Activity Conditions - When a tracked activity triggers, additional conditions can be applied to filter out unnecessary alerts. For example, an alert can be triggered only if a certain user performs a task
* When to Trigger - When the above conditions are met, further filtering can be applied to only alert when a certain threshold is met. For example, an alert is only raised if the activity has been performed more than five times
* Alert Category - An alert category is assigned to assist with tracking and managing the alerts generated
* Alert Severity - An alert severity is assigned to assist with tracking and managing the alerts generated. The severity is displayed in the subject line of the alert email
* Alert Notification - An alert can be configured with a list of email addresses that should receive the alert notifications. Daily notification limits can also be configured to ensure an alert receiver is not bombarded with alert emails for the same event. Triggered alerts can also be viewed in the Security & Compliance Center

Alert Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Alert Policies Status | Default Alert Policies enabled | Custom alert policies are not required for the initial phase. Custom alert policies will be considered in a future project phase. |

## Classification Labels

Classification labels which is located under the Office 365 Security & Compliance Center offers the ability to both control the data flow of sensitive information and control the retention of data. Classifications labels consists of the following:

* Sensitivity Labels – Allow label specific protection policy settings to be enforced
* Retention Labels – Allow label specific retention policy settings to be enforced

Sensitivity labels can be applied in the supported Office applications either in Office 365 ProPlus, Office Online or using the Azure Information Protection \(AIP\) unified labelling client.

Classification labels are published to users using Label Policies. Label Policies define the users who can utilise the label and the locations within Office 365 where it can be used. Classification labels can be applied in the following ways:

* Manually - The label is applied manually by the end-user
* Automatically applied based on the location of the document - Labels can be configured to automatically apply based on the location of the document. For example, SharePoint
* Automatically applied based on detected Sensitive Information Type - Labels can be configured to automatically apply based on the type of sensitive information found. For example, documents containing Australia driver's license numbers

At the time of writing, Sensitivity labels cannot be configured to satisfy some specific requirements listed in the Protective Security Policy Framework \(PSPF\). The PSPF requires the protective marking to be applied to email messages via either:

* Appending the protective marking to the Subject field using a specified syntax \(Subject Field Marking\)
* Including the protective marking in an Internet Message Header Extension using a specified syntax \(Internet Message Header Extension\)

Sensitivity labels create a protective marking within the message header and when combined with Exchange mail flow rules the subject can be modified to prepend text in the subject according to the sensitivity.

Email gateway rules are available in the Network Configuration ABAC document. These rules are based on regular expressions and are easily adaptable to vendor specific email gateways.

Classification Label Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Sensitivity Labels | Enabled | Labels will be applied in accordance with the latest guidance from the PSPF. |
| Retention Labels | Enabled | Labels are recommended to be applied to automate retention configuration and compliance, but the development of specific retention labels is out of scope for this project |
| Labelling Policy | Enabled | Users will apply labels manually initially. Automatic labelling will be developed in a future project stage after considering potential impacts on backups and productivity changes |
| Subject line modification | Configured | Exchange mail flow rules are configured to modify the subject line in accordance with PSPF guidance |

## Retention Policies

Business information is required to be managed in order to comply with industry and government regulations and internal policies that require data to be retained for a certain period.

Office 365 retention policies assist with meeting these requirements by providing the following features:

* Configure policies to proactively decide whether to retain content, delete content, or both retain and then delete the content
* Apply a single policy to the entire organisation or just to specific locations or users
* Apply a policy to all content or just content meeting certain conditions, such as content containing specific keywords or specific types of sensitive information

When information is subject to a retention policy, end-users can continue to edit and work with the content as if nothing has changed because the content is retained in place, in its original location. But if someone edits or deletes content that is subject to the policy, a copy is saved to a secure location where it's retained while the policy is in effect.

Retention policy Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Retention Policies | Configured | To ensure that legislative data retention requirements are met. This is to ensure that the Agency holds the data for fraud detection. |

Retention Policies configuration applicable to agencies leveraging a cloud native implementation.

| Configuration | Value | Description |
| :--- | :--- | :--- |
| **Name: Exchange Indefinite Hold** |  |  |
| Retention configuration | Retain the data "Forever" | How long the data is to be held by the policy. |
| Location | Exchange email – All users included | The Office 365 location where the policy applies. |
| **Name: SharePoint Indefinite Hold** |  |  |
| Retention configuration | Retain the data "Forever" | How long the data is to be held by the policy. |
| Location | SharePoint Sites – All Sites | The Office 365 location where the policy applies. |
| **Name: OneDrive Indefinite Hold** |  |  |
| Retention configuration | Retain the data "Forever" | How long the data is to be held by the policy. |
| Location | OneDrive Accounts – All Accounts | The Office 365 location where the policy applies. |
| **Name: Office 365 Groups Indefinite Hold** |  |  |
| Retention configuration | Retain the data "Forever" | How long the data is to be held by the policy. |
| Location | Office 365 Groups – All Groups | The Office 365 location where the policy applies. |
| **Name: Teams Channel Messages Indefinite Hold** |  |  |
| Retention configuration | Retain the data "Forever" | How long the data is to be held by the policy. |
| Location | Teams channel messages – All teams included | The Office 365 location where the policy applies. |
| **Name: Teams chats Indefinite Hold** |  |  |
| Retention configuration | Retain the data "Forever" | How long the data is to be held by the policy. |
| Location | Teams chats messages – All users included | The Office 365 location where the policy applies. |

Retention Policy Configuration applicable to agencies leveraging a hybrid implementation

| Configuration | Value | Description |
| :--- | :--- | :--- |
| **Name: Exchange 3 Years Hold** |  |  |
| Retention configuration | Retain the data for 3 years | How long the data is to be held by the policy. |
| Location | Exchange email – All users included | The Office 365 location where the policy applies. |
| **Name: SharePoint 3 Years Hold** |  |  |
| Retention configuration | Retain the data for 3 years | How long the data is to be held by the policy. |
| Location | SharePoint Sites – All Sites | The Office 365 location where the policy applies. |
| **Name: OneDrive 3 Years Hold** |  |  |
| Retention configuration | Retain the data for 3 years | How long the data is to be held by the policy. |
| Location | OneDrive Accounts – All Accounts | The Office 365 location where the policy applies. |
| **Name: Office 365 Groups 3 Years Hold** |  |  |
| Retention configuration | Retain the data for 3 years | How long the data is to be held by the policy. |
| Location | Office 365 Groups – All Groups | The Office 365 location where the policy applies. |
| **Name: Teams Channel Messages 3 Years Hold** |  |  |
| Retention configuration | Retain the data for 3 years | How long the data is to be held by the policy. |
| Location | Teams channel messages – All teams included | The Office 365 location where the policy applies. |
| **Name: Teams chats 3 Years Hold** |  |  |
| Retention configuration | Retain the data for 3 years. | How long the data is to be held by the policy. |
| Location | Teams chats messages – All users included | The Office 365 location where the policy applies. |

## Data Loss Prevention

Data Loss Prevention \(DLP\) policies enable an organisation to identify, monitor, and automatically protect sensitive information across Office 365. DLP policies can be targeted to one or more products within the Office 365 suite.

A DLP policy can be configured to:

* Identify sensitive information, documents in a specific site \(for SharePoint only\) or specific labels contained in Exchange Online, SharePoint Online, and OneDrive for Business.
* Prevent end-users from accidentally sharing sensitive information
* Prevent end-users from accidentally deleting a document
* Educate end-users by presenting messages them on how to stay compliant when relevant. This is done without interrupting their workflow

At the time of writing Office 365 has 100 prebuilt sensitive information types \(Australian Passport Numbers etc.\). In addition to the prebuilt sensitive information types custom types can be created. These custom types look for strings, patterns, or key words.

Data Loss Prevention Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Data Lost Prevention Policies | Configured | To provide insights into the movement of potentially sensitive information. |

Data Loss Prevention Configuration applicable to all agencies and implementation types

| Configuration | Value | Description |
| :--- | :--- | :--- |
| **Name: Australian Privacy Act** |  |  |
| Locations | Protect content in Exchange email, Teams chats, channel messages, OneDrive and SharePoint documents. | The locations where the policy will apply. |
| Content type | Australian Driver's Licence number Australian Passport number | The types of sensitive information being detected. |
| Sharing detection | With people outside my organisation | When the policy is applied. |
| Notify users | Enabled | Users are notified when the policy is triggered. They are also provided policy tips for managing sensitive information. |
| Amount of instances | 5 | The amount of sensitive information required to trigger the policy \(10 is the default\). |
| Send incident reports | Enabled | User and nominated administrator are notified when the policy is triggered. |
| Restrict access or encrypt the content | Disabled | Access to the content that triggers the policy can be encrypted or and access limited. |
| **Name: Australian Personally Identifiable Information \(PII\) data** |  |  |
| Locations | Protect content in Exchange email, Teams chats, channel messages, OneDrive and SharePoint documents. | The locations where the policy will apply. |
| Content type | Australia Tax File Number  Australia Driver's Licence Number | The types of sensitive information being detected. |
| Sharing detection | With people outside my organisation | When the policy is applied. |
| Notify users | Enabled | Users are notified when the policy is triggered. They are also provided policy tips for managing sensitive information. |
| Amount of instances | 5 | The amount of sensitive information required to trigger the policy \(10 is the default\). |
| Send incident reports | Enabled | User and nominated administrator are notified when the policy is triggered. |
| Restrict access or encrypt the content | Disabled | Access to the content that triggers the policy can be encrypted or and access limited. |
| **Name: Australian Health Records Act \(HRIP Act\)** |  |  |
| Locations | Protect content in Exchange email, Teams chats, channel messages, OneDrive and SharePoint documents. | The locations where the policy will apply. |
| Content type | Australia Tax File Number  Australia Medical Account Number | The types of sensitive information being detected. |
| Sharing detection | With people outside my organisation | When the policy is applied. |
| Notify users | Enabled | Users are notified when the policy is triggered. They are also provided policy tips for managing sensitive information. |
| Amount of instances | 5 | The amount of sensitive information required to trigger the policy \(10 is the default\). |
| Send incident reports | Enabled | User and nominated administrator are notified when the policy is triggered. |
| Restrict access or encrypt the content | Disabled | Access to the content that triggers the policy can be encrypted or and access limited. |
| **Name: Australian Financial Data** |  |  |
| Locations | Protect content in Exchange email, Teams chats, channel messages, OneDrive and SharePoint documents. | The locations where the policy will apply. |
| Content type | SWIFT Code  Australia Tax File Number  Australia Bank Account Number  Credit Card Number | The types of sensitive information being detected. |
| Sharing detection | With people outside my organisation | When the policy is applied. |
| Notify users | Enabled | Users are notified when the policy is triggered. They are also provided policy tips for managing sensitive information. |
| Number of instances | 10 | The amount of sensitive information required to trigger the policy \(10 is the default\). |
| Send incident reports | Enabled | User and nominated administrator are notified when the policy is triggered. |
| Restrict access or encrypt the content | Disabled | Access to the content that triggers the policy can be encrypted or and access limited. |

## Audit and Logging

The Office 365 Security & Compliance Center provides the ability to monitor and review user and administrator activities across the Office 365 applications from the past 90 days.

Audit logs are kept by default for 90 days but are configurable up to one year by default for E5 licensing.

When an event occurs for the respective application it will take anywhere from 30 minutes up to 24 hours before it can be viewed in the audit log search.

The Office 365 Management Activity API enables third-party applications to consume audit logs from Office 365. If audit logging is disabled, third-party applications can still consume audit logs from the Office 365 Management Activity API.

A list of Office 365 applications, their auditing capabilities and duration wait time once an event occurs.

{:.auto}

| Application | User Activity | Admin Activity | Duration wait time |
| :--- | :--- | :--- | :--- |
| Exchange Online | x | x | 30 minutes |
| OneDrive for Business | x |  | 30 minutes |
| SharePoint Online | x | x | 30 minutes |
| Sway | x | x | 24 hours |
| Power Bi | x | x | 30 minutes |
| Workplace Analytics |  | x | 30 minutes |
| Dynamics 365 | x | x | 24 hours |
| Yammer | x | x | 24 hours |
| Microsoft Power Apps | x | x | 24 hours |
| Microsoft Power Automate | x | x | 24 hours |
| Microsoft Steam | x | x | 30 minutes |
| Microsoft Teams | x | x | 30 minutes |
| Microsoft Forms | x | x | 30 minutes |
| Azure Active Directory |  | x | 24 hours |
| eDiscovery activities in Office 365 Security & Compliance Center | x | x | 30 minutes |

At the time of writing, audit logging is not enabled by default and must be turned on first in the Office 365 Security & Compliance Center before user or administrator activities can be audited.

Auditing and Logging Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Unified Audit Logging | Enabled One-year retention | To provide visibility into the actions being undertaken within the Office 365 environment. |

