# Client Devices Windows 10 Standard Operating Environment

The Standard Operating Environment \(SOE\) consists of the customisations to Windows 10 that will vary between environments. The customisations are largely cosmetic and functional in nature to ensure that end users can operate efficiently.

## Operating System

The operating system allows software application to interface with the hardware. The operating system manages input and output device components like the mouse, keyboard, network and storage.

Windows 10 is available in several editions these include:

* Home – minimal management and deployment features and cannot be joined to either an on-premises or Azure AD domain. It is targeted from home use only
* Professional – this edition includes management and deployment features and can be joined to both an on-premises and Azure AD domain
* Enterprise – this edition has additional enterprise security features as well as the UE-V and App-V clients built in and only distributable through Microsoft's Volume Licensing Program

Servicing of Windows 10 falls into three distinct channels or rings:

* Windows Insider Program – Windows Insider Program receive feature updates immediately allowing pilot machines to evaluate early builds than the semi-annual channel. A business must opt-in for this service and install a specific Windows Insider Program for Business Preview build.
* Semi-Annual Channel – Semi-Annual Channel receives feature update releases twice per year and is designed for the broad population of general-purpose devices within an organisation.
* Long-Term Servicing Channel – Long-Term Servicing Channel \(LTSC\) receives releases much more gradually \(expected every 2 - 3 years\) and is designed for special purpose devices such as those used in Point of Sale \(POS\) systems or controlling factory or medical equipment, and those machines without Microsoft Office. Additionally, a number of applications are not supported on LTSC Windows devices, for example Microsoft Edge, Microsoft Store, and Microsoft Mail, amongst others.

