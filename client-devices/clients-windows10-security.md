# Client Devices Windows 10 Security

Security settings are applied to the Standard Operating Environment largely to slow down and prevent malicious adversaries and payloads from causing harm to an Agency. The security settings should not prevent legitimate users from conducting work and should provide them with the correct amount of access to the environment to allow them to operate without impeding the work.

## Microsoft Defender

Microsoft delivers several threat protection and mitigation capabilities in Windows 10 Enterprise devices delivered through Microsoft Defender.

These capabilities do not require additional agents and are manageable via Intune Endpoint Protection Profiles.

The following details the Microsoft Defender capabilities:

* Microsoft Defender Antivirus – Provides anti-malware and spyware protection including always-on scanning, dedicated protection updates and cloud-delivered protection. Integration with Internet Explorer and Microsoft Edge browsers enable real time scanning of files as they are downloaded to detect malicious software
* Microsoft Defender Exploit Guard – Provides Host-based Intrusion Protection System \(HIPS\) capabilities and replaces the Microsoft Enhanced Mitigation Experience Toolkit \(EMET\)
* Microsoft Defender Application Guard – Provides hardware isolation of Microsoft Edge to protect against malicious websites. Protection is provided through the use of Hyper-V enabled containers isolated from the host operating system for opening untrusted websites
* Microsoft Defender Credential Guard – Provides virtualisation-based security to isolate credentials to protect against identity theft attacks. Much like Device Guard, Credential Guard uses Virtual Secure Mode \(VSM\) to isolate processes, in this case the Local Security Authority \(LSA\). The LSA performs various security operations, including the storage and management of user and system credentials. Unauthorised access to the LSA can lead to credential theft attacks, such as Pass-the-Hash or Pass-The-Ticket
* Microsoft Defender Firewall – Provides stateful packet inspection and blocking of network traffic. Windows Defender Firewall blocks unauthorized network traffic flowing into and out of the client endpoint reducing the attack surface of the device
* Microsoft Defender SmartScreen – Provides malware and phishing website protection including downloaded files. SmartScreen protects users by performing the following
  * Analysing webpages for signs of distrustful behaviour and shows a warning page if it identifies suspicious activity.
  * Validates sites against a dynamic list of known phishing and malicious software sites and shows a warning page if it identifies page
  * Validates downloaded files against a list of known software sites and programs and shows a warning page if it identifies the site or program may be malicious
  * Validates downloaded files against a list of files that are known and used by a large number of windows users. If not found on the list SmartScreen shows a warning

Microsoft Defender Exploit guard comprises of the below features:

* Exploit protection – Exploit protection applies exploit mitigation mechanisms to applications. Works with third-party antivirus solutions and Windows Defender Antivirus
* Attack surface reduction – Attack Surface Reduction \(ASR\) rules reduce the attack surface of applications with rules that stop the vectors used by Office, script, and mail-based malware
* Network protection – Network protection extends the malware and social engineering protection offered by Microsoft Defender SmartScreen in Microsoft Edge to cover network traffic and connectivity on agency devices
* Controlled Folder Access – Controlled folder access protects files in key system folders from changes made by malicious and suspicious apps

Microsoft Defender Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Microsoft Defender | Enabled | Microsoft Defender will be enabled to align with ACSC guidance |
| Microsoft Defender Capabilities Enabled in the SOE | Components: Microsoft Defender Antivirus Microsoft Defender Exploit Guard Microsoft Defender Application Control Microsoft Defender SmartScreen Microsoft Defender Application Guard Microsoft Defender Credential Guard Microsoft Defender Firewall | Provides required security controls for the SOE |
| Microsoft Defender Antivirus Exclusions | Enabled and configured | Meets ACSC Windows 10 1909 hardening guidelines and aligns with security and compliance requirements |
| Microsoft Defender Exploit Guard Configuration | Enabled and configured | Meets ACSC Windows 10 1909 hardening guidelines and aligns with security and compliance requirements |
| Microsoft Defender Application Control Configuration | Enabled and configured | Meets ACSC Windows 10 1909 hardening guidelines and aligns with security and compliance requirements |
| Microsoft Defender Smart Screen Configuration | Enabled and configured | Meets ACSC Windows 10 1909 hardening guidelines and aligns with security and compliance requirements |
| Microsoft Defender Credential Guard Configuration | Enabled and configured | Aligns with security and compliance requirements. Enabled without lock allows Microsoft Defender Credential Guard to be managed remotely |
| Microsoft Defender Firewall Configuration | Enabled and configured | Meets ACSC Windows 10 1909 hardening guidelines and aligns with security and compliance requirements |

