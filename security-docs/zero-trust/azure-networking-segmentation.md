---
title: Apply Zero Trust principles to segmenting Azure-based network communication
description: Learn how to apply Zero Trust principles to segmenting Azure-based network communication.
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

# Apply Zero Trust principles to segmenting Azure-based network communication

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

Additional authors:

- Mays Algebary
- Mauricio Rojas
- Adam Torkar

--->

This article provides guidance for applying the [principles of Zero Trust](zero-trust-overview.md) for segmenting networks in Azure environments. Here are the Zero Trust principles.

| Zero Trust principle | Definition |
| --- | --- |
| Verify explicitly | Always authenticate and authorize based on all available data points. |
| Use least privileged access | Limit user access with Just-In-Time and Just-Enough-Access (JIT/JEA), risk-based adaptive policies, and data protection. |
| Assume breach | Minimize blast radius and segment access. Verify end-to-end encryption and use analytics to get visibility, drive threat detection, and improve defenses. <br><br> You can minimize cyber-attack blast radius and segment access by performing network segmentation at various levels in your Azure infrastructure. |

This article is a part of a [series of articles](azure-networking-overview.md) that demonstrate how to apply the principles of Zero Trust to Azure networking.

As organizations grow from small businesses into large enterprises, they often need to move from a single Azure subscription into multiple subscriptions to separate resources for each department. It’s important to carefully plan the segmentation of your network to create logical boundaries and isolation between environments.

Each environment, typically reflecting a separate department of your organization, should have its own access permissions and policies for specific workloads. For example, users from your internal software developer subscription shouldn't have access to managing and deploying network resources in the connectivity subscription. However, these environments still need network connectivity to achieve the required functionality to basic services, such as DNS, hybrid connectivity, and being able to reach other resources across different [Azure virtual networks (VNets)](/azure/virtual-network/virtual-networks-overview).

The segmentation of your Azure infrastructure provides not only isolation but can also create security boundaries that prevent an attacker from moving across environments and inflicting additional damage (the **Assume breach** Zero Trust principle).

## Reference architecture

You can use different levels of segmentation in Azure to help protect your resources from unauthorized access or malicious attack. These levels of segmentation start at the subscription level and go all the way down to applications running on virtual machines. Segmentation creates a boundary that separates one environment from another, each with its own rules and policies. With the assumption that breaches can happen, you need to segment your networks to prevent their spread.

Azure networking uses the following levels of segmentation:

- Subscriptions

  An Azure subscription is a logical container used to provision resources in Azure. It's linked to an Azure account in a Microsoft Entra ID tenant and serves as a single billing unit for Azure resources assigned to the subscription. An Azure subscription is also a logical boundary for access to the resources contained in the subscription. Access between resources in different subscriptions requires explicit permissions.

- VNets

  An Azure VNet is an isolated private network that by default allows all the virtual machines within it to communicate with each other. By default, VNets can't communicate with other VNets unless you create connections between them through peering, VPN connections, or ExpressRoute. Individual VNets can be used as a trust boundary that divides different applications, workloads, departments, or organizations.

  [Azure Virtual Network Manager](/azure/virtual-network-manager/overview) (AVNM) is a network management service that allows a single administration team to manage VNets and enforce security rules across multiple subscriptions globally. You can use AVNM to define network groups to determine which VNets can communicate with each other. You can also use AVNM to monitor network configuration changes.