Operating System Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Windows 10 Edition | Windows 10 Enterprise 64-bit | Enterprise is required to support BitLocker. The 64-bit edition of Windows is required to support security such as BitLocker and Windows Defender Application Control \(WDAC\) as specified by ACSC Windows 10 hardening guide. |
| Windows 10 Servicing Channels | Semi-Annual Channel | Semi-Annual Channel is the recommended ring to deploy to most enterprise clients, especially those with Office 365. |
| Windows 10 Build | 1909 | At the time of writing build 1909 is the latest Semi-annual Channel release and recommended by Microsoft. See [technet.microsoft.com/en-us/windows/release-info.aspx](https://technet.microsoft.com/en-us/windows/release-info.aspx) |

## Activation and Licencing

License keys and activation processes are leveraged by Microsoft to ensure that the device or user is eligible to use the feature or run the product \(i.e. Windows 10\).

Windows 10 licensing has evolved significantly since the initial release by Microsoft. In addition to the traditional activation methods for on premises networks \(KMS, MAK and AD Based Activation\) it is also possible to use Windows 10 Subscription Activation. The evolution of Windows 10 activation is described below:

* Windows 10, version 1909 updates Windows 10 Subscription Activation to enable step up from Windows 10 Pro to Windows 10 Enterprise for those with a qualifying Windows 10 or Microsoft 365 subscription
* Azure Active Directory \(Azure AD\) available for identity management

Office 365 products require licensing to enable full functionality and support. The available activation methods are:

* Office 365 based activation - Office 365 is Microsoft's productivity solution in the cloud. Office 365 has two sets of suites: one for the small and medium business segment and one for the enterprise segment. These suites are sold across different channels and programs designed to meet each segment's needs. Products are assigned to users and then activated through the online Microsoft Office 365 licensing service

For agencies looking to alternate licensing arrangements, at a minimum, Microsoft recommends the following licensing in addition to the VSA 4 Common Cloud Commitment:

* Microsoft 365 E5 Security
* Microsoft 365 E5 Compliance

The VSA 4 Common Cloud Commitment consists of:

* Windows 10 E3
* Office 365 E3
* Enterprise Mobility and Security E3
* Productivity server licences \(Exchange Server, SharePoint Server, Lync/Skype Server\)
* Office Device licences

These recommendations require a minimum subscription requirement of Microsoft 365 E3, Enterprise Mobility and Security E5 and Microsoft 365 E5 Compliance with one licence required for each user.

This alternate configuration will not provide access to Azure Active Directory Premium P2 licencing meaning that the following components would need to be removed from the Blueprint:

* Azure Active Directory Identity Protection
* Azure Active Directory Privileged Identity Management \(PIM\)

While this meets the Microsoft minimum guidance and will comply with the requirements of the ISM, the exclusion of these two features reduces the effectiveness of the security controls. Specifically, the Just-In-Time administrative access provided by PIM and the automated responses to detected suspicious activities will not be available.

Activation and Licencing Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Licensing for Microsoft Windows 10 Enterprise 1909 Microsoft Office 365 E5 | Microsoft 365 E5 which includes Windows 10 E5, Office 365 E5 and EM+S E5 per user | For agencies to meet their obligations under the ISM, PSPF, and ACSC cloud guidance as they relate to PROTECTED security classification. It is recommended in this design that agencies purchase a Microsoft 365 E5 licence for each user. |
| Windows Activation Method | Windows 10 Subscription | All devices will meet the requirements for Subscription Activation \(1909 and internet access\), and this is the simplest solution to implement and manage. |
| Office Activation Method | Office 365 Subscription | All devices meet the requirement for Office 365 activation \(internet access\) and this is the simplest solution to implement and manage. |

## Windows Features

Windows 10 incorporates optional features that can be enabled to offer additional functionality.

When deploying a Windows 10 SOE, removing unnecessary features from the standard installation creates a simpler image to maintain. In Windows if a feature is not required or used within an environment, its removal means a faster deployment and a simpler user experience.

Windows Features Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| .Net Framework 3.5 | Enabled | This is to meet legacy .net applications that relies on .Net Framework 3.5 and earlier |
| .Net Framework 4.8 | Enabled | This is to allow new .net applications in the Windows 10 device. |
| Windows Media Features | Enabled | Support media content functionality |
| Windows 10 Ink | Enabled | Required to support full functionality of devices to be deployed, including Handwriting support |
| Print and Document Services - Windows Fax and Scan | Enabled | Support scanning functionality |
| Printing | Enabled | Printing enabled for office use only. Printer drivers must be supported by Windows 10 |
| Microsoft Print to PDF | Enabled | Enables user support for Print to PDF |
| Microsoft XPS Doc Writer | Enabled | Enables user support for Microsoft XPS Doc Writer functionality |
| Remote Differential Compression Application Programming Interface \(API\) Support | Enabled | Required for application compatibility |
| Windows PowerShell | Enabled | Support administration scripting activities. |

## Universal Windows Platform Applications

Universal Windows Platform \(UWP\) applications are applications that run on Windows 10 and newer devices. Developers can build line of business Windows Store apps using standard programming languages. The Windows Runtime \(WinRT\) supports C\#, C++, JavaScript and Visual Basic.

UWP applications cannot access user resources unless the application specifically declares a need to use those resources. This ensures a clear connection between apps and the types of resources the app has access to.

Universal Windows Platform Applications Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Windows 10 SOE Footprint | Reduce | The Agency will reduce the size of the Windows 10 SOE footprint by configuring the settings in Table 38 unless the Agency has a specific requirement for these applications to be enabled. |

Universal Windows Platform Application configuration applicable to all agencies and implementation types

| Configuration | Value | Description |
| :--- | :--- | :--- |
| Alarms and Clock | Removed | A versatile combination of alarm clock app, world clock, timer, and stopwatch. |
| Bing | Removed | Weather and News |
| Calculator | Provisioned | A calculator that includes standard, scientific, and programmer modes, as well as a unit converter. |
| Camera | Removed | The redesigned Camera is faster and simpler than ever before. |
| Mail and Calendar | Removed | The Mail and Calendar apps provides access to a user's email, schedule, and contacts. This access will be granted through Outlook. |
| Maps | Removed | Provides search functionality for places to get directions, contact numbers, business info, and reviews. |
| Microsoft OneDrive | OneDrive personal removed. OneDrive for Business will be used. | OneDrive is a cloud storage, file hosting service that allows a user to synchronise files and later access them from a web browser or mobile device. |
| Microsoft Solitaire Collection | Removed | Microsoft Solitaire Collection on Windows 10. |
| Microsoft Video | Removed | The Movies & TV app brings a user the latest entertainment in one simple, fast, and elegant app on Windows. |
| Mixed Reality | Removed | 3D Viewer, Print 3D, Mixed Reality Portal |
| Mobile | Removed | Your Phone, Mobile Plans, Connect App |
| OfficeHub | Removed | MyOffice |
| OneNote | Provisioned | Microsoft OneNote Application |
| Paint3D | Provisioned | Microsoft Paint3d Application |
| People | Removed | The People app in Windows is a modern take on the flat contact lists of the past. It is built for the way people communicate today and is connected to cloud services. |
| Photos | Removed | The best place to enjoy, organise, edit, and share digital memories. |
| Snip and Sketch | Provisioned | Capture a specific area of the screen. |
| MS Paint | Provisioned | Creative paint and drawing tool. |
| Sticky Notes | Provisioned | Sticky Notes |
| Store | Microsoft Store for Business will be used. | Shopfront for purchasing and downloading applications. |
| Microsoft Xbox | Removed | The Xbox experience on Windows 10. The Xbox app brings together friends, games, and accomplishments across Xbox One and Windows 10 devices. |
| Zune | Removed | Groove Music and Movies |

## Microsoft Store

The Microsoft Store is an online store for applications available for Windows 8 and newer operating systems. The Microsoft Store has been designed to be used in both public and enterprise scenarios depending on whether the Microsoft Public Store or Microsoft Store for Business is configured.

The Microsoft Public Store is the central location for browsing the library of available Windows UWP Applications that can be installed on Windows 10. The Microsoft Public Store includes both free and paid applications. Applications published by Microsoft and other developers are available.

The Microsoft Store for Business allows organisations to purchase applications in larger volumes and customise which applications are available to users. Applications which are made available can either be distributed directly from the store or through a managed distribution approach. Applications which have been developed within the organisation can also be added and distributed as required.

Licensing can also be managed through the Microsoft Store for Business and administrators can reclaim and reuse application licenses.

Microsoft Store Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Microsoft Public Store | Disabled | Meets ACSC Windows 10 1909 hardening guidelines and aligns with security and compliance requirements |
| Microsoft Store for Business | Disabled | Meets ACSC Windows 10 1909 hardening guidelines and aligns with security and compliance requirements |

## Enterprise Applications

Enterprise applications provide organisations and end users the functionality they require to perform day to day activities.

Applications can be delivered to the user's desktop by one of the following methods:

* Intune – Ideally suited for Windows 10 only deployments. The only option for delivering application to iOS clients.
* SCCM – Ideally suited where an agency has a large existing investment of packaged applications. The only option for delivering application to servers. Only option for delivering virtual applications. 

Self-Service applications are requested by users directly. They can be delivered via Software Centre which is installed as part of the SCCM client or Company Portal which is available as part of Intune and the Microsoft 365 tenant. As of SCCM version 1802 "user-available" apps now appear in Software Centre under the applications tab where they were previously available in the Application Catalogue

Packaging methodology should be inherited from existing Agency procedures as each application has unique requirements. It is possible to repacked existing applications into an msix format which is compatible with both Intune and SCCM delivery.

Enterprise Applications Design Decisions for cloud native implementations

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Application Delivery Technologies | Deployed via Intune | Applications deployed via Intune and will be installed during the build deployment. |
| Self Service | Company Portal | Allow users to install the apps needed while ensuring the SOE remains as light weight as possible. |
| Packaging Methodology | Agency preference | Applications will be packaged according to agency internal packaging standards and delivered via Intune |

Enterprise Applications Design Decisions for hybrid implementations

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Application Delivery Technologies | Deployed via Intune or SCCM | Applications deployed via Intune and will be installed during the build deployment. SCCM can continue to be used for existing applications, however consideration should be made to migrate these to Intune in future. |
| Self Service | Company Portal or SCCM Software Center | Allow users to request install of specific apps while ensuring the SOE remains as light weight as possible. |
| Packaging Methodology | Agency preference | Applications will be packaged according to agency internal packaging standards and delivered via SCCM or Intune. |

5.7 Power Management

The power settings in Windows 10 can be fully managed by Intune, SCCM, or Group Policy. Individual settings can be enforced or set as defaults that can then be changed by the user as desired.

Users can adjust power and performance options via the system tray power slider icon to:

* Better Battery / Recommended - Better Battery / Recommended provides extended battery life than the default settings on previous versions of Windows
* Better Performance - Better Performance is the default slider mode that slightly favours performance over battery life and is appropriate for users who want to trade-off power for better performance of applications
* Best Performance - Best Performance prioritizes performance over battery life

Power Management Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Power Management technology | Intune, SCCM or Group Policy | Agency preference of technology to configure power options.  If using SCCM or GPO, consideration should be made to migrate these to Intune in future. |
| Default Power Option Battery | Balanced | Default setting, no requirement to change has been identified |
| Default Power Option Powered | Better Performance | Default setting, no requirement to change has been identified |
| Allow standby states when sleeping \(on battery\) | Disabled | Meets ACSC Windows 10 1909 hardening guidelines |
| Allow standby states when sleeping \(plugged in\) | Disabled | Meets ACSC Windows 10 1909 hardening guidelines |
| Require a password when a computer wake \(on battery\) | Enabled | Meets ACSC Windows 10 1909 hardening guidelines |
| Require a password when a computer wakes \(plugged in\) | Enabled | Meets ACSC Windows 10 1909 hardening guidelines |
| Specify system hibernate timeout \(on battery\) | Enabled System Hibernate Timeout \(seconds\): 0 | Meets ACSC Windows 10 1909 hardening guidelines |
| Specify system hibernate timeout \(plugged in\) | Enabled System Hibernate Timeout \(seconds\): 0 | Meets ACSC Windows 10 1909 hardening guidelines |
| Specify system sleep timeout \(on battery\) | Enabled System Sleep Timeout \(seconds\): 0 | Meets ACSC Windows 10 1909 hardening guidelines |
| Specify system sleep timeout \(plugged in\) | Enabled System Sleep Timeout \(seconds\): 0 | Meets ACSC Windows 10 1909 hardening guidelines |
| Specify the unattended sleep timeout \(on battery\) | Enabled Unattended Sleep Timeout \(seconds\): 0 | Meets ACSC Windows 10 1909 hardening guidelines |
| Specify the unattended sleep timeout \(plugged in\) | Enabled Unattended Sleep Timeout \(seconds\): 0 | Meets ACSC Windows 10 1909 hardening guidelines |
| Turned off hybrid sleep \(on battery\) | Enabled | Meets ACSC Windows 10 1909 hardening guidelines |
| Turned off hybrid sleep \(plugged in\) | Enabled | Meets ACSC Windows 10 1909 hardening guidelines |
| Show hibernate in the power options menu | Disabled | Meets ACSC Windows 10 1909 hardening guidelines |
| Show sleep in the power options menu | Disabled | Meets ACSC Windows 10 1909 hardening guidelines |

## Windows Search and Cortana

The Windows Search feature of Windows 10 provides indexing capability of the operating and file system allowing rapid searching for content stored on an attached hard disk. Once indexed, a file can be searched using either the file name or the content contained within the file.

Cortana is a voice search capability of Windows 10. Cortana's features include being able to set reminders, recognise natural voice without the user having to input a predefined series of commands, and answer questions using information from Bing \(like current weather and traffic conditions, sports scores, and biographies\).

Cortana can be used to perform tasks like setting a reminder, asking a question, or launching the app.

Configuration of Cortana features can be managed by GPO or modern management \(such as Microsoft Intune\).

Windows Search is text-based and is built into the local operating system.

Windows Search and Cortana Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Cortana | Disabled | As per the ACSC hardening guidelines the Cortana feature will be disabled to comply with security requirements. |
| Windows Search | Enabled and configured for local content | Windows search will be limited to local items only to prevent data leakage. |

## Internet Browser

The internet browser is a software application used for accessing web pages. This browser may be built into the operating system or installed later.

Microsoft Edge Chromium is a web browser for Windows 10. It has been developed to modern standards and provides greater performance, security, and reliability. It also provides additional features such as Web Note and Reading View.

Alternate browsers may also be deployed to support specific business needs or requirements.

Internet Browser Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Default Browser | Microsoft Edge Chromium – Stable edition | To ensure compatibility and performance with modern web pages. |
| Alternate Browsers | Internet Explorer 11 | To ensure compatibility with legacy web pages. |

## Tablet Mode

Tablet Mode is an adaptive user experience feature in Windows 10 that optimises the look and behaviour of applications and the Windows shell for the physical form factor and end-user's usage preferences.

Tablet Mode is a feature that switches a device experience from tablet mode to desktop mode and back. The primary way for an end-user to enter and exit "tablet mode" is manually through the Action Centre. In addition, Original Equipment Manufacturers \(OEMs\) can report hardware transitions \(for example, transformation of 2-in-1 device from clamshell to tablet and vice versa\), enabling automatic switching between the two modes.

Tablet Mode Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Tablet Mode | Enabled by default on devices that support it. | To provide the option to manipulate Tablet Mode behaviour through the Action Centre on supported devices. |

## Fast User Switching

Fast User Switching allows more than one concurrent connection to a Windows 10 device, however only one session can be active at a time.

Fast User Switching creates potential security risks around session-jacking and credential breaches. If one user reboots or shuts down the computer while another user is logged on, the other user may lose work as applications may not automatically save documents.

Fast User Switching Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Fast User Switching | Disabled | Meets ACSC Windows 10 1909 hardening guidelines |

## Corporate Branding

Organisational branding enables a consistent corporate user experience.

Windows 10 permits the image displayed at the lock screen, logon screen, and desktop wallpaper to be customised and support various resolutions. The appropriate resolution is selected based on an image file name. Windows will automatically select the appropriate image based on the current screen resolution. If a file matching the screen resolution cannot be found, a default image file is used, and the picture stretched to fit the screen.

Custom themes can be deployed to workstations either enforcing the theme or allowing a user to customise it after the initial SOE deployment. Each client agency would be required to provide information necessary to customise the branding.

Although a system is capable of being assessed as PROTECTED, banners and backgrounds should not be set to PROTECTED in the SOE or desktop background until an IRAP assessment has been completed.

Corporate Branding Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Lock Screen | Custom Corporate wallpaper | Customised to the Agency |
| Logon Screen | Custom Corporate wallpaper | Customised to the Agency |
| Wallpaper | Custom Corporate image | Customised to the Agency |
| Account Picture | User account picture must correspond to the user security pass | Customised to the Agency |
| Theme | Custom | Customised to the Agency to set default wallpaper |
| Theme Colour | Default | Default theme is suitable for purposes |
| Windows Colour | Default | Default theme is suitable for purposes |
| Corporate Account Picture | Default | The default Windows 10 user icon will be displayed as the user account picture |
| User Ability to Change Account Picture | Disabled | Disabled to provide a consistent configuration for all agency users. |

## System Properties

The System Properties window can be customised in several ways. Within the System Properties window, the Manufacturer and Model values can be displayed.

Support information can also be populated which includes:

* Support phone number
* Support hours
* Support website

A custom OEM logo can also be displayed below the Windows logo.

The system Computer Description can also be used to display the build date, time and SOE version.

The Manufacturer value is used in the title string displayed in the support section, being "Manufacturer support". If the actual computer manufacturer were to be populated, then the support section heading would be "HP support", for example, which would be misleading for users. Setting the Manufacturer value to "Agency" would set the support section heading to "Agency support".

System Properties Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Company Name | Not Configured | Not required to support deployments |
| OEM Logo | Configured – Australian Government crest | To identify that the equipment is under Australian Government jurisdiction |
| Manufacturer Value | Configured – the Agency Name | To identify the Agency as the device owner |
| Model Value | Configured – Asset Number | To identify the device via asset label |
| Support Hours Value | Configured – Support hours of internal ICT support | To simplify Agency desktop support |
| Support Phone Value | Configured | To simplify Agency desktop support |
| Support URL Value | Configured | To simplify Agency desktop support |
| Computer Description | Configured – Asset type and model | To simplify Agency desktop support |

5.14 Start Menu

The Windows 10 Start Menu contains tiles that represent different programs that a user can launch by clicking on the tile.

The default Start Menu layout can be configured for all users that use the device. Applications can be pinned to the start menu by administrators to ensure a consistent user experience across the environment. There are three levels of enforcement which are possible within the start menu:

* Full enforcement – The start menu is deployed centrally and cannot be altered by users in any way. Applications dictated by administrators are the only items which are present in the start menu. 
* Partial enforcement – The start menu is deployed centrally and can be altered by users. An application group is deployed for corporate shortcuts and users can then add applications to the start menu in a separate application group. The centrally deployed application group cannot be altered.
* No enforcement – No start menu is defined centrally, and users can make any modification to the start menu.

Start Menu Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Start Menu Layout Enforced | Partially | Corporate application group will be enforced, with the rest of the application group able to be customised by users. End-users can customise the Start Menu to suit specific needs, including the ability to resize, reorganise and choose whether to list most recent shortcuts |

## Screen Saver

The screen saver was originally designed prevent burn-in on Cathode Ray Tube \(CRT\) and plasma screens. Modern usage of the screen saver allows the operating system to detect a period of inactivity and lock or blank the screen reducing power usage.

Screensavers should be applied at regular intervals in instances that a user may walk away from their endpoint and leave their workstation unlocked. Screensavers can also be used in some circumstances as a communication mechanism to users. Microsoft does not recommend enabling a screen saver on devices. Instead, Microsoft recommends using automatic power plans to dim or turn off the screen as this can help reduce system power consumption.

Configuration can be applied to restrict the end-user ability to configure or change the screen saver settings.

Screen Saver Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Screen Saver | Disabled | Not required, the device will be configured to sleep after 15 minutes |
| Machine Inactivity | Configured – 900 seconds | This is defined as per ACSC 1709 Windows 10 Hardening guide |
| Users Can Configure the Screen Saver | No | Disable the ability for users to configure the screen saver for all Windows 10 SOE devices |
| Require Password on Wake | Configured | Users will be required to enter their password on machine wake up. This is defined as per ACSC 1709 Windows 10 Hardening guide |

## Profiles, Personalization, and Folder Redirection

Profiles are a collection of data and settings for each user of a Windows computer. Examples of data captured as part of a user's profile are user settings, desktop shortcuts, and application settings.

Profile configuration values are specific to a single user and are stored in a single folder known as the 'User Profile'. These configuration parameters \(themes, window colour, wallpapers, and application settings\) determine the look and feel of the operating environment for a specific user.

Microsoft includes several standard options for user profiles. Alternatively, technologies such as Microsoft UE-V or FSLogix can be used to address user profile and personalisation requirements. If no user profile is configured, a desktop local profile is used, which does not backup options but performs well.

Microsoft provide the following profile management solutions:

* Local Profiles – Local user profiles are stored on the workstation. When the user logs on for the first time, a local user profile is created for the user and stored by default in `C:\Users\%USERNAME%`. Whenever a user logs on to the workstation, the user's local user profile is loaded. When the user logs off the workstation, any configuration changes made to the user's profile are saved in the user's profile
* Mandatory Profiles – Mandatory profiles are a profile that does not save profile changes and are enforced at each logon
* Roaming Profiles – Roaming user profiles are stored in a central location on the network, which is generally a shared folder on a server. When the user logs on to a workstation, the roaming user profile is downloaded from the network location and loaded onto the workstation. When the user logs off the workstation, any profile changes are saved to the network share. In addition to maintaining a copy of the roaming profile on the network share, Windows also keeps a locally cached copy of the roaming profile on each workstation that the user logs on. 

Windows 10 provides two main roaming profile technologies in User Experience Virtualization \(UE-V\) and FSLogix. FSLogix is now the preferred Roaming Profile option as it provides a consistently higher performance than UE-V and can provide a cloud-based roaming profile when configured with suitable Azure cloud storage blobs.

Profiles, Personalization, and Folder Redirection Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Folder Redirection | Redirect Windows Known Folders | Users can continue using the folders they are familiar with. Files are automatically backed up to the users OneDrive folder in the cloud |

Additional Profiles, Personalization, and Folder Redirection Design Decisions for cloud native implementations

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Profile Type | Local Profiles | Local profiles will be configured to support end-user assigned devices. This configuration assumes that users will not share devices and do not require profile backups. Enterprise State Roaming will be enabled for key backup of key user settings. |
| Known Folder Redirection Configuration | Configured as listed below in Table 75 | To enable user personalisation and provide backup of essential user data. |

Additional Profiles, Personalization, and Folder Redirection Design Decisions for hybrid implementations

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Profile Type | Roaming Profiles | Roaming profiles will be configured to support end-user assigned devices. A roaming profile management product is recommended by the vendor, Microsoft. This configuration assumes that users can share devices. |
| Known Folder Redirection Configuration | Configured as listed below in Table 76 | To enable user personalisation and backup of essential user data |

Known Folder Redirection Configuration applicable to agencies leveraging a cloud native implementation

| Folder | Path |
| :--- | :--- |
| AppData | Not Configured |
| Contacts | Not Configured |
| Desktop | `C:\Users\%username%\OneDrive\Desktop` |
| Documents | `C:\Users\%username%\OneDrive\Documents` |
| Downloads | Not Configured |
| Favourites | Not Configured |
| Links | Not Configured |
| Searches | Not Configured |
| Music | Not Configured |
| Pictures | `C:\Users\%username%\OneDrive\Pictures` |
| Videos | Not Configured |

Known Folder Redirection Configuration applicable to agencies leveraging a hybrid implementation

| Folder | Path |
| :--- | :--- |
| AppData | Not Configured |
| Contacts | Not Configured |
| Desktop | `\\\\server\share\Users\%username%\OneDrive\Desktop` |
| Documents | `\\\\server\share\Users\%username%\OneDrive\Documents` |
| Downloads | Not Configured |
| Favourites | Not Configured |
| Links | Not Configured |
| Searches | Not Configured |
| Music | Not Configured |
| Pictures | `\\\\server\share\Users\%username%\OneDrive\Pictures` |
| Videos | Not Configured |

## Operational Support

Windows 10 and supporting management tools offer various SOE support features to allow support personnel to access a machine remotely or provide users with the option to perform automated repairs.

The following support components are available to support Windows 10:

* Intune – Intune can remotely wipe, reset and remove a device from Azure AD. These functions are controlled by role-based administration, permitting only certain administrators to control these settings.
* Windows Remote Management \(WinRM\) – WinRM is the Microsoft implementation of the WS-Management Protocol, a standard Simple Object Access Protocol \(SOAP\) based, firewall-friendly protocol that allows hardware and Operating Systems from different vendors to interoperate
* WS-Management protocol - The WS-Management protocol specification provides a common way for systems to access and exchange management information across an IT infrastructure. WinRM and Intelligent Platform Management Interface \(IPMI\), along with the Event Collector are components of the Windows Hardware Management features
* Windows Remote Assistance – Windows Remote Assistance in Windows 10 uses the Remote Desktop Protocol \(RDP\) protocol to provide a remote desktop connection that is interactive between the locally logged on user and a remote user
* Remote Desktop – Remote Desktop enables a user to remotely logon interactively to a workstation from another computer with a supported Remote Desktop client
* Remote Control – Remote control options are limited to the following:
  * TeamViewer which is a paid service that fully integrates in Intune
  * Remote Control within SCCM is this is configured in a hybrid deployment
  * Microsoft Teams assuming the user can share the desktop

Operational Support Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Intune | Enabled | Intune management functions cannot be disabled when a device is enrolled in Intune and Azure AD. |
| WinRM | Enabled | To meet operating support requirements for the Agency. Consideration should be made to harden the use of WinRM in the agency environment to increase the security of Windows 10 endpoints. |
| Windows Remote Assistance | Disabled | Aligns with Windows 10 1909 hardening guide |
| Remote Desktop | Enabled | To meet operating support requirements for the Agency. Access granted via AD Groups |
| Remote Desktop Client | Enabled | Remote Desktop will be enabled for Windows 10 devices |
| Remote Control via Teams | Enabled | Users can share desktop within the Microsoft Teams application |

## Windows Update and Patching

Many updates released for operating systems and application contain bug fixes and security updates. Vulnerabilities can be exploited by malicious code or hackers and need to be patched as soon as possible.

A risk assessment of a vulnerability is essential in determining the timeframe for applying patches. There are many different sources and indicators that will help with this assessment, for example if the vendor releases a patch outside of their normal patching cycle and its marked as a critical update then it is worth immediate investigation and deployment to see how it could affect an organisation.

It is vital to have a robust and reliable patch management solution based on industry best practices.

For Microsoft Windows environments the primary patching technologies are:

* Windows Server Update Service – WSUS enables administrators to deploy the most recent Microsoft updates. A WSUS server connects directly to Microsoft Update or an "upstream" WSUS server. This allows administrators to control what updates are applied and when, rather than having every computer on the network going to the Internet and installing every available update immediately
* Microsoft System Centre Configuration Manager \(SCCM\) –SCCM integrates with a WSUS server to deliver patch management. WSUS obtains updates from the internet and SCCM is used to approve and deploy the updates. Using SCCM to deploy software updates allows for more control over many aspects of the process such as targeting, maintenance windows, scheduling, and reporting
* Microsoft Intune – Windows Update for Business provides management policies for several types of updates to Windows 10 devices
  * Feature updates: feature updates contain security and quality revisions, significant feature additions and changes; they are released semi-annually in March and September
  * Quality updates: these are traditional operating system updates, typically released the second Tuesday of each month \(though they can be released at any time\). These include security, critical, and driver updates. Windows Update for Business also treats non-Windows updates \(such as those for Microsoft Office or Visual Studio\) as quality updates. These non-Windows Updates are known as "Microsoft updates" and can configure devices to receive or not receive such updates along with their Windows updates
  * Driver updates: these are non-Microsoft drivers that are applicable to the devices. Driver updates can be turned off by using Windows Update for Business policies
  * Microsoft product updates: these are updates for other Microsoft products, such as Office. These updates can be enabled or disabled by using Windows Update for Business policy

Update rings are policies that are assigned to groups of devices. Intune can define update rings that specify how and when service updates are deployed to Windows 10 devices. By using update rings, it is possible to create an update strategy that mirrors business needs

To deploy patches to endpoints as quickly as possible, client-side settings should not restrict or delay the installation of patches where it does not interfere with critical operation or cause loss of data due to unexpected reboots.

Windows Update and Patching Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Patching technology | Agency preference of Intune, SCCM or WSUS | For cloud native deployments, Intune is the only option available.  For hybrid deployments, all three options are available for implementation. Intune provides a simpler approach to patching whilst SCCM and WSUS provide more granular control of patch deployment. |
| Patching Testing Method | Pilot and Production | Allows early deployment and test of Windows updates to selected users prior to the full release of updates to the remaining users.  The Pilot group will be a select number of users who will actively provide feedback on updates before rollout to all users |
| Feature Updates | Enabled | Meets ACSC hardening guidance for Windows 10 1709 |
| Quality Updates | Enabled | Meets ACSC hardening guidance for Windows 10 1709 |
| Driver Updates | Enabled | Meets ACSC hardening guidance for Windows 10 1709 |
| Microsoft Product Updates | Enabled | Meets ACSC hardening guidance for Windows 10 1709 |
| Patching Frequency | Existing Agency patch scheduling based on patch criticality | The Agencies existing patch schedule should reflect:   _**Extreme risk**: within 2 days_  **High risk or lower**: within 7-14 days  Meets ACSC assessing security vulnerabilities and applying patches assessment guidance |

## Networking

Windows 10 contains networking technologies built into the operating system. These features allow Windows to communicate with other networked devices including those on the Internet.

IPv6 can be enabled or disabled within Windows 10 depending on the network to which the device will be connected. IPv6 should be disabled unless it is exclusively used throughout the network.

Windows 10 provides support for several wireless networking technologies that allow devices to connect to a wireless network. The two most popular technologies supported in Windows currently are Wi-Fi and Mobile Broadband networking.

802.1x ensures that only appropriate users or devices can connect to a protected network and that data is secure at the radio transmission level. The Single Sign-On \(SSO\) feature executes Layer 2 network authentication at the appropriate time given the network security configuration, integrating with the user's Windows logon experience.

Networking Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| IPv6 | Disabled | As per ACSC hardening guidance for Windows 10 1909 IPv6 will be disabled. Exceptions to this rule are if IPv6 is wholly deployed within an Agency network with no IPv4. |
| Wireless | Enabled | Where applicable, wireless capable devices will have Wi-Fi enabled to allow use case of mobile working. |
| Wireless Configuration | Refer to Table 86 for wireless configuration recommendations. | As per ACSC hardening guidance for Windows 10 1909 and security compliance requirements. |
| Broadband | Not Configured | If Agency devices have Subscriber Identity Module \(SIM\) capability this can be enabled without affecting an agencies cyber security posture. |
| Network Bridging | Disabled | As per ACSC hardening guidance for Windows 10 1909 and security and compliance requirements. |
| Wake on LAN \(WoL\) | Configured via existing SCCM solution if in use | Wake on LAN configured to allow existing SCCM management tasks to operate on computers regardless of power status. |

Wireless Configuration applicable to all agencies and implementation types

| Configuration | Value | Description |
| :--- | :--- | :--- |
| Connect to Wireless Hotspots | Enabled | Allows users to connect to wireless hotspots when working remotely |
| Automatically Connect to Suggested Open Hotspots | Disabled | Meets ACSC hardening guidance for Windows 10 1909 and aligns with security and compliance requirements |
| Prohibit installation and configuration of Network Bridge | Enabled | Meets ACSC hardening guidance for Windows 10 1909 and aligns with security and compliance requirements |
| Single Sign On 802.1x | Enabled | Meets ACSC hardening guidance for Windows 10 1909 and aligns with security and compliance requirements |
| Wireless Profile Configuration | Configured | Will be configured depending on the Agency requirements |

## Delivery Optimisation

Delivery optimisation makes use of configurable peer-to-peer or caching technologies to decrease the internet bandwidth consumed by patches and updates.

Within an organisation application deployments and patch updates can occur daily to keep an organisation secure and provide the end users the capabilities to perform their work. These application deployments and patch updates can consume high levels of bandwidth, increasing the cost to an organisation. To allow organisations to decrease bandwidth use and cost organisations can implement Delivery Optimisation solutions within their main and remote offices. Delivery Optimisation is essentially a peer-to-peer client service that allows end clients to source installation packages and updates from other clients/servers within the network as opposed to always obtaining them from the source servers or the internet. There are two types of configuration options for Delivery Optimisation:

The following options apply to cloud native and Hybrid \(configured in Intune\):

* HTTP only, no peering:  Delivery Optimisation cloud service used to provide metadata only. Content to be retrieved from the downloads original source with peer-to-peer disabled. 
* HTTP blended with peering behind same NAT: Peer-to-peer sharing within the same network. Delivery Optimisation cloud service locates peers that connect to the internet using the same public IP and attempts to connect peers using their private subnet IP. 
* HTTP blended with peering across private group: Peers are automatically grouped by using the Active Directory Domain Services site or domain they reside in. Custom groups can also be used with peers being either manually or dynamically added to the group. Peers within the same group are connected.
* HTTP blended with internet peering: Enabled Internet peer sources for Delivery Optimisation
* Simple download mode with no peering:  Delivery Optimisation cloud services are disabled. This mode is automatically used with the Delivery Optimisation cloud service is not accessible or when the content file size is less than 10 MB.
* Bypass mode:  Microsoft BITS will be used instead and should only be used if WSUS is in use and the preference is for BranchCache. 

The following options apply to Hybrid \(configured in SCCM\):

* BranchCache: Allows systems within the same subnet and separated from a content source to share downloaded content locally instead of traversing a latent network link back to the SCCM content source. 

BranchCache provides two modes of operation being:

* Distributed Cache Mode - Content cache at a remote office is distributed among client systems
* Hosted Cache Mode - Content cache at a remote office is hosted on one or more hosted cache servers
* Peer Cache: Is a built-in Configuration Manager solution that allows the clients to share content with other clients directly from their local cache providing Delivery Optimisation. 
* Microsoft Connected Cache: With SCCM version 1910 a SCCM distribution point can be configured as a Microsoft Connected Cache server allowing it to act as an on-demand cache for content downloaded by Delivery Optimisation. 

Delivery Optimisation Design Decisions for cloud native implementations

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Delivery Optimisation Method / Feature - single subnet per physical office | HTTP blended with peering behind same NAT | Good for single subnet per office as content will be peered per office only. This will not saturate WAN connections |
| Delivery Optimisation Method / Feature - single subnet spanning multiple physical offices | HTTP blended with peering across private group | Provides the ability to group workstations so only the groupings can peer content |

Delivery Optimisation Design Decisions for hybrid implementations where SCCM is the update delivery mechanism

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Delivery Optimisation Method / Feature | BranchCache | Existing SCCM solution exists with BranchCache Delivery Optimisation feature enabled |
| Mode of operation | Distributed Cache Mode | Existing SCCM solution exists with BranchCache configured in Distribute Cache Mode |

## Microsoft Office Edition

Microsoft Office is available in two release cycles and within those release cycles there are multiple editions.

Microsoft Office has two release cycles:

* Office 365 – Office 365 combines the Microsoft Office desktop suite with cloud-based versions of Microsoft's communications and collaboration services—including Microsoft Exchange Online, Microsoft SharePoint Online, Office Online, and Microsoft Teams. Office 365 is upgraded with new features on a regular basis
* Traditional Office – Traditional Office is sold as a one-time purchase and provides Office applications for a single computer. There are no upgrade options which means to upgrade to the next major release, another copy of Office will have to be procured. Traditional Office is not upgraded with new features for the life of the release

Within these release cycles, you can choose the architecture of 32-bit or 64-bit. Microsoft Office provides 32-bit or 64-bit version to be installed on Windows 10 devices. Microsoft 64-bit version of Office will be automatically chosen to be installed, unless 32-bit version is installed. The 64-bit version of Office provides ability working with larger datasets and files. However, 64-bit version of Office does not support legacy macros, and COM Add-In.

Pro Plus is an optional configuration which installed Office 365 locally on a client machine

Microsoft Office Edition Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Microsoft Office Version | Office 365 Pro Plus 64-bit | Aligns with modernisation vision and provides access to the latest and most updated features. |

## Office Features

The Office 365 ProPlus features include the application set that will be provided to the users.

The Microsoft Office feature section includes the details of the following components:

* Microsoft Access
* Microsoft Excel
* Microsoft Teams
* Microsoft Office OneNote
* Microsoft Outlook
* Microsoft Publisher
* Microsoft PowerPoint
* Microsoft Word
* Microsoft OneDrive Desktop

Office Features Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Microsoft Office Word | Enabled | Required to enable user productivity |
| Microsoft Office Excel | Enabled | Required to enable user productivity |
| Microsoft Office Outlook | Enabled | Required to enable user productivity |
| Microsoft Office PowerPoint | Enabled | Required to enable user productivity |
| Microsoft Office OneNote | Enabled | Required to enable user productivity |
| Microsoft Office Publisher | Enabled | Required to enable user productivity |
| Microsoft Teams | Enabled | Required to enable user productivity |
| Microsoft Office Access | Disabled | Not installed by default |

## Office Language Pack

Language packs add additional display, help, and proofing tools to Microsoft Office. Multiple language packs can be installed to support specific user requirements.

If additional language packs are installed it is also likely that keyboards other than US will be required.

Office Language Pack Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Default Language | English \(UK\) – AU Default | Required to support the Microsoft Office deployment and allow user productivity. English \(US\) language pack is removed from the SOE as part of the English \(UK\) install. English \(UK\) contains the AU region language pack which is then set as default |
| Additional Language | Not Configured | Additional languages will be installed if required to meet agency requirements |

## OneDrive for Business

OneDrive for Business provides a robust cloud storage platform for government agencies.

This OneDrive for Business section considers the client component only. The configuration of the server component of OneDrive for Business is contained in the Office 365 Solution Overview document.

OneDrive enables the secure sharing of files inside and outside an organisation, and on any compatible device. Compliance settings allow administrators to control the level of security within the application.

OneDrive also facilitates collaboration between users. Co-authoring is available via Office web apps, Office mobile apps, and Office desktop apps, helping users maintain a single working version of any file and edit concurrently.

The OneDrive for Business client has access to two distinct primary rings and an additional preview ring:

* Production Ring – The Production ring provides new features and improvements as soon as they are released by Microsoft
* Enterprise Ring – The enterprise ring rolls out changes after validated in the Production ring, reducing the risk of issues. This ring enables administrators to deploy updates from an internal network location and control the timing of the deployment \(within a 60-day window\). This is the recommended update ring for most large scale or high-risk organisations
* Insiders Ring – Insider ring users will receive builds that let them preview new features coming to OneDrive

The Windows Known Folder feature of OneDrive for Business enables administrators to easily move files in a users' Desktop, Documents, and Pictures folders to OneDrive.

OneDrive Files On-Demand enables users to view, search for, and interact with files stored in OneDrive from within File Explorer without downloading them all to the local device. The feature delivers a unified look and feel for both OneDrive and local files whilst saving on space normally taken up on the local hard drive.

OneDrive allows users to work on content that is stored online in the cloud as well as store and synchronise content locally through the OneDrive for Business client. Synchronising this content between the client device and OneDrive storage can consume a considerable amount of bandwidth especially if the internet connection is slow. The OneDrive for Business client provides the capability to shape upload and download rates for synchronising content hence reducing the impact on the network. If the internet connection is too slow the end user can continue to work on the content locally and the content will be automatically synchronised by OneDrive for Business client when the internet connection speed improves.

OneDrive for Business Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| OneDrive for Business | Enabled and silently configured | OneDrive will be configured without user intervention on sign in |
| Sync Client Update Ring | Enterprise | As per Microsoft recommendations for large environments |
| OneDrive Personal Account | Disabled | Personal accounts will be disabled. OneDrive for Business accounts will be used |
| Default Location | `%userprofile%` | Default OneDrive folder location is suitable for the Windows 10 SOE |
| Allow Changing Default Location | Disabled | As per Microsoft recommendation for shared devices users will be prevented from changing the default OneDrive folder location |
| Files On-Demand | Enabled | Files On-Demand will be configured to save storage space on users' computers and minimize the network impact of sync |
| Backup - Sync Windows Known Folders | Enabled | Syncing Windows known folders to OneDrive for Business will be configured for the Windows 10 SOE. This will enable the users Documents, Pictures and Desktop folders to be saved in OneDrive automatically |
| Network settings – Upload | Do not limit | Allow dynamic network configuration to provide best performance |
| Network settings – Download | Do not limit | Allow dynamic network configuration to provide best performance |
| File Collaboration Policy | Enabled | File collaboration will be enabled to allow users to work collaboratively and increase productivity |
| Sync Conflict Policy | Let me choose to merge changes or keep copies | The OneDrive sync conflict policy will be configured to allow the user to choose |

