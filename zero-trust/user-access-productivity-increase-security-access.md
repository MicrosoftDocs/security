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

- Apps

  Enable Azure AD for all SaaS, for VPN authentication, and publish legacy on-premises/IaaS via App Proxy.

- Devices

  Discover and protect sensitive data (via Cloud App Security, CA App Control, Microsoft Info Protection).

After completing this step, you will have built out this part of the Zero Trust architecture.

![The apps and data sections of the Zero Trust architecture](./media/user-access-productivity-overview/user-access-productivity-increase-security-key-resources-apps-data.png)


## Apps

Content TBD

## Data

Discover and protect sensitive data (via Cloud App Security, CA App Control, Microsoft Info Protection)


- Know your data

  Understand your data landscape and identify important information across your cloud and on-premises environment.

- Protect your data

  Protect your sensitive data throughout its lifecycle by applying sensitivity labels linked to protection actions like encryption, access restrictions, visual markings, and more.

- Prevent data loss

  Apply a consistent set of data loss prevention policies across the cloud, on-premises environments, and endpoints to monitor, prevent, and remediate risky activities with sensitive data.

You must implement data protection to ensure rapid and reliable recovery from a ransomware attack and to block some techniques of attackers.

### Program and project member accountabilities

This table describes the overall protection of your organization data from ransomware in terms of a sponsorship/program management/project management hierarchy to determine and drive results.

| Lead | Implementor | Accountability |
|:-------|:-------|:-----|
| [Central IT](/azure/cloud-adoption-framework/organize/central-it) Operations or CIO | | Executive sponsorship |
| Program lead from [Data Security](/azure/cloud-adoption-framework/organize/cloud-security-data-security) | | Drive results and cross-team collaboration |
|  | [Central IT](/azure/cloud-adoption-framework/organize/central-it) Productivity / End User |  Implement changes to Microsoft 365 tenant for OneDrive and Protected Folders |
|  | [Central IT](/azure/cloud-adoption-framework/organize/central-it) Infrastructure/Backup | Enable Infrastructure backup |
|  | Business / Application | Identify critical business assets |
|  | [Security Architecture](/azure/cloud-adoption-framework/organize/cloud-security-architecture)  | Advise on configuration and standards |
|  | [Security Policy and Standards](/azure/cloud-adoption-framework/organize/cloud-security-policy-standards) | Update standards and policy documents |
|  | [Security Compliance Management](/azure/cloud-adoption-framework/organize/cloud-security-compliance-management) | Monitor to ensure compliance |
|  | User Education Team | Ensure guidance for users reflects policy updates |

### Deployment objectives

Meet these deployment objectives to protect your accounts with Zero Trust.

| Done | Deployment objective | Owner | Documentation |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> | 1.  | IT implementer |  |
| <input type="checkbox" /> | 2.  | IT implementer |  |
| <input type="checkbox" /> | 3.  | IT implementer |  |
| <input type="checkbox" /> | 4.  | IT implementer |  |
| <input type="checkbox" /> | 5.  | IT implementer |  |
| <input type="checkbox" /> | 6.  | IT implementer |  |
| <input type="checkbox" /> | 7.  | IT implementer |  |

You have now built out the data section of the Zero Trust architecture.

![The data section of the Zero Trust architecture](./media/user-access-productivity-overview/user-access-productivity-increase-security-key-resources-data.png)

## Next step

Continue your Zero Trust deployment journey with [Step 3. Governance](user-access-productivity-governance.md).
