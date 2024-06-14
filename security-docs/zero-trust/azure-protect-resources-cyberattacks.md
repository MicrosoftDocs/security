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
| Assume breach | Minimize blast radius and segment access. Verify end-to-end encryption and use analytics to get visibility, **drive threat detection, and improve defenses**. <br><br> Improve defenses with resource locks, backups and disaster recovery for virtual machines, protection and availability data services, and protection of your recovery infrastructure, configuration-based services, and platform automation and DevOps tooling. <be><br> For threat detection, use Microsoft Sentinel and advanced multistage detection and prepare your incident response plans for Azure resources. |

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