- Workloads within a VNet

  For workloads within a VNet—such as virtual machines or any PaaS services that support VNet integration such as Azure Databricks and App Service—communication is allowed by default since they're contained within the same VNet and must be further secured using network security groups. Tools and services for segmentation within a VNet include the following:

  - Azure Firewall

    [Azure Firewall](/azure/firewall/overview) is a service deployed in a VNet to filter traffic between cloud resources, on-premises, and the Internet. With Azure Firewall, you can define rules and policies to allow or deny traffic at the network and application layers. You can also benefit from the advanced threat protection features provided by Azure Firewall such as Intrusion Detection and Prevention System (IDPS), Transport Layer Security (TLS) inspection, and threat intelligence-based filtering.

  - Network security group

    A [network security group](/azure/virtual-network/network-security-groups-overview) is an access control mechanism that filters network traffic between Azure resources such as virtual machines within a VNet. A network security group contains security rules that allows or denies traffic at the subnet or virtual machine levels in a VNet. A common use of network security groups is to segment the sets of virtual machines in different subnets.

  - Application security group

    An [application security group](/azure/virtual-network/application-security-groups) is an extension of a network security group that allows you to group the network interfaces of virtual machines based on their roles and functions. You can then use the application security groups in a network security group at scale without having to define the IP addresses of virtual machines.

  - Azure Front Door

    [Azure Front Door](/azure/frontdoor/front-door-overview) is Microsoft’s modern cloud Content Delivery Network (CDN) that provides fast, reliable, and secure access between your users and your applications’ static and dynamic web content across the globe.

The following diagram shows the reference architecture for the levels of segmentation.

:::image type="content" source="media/azure-networking/azure-networking-segmentation-reference-architecture.svg" alt-text="Diagram showing the reference architecture and the levels of segmentation for Azure networking." lightbox="media/azure-networking/azure-networking-segmentation-reference-architecture.svg":::

In the diagram, the solid red lines indicate levels of segmentation between:

1. Azure subscriptions
2. VNets in a subscription
3. Subnets in a VNet
4. The Internet and a VNet

The diagram also shows a set of VNets managed by AVNM that can span Azure subscriptions.

## What's in this article?

Zero Trust principles are applied across the reference architecture within the Azure cloud. The following table describes the recommendations for segmenting networks across this architecture to adhere to the **Assume breach** Zero Trust principle.

| Step | Task |
| --- | --- |
| 1 | Segment within your individual VNets. |
| 2 | Connect multiple VNets with peering. |
| 3 | Connect multiple VNets in a hub and spoke configuration. |

## Step 1: Segment within your individual VNets

Within a single VNet in an Azure subscription, you use subnets to achieve separation and segmentation of resources. For instance, within a VNet there could be a subnet for database servers, another for web applications, and a dedicated subnet for an Azure Firewall or [Azure Application Gateway](/azure/application-gateway/overview) with a [Web Application Firewall](/azure/web-application-firewall/ag/ag-overview). By default, all communication between subnets is enabled within a VNet.

To create isolation between subnets, you can apply network security groups or application security groups to permit or deny specific network traffic based on IP addresses, ports, or protocols. However, designing and maintaining network security groups and application security groups can also create management overhead.

This illustration shows a common and recommended configuration of a three-tier application with separate subnets for each tier and the use of network security groups and application security groups to create segmented boundaries between each subnet.

:::image type="content" source="media/azure-networking/azure-networking-segmentation-nsg-asg.svg" alt-text="Diagram showing the use of network security groups and application security groups for segmentation between subnets." lightbox="media/azure-networking/azure-networking-segmentation-nsg-asg.svg":::

You can also achieve segmentation of resources by routing inter-subnet traffic using user-defined routes (UDRs) pointing to an Azure Firewall or a third-party Network Virtual Appliance (NVA). Azure Firewall and NVAs also have the capability to permit or deny traffic using layer 3 to layer 7 controls. Most of these services provide advanced filtering capabilities.