## Windows 10 Security Baselines

The Windows 10 security baseline settings support Windows 10 version 1809 and later.

The Windows 10 security baseline configures Windows settings as advised by the relevant Microsoft security teams. This baseline configures default settings in accordance with vendor best practice and increases the overall security of the client device whilst still allowing it to function correctly.

Windows 10 Security Baselines Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Above Lock | Configured | Default configuration, meets security requirements. |
| App Runtime | Configured | Default configuration, meets security requirements. |
| Application Management | Configured | Default configuration, meets security requirements. |
| Auto Play | Configured | Default configuration, meets security requirements. |
| BitLocker | Configured | Default configuration, meets security requirements. |
| Browser | Configured | Default configuration, meets security requirements. |
| Connectivity | Configured | Default configuration, meets security requirements. |
| Credentials Delegation | Configured | Default configuration, meets security requirements. |
| Credentials UI | Configured | Default configuration, meets security requirements. |
| Data Protection | Configured | Default configuration, meets security requirements. |
| Device Guard | Configured | Default configuration, meets security requirements. |
| Device Installation | Configured | Default configuration, meets security requirements. |
| Device Lock | Configured | Prevent use of camera, require password, Disable the lock screen slide show settings, Set password minimum age in days |
| DMA Guard | Configured | Default configuration, meets security requirements. |
| Event Log Service | Configured | Event log sizes modified to align with ACSC guidance. |
| Experience | Configured | Default configuration, meets security requirements. |
| Exploit Guard | Configured | Default configuration, meets security requirements. |
| File Explorer | Configured | Default configuration, meets security requirements. |
| Firewall | Configured | Default configuration, meets security requirements. |
| Internet Explorer | Configured | Default configuration, meets security requirements. |
| Local Policies Security Options | Configured | UAC settings have been modified to align with ACSC guidance |
| Microsoft Defender | Configured | Scheduled scan has been disabled in this baseline. This is set in Defender ATP baseline to avoid conflicts. |
| MS Security Guide | Configured | Default configuration, meets security requirements. |
| MSS Legacy | Configured | Default configuration, meets security requirements. |
| Power | Configured | Default configuration, meets security requirements. |
| Remote Assistance | Configured | Default configuration, meets security requirements. |
| Remote Desktop Services | Configured | Default configuration, meets security requirements. |
| Remote Management | Configured | Default configuration, meets security requirements. |
| Remote Procedure Call | Configured | Default configuration, meets security requirements. |
| Search | Configured | Default configuration, meets security requirements. |
| Smart Screen | Configured | Default configuration, meets security requirements. |
| System | Configured | System boot start driver initialization modified to align with ACSC guidance. |
| Wi-Fi | Configured | Default configuration, meets security requirements. |
| Windows Connection Manager | Configured | Default configuration, meets security requirements. |
| Windows Hello for Business | Disabled | Does not meet security requirements. |
| Windows Ink Workspace | Configured | Default configuration, meets security requirements. |
| Windows PowerShell | Configured | Default configuration, meets security requirements. |

## Microsoft Defender ATP Baseline

The Microsoft Defender ATP security baseline settings support Windows 10 version 1809 and later.

