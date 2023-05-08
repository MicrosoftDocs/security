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

:::image type="content" source="media/vwan/ref-arch-vwan.svg" alt-text="Diagram of the reference architecture for Azure Virtual Desktop." lightbox="media/vwan/ref-arch-vwan.svg":::

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

:::image type="content" source="media/vwan/logical-arch-vwan.svg" alt-text="Diagram of the components of Azure vWAN in an Azure AD tenant." lightbox="media/vwan/logical-arch-vwan.svg":::

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
| 6 | Secure P2S users. | Assume breach |
| 7 | Configure monitoring, auditing, and management. | Assume breach |

Steps 1 and 2 must be done in order. The other steps can be done in any order.

## Step 1. Create Azure Firewall policy

As for standalone Azure Firewall deployments in classic hub and spoke architecture, at least one Azure Policy must be created in Azure Firewall Manager and associated to the Azure Virtual WAN hubs. This policy must be created and made available before the conversion of any hub. Once the policy is defined, it will be applied to Azure Firewall instances in Step 2.

Azure Firewall policies can be arranged in [parent-child hierarchy](/azure/firewall-manager/rule-hierarchy). Either in a classic hub and spoke scenario or managed Azure Virtual WAN, a root policy should be defined with IT wide security-specific rules with a common set of rules to allow or deny traffic. Then, for each hub, a child policy could be defined to implement hub specific rules through inheritance. This is an optional step. If rules that must be applied to each hub are identical, a single policy can be applied.

For Zero Trust, a [Premium Azure Firewall policy](/azure/firewall/premium-features) is required and should include the following settings:

- [DNS Proxy](/azure/firewall-manager/dns-settings) – Azure Firewall should be configured as a custom DNS server for spoke VNets, thus protecting the real DNS that will reside in a shared service spoke and/or on-premises.  Azure Firewalls will act as a DNS Proxy, will listen on port 53 and will forward DNS requests to the DNS servers specified in the policy settings. For every spoke, DNS server must be configured at the virtual network level pointing to the internal IP address of the Azure Firewall in the Virtual WAN Hub. No network access should be granted from spokes and branches to the custom DNS. 

