---
title: RaMP checklist — Data protection
description: Use the steps in this guidance to deploy data protection that adheres to Zero Trust principles.
ms.date: 01/08/2024
ms.service: security
ms.author: dansimp
author: dansimp
manager: dansimp
ms.topic: conceptual
ms.collection:
  - zerotrust-ramp
---

# RaMP checklist — Data protection

<!---

Writers notes:

For updates to product names, please also update the appropriate figures.

To update figures that are not screen shots, your options are:

- Locate the source Visio file in internal storage.
- Use the published Visio file in the Microsoft Download Center (see the "Technical publications" section of this article).
- For figures that are published in Scalable Vector Graphics (SVG) format, save the SVG file from the article web page, insert into Visio, modify, and then save it as a new version of the SVG file.

For new articles in this content set, please:

- Add a link in the zero-trust-ramp-overview.md to the new article.
- Add a link to the Zero Trust Guidance Center page (index.yml).

--->

This Rapid Modernization Plan (RaMP) checklist helps you protect your on-premises and cloud data from both inadvertent and malicious access. 

- Inadvertent access occurs when a user gains access to data that, based on their roles and responsibilities, they should not have. The result can be unintended data leakage, data destruction, or violations of data security and privacy regulations.

- Malicious access occurs when an external attacker or a malicious insider intentionally tries to access data. Malicious insiders can use your data for profit or to harm your organization. External attackers can delete, alter, exfiltrate, and encrypt your most sensitive data, leaving you open to a ransomware attack.

For both types of attacks, you must take the necessary steps to identify your data, protect it, prevent its destruction or exfiltration, and ensure that only users with a business purpose have access to it.

Protecting your data is part of the "assume breach" Zero Trust principle. Even with all the user account and device protections in place, you must assume that an attacker could find their way in and begin traversing your environment, searching for the most valuable data for your organization.

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
| | Microsoft 365 Admins |  Implement changes to Microsoft 365 tenant for OneDrive and Protected Folders |
| | Data Security Engineer and/or Infrastructure Security Engineer | Enable infrastructure backup |
| | Application Owners | Identify critical business assets |
| | Data Security Admin | Implement configuration changes |
| | IT Admin | Update standards and policy documents |
| | Security Governance and/or IT Admin | Monitor to ensure compliance |
| | User Education Team | Ensure guidance for users reflects policy updates |


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

| Done | Implementation step | Owner | Documentation |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> | 1. Determine data classification levels. | Data Security Architect | [Learn about](/purview/data-classification-overview#sensitive-information-types-used-most-in-your-content) |
| <input type="checkbox" /> | 2. Determine built-in and custom sensitive information types. | Data Security Architect | [Learn about](/purview/sensitive-information-type-learn-about) |
| <input type="checkbox" /> | 3. Determine the use of pre-trained and custom trainable classifiers. | Data Security Architect | [Learn about](/purview/classifier-learn-about) |
| <input type="checkbox" /> | 4. Discover and classify sensitive data. | Data Security Architect and/or Data Security Engineer | [Learn about](/purview/data-classification-overview) |

<a id="protect"></a>
### 2. Protect your data

Perform these implementation steps to meet the **Protect your data** deployment objective.

| Done | Implementation step | Owner | Documentation |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> | 1. Determine the use and design of sensitivity labels. | Security Architect | [Get started](/purview/get-started-with-sensitivity-labels) |
| <input type="checkbox" /> | 2. Label and protect items for Microsoft 365 apps and services. | Data Security Engineer | [Manage sensitivity labels](/purview/sensitivity-labels-office-apps) |
| <input type="checkbox" /> | 3. Enable and configure Microsoft Defender for Cloud Apps. | Data Security Engineer | [Get started](/defender-cloud-apps/get-started) |
| <input type="checkbox" /> | 4. Discover, label, and protect sensitive items that reside in data stores in the cloud.  | Data Security Engineer | [Best practices](/defender-cloud-apps/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud) |
| <input type="checkbox" /> | 5. Discover, label, and protect sensitive items that reside in on-premises data stores. | Data Security Engineer | [Information protection scanner](/purview/deploy-scanner-configure-install) |
| <input type="checkbox" /> | 6. Extend your sensitivity labels to Azure by using Microsoft Purview Data Map | Data Security Engineer | [Labeling in the Microsoft Purview Data Map](/purview/create-sensitivity-label) |

<a id="prevent"></a>
### 3. Prevent data loss

Perform these implementation steps to meet the **Prevent data loss** deployment objective.

| Done | Implementation step | Owner | Documentation |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> | 1. Design and create data loss prevention (DLP) policies. | Security Architect | [Learn about](/purview/dlp-learn-about-dlp) |
| <input type="checkbox" /> | 2. Enable and configure endpoint data loss prevention. | Data Security Engineer | [Learn about](/purview/endpoint-dlp-learn-about) |
| <input type="checkbox" /> | 3. Configure access policies for Microsoft Defender for Cloud Apps Conditional Access App Control. | Data Security Engineer | [Overview](/cloud-app-security/proxy-intro-aad) |


<a id="strict"></a>
### 4. Use least privilege access

Perform these implementation steps to ensure that your users and admins meet the **Use least privilege access** deployment objective.

| Done | Implementation step | Owner |
|:-------|:-------|:-----|
| <input type="checkbox" /> | 1. From the **Know your data** deployment objective, review the permissions for the locations of sensitive and critical information. | Data Security Engineer |
| <input type="checkbox" /> | 2. Implement minimal permissions for the sensitive and critical information while meeting collaboration and business requirements and inform the users who are affected. | Data Security Engineer |
| <input type="checkbox" /> | 3. Perform change management for your employees so that future locations for sensitive and critical information are created and maintained with minimal permissions. | User Education Team |
| <input type="checkbox" /> | 4. Audit and monitor the locations for sensitive and critical information to ensure that broad permissions aren't being granted. | Data Security Engineer and/or Security Governance Admin |

## Results

After completing these deployment objectives, you will have built out the **Data** section of the Zero Trust architecture.

:::image type="content" source="./media/user-access-productivity-overview/data-compliance-gov-data.png" alt-text="The Data section of the Zero Trust architecture" lightbox="./media/user-access-productivity-overview/data-compliance-gov-data.png":::

