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
- How do these business assets translate to IT assets such as files, applications, databases, and servers?
- How can we protect or isolate these assets so that attackers with access to the general IT environment can’t access them? 

## Secure backups

You must ensure that critical systems and their data are backed up and backups are immutable to protect against deliberate erasure or encryption by an attacker.

Attacks on your backups focus on crippling your organization’s ability to respond without paying, frequently targeting backups and key documentation required for recovery to force you into paying extortion demands. 

Most organizations don’t protect backup and restoration procedures against this level of intentional targeting. 

>[!Note]
>This preparation also improves resilience to natural disasters and rapid attacks like WannaCry and (Not)Petya.
>

[Backup and restore plan to protect against ransomware](https://docs.microsoft.com/security/compass/backup-plan-to-protect-against-ransomware) addresses what to do before an attack to protect your critical business systems and during an attack to ensure a rapid recovery of your business operations.

### Program and project member accountabilities

This table describes the overall protection of your data from ransomware in terms of a sponsorship/program management/project management hierarchy to determine and drive results.

| Lead | Implementer | Accountability |
|:-------|:-------|:-----|
| Central IT Operations or CIO | | Executive sponsorship |
| Program lead from Central IT infrastructure | | Drive results and cross-team collaboration |
|  | Central IT Infrastructure/Backup | Enable Infrastructure backup |
|  | Central IT Productivity/End User | Enable OneDrive Backup |
|  | Security Architecture  | Advise on configuration and standards |
| | Security Policy and Standards | Update standards and policy documents |
| | Security Compliance Management | Monitor to ensure compliance |
|  |  |  |


### Deployment objectives

Meet these deployment objectives to to secure your backup infrastructure.

| Done | Deployment objective | Owner |
|:-------|:-------|:-----|:--------|
| <input type="checkbox" /> | 1. Protect supporting documents required for recovery such as restoration procedure documents, your configuration management database (CMDB), and network diagrams. | IT architect or implementer |
| <input type="checkbox" /> | 2. Establish process to backup all critical systems automatically on a regular schedule and monitor adherence. | IT backup administrator  |
| <input type="checkbox" /> | 3. Establish process and schedule to regularly exercise your business continuity/disaster recovery (BC/DR) plan. | IT architect |
| <input type="checkbox" /> | 4. Include protecting backups against deliberate erasure and encryption in your backup plan: <br><br> - Strong Protection – Require out of band steps (such as multifactor authentication or PIN) before modifying online backups (such as [Azure Backup](/azure/backup/backup-azure-security-feature#prevent-attacks)). <br><br> - Strongest Protection – Store backups in online immutable storage (such as [Azure Blob](/azure/storage/blobs/storage-blob-immutable-storage)) and/or fully offline or off-site.  | IT backup administrator |

## Next step

Continue the user access and productivity initiative with [Step 3. Data](data-compliance-gov-data.md).

