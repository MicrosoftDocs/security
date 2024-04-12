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

Here is some intro stuff.  We want to talk about what the attack is, and refer them back to the [Implement security breach prevention and recovery infrastructure](./adopt/prevent-reduce-business-damage-breach-infrastructure.md) for over all adoption guidance.

We want to reiterate about our audience here - technical implementers as part of the adoption - and set expectations about what we want to do - which is to guide implementers through setting up protection, setting up detection, and reacting.

## Configuring protection

Many organizations implement backup and disaster recover solutions for their virtual machines as part of a migration effort, either using Azure native solutions or continuing to bring their own third party solutions to their ecosystem.

While this is important, it is also critical to expand the scope of protection beyond virtual machines.  This section gives a break down of considerations and recommendations for how to protect different types of resources in Azure from a destructive cyber attack.

In addition to the service specific considerations below, all critical services in Azure should use [Resource Locks](azure/azure-resource-manager/management/lock-resources?tabs=json) to prevent deletion by protecting their management plane.  Resource locks can also be used to render resources read-only.  This works with controlled access to reduce the chance of Azure resources being destroyed in a cyber attack by preventing the modification.

Administrators with access to remove the locks should be limited, and should involve just-in-time access.

The removal of these resource locks from a resource should be alerted on, and their removal should create a state of heightened awareness due to the vulnerability caused.

### Protecting virtual machines

For virtual machine based workloads, including scale sets and Kubernetes clusters, you need to plan for two of protection in addition to the management plane protection mentioned earlier.

First, you need to plan for backing up the data from the virtual machines, so that you can restore lost data in the event of attack.  You also need to protect the backed up data itself from attack, using soft-delete controls.  You can find instructions for configuring this in the following product documentations:

- [Create and configure a Recovery Services vault](azure/backup/backup-create-recovery-services-vault)
- [Back up a virtual machine in Azure](azure/backup/quick-backup-vm-portal)
- [Configure backup for an AKS cluster](azure/backup/quick-backup-aks)
- [Backup and restore plan to protect against ransomware](azure/security/fundamentals/backup-plan-to-protect-against-ransomware)
- [Soft delete for Azure backup](azure/backup/backup-azure-security-feature-cloud?tabs=azure-portal)

Secondly, you need to plan for being able to restore a server to a new location in the event that underlying infrastructure is attacked in your region.  You can find instructions for configuring this on virtual machines in the following product documentation: [Set up disaster recovery for Azure VMs](azure/site-recovery/azure-to-azure-tutorial-enable-replication).

> [!IMPORTANT]
> When using Azure Site Recovery for virtual machines that are part of a virtual machine scale set, you can replicate the VM state.  However, the replicated devices won't support scaling.

For some VM based workloads, such as Kubernetes clusters, the actual state of the servers is not able to replicated through Azure Site Recovery.  For these, additional considerations like active/passive configuration, might be needed.

### Protecting data services

Data services are an informal collection of services that contain data essential for operations, but the resource themselves are not important.  For example, there is little that differentials a storage account or a SQL database configured in the same way and hosting the same data from each other.

This is different from a virtual machine, which might have operating system configurations seperate from the applications running, and seperate from the configuration of the management plane.

As a result, these services often contain their own failover tools, such as a storage accounts ability to replicate to another region as part of Global Redundant Storage skus.

Each service has its own considerations for how to protect the data from attacks and to make the data available again in the event of an attack.

This table provides a reference for commonly used services, but you should investigate each service's product documentation to understand the options available.

> [!WARNING]
> This table is a STUB and needs to be updated with specific how to links.

