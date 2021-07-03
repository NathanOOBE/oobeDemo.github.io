# Platform Client Configuration

## Microsoft Endpoint Manager - Intune

Microsoft Endpoint Manager - Intune \(Intune\) is an Microsoft 365 service that provides Mobile Device Management \(MDM\) and Mobile Application Management \(MAM\) capabilities for Apple iOS, Google Android and Microsoft Windows devices to enhance security and protection.

Intune manages which devices can access corporate data, protects company information by controlling the way data is shared, and enforces device configuration to ensure security requirements are met. It does this via:

* Device Enrolment Profiles – Prior to managing devices in Intune they must be enrolled as either Personal or Corporate devices. These can either be self-enrolled or automatically enrolled.
* Device Compliance Policies – Device Compliance Policies are rules, such as device PIN length or encryption requirements, that can be applied to devices. These rules must be met before a device is considered compliant. Device Compliance can then be used by services such as Conditional Access.
* Device Configuration Profiles - Device Configuration Profiles provide the ability to control settings and features on supported endpoints. These include, device and user settings, browser settings and hardware settings. Device Configuration Profiles can be deployed to specific users or devices in Azure AD groups.
* Device Security Baselines – Security baselines are pre-configured groups of Windows settings that are recommended by Microsoft security teams. The security baselines are templates and are used to create a profile that is specific to the environment for deployment.
* Client Applications – Client applications can be delivered to devices registered in Intune based on device type and group membership. Application types that can be distributed include store apps, MS Office suite, MS Edge browser, web links, line of business and Win32 applications. Monitoring of application distribution is provided.
* Software Updates – Software update policies store the configuration of updates without the updates themselves. This prevents the need to approve individual updates allowing for a faster turnaround time. Individual policies can be created and targeted to different groups of devices.

When devices are enrolled into Intune, authorised administrators are able to view hardware details, how the device is used, and what compliance levels currently are for the device's software, hardware, and operating system.

Additionally, Intune can present a customised Company Portal to end users which can be used to install and launch applications or websites via single sign-on \(SSO\) authentication.

Intune is a component of EMS and integrates with other EMS components such as Azure AD and Azure Information Protection \(AIP\) natively. This allows for total granular visibility of all endpoints within the Enterprise Mobility Management sphere and simplifies the approach for management.

To complement this visibility, an Intune Data Warehouse can be deployed to capture and create custom reports from Intune data using a reporting service. This can assist in gaining insight into which users are using Intune, what licences are being used, operating system and device breakdowns, and compliance trends. The Data Warehouse also has the capability to export directly to Power BI and create interactive & dynamic reports.

Intune can also configure Windows Information Protection \(WIP\) polices. WIP can be deployed to:

* Protect against potential data leakage – WIP protects against potential data leakage without any impact to user functionality.
* Protect enterprise applications and data - WIP protects against accidental data leakage on enterprise-owned and personal devices. This can occur without changes to the corporate environment or applications.

Within WIP, Network boundaries are created as a network perimeter that controls what applications can be accessed on the network.

Clients managed by Intune are configured to refresh their status on an 8-hour interval. During this refresh. their policy compliance, configuration profile, and app assignments are checked. If the client is recently enrolled then the compliance, non-compliance, and configuration check-in runs more frequently.

