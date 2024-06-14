---
title: How do I protect my Azure resources from destructive cyberattacks?
description: Learn how to secure an Azure Virtual Desktop deployment with Zero Trust principles. 
ms.date: 02/11/2024
ms.service: security
author: rudneir2
ms.author: ruolivei
ms.topic: conceptual
ms.collection: 
  - msftsolution-azurepaas
  - msftsolution-scenario
  - zerotrust-solution
  - zerotrust-azure
---

<!---

Writers notes:

For updates to product names, please also update the appropriate figures.

To update figures that are not screen shots, your options are:

- Locate the source Visio file in internal storage.
- Use the published Visio file in the Microsoft Download Center (see the "Technical publications" section of this article).
- For figures that are published in Scalable Vector Graphics (SVG) format, save the SVG file from the article web page, insert into Visio, modify, and then save it as a new version of the SVG file.

For any updates to figures, please update the corresponding posters as needed (see the "Technical publications" section of this article) and republish the Visio and PDF files in the Microsoft Download Center.

For new articles in this content set, please:

- Add cross-links in the "Next Steps" section FROM all the other articles in this content set TO the new article.
- Add a link to the Zero Trust Guidance Center page (index.yml).
- Update the "Content architecture" figure in the apply-zero-trust-azure-services-overview.md article as needed.

--->

# Protect your Azure resources from destructive cyberattacks

This article provides steps to apply the [principles of Zero Trust](zero-trust-overview.md) to protect your Azure resources from destructive cyberattacks in the following ways:

| Zero Trust principle | Definition |
| --- | --- |
| Verify explicitly |Always authenticate and authorize based on all available data points. |
| Use least privileged access |  Limit user access with Just-In-Time and Just-Enough-Access (JIT/JEA), risk-based adaptive policies, and data protection. |
| Assume breach | Minimize blast radius and segment access. Verify end-to-end encryption and use analytics to get visibility, **drive threat detection, and improve defenses**. <br><br> Improve defenses with resource locks, backups and disaster recovery for virtual machines, protection and availability data services, and protection of your recovery infrastructure, configuration-based services, and platform automation and DevOps tooling. <br><br> For threat detection, use Microsoft Sentinel and advanced multistage detection and prepare your incident response plans for Azure resources. |

## Reference architecture

The following figure shows the reference architecture for this Zero Trust guidance with groupings for each category of protection.

:::image type="content" source="media/cyberattacks/protect-cyberattacks-reference-architecture.svg" alt-text="Diagram of the reference architecture for protecting your Azure resources from cyberattacks." lightbox="media/cyberattacks/protect-cyberattacks-reference-architecture.svg":::

This Azure environment includes:

| Component | Description |
| --- | --- |
| A | Virtual machines and their files |
| B | Data services and their data |
| C | Recovery infrastructure including files and templates and automation scripts |
| D | Configuration-based services |
| E | Platform automation and DevOps tooling |

Tasks for protecting each type of asset are described in detail in Step 1.

## What’s in this article?

This article walks through the steps to apply the principles of Zero Trust across the reference architecture.

| Step | Task |
| --- | --- |
| 1 | Configure protection against cyberattacks. |
| 2 | Configure detection of cyberattacks. |
| 3 | Prepare your incident response plans. |

## Step 1: Configure protection against cyberattacks

Many organizations implement backup and disaster recovery solutions for their Azure virtual machines as part of a migration effort. For example, you might use Azure native solutions or opt to use your own third-party solutions for your cloud ecosystem.

While protecting virtual machines and their apps and data is important, it's also critical to expand the scope of protection beyond virtual machines. This section provides a breakdown of considerations and recommendations for how to protect different types of resources in Azure from a destructive cyberattack.

In addition to the service-specific considerations, you should consider using Resource Locks to prevent deletion of services by protecting their management plane. You can also use resource locks to render resources read-only. Resource locks work with controlled access to reduce the chance of Azure resources being destroyed in a cyberattack by preventing their modification or destruction.