The Defender ATP security baseline configures Defender settings as advised by the relevant Microsoft security teams. This baseline configures default settings in accordance with vendor best practice and increases the overall security of the client device whilst still allowing it to function correctly.

Defender ATP security baseline Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Application Guard | Configured | Application Guard, Windows network isolation policy |
| BitLocker | Configured | Require device encryption with AES 256-bit XTS, BitLocker removable drive policy, BitLocker fixed drive policy, BitLocker system drive policy |
| Browser | Configured | Malicious site and file settings for MS Edge |
| Data Protection | Configured | DMA block |
| Device Guard | Configured | Credential guard settings |
| Device Installation | Configured | Manage the installation of hardware devices based off hardware identifiers |
| DMA Guard | Configured | Additional DMA protection for external DMA capable devices |
| Endpoint Detection and Response | Configured | Expedite telemetry reporting frequency, Sample sharing for all files |
| Firewall | Configured | Security association idle time before deletion, File Transfer Protocol, Packet queuing, Firewall profile domain, Firewall profile public, Firewall profile private, Firewall pre shared key encoding method, Certificate revocation list verification |
| Microsoft Defender | Configured | Several security settings ranging from Scanning scripts / incoming mail, File Blocking to real-time monitoring |
| Microsoft Defender Security Center | Configured | Blocking the use of Exploit Guard settings |
| Smart Screen | Configured | Application protection interface for end users |
| Windows Hello for Business | Disabled | Does not meet security requirements. |

## Microsoft Edge Security Baseline

The Microsoft Edge security baseline settings support Edge version 80 and later.

The Microsoft Edge security baseline has pre-configured groups of Windows settings and the default settings as advised by the relevant Microsoft security teams.

Microsoft Edge security baseline Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Microsoft Edge Settings | Configured | Default configuration, meets security requirements of this design. |

## Windows Defender Application Control

Application control is a crucial line of defence for protecting enterprises given today's threat landscape, and it has an inherent advantage over traditional antivirus solutions. Specifically, application control moves away from the traditional application trust model where all applications are assumed trustworthy by default to one where applications must earn trust in order to run. ASD frequently cite application control as one of the most effective means for addressing the threat of executable file-based malware \(.exe, .dll, etc.\).

Windows Defender Application Control \(WDAC\) helps mitigate these types of security threats by restricting the applications that users can run and the code that runs in the System Core \(kernel\). WDAC policies also block unsigned scripts and MSIs, and Windows PowerShell runs in Constrained Language Mode.

