---
title: Apply Zero Trust principles to Azure Virtual WAN
description: Learn how to secure an Azure Virtual WAN deployment with Zero Trust principles. 
ms.date: 02/12/2024
ms.service: security
author: sikovatc
ms.author: sikovatc
ms.topic: conceptual
ms.collection: 
  - msftsolution-azurepaas
  - msftsolution-scenario
  - zerotrust-solution
  - zerotrust-azure
---

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

# Apply Zero Trust principles to an Azure Virtual WAN deployment

With the modern cloud, mobile devices, and other endpoints evolution, relying only on corporate firewalls and perimeter networks is no longer sufficient. An end-to-end Zero Trust strategy assumes that security breaches are inevitable. That means you must verify each request as if it originates from an uncontrolled network. Networking still plays an important role in Zero Trust to connect and protect infrastructure, applications, and data. In the Zero Trust model, there are three key objectives when it comes to securing your networks:

- Be ready to handle attacks before they happen.
- Minimize the extent of the damage and how fast it spreads.
- Increase the difficulty of compromising your cloud footprint.

Azure Virtual WAN allows a [global transit network architecture](/azure/virtual-wan/virtual-wan-global-transit-network-architecture#globalnetworktransit) by enabling ubiquitous, any-to-any connectivity between globally distributed sets of cloud workloads in virtual networks (VNets), branch sites, SaaS and PaaS applications, and users. Adopting a Zero Trust approach in Azure Virtual WAN is critical to ensure that your backbone is secure and protected. 

This article provides steps to apply the [principles of Zero Trust](zero-trust-overview.md#guiding-principles-of-zero-trust) to an Azure Virtual WAN deployment in the following ways:

| Zero Trust principle | Definition | Met by |
| --- | --- | --- |
| Verify explicitly |Always authenticate and authorize based on all available data points. | Use Azure Firewall with Transport Layer Security (TLS) inspection to verify risk and threats based on all available data. Conditional Access controls are intended to provide authentication and authorization by diverse data points and the Azure Firewall doesn't perform user authentication. |
| Use least privileged access |  Limit user access with Just-In-Time and Just-Enough-Access (JIT/JEA), risk-based adaptive policies, and data protection. | User access is beyond the scope of Azure network infrastructure deployments. Using Identity pillar solutions like Privileged Access Management, Conditional Access, and other controls are the way to deliver on this principle. |
| Assume breach | Minimize blast radius and segment access. Verify end-to-end encryption and use analytics to get visibility, drive threat detection, and improve defenses. | Each spoke VNet has no access to other spoke VNets unless the traffic gets routed through the firewall integrated inside each Azure Virtual WAN hub. The firewall is set to deny by default, allowing only traffic allowed by specified rules. In the event of a compromise or breach of one application/workload, it has limited ability to spread due to the Azure Firewall performing traffic inspection and only forwarding allowed traffic. Only resources in the same workload are exposed to the breach in the same application. |

For more information about how to apply the principles of Zero Trust across an Azure IaaS environment, see the [Apply Zero Trust principles to Azure infrastructure overview](azure-infrastructure-overview.md).

For an industry discussion of Zero Trust, see [NIST Special Publication 800-207](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-207.pdf).

## Azure Virtual WAN

Azure Virtual WAN is a networking service that brings many networking, security, and routing functionalities together to provide a single operational interface. Some of the main features include:

- Advanced routing features
- Security "bump-in-the-wire" integration through Azure Firewall or supported Network Virtual Appliances (NVAs) in the hub
- Encrypted ExpressRoute

A Zero Trust approach for Azure Virtual WAN requires configuration of several underlying services and components from the Zero Trust principle table previously listed. Here's a list of steps and actions:

- Deploy Azure Firewall or [supported Next Generation Firewall (NGFW)](/azure/virtual-wan/virtual-wan-locations-partners#partners-with-integrated-virtual-hub-offerings) NVAs inside each Virtual WAN hub.
- Configure inter-VNet and on-premises branch routing to create a Zero Trust environment by sending all traffic to security appliances in the hubs for inspection. Configure the routing to provide filtering and protection for known threats.
- Ensure that no resources in the spokes have direct access to the Internet.
- Provide application micro-segmentation in spoke networks, along with an ingress/egress micro-perimeters strategy.
- Provide observability for network security events.

## Reference architecture

The following diagram shows a common reference architecture that demonstrates a commonly deployed environment and how to apply the principles of Zero Trust to Azure Virtual WAN.

:::image type="content" source="media/vwan/ref-arch-vwan.svg" alt-text="Diagram of the reference architecture for Azure Virtual Desktop." lightbox="media/vwan/ref-arch-vwan.svg":::

Azure Virtual WAN is deployable in [Basic and Standard types](/azure/virtual-wan/virtual-wan-about#basicstandard). Applying Zero Trust principles for Azure Virtual WAN with Azure Firewall or an NGFW requires the Standard type.

The Azure Virtual WAN with secured hubs reference architecture includes:

- A single logical Virtual WAN.
- Two secured virtual hubs, one per region.
- An instance of Azure Firewall Premium deployed in each hub.
- At least one Azure Firewall [Premium policy](/azure/firewall-manager/policy-overview#basic-standard-and-premium-policies).
- Point-to-site (P2S) and site-to-site (S2S) VPN and ExpressRoute gateways.
- P2S, S2S, and ExpressRoute-connected branches.
- A shared services VNet containing core infrastructure resources that can't be deployed into a Virtual WAN hub, such as custom DNS VMs or Azure DNS Private Resolver, Active Directory Domain Services [AD DS] domain controllers, Azure Bastion, and other shared resources.
- Workload VNets with Azure Application Gateway, Azure web application firewall (WAF), and Private Endpoints if needed.

Azure Virtual WAN supports the integration of a limited set of [third party firewalls](/azure/virtual-wan/about-nva-hub) inside its hubs as an alternative to native Azure Firewall. This article only describes Azure Firewall. What is included in the **VNet-Shared Services** spoke in the reference architecture is just an example of what you could deploy. Microsoft manages Azure Virtual WAN hubs and you can't install anything else within them except what Azure Firewall and supported NVAs explicitly allow.

This reference architecture aligns to the architectural principles described in the Cloud Adoption Framework article for [Virtual WAN network topology](/azure/cloud-adoption-framework/ready/azure-best-practices/virtual-wan-network-topology).

## Routing Security

Securing route propagation and isolation of on-premises environment is a critical security element that must be managed.

Other than traffic segmentation, routing security is a critical part of any network security design. Routing protocols are an integral part of most networks, including Azure. You need to protect your infrastructure from the inherent risks to routing protocols such as misconfigurations or malicious attacks. The BGP protocol used for [VPN](/azure/vpn-gateway/vpn-gateway-bgp-overview) or [ExpressRoute](/azure/expressroute/expressroute-routing#dynamic-route-exchange) offers very rich possibilities of protecting your network against undesired routing changes, which might include the advertisement of too specific routes or too broad routes.

The best way protect your network is configure your on-premises devices with appropriate [route policies](/azure/expressroute/expressroute-config-samples-routing#route-policies) and [route maps](/azure/expressroute/expressroute-config-samples-routing#route-maps) to make sure that only allowed prefixes are propagated into your network from Azure. For example, you can:

- Block inbound prefixes that are too generic.

  If due to a misconfiguration Azure starts sending generic prefixes such as 0.0.0.0/0 or 10.0.0.0/8, it could be attracting traffic that might otherwise stay in your on-premises network.

- Block inbound prefixes that are too specific.

  Under certain circumstances you could get some long IPv4 prefixes from Azure (network prefix length 30 to 32), which are typically included in other less specific prefixes and therefore not required. Dropping these prefixes prevents your on-premises routing tables from growing unnecessarily large.

- Block inbound prefixes that aren't in Azure unless you're using Azure as a transit network.

  If you aren't using Azure to transport traffic between your on-premises locations (for example, with technologies such as ExpressRoute Global Reach), an on-premises prefix being advertised from Azure would indicate a routing loop. Only taking Azure prefixes in your on-premises routers would protect you from these types of routing loops.

- Block outbound prefixes that aren't on-premises.

  If you aren't using your on-premises network for transit between Azure regions, you shouldn’t be advertising to Azure any prefix that you don’t use on-premises. If you don’t, you run into the risk of creating routing loops, especially given the fact that eBGP implementations in most routers re-advertise all prefixes on non-preferred links. This has the effect of sending Azure prefixes back to Azure unless you have configured eBGP multi-path.

## Logical architecture

Azure Virtual WAN is a collection of hubs and services made available inside a hub. You can deploy as many Virtual WANs as you need. In a Virtual WAN hub, there are multiple services such as VPN, ExpressRoute, Azure Firewall, or a third party integrated NVA.

The following diagram shows the logical architecture of Azure infrastructure for an Azure Virtual WAN deployment as depicted in the [Cloud Adoption Framework](/azure/cloud-adoption-framework/ready/azure-best-practices/virtual-wan-network-topology).

:::image type="content" source="media/vwan/logical-arch-vwan.svg" alt-text="Diagram of the components of Azure Virtual WAN topology and Azure subscriptions." lightbox="media/vwan/logical-arch-vwan.svg":::

The majority of resources are contained inside the connectivity subscription. You deploy all Virtual WAN resources into a single resource group in the connectivity subscription, including when you're deploying across multiple regions. Azure VNet spokes are in the landing zone subscriptions. If you use [inheritance and hierarchy](/azure/firewall-manager/rule-hierarchy)  Azure Firewall policy, the parent policy and the child policy must be located in the same region. You can still apply a policy that you created in one region on a secured hub from another region.

## What’s in this article?

This article walks through the steps to apply the principles of Zero Trust across the Azure Virtual WAN reference architecture.

| Step | Task | Zero Trust principle(s) applied |
| --- | --- | --- |
| 1 | Create Azure Firewall policy. | Verify explicitly <br> Assume breach |
| 2 | Convert your Azure Virtual WAN hubs to secured hubs. | Verify explicitly <br> Assume breach |
| 3 | Secure your traffic. | Verify explicitly <br> Assume breach |
| 4 | Secure your spoke VNets. | Assume breach |
| 5 | Review your use of encryption. | Assume breach |
| 6 | Secure your P2S users. | Assume breach |
| 7 | Configure monitoring, auditing, and management. | Assume breach |

You must do Steps 1 and 2 in order. The other steps can be done in any order.

## Step 1: Create Azure Firewall policy

For standalone Azure Firewall deployments in a classic hub and spoke architecture, at least one Azure policy must be created in Azure Firewall Manager and associated to the Azure Virtual WAN hubs. This policy must be created and made available before the conversion of any hub. Once the policy is defined, it's applied to Azure Firewall instances in [Step 2](#step-2-convert-your-azure-virtual-wan-hubs-to-secured-hubs).

Azure Firewall policies can be arranged in a [parent-child hierarchy](/azure/firewall-manager/rule-hierarchy). For either a classic hub and spoke scenario or a managed Azure Virtual WAN, you should define a root policy with a common set of IT-wide security rules to allow or deny traffic. Then, for each hub, a child policy could be defined to implement hub-specific rules through inheritance. This step is optional. If rules that must be applied to each hub are identical, a single policy can be applied.

For Zero Trust, a [Premium Azure Firewall policy](/azure/firewall/premium-features) is required and should include the following settings:

- [DNS Proxy](/azure/firewall-manager/dns-settings) – You should configure Azure Firewall as a custom DNS server for spoke VNets that protect the real DNS that resides in a shared service spoke or on-premises. Azure firewalls act as a DNS Proxy, listen on UDP port 53, and forward DNS requests to the DNS servers specified in the policy settings. For every spoke, you must configure a DNS server at the virtual network level pointing to the internal IP address of the Azure Firewall in the Virtual WAN Hub. You shouldn't grant network access from spokes and branches to the custom DNS.

- [TLS inspection](/azure/firewall/premium-features#tls-inspection) should be enabled for these scenarios:

  - **Outbound TLS Inspection** to protect against malicious traffic that is sent from an internal client hosted in Azure to the Internet.

  - **East-West TLS Inspection** to include traffic that goes to or from on-premises branches and between Virtual WAN spokes, which protects your Azure workloads from potential malicious traffic sent from within Azure.

- [Intrusion detection and prevention system (IDPS)](/azure/firewall/premium-features#idps) should be enabled in "Alert and Deny" mode.

- [Threat Intelligence](/azure/firewall/threat-intel) should be enabled in "Alert and Deny" mode.

As part of the policy creation, you must create the necessary Destination Network Address Translation (DNAT) rules, network rules, and application rules to enable only the network flows for explicitly permitted traffic. To enable TLS inspection for selected targets, the corresponding application rule must have "TLS inspection" setting enabled. When creating rules in Rules Collections, you should use the most restrictive "Destination" and "Destination Type".

## Step 2: Convert your Azure Virtual WAN hubs to secured hubs

At the core of Zero Trust approach for Azure Virtual WAN  is the concept of Secured Virtual WAN hub (secure hub). A secure hub is an Azure Virtual WAN hub with an integrated Azure Firewall. Usage of supported security appliances from third parties is supported as an alternative to Azure Firewall but isn't described in this article. You can use these virtual appliances to inspect all North-South, East-West, and Internet-bound traffic.

We recommend Azure Firewall Premium for Zero Trust and that you configure it with the Premium Policy described in [Step 1](#step-1-create-azure-firewall-policy).

>[!Note]
>Usage of DDoS Protection is [not supported](/azure/firewall-manager/overview#known-issues) with a secure hub.
>

For more information, see [Install Azure Firewall in a Virtual WAN hub](/azure/virtual-wan/howto-firewall).

## Step 3: Secure your traffic

Once you've upgraded all your Azure Virtual WAN hubs to secure hubs, you must configure [Routing Intent and Policies](/azure/virtual-wan/how-to-routing-policies) for Zero Trust principles. This configuration enables the Azure Firewall in each hub to attract and inspect traffic between spokes and branches in the same hub and across remote hubs. You should configure your policies to send both "Internet traffic" and "Private traffic" through the Azure Firewall or your third party NVA). The "Inter-hub" option must be also enabled. Here's an example.
 
:::image type="content" source="media/vwan/example-routing-policy-configuration.png" alt-text="Example of the Azure Firewall routing policy." lightbox="media/vwan/example-routing-policy-configuration.png":::

When the "Private Traffic" routing policy is enabled, VNet traffic in and out of the Virtual WAN Hub, including inter-hub traffic, is forwarded to the next-hop Azure Firewall or NVA that was specified in the policy. Users with [Role-Based Access Control (RBAC)](/azure/role-based-access-control/overview) privileges could override Virtual WAN route programming for spoke VNets and associate a custom [User Defined Route (UDR)](/azure/virtual-network/virtual-networks-udr-overview#user-defined) to bypass the hub firewall. To prevent this vulnerability, [RBAC permissions](/azure/virtual-network/manage-route-table#permissions) to assign UDRs to spoke VNet subnets should be restricted to central network administrators and not delegated to the landing zone owners of the spoke VNets. To associate a UDR with a VNet or subnet, a user must have the **Network Contributor** role or a custom role with the "Microsoft.Network/routeTables/join/action" action or permission.

>[!Note]
>In this article, Azure Firewall is primarily considered for both Internet traffic and private traffic control. For Internet traffic, a third party, supported security NVA can be used or a [third party Security as a Service (SECaaS) provider](/azure/firewall-manager/deploy-trusted-security-partner). For private traffic, third party supported security NVAs can be used as an alternative to Azure Firewall.
>

>[!Note]
>[Custom Route Tables](/azure/virtual-wan/scenario-isolate-vnets-custom) in Azure Virtual WAN can't be used in conjunction with Routing Intent and Policies and should not be considered as a security option.
>

## Step 4: Secure your spoke VNets

Each Azure Virtual WAN hub can have one or more VNets [connected](/azure/virtual-wan/virtual-wan-site-to-site-portal#vnet) with VNet peering. Based on the [landing zone](/azure/cloud-adoption-framework/ready/landing-zone/) model in the Cloud Adoption Framework, every VNet contains a landing zone workload, applications, and services supporting an organization. Azure Virtual WAN manages the connection, the route propagation and association, and the outbound and inbound routing, but can't affect intra-VNet security. Zero Trust principles must be applied inside each spoke VNet according to the guidance published in [Apply Zero Trust principles to a spoke virtual network](azure-infrastructure-iaas.md) and other articles depending on the resource type, such as virtual machines and storage. Consider the following elements:

- **Micro-segmentation:** Even if Azure Virtual WAN attracts and filters outbound traffic, use of [network security groups (NSGs)](/azure/virtual-network/security-overview) and [application security groups (ASGs)](/azure/virtual-network/application-security-groups) to regulate intra-VNet flows is still recommended. 
- **Local DMZ:** A DNAT rule created in the central firewall inside the Azure Virtual WAN Hub should filter and allow inbound non-http or https traffic. Inbound http or https traffic should be managed by a local [Azure Application Gateway and associated Web Application Firewall](/azure/active-directory/app-proxy/application-proxy-application-gateway-waf).

   Although Azure Virtual WAN secure virtual hubs don't support [Azure DDoS Protection](/azure/ddos-protection/ddos-protection-overview) yet, usage of DDoS to protect Internet-facing endpoints in spoke VNets is possible and highly recommended. For more information, see [Azure Firewall Manager known](/azure/firewall-manager/overview#known-issues) issues and [Hub virtual network and secured virtual hub comparison](/azure/firewall-manager/vhubs-and-vnets#comparison).

- **Advanced threat detection and protection:** See [Apply Zero Trust principles to a spoke virtual network](azure-infrastructure-iaas.md). The elements inside the spoke must be protected with threat protection tools like Microsoft Defender for Cloud.

Because the hub in Azure Virtual WAN is locked and managed by Azure, custom components can't be installed or enabled there. Some resources that are normally deployed inside the hub, in a classic hub and spoke model, must be placed in one or more spokes that acts as shared resource networks. For example:

- **Azure Bastion:** [Azure Bastion](/azure/bastion/vnet-peering) supports Azure Virtual WAN but must be deployed inside a spoke virtual network because the hub is restricted and managed by Azure. From the Azure Bastion spoke, users can reach resources in other VNets, but requires [IP-based connection](/azure/bastion/connect-ip-address) available with the Azure Bastion Standard SKU. 
- **Custom DNS servers:** DNS server software can be installed on any virtual machine and act as DNS server for all the spokes in Azure Virtual WAN. The DNS server must be installed in a spoke VNet that serves all other spokes directly, or through DNS Proxy feature offered by the Azure Firewall that is integrated inside the Virtual WAN hub. 
- **Azure Private DNS Resolver:** Deployment of an [Azure Private DNS Resolver](/azure/dns/dns-private-resolver-overview) is supported inside one of the spoke VNets connected to Virtual WAN hubs. Azure Firewall that is integrated inside the Virtual WAN hub can use this resource as a custom DNS when you enable the DNS Proxy feature. 
- **Private Endpoints:** This resource type [is compatible](/azure/virtual-wan/howto-private-link) with Virtual WAN but must be deployed inside a spoke VNet. This provides connectivity to any other virtual network or branch connected to the same Virtual WAN, if the integrated Azure Firewall allows the flow. Instructions on how to secure traffic to Private Endpoints using the Azure Firewall integrated inside a Virtual WAN hub can be found in [Secure traffic destined to private endpoints in Azure Virtual WAN](/azure/firewall-manager/private-link-inspection-secure-virtual-hub).
- **Azure Private DNS Zone (links):** This type of resource doesn't live inside a virtual network but must be [linked](/azure/dns/private-dns-virtual-network-links) to them to function correctly. Private DNS Zones can't be linked to Virtual WAN hubs. Instead, they should be connected to the spoke VNet containing custom DNS servers or an Azure Private DNS Resolver ([recommended](/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances)) or directly to the spoke VNets that require the DNS records from that zone.

## Step 5: Review your encryption

Azure Virtual WAN provides some traffic encryption capabilities through its own gateways for traffic entering the Microsoft network. Whenever possible, encryption should be enabled, based on the gateway type. Consider the following default encryption behavior:

- Virtual WAN S2S VPN gateway provides encryption when using [IPsec/IKE](/azure/virtual-wan/virtual-wan-site-to-site-portal) (IKEv1 and IKEv2) VPN connection. 
- Virtual WAN P2S VPN gateway provides encryption when using [user VPN connection over OpenVPN or IPsec/IKE (IKEv2)](/azure/virtual-wan/virtual-wan-point-to-site-portal). 
- The Virtual WAN ExpressRoute gateway doesn't provide encryption, therefore the same considerations from standalone ExpressRoute apply.

  - Only for ExpressRoute circuits that are provisioned on top of [ExpressRoute Direct](/azure/expressroute/expressroute-erdirect-about), it's possible to leverage platform-provided [MACsec encryption](/azure/expressroute/expressroute-howto-macsec) to secure the connections between your edge routers and Microsoft's edge routers.

  - Encryption could be established using an [IPsec/IKE VPN connection](/azure/virtual-wan/vpn-over-expressroute) from your on-premises network to Azure over the private peering of an Azure ExpressRoute circuit. Routing Intent and Policies now supports this configuration with additional configuration steps required, as explained in [Encrypted ExpressRoute](/azure/virtual-wan/how-to-routing-policies#encryptedER). 

- For third party [Software-Defined WAN (SD-WAN) devices and NVAs](/azure/virtual-wan/about-nva-hub) integrated into Virtual WAN hub, specific encryption capabilities must be verified and configured according to the vendor's documentation.

Once the traffic has entered the Azure network infrastructure through one of the gateways or an SD-WAN/NVA, there's no specific Virtual WAN service or capability that provides network encryption. If traffic between a hub and its virtual network and hub-to-hub is unencrypted, you must use application-level encryption if needed.

>[!Note]
>Virtual WAN spokes doesn't support VNet-to-VNet encryption using Azure VPN Gateway because a spoke is required to use Virtual WAN hub remote gateway.
>

## Step 6: Secure your P2S users

Azure Virtual WAN is a networking service that brings many networking, security, and routing functionalities together to provide a single operational interface. From a user identity perspective, the only touch point with Virtual WAN is in the authentication method used to allow a [user P2S VPN](/azure/virtual-wan/virtual-wan-point-to-site-portal). Several [authentication methods](/azure/virtual-wan/virtual-wan-point-to-site-portal#p2sconfig) are available, but we recommend following general Zero Trust principles [Microsoft Entra authentication](/azure/virtual-wan/virtual-wan-point-to-site-azure-ad). With Microsoft Entra ID, you can require [Multi-Factor Authentication (MFA) and Conditional Access](/azure/virtual-wan/openvpn-azure-ad-mfa) apply Zero Trust principles to client devices and user identities.

>[!Note]
>Microsoft Entra authentication is only available for gateways that use the OpenVPN protocol, which is supported only for OpenVPN protocol connections and requires the Azure VPN Client.
>

Azure Virtual WAN and Azure Firewall don't provide traffic routing and filtering based on user account or group names, but it's possible to [assign different groups of users different pools of IP addresses](/azure/virtual-wan/user-groups-about). You can then define rules on the integrated Azure Firewall to restrict users or groups based on their assigned P2S IP address pool.

If you divide your P2S users into different groups based on network access requirements, we recommend that you differentiate them at the network level and ensure that they can access only a subset of the internal network. You can create multiple IP address pools for Azure Virtual WAN. For more information, see [Configure user groups and IP address pools for P2S User VPNs](/azure/virtual-wan/user-groups-create).

## Step 7: Configure monitoring, auditing, and management

Azure Virtual WAN provides extensive monitoring and diagnostic capabilities with [Azure Monitor](/azure/virtual-wan/monitor-virtual-wan). Additional details and topology can be obtained using a focused, prebuilt, monitoring dashboard in the Azure portal named [Azure Monitor Insights for Virtual WAN](/azure/virtual-wan/azure-monitor-insights). These monitoring tools aren't security specific. The Azure Firewall deployed inside each Virtual WAN hub provides the integration point for Zero Trust and security monitoring. You must configure [Diagnostics and logging for Azure Firewall](/azure/virtual-wan/monitor-virtual-wan-reference#azure-firewall) the same as Azure Firewalls outside Virtual WAN.

Azure Firewall provides the following monitoring tools that you should use to ensure security and correct application of Zero Trust principles:

- [Azure Firewall Policy Analytics](/azure/firewall/policy-analytics) provide insights, centralized visibility, and control to Azure Firewall. Security does require that proper firewall rules are in place and effective to protect the internal infrastructure. The Azure Portal summarizes details about "Potential Malicious Sources" generated by firewall engine IDPS and Threat Intelligence features.

- [Azure Firewall Workbook](/azure/firewall/firewall-workbook) provides a flexible canvas for Azure Firewall data analysis. You can gain insights into Azure Firewall events, learn about your application, and network rules, and see statistics for firewall activities across URLs, ports, and addresses. We highly recommend that you periodically review check [IDPS Log Statistics](/azure/firewall/firewall-workbook#idps-log-statistics) and from the **Investigations** tab, check denied traffic, source and destination flows, and the Threat Intelligence report to review and optimize firewall rules.

Azure Firewall also integrates with [Microsoft Defender for Cloud](/azure/defender-for-cloud/defender-for-cloud-introduction) and [Microsoft Sentinel](https://azure.microsoft.com/services/azure-sentinel/). We highly recommend that you correctly configure both tools and actively use them for Zero Trust in the following ways:

- With Microsoft Defender for Cloud [integration](https://techcommunity.microsoft.com/t5/microsoft-defender-for-cloud/azure-network-security-using-microsoft-defender-for-cloud/ba-p/2228222), you can visualize the all-up status of network infrastructure and network security in one place, including Azure Network Security across all VNets and Virtual Hubs spread across different regions in Azure. With a single glance, you can see the number of Azure Firewalls, firewall policies, and Azure regions where Azure Firewalls are deployed.
- A Microsoft Sentinel [solution](https://www.microsoft.com/security/blog/2021/06/08/optimize-security-with-azure-firewall-solution-for-azure-sentinel/) for seamless Azure Firewall integration provides threat detection and prevention. Once deployed, the solution allows built-in customizable threat detection on top of Microsoft Sentinel. The solution also includes a [workbook, detections, hunting queries and playbooks](https://techcommunity.microsoft.com/t5/azure-network-security-blog/new-detections-hunting-queries-and-response-automation-in-azure/ba-p/2688746).

## Training for administrators

The following training modules help your team with the skills necessary to apply Zero Trust principles to your Azure Virtual WAN deployment.

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

For more training on security in Azure, see these resources in the Microsoft catalog:<br> 
[Security in Azure](/training/browse/?subjects=security&products=azure)

## Next Steps

See these additional articles for applying Zero Trust principles to Azure:

- [Azure IaaS overview](azure-infrastructure-overview.md)
  - [Azure storage](azure-infrastructure-storage.md)
  - [Virtual machines](azure-infrastructure-virtual-machines.md)
  - [Spoke virtual networks](azure-infrastructure-iaas.md)
  - [Hub virtual networks](azure-infrastructure-networking.md)
- [Azure Virtual Desktop](azure-infrastructure-avd.md)
- [IaaS applications in Amazon Web Services](secure-iaas-apps.md)
- [Microsoft Sentinel and Microsoft Defender XDR](/security/operations/siem-xdr-overview)

## References

Refer to these links to learn about the various services and technologies mentioned in this article.

### Azure Virtual WAN

- [Azure Virtual WAN overview](/azure/virtual-wan/virtual-wan-about)
- [How to configure Virtual WAN hub routing policies](/azure/virtual-wan/how-to-routing-policies)
- [Install Azure Firewall in a Virtual WAN hub](/azure/virtual-wan/howto-firewall)
- [What is a secured virtual hub?](/azure/firewall-manager/secured-virtual-hub)
- [How to configure Virtual WAN hub routing policies](/azure/virtual-wan/how-to-routing-policies)
- [Tutorial: Secure your virtual hub using Azure Firewall Manager](/azure/firewall-manager/secure-cloud-network)
- [Tutorial: Secure your virtual hub using Azure PowerShell](/azure/firewall-manager/secure-cloud-network-powershell)
- [Share a private link service across Virtual WAN](/azure/virtual-wan/howto-private-link)
- [Manage secure access to resources in spoke VNets for P2S clients](/azure/virtual-wan/manage-secure-access-resources-spoke-p2s)

### Security baselines

- [Azure Firewall](/security/benchmark/azure/baselines/firewall-security-baseline)
- [Azure Firewall Manager](/security/benchmark/azure/baselines/azure-firewall-manager-security-baseline)

### Well-Architected Framework review

- [Azure Firewall](/azure/architecture/framework/services/networking/azure-firewall)

### Azure security

- [Introduction to Azure security](/azure/security/fundamentals/overview)
- [Zero Trust implementation guidance](zero-trust-overview.md)
- [Overview of the Microsoft cloud security benchmark](/security/benchmark/azure/overview)
- [Building the first layer of defense with Azure security services](/azure/architecture/solution-ideas/articles/azure-security-build-first-layer-defense)
- [Microsoft Cybersecurity Reference Architectures](/security/cybersecurity-reference-architecture/mcra)

## Technical illustrations

You can download the illustrations used in this article. Use the Visio file to modify these illustrations for your own use.

[PDF](https://download.microsoft.com/download/1/e/f/1ef1ad20-138e-419d-b30d-7f20811ef923/apply-zero-trust-to-Azure-vWAN-diagrams.pdf) | [Visio](https://download.microsoft.com/download/1/e/f/1ef1ad20-138e-419d-b30d-7f20811ef923/apply-zero-trust-to-Azure-vWAN-diagrams.vsdx)
