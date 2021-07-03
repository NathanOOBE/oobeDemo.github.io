# Office 365 SharePoint Online

## SharePoint Sites

SharePoint Online provides the ability to create Intranet sites and Team Sites for groups or agencies to collaborate and manage their documents. A SharePoint site allows members of a team or from other teams to contribute content on a single platform. The information is limited to the members of the team or project.

The creation and storage sizing of SharePoint online sites can be controlled. Out of the box, users can create SharePoint sites and these sites have no storage limits applied. Without restriction there is potentially a large management overhead so we have set a 200GB default which agencies can override.

Administrators can put controls in place which restricts who can create a SharePoint site and set the size requirements.

SharePoint Site Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| SharePoint site naming convention | Avoid spaces and special characters in site collection naming | Spaces and special characters can cause problems with indexing and extend the length of the path. Short names are easier to remember |
| Configure Site Storage limits | Configured | Larger storage can increase management. This can be manually set by SharePoint Administrator. Suggest 200GB |
| Block access from unmanaged devices | Configured | Allow limited web only access. Default settings. |
| Enable Idle Session sign outs | Sign out users after 1 hr Give users this much notice before signing out: 5 minutes | Default settings |
| Only allow access from specific IP address locations | Not configured | Access to be controlled via Conditional Access policies. |
| Only allow access from apps that use modern authentication | Enabled | Default settings |

## SharePoint Hybrid

In a hybrid configuration SharePoint Online integrates with an existing on-premises SharePoint Servers, extending the functionality and access between the two environments. Enhanced search results and site redirection provides administrators the control on which location a user access information.

SharePoint hybrid offers the following options for a hybrid configuration:

* Hybrid Federated Search – In a Federated Search configuration, the index for documents remains in the same system as the data. A SharePoint server can display results from SharePoint Online by making a remote SharePoint query, and users can also search SharePoint on-premises directly from SharePoint Online.
* Hybrid Cloud Search – In Cloud Search, the index of the SharePoint Server is pushed and merged with the SharePoint Online index. All the Content Processing and Analytics are done in Office 365, where the index is stored.
* Hybrid Site following – Hybrid site following can be configured to send users from the on-premises SharePoint Server to the equivalent service in Office 365.

SharePoint Hybrid Design Decisions for hybrid implementations

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| SharePoint Hybrid | SharePoint Hybrid Search will be configured. | To allow searching capabilities between SharePoint on-premises and SharePoint Online. |

## Application Management

