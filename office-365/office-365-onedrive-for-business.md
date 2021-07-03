# Office 365 OneDrive for Business

OneDrive for Business is a cloud-based, secure, personal document store. It allows storage and access of files from any approved device, allows offline editing, simple organisational collaboration, search tools, and advanced encryption and security features. The sharing of these documents can be controlled to allow or disallow sharing with external parties.

OneDrive data can be configured to automatically synchronise data, ensuring the user does not need to download files every time they wish to access them.

On deletion of a user's account content can be deleted or retained for a specified period.

## Sharing

The OneDrive sharing administration screen provides granular configuration. Controlling OneDrive sharing ensures that data is shared internally and externally in a secure manner.

OneDrive provides end users the ability to securely store their personal data in Office 365. The design considers that OneDrive is used for personal storage and sharing within the Agency.

OneDrive for Business Sharing Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| External Sharing | Disabled | Sharing to external users will be disabled. Collaboration and sharing will be achieved using Teams. |

OneDrive sharing configuration applicable to all agencies and implementation types

| Configuration | Value | Description |
| :--- | :--- | :--- |
| **Links** |  |  |
| Default Link Type | Internal: Only people in your organisation | No sharing is permitted outside the Agency. |
| **External Sharing** |  |  |
| SharePoint | Only people in your organisation | No external sharing allowed. |
| OneDrive | Only people in your organisation | No external sharing allowed. |
| **Advanced settings for external sharing** |  |  |
| Allow or block sharing with people on specific domains | Unchecked | Specific domains are not defined, meaning that content is permitted to be shared with all users within the directory \(internal\). |
| External users must accept sharing invitation using the same account that the invitations were sent to | Checked | Required to ensure users are authenticated before accepting sharing invitation |
| Let external users share items they don't own | Unchecked | Restricts external users \(guests\) from re-sharing content. |
| **Other settings** |  |  |
| Display to owner the names of people who viewed their files | Checked | Ensure owner is are aware of who it has been shared with |

## Storage and Synchronisation

OneDrive and SharePoint can synchronise content locally through the OneDrive for Business client.

Content can be "pinned" for offline use, ensuring that specific content is available offline, and changes are merged later.

The Sync Administration screen provides control Synchronising of File in OneDrive and SharePoint.

The sync client is required to provide the ability for end users to work offline from Office 365.

Storage and Synchronisation Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Synchronisation client | Configured | The Agency must use the OneDrive sync client to provide an offline file capability. |
| Storage Limitations | Configured | To assist the Agency in managing user data specific storage and retention limitations will be configured. |

Storage and Synchronisation Configuration applicable to all agencies and implementation types

| Configuration | Value | Description |
| :--- | :--- | :--- |
| Show the Sync button on the OneDrive Website | Checked | The synchronise button allows OneDrive files to be synced locally through the OneDrive for Business client. |
| Allow syncing only on PC joined to specific domains | Checked | Access to OneDrive content and synchronisation is controlled via Conditional Access, so this setting is not configured. Domain GUIDs to be provided by the Domain. |
| Block syncing of specific file type | Unchecked | File type synchronisation is not restricted. Office ATP and Defender ATP provides additional protection against malicious files. |
| Days to retain files after user account is marked for deletion | 365 days | Must align with the Agency internal record keeping policies. |
| Limit OneDrive user Capacity | 1024GB | Default setting. |

## Notifications

Notifications provide OneDrive users with information about how OneDrive is operating. The notification administration screen provides notification control to OneDrive owners.

The design considers notification and alerting of users for all shared documents in the organisation to ensure users are aware of the status of shared documents.

Users can be notified by email when:

* Other users invite additional users
* External users accept invitations
* An anonymous access link is created or changed

OneDrive for Business Notification Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| User notifications | Configured | Notifications will be configured to provide users with relevant information. |

OneDrive for Business Notification Configuration applicable to all agencies and implementation types

| Configuration | Value | Description |
| :--- | :--- | :--- |
| Display device notification to users when OneDrive files are shared with them | Checked | OneDrive will notify users when new files are shared with them |
| **E-mail OneDrive owners when** |  |  |
| Other users invite additional external users to shared files | Checked | OneDrive will notify users when a user re-shares a document to an external user \(guest\) |
| External users accept invitations to access files | Checked | OneDrive will notify users when external users accept an invitation to access files. |
| An anonymous access link is created | Checked | OneDrive will notify users when an anonymous access link is created |

## Content Migration

The implementation of OneDrive for Business can be coupled with a migration from an existing on-premises SharePoint farm infrastructure.

This migration can take the form of one of the following:

* OneDrive \(SharePoint 2010/2013\) – Administrators can move an existing OneDrive site hosted to SharePoint Online. Administrators can also leverage the capability of a Hybrid configuration to automatically redirect users to their OneDrive for Business post migration.
* Network and local file shares – Most users will have a personal drive or a designated location on the network to save work which may not have a function assigned. To free up network storage and extend the ability to access files in the cloud, administrators can move files from a specific network path to the user's OneDrive for Business site.

If a migration is not required, the deployment is referred to as a greenfield deployment.

Access to OneDrive can be controlled to ensure Agency data is protected. This includes the configuration of:

* Only allowing access from specific IP address locations
* Only allowing access from applications that use modern authentication
* Only syncing to PCs joined to a specific domain

On deletion of a user's account content will be deleted. The deletion period can be customised however it is recommended that the data be archived in an external system or migrated to a SharePoint Site.

Content Migration Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Deployment Type | Migration of data is out of scope for the blueprint however Microsoft provides vendor guidance  on possible migration paths for the agency | Migration method is dependent on the outcome of an assessment of quantity and type of data to be migrated. |

