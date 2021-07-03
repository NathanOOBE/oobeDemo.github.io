# Office 365 Exchange Online Protection

Exchange Online Protection has a feature known as Connection filtering which verifies the identity of the sender using SPF, DKIM, DMARC and Microsoft intelligence.

## Connection Filtering

Connection filtering within Exchange Online Protection refers to the verification of the sender using SPF, DKIM, DMARC and Microsoft intelligence.

Exchange Online Protection Connection Filtering is always enabled however it can, to a degree, be configured. A connection filter can be implemented to always allow or always block traffic based upon an IP list.

Connection Filtering Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Configure Connection Filter | Configured | Agencies are to provide IP addresses considered as safe. |

Connection Filter Configuration applicable to all agencies and implementation types

| Configuration | Value | Description |
| :--- | :--- | :--- |
| Connection filter policy name | Default | This policy is the default policy configured when Exchange Online is enabled and is consistent with best practice. |
| Scoped to | All Domains | This is the default setting configured when Exchange Online is enabled. |
| IP Allow list | Not Configured | This is the default setting configured when Exchange Online is enabled. |
| IP Block list | Not Configured | This is the default setting configured when Exchange Online is enabled. |
| Safe list | Disabled | This is the default setting configured when Exchange Online is enabled. |

## Anti-malware

Anti-malware within Exchange Online Protection refers to the default anti-malware scanning which is completed on all emails routing through the service.

In addition to the default scanning, anti-malware policies can be configured. These polices allow for the customisation of a response if malware is detected and the restriction of attachment file types.

Anti-malware Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Configure Anti-malware Policy | Configured | Configuring the anti-malware policy to allow for the customisation of a response if malware is detected and the restriction of attachment file types. |

Anti-malware Policy Configuration applicable to all agencies and implementation types

| Configuration | Value | Description |
| :--- | :--- | :--- |
| Anti-malware policy name | Default | Editing the default policy ensures it applies to all incoming and outgoing mail and is consistent with best practice. |
| Malware detection response | Notify recipients that the message has been quarantined with the default notification text | This will send a notification to recipients when a message is quarantined. |
| Sender notifications | Notify internal senders | This will send notification to senders when their message is quarantined. |
| Administrator notifications | Notify administrators about undelivered messages from internal senders |  |
| Notify administrators about undelivered messages from external senders | Administrators will be notified when messages are undelivered. |  |
| Allowed File type filtering | Disabled | This is the default setting configured when Exchange Online is enabled and is Microsoft best practice. This ensures that all file types are inspected for malware with no exceptions. |

## Policy Filtering

Policy filtering within Office 365 Exchange Online Protection refers to the enforcement of Transport Rules.

Transport Rules are a set of rules enforced on mail transiting through the Exchange Organisation. Transport rules can be leveraged by Administrators to complete a number of actions on all mail or a subsection of the mail transiting through the Exchange Organisation. These items include:

* Block mail with certain headers
* Apply disclaimers to emails
* Apply Office 365 message encryption

Transport Rules follow the following basic structure:

* Conditions – Conditions identify which mail the transport rule applies to. These conditions largely target either information gained from message headers \(e.g. the 'to', 'from' or 'CC' fields\) or message properties \(e.g., size, attachments, subject, body, message classification\). A single rule can have multiple conditions apply
* Exceptions – Exceptions are an optional component of a Transport Rule and define the mail exempt from the rule
* Actions – Actions are used to define what actions to undertake on the messages matching the conditions and which do not match any exemption. These actions include rejecting, deleting, redirecting the emails, and adding recipients, prefixes, and disclaimers. A single rule can have multiple actions applied however some actions are incompatible with others
* Properties – Properties are used to define anything which do not fall into another category. This includes enforcing or testing the rule

Policy Filtering Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Mail flow rules | Configured | Mail flow rules within the environment are required to enforce business rules and process. |

## Content Filtering

Content Filtering within Exchange Online Protection refers to SPAM management and SPAM policies.

Content Filtering polices allow for:

* The customisation of response on SPAM detection
* Marking emails as SPAM based on language detected
* Marking emails as SPAM based on the sender or sender's domain
* Increasing the SPAM score if certain content is present in the email
* Marking emails as SPAM if certain content is present in the email

The use of these policies allows greater management control over SPAM emails.

Content Filtering Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Configure SPAM policy | Default configuration | Exchange Online Protection will complete SPAM evaluation. |

