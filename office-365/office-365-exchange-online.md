# Office 365 Exchange Online

Microsoft Exchange Online is a cloud-hosted messaging solution that has the capabilities of on-premises Exchange services. Exchange Online provides email, calendar, contacts, and tasks. Exchange Online supports mailbox delegation, where a delegate can have send-on-behalf and management rights over other mailboxes. Shared mailboxes can be assigned to and administered by many users. Application mail sending is supported where the application can authenticate against the Simple Mail Transport Protocol \(SMTP\) message submission to users inside the managed environment or authenticated SMTP message relay to addresses outside the managed environment.

Agencies should also refer to [Mail Flow and Gateway](office-365-exchange-online.md#mail-flow-and-gateway) for more information on mail flows, mail gateways and the use of GovLink.

## Mail Migration

The implementation of Exchange Online can be coupled with a migration from the existing on-premises Exchange infrastructure. If a migration is not required, the deployment is referred to as a greenfield deployment of Exchange Online.

There are three migration options:

* Hybrid Migration – Often referred to as a staged migration, is where the on-premises Exchange environment is extended to Office 365 through departmental relationships or federation. During migration user mailboxes will be spread between the online and on-premises environments, this necessitates planning to ensure free/busy, calendar and mailbox sharing all continue to work.
* Cutover Migration – A cutover migration is only recommended for organisations with less than 150 mailboxes and occurs over one or a few days. During this period email access may be unavailable. Prior to the migration event, a connection between the on-premises Exchange organisation and Exchange Online needs to be established.
* PST Migration – A Personal Storage Table \(PST\) migration is where PST files with a mapping file are either shipped to or uploaded into Office 365. The Exchange Online instance is a greenfield deployment with no configuration required on the on-premises Exchange environment.

Mail Migration Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Office 365 Tenant | Single tenant | Exchange Online services will be hosted within the Agency's secure Office 365 tenant. |

Additional Mail Migration Design Decisions for cloud native implementations

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Deployment Type | Exchange Online only | Exchange Online is suitable for agencies that are not leveraging any on- premises equipment. |

Additional Mail Migration Design Decisions for hybrid implementations

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Deployment Type | Hybrid Migration | User mailboxes should be migrated from the on-premises Exchange environment. |

## User Mailbox Configuration

User Mailboxes are Exchange Mailboxes that are associated with a user account. Usually one mailbox is associated to one user account.

User mailboxes can be configured to:

* Allow or disallow Internet Message Access Protocol \(IMAP\) and Post Office Protocol \(POP\) connections to them
* Prevent mail from deletion
* Control ActiveSync connections to them
* Control mail size limits
* Control the use of mail archives

The above configuration can be completed on all new mailboxes using a Client Access Services \(CAS\) Mailbox Plan. A CAS Mailbox Plan is used to configure settings when a licence is assigned to a new user. If the licence is changed, the CAS Mailbox plan linked to that new licence is applied. CAS Mailbox plans will be inherited from the existing Agency plans.

In addition to the above mailbox configuration, by default, standard user accounts have access to Exchange Online via Exchange Online PowerShell . ACSC guidance to disable unneeded features requires that this feature be disabled.

User Mailbox Configuration Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Disable IMAP | Configured | IMAP will be disabled to meet ACSC guidance to disable unneeded features. |
| Disable POP | Configured | POP will be disabled to meet ACSC guidance to disable unneeded features. |
| Exchange Mailbox Size | 100GB per user | Included with Office 365 E3 / E5 licencing. |
| Language | English | The default language is English, users will have the ability to adjust this if required. |
| Default time zone | GMT +10 | The default time zone is GMT +10 however this will be adjusted based on user location. |
| Exchange Message Size Limits | Up to 90MB | Default setting. Note that message limits may be smaller when sending messages to external mail recipients \(can be as low as 10MB\). |
| Custom Primary SMTP Addressing | first.last@agency.gov.au Usernames are recommended to follow the Universal Principal Name \(UPN\) format of the user, which is `first.last@<agency>.gov.au` | The primary SMTP address will be changed from `first.last@<tenant>.onmicrosoft.com` to ensure email continues to function in the same manner |
| Exchange Online PowerShell | Disabled for standard users | Standard users have no need to access Exchange Online via Powershell |

## Authentication Policies

Authentication policies control the authentication methods which can be used to access Exchange Mailboxes.

Authentication polices can be leveraged to protect the organisation from brute force and spray attacks. To protect against this, Basic Authentication can be blocked. Basic authentication is where a username and a password are leveraged for client access requests.

Blocking Basic Authentication forces clients to use Modern Authentication. Blocking Basic Authentication can cause issues when clients within the environment do not support Modern Authentication. If this occurs, it is recommended to investigate whether the client can be upgraded to support Modern Authentication. If it can, then it is recommended that the client be upgraded. If it cannot then a separate authentication policy can be leveraged enabling Basic Authentication for that client only.

Authentication Policy Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Basic Authentication | Disabled | Basic Authentication has known exploits, Modern Authentication is preferred. |
| Authentication Policy Configuration | Configured | Authentication Policy will be deployed to meet the security requirements of the Agency and be deployed in conjunction with the Agency security requirements. |

## Outlook on the Web Policies

Formerly known as Outlook Web App or Outlook Web Access, Outlook on the Web \(OWA\) policies, are used to control the availability of features and settings in Outlook on the Web. There are no security concerns with enabling OWA however agencies may wish to consider internal agency policies to inform decisions. A decision to disable OWA will not alter an agency's cyber security posture.

A mailbox can only be assigned one OWA policy and every mailbox must have a policy assigned.

Features and settings which can be controlled by an OWA policy include:

* Third party file provider integration
* Office 365 group creation
* Microsoft Satisfaction survey prompts

OWA Policy Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Outlook on the Web | Enabled | OWA will be enabled to allow users to access their email in a flexible manner |
| Third party file provider integration | Disabled | Only Microsoft file providers are approved for integration, no third-party file providers will be configured. This decreases security risk associated with third-party tools. |
| Office 365 group creation by users | Disabled | Groups can only be created by administrators, not users. This will ensure that the GAL is the most up to date and that there is a consistent naming convention utilised. |

## Mailbox Archive

Office 365 Mailbox Archives provide an unlimited email storage space for users. A mailbox archive is an additional mailbox storage space.

This archive can be accessed through the web portal or the Outlook client. Users can move or copy mail between their primary and archive mailboxes. Administrators can enable archive and deletion policies. These policies automatically move mail to the archive and, if required, delete mail from the archive when the set criteria are met. Mailbox archives are also subject to retention policies.

Mailbox Archive Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Mailbox Archive | Enabled | The archive mailbox is required to control primary mailbox cache sizes. |
| Mailbox Archive Policy | Enabled | The use of automated archive mailbox policies improves the user experience and ensures that primary mailbox sizes are controlled. |
| Archive configuration | Configured |  |

## Mailbox Auditing

Mailbox Auditing provides visibility into the access and modification of user mailboxes by owners, delegates, and administrators.

Once enabled on a user's mailbox, the activities subject to audit appear within the Office 365 audit log. This information is then available for security to review and run analysis. It is recommended that this audit log be exported to a centralised logging service.

Mailbox Auditing Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Mailbox Auditing | Configured | An event log auditing process, and supporting event log auditing procedures, is developed and implemented covering the scope and schedule of audits, what constitutes a violation of security policy, and actions to be taken when violations are detected, including reporting requirements. |
| Centralised Logging Facility | Not Configured | Agencies should consider their operational and security requirements around the use of a SIEM separately to the implementation of the Blueprint.  This design will implement Office ATP and Defender ATP which audit most Office and Defender logs for up to two years. These technologies send alert emails to Global Administrators and selected Office 365 administrators. |

Mailbox Auditing configuration applicable to all agencies and implementation types.

| Configuration | Value | Description |
| :--- | :--- | :--- |
| **User Mailbox and Shared Mailbox Audit Configuration** |  |  |
| Admin Audited Actions | ApplyRecord Copy Create FolderBind HardDelete MessageBind Move MoveToDeletedItems RecordDelete SendAs SendOnBehalf SoftDelete Update UpdateCalendarDelegation UpdateFolderPermissions UpdateInboxRules | All available audit actions will be selected in order to provide the required visibility of changes made to a mailbox. |
| Delegate Audited Actions | ApplyRecord Create FolderBind HardDelete Move MoveToDeletedItems RecordDelete SendAs SendOnBehalf SoftDelete Update UpdateFolderPermissions UpdateInboxRules | All available audit actions will be selected in order to provide the required visibility of changes made to a mailbox. |
| Owner Audited Actions | ApplyRecord Create HardDelete MailboxLogin Move MoveToDeletedItems RecordDelete SoftDelete Update UpdateCalendarDelegation UpdateFolderPermissions UpdateInboxRules | All available audit actions will be selected in order to provide the required visibility of changes made to a mailbox. |
| **Office 365 Group Mailbox Audit Configuration** |  |  |
| Admin Audited Actions | Create HardDelete MoveToDeletedItems SendAs SendOnBehalf SoftDelete Update | All available audit actions will be selected in order to provide the required visibility of changes made to a mailbox. |
| Delegate Audited Actions | Create HardDelete MoveToDeletedItems SendAs SendOnBehalf SoftDelete Update | All available audit actions will be selected in order to provide the required visibility of changes made to a mailbox. |
| Owner Audited Actions | HardDelete MoveToDeletedItems SoftDelete Update | All available audit actions will be selected in order to provide the required visibility of changes made to a mailbox. |

## Journaling

Journaling within Exchange is the recording of email communications as part of an organisation's retention strategy.

Journaling can assist with achieving compliance with government regulations. A Journal rule can be scoped to:

* Internal messages only
* External messages only
* All messages
* Specific recipients

Office 365 supports the use of journaling with the caveat that an Exchange Online mailbox cannot be used as a journaling mailbox. When configuring a mailbox for journaling, it must reside on an Exchange server. Journal reports can be delivered to a separate system to the Exchange Online instance.

Within Office 365, additional options are available to be leveraged in an organisation's retention strategy. These include:

* Retention Policies
* Litigation hold

Retention Policies can also be leveraged across the Office 365 organisation, whereas litigation hold is configured on a per-mailbox basis. These options reduce the complexity and management overhead involved with recording email and backing up to separate systems.

Journaling Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Configure Journaling | Not Configured | In place of Journaling, Litigation hold and retention policies in conjunction with eDiscovery will be leveraged by the Agency to meet investigation requirements. |

## Litigation Hold

Litigation hold preserves a mailbox and its contents from being modified or removed for e-Discovery purposes. A user can continue to send and receive email whilst litigation hold is enabled, even delete an item from the mailbox, and Office 365 will retain the items for discovery purposes.

Litigation hold is not enabled by default, and legal teams will need to proactively enable the feature to avoid users potentially deleting any critical data elements. You can also specify the duration for the hold, this is calculated from the date a mailbox item is received or created. If a duration is not set, items are held indefinitely or until the hold is removed.

Litigation hold is not an alternative to backups. While it is true that it keeps a copy of your data elements it is not saved in a separate location and cannot be restored to its original location.

Litigation Hold Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Litigation hold | Configured as required on selected users | Litigation hold requirements are unique to each Agency and user. |

## Shared Mailboxes

A Shared Mailbox is a mailbox which allows one or more users read and send messages. Shared Mailboxes also allow the sharing of a calendar between multiple people.

Within Office 365 shared mailboxes do not require a licence to be assigned to them unless the mailbox has over 50GBs of data.

Unlike user mailboxes, within AD, these mailboxes are represented by a disabled user account. These accounts can be enabled however this poses a security risk as the mailbox account is not related to a single user.

User access to the mailbox is provided using mailbox delegation rights \(Full Access, Send As, Send on Behalf\). These rights can be assigned either directly or using a mail enabled security group.

Shared Mailbox Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Shared mailbox delegation \(Full Access, Send As, Send on Behalf\) | Configured via mail-enabled Security groups which are hidden from the Global Address book | Mail-enabled security groups limit the management overhead associated with mailbox delegation when compared to direct delegations. A security group is required to be mail-enabled to appear within Office 365. |
| Naming standard for security groups | Configured | To distinguish between a security groups managing a shared mailbox a naming standard will be followed. e.g. `GMSG_<mailboxname>` |
| Shared Mailbox user account | Disabled | Default configuration. Accounts will remain disabled to reduce system attack surface. |

## Resource Mailboxes

A Resource Mailbox is a mailbox which is assigned to a resource as opposed to a user.

Resource Mailboxes have two types:

* Room mailboxes – Used for meeting rooms
* Equipment mailboxes – Used for non-location specific resources such as computers, projectors, microphones, or cars

Users book these resources using meeting requests. Resource Mailboxes can be configured to accept or decline the request based on their availability.

Room Mailboxes can be sorted into lists using Room Lists. Room Lists are leveraged to simplify the booking process by grouping all rooms that meet a certain requirement together \(Room lists are usually configured by location\). When a user books a meeting, they can select the appropriate room list and then see the available rooms for that time.

Resource Mailbox Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Room Mailboxes | Configured | There is a requirement for booking rooms within the solution. Rooms will be configured with a mailbox so that users can book them through their calendars. |
| Equipment Mailboxes | Configured | There is a requirement for booking equipment within the solution. Equipment will be configured with a mailbox so that users can book them through their calendars. |
| Room Lists | Configured | There is a requirement for booking rooms within the solution. Room Assets will be configured with a list so that users can book them through their calendars. |
| Naming standards for Resource mailboxes | Configured e.g. `RES_<location>` | To distinguish between resource mailboxes a naming standard will be followed for each resource mailbox. |

## Distribution Lists

A distribution list is a grouping of mail recipients that is addressed as a single recipient. Distribution lists are used to send e-mail to groups of people without having to enter each recipient's individual address. Distributions lists can be established to receive and distribute internal, external, or internal and external email.

This saves the sender from needing to enter each individual email address when emailing a group. These groups/lists are generally leveraged for emailing an entire team or project. Only internal agency employees can send emails to the "Agency-all" distribution list.

Distribution lists are created in different ways depending on the Exchange architecture:

* Cloud Deployments - For cloud only deployments, distribution lists are created within Office 365
* Hybrid Deployments - For hybrid deployments, distribution lists can be created both within Office 365 and on-premises. upon-premises lists are then synchronised to Office 365. The on-premises method has the benefit of living with the user identity source of truth however it does create complexity when it is not managed in the same location as Exchange

Management of Distribution lists can be streamlined through the enforcement of a Naming Policy. A Distribution list Naming Policy allows the enforcement of a consistent naming strategy across Office 365 Groups. It consists of two parts:

* Prefix-Suffix Naming Policy – Setting of prefixes or suffixes for groups names. The prefixes/suffixes can be either fixed strings or user attributes
* Custom Blocked Words – Blocking of words in the name based on a custom list

Distribution List Design Decisions for cloud native implementations

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Distribution Groups creation | Cloud Created | Management activities for Exchange Online will occur within the portal. The use of cloud created distribution groups also allows for the groups to be upgraded to Office 365 groups at a later stage. |
| Distribution Naming Policy | Configured The naming convention will be `AgencyName-PolicyName` | Naming policies streamline the management of Distribution lists and allow for groups to be easily sorted. |

Distribution List Design Decisions for hybrid implementations

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Distribution Groups creation | Hybrid Created | Management activities for Exchange Online will occur on the on-premises Exchange server. |
| Distribution Naming Policy | Configured | Naming policies streamline the management of Distribution lists and allow for groups to be easily sorted. |

## Office 365 Groups

Office 365 Groups are an extension on the traditional mail Distribution Lists, Mail-enabled Security groups and Shared Mailboxes.

Office 365 Groups allow members to collaborate with a group email, shared a workspace for conversations, files, calendar events, and a Planner. Unlike Shared Mailboxes, Office 365 groups can be accessed via mobile applications. Office 365 groups are also integrated with Microsoft Teams and are created when a Team is created.

Membership of an Office 365 Group can be dynamically updated using user attributes available in Azure AD. This removes some of the management overhead involved with managing the traditional group structures.

Management of Office 365 Groups can be streamlined through the enforcement of a Naming Policy, Office 365 group expiry, and creation restrictions. An Office 365 Group Naming Policy allows the enforcement of a consistent naming strategy across Office 365 Groups. It consists of two parts:

* Prefix-Suffix Naming Policy – Setting of prefixes or suffixes for groups names. The prefixes/suffixes can be either fixed strings or user attributes; and
* Custom Blocked Words – Blocking of words in the name based on a custom list.

In conjunction with the Naming Policy, Office 365 groups can also be given expiration dates. This assists with unused group clean-up activities. The expiration period commences on group creation and can be renewed at the end of the period \(The owner or contact for groups with no owners has 30 days to renew the group\). When a group expires, it is soft deleted for 30 days. Retention policies will however hold the data for the period of the retention policy. An expiration policy can be applied globally to all groups or to specific groups.

Office 365 Groups, by default can be created by any user. This can be restricted to Administrators and members of a security group. This restriction prevents the needless creation of groups. It is advisable to develop a workflow to control the provisioning process.

Office 365 Group Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Office 365 Group creation restrictions | Configured  Only administrators can create/configure Office 365 groups. | This will ensure that groups are approved before being created, ensuring all groups have a purpose. This setting also affects Exchange, SharePoint and Teams. |
| Naming Policy | `grp-AgencyName-SecurityGroup-Role` | Exchange groups will be named like the following AgencyName-Agency e.g. `grp-DTA-ExchangeMailbox-ITHelpdesk` |
| Group Expiration | All groups - annually | Group Expiration is required to simplify the management overhead associated with groups and to limit Azure AD clutter. |

## Address Book / Address List

The Outlook Address Lists, Global Address List \(GAL\), and Offline Address Book \(OAB\) are collections of mail-enabled objects.

They are leveraged for recipient lookup operations \(i.e. When a user leverages either the Address book or Check names tools in Outlook\). The types of mail-enabled object collections are as follows:

* GAL – The GAL is automatically created by Exchange and lists all mail-enabled objects. \(The GAL is available by default to all users\)
* OAB – The OAB is an offline version of the GAL leveraged by clients in Cached Mode
* Outlook Address List - An Outlook Address List is a subset of the mail-enabled objects. By default, a number of Address Lists are created, however, additional Address Lists can be created as required

Address Book and Address List Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Custom Address Lists | Configured | Custom address lists can be configured by Agency administrators, however one initial custom list, `AgencyName-All`, should be manually created. |
| GAL and OAB | Generated | These will be generated so that users can send emails within the organisation in accordance with Microsoft best practice. |

