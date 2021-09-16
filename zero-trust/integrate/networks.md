---
title: Network Zero Trust integration overview
description: Independent software vendors (ISVs) integrate their solutions with Azure Firewall Manager to help customers adopt a Zero Trust model and keep their organizations secure.
ms.date: 09/17/2021
ms.service: security
author: knicholasa
ms.author: nichola
ms.topic: conceptual
---

# Network integrations

:::image type="icon" source="../media/icon-networks-medium.png":::

Traditional enterprise networks are designed to provide users access to applications and data hosted in company operated data centers with strong perimeter security. However, the modern workplace increasingly uses services and data outside the corporate firewall. Apps and services have moved to the cloud, and users need to be able to access them from a variety of work and personal devices.

Network solutions are an important piece of Zero Trust. They verify that the ingress and egress at the edge of the network is allowable and inspect traffic for malicious content. They support least privileged access and the principle of "assume breach" by allowing organizations to segment networks and only connect users to the segment of the network they need access to.

## Networks Zero Trust integration guidance

Independent Software Vendor (ISV) partners integrate with Microsoft's network solutions and bring their own security expertise to enhance the products.

In this article we discuss the partners who have integrated with Azure Firewall Manager so customers can use familiar, best-in-breed, third-party security as a service (SECaaS) offerings to protect Internet access for their users.

### Azure Firewall Manager

[Azure Firewall Manager](/azure/firewall-manager/overview) is a security management service that provides central security policy and route management for cloud-based security perimeters.

Security partner providers have [integrated with Azure Firewall Manager](/azure/firewall-manager/trusted-security-partners) so customers can use familiar, best-in-breed, third-party security as a service (SECaaS) offerings to protect Internet access for their users. Customers can secure a hub with a supported security partner and route and filter Internet traffic from Virtual Networks (VNets) or branch locations within a region. Hubs can be deployed in multiple Azure regions to get connectivity and security anywhere across the globe, using the security partner’s offering for Internet/SaaS application traffic and Azure Firewall for private traffic in the secured hubs.

The supported security partners are Zscaler, Check Point, and iboss.

:::image type="content" source="../media/integrate/networks/firewall-security-partners.png" alt-text="Architectural network diagram illustrating ZScaler, Check Point, and iboss solutions with a bi-directional connection to a secured vHub. The vHub is in the same vNet as a hub VNET hosted in another Azure region. The vHub is also connected to the company headquarters with a virual WAN and by a VPN to end user devices. The hub VNET is connected by a VPN to a data center.":::

If your solution will connect with Microsoft 365, you can use the guidance from the [Microsoft 365 Networking Partner Program](/en-us/microsoft-365/enterprise/microsoft-365-networking-partner-program) to ensure that your solution follows [Microsoft 365 network connectivity principles]((/microsoft-365/enterprise/microsoft-365-network-connectivity-principles). The purpose of this program is to facilitate great customer experience with Microsoft 365 through easy discovery of validated partner solutions that consistently demonstrate alignment to key principles for optimal Microsoft 365 connectivity in customer deployments.

## Next steps

- [Azure Firewall Manager documentation](/azure/firewall-manager/)