---
title: Apply Zero Trust principles to Azure Virtual Desktop
description: Learn how to secure an Azure Virtual Desktop deployment with Zero Trust.   
ms.date: 02/03/2023
ms.service: security
author: v-joedavies
ms.author: v-joedavies
ms.topic: conceptual
ms.collection: 
  - msftsolution-azurepaas
  - msftsolution-scenario
  - zerotrust-solution
---

# Apply Zero Trust principles to a spoke virtual network in Azure

This article will help you apply the principles of Zero Trust to an Azure Virtual Desktop deployment in the following ways:

| Zero Trust principle | Met by |
| --- | --- |
| Verify explicitly |  |
| Use least privileged access | |
| Assume breach |  |

This article is a part of a series of articles that demonstrate how to apply the principles of Zero Trust across an environment in Azure that includes Azure Virtual Desktop. For more information, see the [Apply Zero Trust principles to Azure infrastructure overview](azure-infrastructure-overview.md).

## Reference architecture

The following diagram shows a common reference architecture for Azure Virtual Desktop.

:::image type="content" source="media/avd/placeholder.png" alt-text="Diagram of the reference architecture for Azure Virtual Desktop." lightbox="media/avd/placeholder.png":::

In the diagram:

- 


The following diagram shows the components of a resource group for Azure Virtual Desktop in an Azure subscription.

:::image type="content" source="media/avd/placeholder.png" alt-text="Diagram of the components of a resource group for Azure Virtual Desktop." lightbox="media/avd/placeholder.png":::

In the diagram, all the components of Azure Virtual Desktop are contained in a dedicated resource group:

- 
- 
- 
- 
- 

## What's in this article

Zero Trust principles are applied across the architecture, from the tenant and directory level down to the assignment of virtual machines to application security groups. The following table describes the recommendations for securing this architecture.

| Step | Task |
| --- | --- |
| 1 |  |
| 1 |  |
| 1 |  |
| 1 |  |
| 1 |  |
| 1 |  |
| 1 |  |
| 1 |  |

## Step 1. title


## Recommended training

- [Secure your Azure resources with Azure role-based access control (Azure RBAC)](/training/modules/secure-azure-resources-with-rbac/)
- [Configure and manage Azure Monitor](/training/modules/azure-monitor/)
- [Configure network security groups](/training/modules/configure-network-security-groups/)
- [Design and implement network security](/training/modules/design-implement-network-security-monitoring/)
- [Secure access to your applications by using Azure identity services](/training/modules/secure-access-azure-identity-services/)

For more training on security in Azure, see these resources in the Microsoft catalog:<br> 
[Security in Azure | Microsoft Learn](/training/browse/?subjects=security&products=azure)

## Next Steps

- [Apply Zero Trust principles to Azure storage](azure-infrastructure-storage.md)
- [Apply Zero Trust principles to virtual machines](azure-infrastructure-virtual-machines.md)
- [Apply Zero Trust principles to a spoke virtual network in Azure](azure-infrastructure-iaas.md)
- [Apply Zero Trust principles to a hub virtual network in Azure](azure-infrastructure-networking.md)

## References

- [Embrace proactive security with Zero Trust](https://aka.ms/zerotrust)
- [Secure networks with Zero Trust](/security/zero-trust/deploy/networks)
- [Zero-trust network for web applications with Azure Firewall and Application Gateway - Azure Architecture Center](/azure/architecture/example-scenario/gateway/application-gateway-before-azure-firewall)
- [Azure Landing Zone Policies](https://github.com/Azure/Enterprise-Scale/wiki/ALZ-Policies)
- [Common Zero Trust identity and device policies](/microsoft-365/security/office-365-security/identity-access-policies)