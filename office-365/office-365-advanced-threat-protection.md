# Office 365 Advanced Threat Protection

Office 365 Advanced Threat Protection \(ATP\) extends the native security features in Office 365. The protections provided by Office 365 ATP are designed to defend against attacks from multiple threat vectors including email, websites and documents stored in online libraries, such as SharePoint Online. Each of the Office 365 ATP capabilities is enabled and managed via policies configured from the Office 365 Security and Compliance Center.

Office 365 ATP provides the following capabilities:

* Safe Links - Office 365 ATP Safe Links provides inspection of links included in emails and Office 365 documents to determine if it is malicious, redirecting the user if it is.
* Safe Attachments - Office 365 ATP Safe Attachments provides sandbox execution of attachments to detect and delete malicious content.
* Anti-Phishing - Office 365 ATP Anti-Phishing provides machine learning capabilities to detect advanced phishing campaigns.

## Safe Links

ATP Safe Links can help protect an organisation by providing time-of-click verification of web addresses \(URLs\) in email messages and Office documents. Protection is defined through ATP Safe Links policies that are configured by an organisation.

Administrators can redirect URLs in order to avoid being sent to the original link. In addition, administrators can obfuscate the original link preventing users from copying and pasting the link into a web browser.

Real-time scanning of URLs provides an additional layer of protection by scanning links during transit and hold an email message from being delivered until the links have been scanned and considered safe.

Safe Links can be configured at an organisation level or on a per recipient basis. These policies then be applied to either Exchange Online, Office 365 applications or both.

ATP Safe Links protection works as outlined below for URLs in emails that are hosted in Office 365:

* All incoming email goes through Exchange Online Protection, where IP and envelope filters, signature-based malware protection, anti-spam and anti-malware filters are applied
* An end-user signs into Office 365 and accesses their Exchange Online mailbox
* An end-user opens an email message containing a URL, and then clicks on the URL in the email message
* The ATP Safe Links feature immediately checks the URL before opening the website. The URL is identified as blocked, malicious, or safe
* If the URL sends an end-user to a website that is included in a custom "Do not rewrite" URLs list for a policy that applies to the user, the website opens
* If the URL sends an end-user to a website that is included in the organisation's custom blocked URLs list, a warning page opens
* If the URL sends an end-user to a website that has been determined to be malicious, a warning page opens
* If the URL goes to a downloadable file and the ATP Safe Links policies are configured to scan such content, the downloadable file is checked
* If the URL is considered safe, the end-user is taken to the website

ATP Safe Links protection works as outlined below for URLs in Office 365 ProPlus applications:

* A user opens a Word, Excel, PowerPoint, or Visio, and is signed in using their Office 365 security credentials. The document contains URLs
* When a user clicks on a URL in the document, the link is checked by the ATP Safe Links service
* If the URL sends an end-user to a website that is included in a custom "Do not rewrite" URLs list for a policy that applies to the user, that user is taken to the website
* If the URL sends an end-user to a website that is included in the organisation's custom blocked URLs list, the user is taken to a warning page
* If the URL sends an end-user to a website that has been determined to be malicious, the user is taken to a warning page
* If the URL goes to a downloadable file and the ATP Safe Links policies are configured to scan such downloads, the downloadable file is checked
* If the URL is considered safe, the end-user is taken to the website

Safe Links Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Office 365 ATP Safe Links | Configured | Configured to align with ACSC - PROTECT - Malicious Email Mitigation Strategies \(June 2020\) and Microsoft guidance. |

Safe Links Configuration applicable to all agencies and implementation types

| Configuration | Value | Description |
| :--- | :--- | :--- |
| **Settings that apply to content across Office 365** |  |  |
| Block the following URL's | No URLs defined | Managing the Blocked URL list is an ongoing administrative task. Agencies will need to consider the resourcing requirements of maintaining a blocked URL list. |
| **Settings that apply to content except mail** |  |  |
| Use safe links in Office 365 ProPlus, Office for iOS and Android | Checked | Safe links will be checked by default within these Office 365 applications. |
| For the locations selected above: Do not track when users click safe links | Unchecked | Information about when end-users click safe links in the Office 365 documents will be tracked. |
| For the locations selected above: Do not let users click through safe links to original URL | Checked | If end-users click on safe links in Office 365 documents, then they will be directed to a warning page and will not be presented with an option to continue to the original link. |

## Safe Attachments

The ATP Safe Attachments feature checks email attachments after the email is received but before it is delivered to the user mailbox.

