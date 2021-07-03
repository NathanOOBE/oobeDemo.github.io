# Platform System Administration

System Administration is the process of managing, troubleshooting, and maintaining the solution. To complete this, system administrators are granted permissions over the solution. The allocation of permissions to administrators should align with the administrator's role within the organisation and the principle of least privileged access. The allocation of permission to the administrator's role is captured within the Role Based Access Control \(RBAC\) policy.

## Administrative consoles

To manage and configure the solution, administrators will use various administrative consoles. These consoles are a mixture of server based and web-based consoles that exist internally or in the cloud.

Web based administrative consoles are provided by Microsoft however the urls for these consoles constantly change \(refer to [Microsoft Security Portals](https://docs.microsoft.com/en-us/microsoft-365/security/mtp/portals?view=o365-worldwide)\). The consoles listed below are correct at the time of writing.

Administration consoles Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Azure Portal | Available from web console | The console is available from any managed device using a standard Web browser with internet access. The FQDN used for access will be [https://portal.azure.com](https://portal.azure.com/). Standard users do not have access to the portal. |
| Microsoft 365 Admin Center | Available from web console | The console is available from any managed device using a standard Web browser with internet access. The FQDN used for access will be [https://admin.microsoft.com/](https://admin.microsoft.com/) |
| Microsoft Defender ATP Portal | Available from web console | The console is available from any managed device using a standard Web browser with internet access. The FQDN used for access will be [https://securitycenter.windows.com/](https://securitycenter.windows.com/) |
| MCAS Portal | Available from web console | The console is available from any managed device using a standard Web browser with internet access. The FQDN used for access will be [https://portal.cloudappsecurity.com/](https://portal.cloudappsecurity.com/) |
| Microsoft 365 Compliance Center | Available from web console | The console is available from any managed device using a standard Web browser with internet access. The FQDN used for access will be [https://compliance.microsoft.com/](https://compliance.microsoft.com/) |
| Microsoft Endpoint Manager Admin Center | Available from web console | The console is available from any managed device using a standard Web browser with internet access. The FQDN used for access will be [https://endpoint.microsoft.com/](https://endpoint.microsoft.com/) |
| Microsoft 365 Security Center | Available from web console | The console is available from any managed device using a standard Web browser with internet access. The FQDN used for access will be [https://security.microsoft.com/](https://security.microsoft.com/) |
| Azure ATP Portal | Available from web console | The console is available from any managed device using a standard Web browser with internet access. The FQDN used for access will be [https://portal.atp.azure.com/](https://portal.atp.azure.com/) |
| Microsoft Defender Security Intelligence Portal | Available from web console | The console is available from any managed device using a standard Web browser with internet access. The FQDN used for access will be [https://microsoft.com/wdsi/](https://microsoft.com/wdsi/) |

## Role Based Access Control \(RBAC\)

RBAC defines what an end user or administrator can do. In relation to system administration, RBAC provides various roles each of which can only perform certain tasks. For example, help desk staff may be able to only view certain resources, whereas system administrators could view, create, and delete those resources.

When deploying the RBAC model in Azure, there are two scopes where access can be granted. The use of the scopes can be used separately or together depending on the services activated. The scopes include:

* Tenant Scope - Roles within the Tenant Scope allow access to perform tasks at the Tenant and Office 365 administration level. By default, there are 51 built-in RBAC roles that can be assigned at this level to ensure least privilege access is implemented.
* Subscription Scope – Roles within the Subscription Scope allow access to perform tasks within a subscription. Subscription roles do not have permissions at the Tenant Scope level.

Privileged Identity Management \(PIM\) can be leveraged to enhance the Azure RBAC model. PIM is an implementation of Just-in-time \(JIT\) access. JIT access ensures that an administrative account only has privileges when required to complete a function. JIT aligns to the principal of Zero Standing Privilege.

Each PIM role assignment can have the following attributes:

* Activation Duration - the Activation Duration attribute specifies the duration to allow the access request, the maximum is 72 hours.
* Approver – the Approver attribute specifies the person or people who can approve role activation requests.
* Notification – the Notification attribute specifies that a pending request is awaiting approval via email.
* Incident Request Ticket – the Incident Request Ticket attribute specifies that the approver add an incident ticket number to the approval request.
* Multi-factor Authentication – the Multi-factor Authentication attribute specifies whether MFA is required for activation.

RBAC Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Azure AD Role Based Management | Least Privilege, using PIM | PIM will be utilised to provide Just-in-Time role-based management to ensure elevated access is only provided when required. |
| PIM Roles | Authentication Administrator Azure Information Protection Administrator Global Administrator Exchange Service Administrator Helpdesk Administrator Intune Service Administrator Office Apps Administrator Power BI Service Administrator Power Platform Administrator Privileged Role Administrator Security Administrator Security Operator SharePoint Service Administrator Teams Communications Administrator Teams Communications Support Engineer Teams Communications Support Specialist Teams Service Administrator User Account Administrator | The configured PIM roles align to the services utilised within the solution. |
| PIM approval | Automatic approval for all roles except for Global Administrator | Approval will only be required for Global Administrators. |
| Activation duration | 8 hours | The activation duration will be one workday to ensure that administrative actions are not impeded. |