Intune Design Decisions for cloud native implementations

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Co-management | Disabled | Co-Management is disabled as this is not a function that is used in a cloud only solution. |
| Enrolled Device Types | Windows 10: 10.0.17134 \(minimum\) iOS: 14.0 | The use of Windows 10 on designated hardware is mandatory. The following platforms will be disabled: macOS Android |
| Device Compliance | Enabled | Device Compliance is enabled. All devices will be Intune enrolled and have a custom set of compliance policies applied. |
| Device Enrolment | Enabled | All users must be enrolled to ensure device compliance. |
| Company Portal | Enabled | The Company Portal is enabled for application deployment. Applications to be deployed will be set by requirements. |
| Conditional Access | Enabled | Conditional Access is enabled. It will leverage device & user compliance to allow or disallow access to the corporate environment. |
| Mobile Device Management \(MDM\) | Enabled | MDM will be used to control what a user can and cannot do on their mobile device defined by policies set by administrators. |
| Mobile Application Management \(MAM\) | Enabled | MAM will be used to ensure that users have access to the apps they need to do their work. |
| Windows Information Protection mode | Configured | Default settings prevent copying and pasting of data between 'work' locations and other 'personal' locations. |
| Network Boundaries | Cloud resources | Network boundaries create a list of resources that are considered to be on the enterprise network. These boundaries are used to apply policies that reside in these locations. |
| Cloud Resources Protected via Network Boundaries | SharePoint Office 365 | Different policies will be created depending on the network location of the client. |
| Intune Data Warehouse | Not enabled | While this feature is available, it will not be deployed for the solution. |
| **Self Service Group Management** |  |  |
| Owners can manage group membership requests in the Access Panel | No | Group creation and modification is to be locked down and controlled by authorised personnel, such as service desk staff, or Administrators. |
| Restrict access to Groups in the Access Panel | No | Accessing groups is an Administrative function and has been locked down to Administrators. |
| **Security Groups** |  |  |
| Users can create security groups in Azure portals | No | Group creation and modification is to be locked down and controlled by authorised personnel, such as service desk staff, or Administrators. |
| **Microsoft 365 groups** |  |  |
| Users can create Microsoft 365 groups in the Azure portals | No | Group creation and modification is to be locked down and controlled by authorised personnel, such as service desk staff, or Administrators. |
| **Directory-wide Groups** |  |  |
| Enable an "All Users" group in the directory | No | This group is not required. All users to be a member of a controlled group. |

## Intune - mobile application management

Mobile Application Management \(MAM\) allows the management and protection of an Agency's data within an application. It controls data flows into and out of the application container which houses corporate data.

Using MAM, a corporate app that contains sensitive data can be managed on a wide variety of devices. Many productivity apps, such as the Microsoft Office apps, can be managed by Intune MAM. MAM can protect data within the application container using authentication methods and copy/paste controls, but these controls must be balanced with any MDM controls of the device to maintain usability of the solution.

When deploying a hybrid solution, the management of Windows devices should be considered when choosing to implement MAM for clients. Management solutions such as Group Policy and MECM can provide functionality to control applications which negates the use of MAM on Windows machines.

Mobile Application Management Design Decisions for cloud native implementations

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Mobile Application Management Method | Windows 10 – Intune iOS - Intune | Mobile applications \(Windows 10 and iOS\) will be deployed via Intune. |
| Applications Managed | Microsoft Azure Information Protection Microsoft Corporate Portal Adobe Reader Microsoft Suite -  Outlook Word Excel Teams PowerPoint OneNote OneDrive | These core Microsoft business applications will be managed via Intune as they will be deployed to all Windows 10 and iOS users. |

Mobile Application Management Design Decisions for hybrid implementations

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Mobile Application Management Method | Windows 10 – Not Configured iOS - Intune | Agencies operating in hybrid environments can elect to have Windows 10 applications managed by an existing management solution such as MECM and Group Policy, or to manage Windows 10 applications via Intune. This Blueprint offers an example of using MECM as the Windows10 Management tool for illustrative purposes however agencies can elect to have Intune as the primary MAM method for both platforms without affecting cyber security postures. Mobile applications \(iOS\) will be deployed via Intune. |
| Applications Managed | Microsoft Azure Information Protection Microsoft Corporate Portal Adobe Reader Microsoft Suite -  Outlook Word Excel Teams PowerPoint OneNote OneDrive | Agencies operating in hybrid environments can elect to have Windows 10 applications managed by an existing management solution such as MECM and Group Policy, or to manage Windows 10 applications via Intune. This Blueprint offers an example of using MECM as the Windows10 Management tool for illustrative purposes however agencies can elect to have Intune as the primary MAM method for both platforms without affecting cyber security postures. Mobile applications \(iOS\) will be deployed via Intune. |

## Intune - enrolment

Device enrolment registers the Windows 10 and iOS devices into the corporate device management solution and ensures the device is then able to be managed by administrators.

Microsoft Intune provides a mechanism for enrolling devices into Azure AD. Once registered the device is populated into Intune policy groups using dynamic membership. This ensures that the device meets the compliance policy, monitored, and secured to the Agency's security requirements.

Microsoft Intune provides three separate experience in enrolling the iOS devices into the Agency's Azure Active directory. The enrolment experiences are:

* Device Enrolment Program \(DEP\) – Device Enrolment Program is a managed device enrolment process. The devices serial number is registered with Apple Business Manager allows Intune to bypass Assisted Setup by preconfigure device settings. The user's account will be assigned to the device. The device will be marked as a Supervised device.
* Device Enrolment Manager \(DEM\) – Device Enrolment Manager assigns a single Azure Active Directory account as the owner of the device. The end users cannot administer or purchase any apps on the device.
* User Enrolment – User enrolment process requires users set up the iOS device and manually install Company Portal to register the device as Intune enrolled device. The device will be marked as a BYOD device.

