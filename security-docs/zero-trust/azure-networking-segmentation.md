---
title: Apply Zero Trust principles to segmenting Azure-based network communication
description: Learn how to apply Zero Trust principles to segmenting Azure-based network communication.
ms.date: 05/20/2024
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

# Apply Zero Trust principles to segmenting Azure-based network communication

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

This article provides guidance to applying the [principles of Zero Trust](zero-trust-overview.md) for segmenting networks in Azure environments. Here are the Zero Trust principles. 

| Zero Trust principle | Definition |
| --- | --- |
| Verify explicitly | Always authenticate and authorize based on all available data points. |
| Use least privileged access | Limit user access with Just-In-Time and Just-Enough-Access (JIT/JEA), risk-based adaptive policies, and data protection. |
| Assume breach | Minimize blast radius and segment access. Verify end-to-end encryption and use analytics to get visibility, drive threat detection, and improve defenses. |

This article is a part of a series of articles that demonstrate how to apply the principles of Zero Trust for Azure networking.

As organizations grow from small businesses into large enterprises, they often need to move from a single Azure subscription into multiple subscriptions to separate resources for each department. It’s important to carefully plan the segmentation of your network to create logical boundaries and isolation between environments. 

Each environment, typically reflecting a separate department of your organization, should have its own access permissions and policies for specific workloads. For example, users from your internal software developer subscription shouldn't have access to managing and deploying network resources in the connectivity subscription. However, these environments still need network connectivity to achieve the required functionality to basic services, such as DNS, hybrid connectivity, and being able to reach other resources across different [Azure virtual networks (VNets)](/azure/virtual-network/virtual-networks-overview). 

The segmentation of your Azure infrastructure provides not only isolation but can also create security boundaries that prevent an attacker from moving across environments and inflicting additional damage (the Assume breach Zero Trust principle).

## Reference architecture

The following diagram shows the reference architecture for this Zero Trust guidance for encrypted communication between users and admins on-premises or on the internet and components in the Azure environment for the steps described in this article.

:::image type="content" source="media/azure-networking/azure-networking-segmentation.svg" alt-text="The reference architecture for Azure networking components with segmentation and Zero Trust principles applied." lightbox="media/azure-networking/azure-networking-segmentation.svg":::
 
In the diagram, the numbers correspond to the steps in the following sections.

## What's in this article?

Zero Trust principles are applied across the reference architecture, from users and admins on the internet or your on-premises network to and within the Azure cloud. The following table describes the recommendations for ensuring the encryption of network traffic across this architecture.

| Step | Task | Zero Trust principle(s) applied |
| --- | --- | --- |
| 1 | Implement network layer encryption. | Verify explicitly <br> Use least privileged access <br> Assume breach |
| 2 | Secure and verify communication from an on-premises network to Azure VNets. | Verify explicitly <br> Assume breach |
| 3 | Secure and verify communication within and across Azure VNets. | Assume breach |
| 4 | Implement application layer encryption. | Verify explicitly <br> Assume breach |
| 5 | Use Azure Bastion to protect Azure virtual machines. | Assume breach |

## Step 1: 


## Step 2: 


## Step 3: 


## Step 4: 


## Step 5: 



## Recommended training

- [Connect your on-premises network to Azure with VPN Gateway](/training/modules/connect-on-premises-network-with-vpn-gateway/)
- [Connect your on-premises network to the Microsoft global network by using ExpressRoute](/training/modules/connect-on-premises-network-with-expressroute/)
- [Introduction to Azure Front Door](/training/modules/intro-to-azure-front-door/)
- [Configure Azure Application Gateway](/training/modules/configure-azure-application-gateway/)
- [Introduction to Azure Bastion](/training/modules/intro-to-azure-bastion/)

## Next Steps

For additional information about applying Zero Trust to Azure networking, see:

- [Apply Zero Trust principles to encrypting Azure-based network communication](azure-networking-encryption.md)
- [Secure networks with Zero Trust](./deploy/networks.md)
- [Spoke virtual networks in Azure](azure-infrastructure-iaas.md)
- [Hub virtual networks in Azure](azure-infrastructure-paas.md)
- [Spoke virtual networks with Azure PaaS services](azure-infrastructure-paas.md)
- [Azure Virtual WAN](azure-virtual-wan.md)

## References

Refer to these links to learn about the various services and technologies mentioned in this article.