Application management allows the Agency to control who can purchase third party applications for SharePoint Online. These apps can be purchased from [Microsoft App Store](https://appsource.microsoft.com/en-us/marketplace/apps?product=sharepoint) and used within SharePoint Online itself.

SharePoint default methods of displaying and sharing of sharing data are available. Third party applications may circumvent controls or auditing and provide other methods of displaying or sharing of SharePoint data. Any third-party applications will need to be validated for compliance.

The blueprint requires the Office 365 tenant to be rated up to Protected. The Agency must ensure information stays within the tenant to control the follow of information between its devices and Office 365 tenancy.

Application Management Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Users to have the ability to get apps from marketplace | Not Configured | Only administrators are approved to assign or purchase application. |
| Allow third party apps from the store be open office documents in the browser | Not Configured | This setting increases the security of the solution by ensuring documents in the browser cannot start third party apps for Office. |

## Web Parts

SharePoint Online provides spaces for users to customise their SharePoint page to include web parts into the page. Web Parts are additional functional parts that can be added into SharePoint pages to enhance productivity and usability for the site.

Web Parts are client-side applications that can be added into SharePoint Online. The document considers these two out of the box sets of webparts that needs to be considered as a part of the design decisions:

* Microsoft published webpart
* Third party published webpart

Web Part Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Microsoft published webpart | Enabled | Microsoft published webparts cannot be disabled in SharePoint. |
| Third Party published webpart | Disabled | Third party web parts will be disabled due to potential unsecure data flow outside of Office 365. If a third party published webpart is identified for use in future, the organisation will undertake a risk assessment before implementation. |

## Sharing and Access Controls

Sharing and Access controls provide granular control over external sharing and access to SharePoint Online. Sharing and Access control is essential for securing SharePoint Online document and information sharing.

Access to SharePoint Sites can be controlled through a variety of means to ensure that the data of the sites is protected. This includes the configuration of:

* Only allowing access from specific IP address locations
* Only allowing access from apps that use modern authentication
* Blocking access from devices which are not managed by the organisation through Intune
* Sites can be further secured through the implementation of Idle session timeouts. Idle session timeouts essentially act to log a user out of SharePoint after a period of inactivity

Access Controls provides an administrative tool to restrict access contents in SharePoint.

Sharing and Access Control Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Sharing Controls | Configured | Sharing to external users will be disabled. Documents within SharePoint Online can only be shared with internal users. Collaboration and sharing will be achieved using Teams. |
| Access Controls | Configured | Access to SharePoint Online will be controlled on a device level to ensure data is being accessed from approved devices. |

Sharing Configuration applicable to agencies leveraging a cloud native implementation

| Configuration | Value | Description |
| :--- | :--- | :--- |
| **External Sharing** |  |  |
| SharePoint | New and existing guests | Guest access is available in accordance with Collaboration in the DTA – Platform Design document |
| More external sharing settings | Limit external sharing by domain Guests must sign in using the same account to which the sharing invitations are sent | Checked. `Add domains that are allowed` Checked. |
| OneDrive | Only people in your organisation | No external sharing allowed. |
| **File and folder links** |  |  |
| Choose the type of link that is created by default when users get links | Specific people | Internal link which can only be sent to people in your organisation. |
| **Other settings** |  |  |
| Show owners the names of people who viewed their files in OneDrive | Checked | This is to ensure owners are aware of external users who have access to the document. |
| Let site owners choose to display the names of people who viewed files or pages in SharePoint | Checked | Permits display of activity on SharePoint sites to foster collaboration. |
| Use shorter links when sharing files and folders | Checked | Ensure URL are short and concise. |
| Default link permission | Edit | Users will have edit permissions by default to increase usability. If view permissions are required, this is also available. |

Sharing Configuration applicable to agencies leveraging a hybrid implementation

| Configuration | Value | Description |
| :--- | :--- | :--- |
| External Sharing |  |  |
| SharePoint | Only people in your organisation | No external sharing allowed. |
| OneDrive | Only people in your organisation | No external sharing allowed. |
| File and folder links |  |  |
| Choose the type of link that is created by default when users get links | Only people in your organisation | Internal link which can only be sent to people in your organisation. |
| Other settings |  |  |
| Show owners the names of people who viewed their files in OneDrive | Checked | This is to ensure owners are aware of external users who have access to the document. |
| Let site owners choose to display the names of people who viewed files or pages in SharePoint | Checked | Permits display of activity on SharePoint sites to foster collaboration. |
| Use shorter links when sharing files and folders | Checked | Ensure URL are short and concise. |
| Default link permission | Edit | Users will have edit permissions by default to increase usability. If view permissions are required, this is also available. |

Access Control Configuration applicable to all agencies and implementation types

| Configuration | Value | Description |
| :--- | :--- | :--- |
| **Unmanaged Devices** |  |  |
| Unmanaged Devices | Allow limited, web only access | Provide restricted access to devices that are not Intune compliant. |
| **Idle session time-out** |  |  |
| Sign out inactive users automatically | On | Controls idle time on users logged onto a device. |
| Sign out users after: | 1 hour | Ensure users are logged out after an idle time. |
| Give users this much notice: | 5 minutes | Ensure users are notified before they are signed out. |
| **Network Location** |  |  |
| Allow access only from a specific IP address range | Off | Define a trusted network boundary by specifying one or more authorized IP address ranges. |
| **Apps that do not use modern Authentication** |  |  |
| Apps that do not use modern Authentication | Block access | Some third-party apps and previous versions of Office cannot enforce device-based restrictions. Use this setting to block all access from these apps. |

## Legacy Features

Legacy features allow for backwards compatibility for legacy capabilities from SharePoint on-premises to SharePoint Online. Legacy features are enabled only when there is a reason to do so, as they restrict the features available in SharePoint Online.

SharePoint Online provides legacy features by default to ensure backwards compatibility with legacy SharePoint on-premises solution.

Legacy Features Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| InfoPath | Not configured | InfoPath is going to be deprecated and it is recommended that InfoPath forms to be redeveloped into PowerApps in Office 365 |
| Records Management | Not configured | Records Management administrative screen provides configuration settings to route files from a SharePoint Document Library to a centralised SharePoint Records Management site. This is to support the traditional Centralised records management system in SharePoint. |
| Secure Store Settings | Not Configured | Secure Store in SharePoint Online provides a key vault to store all sensitive information in SharePoint. This is primarily used by InfoPath to store sensitive keys and passwords. It is recommended to use Azure Key Vault to store sensitive information. |
| Business Connectivity Settings | Not configured | Business Connectivity Settings provides SharePoint on-premises ability to consume information from third party OData Information store. It is recommended to use Power BI to consume third party data and publish it to SharePoint Online. |
| Search | Not configured | Search provides legacy support on crawled properties, managed properties and custom configuration required. |
| Term Store | To be configured based on Agency existing term store to support existing taxonomy if required. | Term store is configured for the solution if required by Agency. Term store provides a consistent taxonomy and ontology for the Agency. This enables ease of search for information within SharePoint. |
| User Profile | Not configured | User Profiles provide legacy support of custom properties for users and complied audience. |
| Hybrid Picker | Not configured | This is to ensure hybrid term stores are synchronised between SharePoint Online and on-premises. |