| Service | Data Protection | Data Availability |
|---|---|---|
| Storage accounts | *TBD*  | *TBD* |
| SQL databases | *TBD* | *TBD* |
| Key vaults | [Enable soft-delete and purge protection for key vaults](azure/key-vault/general/key-vault-recovery?tabs=azure-portal#what-are-soft-delete-and-purge-protection) | *TBD* |

### Protecting recovery infrastructure

In addition to protecting the resources that deliver on your workloads, you also need to plan to protect the resources that are a part of your protection plans and are used to restore functionality after a disruption.  If attackers are able to target and disrupt your recovery infrastructure, then the whole environment is able to be compromised.

For data protected by Azure Backup, using [Soft delete for Azure backup](azure/backup/backup-azure-security-feature-cloud?tabs=azure-portal) allows you to recover backup data even if it has been deleted.  In addition, [enhanced soft delete](azure/backup/quick-backup-azure-enable-enhanced-soft-delete?tabs=recovery-services-vault) will enforce the assignment of soft-delete and allow you to define a retention period.

> [!WARNING]
> This section is incomplete without protection of Azure Site Recovery

### Protecting configuration-based services

> [!WARNING]
> This section needs links to details.

Configuration-based services are Azure services that do not have data aside from their configuration in the management plane.  These resources are generally infrastructure based and are foundational services that support workloads.  Examples of these services include virtual networks, load balancers, network gateways, and application gateways.

Because there is no "operating data" to protect, and most of these services are stateless, the best option for protecting these services is to have infrastructure as code deployment templates, like Bicep, that can restore the state of these services after a destructive event.

So long as a resource configured the same way can be deployed, services can continue to operate.  So rather than try to backup and maintain copies of these resources, you can leverage the programatic deployment to recover from an attack or disaster.

### Protecting platform automation and DevOps tooling

If you are leveraging programatic deployments or other automation, these resources need to be secured as well.  The article on [Securing DevOps CI/CD pipelines](azure/cloud-adoption-framework/secure/best-practices/secure-devops) gives examples for how source code can be protected as part of the process.

However, you should also plan to protect the code itself.  This can vary on the source control tools being used.  For example, GitHub has instructions for [Backing up a repository](https://docs.github.com/en/repositories/archiving-a-github-repository/backing-up-a-repository) that provides instructions for backing up your source code repositories.

You should review your specific services to determine how best to protect your source code and pipelines from malicious destruction.

For components such as build agents hosted on virtual machines, you can use the appropriate VM based protection plan to make sure your agents are available when needed.

## Configure Detection

> [!WARNING]
> This section is a STUB.  It needs details for detecting destructive cyber attacks using Sentinel.

Now that resources are protected...

## Incident Response

You need to have a well defined incident response plan for destructive cyber attacks at the ready for when incidents occur.  During an incident is no time to be figuring out how to restore services.

Applications and shared services should all have response and recovery plans that include playbooks for restoring VMs, data, configuration services, and automation/DevOps services.  Each application or service area should have its definition, and dependencies between them should be well defined.

Your playbooks should include your processes for the following scenarios:

- [Fail over Azure VMs to a secondary region](azure/site-recovery/azure-to-azure-tutorial-failover-failback)
- [How to restore Azure VM data in Azure portal](azure/backup/backup-azure-arm-restore-vms)
- [Restore files to a virtual machine in Azure](azure/backup/tutorial-restore-files)
- [Recover soft deleted data and recovery points using enhanced soft delete in Azure Backup](azure/backup/backup-azure-enhanced-soft-delete-tutorial?tabs=recovery-services-vault)
- [Restore the state of Kubernetes clusters after a disaster](azure/aks/hybrid/restore-aks-cluster)
- [Recover a soft-deleted key vault](azure/key-vault/general/key-vault-recovery?tabs=azure-portal#list-recover-or-purge-a-soft-deleted-key-vault)
- [Recover soft-deleted secrets, keys, and certificates from a key vault](azure/key-vault/general/key-vault-recovery?tabs=azure-portal#list-recover-or-purge-soft-deleted-secrets-keys-and-certificates)

As well as restoration process for any other resources that make up this service.

In addition, these response plans should be tested periodically.

> [!WARNING]
> This section is a STUB. We should identify specific guidance for testing to continue to flesh it out.