Intune Enrolment Design Decisions for cloud native implementations

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Windows Enrolment | Configured | Windows 10 devices must be enrolled in Intune prior to management of the device. |
| iOS Enrolment | Configured | iOS devices must be enrolled in Intune prior to management of the device. |

## Intune - co-management

Co-management provides the ability to manage devices via MECM and Intune.

For a deployment to be enabled for co-management, devices must be Azure AD joined, be enrolled in Intune and have the MECM client installed.

Once co-management is enabled, management tasks such as compliance policies, Windows Update policies, resource access policies, and endpoint protection, can be moved from MECM management over to Intune as required.

Microsoft cloud-hosted services offer the benefit of maintaining cadence with the latest technology updates from Microsoft with reduced effort required by IT BAU teams. Microsoft Intune and Microsoft's co-management strategy is constantly evolving with additional services published regularly.

Intune deploys and manages first-party Microsoft applications in a simple manner but does not allow for a large amount of customisation of update schedule, granular application deployment or application add-ons. Intune does not provide the ability to deploy and update third-party applications in a simple manner at time of writing.

Intune also provides a patching mechanism which simplifies the deployment of Microsoft first-party updates for applications and Windows 10 but does not allow granular control over patches.

The following figure provides an overview of co-management. Figure reproduced from [https://docs.microsoft.com/en-us/mem/configmgr/comanage/overview](https://docs.microsoft.com/en-us/mem/configmgr/comanage/overview)

![Co-management overview](https://github.com/oobeDemo/NewBlueprint/tree/f48ec29dcba45b149369e2d400a57f730443491b/assets/images/platform-intune-comgmt.png)

Intune Co-Management design considerations and decisions apply to the HYBRID solution.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Co-management | Enabled | The Microsoft co-management approach will enable Agency to strategically move device management from on-premises to the cloud in a staged manner. |
| Compliance policies controlled by | Intune preferred | Compliance and remediation policies to controlled via Intune. Staged migration to be completed from MECM if previously in use. |
| Device Configuration policies controlled by | Intune preferred | Device configuration policies to be controlled via Intune. Staged migration to be completed from MECM if previously in use. |
| Endpoint Protection policies controlled by | Intune preferred | Endpoint protection, including the Windows Defender products and features are controlled via Intune policies. Staged migration to be completed from MECM if previously in use. |
| Resource Access policies controlled by | Intune preferred | Resources in this instance refers to VPN profiles, Wi-Fi profiles, certificate profiles, etc. are controlled via Intune policies. Staged migration to be completed from MECM if previously in use. |
| Office Click-to-Run policies controlled by | Intune preferred | Office Click-to-Run application deployment and updates to be managed through Intune. Staged migration to be completed from MECM if previously in use. |
| Windows Update policies controlled by | Intune preferred | Windows 10 updates will be managed via Intune update rings. Staged migration to be completed from MECM if previously in use. |
| MECM minimum version | At least MECM update 1802 | Compatible with co-management and determined by the Agency. |
| Enrolled Device Types | Windows 10: 10.0.17134 \(minimum\) | The use of Windows 10 on designated hardware is mandatory. The following platforms will be disabled: macOS Android iOS Note: iOS is permitted but controlled by Intune only |
| Device Compliance | Enabled | Device Compliance is enabled. All devices will be Intune enrolled and have a custom set of compliance policies applied. |
| User Enrolment | Enabled | All users must be enrolled to ensure device compliance. |
| Company Portal | Enabled | The Company Portal is enabled for application deployment. Applications to be deployed will be set by Agency requirements. |
| Conditional Access | Enabled | Conditional Access is enabled. It will leverage device & user compliance to allow or disallow access to the corporate environment. |
| Mobile Device Management \(MDM\) | Enabled | MECM will be the MDM authority for the solution, with Intune inspecting compliance. |
| Mobile Application Management \(MAM\) | Disabled | Not required as Group Policy will configure application controls. |

## Intune - Windows AutoPilot

Windows Autopilot provides the ability to set up and pre-configure new devices without the need for on premises infrastructure. It is also possible to use Windows Autopilot to reset, repurpose and recover devices.

Windows Autopilot provides the ability to:

* Automatically join devices – Azure Active Directory \(Azure AD\).
* Auto-enrol devices – Auto-enrol MDM services, such as Microsoft Intune.
* Restrict the Administrator – Restrict administrator account creation.
* Create and auto-assign devices – Auto assign to configuration groups based on a device's profile.

![Autopilot Deployment](https://github.com/oobeDemo/NewBlueprint/tree/f48ec29dcba45b149369e2d400a57f730443491b/assets/images/platform-autopilot.png)

Intune Windows AutoPilot Design Decisions for cloud native implementations

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Automatically Join Devices | Azure Active Directory \(Azure AD\) | Devices will automatically joint the Azure Active Directory. |
| Auto-enrol devices | Configured | Enrolled automatically into Intune MDM. |
| Restrict the Local Administrator Account | Configured | Aligns with the ACSC Hardening Microsoft Windows 10 1709 Workstations. |
| Create and auto-assign devices | Configured | For ease of management and enrolment for devices within Agency. |
| Deployment profile | Refer to DTA – Intune Enrolment -ABAC document | Deployment profile will ensure that all workstations are configured in accordance with the Agency standards with no user intervention. |

## Intune - device compliance

Device Compliance Policies are rules, such as device PIN length or encryption requirements, that are applied to devices. These policies must be met before a device is considered compliant, the device compliance status can then be used by services such as Conditional Access to grant or disallow access to applications or services.

Microsoft Intune can control access to resources by interrogating endpoints and determining whether they meet a minimum list of features and are judged as "compliant". Compliance can be assigned a grace period where a device which is not judged as compliant can still access resources for a period or be blocked immediately.

Each compliance policy can be edited to ensure that devices are tested before being allowed access to corporate resources.

Device Compliance Profiles deployed ensure a strong security posture for the entire Windows 10 and iOS fleet. Compliance Policies allow the Agency to ensure that baselines are met prior to access being granted to any corporate applications or data. The Windows 10 compliance policy settings include:

* Device Health – This includes BitLocker status and whether code integrity is enabled.
* Device Properties – Including a minimum and maximum Operating System version.
* Configuration Manager Compliance – Whether the endpoint is compliance will all Configuration Manager evaluations. This is especially applicable in a co-managed scenario such as this deployment.
* System Security – Password compliance, standards, length, and complexity. This also includes device level firewall, TPM, Antivirus, Antispyware, and Microsoft Defender Antimalware settings.
* Microsoft Defender ATP – Configures the maximum allowed machine risk score, if exceeded the device is marked as noncompliant.

Device Compliance Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Compliance Assessment | Configured | Since mobile devices routinely leave the office environment, and the protection it affords, it is important that organisations develop a mobile device usage policy governing their use. |

## Intune - device configuration

Device Configuration Profiles provide the ability to control settings and features on supported endpoints. These include, device and user settings, browser settings, and hardware settings. Device Configuration Profiles can be deployed to specific users or devices by using Azure AD groups.

There are many supported platforms, each of which have several profile sub-types that they offer configuration for, at the time of writing, the following platforms are supported:

* Android device administrator
* Android Enterprise
* iOS/iPadOS
* macOS
* Windows Phone 8.1
* Windows 8.1 and later
* Windows 10 and later

Within each platform there are number of profile types allowing many settings to be configured. The profile types and settings that are configurable vary depending on the platform.

In general terms, configuration profiles either configure the device for use by the user or secure the device.

Custom profiles can be created for a platform although this should be considered a last resort if the settings are not available in any other way.

In a co-managed state, these settings may be superfluous to existing Group Policies and SOE settings.

Device Configuration Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| iOS policies | Configured | Intune policies are applied easing management. |
| Device security policies | Configured by exception | Security baselines as discussed below provide a better option when the settings are available. |

Additional Device Configuration Design Decisions for cloud native implementations

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Windows 10 and later polices | Configured | Intune policies are applied easing management. |

Additional Device Configuration Design Decisions for hybrid implementations

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Windows 10 and later polices | Not Configured | Management solution such as MECM and Group Policy are applied to manage settings. |

## Intune - security baselines

Security Baselines are pre-configured groups of Windows settings that are recommended by Microsoft. The security baselines are templates and are used to create a profile that is specific to the environment for deployment and applied to enrolled devices.

Within Intune, pre-configured Security Baselines profiles can be associated to devices to align them with Microsoft security best practices. These profiles contain multiple device specific configuration profiles and control several security related settings such as, but not limited to:

* App Runtime
* Autoplay
* BitLocker

These baselines provide robust security guidelines and are generated by Microsoft.

In the case of a co-managed / hybrid scenario, security baselines should only be used when they do not conflict with settings deployed through MECM and Group Policy.

Security Baselines Design Decisions for cloud native implementations

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Windows 10 Security Baselines | Configured | System configuration is managed via Intune. |
| Microsoft Defender ATP Baselines | Configured | System configuration is managed via Intune. |
| Microsoft Edge Baseline | Configured | System configuration is managed via Intune. |

Security Baselines Design Decisions for hybrid implementations

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Windows 10 Security Baselines | Configured | Agencies operating in hybrid environments can elect to have system configuration managed by an existing management solution such as MECM and Group Policy, or to manage system configuration via Intune. This Blueprint offers an example of using Intune as the system configuration Management tool for illustrative purposes however agencies can elect to have MECM and Group Policy as the primary system configuration method without affecting cyber security postures. System configuration will be deployed via Intune. |
| Microsoft Defender ATP Baselines | Configured | Agencies operating in hybrid environments can elect to have system configuration managed by an existing management solution such as MECM and Group Policy, or to manage system configuration via Intune. This Blueprint offers an example of using Intune as the system configuration Management tool for illustrative purposes however agencies can elect to have MECM and Group Policy as the primary system configuration method without affecting cyber security postures. System configuration will be deployed via Intune. |
| Microsoft Edge Baseline | Configured | Agencies operating in hybrid environments can elect to have system configuration managed by an existing management solution such as MECM and Group Policy, or to manage system configuration via Intune. This Blueprint offers an example of using Intune as the system configuration Management tool for illustrative purposes however agencies can elect to have MECM and Group Policy as the primary system configuration method without affecting cyber security postures. System configuration will be deployed via Intune. |

## Intune - information protection

Application protection policies are rules that ensure an Agency's data remains safe or contained in a managed application.

An application protection policy can be a rule that is enforced when the user attempts to access or move "corporate" data, or a set of actions that are prohibited or monitored when the user is inside the app.

Information Protection Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| MAM or MDM policies | MDM will be used to apply application protection policies. | MAM based policy is not able to manage non-enlightened line of business applications. \(Non-Microsoft Office apps\). |
| Desktop Protected Apps | All Microsoft Office desktop applications will be protected. Detailed settings are in the DTA – Platform – ABAC document. | No additional desktop applications are included in this Blueprint. |
| Mobile Apps | Default set will be protected on mobile devices. Detailed settings are in the DTA – Platform – ABAC document. | Default set of mobile apps covers all of the apps in this Blueprint. |
| Network Boundary – Cloud Resources | Default SharePoint URLs will be protected. Detailed settings are in the DTA – Platform – ABAC document. | If additional URLs are identified these can also be added to the Cloud Resources scope. |
| Network Boundary – Network Domain | Production domain will be protected. Detailed settings are in the DTA – Platform – ABAC document. | If additional network subnets are identified these can also be added to the Network Domain scope. |

## Intune - software updates

Windows Update for Business uses Intune to manage the installation of updates and features from Microsoft Windows Update servers. There is no requirement for on-premises servers or storage of update files.

Intune stores the update policy assignments not the updates themselves. No requirement for on-premises infrastructure.

There is no requirement or ability to selectively enable or disable a particular update.

Fast and slow update rings can be configured and assigned to different groups or users or devices allow early adopters to provide a level of validation before all users are provided with updates.

When deploying a hybrid solution, the software and patch updates of Windows devices should be considered. Other management solutions such as MECM and Windows Server Update Service \(WSUS\) may be servicing the Windows devices for the updates hence duplicating processes.

Software Updates Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Servicing Channel | Semi-Annual Channel | Aligns with ACSC guidance for Operating System updates. |
| Microsoft Product updates | Allow | Aligns with ACSC guidance for product updates. |
| Windows Drivers | Allow | Aligns with ACSC guidance for driver updates. |
| Quality Deferral period | 0 days | Aligns with general ACSC guidance for updates. |
| Feature Deferral | 0 days | Aligns with general ACSC guidance for updates. |
| Feature Update uninstall period | 10 days | Allows reversal for a short period of time in the event of breaking change updates. |

## Intune - iOS

iOS devices will be enrolled with the Intune Agency Portal to gain secure access to Agency data.

After devices are enrolled, they become managed. Agencies can assign policies and apps to the device through a mobile device management \(MDM\) provider, such as Intune.

Intune iOS Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| iOS Enrolment | Configured | iOS is commonly deployed across the Commonwealth and can be hardened in line with the ACSC hardening guide for iOS devices |
| iOS Configuration | Configurations will follow the ACSC hardening guide for iOS devices as much as possible using Intune. Refer to DTA – Intune Configuration - ABAC document. | Aligns with the ACSC Security Configuration Guide Apple iOS 14. |

## Registry settings

Registry settings are applied to the Windows registry to modify the underlying operating system. Registry settings are typically changed in a client operating system to configure the system or increase the security of system.

There are several tools available to apply registry settings such as:

* Group Policy
* Intune
* Configuration Manager \(MECM\)

The ACSC provides the Microsoft Windows and Office 365 hardening guides that defines group policy settings along with other recommendations to significantly reduce the attack surface available to malicious attacks.

Registry settings Design Decisions for cloud native implementations

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Registry Setting Method | Intune | The Agency will use Intune to implement and modify user and computer registry settings to comply with ACSC Windows and Office 365 Pro Plus hardening guides. |

Registry settings Design Decisions for hybrid implementations

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Registry Setting Method | Group Policy Objects & MECM | The Agency may utilise management solutions such as Group Policy Objects and MECM to implement and modify user and computer registry settings to comply with ACSC Windows and Office 365 Pro Plus hardening guides. |

## Applications

The lifecycle of applications can be managed using Intune. Applications can be deployed, configured, protected and removed.

Managed applications can be provisioned to the following platforms:

* Android
* iOS
* Windows Phone
* Windows 8.1
* Windows 10 and later

Applications types that can be managed include:

* Store Apps \(Android, iOS, Windows Phone, Microsoft Store and Google Play\)
* The Microsoft Office suite
* Microsoft Edge
* Microsoft Defender ATP
* Web links
* Built-In applications
* Line of Business applications
* Win32 applications
* Android Enterprise system applications

When deploying a hybrid solution, the application lifecycle method should be considered as other management solutions such as MECM may be performing the same service.

Applications Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Application Deployment | Configured | Deployment and monitoring of the deployment can be assigned to users or devices. |
| Application Configuration | Configured | Store applications are easily updated while Win32 applications will need some packaging. |
| Application Protection | Configured | In combination with conditional access and network boundaries, applications are limited with respect to the copy, paste, forwarding, printing capabilities. |
| Application Removal | Configured | When applications \(or versions of applications\) are no longer required they are removed via Agency's nominated management solution. |

## Printing

Printing is a legitimate method of data transfer out of an environment. Printing allows users to physically export data from a network and hence also it can be leveraged by malicious actors for data exfiltration. To minimize the risks associated with printing, the location where printing is allowed should be controlled.

Intune can be leveraged to control what printers are available within a device and whether a user is able to add additional local printers.

For a user to leverage an available printer, connectivity and a device driver is often required. The drivers can be delivered and updated using Intune and/or MECM. Connectivity depends on the connected network\(s\) of the client. The options include:

* Corporate Network printing – In the workplace, the domain joined computers can connect to the print servers and send jobs to the queue.
* External Network printing via Hybrid Cloud Print – Without network connectivity via Citrix, a VPN, or Microsoft Hybrid Cloud Print, direct print server connectivity is not available. Microsoft Hybrid Cloud Print utilises a reverse proxy to communicate with the print servers located within the work network.
* External Network printing via VPN – When direct printer connectivity is not available from external networks, a VPN such as Windows 10 Always-On VPN can allow clients to function as if they were part of the corporate network.

When deploying a hybrid solution, the allocation of printers to users should be considered. Other management solutions such as Group Policy and MECM may be servicing the allocation of printers to devices.

Printing Design Decisions for cloud native implementations

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Printer addition restrictions | Configured | Configured using scripts deployed via Intune. Printers must be supported out of the box in Windows 10. |
| Unsecure location Printing | Configured | Out of office printing is to be restricted as adequate controls for the creation, storage and destruction of classified content cannot be implemented |

Printing Design Decisions for hybrid implementations

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Printer addition restrictions | Configured | Management tools such as Group Policy can be used to configure printer configurations. Printers will need to be supported out of the box in Windows 10. |
| Unsecure location Printing | Configured | Out of office printing is restricted as adequate controls cannot be implemented to prevent the creation of classified content on untrusted print device. |

