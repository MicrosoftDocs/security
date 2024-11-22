---
title: How do I apply Zero Trust principles to Azure networking?
description: An overview of how to apply Zero Trust principles to Azure networking infrastructure.
ms.date: 05/29/2024
ms.service: security
author: duongau
ms.author: duau
ms.reviewer: adtork, maroja, maalgeba
ms.topic: conceptual
ms.collection: 
  - msftsolution-azureiaas
  - msftsolution-scenario
  - zerotrust-solution
  - zerotrust-azure
---

<!---

Writers notes:

For updates to product names, please also update the appropriate figures.

To update figures that are not screen shots, your options are:

- Locate the source Visio file in internal storage (see the Illustrations-locations.docs file).
- Use the published Visio file in the Microsoft Download Center (see the "Technical publications" section of this article).
- For figures that are published in Scalable Vector Graphics (SVG) format, save the SVG file from the article web page, insert into Visio, modify, and then save it as a new version of the SVG file.

For any updates to figures, please update the corresponding posters as needed (see the "Technical publications" section of this article) and republish the Visio and PDF files in the Microsoft Download Center.

For new articles in this content set, please:

- Add cross-links in the "Next Steps" section FROM all the other articles in this content set TO the new article.
- Add a link to the Zero Trust Guidance Center page (index.yml).
- Update the "Content architecture" figure in the apply-zero-trust-azure-services-overview.md article as needed.

--->

# Overview – Apply Zero Trust principles to Azure networking

This series of articles help you apply the [principles of Zero Trust](zero-trust-overview.md) to your networking infrastructure in Microsoft Azure based on a multi-disciplinary approach. Zero Trust is a security strategy. It isn't a product or a service, but an approach in designing and implementing the following set of security principles:

- Verify explicitly
- Use least privileged access
- Assume breach

Implementing the Zero Trust mindset to "assume breach, never trust, always verify" requires changes to cloud networking infrastructure, deployment strategy, and implementation.

The following articles show you how to apply Zero Trust approach to networking for commonly deployed Azure infrastructure services:

- [Encryption](azure-networking-encryption.md)
- [Segmentation](azure-networking-segmentation.md)
- [Gain visibility into your network traffic](azure-networking-visibility.md)
- [Discontinue legacy network security technology](azure-networking-legacy.md)

> [!IMPORTANT]
> This Zero Trust guidance describes how to use and configure several security solutions and features available on Azure for a reference architecture. Several other resources also provide security guidance for these solutions and features, including:
> - [Microsoft Cloud Security Benchmark](/security/benchmark/azure/introduction)
> - [Microsoft Cloud Security Baseline](/security/benchmark/azure/security-baselines-overview)

To describe how to apply a Zero Trust approach, this guidance targets a common pattern used in production by many organizations: a virtual-machine-based application hosted in a VNet (and IaaS application). This is a common pattern for organizations migrating on-premises applications to Azure, which is sometimes referred to as "lift-and-shift."

## Threat Protection with Microsoft Defender for Cloud

For the **Assume breach** Zero Trust principle for Azure networking, Microsoft Defender for Cloud is an extended detection and response (XDR) solution that automatically collects, correlates, and analyzes signal, threat, and alert data from across your environment. Defender for Cloud is intended to be used together with Microsoft Defender XDR to provide a greater breadth of correlated protection of your environment, as shown in the following diagram.

:::image type="content" source="media/azure-infra-overview/azure-infra-overview-threat-protection.svg" alt-text="Diagram of the logical architecture of Microsoft Defender for Cloud and Microsoft Defender XDR that provides threat protection for Azure networking." lightbox="media/azure-infra-overview/azure-infra-overview-threat-protection.svg":::

In the diagram:

- Defender for Cloud is enabled for a management group that includes multiple Azure subscriptions.
- Microsoft Defender XDR is enabled for Microsoft 365 apps and data, SaaS apps that are integrated with Microsoft Entra ID, and on-premises Active Directory Domain Services (AD DS) servers.

For more information about configuring management groups and enabling Defender for Cloud, see:

- [Organize subscriptions into management groups and assign roles to users](/azure/defender-for-cloud/management-groups-roles)
- [Enable Defender for Cloud on all subscriptions in a management group](/azure/defender-for-cloud/onboard-management-group)

## Additional resources

See these additional articles for applying Zero Trust principles to Azure IaaS:

- For Azure IaaS:
  - [Azure storage](azure-infrastructure-storage.md)
  - [Virtual machines](azure-infrastructure-virtual-machines.md)
  - [Spoke virtual networks](azure-infrastructure-iaas.md)
  - [Hub virtual networks](azure-infrastructure-networking.md)
  - [Spoke virtual networks with Azure PaaS services](azure-infrastructure-paas.md)
- [Azure Virtual Desktop](azure-infrastructure-avd.md)
- [Azure Virtual WAN](azure-virtual-wan.md)
- [IaaS applications in Amazon Web Services](secure-iaas-apps.md)
- [Microsoft Sentinel and Microsoft Defender XDR](/security/operations/siem-xdr-overview)
