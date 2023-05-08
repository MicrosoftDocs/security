---
title: Apply Zero Trust principles to Azure Virtual WAN
description: Learn how to secure an Azure Virtual WAN deployment with Zero Trust principles. 
ms.date: 02/21/2023
ms.service: security
author: sikovatc
ms.author: sikovatc
ms.topic: conceptual
ms.collection: 
  - msftsolution-azurepaas
  - msftsolution-scenario
  - zerotrust-solution
---

# Apply Zero Trust principles to an Azure Virtual WAN deployment

With the modern cloud, mobile devices, and other endpoints evolution, relying only on corporate firewalls and perimeter networks is no longer sufficient. An end-to-end Zero Trust strategy assumes breaches are inevitable. That means you must verify each request as if it originates from an uncontrolled network. Networking still plays an important role in Zero Trust to connect and protect infrastructure, applications, and data. In the Zero Trust model, there are three key objectives when it comes to securing your networks:

- Be ready to handle attacks before they happen.
- Minimize the extent of the damage and how fast it spreads.
- Increase the difficulty of compromising your cloud footprint.

Azure Virtual WAN allows a [global transit network architecture](/azure/virtual-wan/virtual-wan-global-transit-network-architecture#globalnetworktransit) by enabling ubiquitous, any-to-any connectivity between globally distributed sets of cloud workloads in virtual networks (VNets), branch sites, SaaS and PaaS applications, and users. Adopting a Zero Trust approach in Azure Virtual WAN is critical to ensure that your backbone is secure and protected. 

This article provides steps to apply the [principles of Zero Trust](zero-trust-overview.md#guiding-principles-of-zero-trust) to an Azure Virtual WAN deployment in the following ways:

| Zero Trust principle | Definition | Met by |
| --- | --- | --- |
| Verify explicitly |Always authenticate and authorize based on all available data points. | Use Azure Firewall with Transport Layer Security (TLS) inspection to verify risk and threats based on all available data.  Conditional Access controls are intended to be used to deliver authentication by diverse data points, the Azure Firewall does not perform user authentication. |
| Use least privileged access |  Limit user access with Just-In-Time and Just-Enough-Access (JIT/JEA), risk-based adaptive policies, and data protection. | User access is beyond the scope of Azure network infrastructure deployments. Using Identity pillar solutions like Privileged Access Management, Conditional Access, and other controls are the way to deliver on this principle.  |
| Assume breach | Minimize blast radius and segment access. Verify end-to-end encryption and use analytics to get visibility, drive threat detection, and improve defenses. | Each spoke VNet has no access to other spoke VNets unless the traffic gets routed through the firewall integrated inside each Azure Virtual WAN hub. The firewall is set to deny by default, allowing only traffic allowed by specified rules. In the event of a compromise or breach of one application/workload, it has limited ability to spread due to the Azure Firewall performing traffic inspection and only forwarding allowed traffic. Only resources in the same workload would be exposed to the breach in the same application. |

For more information about how to apply the principles of Zero Trust across an Azure IaaS environment, see the [Apply Zero Trust principles to Azure infrastructure overview](azure-infrastructure-overview.md).

For an industry discussion of Zero Trust, [NIST Special Publication 800-207](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-207.pdf).

## Azure Virtual WAN

Azure Virtual WAN is a networking service that brings many networking, security, and routing functionalities together to provide a single operational interface. Some of the main features include:

- Advanced routing features
- Security “bump-in-the-wire” integration (through Azure Firewall or Firewall supported Network Virtual Appliances [NVAs] in the hub)
- Encrypted ExpressRoute

A Zero Trust approach for Azure Virtual WAN requires configuration of several underlying services and components from the list above. Below is a list of steps and actions that will be detailed in the remaining part of this document: 	

- Deploy Azure Firewall or [supported Next Generation Firewall (NGFW)](/azure/virtual-wan/virtual-wan-locations-partners#partners-with-integrated-virtual-hub-offerings) NVAs inside each Virtual WAN hub.
- Configure inter-VNet and on-premises branch routing to create a Zero Trust environment by sending all traffic to security appliances in the hubs for inspection. Configure it to provide filtering and protection for known threats.
- Ensure no resources in the spokes have direct access to the Internet.
- Provide application micro-segmentation in spoke networks, along with ingress/egress micro-perimeters strategy.
- Provide observability for network security events.

## Reference architecture

The following diagram shows a common reference architecture will be used to demonstrate a commonly deployed environment and how to apply the principles of Zero Trust to Azure Virtual WAN. 

:::image type="content" source="media/vwan/ref-arch-vwan.png" alt-text="Diagram of the reference architecture for Azure Virtual Desktop." lightbox="media/vwan/ref-arch-vwan.png":::

Azure Virtual WAN is deployable in [two types](/azure/virtual-wan/virtual-wan-about#basicstandard), Basic and Standard. Standard is required to leverage Zero Trust architecture with Virtual WAN with Azure Firewall or an NGFW.

The Azure Virtual WAN with secured hubs reference architecture includes:

- A single logical Virtual WAN.
- Two secured virtual hubs, one per region.
- An instance of Azure Firewall Premium deployed in each hub.
- At least one Azure Firewall Policy-[Premium](/azure/firewall-manager/policy-overview#basic-standard-and-premium-policies).
- Point-to-site (P2S) and site-to-site (S2S) VPN gateways, ExpressRoute gateways.
- Point-to-site, site-to-site and ExpressRoute-connected “branches.”
- A “shared services” VNet containing core infrastructure resources that cannot be deployed into a Virtual WAN hub (custom DNS VMs or Azure DNS Private Resolver, Active Directory Domain Services [AD DS] domain controllers, Azure Bastion, and other shared resources).
- Workload VNets with Azure Application Gateway, Azure web application firewall (WAF) and Private Endpoints if required.

Azure Virtual WAN supports the integration of a limited set of [third party firewalls](/azure/virtual-wan/about-nva-hub) inside its hubs as an alternative to native Azure Firewall. For this article, we will only refer to Azure Firewall. What is included in the **Vnet-Shared Services** spoke in the reference architecture is just an example of what you could deploy. Azure Virtual WAN hubs are managed by Microsoft and nothing can be installed in there except what is explicitly allowed by Azure Firewall and [supported NVAs](/azure/virtual-wan/virtual-wan-locations-partners#partners-with-integrated-virtual-hub-offerings).

This reference architecture aligns to the architectural principles described in the Cloud Adoption Framework article for [Virtual WAN network topology](/azure/cloud-adoption-framework/ready/azure-best-practices/virtual-wan-network-topology).

## Routing Security

Securing route propagation and isolation of on-premises environment is a critical security aspect that must be managed.

Other than traffic segmentation, routing security is a critical part of any network security design. Routing protocols are an integral part of most networks, including Azure. However, there are inherent risks to routing protocols such as misconfigurations or malicious attacks, and you need to protect your infrastructure from those as well. The BGP protocol used for [VPN](/azure/vpn-gateway/vpn-gateway-bgp-overview) or [ExpressRoute](/azure/expressroute/expressroute-routing#dynamic-route-exchange) offers very rich possibilities of protecting your network against undesired routing changes, that might include the advertisement of too specific routes or too broad routes. The best way of using these mechanism is configuring on your on-premises devices appropriate [route policies](/azure/expressroute/expressroute-config-samples-routing#route-policies) and [route maps](/azure/expressroute/expressroute-config-samples-routing#route-maps) to make sure that only allowed prefixes are propagated into your network from Azure. For example:

- Block inbound prefixes that are too generic

  If due to a misconfiguration Azure starts sending generic prefixes such as 0.0.0.0/0 or 10.0.0.0/8, it could be attracting traffic that might otherwise stay in your on-premises network.

- Block inbound prefixes that are too specific

  Under certain circumstances you could get some long IPv4 prefixes from Azure (network prefix length 30 to 32), which are typically included in other less specific prefixes and hence not required. Dropping these prefixes will prevent your on-premises routing tables from growing unnecessarily large.

- Block inbound prefixes that are not in Azure, unless you are using Azure as a transit network

  If you are not using Azure to transport traffic between your on-premises locations (for example with technologies such as ExpressRoute Global Reach), an on-premises prefix being advertised from Azure would indicate a routing loop. Only taking Azure prefixes in your on-premises routers would protect you against these routing loops.

- Block outbound prefixes that are not on-premises

  For similar reasons as the previous point, if you are not using your on-premises network for transit between Azure regions, you shouldn’t be advertising to Azure any prefix that you don’t use on-premises. If you don’t do that you run into the risk of creating routing loops, especially given the fact that eBGP implementations in most routers re-advertise all prefixes on non-preferred links, having the effect of sending Azure prefixes back to Azure unless you have configured eBGP multi-path.

## Logical architecture

Virtual WAN is a collection of hubs and services made available inside the hub. You can deploy as many Virtual WANs as you need. In a Virtual WAN hub, there are multiple services such as VPN, ExpressRoute, Azure Firewall, or a third party integrated NVA. 

The following diagram shows the logical architecture of Azure infrastructure for an Azure Virtual WAN deployment as depicted in the [Cloud Adoption Framework](/azure/cloud-adoption-framework/ready/azure-best-practices/virtual-wan-network-topology).

:::image type="content" source="media/vwan/logical-arch-vwan.png" alt-text="Diagram of the components of Azure vWAN in an Azure AD tenant." lightbox="media/vwan/logical-arch-vwan.png":::

The majority of resources are contained inside the connectivity subscription. Deploy all Virtual WAN resources into a single resource group in the connectivity subscription, including when you're deploying across multiple regions. Azure VNet spokes instead, will be in the landing zone subscriptions. For Azure Firewall Policy, if policy [inheritance and hierarchy](/azure/firewall-manager/rule-hierarchy) is used, the parent policy and the child policy must be located in the same region. You can still apply a policy that was created in one region on a secured hub from another region.

## What’s in this article?

This article walks through the steps to apply the principles of Zero Trust across the Azure Virtual WAN reference architecture.

| Step | Task | Zero Trust principle(s) applied |
| --- | --- | --- |
| 1 | Create Azure Firewall policy. | Verify explicitly <br> Assume breach |
| 2 | Convert Azure Virtual WAN hubs to secured hubs. | Verify explicitly <br> Assume breach |
| 3 | Secure traffic. | Verify explicitly <br> Assume breach |
| 4 | Secure spoke VNets. | Assume breach |
| 5 | Review encryption. | Assume breach |
| 6 | Secure P2S users | Assume breach |
| 7 | Configure monitoring, auditing, and management. | Assume breach |

Steps 1 and 2 must be done in order. The other steps can be done in any order.

## Step 1. desc

TBD

## Step 2. desc

TBD

## Step 3. desc

TBD

## Step 4. desc

TBD

## Step 5. desc

TBD

## Step 6. desc

TBD

## Step 7. desc

TBD

## Recommended training

PLACEHOLDER for additional training modules

### Introduction to Azure Virtual WAN

|Training  |[Introduction to Azure Virtual WAN](/training/modules/introduction-azure-virtual-wan/)|
|---------|---------|
|:::image type="icon" source="media/introduction-to-azure-virtual-wan.svg" border="false"::: | Describe how to construct a wide area network (WAN) using software-defined Azure Virtual WAN networking services. |
> [!div class="nextstepaction"]
> [Start >]/training/modules/introduction-azure-virtual-wan/)

### title

|Training  |[title](url)|
|---------|---------|
|:::image type="icon" source="media/3-design-for-user-identities-and-profiles.svg" border="false"::: | desc |
> [!div class="nextstepaction"]
> [Start >](url)


Training SVGs:

introduction-to-azure-firewall.svg
generic-badge.svg (FW manager)
6-design-and-implement-network-security-and-monitoring.svg


For more training on security in Azure, see these resources in the Microsoft catalog:<br> 
[Security in Azure](/training/browse/?subjects=security&products=azure)

## Next Steps

See these additional articles for applying Zero Trust principles to Azure PaaS:

- [Apply Zero Trust principles to Azure PaaS overview](azure-paas-overview.md)
- [Apply Zero Trust principles to Azure Virtual Desktop](azure-infrastructure-avd.md)

See these additional articles for applying Zero Trust principles to Azure IaaS:

- [Apply Zero Trust principles to Azure infrastructure overview](azure-infrastructure-overview.md)
- [Apply Zero Trust principles to Azure storage](azure-infrastructure-storage.md)
- [Apply Zero Trust principles to virtual machines](azure-infrastructure-virtual-machines.md)
- [Apply Zero Trust principles to a spoke virtual network in Azure](azure-infrastructure-iaas.md)
- [Apply Zero Trust principles to a hub virtual network in Azure](azure-infrastructure-networking.md)

## References

Refer to the links below to learn about the various services and technologies mentioned in this article.

- [What is Azure - Microsoft Cloud Services](https://azure.microsoft.com/resources/cloud-computing-dictionary/what-is-azure/)
- [Introduction to Azure security](/azure/security/fundamentals/overview)
- [Zero Trust implementation guidance](/security/zero-trust/zero-trust-overview)
- [Overview of the Microsoft cloud security benchmark](/security/benchmark/azure/overview)
- [Security baselines for Azure overview](/security/benchmark/azure/security-baselines-overview)
- [Building the first layer of defense with Azure security services](/azure/architecture/solution-ideas/articles/azure-security-build-first-layer-defense)
- [Microsoft Cybersecurity Reference Architectures](/security/cybersecurity-reference-architecture/mcra)

PLACEHOLDER for additional links