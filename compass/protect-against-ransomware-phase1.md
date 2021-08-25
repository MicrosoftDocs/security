---
title: "Phase 1: Prepare your recovery plan"
ms.author: josephd
author: JoeDavies-MSFT
f1.keywords:
- NOCSH
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection: 
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-ransomware
- m365solution-overview
ms.custom: 
description: Prepare your organization so that you can recover from an attack without having to pay the ransom.

---

# Phase 1: Prepare your recovery plan

The first thing you should do for these attacks is prepare your organization so that it has a viable alternative to paying the ransom. While attackers in control of your organization have a variety of ways to pressure you into paying, the demands primarily focus on two categories:

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

You must ensure that critical systems and their data are backed up and backups are protected against deliberate erasure or encryption by an attacker.

Attacks on your backups focus on crippling your organization’s ability to respond without paying, frequently targeting backups and key documentation required for recovery to force you into paying extortion demands. 

Most organizations don’t protect backup and restoration procedures against this level of intentional targeting. 

>[!Note]
>This preparation also improves resilience to natural disasters and rapid attacks like WannaCry and (Not)Petya.
>

### Program and project member accountabilities

This table describes the overall protection of your data from ransomware in terms of a sponsorship/program management/project management hierarchy to determine and drive results.

| Lead | Implementor | Accountability |
|:-------|:-------|:-----|
| [Central IT](/azure/cloud-adoption-framework/organize/central-it) Operations or CIO | | Executive sponsorship |
| Program lead from [Central IT](/azure/cloud-adoption-framework/organize/central-it) infrastructure | | Drive results and cross-team collaboration |
|  | [Central IT](/azure/cloud-adoption-framework/organize/central-it) Infrastructure/Backup | Enable Infrastructure backup |
|  | [Central IT](/azure/cloud-adoption-framework/organize/central-it) Productivity / End User | Enable OneDrive Backup |
|  | [Security Architecture](/azure/cloud-adoption-framework/organize/cloud-security-architecture)  | Advise on configuration and standards |
| | [Security Policy and Standards](/azure/cloud-adoption-framework/organize/cloud-security-policy-standards) | Update standards and policy documents |
| | [Security Compliance Management](/azure/cloud-adoption-framework/organize/cloud-security-compliance-management) | Monitor to ensure compliance |
|  |  |  |

### Implementation checklist

Apply these best practices to secure your backup infrastructure.

| Done| Task | Description |
|:-------|:-------|:-----|
| <input type="checkbox" /> | Backup all critical systems automatically on a regular schedule. | Allows you to recover data up to the last backup. |
| <input type="checkbox" /> | Regularly exercise your business continuity/disaster recovery (BC/DR) plan. | Ensures rapid recovery of business operations by treating a ransomware or extortion attack with the same importance as a natural disaster. |
| <input type="checkbox" /> | Protect backups against deliberate erasure and encryption: <br><br> - Strong Protection – Require out of band steps (MFA or PIN) before modifying online backups (such as [Azure Backup](/azure/backup/backup-azure-security-feature#prevent-attacks)). <br><br> - Strongest Protection – Store backups in online immutable storage (such as [Azure Blob](/azure/storage/blobs/storage-blob-immutable-storage)) and/or fully offline or off-site. | Backups that are accessible by attackers can be rendered unusable for business recovery. |
| <input type="checkbox" /> | Protect supporting documents required for recovery such as restoration procedure documents, CMDB, and network diagrams. | Attackers deliberately target these resources because it impacts your ability to recover. |


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

## Next step

[![Phase 2. Limit the scope of damage](media/protect-against-ransomware/protect-against-ransomware-phase2.png)](protect-against-ransomware-phase2.md)

Continue with [Phase 2](protect-against-ransomware-phase2.md) to limit the scope of damage of an attack by protecting privileged roles.
