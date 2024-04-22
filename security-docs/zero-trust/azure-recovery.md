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

> [!WARNING]
> This section is a STUB and needs to be updated.

Here is some intro stuff. We want to talk about what the attack is, and refer them back to the [Implement security breach prevention and recovery infrastructure](./adopt/prevent-reduce-business-damage-breach-infrastructure.md) for over all adoption guidance.

We want to reiterate about our audience here - technical implementers as part of the adoption - and set expectations about what we want to do - which is to guide implementers through setting up protection, setting up detection, and reacting.

## Configuring protection

Many organizations implement backup and disaster recover solutions for their virtual machines as part of a migration effort. They might use Azure native solutions or they might opt to use their own third party solutions to their ecosystem.

While protecting virtual machines is important, it is also critical to expand the scope of protection beyond virtual machines. This section gives a break down of considerations and recommendations for how to protect different types of resources in Azure from a destructive cyber attack.

In addition to the service specific considerations, you should consider using [Resource Locks](https://learn.microsoft.com/azure/azure-resource-manager/management/lock-resources?tabs=json) to prevent deletion of services by protecting their management plane. Resource locks can also be used to render resources read-only. Resource locks work with controlled access to reduce the chance of Azure resources being destroyed in a cyber attack by preventing the modification.

Resource locks do have additional considerations, however. You should review the [Considerations before applying your locks](https://learn.microsoft.com/azure/azure-resource-manager/management/lock-resources?tabs=json#considerations-before-applying-your-locks) to make sure you are applying the locks to the appropriate resources in a way that allows them to still operate.

Because of these considerations, you should prioritize locking resources that, if changed or deleted, would cause the most disruption. For example, locking a virtual network instead of a whole resource group can prevent the lock from being too restrictive on other resources.

Locks may also have some considerations for the Recovery Time Objectives for workloads being failed over. Your disaster recovery plan should take this into account, and you should have a tested procedure for teh removal of locks in a controlled manner. Training on how to manage locks as part of both day to day operations and emergency scenarios should occur.

Administrators with access to remove the locks should be limited, and should involve just-in-time access such as that provided with Privileged Identity Management. Access to this is controlled with the `Microsoft.Authorization/locks/*` scope, and should not be granted as part of standing access.

The removal of resource locks from a resource should be alerted on, and their removal should create a state of heightened awareness due to the vulnerability caused.

### Protecting virtual machines

For virtual machine based workloads, including scale sets and Kubernetes clusters, you need to plan for two of protection in addition to the management plane protection mentioned earlier.

First, you need to plan for backing up the data from the virtual machines, so that you can restore lost data in the event of attack. You also need to protect the backed up data itself from attack, using soft-delete controls. You can find instructions for configuring backups in the following product documentations:

- [Create and configure a Recovery Services vault](https://learn.microsoft.com/azure/backup/backup-create-recovery-services-vault)
- [Back up a virtual machine in Azure](https://learn.microsoft.com/azure/backup/quick-backup-vm-portal)
- [Configure backup for an Azure Kubernetes Service cluster](https://learn.microsoft.com/azure/backup/quick-backup-aks)
- [Backup and Recovery for AKS](https://learn.microsoft.com/azure/architecture/operator-guides/aks/aks-backup-and-recovery)
- [Backup and restore plan to protect against ransomware](https://learn.microsoft.com/azure/security/fundamentals/backup-plan-to-protect-against-ransomware)
- [Soft delete for Azure backup](https://learn.microsoft.com/azure/backup/backup-azure-security-feature-cloud?tabs=azure-portal)

Secondly, you need to plan for being able to restore a server to a new location when that underlying infrastructure is attacked in your region. You can find instructions for configuring replication on virtual machines in the following product documentation: [Set up disaster recovery for Azure VMs](https://learn.microsoft.com/azure/site-recovery/azure-to-azure-tutorial-enable-replication).

> [!IMPORTANT]
> When using Azure Site Recovery for virtual machines that are part of a virtual machine scale set, you can replicate the VM state. However, the replicated devices won't support scaling.

For some VM based workloads, such as Kubernetes clusters, the actual state of the servers is not able to replicated through Azure Site Recovery. Other solutions, like active/passive configuration, might be needed.

### Protecting data services

Data services are an informal collection of services that contain data essential for operations, but the resource itself is not not important. For example, there is little that differentials a storage account or a SQL database configured in the same way and hosting the same data from each other.

Data services are different from a virtual machines, which might have operating system configurations seperate from the applications running, and seperate from the configuration of the management plane.

As a result, these services often contain their own failover tools, such as a storage accounts ability to replicate to another region as part of Global Redundant Storage SKUs.

Each service has its own considerations for how to protect the data from attacks and to make the data available again in the event of an attack.

This table provides a reference for commonly used services, but you should investigate each service's product documentation to understand the options available.

| Service | Data Protection | Data Availability |
|---|---|---|
| Azure Files | [Backup Azure File shares](https://learn.microsoft.com/azure/backup/backup-azure-files?toc=%2Fazure%2Fstorage%2Ffiles%2Ftoc.json&tabs=backup-center) <P> [Prevent accidental deletion of Azure file shares](https://learn.microsoft.com/azure/storage/files/storage-files-prevent-file-share-deletion) | [Enable soft delete on Azure file shares](https://learn.microsoft.com/azure/storage/files/storage-files-enable-soft-delete?tabs=azure-portal) | 
| Azure Blob Storage | [Enable point-in-time restore on blob data](https://learn.microsoft.com/azure/storage/blobs/point-in-time-restore-manage?tabs=portal)  <p> [Store business-critical blob data with immutable storage](https://learn.microsoft.com/azure/storage/blobs/immutable-storage-overview) | [Data protection for Azure blob overview](https://learn.microsoft.com/azure/storage/blobs/data-protection-overview) <p> [Enable and manage soft delete for containers](https://learn.microsoft.com/azure/storage/blobs/soft-delete-container-enable?tabs=azure-portal)  <p> [Enable soft delete for blobs](https://learn.microsoft.com/azure/storage/blobs/soft-delete-blob-enable?tabs=azure-portal)| 
| Azure SQL database | [Automated backups in Azure SQL database](https://learn.microsoft.com/azure/azure-sql/database/automated-backups-overview?view=azuresql) | [Active geo-replication](https://learn.microsoft.com/azure/azure-sql/database/active-geo-replication-overview?view=azuresql-db) <p> [Failover groups for Azure SQL database](https://learn.microsoft.comazure/azure-sql/database/failover-group-sql-db?view=azuresql-db)|
| SQL Managed Instances | [Automated backups in Azure SQL Managed Instance](https://learn.microsoft.com/azure/azure-sql/managed-instance/automated-backups-overview?view=azuresql) | [Failover groups for Azure SQL managed instance](https://learn.microsoft.com/azure/azure-sql/managed-instance/failover-group-sql-mi?view=azuresql) | 
| SQL on Azure VMs | [Backup and restore for SQL server on Azure VMs](https://learn.microsoft.com/azure/azure-sql/virtual-machines/windows/backup-restore?view=azuresql) | [Failover cluster instances with SQL server on Azure Virtual Machines](https://learn.microsoft.com/azure/azure-sql/virtual-machines/windows/failover-cluster-instance-overview?view=azuresql) |
| Key vaults |  [Azure Key Vault backup and restore](https://learn.microsoft.com/azure/key-vault/general/backup?tabs=azure-cli)| [Enable soft-delete and purge protection for key vaults](https://learn.microsoft.com/azure/key-vault/general/key-vault-recovery?tabs=azure-portal#what-are-soft-delete-and-purge-protection) <p> [Azure Key Vault availability and redundancy](https://learn.microsoft.com/azure/key-vault/general/disaster-recovery-guidance) |

> [!WARNING]
> Some storage account recovery scenarios are not supported.  See [Non-supported storage recovery](https://learn.microsoft.com/azure/storage/blobs/point-in-time-restore-manage?tabs=portal) for more information.

### Protecting recovery infrastructure

In addition to protecting the resources that deliver on your workloads, you also need to plan to protect the resources that are a part of your protection plans and are used to restore functionality after a disruption. If attackers are able to target and disrupt your recovery infrastructure, then the whole environment is able to be compromised.

For data protected by Azure Backup, using [Soft delete for Azure backup](https://learn.microsoft.com/azure/backup/backup-azure-security-feature-cloud?tabs=azure-portal) allows you to recover backup data even if it has been deleted. In addition, [enhanced soft delete](https://learn.microsoft.com/azure/backup/quick-backup-azure-enable-enhanced-soft-delete?tabs=recovery-services-vault) will enforce the assignment of soft-delete and allow you to define a retention period.

> [!WARNING]
> This section is incomplete without protection of Azure Site Recovery

### Protecting configuration-based services

> [!WARNING]
> This section needs links to details.

Configuration-based services are Azure services that do not have data aside from their configuration in the management plane. These resources are generally infrastructure based and are foundational services that support workloads. Examples of these services include virtual networks, load balancers, network gateways, and application gateways.

Because there is no "operating data" to protect, and most of these services are stateless, the best option for protecting these services is to have infrastructure as code deployment templates, like Bicep, that can restore the state of these services after a destructive event.

So long as a resource configured the same way can be deployed, services can continue to operate. So rather than try to backup and maintain copies of these resources, you can leverage the programatic deployment to recover from an attack or disaster.

### Protecting platform automation and DevOps tooling

If you are leveraging programatic deployments or other automation, these resources need to be secured as well. The article on [Securing DevOps CI/CD pipelines](https://learn.microsoft.com/azure/cloud-adoption-framework/secure/best-practices/secure-devops) gives examples for how source code can be protected as part of the process.

However, you should also plan to protect the code itself. This can vary on the source control tools being used. For example, GitHub has instructions for [Backing up a repository](https://docs.github.com/en/repositories/archiving-a-github-repository/backing-up-a-repository) that provides instructions for backing up your source code repositories.

You should review your specific services to determine how best to protect your source code and pipelines from malicious destruction.

For components such as build agents hosted on virtual machines, you can use the appropriate VM based protection plan to make sure your agents are available when needed.

## Configure Detection

> [!WARNING]
> This section is a STUB. It needs details for detecting destructive cyber attacks using Sentinel.

Now that resources are protected...

## Incident Response

You need to have a well defined incident response plan for destructive cyber attacks at the ready for when incidents occur. During an incident is no time to be figuring out how to restore services.

Applications and shared services should all have response and recovery plans that include playbooks for restoring VMs, data, configuration services, and automation/DevOps services. Each application or service area should have its definition, and dependencies between them should be well defined.

Your playbooks should include your processes for the following scenarios:

- [Fail over Azure VMs to a secondary region](https://learn.microsoft.com/azure/site-recovery/azure-to-azure-tutorial-failover-failback)
- [How to restore Azure VM data in Azure portal](https://learn.microsoft.com/azure/backup/backup-azure-arm-restore-vms)
- [Restore files to a virtual machine in Azure](https://learn.microsoft.com/azure/backup/tutorial-restore-files)
- [Recover soft deleted data and recovery points using enhanced soft delete in Azure Backup](https://learn.microsoft.com/azure/backup/backup-azure-enhanced-soft-delete-tutorial?tabs=recovery-services-vault)
- [Restore the state of Kubernetes clusters after a disaster](azure/aks/hybrid/restore-aks-cluster)
- [Recover a deleted storage account](https://learn.microsoft.coms/azure/storage/common/storage-account-recover)
- [Recover a soft-deleted key vault](https://learn.microsoft.com/azure/key-vault/general/key-vault-recovery?tabs=azure-portal#list-recover-or-purge-a-soft-deleted-key-vault)
- [Recover soft-deleted secrets, keys, and certificates from a key vault](https://learn.microsoft.com/azure/key-vault/general/key-vault-recovery?tabs=azure-portal#list-recover-or-purge-soft-deleted-secrets-keys-and-certificates)
- [Disaster recovery guidance - Azure SQL Database](https://learn.microsoft.com/azure/azure-sql/database/disaster-recovery-guidance?view=azuresql-db)

As well as restoration process for any other resources that make up this service.

In addition, these response plans should be tested periodically.

> [!WARNING]
> This section is a STUB. We should identify specific guidance for testing to continue to flesh it out.