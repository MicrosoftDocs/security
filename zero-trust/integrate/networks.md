---
title: Zero Trust integration with Networks overview
description: Independent software vendors (ISVs) integrate their solutions with Azure Firewall Manager to help customers adopt a Zero Trust model and keep their organizations secure.
ms.date: 03/22/2023
ms.service: security
author: janicericketts
ms.author: jricketts
ms.topic: conceptual
---

# Network integrations

:::image type="icon" source="../media/icon-networks-medium.png":::

Traditional enterprise networks are designed to provide users access to applications and data hosted in company operated data centers with strong perimeter security. However, the modern workplace increasingly uses services and data outside the corporate firewall. Apps and services have moved to the cloud, and users need to be able to access them from a variety of work and personal devices.

Network solutions are an important piece of Zero Trust. They verify that the ingress and egress at the edge of the network is allowable and inspect traffic for malicious content. They support least privilege access and the principle of "assume breach" by allowing organizations to segment networks and only connect users to the segment of the network they need access to.

## Zero Trust integration with Networks guidance

Independent Software Vendor (ISV) partners integrate with Microsoft's network solutions and bring their own security expertise to enhance the products.

In this article we discuss our Network integration partners so customers can use familiar, best-in-breed, third-party security as a service (SECaaS) offerings to protect Internet access for their users. Please see [Microsoft 365 Networking Partner Program](/microsoft-365/enterprise/microsoft-365-networking-partner-program) for more information about becoming an ISV partner.

### Gateway Load Balancer
Gateway Load Balancer is a SKU of the Azure Load Balancer portfolio catered for high performance and high availability scenarios with third-party Network Virtual Appliances (NVAs). It enables you to easily deploy, scale, and manage NVAs. 

### Virtual WAN
Virtual WAN is a networking service that brings many networking, security, and routing functionalities together to provide a single operational interface. It provides a hub and spoke architecture with scale and performance built in for branches (VPN/SD-WAN devices), users (Azure VPN/OpenVPN/IKEv2 clients), ExpressRoute circuits, and virtual networks. It enables a global transit network architecture, where the cloud hosted network 'hub' enables transitive connectivity between endpoints that may be distributed across different types of 'spokes'.

### Azure Web Application Firewall
Azure Web Application Firewall (WAF) provides centralized protection of your web applications from common exploits and vulnerabilities. WAF can be deployed with Azure Application Gateway, Azure Front Door, and Azure Content Delivery Network (CDN) service from Microsoft. WAF on Azure CDN is currently under public preview. 

### DDOS Protection
Azure DDoS Protection, combined with application design best practices, provides enhanced DDoS mitigation features to defend against DDoS attacks. It's automatically tuned to help protect your specific Azure resources in a virtual network. Protection is simple to enable on any new or existing virtual network, and it requires no application or resource changes.

### Azure Firewall Manager

[Azure Firewall Manager](/azure/firewall-manager/overview) is a security management service that provides central security policy and route management for cloud-based security perimeters.

Security partner providers have [integrated with Azure Firewall Manager](/azure/firewall-manager/trusted-security-partners) so customers can use familiar, best-in-breed, third-party security as a service (SECaaS) offerings to protect Internet access for their users. Customers can secure a hub with a supported security partner and route and filter Internet traffic from Virtual Networks (VNets) or branch locations within a region. Hubs can be deployed in multiple Azure regions to get connectivity and security anywhere across the globe, using the security partner’s offering for Internet/SaaS application traffic and Azure Firewall for private traffic in the secured hubs.

The supported security partners are Zscaler, Check Point, and iboss.

:::image type="content" source="../media/integrate/networks/firewall-security-partners.png" alt-text="Architectural network diagram illustrating ZScaler, Check Point, and iboss solutions with a bi-directional connection to a secured vHub. The vHub is in the same vNet as a hub VNET hosted in another Azure region. The vHub is also connected to the company headquarters with a virual WAN and by a VPN to end user devices. The hub VNET is connected by a VPN to a data center.":::

If your solution will connect with Microsoft 365, you can use the guidance from the [Microsoft 365 Networking Partner Program](/microsoft-365/enterprise/microsoft-365-networking-partner-program) to ensure that your solution follows [Microsoft 365 network connectivity principles](/microsoft-365/enterprise/microsoft-365-network-connectivity-principles). The purpose of this program is to facilitate great customer experience with Microsoft 365 through easy discovery of validated partner solutions that consistently demonstrate alignment to key principles for optimal Microsoft 365 connectivity in customer deployments.

## Next steps
- [Gateway Load Balancer documentation](/azure/load-balancer/gateway-overview)
- [Virtual WAN documentation](/azure/virtual-wan/virtual-wan-about)
- [DDOS Protection documentation](/azure/ddos-protection/ddos-protection-overview)
- [Azure Firewall Manager documentation](/azure/firewall-manager/)
