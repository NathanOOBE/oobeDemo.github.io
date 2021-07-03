# Client Devices Windows 10 Hardware

While most modern hardware will be capable of running Windows 10, making sure the right choice of hardware is made will ensure that the Standard Operating Environment runs efficiently. This section focuses on the technical requirements to support Windows 10 features described in this design.

The style of hardware will also need to be considered, whether a typical desktop model which will be permanently located on a desk or a laptop model to facilitate a more mobile workforce. The DTA recommends that, within operational constraints, agencies consider a laptop deployment to increase the flexibility and mobility of an agency workforce.

## Hardware Requirements

The hardware platform chosen to support the Standard Operating Environment \(SOE\) is key to its stability and provides the components that can be configured by the operating system and applications.

The selected processor architecture and associated firmware capability directly influence the supportability of applications and security features of an operating system. The minimum hardware requirements listed below will ensure that the system runs reliably and is supported by the vendor, Microsoft.

Hardware Requirements Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Laptop Model | Any device that meets the below requirements and the Agency procurement processes | To meet the Agency requirements. |
| Desktop Model | Any device that meets the below requirements and the Agency procurement processes | To meet the Agency requirements. |

Minimum hardware configuration for the Windows 10 SOE applicable to all agencies and implementation types.

| Component | Description | Justification |
| :--- | :--- | :--- |
| Architecture | x64 | Required to Support more than 4GB RAM |
| Processor | At least 4 logical processors, VT-x \(Intel\) or AMD-V CPU extensions, 2 GHz or higher with Second Level Address Translation \(SLAT\) support | SLAT is required to support Windows Defender Application Guard as required by ACSC hardening guide for Windows 10 1709 |
| RAM | 8GB | To meet design specifications. |
| Graphics Card | DirectX 9 WDDM 1.0 | To meet design specifications. Integrated or dedicated. |
| Input Device\(s\) | Keyboard Mouse Multi-touch display screen to enable Windows 10 touch screen features \(optional\) | Keyboard and mouse may be built into a laptop, but touch screens are optional. |
| Minimum HDD Space | 128GB | To meet design specifications. |
| Microphone | Required for speech recognition \(optional\) | Speech recognition is not required to be enabled but may be needed for agencies with accessibility requirements. |
| BIOS | Minimum UEFI 2.3.1 | Required to support Secure Boot, Windows Defender Device Guard, Windows Defender Credential Guard, Windows Defender Exploit Guard and Kernel DMA Protection |
| TPM | Minimum version 2.0 | Required to support Intune Autopilot and SCCM |

## Drivers and Peripherals

Drivers allow hardware and software to function within a SOE. Drivers are essentially written code that allows Windows to recognise physical components of a computer such as printers, keyboards, mouse, graphics cards and peripherals. It is critical these drivers are supported on the Operating System version and are deployed at the right time.

Drivers that are essential to the hardware platform can be deployed in the base reference image, during device deployment task sequence through SCCM, via Microsoft Intune or later by Microsoft Windows Update. Drivers such as network drivers are critical during the deployment phase, whereas a microphone driver is not. The more generic a reference image, the lower the deployment and maintenance costs.

Other drivers like printer drivers can be deployed after the end user has logged onto the device using either a "Follow Me Print" or "Defined print queue list" selected by the end user.

Drivers and Peripherals Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Driver Integration | Configured | Deployed via Microsoft Windows Update which aligns with the ACSC guidance |
| Approved Peripheral Devices | Configured | The SOE will whitelist approved peripheral devices using Intune |
| Unapproved Peripheral Devices | Blocked | The SOE will block installation of unapproved peripheral devices using Intune |
| Signed Device Driver Store | Configured | Deployed via Microsoft Windows Update which aligns with the ACSC guidance |
| Peripheral Drivers | Configured | Deployed via Microsoft Windows Update which aligns with the ACSC guidance |
| Workstation Device Drivers | Configured | Deployed via Microsoft Windows Update which aligns with the ACSC guidance |
| Printer Drivers | Configured | Deployed via Microsoft Windows Update which aligns with the ACSC guidance |

## Firmware Configuration

The firmware is the software that provides the interface between the hardware and the operating system. Firmware configuration and capabilities can directly influence the security features of an operating system.

Two important Firmware capabilities are detailed below:

* UEFI - Unified Extensible Firmware Interface \(UEFI\) is a replacement for the older Basic Input / Output System \(BIOS\) firmware interface and the Extensible Firmware Interface \(EFI\) 1.10 specifications
* Secure Boot - Secure Boot ensures that the device boots using only software that is trusted by the PC manufacturer. When the PC starts, the firmware checks the signature of each piece of boot software, including firmware drivers \(Option ROMs\) and the operating system. If the signatures are valid, the PC boots, and the firmware gives control to the operating system

Firmware that meets the UEFI 2.3.1 or newer specifications provides the following benefits:

* Faster boot and faster resume times
* Use of security features such as Secure Boot and factory encrypted drives help prevent suspicious code from running before the operating system is loaded
* Able to support 2 terabytes and greater hard drives with more than four partitions
* Some UEFI-based PCs have a Compatibility Support Module \(CSM\) that can emulate earlier BIOS which provide greater flexibility and compatibility for end users.

Note: Secure Boot must be disabled in order to use CSM.

* Capable of Multicast deployment whereby a PC image from a PC manufacturer can be received by multiple PCs without saturating the network or source image server.
* Support for UEFI firmware drivers, Option ROMs and applications.

UEFI 2.3.1 is a requirement for the use of Device Guard.

Secure Boot is required for the use of Credential Guard.

Firmware Configuration Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| UEFI version | At least 2.3.1 | This is minimum UEFI version required for Device Guard |
| Secure Boot | Enabled | Secure Boot is a requirement for the use of Windows Credential Guard and provides greater security protection for users |
| Secure Boot Configuration Method | Configured via Intune | Meets ACSC Windows 10 1909 hardening guidelines. |

## Trusted Platform Module

A Trusted Platform Module \(TPM\) is a microchip designed to provide basic security-related functions, primarily involving encryption keys. The TPM is usually installed on the motherboard of a computer or laptop and communicates with the rest of the system using a hardware bus.

With a TPM, private portions of key pairs are kept separate from the memory controlled by the Operating System. Keys can be sealed to the TPM, and certain assurances about the state of a system—that define its "trustworthiness"—can be made before the keys are unsealed and released for use. Because the TPM uses its own internal firmware and logic circuits for processing instructions, it does not rely upon the Operating System and is not exposed to external software vulnerabilities.

A TPM of specific version number is required to support Windows 10 features such as Windows Hello and Bitlocker to help meet ACSC hardening guidelines for the OS.

Trusted Platform Module Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| TPM | Enabled in BIOS/UEFI from hardware vendor or manually configured | Required for Windows 10 and BitLocker |
| TPM Version | 2.0 | Meets ACSC Windows 10 1909 hardening guidelines |