For more information, see the guidance in [Pattern 1: Single virtual network](/azure/architecture/reference-architectures/hybrid-networking/network-level-segmentation#pattern-1-single-virtual-network).

## Step 2: Connect multiple VNets with peering

By default, there's no allowed communication between VNets with a single Azure subscription or across multiple subscriptions. Multiple VNets, each belonging to different entities, have their own access controls. They can connect to each other or to a centralized hub VNet using VNet peering, where an Azure Firewall or a third-party NVA inspects all traffic.

This illustration shows a VNet peering connection between two VNets and the use of Azure Firewall on each end of the connection.

:::image type="content" source="media/azure-networking/azure-networking-segmentation-vnet-peering.svg" alt-text="Diagram showing VNet peering and the use of Azure Firewalls to connect and segment two VNets." lightbox="media/azure-networking/azure-networking-segmentation-vnet-peering.svg":::

A hub VNet typically contains shared components such as firewalls, identity providers, and hybrid connectivity components, among others. UDR management becomes simpler because adding specific prefix UDRs for micro-segmentation would only be necessary if intra-VNet traffic is a requirement. However, since the VNet has its own boundaries, security controls are already in place.

For more information, see the following guidance:

- [Firewall and Application Gateway for virtual networks](/azure/architecture/example-scenario/gateway/firewall-application-gateway)
- [Pattern 2: Multiple virtual networks with peering in between them](/azure/architecture/reference-architectures/hybrid-networking/network-level-segmentation#pattern-2-multiple-virtual-networks-with-peering-in-between-them)
- [Apply Zero Trust principles to a spoke virtual network in Azure](/security/zero-trust/azure-infrastructure-iaas)
- [Apply Zero Trust principles to a hub virtual network in Azure](/security/zero-trust/azure-infrastructure-networking)

## Step 3: Connect multiple VNets in a hub and spoke configuration

For multiple VNets in a hub and spoke configuration, you need to consider how to segment your network traffic for these boundaries:

- Internet boundary
- On-premises network boundary
- Boundaries to global Azure services

### Internet boundary

Securing Internet traffic is a fundamental priority in network security, which involves managing ingress traffic from the Internet (untrusted) and egress traffic directed towards the Internet (trusted) from your Azure workloads.

Microsoft recommends that ingress traffic from the Internet has a single point of entry. Microsoft highly encourages that the ingress traffic traverse through an Azure PaaS resource such as Azure Firewall, Azure Front Door, or Azure Application Gateway. These PaaS resources offer more capabilities than a virtual machine with a public IP address.

#### Azure Firewall

This illustration shows how Azure Firewall in its own subnet acts as a central entry point and segmentation boundary for traffic between the Internet and a three-tier workload in an Azure VNet.

:::image type="content" source="media/azure-networking/azure-networking-segmentation-azure-firewall.svg" alt-text="Diagram showing the use of Azure Firewall for traffic segmentation between a VNet and the Internet." lightbox="media/azure-networking/azure-networking-segmentation-azure-firewall.svg":::

For more information, see [Azure Firewall](/azure/well-architected/service-guides/azure-firewall) in the Microsoft Azure Well-Architected Framework.

#### Azure Front Door

Azure Front Door can act as a boundary between the Internet and services hosted in Azure. Azure Front Door supports [Private Link](/azure/private-link/private-link-overview) connectivity to resources such as Internal Load Balancing (ILB) for VNet access, storage accounts for static websites and blob storage, and Azure App services. Azure Front Door is usually done for at-scale deployments.

Azure Front Door is more than a load balancing service. The Azure Front Door infrastructure has DDoS protection built in. When caching is enabled, content can be retrieved from point of presence (POP) locations rather than constantly accessing backend servers. When the cache expires, Azure Front Door retrieves the requested resource and updates the cache. Rather than end users accessing their servers, Azure Front Door uses Split TCP for two separate connections. This not only improves end user experience but prevents malicious actors from accessing resources directly.

This illustration shows how Azure Front Door provides segmentation between Internet users and Azure resources, which can be in storage accounts.

:::image type="content" source="media/azure-networking/azure-networking-segmentation-azure-front-door.svg" alt-text="Diagram showing the use of an Azure Front Door as a boundary between the Internet and services hosted in Azure." lightbox="media/azure-networking/azure-networking-segmentation-azure-front-door.svg":::

For more information, see [Azure Front Door](/azure/well-architected/service-guides/azure-front-door) in the Azure Well-Architected Framework.

#### Azure Application Gateway

The Internet point of entry can also be a combination of ingress points. For example, HTTP/HTTPS traffic can ingress through an Application Gateway protected by a Web Application Firewall or Azure Front Door. Non-HTTP/HTTPS traffic such as RDP/SSH can ingress via Azure Firewall or an NVA. You can use these two elements in tandem for deeper inspection and to control traffic flow using UDRs.

This illustration shows Internet ingress traffic and the use of an Application Gateway with a Web Application Firewall for HTTP/HTTPS traffic and an Azure Firewall for all other traffic.

:::image type="content" source="media/azure-networking/azure-networking-segmentation-application-gateway.svg" alt-text="Diagram showing the ways to connect and segment traffic between an Azure subscription and an on-premises network." lightbox="media/azure-networking/azure-networking-segmentation-application-gateway.svg":::

Two commonly recommended scenarios are to:

- Place an Azure Firewall or an NVA in parallel with an Application Gateway. 
- Place an Azure Firewall or an NVA after an Application Gateway for further traffic inspection before it reaches the destination. 

For more information, see [Azure Application Gateway in the Microsoft Azure Well-Architected Framework](/azure/well-architected/service-guides/azure-application-gateway).

Here are additional common patterns for Internet traffic flows.

#### Ingress traffic using multiple interfaces

One approach involves using multiple network interfaces on virtual machines when using NVAs: one interface for untrusted traffic (external facing) and another for trusted traffic (internal facing). In terms of traffic flow, you must route ingress traffic from on-premises to the NVA using UDRs. Ingress traffic from the Internet received by the NVA must be routed to the destination workload on the appropriate VNet or subnet by a combination of static routes in the guest OS appliance and UDRs.

#### Egress traffic and UDRs

For traffic departing your VNet for the Internet, you can apply a UDR using a route table with the chosen NVA as the next hop. To reduce complexity, you can deploy an Azure Firewall or NVA inside your [Azure Virtual WAN](/azure/virtual-wan/virtual-wan-about) hub and turn on [Internet security with Routing Intent](/azure/virtual-wan/how-to-routing-policies). This ensures that both north-south traffic (coming in and out of a network scope) and east-west traffic (between devices within a network scope) destined for non-Azure Virtual IP addresses (VIPs) gets inspected.

#### Egress traffic and a default route

Some methods involve managing a default route (0.0.0.0/0) with different methods. As a general rule, it's recommended that egress traffic originating in Azure utilizes exit points and inspection with Azure Firewall or NVAs due to the amount of throughput that the Azure infrastructure can handle, which in most cases might be far greater and more resilient. In this case, configuring a default route in the UDRs of workload subnets can force traffic to those exit points. You might also prefer to route egress traffic from on-premises to Azure as an exit point. In this case, utilize [Azure Route Server](/azure/route-server/overview) in combination with an NVA to advertise a default route to on-premises utilizing Border Gateway Protocol (BGP).

There are special cases when you need all egress traffic to be routed back to on-premises by advertising a default route over BGP. This forces traffic leaving the VNet to be tunneled via your on-premises network to a firewall for inspection. This last approach is the least desired due to increased latency and lack of security controls provided by Azure. This practice is widely adopted by the government and banking sectors that have specific requirements for traffic inspection within their on-premises environment.

In terms of scale:

- For a single VNet, you can use network security groups, which strictly adhere to layer 4 semantics, or you can use an Azure Firewall that adheres to both Layer 4 and Layer 7 semantics.
- For multiple VNets, a single Azure Firewall can still be used if it's reachable, or you can deploy an Azure Firewall in each virtual network and direct traffic with UDRs.

For large enterprise distributed networks, you can still use the hub and spoke model and direct traffic with UDRs. However, this can lead to management overhead and VNet peering limits. For ease of use, Azure Virtual WAN can achieve this if you deploy an Azure Firewall in the virtual hub and activate Routing Intent for Internet security. This will inject default routes across all spokes and branch networks and send Internet-bound traffic to the Azure Firewall for inspection. Private traffic destined to RFC 1918 address blocks is sent to the Azure Firewall or NVA as the designated next-hop inside the Azure Virtual WAN hub.

### On-premises network boundary

In Azure, the main methods to establish connectivity with on-premises networks include Internet Protocol (IPsec) tunnels, ExpressRoute tunnels, or Software-defined WAN (SD-WAN) tunnels. Typically, you use an [Azure Site-to-Site (S2S) VPN connection](/azure/vpn-gateway/vpn-gateway-about-vpngateways) for smaller workloads that require less bandwidth. For workloads that require a dedicated service path and higher throughput needs, Microsoft recommends ExpressRoute.

This illustration shows the different types of connection methods between an Azure environment and an on-premises network.

:::image type="content" source="media/azure-networking/azure-networking-segmentation-on-premises.svg" alt-text="Diagram showing the different types of connection methods between an Azure environment and an on-premises network." lightbox="media/azure-networking/azure-networking-segmentation-on-premises.svg":::

While Azure VPN connections can support multiple tunnels, ExpressRoute is often configured for larger enterprise networks that require higher bandwidth and private connections through a connectivity partner. For ExpressRoute, it's possible to connect the same VNet to multiple circuits, but for segmentation purposes, this is often not ideal as it allows VNets not connected with each other to communicate.

One method of segmentation involves choosing not to use a remote gateway on spoke VNets or disabling BGP route propagation if you're using route tables. You can still segment hubs connected to ExpressRoute with NVAs and Firewalls. For spokes that are peered to hubs, you can choose not to use remote gateway in the VNet peering properties. That way, spokes only learn about their directly connected hubs and not any on-premises routes.

Another emerging approach to segment traffic going to and from on-premises is the use of SD-WAN technologies. You can extend your branch locations into Azure SD-WAN by using third-party NVAs in Azure to create segmentation based on SD-WAN tunnels coming from different branches inside the NVA appliances. You can use Azure Route Server to inject the address prefixes for the SD-WAN tunnels into the Azure platform for a hub and spoke topology.

For a virtual WAN topology, you can have direct integration of the third-party SD-WAN NVA inside the virtual hub. You can also use BGP endpoints to allow the use of SD-WAN solutions, creating tunnels from the virtual hub-integrated NVA.

For both models, you can use ExpressRoute to segment underlying private or public connectivity with private peering or Microsoft peering. For security, a common practice is to advertise a default route over ExpressRoute. This forces all traffic leaving the VNet to be tunneled to your on-premises network for inspection. Similarly, traffic coming over both VPN and ExpressRoute can be sent to an NVA for further inspection. This also applies to traffic leaving Azure. These methods are straightforward when the environment is smaller, such as one or two regions.

For large, distributed networks, you can also use Azure Virtual WAN by activating private traffic inspection using Routing Intent. This directs all traffic destined to a private IP address of the NVA for inspection. As with the above methods, this is much easier to manage when your environment spans multiple regions.

The other approach with Azure Virtual WAN is to use custom route tables for isolation boundaries. You can create custom routes and only associate and propagate the VNets you want to those route tables. However, this capability can't be combined with routing intent today. To isolate branches, you can assign labels to associate branches to that label. You can also disable propagation to the default label on a per-hub basis. Currently, you can't isolate individual branches in Azure separately on a single hub. For example, you can't isolate SD-WAN from ExpressRoute. But on an entire hub, you can disable propagation to the default label.

### Boundaries to global Azure services

In Azure, most services are by default accessible through the Azure global WAN. This also applies to public access to Azure PaaS services. For instance, Azure Storage has a built-in firewall that can restrict access to VNets and block public access. However, there's often a need for more granular control. The typical preference is to connect to Azure VIPs privately, rather than using the default public IP addresses provided.

The most common method to restrict access to PaaS resources is through Azure Private Link. When you create a private endpoint, it gets injected into your VNet. Azure uses this private IP address to tunnel to the PaaS resource in question. Azure maps a DNS A record to the private endpoint using Azure Private DNS Zones and maps a CNAME record to the private link PaaS resource.

Service endpoints offer an alternative method for connecting to PaaS VIPs. You can select service tags to allow connections to all PaaS resources within that tag and provide private connectivity to the PaaS resource.

Another prevalent method involves using Microsoft Peering for ExpressRoute. If you want to connect to PaaS VIPs from on-premises, you can set up Microsoft Peering. You can choose the BGP community for the VIPs to be consumed and this gets advertised over the Microsoft Peering path.

For more information, see the following guidance:

- [Firewall and Application Gateway for virtual networks](/azure/architecture/example-scenario/gateway/firewall-application-gateway)
- [Pattern 3: Multiple virtual networks in a hub and spoke model](/azure/architecture/reference-architectures/hybrid-networking/network-level-segmentation#pattern-3-multiple-virtual-networks-in-a-hub-and-spoke-model)

## Segmentation summary

This table summarizes the different levels of segmentation and security methods.

| Between… | Default behavior | Communication enabled by… | Segmentation security method(s) |
| --- | --- | --- | --- |
| Subscriptions | No communication | - VNet peering <br><br> - VPN gateways | Azure Firewall |
| VNets | No communication | - VNet peering <br><br> - VPN gateways | Azure Firewall |
| Workloads on subnets within a VNet | Open communication | N/A | - Network security groups <br><br> - Application security groups |
| The Internet and a VNet | No communication | - Load Balancer <br><br> - Public IP <br><br> - Application Gateway <br><br> - Azure Front Door | - Azure Application Gateway with a Web Application Firewall <br><br> - Azure Firewall <br><br> - Azure Front Door with a Web Application Firewall |
| The Internet and your on-premises networks | No communication | - Azure S2S VPN <br><br> - IPSec tunnel <br><br> - ExpressRoute tunnel <br><br> - SD-WAN tunnel | Azure Firewall |
| The Internet and virtual machines in a VNet | No communication if the virtual machines have only private IP addresses | Assigning the virtual machine a public IP address | Local virtual machine firewall |

## Recommended training

- [Configure and manage virtual networks for Azure administrators](/training/paths/azure-administrator-manage-virtual-networks/)
- [Introduction to Azure Web Application Firewall](/training/modules/introduction-azure-web-application-firewall/)
- [Secure and isolate access to Azure resources by using network security groups and service endpoints](/training/modules/secure-and-isolate-with-nsg-and-service-endpoints/)
- [Introduction to Azure Front Door](/training/modules/intro-to-azure-front-door/)
- [Introduction to Azure Application Gateway](/training/modules/intro-to-azure-application-gateway/)
- [Introduction to Azure Private Link](/training/modules/introduction-azure-private-link/)
- [Introduction to Azure Virtual WAN](/training/modules/introduction-azure-virtual-wan/)
- [Connect your on-premises network to Azure with VPN Gateway](/training/modules/connect-on-premises-network-with-vpn-gateway/)

## Next Steps

For additional information about applying Zero Trust to Azure networking, see:

- [Encrypt Azure-based network communication](azure-networking-encryption.md)
- [Gain visibility into your network traffic](azure-networking-visibility.md)
- [Discontinue legacy network security technology](azure-networking-legacy.md)
- [Secure networks with Zero Trust](./deploy/networks.md)
- [Spoke virtual networks in Azure](azure-infrastructure-iaas.md)
- [Hub virtual networks in Azure](azure-infrastructure-networking.md)
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