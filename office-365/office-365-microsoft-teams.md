# Office 365 Microsoft Teams

A Team in Microsoft Teams is a grouping of users who are working together to achieve an outcome. It allows users to communicate together through chat and meeting functions as well as collaborate on documents. Within the Team, Channels can be used to breakdown the work into smaller more specific items. These channels can be extended using Bots, Tabs, and connectors.

Microsoft Teams leverages most of the functionality of the Office 365 components. When a Team is created the following artefacts are created out of the box:

* SharePoint Site - A new SharePoint site with the URL format of `/sites/<SiteTitle>`, with the `SiteTitle`'s spaces are stripped out.
* Office 365 Group - A new Office 365 Group, which is added into the Azure AD tenant. This is created with the site title as the Group Name.
* Teams email – A new email address per channel can be created. The email inbox is managed centrally by the Microsoft Team services. At the time of writing this document, the email address will have a domain of `<custom email inbox>@apac.teams.ms`. 

Note: This email is not part of Microsoft Exchange Online.

## Access

Access to a team is controlled using Office 365 groups located in Azure AD.

When a Team is created, an Office 365 group will be created. Owners of the group are delegated to perform administrative actions across the team, while members can participate in the team but not undertake any administrative actions.

The design considers permissions, roles and responsibility to administer, manage team owners and members within the team.

Microsoft Teams Access Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Team creation permission | Selected administrators | Teams will be created by select administrators to ensure that Teams are created using a documented approval workflow, avoiding Team proliferation. This setting is required as Azure AD group creation is restricted which only allows administrators to create 365 groups, and hence Teams. |
| Administrative action over Teams after creation | Team Owners | Team Owners will either be selected administrators \(for Teams such as branches with many users\) or managers and their delegates \(such as in a section with relatively small user counts\). Team owners will be assigned logically at creation time and updated as required. |
| Team membership allocation | Manual by administrators or Team Owners | Team membership will be allocated manually initially with dynamic group allocation investigated in a future project phase when the logic for group membership is developed. |

## Dynamic Security group

Dynamic Security Groups are Azure AD security groups that are populated based on device and/or user attributes.

Dynamic Security groups can be leveraged to control access to locations, services, and features.

The membership of a Dynamic Security group is updated whenever an attribute of a device or user is modified. If the user/device no longer matches the group rule, then that user/device is removed. Conversely if a user/device now matches the group rule they are added. When a user is added the group can be configured so that the added user receives an email notifying them of the addition.

Naming of Dynamic Security groups can be streamlined using a Naming Policy. The Naming Policy ensures that the groups within the environment conform to a standard and their purpose can be easily identified.

Dynamic Security Groups Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Naming Policy | `grp-<Agency>-<GroupName>` | Assists in MOGs and standardisation of Agency configuration. |
| Welcome Email | Disabled | The welcome email will be disabled to reduce the amount of generic correspondence being sent to users. |

## Organisation Wide Configuration

Microsoft Teams is a collaboration platform that enable the Agency to work collaboratively with external agencies. This allows Agency users to collaborate internally, with trusted guest users and set up meetings with external users.

The design will consider the following configurations

* External Access - configures allowable domains to connect to the Agency instance of Microsoft Teams. This also configures Skype for Business integration.
* Guest Access – is when an external user is invited to be a member of the team. Once a team owner has granted someone guest access, they can access that team's resources, share files, and join a group chat with other team members.
* Teams Settings – configures the default behaviour of all users in the Teams application.

Organisation Wide Configuration Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| External Access | Configured: \(Example\) Allow dta.gov.au | Allow only dta.gov.au and deny sharing to external users. This will prevent users from setting up meetings with users that are not setup as a Guest of the Agency. |
| Guest Access | Configured: Guest Access: Enabled | Allows people outside of the agency to access teams and channels. |
| Teams Setting | Configured Disable all third-party file storage | This is to ensure departmental users do not save file outside of the Office 365 tenant. |

## Policies & Settings

Microsoft Teams provides ability to create policies around messaging, meetings, calling, video, and guest access. These settings can be configured in policies and assigned to individual users within the organisation.

The list below highlights the policies that can be configured with in teams:

* Teams Policies – Teams policies defines the policy for users to discover private teams and create private channels.
* Meeting Policies – Meeting policies define creations of meetings, audio and video, content sharing, and participant and guest permissions to meetings in Teams
* Live events Policies – Live events policies is used to globally broadcast departmental meeting via teams.
* Messaging Policies – Messaging policies defines behaviour of messages in Teams. The policy defines user capability in sending, editing, deleting, voice messages, and using giphy, stickers, URL preview and translator.
* Teams App – Teams apps policy defines the list of apps that can be used in Teams. Microsoft Teams provides Microsoft published apps and third-party apps that can be used in Microsoft Teams. Agency can control creation of custom apps in Teams.

Policies and Settings Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Team Policy | Configured Disable private channels | Team policy will be left as default settings. Discovered private teams Create private channels |
| Meeting Policies | Configured Global policy: Disable Whiteboard Automatically admit people – Everyone in your organisation | Meeting policy dictates how audio, videos and applications that are used in a team meeting. Whiteboard will be disable as the application does not meet application residency requirements. |
| Live events Policies | Configured Who can join live events: Everyone in Organisation | Live events is configured to prevent users outside of the organisation \(guest and external users\) cannot attend these meeting. |
| Messaging Policy | Configured | Messaging policy dictates how messaging is used in Teams. These includes usage of Giphy, Memes and stickers in messages. |
| Teams app | Configured Global Policy: Block specific app from Microsoft Apps  _Forms_  Yammer Block all Third-Party Apps Block all Tenant Apps | Microsoft Forms and Yammer are hosted in United States. This will cause data sovereignty issue for the Agency  All Third-Party Apps are blocked. These Third-Party apps needs to be evaluated individually. Tenant Apps are custom developed applications created by the Agency. This should be enabled if it is required. |

## Unified Communication

Teams provides a Unified Communication \(UC\) capability which allows users to participate in audio-visual conferencing in meetings and on-demand.

Teams can integrate with third-party UC products and provide configurable levels of functionality when integrated. Third party UC products will be the responsibility of the agency.

Microsoft Teams can natively provide the following UC features:

* Individual and group voice calls
* Individual and group video calls
* Individual and group chat

Unified Collaboration Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Individual and group voice calls | Configured | Default functionality |
| Individual and group video calls | Configured | Default functionality |
| Individual and group chat | Configured | Default functionality |

## Voice Calling

Enables agencies to make calls to landlines or mobiles within Microsoft Teams.

Telstra Calling for Office 365 avoids the complexity of separate collaboration systems.

The following image describes how connectivity is achieved between Microsoft Teams and Telstra.

![Telstra Calling for Office 365](https://github.com/oobeDemo/NewBlueprint/tree/66fd6517c124f7a383765d0b482624e905d46e0c/assets/images/o365-voice.png)

Voice Calling Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Telstra calling for Office 365 | Not configured | Agencies may require dial in and dial out functionality. This arrangement will need to be organised, paid for and configured by agencies that require this functionality. The configuration will not be covered in this blueprint. |

