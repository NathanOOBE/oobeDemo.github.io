# Client Devices iOS

ACSC guidance for mobile devices currently only covers iOS devices. Due to this, the recommendation is to utilise iOS for Agency devices to ensure that the environment is following security guidelines.

## iOS Devices

iOS follows a yearly major release cycle. With every major release of iOS, older iPhone devices are deprecated from support, hence security updates will not be available to these devices.

iOS devices should be configured to adhere to the ACSC hardening requirements to provide secure access to corporate information. ACSC recommends that the latest version of iOS is used in order to have the most secure operating system present on the device.

iOS Devices Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| iOS version | iOS 13 or above | To align with the ACSC Security Configuration guide – iOS version enforcement of n or n-1 will allow for testing of patches and internal applications before deploying operating system updates.  Apple applies the n-1 rule to incremental updates, all other versions are no longer signed.   Once a version is not signed a device cannot be restored to it. |
| iOS Devices | iPhone XS and above | iPhone X and older are all vulnerable to the exploit Checkm8 and should be avoided. |
| Jailbroken/rooted devices | Blocked | Prevents jail broken devices from accessing Agency information. |

## Enrolling iOS Devices

Device enrolment registers the iOS devices into the corporate device management solution and ensures the device is then able to be managed by administrators.

Microsoft Intune provides a mechanism for enrolling devices into Azure AD. Once registered the device is populated into Intune policy groups using dynamic membership. This ensures that the device meets the compliance policy, monitored, and secured to the Agencies security requirements.

Microsoft Intune provides three separate experience in enrolling the iOS devices into the Agencies Azure Active directory. The enrolment experiences are:

* Device Enrolment Program \(DEP\) – Device Enrolment Program is a managed device enrolment process. The devices serial number is registered with Apple Business Manager allows Intune to bypass Assisted Setup by preconfigure device settings. The user's account will be assigned to the device. The device will be marked as a Supervised device.
* Device Enrolment Manager \(DEM\) – Device Enrolment Manager assigns a single Azure Active Directory account as the owner of the device. The end users cannot administer or purchase any apps on the device
* User Enrolment – User enrolment process requires users set up the iOS device and manually install Company Portal to register the device as Intune enrolled device. The device will be marked as a BYOD device

Enrolling iOS Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Enrolment method | Device Enrolment Program | Devices will be pre-configured before the device is handed over to the end user. This in line with the ACSC iOS Secure Configuration Hardening guide for PROTECTED devices. |

## Securing iOS Devices

Intune provides ability to configure iOS configuration settings for securing, configuring and applications on iOS devices. These configurations are managed via Mobile Device Management \(MDM\) as an Intune policy. MDM allows the Agency to deploy consistent configuration on enrolled iOS devices.

MDM provides the capability to configure iOS devices. These devices must be configured to meet ACSC iOS Secure Hardening guide to ensure the device can access and store the Agencies data. These configurations can be categories as:

* Security – Ensure device has up to date and secure authentication policies and encryption devices that meets ACSC Secure iOS guide. 
* Branding – The Agencies branding for lock screen, wallpapers, and reporting if the device is lost can be configured.
* Device features – Configures device features, for example, AirDrop and Bluetooth pairing, within iOS devices.

Securing iOS devices Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Mobile Device Management | Mobile devices will be managed using Intune | Leveraging the capabilities already available in the licensing agreement. Intune and Apple Business Manager will be adopted to manage mobile devices. |
| Security policies and hardening requirements | Security policies will be enforced on all mobile devices managed by the Agency | Security policies will be configured in line with the ACSC Security Configuration Guide – Apple iOS 12 Devices. |
| Device Features | Disabled | AirDrop, Bluetooth pairing, AirPrint |

Mobile Device Management Configuration applicable to all agencies and implementation types