When an ATP Safe Attachments policy is in place and an end-user who is covered by that policy views their email in Office 365, their email attachments are checked, and appropriate actions are taken, based on the configured policies. To deploy this feature, an Office 365 E5 subscription or an Advanced Threat Protection licence is required.

Safe Attachments Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Office 365 ATP Safe Attachments | Configured | Configured in accordance with PROTECT - Malicious Email Mitigation Strategies \(June 2020\) |

ATP Safe Attachments Configuration applicable to all agencies and implementation types

| Configuration | Value | Description |
| :--- | :--- | :--- |
| Protect files in SharePoint, OneDrive, and Microsoft Teams | Ticked | If a file in any SharePoint, OneDrive, or Microsoft Teams library is identified as malicious, ATP will prevent users from opening and downloading the file. |
| Turn on Safe Documents for Office clients | Ticked | Before a user is allowed to trust a file opened in Office 365 ProPlus, the file will be verified by Microsoft Defender Advanced Threat Protection. |
| Warning | Dynamic Delivery | Dynamic Delivery ensures attachments are scanned and detected malware is quarantined. It also includes attachment previewing capabilities for most PDFs and Office files during scanning. |
| Redirect attachment on detection. Send the blocked, monitored or replaced attachment to an email address | Enable Redirect - Ticked | This will send blocked or replaced email messages with an attachment that is identified as malicious to a selected email address. |
| Apply the above selection of malware scanning for attachments times out or error occurs | Ticked | Will redirect an end-user's email messages to a selected email address even if a time out or error occurs when malware scanning an attachment. This allows legitimate emails to be recovered and malware to be investigated. |
| Applied to | Configured | All Agency domains \(e.g., dta.gov.au\). |

## Anti-Phishing

ATP anti-phishing protects users by checking incoming messages for indicators that the message may be spoofed by impersonator or part of a phishing campaign. Most phishing emails involves a malicious actor disguising oneself \(spoofing\) as an individual who is known to the recipient. The messaged is crafted in a such a way which can trick the user into clicking a link, downloading malware, or stealing user credentials.

Anti-phishing uses mailbox intelligence to build a profile of communication habits between each user and maps out these relationship patterns. In an event of a phishing campaign ATP will analyse the message behaviour against the user profiles to determine if the sender is legitimate or an impersonator.

Anti-spoof specifically analyses the senders address to determine if it is legitimate or forged. Administrators can allow our block specific users from spoofing an internal domain. i.e. An external organisation to send out advertising or products on behalf of the agency.

Anti-phishing Design Decisions for all agencies and implementation types.

| Decision Point | Design Decision | Justification |
| :--- | :--- | :--- |
| Office 365 ATP Anti-Phishing | Configured | Configured to meet ACSC - PROTECT - Malicious Email Mitigation Strategies \(June 2020\) |

Anti-Phishing Configuration applicable to all agencies and implementation types

| Configuration | Value | Description |
| :--- | :--- | :--- |
| **Impersonation Policy** |  |  |
| Add users to protect | Off | Add up to 60 internal and external users you want to protect from being impersonated by attackers. |
| Add domains to protect | Automatically include the domains I own: On Include custom domains: Off | Specify domains which you want to protect from being impersonated by attackers. |
| Actions | If email is sent by an impersonated user: Quarantine the message If email is sent by an impersonated domain: Quarantine the message | Specify an action in an event an attacker impersonates the users or domains you have specified. |
| Mailbox Intelligence | Enable mailbox intelligence: On Enable mailbox intelligence based on impersonated protection: On If an email is sent by an impersonate user: Quarantine the message | This feature uses machine learning to determine a user's email patterns with their contacts. With this information, the artificial intelligence can better distinguish between genuine and phishing emails. Impersonated protection allows Office 365 to customize user impersonation detection and better handle false positives. When user impersonation is detected, based on mailbox intelligence, you can define what action to take on the message. |
| Add trust senders and domains | Not configured | When users interact with domains or users that trigger impersonation but are considered to be safe. i.e. if a partner has the same/similar display name or domain name as a user defined on the list. |
| **Spoofing Policy** |  |  |
| Spoofing filter settings | Enable antispoofing protection: On | Allows the Agency to filter email from senders who are spoofing domains. |
| Enable Unauthenticated Sender Feature | Enable Unauthenticated Sender: On | Displays a notification to users in Outlook when a sender fails authentication checks. |
| Actions | If email is sent by someone who's not allowed to spoof your domain: Quarantine the message | Specify an action in an event an unauthorised user spoofs a domain. |

