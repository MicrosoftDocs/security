---
title: Step 3. Data
description: Data
ms.service: security
ms.author: josephd
author: JoeDavies-MSFT
manager: dansimp
ms.topic: conceptual
---

# Step 3. Data

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

- Use least privilege access

  Apply minimal permissions consisting of who is allowed to access and what they are allowed to do with data to meet business and productivity requirements.

## Program and project member accountabilities

This table describes the overall protection of your organization data in terms of a sponsorship/program management/project management hierarchy to determine and drive results.


| Lead | Owner | Accountability |
|:-------|:-------|:-----|
|  CISO, CIO, or Director of Data Security | | Executive sponsorship |
| Program lead from Data Security | | Drive results and cross-team collaboration |
| | Security Architect  | Advise on configuration and standards |
| | Application Owners |  Implement changes to Microsoft 365 tenant for OneDrive and Protected Folders |
| | Data Security and/or Infrastructure Security | Enable infrastructure backup |
| | Application Owners | Identify critical business assets |
| | Data Security | Implement configuration changes |
| | IT Admin | Update standards and policy documents |
| | Security Governance and/or IT Admin | Monitor to ensure compliance |
| | User Education | Ensure guidance for users reflects policy updates |


## Deployment objectives

Meet these deployment objectives to protect your data for Zero Trust.

| Done | Deployment objective | Owner |
|:-------|:-------|:-----|
| <input type="checkbox" /> | [1. Know your data](#know) | Data Security Architect |
| <input type="checkbox" /> | [2. Protect your data](#protect) | Data Security Engineer |
| <input type="checkbox" /> | [3. Prevent data loss](#prevent) | Data Security Engineer |
| <input type="checkbox" /> | [4. Use least privilege access](#strict) | Data Security Engineer |

<a id="know"></a>
### 1. Know your data

Perform these implementation steps to meet the **Know your data** deployment objective.

| Done | Implementation objective and results | Owner | Documentation |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> | 1. Determine data classification levels. | Data Security Architect | [Learn about](https://docs.microsoft.com/microsoft-365/compliance/data-classification-overview#sensitive-information-types-used-most-in-your-content) |
| <input type="checkbox" /> | 2. Determine built-in and custom sensitive information types. | Data Security Architect | [Learn about](https://docs.microsoft.com/microsoft-365/compliance/sensitive-information-type-learn-about) |
| <input type="checkbox" /> | 3. Determine the use of pre-trained and custom trainable classifiers. | Data Security Architect | [Learn about](https://docs.microsoft.com/en-us/microsoft-365/compliance/classifier-learn-about) |
| <input type="checkbox" /> | 4. Discover and classify sensitive data. | Data Security Architect | [Learn about](https://docs.microsoft.com/microsoft-365/compliance/data-classification-overview) |

<a id="protect"></a>
### 2. Protect your data

Perform these implementation steps to meet the **Protect your data** deployment objective.

| Done | Implementation objective and results | Owner | Documentation |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> | 1. Determine the use and design of sensitivity labels. | Security Architect | [Get started](https://docs.microsoft.com/microsoft-365/compliance/get-started-with-sensitivity-labels) |
| <input type="checkbox" /> | 2. Label and protect items for Microsoft 365 apps and services. | Data Security Engineer | [Manage sensitivity labels](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-office-apps) |
| <input type="checkbox" /> | 3. Enable and configure Microsoft Cloud App Security. | Data Security Engineer | [Get started](https://docs.microsoft.com/cloud-app-security/getting-started-with-cloud-app-security) |
| <input type="checkbox" /> | 4. Discover, label, and protect sensitive items that reside in data stores in the cloud.  | Data Security Engineer | [Best practices](https://docs.microsoft.com//defender-cloud-apps/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud) |
| <input type="checkbox" /> | 5. Discover, label, and protect sensitive items that reside in on-premises data stores. | Data Security Engineer | [Azure Information Protection (AIP) unified labeling scanner](https://docs.microsoft.com//azure/information-protection/deploy-aip-scanner-configure-install) |
| <input type="checkbox" /> | 6. Extend your sensitivity labels to Azure resources Azure Purview | Data Security Engineer | [Labeling in Azure Purview](https://docs.microsoft.com//purview/create-sensitivity-label) |



<a id="prevent"></a>
### 3. Prevent data loss

Perform these implementation steps to meet the **Prevent data loss** deployment objective.

| Done | Implementation objective and results | Owner | Documentation |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> | 1. Design and create data loss prevention (DLP) policies. | Security Architect | [Learn about](https://docs.microsoft.com/microsoft-365/compliance/dlp-learn-about-dlp) |
| <input type="checkbox" /> | 2. Enable and configure endpoint data loss prevention. | Data Security Engineer | [Learn about](https://docs.microsoft.com/microsoft-365/compliance/endpoint-dlp-learn-about) |
| <input type="checkbox" /> | 3. Configure access policies for Cloud App Security Conditional Access App Control. | Data Security Engineer | [Overview](https://docs.microsoft.com/cloud-app-security/proxy-intro-aad) |


<a id="strict"></a>
### 4. Use least privilege access

Perform these implementation steps to ensure that your workers and admins meet the **Use least privilege access** deployment objective.

| Done | Implementation objective and results | Owner |
|:-------|:-------|:-----|
| <input type="checkbox" /> | 1. From the **Know your data** deployment objective, review the permissions for the locations of sensitive and critical information. | Data Security Engineer |
| <input type="checkbox" /> | 2. Implement minimal permissions for the sensitive and critical information while meeting collaboration and business requirements and inform the users that are affected. | Data Security Engineer |
| <input type="checkbox" /> | 3. Perform change management for your employees so that future locations for sensitive and critical information are created and maintained with minimal permissions. | User Education Team |
| <input type="checkbox" /> | 4. Audit and monitor the locations for sensitive and critical information to ensure that broad permissions aren't being granted. | Data Security Engineer and/or Security Governance |

## Results

After completing these deployment objectives, you will have built out the **Data** section of the Zero Trust architecture.

:::image type="content" source="./media/user-access-productivity-overview/data-compliance-gov-data.png" alt-text="The Data section of the Zero Trust architecture" lightbox="./media/user-access-productivity-overview/data-compliance-gov-data.png":::

## Next step

Continue your Zero Trust deployment journey with the [Modernize security operations initiative](modernize-security-operations-overview.md).