| Configuration | Value | Description |
| :--- | :--- | :--- |
| **Security** |  |  |
| Supervised Mode | Enable | Agency iPhones are managed devices. This is in line with the ACSC iOS Secure Configuration Hardening guide for PROTECTED devices. |
| Device passcode | Device passcode of 12 characters or above | iOS devices, by default, is encrypted once a passcode is provided to the device. Configured in line with the ACSC iOS Secure Configuration Hardening guide for PROTECTED devices. |
| Biometrics | Disable | This is in line with the ACSC iOS Secure Configuration Hardening guide for PROTECTED devices. |
| Mobile Device Management | Enable | Mobile Device Management provides the Agency better auditing tools on the device. In line with ACSC iOS Secure Configuration Hardening guide for PROTECTED devices |
| Maximum Auto-Lock | 2 minutes | Auto Lock will lock a device if it is inactive for specified time |
| Virtual Private Network \(VPN\) | Not Configured | VPN will not be setup as part of the iOS device. Per-app VPN will be set up to secure communication between the device and the Agencies data |
| **Branding** |  |  |
| Lock Screen and background branding | Configured | Agency branding will be applied to endpoints. It is recommended that agencies include the contact information of the relevant IT Support in the event that a device is lost. |
| **Device Features** |  |  |
| Disable Screenshot and screen recording | Disable | Disablement of screenshot and screen recording, disable users from taking a snapshot of protected documents |
| Allow iCloud backup, document data and Keychain | Disable | The Agencies data on mobile devices must be uploaded into the Agencies tenant. This is done to prevent accidental information being backed up to iCloud or another unsecure data store |
| Managed Open-In | Enable | Managed Open-In is enable segregates between corporate managed and personal application in an iOS device. This in line with the ACSC iOS Secure Configuration Hardening guide for PROTECTED devices. |
| Allow documents from managed sources in unmanaged destination | Disable | The Agencies data cannot be moved between managed and unmanaged application destination. This is to prevent PROTECTED from being transferred to an unmanaged application or location |
| Treat AirDrop as unmanaged destination | Disable | AirDrop provides the ability to wirelessly transfer documents between Apple devices. Setting AirDrop as an unmanaged destination prevents users from accidentally transferring Agency data to unsecure applications or locations |

## Securing iOS Applications

Mobile Application Management \(MAM\) in Intune allows configuration of managed applications within an iOS device. Managed applications enclose Agency applications within an application bubble. This bubble prevents accidental data spillage by preventing cutting and pasting, as well as allowing data sharing within the application bubble.

MAM provides the capability to configure iOS device applications. These configurations include:

* Managed Applications – List of Agency business applications
* Managed Application configuration – Configure and secure managed application configuration within the device. These configurations allow and isolate managed applications to resides next to unmanaged applications.
* Per-app VPN - Secure communication between applications on devices, and the Office 365 tenant. This will require the Agencies VPN device setup to accept communication from the VPN connection from managed apps.

Securing iOS Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Managed Applications | Microsoft Corporate Portal Microsoft Azure Information Protection Microsoft Word Microsoft Excel Microsoft Outlook Microsoft PowerPoint Microsoft Teams Microsoft Edge Adobe Reader Microsoft OneDrive Microsoft OneNote | This is to meet the Agencies requirement for managed applications |
| Application VPN configuration | Configured for Managed Applications | Managed applications will use VPN to secure its connection to the Agencies Office 365 tenant |
| Disable organisation data to be backed up to iCloud | Disable | PROTECTED must be stored within the Agencies environment / corporate data store |
| Encrypt organisation data in mobile device | Not required. | Encrypting organisation data requires an additional PIN for managed applications in the device. The Agency will utilise sensitivity labels alongside device encryption to ensure encryption requirements are met based on ACSC hardening requirements. |
| Send organisation data to unmanaged apps | Policy managed apps with Open In/Share Filtering | Prevents data to be shared between managed application stated above and other unmanaged application on the device |
| Save copies of organisation data | SharePoint and OneDrive for Business only | Ensure all data is saved within the Agencies tenant |
| Organisation data notification | Block organisation Data | Prevents Agency information being displayed on the lock screen |
| Microsoft Edge Configuration | Configured. Set Microsoft Edge proxy and homepage URL to Agencies Intranet | Configured so Microsoft Edge is able to access Agencies internal websites |
| Microsoft Outlook | Configured. Ensure Contact list is added into Outlook Contact list rather than device | Configured so Agencies contact list is maintained within managed application rather than the phone's contact details |

## Remote Wipe iOS Devices

iOS devices can be used to access information while away from the office. The device is used to access the Agencies intranet, documents and for collaboration purpose.

Intune provides the ability to reset the device \(factory reset\) or remove managed application data from the device. The Factory reset option remotely wipes and resets the iOS device. The Intune manage application wipe does not clear the device of non-managed application data which allow for potential security issues.

The Agency has indicated that the device must be able to be remotely wipe in case it is lost. This is to ensure information cannot be recovered in any circumstances.

Remote wipe iOS devices Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Device Lost Mode | Enabled | Lost mode sends notification to the device's lock screen. |
| Device remote wipe | Device will be remote wiped of corporate data \(Factory Reset\). | To minimize the security if the device is lost or not return to the Agency. Intune remotely wipe and reset the iOS device when a user is off-boarded. This allows the device to be reassign to other users in the Agency. |