To prevent resource locks from producing unexpected results, you should review the considerations before applying your locks to make sure you're applying the locks to the appropriate resources in a way that still allows them to operate.

Because of these considerations, you should prioritize locking resources that, if changed or deleted, would cause the most disruption. For example, locking a virtual network instead of a whole resource group can prevent the lock from being too restrictive on other resources with the resource group.

Locks may also have some considerations for the Recovery Time Objectives for workloads being failed over. Your disaster recovery plan should take the locks into account and you should have a tested procedure for the removal of locks in a controlled manner. You will need to train your admins and SecOps staff on how to manage locks as part of both day-to-day operations and emergency scenarios.

Administrators with access to remove the locks should be limited and should involve JIT access such as that provided with Microsoft Entra Privileged Identity Management. Access to change locks on resources are controlled with the Microsoft.Authorization/locks/* scope and shouldn't be granted as part of standing access.

The removal of resource locks from a resource should be alerted on, and their removal should create a state of heightened awareness due to the vulnerability caused.

### A. Protecting virtual machines

>> Is app installation and configuration recovery a consideration? Is this part of disaster recovery replication?

For virtual machine-based workloads, including scale sets and Kubernetes clusters, you need to plan for two layers of protection in addition to the use of resource locks in the management plane.

First, you need to plan for backing up the data from the virtual machines so that you can restore lost data if an attack occurs, which includes the Azure Kubernetes Service (AKS). You also need to protect the backed-up data itself from attack using soft-delete controls. For information on configuring backups, see:

•	Create and configure a Recovery Services vault
•	Back up a virtual machine in Azure
•	Configure backup for an Azure Kubernetes Service cluster
•	Backup and Recovery for AKS
•	Backup and restore plan to protect against ransomware
•	Soft delete for Azure backup

Secondly, you need to plan for being able to restore a server to a new location when the underlying infrastructure in your region is attacked. For information on configuring replication on virtual machines, see Set up disaster recovery for Azure VMs.  This includes configuration of applications and settings to the resources used during failover.

>> Important
When using Azure Site Recovery for virtual machines that are part of a virtual machine scale set, you can replicate the virtual machine state. However, the replicated devices won't support scaling.

For some virtual machine-based workloads, such as Kubernetes clusters, the actual state of the servers can’t be replicated through Azure Site Recovery. You might need other solutions such as active/passive configuration.

### B. Protecting data services

Data services are an informal collection of services that contain data essential for operations, but the resource itself isn't as important. For example, there's little difference between two storage accounts configured in the same way and hosting the same data.

Data services are different from virtual machines, which might have operating system configurations separate from the applications running and separate from the configuration of the management plane. As a result, these services:

•	Often contain their own failover tools, such as a storage account's ability to replicate to another region as part of geo-redundant storage (GRS) tiers.
•	Have their own considerations for how to protect data from attacks and to make the data available again in the event of an attack.

The following table provides data protection and availability references for commonly-used services, but you should investigate each service's product documentation to understand the options available.

Service	Data protection	Data availability
Azure Files	Backup Azure File shares
Prevent accidental deletion of Azure file shares
Enable soft delete on Azure file shares

Azure Blob Storage	Enable point-in-time restore on blob data
Store business-critical blob data with immutable storage
Data protection for Azure blob overview
Enable and manage soft delete for containers
Enable soft delete for blobs

Azure SQL database	Automated backups in Azure SQL database
Active geo-replication
Failover groups for Azure SQL database

SQL Managed Instances	Automated backups in Azure SQL Managed Instance
Failover groups for Azure SQL managed instance

SQL on Azure VMs	Backup and restore for SQL server on Azure VMs
Failover cluster instances with SQL server on Azure Virtual Machines

Key vaults	Azure Key Vault backup and restore
Enable soft-delete and purge protection for key vaults
Azure Key Vault availability and redundancy


>> Warning Some storage account recovery scenarios are not supported. For more information, see Non-supported storage recovery.

### C. Protecting recovery infrastructure

In addition to protecting the resources on your workloads, you also need to protect the resources that you use to restore functionality after a disruption, such as recovery procedures documentation and configuration scripts and templates. If attackers can target and disrupt your recovery infrastructure, your entire environment can be compromised leading to substantial delays in recovering from the attack and leaving your organization vulnerable to ransomware scenarios.

For data protected by Azure Backup, using soft delete for Azure backup allows you to recover backup data even if deleted. In addition, enhanced soft delete enforces the assignment of soft-delete and allows you to define a retention period. 

To further enhance security, implement multi-user authorization (MUA) for critical operations, which requires that two or more users approve critical operations before they're executed. This adds an extra layer of security by ensuring that no single user, and therefore an attacker with only one user account, can compromise the backup integrity. Enable and configure MUA to safeguard your backup policies against unauthorized changes and deletions.

You can protect Azure Site Recovery with resource locks and JEA/JIT access to prevent unauthorized access and detection when resources are at risk.

When replicating virtual machines with Azure Site Recovery that have been encrypted with Azure Disk Encryption (ADE) or Customer Managed Keys (CMK), ensure that the encryption keys are stored in Azure Key Vault in the target region. Storing the keys in the target region facilitates seamless access to the keys after failover and maintains data security continuity. To protect the Azure Key Vault from destructive cyberattacks, enable advanced threat protection features such as soft-delete and purge protection.

For step-by-step replication guidance for encrypted VMs, see the following:

•	Replication of ADE-protected VMs
•	Replication of VMs with CMK disks

### D. Protecting configuration-based services

Configuration-based services are Azure services that don't have data aside from their configuration in the management plane. These resources are generally infrastructure-based and are foundational services that support workloads. Examples include virtual networks, load balancers, network gateways, and application gateways.

Because these services are stateless, there's no operating data to protect. The best option for protecting these services is to have infrastructure as code (IaC) deployment templates, like Bicep, that can restore the state of these services after a destructive event. You can also use scripts for deployments, but IaC deployments work better to restore functionality in an existing environment where only a few services are impacted.

As long as a resource configured the same way can be deployed, services can continue to operate. Rather than try to backup and maintain copies of these resources, you can use the programmatic deployment to recover from an attack.

For more information about using IaC, see Recommendations for using infrastructure as code.

### E. Protecting platform automation and DevOps tooling

If you're using programmatic deployments or other types of automation, platform automation and DevOps tooling resources need to be secured as well. For examples to protect your deployment infrastructure, see Securing DevOps CI/CD pipelines and Recommendations for securing a development lifecycle.

However, you should also plan to protect the code itself, which varies based on the source control tools you are using. For example, GitHub has instructions for Backing up a repository for your source code repositories.

You should also review your specific services to determine how best to protect your source code and pipelines from attack and destruction.

For components such as build agents hosted on virtual machines, you can use the appropriate virtual machine-based protection plan to make sure your agents are available when needed.

## Step 2: Configure detection of cyberattacks

For detection of attacks on your Azure infrastructure, start with [Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-cloud-introduction), a cloud-native application protection platform (CNAPP) that is made up of security measures and practices that are designed to protect cloud-based applications from various cyber threats and vulnerabilities. 

Defender for Cloud, in conjunction with additional plans for Azure components, collects signals from Azure components and provides specific protections for servers, containers, storage, databases, and other workloads. 

The following diagram shows the flow of security event information from Azure services through Defender for Cloud and [Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/overview?tabs=azure-portal).

:::image type="content" source="media/cyberattacks/cyberattack-detection-information-flow.svg" alt-text="Diagram of the flow of security event information from Azure services through Defender for Cloud and Microsoft Sentinel." lightbox="media/cyberattacks/cyberattack-detection-information-flow.svg":::

In the figure:

- Azure services send signals to Microsoft Defender for Cloud.
- Microsoft Defender for Cloud, with additional plans such as Defender for Servers, analyzes the signals for enhanced threat detection and sends security information and event management (SIEM) data to Microsoft Sentinel.
- Microsoft Sentinel uses the SIEM data for cyberattack detection, investigation, response, and proactive hunting.

After you have better protected your Azure resources with the recommendations in Step 1 of this article, you need to have a plan for detecting destructive cyberattacks using Microsoft Sentinel. A starting point is to use [advanced multistage attack detection in Microsoft Sentinel](https://review.learn.microsoft.com/en-us/azure/sentinel/fusion). This allows you to build detections for specific scenarios such as data destruction, denial of service, malicious administrative activity, and many more.

As part of preparing your workloads for response, you need to:

- Identify how you will determine if a resource is under attack.
- Determine how you can capture and raise an incident as a result.


## Step 3: Prepare your incident response plans

You need to have well-defined and ready-to-implement incident response plans for destructive cyberattacks before incidents occur. During an incident, you will have no time to determine how to thwart attacks in progress or restore damaged data and services.

Azure applications and shared services should all have response and recovery plans that include playbooks for restoring virtual machines, data services, configuration services, and automation/DevOps services. Each application or service area should have its definitions and the well-defined dependencies.

Your playbooks should:

- Include your processes for the following scenarios:

  - [Fail over Azure VMs to a secondary region](https://review.learn.microsoft.com/en-us/azure/site-recovery/azure-to-azure-tutorial-failover-failback)
  - [How to restore Azure VM data in Azure portal](https://review.learn.microsoft.com/en-us/azure/backup/backup-azure-arm-restore-vms)
  - [Restore files to a virtual machine in Azure](https://review.learn.microsoft.com/en-us/azure/backup/tutorial-restore-files)
  - [Recover soft deleted data and recovery points using enhanced soft delete in Azure Backup](https://review.learn.microsoft.com/en-us/azure/backup/backup-azure-enhanced-soft-delete-tutorial?tabs=recovery-services-vault)
  - [Restore the state of Kubernetes clusters after a disaster](https://review.learn.microsoft.com/en-us/azure/aks/hybrid/restore-aks-cluster)
  - [Recover a deleted storage account](https://review.learn.microsoft.com/en-us/azure/storage/common/storage-account-recover)
  - [Recover a soft-deleted key vault](https://review.learn.microsoft.com/en-us/azure/key-vault/general/key-vault-recovery?tabs=azure-portal#list-recover-or-purge-a-soft-deleted-key-vault)
  - [Recover soft-deleted secrets, keys, and certificates from a key vault](https://review.learn.microsoft.com/en-us/azure/key-vault/general/key-vault-recovery?tabs=azure-portal#list-recover-or-purge-soft-deleted-secrets-keys-and-certificates)
  - [Disaster recovery guidance - Azure SQL Database](https://review.learn.microsoft.com/en-us/azure/azure-sql/database/disaster-recovery-guidance)

- Include the restoration process for any other resources that make up this service.
- Be tested periodically as part of your SecOps maintenance processes.

## Recommended training

>> ADD

## Next Steps

Continue to implement your [security breach prevention and recovery infrastructure](./adopt/prevent-reduce-business-damage-breach-infrastructure.md).

## References

Refer to these links to learn about the various services and technologies mentioned in this article.

- [Resource Locks](/azure/azure-resource-manager/management)
- [Microsoft Entra Privileged Identity Management](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-configure)
- [Soft delete for Azure backup](https://learn.microsoft.com/en-us/azure/backup/backup-azure-security-feature-cloud?tabs=azure-portal)
- [Multi-user authorization (MUA)](https://learn.microsoft.com/en-us/azure/backup/multi-user-authorization-concept?tabs=recovery-services-vault)
- [Bicep](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/)
- [Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-cloud-introduction)
- [Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/overview?tabs=azure-portal)
