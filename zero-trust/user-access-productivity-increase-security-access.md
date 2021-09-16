---
title: Step 2. Increase security for accessing key resources
description: Increase security for accessing key resources 
ms.service: security
ms.author: josephd
author: JoeDavies-MSFT
manager: dansimp
ms.topic: conceptual
---

# Step 2. Increase security for accessing key resources

This step includes using Zero Trust to explicitly validate trust for all access requests for:

- [Apps](#apps)

  Enable Azure Active Directory (Azure AD) for all SaaS apps and VPN authentication and publish legacy on-premises and IaaS-based Web services with Azure AD Application Proxy.

- [Data](#data)

  Discover and protect sensitive data with Microsoft Information Protection, Microsoft 365 compliance features, and Microsoft Cloud App Security.

After completing this step, you will have built out this part of the Zero Trust architecture.

![The apps and data sections of the Zero Trust architecture](./media/user-access-productivity-overview/user-access-productivity-increase-security-key-resources-apps-data.png)


## Apps

Content TBD

After completing these deployment objectives, you will have built out the **apps** section of the Zero Trust architecture.

![The apps section of the Zero Trust architecture](./media/user-access-productivity-overview/user-access-productivity-validate-trust-apps.png)


## Data

Your cloud data is a primary target of cyber attackers. Once they have access to your data, they can delete, alter, exfiltrate, and encrypt it, leaving you open to a ransomware attack. You must take the necessary steps identify it, protect it in place, ensure that does not get deleted or exfiltrated, and configure access permissions to only those with a business purpose.

Protecting your data is part of the "assume breach" security principle. Even with all the user account and device protections in place, you must assume that an attacker could find their way in and begin traversing your environment, searching for the most valuable data for your organization.

<!--
Discover and protect sensitive data (via Cloud App Security, CA App Control, Microsoft Info Protection)

https://docs.microsoft.com/en-us/microsoft-365/compliance/information-protection?view=o365-worldwide

https://docs.microsoft.com/en-us/security/compass/protect-against-ransomware-phase1#data-protection

https://docs.microsoft.com/en-us/microsoft-365/solutions/information-protection-deploy-protect-information?view=o365-worldwide#managing-information-protection-in-microsoft-365

https://review.docs.microsoft.com/en-us/microsoft-365/solutions/protect-against-ransomware-microsoft-365-step5?view=o365-21vianet&branch=Josephd-M365-ransomware-solution
--> 

Therefore, you must:

- Know your data

  Understand your data landscape and identify important information across your cloud and on-premises environment.

- Protect your data

  Protect your sensitive data throughout its lifecycle by applying sensitivity labels linked to protection actions like encryption, access restrictions, visual markings, and more.

- Prevent data loss

  Apply a consistent set of data loss prevention policies across the cloud, on-premises environments, and endpoints to monitor, prevent, and remediate risky activities with sensitive data.


### Program and project member accountabilities

This table describes the overall protection of your organization data in terms of a sponsorship/program management/project management hierarchy to determine and drive results.

| Lead | Implementer | Accountability |
|:-------|:-------|:-----|
| [Central IT](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/central-it) Operations or CIO | | Executive sponsorship |
| Program lead from [Data Security](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-data-security) | | Drive results and cross-team collaboration |
|  | [Central IT](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/central-it) Productivity / End User |  Implement changes to Microsoft 365 tenant for OneDrive and Protected Folders |
|  | [Central IT](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/central-it) Infrastructure/Backup | Enable Infrastructure backup |
|  | Business / Application | Identify critical business assets |
|  | [Security Architecture](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-architecture)  | Advise on configuration and standards |
|  | [Security Policy and Standards](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-policy-standards) | Update standards and policy documents |
|  | [Security Compliance Management](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-compliance-management) | Monitor to ensure compliance |
|  | User Education Team | Ensure guidance for users reflects policy updates |

### Deployment objectives

Meet these deployment objectives to protect your data for Zero Trust.

| Done | Deployment objective | Owner |
|:-------|:-------|:-----|
| <input type="checkbox" /> | [1. Know your data](#know) | Data Security Architect |
| <input type="checkbox" /> | [2. Protect your data](#protect) | Data Security Engineer |
| <input type="checkbox" /> | [3. Prevent data loss](#prevent) | Data Security Engineer |
| <input type="checkbox" /> | [4. Use tight permissions](#tighten) | Data Security Engineer |

After completing these deployment objectives, you will have built out the **data** section of the Zero Trust architecture.

![The data section of the Zero Trust architecture](./media/user-access-productivity-overview/user-access-productivity-increase-security-key-resources-data.png)

#### <a id="know">1. Know your data</a>

Perform these implementation steps to meet the **Know your data** deployment objective.

| Done | Implementation objective and results | Owner | Documentation |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> | 1. Determine data classification levels. | Data Security Architect | [Learn about](https://docs.microsoft.com/microsoft-365/compliance/data-classification-overview) |
| <input type="checkbox" /> | 2. Determine built-in and custom sensitive information types. | Data Security Architect | [Learn about](https://docs.microsoft.com/microsoft-365/compliance/sensitive-information-type-learn-about) |

#### <a id="protect">2. Protect your data</a>

Perform these implementation steps to meet the **Protect your data** deployment objective.

| Done | Implementation objective and results | Owner | Documentation |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> | 1. Determine the use and design of sensitivity labels. | Security Architect | [Get started](https://docs.microsoft.com/microsoft-365/compliance/get-started-with-sensitivity-labels) |
| <input type="checkbox" /> | 2. Enable double key encryption | Data Security Engineer. | [Overview](https://docs.microsoft.com/microsoft-365/compliance/double-key-encryption) |
| <input type="checkbox" /> | 3. Enable Office Message Encryption (OME). | Data Security Engineer | [Overview](https://docs.microsoft.com/microsoft-365/compliance/ome) |
| <input type="checkbox" /> | 4. Enable and configure Microsoft Cloud App Security. | Data Security Engineer | [Get started](https://docs.microsoft.com/cloud-app-security/getting-started-with-cloud-app-security) |


#### <a id="prevent">3. Prevent data loss</a>

Perform these implementation steps to meet the **Prevent data loss** deployment objective.

| Done | Implementation objective and results | Owner | Documentation |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> | 1. Design and create data loss prevention (DLP) policies. | Security Architect | [Learn about](https://docs.microsoft.com/microsoft-365/compliance/dlp-learn-about-dlp) |
| <input type="checkbox" /> | 2. Enable and configure endpoint data loss prevention. | Data Security Engineer | [Learn about](https://docs.microsoft.com/microsoft-365/compliance/endpoint-dlp-learn-about) |
| <input type="checkbox" /> | 3. Configure access policies for Cloud App Security Conditional Access App Control. | Data Security Engineer | [Overview](https://docs.microsoft.com/cloud-app-security/proxy-intro-aad) |


#### <a id="tighten">4. Use tight permissions</a>

Perform these implementation steps to meet the **Use tight permissions** deployment objective.

| Done | Implementation objective and results | Owner |
|:-------|:-------|:-----|
| <input type="checkbox" /> | 1. From the **Know your data** deployment objective, review the permissions for the locations of sensitive and critical information. | Data Security Engineer |
| <input type="checkbox" /> | 2. Implement strict permissions for the sensitive and critical information while meeting collaboration and business requirements and inform the users that are affected. | Data Security Engineer |
| <input type="checkbox" /> | 3. Perform change management for your users so that future locations for sensitive and critical information are created and maintained with strict permissions. | User Education Team |
| <input type="checkbox" /> | 4. Audit and monitor the locations for sensitive and critical information to ensure that broad permissions aren't being granted. | Data Security Engineer |

## Next step

Continue your Zero Trust deployment journey with the [Modernize security operations area](modernize-security-operations-overview.md).