Application Whitelisting Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Application Whitelisting Product | WDAC | Microsoft recommended product for [application whitelisting](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control#choose-when-to-use-wdac-or-applocker) |
| Whitelisted method | A combination of publisher certificate and path rules and will be used. | Controlled via Intune to align with the ACSC Windows 10 1909 hardening guidance. WDAC policies are natively supported in Intune and SCCM co-management |
| Microsoft Block Rules | Configured | To align with the ACSC Windows 10 1909 hardening guidance. |
| Intelligent Security Graph connection | Configured | In accordance with Microsoft best practice. |

## Identity Providers

The identity providers section considers the different methods of logging on to the Windows 10 device. The local administrator account is addressed in a separate section.

Windows 10 provides various user account types or identity providers. This section outlines the identity providers that can be implemented for a Windows 10 device.

* Local Accounts - A local account is an account on a single Windows system. Local accounts are not replicated and cannot access to corporate resources. They allow access to local storage only. It may be desirable to disable, rename and scramble the passwords for the in-built local accounts
* Active Directory Domain - Domain identities are used to grant access to corporate resources and are implemented using Active Directory Domain Services. Administrators manage domain identities and ensure that users have access to the appropriate resources when group policies or any profile management solution is applied to the account. Domain identities are recommended if personalisation data will be stored in a corporate datacentre and will be synchronised to multiple corporate devices
* Azure Active Directory \(Azure AD\) - Azure AD is Microsoft's cloud directory and identity management service. Azure AD includes a full suite of identity management capabilities. Azure AD is a prerequisite for Microsoft Intune mobile device management including Conditional Access
* Microsoft Account - A Microsoft Account is an email address issued by or linked to a Microsoft authentication service. A Microsoft Account is a public version of an Azure Active Directory account. If this account is disabled certain features such as Windows Store cannot function.

Identity Providers Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Guest Account \(Local\) | Disabled | In line with the ACSC Windows 10 1909 hardening guidelines |
| Guest Account Name | Renamed | In line with the ACSC Windows 10 1909 hardening guidelines |
| Microsoft Accounts | Disabled | In line with the ACSC Windows 10 1909 hardening guidelines |
| Windows Hello for Business | Disabled | Does not meet security requirements. |
| Windows Hello for Business Configuration Method | Disabled | Does not meet security requirements. |

Additional Identity Providers Design Decisions for cloud native implementations

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Azure Active Directory Accounts | Enabled | Machines will be Azure AD Joined |
| Domain Accounts | Disabled | Machine will be Azure AD Joined |

Additional Identity Providers Design Decisions for hybrid implementations

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Azure Active Directory Accounts | Enabled | Machines will be Hybrid Azure AD Joined |
| Domain Accounts | Enabled | Users will log onto devices using credentials which originate in an on-premises domain. Machines will also be joined to the Agency domain |

## Desktop Analytics

Desktop Analytics is a service which provides insight and intelligence to an organisation to make informed decisions about the update readiness of the Windows clients. Desktop Analytics is a Microsoft cloud service that integrates with Configuration Manager \(SCCM\). The data collected from the organisation is pooled together with many of other systems that are connected to the Microsoft cloud services.

Desktop Analytics can be used with Configuration Manager to:

* Capture application inventory for an organisation
* Analyse application compatibility with latest Windows 10 feature updates
* Determine compatibility issues and provide potential resolutions
* Analyse the data to provide pilot groups consisting of devices which cover most of the organisation's application set
* Deploy Windows 10 to pilot and production-managed devices

Desktop Analytics is replacing Windows Analytics and Configuration Manager \(SCCM\) is a pre-requisite to enabling Desktop Analytics. Desktop Analytics provides:

* Device and software inventory - collect information such as application information and Windows versions
* Pilot identification - Identifying the devices which have the most coverage of components for the pilot of Windows upgrades and updates
* Issue identification - Potential issues are highlighted with upgrading and patching Windows by analysing captured data from Microsoft clients and organisational data. Potential mitigations can then be recommended
* Configuration Manager integration - Extends the on-premises infrastructure by allowing data to be analysed in order to assist in the deployment and management of Windows devices

Desktop Analytics Design Decisions for hybrid implementations

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Desktop Analytics | Enable and configure | In line with the ACSC hardening guideline policy recommendations and meets requirements for future Desktop Analytics use |
| Data Location | United States | The Windows diagnostic data \(non-business data\) is encrypted using SSL and sent to and processed at a Microsoft-managed secure data centre located in the United States. This service is only hosted in the United States  The diagnostic data cannot be seen by another customer nor unauthorised Microsoft personnel  Note: As the diagnostic data is located offshore this may raise data sovereignty questions for the Agency, for which internal decisions might need to be made |

## Telemetry Collection

Windows 10 and Windows Server include the Connected User Experiences and Telemetry component, which uses Event Tracing for Windows \(ETW\) trace logging technology that gathers and stores diagnostic data events and data.

The operating system and some Microsoft management solutions, such as SCCM use the same logging technology.

Windows uses telemetry information to analyse and fix software problems. It also helps Microsoft improve its software and provide updates that enhance the security and reliability of devices within organisations.

Telemetry level options are:

* Off – Disable telemetry data collection
* Security – Information that is required to help keep Windows secure, including info about telemetry client settings, the Malicious Software Removal Tool, and Windows Defender. This level is available only on Windows 10 Enterprise and Windows 10 Education, and Windows 10 IoT Core
* Basic – Basic device info, including quality-related info, application compatibility, and info from the Security level
* Enhanced – Additional insights, including how Windows and Windows apps are used, how they perform, advanced reliability info, and info from both the Basic and the Security levels
* Full – All info necessary to identify and help to fix problems, plus info from the Security, Basic, and Enhanced levels

The following image shows the information in each of the different Telemetry Collection levels.

![Telemetry Options](https://github.com/oobeDemo/NewBlueprint/tree/321d78d85948b495d5b11c22c1ec206d7c371721/assets/images/cd-telemetry.png)

Telemetry Collection Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Allow Telemetry | Enabled | In line with the ACSC hardening guideline policy recommendations and meets requirements for future Desktop Analytics use. |
| Telemetry Level | 2 – Enhanced | Microsoft recommend Enhanced Limited for Desktop Analytics |

## Office Macro Hardening

Microsoft Office files can include Visual Basic for Applications \(VBA\) programming code \(macro\) embedded into the document.

A macro can comprise of several repeatable actions that can be coded or recorded and rerun later to automate repetitive tasks. Macros are powerful tools that can be easily created by novice users to greatly improve their productivity. However, an adversary can also create macros to perform a variety of malicious activities, such as assisting in the compromise of workstations to exfiltrate or deny access to sensitive information.

The ACSC provides guidelines in securing systems against malicious macros and recommend they are implemented in all Windows environments. The ACSC recommends that one of the following approaches is implemented:

* All macros are disabled
* Only macros from trusted locations are enabled
* Only digitally signed macros are enabled

Email and web content filtering is recommended to be implemented by the ACSC to ensure that macros are not delivered to users via email by malicious actors.

Office Macro Hardening Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Implementation approach | Only digitally signed macros are enabled | In line with the ACSC Microsoft Office Macro security policy recommendation |
| Email and Web Content Filtering | Enabled | In line with the ACSC Microsoft Office Macro security policy recommendation |
| Configuration Method | Agency preference | Macro hardening can be configured via the Agencies existing Group Policies or Intune as well as Attack Surface Reduction in Windows Defender Exploit Guard |

## Local Administrator

The default local Administrator account is a highly privileged user account found on every Windows operating system. The Administrator account is the first account that is created during the installation for all Windows client operating systems.

The Administrator account can be used to create local users and assign user rights and access control permissions. It can also be used take control of local resources at any time simply by changing the user rights and permissions.

The default Administrator account cannot be deleted or locked out, but it can be renamed and / or disabled. It is Microsoft best practice and an ACSC hardening guideline recommendation to leave the Administrator account disabled and renamed.

If there is a requirement to utilise the local Administrator account in an on-premises environment, Microsoft provides Local Administrator Password Solution \(LAPS\), an Active Directory integrated Access Control List \(ACL\) protected password management tool.

LAPS allows system administrators the ability to set a different, random password for the common local administrator account on each computer in the domain and store the password for the computer's local administrator account in Active Directory, secured in a confidential attribute in the computer's corresponding Active Directory object.

Local Administrator Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Local Administrator Account | Disabled | The local administrator account will be disabled in line with the ACSC Windows 10 1909 hardening guideline policy recommendations |
| Local Administrator Account Name | Renamed | The local administrator account will be renamed during the image deployment In line with [Microsoft recommendations for securing the local administrator account](https://docs.microsoft.com/en-us/windows/security/threat-protection/security-policy-settings/accounts-rename-administrator-account) |
| Local Administrator Account Password | Randomised | In line with the ACSC Windows 10 1909 hardening guideline policy recommendations |
| Additional Local Administrator Accounts | Not Configured | Additional administrator accounts will not be created during the image deployment |
| LAPS | Not Configured | Not required for the solution. The local Administrator account will be disabled and renamed |

