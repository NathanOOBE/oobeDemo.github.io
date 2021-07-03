# Office 365 Organisation

## Residency

Office 365 is a global service which is offered in many different physical regions. Choosing a region to store data is required to ensure that the data of the Agency does not get transferred or stored offshore.

Office 365 tenant residency is critical when setting up the Agency's Office 365 tenant. The region where the Office 365 tenant is set up determines where the data is store. Details of Office 365 data residency can be found from [Microsoft's site](https://products.office.com/en-au/where-is-your-data-located).

Office 365 tenant data residency consideration is required to ensure the Agency's Office 365 tenant is created and data is stored in Australia.

Office 365 Region Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Office 365 Region | Australia | Aligns with ACSC guidance. |

## Licence

Microsoft licenses access to Office 365 and its security offerings through user-based licensing.

Microsoft offers several enterprise licencing options for Office 365, Enterprise Mobility and Security \(EMS\), and Windows.

These licencing options are summarised below:

* Microsoft 365 E5 \(recommended for this Blueprint\) – Top level Enterprise Plan. Microsoft 365 E5 includes everything inside Microsoft 365 E3 plus additional features and services \(largely security and compliance related\). In the case of Office 365 E5, the capabilities in Office 365 Advanced Threat Protection \(ATP\) suite as well as other services such as Office 365 Advanced Compliance are increased.
* Microsoft 365 E3 - Mid range Enterprise Plan. Microsoft 365 E3 provides access to core products with enhanced features and security features. In the case of Office 365 E3, the Office client suite is included, and the service limits are increased.

To grant access to the services a license is assigned to an individual user account. A license can be assigned by an administrator at the time of the user account is created or through Azure AD group-based licensing. Azure AD group-based licensing allows an Administrator to associate a license to a group. Any members within the group will be assigned that license automatically. When a user is removed from the group the license is removed.

Licencing Design Decisions for all agencies and implementation types

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Products Licenced | Microsoft 365 E5 | Microsoft 365 E5 licences combines Office 365 E5, EMS E5, and Windows 10 E5 are required to ensure that Office 365 tenant can be rated up to Protected. |
| Licence Allocation Method | Automated | Dynamic Security Groups in Azure AD will be used to automatically assign licences and reduce the management overhead associated with licensing. |

Licencing Configuration for all agencies and implementation types.

| Configuration | Value | Description |
| :--- | :--- | :--- |
| Admin Licence Group | `rol-AgencyName-Administrator` | This is the group that the Agency administrators belong to. |
| User Licence Groups | `rol-AgencyName-Users` | This is the group that the Agency non-administrator users belong to. |

## Self Service Purchase

Self-Service purchase add-ins for Office 365 allows users of Office 365 to purchase 3rd party add-ins to be added into Office 365 tenancy.

Self-service purchase of applications from the Microsoft Power Platform products was introduced in January 2020. By default, this is enabled for all users within the tenant and paid by credit card.

These processing of data for these add-ins does not sit within Office 365 tenancy. This might cause the data to flow outside and/or stored outside of Australia.

Self-Service Design Decisions for all agencies and implementation types

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Global self-service purchase | Disabled | Only administrators are permitted to purchase applications |
| Power BI self Service purchase | Disabled | Only administrators are permitted to purchase applications |
| Power Apps self-service purchase | Disabled | Only administrators are permitted to purchase applications |
| Power Automate \(Flow\) self-service purchase | Disabled | Only administrators are permitted to purchase applications |

## Themes

Office 365 Themes provide a method to customise the portal's look and feel for users.

The logo of the organisation can be added to the top navigation panel. Themes assist users with familiarisation and adoption of the new system.

Theme Design Decisions for all agencies and implementation types

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Custom Portal Theme | Configured | Customising the Theme setting assists user to identify that they are in the correct portal. |

Note: Themes will be the responsibility of the Agency and this table contains recommendations and restrictions for the themes.

Theme Configuration for all agencies and implementation types

| Configuration | Value | Description |
| :--- | :--- | :--- |
| Logo Image | Agency logo is recommended | Under 10 KB, 200 x 30 pixels in JPG, PNG, GIF, or SVG format. SVG is the preferred format. |
| Background Image | Agency logo is recommended | 15 KB or less, 1366 x 50 pixels in JPG, PNG, or GIF format. This is in line with Microsoft best practice. |
| Prevent users from overriding their theme | Yes | Flip this toggle to prevent users from choosing their own theme from the Microsoft theme gallery. This is enabled to maintain cadence between potential personal tenancies and the 'corporate' environment. |
| Navigation bar colour | Default | Based on Agency branding standards. To maintain cadence with corporate standards. |
| Text and icon colour | Default | Based on Agency branding standards. |
| Accent Colour | Default | Based on Agency branding standards. |
| Show the users name on the top navigation bar when the user is signed in | Yes | The users name will be shown to identify who is signed in. |

## Office 365 Services and Add-Ins

Office 365 centrally manages Office services and add-ins. Office services and add-ins can enhance both the way information is accessed and the way business is conducted. Enabling Services and Add-ins also comes with risks \(such as the risk of data loss\). Out of the box several services and add-ins are configured within the portal.

The design will take into consideration the services and add-in that are part of Office 365. The design decision is based on the requirement provided by the Agency and location of the application that is hosted on.

Services and Add-ins Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Azure Speech Services | Disabled | Default setting |
| Bookings | Disabled | Exposes a public web page. No requirement. |
| Calendar | Disabled | External sharing is disabled to prevent potential data spills. |
| Cortana | Disabled | To align with ACSC Windows 10 1709 hardening, Page 55. |
| External Form sharing | Disabled | Microsoft Forms is hosted outside of Australia. |
| Microsoft Graph Data Connect | Enabled | API connectivity required for solution management. |
| Microsoft Planner | Enabled | Internet calendars will be enabled, it is up to the Agency which calendars they wish to publish. |
| Microsoft Search in Bing | Disabled | Microsoft Search integrates with bing.com for Search. Office 365 data is indexed to provide bing.com search functionality and is therefore not desirable for this design. |
| Microsoft communication to users | Disabled | System admins will be responsible for communication to users |
| Modern Authentication | Enabled | Modern authentication is a group of technologies that combines authentication, authorisation and conditional access policies to secure an Office 365 tenant. Enabling of Modern Authentication provides ability to use Multi Factor Authentication. |
| MyAnalytics | Enabled | Provides users with details about their usage of Office 365 |
| External Office 365 group content sharing | Enabled | External collaboration will be conducted in Microsoft Teams which relies on Office 365 groups |
| ‎Office‎ software download settings | Disabled | Only one instance of the Office Suite is to be installed per user on their Government issued device. Office applications will be deployed to users via the Business Store. |
| Office What's New management preview | Disabled | System admins will be responsible for communication to users. |
| Office on the web | Disabled | Do not allow users to open files in third party storage |
| Reports | Disabled | Disable data reporting to Microsoft on Office 365 usage. |
| SharePoint | Enabled | New and Existing guests must sign in or provide a verification code when accessing SharePoint data. |
| External Sway sharing | Disabled | External collaboration will be conducted in teams. |
| User owned apps and services | Disabled | Applications will be delivered via the Business Store, there is no need to have the Official Store enabled. |
| Whiteboard | Disabled | Microsoft Whiteboard is not hosted in Australia. |

## Role Based Access Control

Role Based Access Control \(RBAC\) defines what an end user or administrator can do. In relation to system administration, RBAC provides various roles each of which can only perform certain tasks. For example, help desk staff may be able to only view certain resources, whereas system administrators could view, create, and delete those resources. Office 365 provides a subset of administrative roles available in Microsoft Azure.

Privileged Identity Management \(PIM\) can be leveraged to enhance the RBAC model for Azure Active Directory role-based management access, and parts of other Microsoft services like Office 365 and Intune. PIM requests are made through the Azure portal for elevated access only when they are required, and access is expired after a specified period.

The following Office 365 roles can be assigned via PIM:

* Exchange administrator
* SharePoint administrator
* Teams Service administrator
* Power BI Administrator

Role Based and Access Control Design Decisions for all agencies and implementation types

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| PIM | Configured | PIM provides time-based and approval-based role activation to mitigate the risks of excessive, unnecessary, or misused access permissions on resources that you care about. PIM |
| Office 365 administrative sub-roles | Not Configured | Office 365 administrative sub-roles will not be configured in favour of PIM. This ensures Azure is the location to manage Role Base Access Control permission for the Agency tenant. |

## Customer Lockbox

Customer lockbox provides a time-boxed, secure mechanism for Microsoft Support Engineers to assist in customers support query in Office 365. Microsoft Support engineers will have to request authorisation from the Agency to access the underlying data in Office 365 tenant.

Customer Lockbox address situations where Microsoft Engineers require access to client data within Office 365 to resolve an incident. All access requests are recorded for auditing purpose.

Customer Lockbox Design Decisions for all agencies and implementation types

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Customer Lockbox | Enable | This is to ensure the Agency approves and log interaction with Microsoft Support Engineers. |

