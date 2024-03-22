---
title: How do I protect my resources in Azure from destructive cyber attacks?
description: How to apply Zero Trust principles to your recovery plan 
ms.date: 03/20/2024
ms.service: security
author: brsteph
ms.author: bstephenson, sdolgin
ms.topic: conceptual
ms.collection: 
  - msftsolution-azureiaas
  - msftsolution-scenario
  - zerotrust-solution
  - zerotrust-azure
---

# How do I protect my resources in Azure from destructive cyber attacks?

Here is some intro stuff.  We want to talk about what the attack is, and refer them back to the [Implement security breach prevention and recovery infrastructure](./adopt/prevent-reduce-business-damage-breach-infrastructure.md) for over all adoption guidance.

We want to reiterate about our audience here - technical implementers as part of the adoption - and set expectations about what we want to do - which is to guide implementers through setting up protection, setting up detection, and reacting.

## Configuring Protection

We already have a lot of good articles that detail how to set up protection.  For example, this tutorial on [Set up disaster recovery for Azure VMs](azure/site-recovery/azure-to-azure-tutorial-enable-replication) gives instructions for setting up disaster recovery and gives links to drills, failover and reprotect, and failback.

We definitely want to take them to [Backup and restore plan to protect against ransomware](azure/security/fundamentals/backup-plan-to-protect-against-ransomware)

It would be nice if that section had an overview that we could link to, but that's a seperate revision.

We also have:
- [Create and configure a Recovery Services vault](azure/backup/backup-create-recovery-services-vault)
- [Back up a virtual machine in Azure](azure/backup/quick-backup-vm-portal)
- [Configure backup for an AKS cluster](azure/backup/quick-backup-aks)

We could make this a table that has services and protection considerations.

Do we want to explain the difference between backup and recovery protection?  That  feels like it is at a higher level.

Maybe we have a table like this:

| Service | Data Backup | Resource Protection |
|---|---|---|
| Virtual Machines | [Back up a virtual machine in Azure](azure/backup/quick-backup-vm-portal) | [Set up disaster recovery for Azure VMs](azure/site-recovery/azure-to-azure-tutorial-enable-replication) |

We need to include specific guidance for the persistent settings that are needed to protect backups and replication from being deleted.

## Configure Detection

Here is where things are unclear for me - what is the best way to detect that resources are being destroyed or targetted for destruction?

## Response

Would this be a kind of response guide?  Would this be its own playbook?

We could link them to the following:

- [Fail over Azure VMs to a secondary region](azure/site-recovery/azure-to-azure-tutorial-failover-failback)
- [How to restore Azure VM data in Azure portal](azure/backup/backup-azure-arm-restore-vms)
- [Restore files to a virtual machine in Azure](azure/backup/tutorial-restore-files)
- [Recover soft deleted data and recovery points using enhanced soft delete in Azure Backup](azure/backup/backup-azure-enhanced-soft-delete-tutorial?tabs=recovery-services-vault)

None of these are Zero Trust specific, but I don't think there are specific response differences.
