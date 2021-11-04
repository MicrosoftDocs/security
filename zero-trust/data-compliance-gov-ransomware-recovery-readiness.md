---
title: Step 2. Ransomware recovery readiness
description: Ransomware recovery readiness 
ms.service: security
ms.author: josephd
author: JoeDavies-MSFT
manager: dansimp
ms.topic: conceptual
---

# Step 2. Ransomware recovery readiness

You must prepare your organization so that it has a viable alternative to paying the ransom demanded by ransomware attackers. While attackers in control of your organization have a variety of ways to pressure you into paying, the demands primarily focus on two categories:

- **Pay to regain access**

  Attackers demand payment under the threat that they won’t give you back access to your systems and data. This is most frequently done by encrypting your systems and data and demanding payment for the decryption key. 

  >[!Important]
  >Paying the ransom isn’t as simple and clean of a solution as it may seem. Because you're dealing with criminals that are only motivated by payment (and often relatively amateur operators who are using a toolkit provided by someone else), there is a lot of uncertainty around how well paying the ransom will actually work. There is no legal guarantee that they will provide a key that decrypts 100% of your systems and data, or even provide a key at all. The process to decrypt these systems uses homegrown attacker tools, which is often a clumsy and manual process.
  >

- **Pay to avoid disclosure**

   Attackers demand payment in exchange for not releasing sensitive or embarrassing data to the dark web (other criminals) or the general public. 

To avoid being forced into payment (the profitable situation for attackers), the most immediate and effective action you can take is to ensure your organization can restore your entire enterprise from immutable storage, which neither the attacker nor you can modify. 

Identifying the most sensitive assets and protecting them at a higher level of assurance is also critically important but is a longer and more challenging process to execute. We don’t want you to hold up other areas in phases 1 or 2, but we recommend you get the process started by bringing together business, IT, and security stakeholders to ask and answer questions like: 

- What business assets would be the most damaging if compromised? For example, what assets would business leadership would be willing to pay an extortion demand if attackers controlled them? 
- How do these business assets translate to IT assets (files, applications, databases, servers, etc.)?
- How can we protect or isolate these assets so that attackers with access to the general IT environment can’t access them? 

## Secure backups

You must ensure that critical systems and their data are backed up and backups are immutable to protect against deliberate erasure or encryption by an attacker.

Attacks on your backups focus on crippling your organization’s ability to respond without paying, frequently targeting backups and key documentation required for recovery to force you into paying extortion demands. 

Most organizations don’t protect backup and restoration procedures against this level of intentional targeting. 

>[!Note]
>This preparation also improves resilience to natural disasters and rapid attacks like WannaCry and (Not)Petya.
>

[Backup and restore plan to protect against ransomware](backup-plan-to-protect-against-ransomware.md) addresses what to do before an attack to protect your critical business systems and during an attack to ensure a rapid recovery of your business operations.

### Program and project member accountabilities

This table describes the overall protection of your data from ransomware in terms of a sponsorship/program management/project management hierarchy to determine and drive results.

| Lead | Implementor | Accountability |
|:-------|:-------|:-----|
| [Central IT](/azure/cloud-adoption-framework/organize/central-it) Operations or CIO | | Executive sponsorship |
| Program lead from [Central IT](/azure/cloud-adoption-framework/organize/central-it) infrastructure | | Drive results and cross-team collaboration |
|  | [Central IT](/azure/cloud-adoption-framework/organize/central-it) Infrastructure/Backup | Enable Infrastructure backup |
|  | [Central IT](/azure/cloud-adoption-framework/organize/central-it) Productivity/End User | Enable OneDrive Backup |
|  | [Security Architecture](/azure/cloud-adoption-framework/organize/cloud-security-architecture)  | Advise on configuration and standards |
| | [Security Policy and Standards](/azure/cloud-adoption-framework/organize/cloud-security-policy-standards) | Update standards and policy documents |
| | [Security Compliance Management](/azure/cloud-adoption-framework/organize/cloud-security-compliance-management) | Monitor to ensure compliance |
|  |  |  |


### Deployment objectives

Meet these deployment objectives to to secure your backup infrastructure.

| Done | Deployment objective | Owner |
|:-------|:-------|:-----|:--------|
| <input type="checkbox" /> | 1. Protect supporting documents required for recovery such as restoration procedure documents, your configuration management database (CMDB), and network diagrams. | IT architect or implementator |
| <input type="checkbox" /> | 2. Establish process to backup all critical systems automatically on a regular schedule and monitor adherance. | IT backup administrator  |
| <input type="checkbox" /> | 3. Establish process and schedule to regularly exercise your business continuity/disaster recovery (BC/DR) plan. | IT architect |
| <input type="checkbox" /> | 4. Include protecting backups against deliberate erasure and encryption in your backup plan: <br><br> - Strong Protection – Require out of band steps (MFA or PIN) before modifying online backups (such as [Azure Backup](/azure/backup/backup-azure-security-feature#prevent-attacks)). <br><br> - Strongest Protection – Store backups in online immutable storage (such as [Azure Blob](/azure/storage/blobs/storage-blob-immutable-storage)) and/or fully offline or off-site.  | IT backup administrator |


<!--

### Implementation results and timelines

Within 30 days, ensure that Mean Time to Recover (MTTR) meets your BC/DR goal, as measured during simulations and real-world operations.

## Data protection

You must implement data protection to ensure rapid and reliable recovery from a ransomware attack and to block some techniques of attackers.

Ransomware extortion and destructive attacks only work when all legitimate access to data and systems is lost. Ensuring that attackers cannot remove your ability to resume operations without payment will protect your business and undermine the monetary incentive for attacking your organization.

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
|  |  |  |

### Implementation checklist

Apply these best practices to protect your organization data.

| Done| Task | Description |
|:-------|:-------|:-----|
| <input type="checkbox" /> | Migrate your organization to the cloud: <br><br> - Move user data to cloud solutions like OneDrive/SharePoint to take advantage of [versioning and recycle bin capabilities](/microsoft-365/enterprise/microsoft-365-malware-and-ransomware-protection#sharepoint-online-and-onedrive-for-business-protection-against-ransomware). <br><br> - Educate users on how to [recover their files](https://support.microsoft.com/office/restore-your-onedrive-fa231298-759d-41cf-bcd0-25ac53eb8a15) by themselves to reduce delays and cost of recovery. | User data in the Microsoft cloud can be protected by built-in security and data management features. |
| <input type="checkbox" /> | Designate [Protected Folders](/windows/security/threat-protection/microsoft-defender-atp/controlled-folders). | Makes it more difficult for unauthorized applications to modify the data in these folders. |
| <input type="checkbox" /> | Review your permissions: <br><br> - Discover broad write/delete permissions on file shares, SharePoint, and other solutions. Broad is defined as many users having write/delete permissions for business-critical data. <br><br> - Reduce broad permissions while meeting business collaboration requirements.  <br><br> - Audit and monitor to ensure broad permissions don’t reappear. | Reduces risk from broad access-enabling ransomware activities. |
|  |  |  |

--> 

## Next step

Continue the user access and productivity initiative with [Step 3. Data](data-compliance-gov-data.md).

