---
title: Apply Zero Trust principles to gain visibility into network traffic
description: Learn how to apply Zero Trust principles to gain visibility into network traffic.
ms.date: 06/06/2024
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

# Apply Zero Trust principles to gain visibility into network traffic

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

Additional authors:

- Mays Algebary
- Mauricio Rojas
- Adam Torkar

--->

This article provides guidance to applying the [principles of Zero Trust](zero-trust-overview.md) for segmenting networks in Azure environments. Here are the Zero Trust principles.

| Zero Trust principle | Definition |
| --- | --- |
| Verify explicitly | Always authenticate and authorize based on all available data points. |
| Use least privileged access | Limit user access with Just-In-Time and Just-Enough-Access (JIT/JEA), risk-based adaptive policies, and data protection. |
| Assume breach | Minimize blast radius and segment access. Verify end-to-end encryption and use analytics to get visibility, drive threat detection, and improve defenses. <br><br> You can minimize cyber-attack blast radius and segment access by performing network segmentation at various levels in your Azure infrastructure. |

This article is a part of a [series of articles](azure-networking-overview.md) that demonstrate how to apply the principles of Zero Trust to Azure networking.


## Recommended training

- [Configure and manage virtual networks for Azure administrators](/training/paths/azure-administrator-manage-virtual-networks/)
- [Introduction to Azure Web Application Firewall](/training/modules/introduction-azure-web-application-firewall/)
- [Secure and isolate access to Azure resources by using network security groups and service endpoints](/training/modules/secure-and-isolate-with-nsg-and-service-endpoints/)
- [Introduction to Azure Front Door](/training/modules/intro-to-azure-front-door/)
- [Introduction to Azure Application Gateway](/training/modules/intro-to-azure-application-gateway/)
- [Introduction to Azure Web Application Firewall](/training/modules/introduction-azure-web-application-firewall/)
- [Introduction to Azure Private Link](/training/modules/introduction-azure-private-link/)
- [Introduction to Azure Virtual WAN](/training/modules/introduction-azure-virtual-wan/)
- [Connect your on-premises network to Azure with VPN Gateway](/training/modules/connect-on-premises-network-with-vpn-gateway/)

## Next Steps

For additional information about applying Zero Trust to Azure networking, see:

- [Apply Zero Trust principles to encrypting Azure-based network communication](azure-networking-encryption.md)
- [Apply Zero Trust principles to segmenting Azure-based network communication](azure-networking-segmentation.md)
- [Secure networks with Zero Trust](./deploy/networks.md)
- [Spoke virtual networks in Azure](azure-infrastructure-iaas.md)
- [Hub virtual networks in Azure](azure-infrastructure-paas.md)
- [Spoke virtual networks with Azure PaaS services](azure-infrastructure-paas.md)
- [Azure Virtual WAN](azure-virtual-wan.md)

## References

Refer to these links to learn about the various services and technologies mentioned in this article.

- [Azure Virtual Network Manager](/azure/virtual-network-manager/overview)
- [Azure Firewall](/azure/firewall/overview)
- [Network security groups](/azure/virtual-network/network-security-groups-overview)
- [Application security groups](/azure/virtual-network/application-security-groups)
- [Azure Front Door](/azure/frontdoor/front-door-overview)
- [Azure Application Gateway](/azure/application-gateway/overview)
- [Web Application Firewall](/azure/web-application-firewall/ag/ag-overview)
- [Azure Private Link](/azure/private-link/private-link-overview)
- [Azure Virtual WAN](/azure/virtual-wan/virtual-wan-about)
- [Internet security with Routing Intent](/azure/virtual-wan/how-to-routing-policies)
- [Azure Site-to-Site (S2S) VPN connection](/azure/vpn-gateway/vpn-gateway-about-vpngateways)
- [Azure Route Server](/azure/route-server/overview)