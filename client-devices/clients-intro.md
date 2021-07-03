---
layout: page
title: Client Devices
---

# Client Devices Introduction

This document covers the following topics.

| Section | Description |
| :--- | :--- |
| Windows 10 Hardware | The Hardware Platform section includes the physical hardware, firmware drivers, and peripherals. |
| Windows 10 Deployment & Management | The Deployment & Management section shows the typical deployment options for cloud & hybrid as well as the management options that can be used in the application of the SOE and security. |
| Windows 10 Standard Operating Environment \(SOE\) | The SOE section defines all the operating system components that are installed on the physical hardware. It includes the operating system and core services. |
| Windows 10 Security | The Windows Security section describes the configuration and methods of locking down the configuration to align with Microsoft security best practices and ACSC guidance for Windows 10 clients. |
| iOS | The iOS section covers enrolment and security of the mobile devices. |

For each component within the document there is a brief description of the contents of the section, a commentary on the things that have been considered in determining the decisions and the design decisions themselves.

## Assumptions

* ACSC Windows 10 hardening guidelines are being adhered to.
* The Intune Console is the preferred method to manage all settings regardless of a cloud native or hybrid implementation. Although a combination of the System Center Configuration Manager \(SCCM\) Console and Group Policy Objects \(GPOs\) would  be able to achieve the same settings in a hybrid environment, this Blueprint does not include SCCM and GPOs example configurations due to the level of dissimilarities and per agency customisation in existing SCCM and GPOs configurations across Commonwealth entities.
* Minimum version of SCCM 1710 is required for co-management, recommended at least 1910.