- [TLS inspection](/azure/firewall/premium-features#tls-inspection) should be enabled for the scenarios below: 

   - **Outbound TLS Inspection** to protect against malicious traffic that is sent from an internal client hosted in Azure to the Internet.

   - **East-West TLS Inspection**, including traffic that goes from/to an on-premises branches and between Virtual WAN spokes, to protect your Azure workloads from potential malicious traffic sent from within Azure.

- [IDPS](/azure/firewall/premium-features#idps) should be enabled in “Alert and Deny” mode.

- [Threat Intelligence](/azure/firewall/threat-intel) should be enabled in “Alert and Deny” mode.

As part of the policy creation, the necessary  Destination Network Address Translation (DNAT) rules, Network rules and Application rules must be created to enable only the network flows that are intended to be explicitly permitted. To enable TLS inspection for selected targets, the correspondent Application rule must have “TLS inspection” flag enabled. When creating Rules in Rules Collections, the most restrictive “Destination” and “Destination Type” should be used.


## Step 2. Convert Azure Virtual WAN hubs to secured hubs

At the core of Zero Trust approach for Azure Virtual WAN there is the concept of Secured Virtual WAN Hub (secure hub). A secure hub  is an Azure Virtual WAN hub with Azure Firewall integrated. Usage of supported [security appliances from third parties](/azure/virtual-wan/virtual-wan-locations-partners#partners-with-integrated-virtual-hub-offerings) is supported, as an alternative to Azure Firewall, but is not described in this article. These virtual appliances can be used to inspect all North-South, East-West, and Internet-bound traffic.

Usage of a Premium tier for Azure Firewall is recommended for Zero Trust. During the configuration, the Premium Policy created in Step 1 should be applied.

>[!Note]
>Usage of DDoS Protection is [not supported](/azure/firewall-manager/overview#known-issues) with Secured Virtual WAN Hub.
>

For more information, see [Install Azure Firewall in a Virtual WAN hub](/azure/virtual-wan/howto-firewall).

## Step 3. Secure traffic

Once upgraded all Azure Virtual WAN hubs to secure hubs, [Routing Intent and Policies]/azure/virtual-wan/how-to-routing-policies) must be configured to apply Zero Trust principles. This mechanism will enable the Azure Firewall in each hub to attract and inspect traffic between spokes and branches in the same hub and across remote hubs. This feature should be [configured](/azure/virtual-wan/how-to-routing-policies#azurefirewall) to send both “Internet traffic” and “Private traffic” through the Azure Firewall (or third party NVA). “Inter-hub” option must be also enabled. Here is an example.
 
:::image type="content" source="media/vwan/example-routing-policy-configuration.png" alt-text="Example of the Azure Firewall routing policy." lightbox="media/vwan/example-routing-policy-configuration.png":::

When the Private Traffic Routing Policy is enabled, VNet traffic in and out of the Virtual WAN Hub, including inter-hub traffic, will be forwarded to the next hop Azure Firewall resource or NVA resource that was specified in the policy itself. Users with enough [Role-Based Access Control (RBAC)](/azure/role-based-access-control/overview) privileges could override Virtual WAN route programming for spoke VNets and associate a custom [User Defined Route (UDR)](/azure/virtual-network/virtual-networks-udr-overview#user-defined) to bypass the hub firewall. To prevent this possibility, [RBAC permissions](/azure/virtual-network/manage-route-table#permissions) to assign UDR to spoke VNet subnets should be restricted to central network administrators and not delegated to the landing zone owners of the spoke VNets. In order to associate a UDR to a VNet or subnet, a user must have the [Network Contributor](/azure/role-based-access-control/built-in-roles?toc=/azure/virtual-network/toc.json#network-contributor) role or custom role with the required action/permission named “Microsoft.Network/routeTables/join/action”. 

>[!Note]
>In this document Azure Firewall will be primarily considered for both Internet traffic and Private traffic control. For the former, a [third party supported security NVA](/azure/virtual-wan/virtual-wan-locations-partners#partners-with-integrated-virtual-hub-offerings) can be used or [third party Security as a Service (SECaaS) provider](/azure/firewall-manager/deploy-trusted-security-partner). For the latter, [third party supported security NVA](/azure/virtual-wan/virtual-wan-locations-partners#partners-with-integrated-virtual-hub-offerings) can be used as an alternative to Azure Firewall.
>

>[!Note]
>[Custom Route Tables](/azure/virtual-wan/scenario-isolate-vnets-custom) in Azure Virtual WAN cannot be used in conjunction with Routing Intent and Policies and should not be considered as a security mechanism.
>

## Step 4. Secure spoke VNets

Each Azure Virtual WAN Hub can have one or more VNet connected through virtual network peering. According to the Cloud Adoption Framework model, every VNet contains a “landing zone” workload, applications and services supporting the organization business. Azure Virtual WAN will manage the connection, the route propagation and association, the outbound and inbound routing, but will not be able to influence “intra-VNet” security. Zero-Trust principles must be applied inside each spoke VNet according to the guidance published in this article and other articles depending on the resource type (virtual machines, storage, SQLDB, etc.). Specifically:

-	**Micro-segmentation:** even if Azure Virtual WAN will attract and filter outbound traffic, usage of Network Security Groups (NSG) and Application Security Group (ASG) to regulate intra-VNet flows is still recommended. 
-	**Local DMZ:** Inbound non-http/https traffic should be filtered and allowed by a DNAT rule created in the central firewall inside Azure Virtual WAN Hub. Inbound http/https traffic instead, should be managed by a local Azure Application Gateway and associated Web Application Firewall.

   Note that Even if Azure Virtual WAN secure virtual hubs don't support Azure DDoS Protection plans yet, usage of DDoS to protect Internet facing endpoints in spoke VNets is possible and highly recommended. For more information, see Azure Firewall Manager known issues and Hub virtual network and secured virtual hub comparison.

-	**Advanced threat detection and protection:** as explained in the in this article, what is inside the spoke must be protected using tools like Microsoft Defender for Cloud (MDC).

Because in Azure Virtual WAN the hub is locked and managed by Azure, custom components cannot be installed/enabled in there. Some resources that are normally deployed inside the hub, in a classic Hub & Spoke model, must be placed in one or more spokes that will act as shared resources networks. For example:

-	**Azure Bastion:** Usage of Azure Bastion is supported with Azure Virtual WAN but must be deployed inside a spoke virtual network since the hub is restricted and managed by Azure. From the Azure Bastion spoke, users can reach resources in other VNets, but will require IP-Based Connection available with the Standard SKU. 
-	**Custom DNS servers:** A custom DNS software can be installed inside any Virtual Machine and act as DNS server for all the spokes in Azure Virtual WAN. This resource must be installed in a spoke VNet that will serve all other spokes directly, or through DNS Proxy feature offered by the Azure Firewall integrated inside the Virtual WAN hub. 
-	**Azure Private DNS Resolver:** Deployment of this resource is supported inside one of the spoke VNets connected to Virtual WAN hubs. Azure Firewall integrated inside the Virtual WAN hub can use this resource as custom DNS when DNS Proxy featured is enabled. 
-	**Private Endpoints:** This resource type is compatible with Virtual WAN but must be deployed inside a spoke VNet. This provides connectivity to any other virtual network or branch connected to the same Virtual WAN, if the integrated Azure Firewall will allow the flow. Instructions on how to secure traffic to Private Endpoint using the Azure Firewall integrated inside Virtual WAN hub can be found in this article. 
-	**Azure Private DNS Zone (links):** This type of resources does not live inside a virtual network but must be linked to them to function correctly. Private DNS Zones cannot be linked to Virtual WAN hubs. Instead, should be connected to the spoke VNet containing the custom DNS servers or Azure Private DNS Resolver (recommended), or directly to the spoke VNets that require the DNS records from that zone. 


## Step 5. Review encryption

Azure Virtual WAN provides some traffic encryption capabilities through its own gateways, for traffic entering the Microsoft network. Whenever possible, encryption should be enabled, based on the gateway type. 

- Encryption is provided by Virtual WAN site-to-site (S2S) VPN gateway using IPsec/IKE (IKEv1 and IKEv2) VPN connection. 
- Encryption is provided by Virtual WAN point-to-site (P2S) VPN gateway using user VPN connection over OpenVPN or IPsec/IKE (IKEv2). 
- The Virtual WAN ExpressRoute gateway component does not provide encryption, therefore the same considerations from standalone ExpressRoute apply.

  - Only for ExpressRoute circuits provisioned on top of ExpressRoute Direct, it is possible to leverage platform provided MACsec encryption to secure the connections between your edge routers and Microsoft's edge routers.

  - Encryption could be established using IPsec/IKE VPN connection from your on-premises network to Azure over the private peering of an Azure ExpressRoute circuit, however this configuration is not supported yet with secured hubs.

- For third party SDWAN and NVAs integrated into Virtual WAN hub, specific encryption capabilities must be verified and configured according to the vendor documentation.

Once the traffic is entered the Azure network infrastructure through one of the above gateways or SDWAN/NVA, there is no specific Virtual WAN service or capability that will provide network encryption. Traffic between a hub and its virtual network, and hub-to-hub is un-encrypted then application-level encryption must be used if necessary.

>[!Note]
>VNet-to-VNet encryption using Azure VPN Gateway is not supported for Virtual WAN spokes since a spoke is required to use Virtual WAN hub remote gateway.
>


## Step 6. Secure P2S users

Azure Virtual WAN is a networking service that brings many networking, security, and routing functionalities together to provide a single operational interface. From a user identity perspective, the only touch point with Virtual WAN is in the authentication method used to allow user point-to-site (P2S) VPN. Several authentication methods are available, but following general Zero-Trust principles Azure Active Directory authentication is recommended. Using this method, it will be possible to enable Multi-Factor Authentication (MFA) and Conditional Access Policy, then applying Zero-Trust considerations to client devices and user identities. 

>[!Note]
>Azure AD authentication is only available for gateways that use the OpenVPN protocol, supported only for OpenVPN protocol connections and requires the Azure VPN Client.
>

Azure Virtual WAN and Azure Firewall do not provide per-user/per-group traffic routing and filtering directly, but it is possible to assign different group of users a different pool of IP addresses. Once done, it is possible to define rules on the integrated Azure Firewall to restrict users, based on their assigned P2S IP address pool.

If in the specific customer scenario is possible to divide P2S users into different groups, based on network access requirements, it is recommended to differentiate them at the network level and ensure that they can access only a subset of the internal network. This can be accomplished creating multiple pools for Azure Virtual WAN as explained in this article.


## Step 7. Configure monitoring, auditing, and management

Azure Virtual WAN provides extensive monitoring and diagnostic capabilities using Azure Monitor. Additional details and topology can be obtained using a special focused pre-built monitoring dashboard in the Azure portal called Azure Monitor Insights for Virtual WAN. These monitoring tools are not specific for security. The integration point for Zero-Trust and security monitoring is provided through the Azure Firewall deployed inside each Virtual WAN hub. Diagnostics and logging for Azure Firewall must be configured as with normal Azure Firewalls outside Virtual WAN context. 

In Azure Firewall there are multiple monitoring tools that should be used to ensure security and correct implementation of Zero-Trust principle: 

- Azure Firewall Policy Analytics - Policy Analytics provides insights, centralized visibility, and control to Azure Firewall. Security does require proper firewall rules are in place and effective to protect the internal infrastructure. In the Azure Portal blade details about “Potential Malicious Sources” generated by firewall engine IDPS and Threat Intelligence features are summarized. 

- Azure Firewall Workbook - Azure Firewall Workbook provides a flexible canvas for Azure Firewall data analysis.  You can gain insights into Azure Firewall events, learn about your application, and network rules, and see statistics for firewall activities across URLs, ports, and addresses. It is highly recommended to periodically review check IDPS Log Statistics and the Investigations tab: here, check denied traffic, source and destination flows, Threat Intelligence report to eventually review and optimize firewall rules.

Azure Firewall also integrates with Microsoft Defender for Cloud and Microsoft Sentinel, both tools are highly recommended to be correctly configured and actively used for Zero-Trust:

- Microsoft Defender for Cloud – Leveraging this integration is now possible to visualize all-up status of network infrastructure and network security in one place. It provides an all-up status of Azure Network Security across all VNets and Virtual Hubs spread across different regions in Azure.  With a single glance, you can see the number of Azure Firewalls, Firewall Policies and Azure regions where Azure Firewalls are deployed.
- Microsoft Sentinel – An Azure Sentinel solution is available for seamless Azure Firewall integration providing both detection and prevention. Available from the Azure Marketplace, once deployed it will allow built-in customizable threat detection on top of Azure Sentinel. The solution contains a workbook, detections, hunting queries and playbooks.

## Training for administrators

The following training modules help your team with the skills that are necessary to implement the layers of protection required to apply Zero Trust principles to your Azure Virtual WAN deployment.

### Introduction to Azure Virtual WAN

|Training  |[Introduction to Azure Virtual WAN](/training/modules/introduction-azure-virtual-wan/)|
|---------|---------|
|:::image type="icon" source="media/vwan/introduction-to-azure-virtual-wan.svg" border="false"::: | Describe how to construct a wide area network (WAN) using software-defined Azure Virtual WAN networking services. |
> [!div class="nextstepaction"]
> [Start >](/training/modules/introduction-azure-virtual-wan/)

### Introduction to Azure Firewall

|Training  |[Introduction to Azure Firewall](/training/modules/introduction-azure-firewall/)|
|---------|---------|
|:::image type="icon" source="media/vwan/introduction-to-azure-firewall.svg" border="false"::: | Describe how Azure Firewall protects Azure VNet resources, including the Azure Firewall features, rules, deployment options, and administration with Azure Firewall Manager. |
> [!div class="nextstepaction"]
> [Start >](/training/modules/introduction-azure-firewall/)

### Introduction to Azure Firewall Manager

|Training  |[Introduction to Azure Firewall Manager](/training/modules/intro-to-azure-firewall-manager/)|
|---------|---------|
|:::image type="icon" source="media/vwan/introduction-to-azure-firewall-manager.svg" border="false"::: | Describe whether you can use Azure Firewall Manager to provide central security policy and route management for your cloud-based security perimeters. Evaluate whether Azure Firewall Manager can help secure your cloud perimeters. |
> [!div class="nextstepaction"]
> [Start >](/training/modules/intro-to-azure-firewall-manager/)

### Design and implement network security

|Training  |[Design and implement network security](/training/modules/design-implement-network-security-monitoring/)|
|---------|---------|
|:::image type="icon" source="media/vwan/design-implement-network-security.svg" border="false"::: | You will learn to design and implement network security solutions such as Azure DDoS, Network Security Groups, Azure Firewall, and Web Application Firewall. |
> [!div class="nextstepaction"]
> [Start >](/training/modules/design-implement-network-security-monitoring/)

<!---
Training SVGs:

introduction-to-azure-firewall.svg
generic-badge.svg (FW manager)
6-design-and-implement-network-security-and-monitoring.svg

--->

For more training on security in Azure, see these resources in the Microsoft catalog:<br> 
[Security in Azure](/training/browse/?subjects=security&products=azure)

## Next Steps

See these additional articles for applying Zero Trust principles to Azure IaaS:

- [Apply Zero Trust principles to Azure infrastructure overview](azure-infrastructure-overview.md)

  - [Apply Zero Trust principles to Azure storage](azure-infrastructure-storage.md)

  - [Apply Zero Trust principles to virtual machines](azure-infrastructure-virtual-machines.md)

  - [Apply Zero Trust principles to a spoke virtual network in Azure](azure-infrastructure-iaas.md)

  - [Apply Zero Trust principles to a hub virtual network in Azure](azure-infrastructure-networking.md)

- [Apply Zero Trust principles to Azure Virtual Desktop](azure-infrastructure-avd.md)
- [Secure AWS applications with Azure](secure-iaas-apps.md)

## References

Refer to the links below to learn about the various services and technologies mentioned in this article.

- [What is Azure - Microsoft Cloud Services](https://azure.microsoft.com/resources/cloud-computing-dictionary/what-is-azure/)


- [Security baselines for Azure overview](/security/benchmark/azure/security-baselines-overview)

### Azure Virtual WAN

- Azure Virtual WAN Overview
- How to configure Virtual WAN Hub routing policies 
- Install Azure Firewall in a Virtual WAN hub 
- What is a secured virtual hub?
- How to configure Virtual WAN Hub routing policies 
- Tutorial: Secure your virtual hub using Azure Firewall Manager
- Tutorial: Secure your virtual hub using Azure PowerShell
- Share a private link service across Virtual WAN 
- Manage secure access to resources in spoke VNets for P2S clients 

### Security baselines

- Azure Firewall
- Azure Firewall Manager

### Well-Architected Framework review

- Azure Firewall

### Azure security

- [Introduction to Azure security](/azure/security/fundamentals/overview)
- [Zero Trust implementation guidance](/security/zero-trust/zero-trust-overview)
- [Overview of the Microsoft cloud security benchmark](/security/benchmark/azure/overview)
- [Building the first layer of defense with Azure security services](/azure/architecture/solution-ideas/articles/azure-security-build-first-layer-defense)
- [Microsoft Cybersecurity Reference Architectures](/security/cybersecurity-reference-architecture/mcra)

## Technical illustrations

You can download the illustrations used in this series of articles. Use the Visio file to modify these illustrations for your own use.

PDF | Visio
