# Client Devices Windows 10 Deployment and Management

The type of deployment and management methods used for the Standard Operating Environment \(SOE\) will vary depending on the use of either a cloud native or hybrid configuration. Cloud native will typically utilise pre-installed or offline custom images with Autopilot for the deployment method and utilise Intune as the ongoing management method.

Hybrid can benefit from enabling the SCCM Co-management feature. Once enabled this allows additional deployment methods which can be utilised to ensure images remain light weight. Co-management provides a more staged approach to moving workloads into the cloud that may assist existing larger environments to complete a more gradual transition.

## Deployment

Windows 10 can be deployed via Intune or SCCM, or a combination of both. The configuration of a Windows 10 deployment will depend upon which technologies are available to an agency and whether a hybrid deployment is required.

Windows 10 deployments will be based on either a deployment which is cloud native or hybrid.

* Cloud native – Image on the workstation will be modified using Autopilot and Intune. The OEM image in use should be from a trusted vendor or custom-built by the agency and provided to the OEM vendor for implementation prior to being dispatched to the agency. Alternatively, an offline image will need to be created by the agency and applied to the workstation prior to Autopilot and Intune. The offline image should be light weight consisting of the base Windows image and required base drivers only.
* Hybrid – OEM image or SCCM task sequence should be used as the base for Windows 10, with Intune and Autopilot applied over the top of the image for further customisation. The OEM image in use should be from a trusted vendor or custom built by the agency and provided to the OEM vendor for implementation prior to being dispatched to the agency. Alternatively, an agency specific SCCM task sequence including the Windows image and base drivers. This image will then be further customised with Intune and Autopilot.

Deployment Design Decisions for cloud native implementations

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Deployment method | Agency light weight base image with Autopilot and Intune deployments applied as during enrolment | An agency specific light weight base image provides the benefit of removing all OEM applications and firmware prior to onboarding to the agency through Intune & Autopilot. |

Deployment Design Decisions for hybrid implementations

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Deployment method | Agency light weight base image with SCCM deployment applied | An agency specific light weight base image provides the benefit of removing all OEM applications and firmware prior to onboarding to the agency through SCCM. |

## Management

Windows 10 can be managed via Intune or SCCM, or a combination of both. The configuration of Windows 10 management will depend upon which technologies are available to an agency and whether a hybrid deployment is required.

Windows 10 management options will be based on either a deployment which is cloud native or hybrid. This section provides detailed information on the different configuration options for Windows 10 management.

Cloud native deployments provides the agency the immediate benefits of working with Intune and Autopilot while also integrating directly with other cloud services including Microsoft 365 and Azure AD. Using Intune will simplify the overall deployment and management of Windows 10 to a single console which is also shared with the mobile device management of iOS devices.

A hybrid deployment gives the option of co-management which enables the agency to manage Windows 10 by using both SCCM and Intune. Enabling co-management within SCCM allows the agency to utilise their investment in SCCM and take advantage of additional cloud capabilities. This allows the agency additional flexibility to use the technology solution that works best for them and facilitates a more gradual move to cloud native as the agency can pilot test various workloads in Intune first.

Hybrid deployments can choose to enable SCCM or Intune for client management depending on the cloud maturity level of the agency. It is not a requirement of agencies undertaking hybrid implementations to use SCCM. This Blueprint provides guidance on integration between SCCM and Intune for hybrid deployments however agencies with existing infrastructure may alternatively elect to migrate device management from SCCM to Intune, which will not affect cyber security postures.

Management methods that can be used to manage Windows 10 in a Microsoft 365 environment.

| Microsoft 365 Implementation | SCCM Implementation | Management Method for Windows 10 | Benefits |
| :--- | :--- | :--- | :--- |
| Cloud native | SCCM is not possible with cloud native | Intune | No on-premises infrastructure required for management. Well suited for Azure AD joined workstations for a full cloud solution. |
| Hybrid with Intune management | Suitable for:   _No SCCM or_  SCCM with co-management enabled and Workloads set to Intune | Intune | Existing on-premises SCCM infrastructure with Hybrid Azure AD joined workstation. Well suited for an agency that does not have SCCM or does not want to use SCCM to manage workstations. |
| Hybrid with SCCM management | SCCM with co-management enabled and Workloads set to SCCM | SCCM | Existing on-premises SCCM infrastructure with Hybrid Azure AD joined workstations. Well suited for an agency that has a significant investment in SCCM and requires a more gradual migration to Intune. Individual Workloads can be targeted and pilot-tested in Intune. |

The following image displays an overview diagram of SCCM Co-Management.

![SCCM Co-Management diagram](https://github.com/oobeDemo/NewBlueprint/tree/321d78d85948b495d5b11c22c1ec206d7c371721/assets/images/cd-sccm-comgmt.png)

With co-management enabled, the agency can choose which workloads remain on-premises and which workloads are offloaded to Intune. The workloads are:

* Compliance Policies – Compliance policies define the rules and settings that a device must comply with to be considered compliant by conditional access policies. Compliance policies will also monitor and remediate compliance issues with devices. 
* Device Configuration – The device configuration workload includes settings that you manage for devices in your organization. Switching this workload also moves the Endpoint Protection and Resource Access workloads.
* Endpoint Protection – The Endpoint Protection workload includes the Windows Defender suite of antimalware protection features including Defender Advanced Threat Protection.
* Resource Access Policies – Resource access policies configure VPN, Wi-Fi, email, and certificate settings on devices.
* Client Apps – Use Intune to manage client apps and PowerShell scripts on co-managed Windows 10 devices. After transitioning this workload, any available apps deployed from Intune will be available in the Company Portal. Apps that are deployed from Configuration Manager are available in Software Centre.
* Office Click-to-Run Apps – This workload manages Office 365 apps on co-managed devices.
* Windows Update Policies – Windows Update for Business policies allow deferral policies for Windows 10 feature updates or quality updates for Windows 10 devices managed directly by Windows Update for Business.

With co-management disabled and no cloud integration, the agency will rely on on-premises management of the Windows 10 workstations. These could include utilising SCCM task sequencing, SCCM Compliance and Endpoint Protection policies, various scripting methods and Group Policy Preferences.

There are many benefits to going cloud native or hybrid co-management utilising workloads weighted to Intune. The workstations can be managed from any internet-connected location whether that be in the office or a remote location \(home, client site etc\).

Management Design Decisions for cloud native implementations

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Management method | Cloud native Intune management | Cloud native implementation offers a simple and efficient implementation. Single console to manage both Windows 10 and iOS. |

Management Design Decisions for hybrid implementations

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Management method | Hybrid with SCCM co-management enabled. | Intune integration is required to enable features such as Conditional Access.  SCCM co-management offers flexibility for the agency to take advantage of cloud services immediately or pilot and move individual workloads across when ready while leveraging existing configuration on-premises. |
| Management tool | Agency preference for Intune or SCCM managing endpoints in co-management. | Each agency has a different level of investment and different maturity in SCCM and cloud products. Co-management has several options to meet the unique requirements of each agency. |

