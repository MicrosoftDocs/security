---
title: Step 2. Ransomware recovery readiness
description: Ransomware recovery readiness 
ms.service: security
ms.author: josephd
author: JoeDavies-MSFT
manager: dansimp
ms.topic: conceptual
---

# RaMP checklist —  Ransomware recovery readiness

This Rapid Modernization Plan (RaMP) checklist helps you prepare your organization so that it has a viable alternative to paying the ransom demanded by ransomware attackers. While attackers in control of your organization have a variety of ways to pressure you into paying, the demands primarily focus on two categories:

- **Pay to regain access**

  Attackers demand payment under the threat that they won’t give you back access to your systems and data. This is most frequently done by encrypting your systems and data and demanding payment for the decryption key. 

  >[!Important]
  >Paying the ransom isn’t as simple and clean of a solution as it may seem. Because you're dealing with criminals that are only motivated by payment (and often relatively amateur operators who are using a toolkit provided by someone else), there is a lot of uncertainty around how well paying the ransom will actually work. There is no legal guarantee that they will provide a key that decrypts 100% of your systems and data, or even provide a key at all. The process to decrypt these systems uses homegrown attacker tools, which is often a clumsy and manual process.
  >

- **Pay to avoid disclosure**

   Attackers demand payment in exchange for not releasing sensitive or embarrassing data to the dark web (other criminals) or the general public. 

To avoid being forced into payment (the profitable situation for attackers), the most immediate and effective action you can take is to ensure your organization can restore your entire enterprise from immutable storage that has not already been infected or encrypted by a ransomware attack, which neither the attacker nor you can modify. 

Identifying the most sensitive assets and protecting them at a higher level of assurance is also critically important but is a longer and more challenging process to execute. We don’t want you to hold up other areas, but we recommend you get the process started by bringing together business, IT, and security stakeholders to ask and answer questions like: 

- What business assets would be the most damaging if compromised? For example, what assets would business leadership be willing to pay an extortion demand if attackers controlled them? 
- How do these business assets translate to IT assets such as files, applications, databases, and servers?
- How can we protect or isolate these assets so that attackers with access to the general IT environment can’t access them? 

## Secure backups

You must ensure that critical systems and their data are backed up and are immutable to protect against deliberate erasure or encryption by an attacker. The backups **must have not already been infected or encrypted by a ransomware attack**, otherwise you are restoring a set of files that could contain entry points for the attackers to exploit after the recovery.

Attacks on your backups focus on crippling your organization’s ability to respond without paying, frequently targeting backups and key documentation required for recovery to force you into paying extortion demands. 

Most organizations don’t protect backup and restoration procedures against this level of intentional targeting. 

>[!Note]
>This preparation also improves resilience to natural disasters and rapid attacks like WannaCry and (Not)Petya.
>

[Backup and restore plan to protect against ransomware](/security/compass/backup-plan-to-protect-against-ransomware) addresses what to do before an attack to protect your critical business systems and during an attack to ensure a rapid recovery of your business operations using Azure Backup and other Microsoft cloud services. If you are using an offsite backup solution provided by a third-party, please consult their documentation.

### Program and project member accountabilities

This table describes the overall protection of your data from ransomware in terms of a sponsorship/program management/project management hierarchy to determine and drive results.

| Lead | Owner | Accountability |
|:-------|:-------|:-----|
| Central IT Operations or CIO | | Executive sponsorship |
| Program lead from Central IT infrastructure | | Drive results and cross-team collaboration |
|  | Infrastructure/Backup Engineer | Enable Infrastructure backup |
|  | Microsoft 365 Admins | Implement changes to Microsoft 365 tenant for [OneDrive](/microsoft-365/enterprise/microsoft-365-malware-and-ransomware-protection#sharepoint-online-and-onedrive-for-business-protection-against-ransomware) and Protected Folders |
|  | Security Engineer | Advise on configuration and standards |
|  | IT Admin | Update standards and policy documents |
|  | Security Governance and/or IT Admin | Monitor to ensure compliance |
|  | User Education Team | Ensure guidance for users recommends the use of OneDrive and Protected Folders |

### Deployment objectives

Meet these deployment objectives to secure your backup infrastructure.

| Done | Deployment objective | Owner |
|:-------|:-------|:-----|:--------|
| <input type="checkbox" /> | 1. Protect supporting documents required for recovery such as restoration procedure documents, your configuration management database (CMDB), and network diagrams. | IT architect or implementer |
| <input type="checkbox" /> | 2. Establish process to backup all critical systems automatically on a regular schedule and monitor adherence. | IT backup administrator |
| <input type="checkbox" /> | 3. Establish process and schedule to regularly exercise your business continuity/disaster recovery (BC/DR) plan. | IT architect |
| <input type="checkbox" /> | 4. Include protecting backups against deliberate erasure and encryption in your backup plan: <br><br> - Strong Protection – Require out-of-band steps (such as multifactor authentication or a PIN) before modifying online backups (such as [Azure Backup](/azure/backup/backup-azure-security-feature#prevent-attacks)). <br><br> - Strongest Protection – Store backups in online immutable storage (such as [Azure Blob](/azure/storage/blobs/storage-blob-immutable-storage)) and/or fully offline or off-site.  | IT backup administrator |
| <input type="checkbox" /> | 5. Have your users configure [OneDrive backup](https://support.microsoft.com/office/back-up-your-documents-pictures-and-desktop-folders-with-onedrive-d61a7930-a6fb-4b95-b28a-6552e77c3057) and [Protected Folders](/windows/security/threat-protection/microsoft-defender-atp/controlled-folders).  | Microsoft 365 productivity administrator |


## Next step

Continue the data, compliance, and governance initiative with [Step 3. Data](data-compliance-gov-data.md).

