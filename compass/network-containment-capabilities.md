---
title: "Network security and containment capabilities"
ms.author: dansimp
author: dansimp
manager: dansimp
audience: Admin
ms.topic: article
ms.service: security
localization_priority: Normal
description: "Lists capabilities that can help with network traffic and containment."
---

# Network security and containment capabilities

This article lists capabilities that can help with network traffic and containment.

## Capabilities that work with SaaS, PaaS, and IaaS apps
<br>


|Capability  |Description |More information  |
|---------|---------|---------|
|Azure ExpressRoute    |Use Azure ExpressRoute to create private connections between Azure datacenters and infrastructure on your premises or in a colocation environment. ExpressRoute connections don't go over the public Internet, and they offer more reliability, faster speeds, and lower latencies than typical Internet connections.       | [Azure ExpressRoute](https://azure.microsoft.com/services/expressroute/) <br> <br>  [Azure ExpressRoute for Office 365](/office365/enterprise/azure-expressroute)      |



## Capabilities that work with PaaS and IaaS apps
<br>

|Capability  |Description |More information  |
|---------|---------|---------|
|Azure Application Gateway    |  Azure Application Gateway is a web traffic load balancer that enables you to manage traffic to your web applications. Traditional load balancers operate at the transport layer (OSI layer 4 - TCP and UDP) and route traffic based on source IP address and port, to a destination IP address and port. With Application Gateway, you can make routing decisions based on additional attributes of an HTTP request, such as URI path or host headers.       |[What is Azure Application Gateway?](/azure/application-gateway/overview)      |
|Azure Traffic Manager     |Azure Traffic Manager is a DNS-based traffic load balancer that enables you to distribute traffic optimally to services across global Azure regions, while providing high availability and responsiveness. Traffic Manager uses DNS to direct client requests to the most appropriate service endpoint based on a traffic-routing method and the health of the endpoints.         |[What is Traffic Manager?](/azure/traffic-manager/traffic-manager-overview)  |
|  |         |         |

## Additional capabilities for IaaS apps
<br>

|Capability  |Description |More information  |
|---------|---------|---------|
|Azure Virtual Network    |  Azure Virtual Network (VNet) is the fundamental building block for your private network in Azure. VNet enables many types of Azure resources, such as Azure Virtual Machines (VM), to securely communicate with each other, the internet, and on-premises networks. VNet is similar to a traditional network that you'd operate in your own data center, but brings with it additional benefits of Azure's infrastructure such as scale, availability, and isolation. <br><br> When you create a VNet, you configure the following elements: address space, subnets, regions, and subscription.  |   [What is Azure Virtual Network?](/azure/virtual-network/virtual-networks-overview)  <br> <br> [Virtual Network documentation](/azure/virtual-network/)    |
|Point-to-site virtual private network (VPN) and Site-to-site VPN     |  You can connect your on-premises computers and networks to a virtual network using any combination of these VPN options and Azure ExpressRoute.       | [Point-to-site VPN](/azure/vpn-gateway/vpn-gateway-about-vpngateways?toc=%2fazure%2fvirtual-network%2ftoc.json#P2S) <br> <br> [Site-to-site VPN ](/azure/vpn-gateway/vpn-gateway-about-vpngateways?toc=%2fazure%2fvirtual-network%2ftoc.json#s2smulti)       |
|Security groups and Network virtual appliances |  You can filter network traffic between subnets using either or both of these options. <br><br>Network security groups and application security groups can contain multiple inbound and outbound security rules that enable you to filter traffic to and from resources by source and destination IP address, port, and protocol. <br><br> A network virtual appliance is a VM that performs a network function, such as a firewall, WAN optimization, or other network function.       |[Network security groups](/azure/virtual-network/security-overview#network-security-groups) <br><br> [Application security groups](/azure/virtual-network/security-overview#application-security-groups) <br><br> Network virtual appliances ([Azure Marketplace](https://azuremarketplace.microsoft.com/marketplace/apps/category/networking?page=1&subcategories=appliances))    |
|Route tables and border gateway protocol (BGP) routes   |Azure routes traffic between subnets, connected virtual networks, on-premises networks, and the Internet, by default. You can implement either or both of the options to override the default routes Azure creates.        |  [Route tables](/azure/virtual-network/virtual-networks-udr-overview#user-defined) <br><br> [About BGP with Azure VPN Gateway](/azure/vpn-gateway/vpn-gateway-bgp-overview?toc=%2fazure%2fvirtual-network%2ftoc.json)       |
|Azure DDoS Protection    |Azure DDoS protection, combined with application design best practices, provide defense against DDoS attacks. <br><br> Azure DDoS Protection Basic is automatically enabled as part of the Azure platform and provides real-time mitigation of common network-level attacks.<br> <br>DDoS Protection Standard provides additional mitigation capabilities that are tuned specifically to Azure Virtual Network resources. DDoS Protection Standard can mitigate the following types of attacks: volumetric attacks, protocol attacks, and resource (application) layer attacks.  |        [Azure DDoS Protection Standard overview](/azure/virtual-network/ddos-protection-overview) |
| Azure Firewall |Cloud-native network security to protect your Azure Virtual Network resources.  |       [Azure Firewall](https://azure.microsoft.com/services/azure-firewall/)  |
|  |         |         |

## Next steps
For additional security guidance from Microsoft, see [Microsoft security documentation](/security/).
