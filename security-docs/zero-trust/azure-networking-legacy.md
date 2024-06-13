---
title: Apply Zero Trust principles to discontinue legacy network security technology
description: Learn how to apply Zero Trust principles to discontinue legacy network security technology.
ms.date: 06/13/2024
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

# Apply Zero Trust principles to discontinue legacy network security technology

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
| Assume breach | Minimize blast radius and segment access. Verify end-to-end encryption and use analytics to get visibility, drive threat detection, and improve defenses. <br><br> Improve defenses for your network by removing or upgrading your legacy network services for higher levels of security. |

This article is a part of a [series of articles](azure-networking-overview.md) that demonstrate how to apply the principles of Zero Trust to Azure networking.

The Azure networking areas to review to discontinue the use of legacy network security technologies are:

- Networking foundation services
- Hybrid connectivity services
- Load balancing and content delivery services

The transition away from using legacy network security technologies can prevent an attacker from accessing environments or moving across them to inflict additional damage (the Assume breach Zero Trust principle).

## Reference architecture

The following diagram shows the reference architecture for this Zero Trust guidance for discontinuing legacy network security technology for users and admins on-premises or on the Internet and components in the Azure environment for the steps described in this article.

:::image type="content" source="media/azure-networking/azure-networking-legacy-reference-architecture.svg" alt-text="Diagram showing the reference architecture for discontinuing legacy network security technology with Azure networking components." lightbox="media/azure-networking/azure-networking-legacy-reference-architecture.svg":::

This reference architecture includes:

- Azure IaaS workloads running on Azure virtual machines.
- Azure services.
- A security virtual network (VNet) that contains an Azure VPN Gateway and Azure Application Gateway.
- An Internet edge VNet that contains an Azure Load Balancer and Azure Front Door.
- An Azure ExpressRoute circuit.

## What's in this article?

Zero Trust principles are applied across the reference architecture, from users and admins on the Internet or your on-premises network to and within the Azure cloud. The following table describes the recommendations for discontinuing legacy network security technology across this architecture for the Assume breach Zero Trust principle.

| Step | Task |
| --- | --- |
| 1 | Review your network foundations services. |
| 2 | Review your content delivery and load balancing services. |
| 3 | Review your hybrid connectivity services. |

## Step 1: Review your network foundations services

Your review of network foundation services include:

- Moving from the Basic Public IP SKU to the Standard Public IP SKU.
- Ensuring that virtual machine IP addresses are using explicit outbound access.

This diagram shows the components for updating Azure network foundation services in the reference architecture.

:::image type="content" source="media/azure-networking/azure-networking-legacy-step-1.svg" alt-text="Diagram showing the components for updating Azure network foundation services." lightbox="media/azure-networking/azure-networking-legacy-step-1.svg":::

### Basic Public IP SKU

IP addresses (public and private) are part of the IP services in Azure that enable communication among private and public resources. Public IPs are linked to services like VNet gateways, application gateways, and others that need outbound connectivity to the Internet. Private IPs enable communication between Azure resources internally. 

The Basic Public IP SKU is seen as legacy today and has more limitations than Standard Public IP SKU. One of the major limitations for Zero trust for the Basic Public IP SKU is that the use of network security groups is not required but recommended, while it is mandatory with the Standard Public IP SKU.

Another important feature for the Standard Public IP SKU is the ability to select a Routing Preference, such as routing through the Microsoft global network. This feature secures traffic within the Microsoft backbone network whenever possible and outbound traffic exits as close to the service or end-user as possible.

For more information, see [Azure Virtual Network IP Services](/azure/virtual-network/ip-services/ip-services-overview).

### Default outbound access

By default, Azure provides outbound access to the Internet. This means that connectivity from the resources is granted by default by the system routes and by the default outbound rules for the network security groups in place. In other words, if no explicit outbound connectivity method is configured, Azure configures a default outbound access IP address. However, without explicit outbound access, certain security risks arise.

Microsoft recommends that you do not leave a virtual machine IP address open to Internet traffic. There is no control over the default outbound IP access and IP addresses, along with their dependencies, can change. For virtual machines equipped with multiple network interface cards (NICs), it is not recommended to allow all NIC IP addresses to have Internet outbound access. Instead, you should restrict access to the necessary NICs.

Microsoft recommends that you set up explicit outbound access with one of the following options:

- [Azure NAT Gateway](/azure/nat-gateway/nat-overview)

  For the maximum source network address translation (SNAT) ports, Microsoft recommends Azure NAT Gateway for outbound connectivity.

- Standard SKU [Azure Load Balancers](/azure/load-balancer/load-balancer-overview)

  This requires a load balancing rule to program SNAT, which may not be as efficient as an Azure NAT Gateway.

- Restricted use of public IP addresses

  Assigning a direct public IP to a virtual machine should be done only for testing or development environments due to considerations of scalability and security.

## Step 2: Review your content delivery and load balancing services

Azure has many application delivery services that help you send and distribute traffic to your web applications. Sometimes a new version or tier of the service improves the experience and provides the latest updates. You can use the migration tool within each of the application delivery services to easily switch to the newest version of the service and benefit from new and enhanced features.

Your review of content delivery and load balancing services include:

- Migrating your [Azure Front Door](/azure/frontdoor/front-door-overview) tier from Classic to the Premium or Standard tiers.
- Migrating your [Azure Application Gateways](/azure/application-gateway/overview-v2) to WAF_v2.
- Migrating to Standard SKU Azure Load Balancer.

This diagram shows the components for updating Azure content delivery and load balancing services.

:::image type="content" source="media/azure-networking/azure-networking-legacy-step-2.svg" alt-text="Diagram showing the components for updating Azure content delivery and load balancing services." lightbox="media/azure-networking/azure-networking-legacy-step-2.svg":::

### Azure Front Door

Azure Front Door has three different tiers: Premium, Standard, and Classic. Standard and Premium tiers combine features from Azure Front Door Classic tier, [Azure Content Delivery Network](/azure/cdn/cdn-overview), and [Azure Web Application Firewall (WAF)](/azure/web-application-firewall/overview) into one service.

Microsoft recommends migrating your classic Azure Front Door profiles to the Premium or Standard tiers to enjoy these new features and updates. The Premium tier focuses on improved security features such as private connectivity to your backend services, Microsoft managed WAF rules, and bot protection for your web applications.

In addition to the improved features, Azure Front Door Premium includes security reports that are built into the service at no extra cost. These reports will help you analyze the WAF security rules and see what kind of attacks your web applications could face. The security report also lets you examine metrics by different dimensions, which helps you understand where traffic comes from and a breakdown of top events by criteria.

The Azure Front Door Premium tier provides the most robust Internet security measures between clients and web applications.

### Azure Application Gateway

Azure Application Gateway has two SKU types, v1 and v2, and a WAF version that can be applied to either SKU. Microsoft recommends migrating your Azure Application Gateway to the WAF_v2 SKU to benefit from the performance upgrades and new features such as autoscaling, custom WAF rules, and support for [Azure Private Link](/azure/private-link/private-link-overview). 

Custom WAF rules allow you to specify conditions to evaluate every request that goes through the Azure Application Gateway. These rules have higher priority than the rules in the managed rule sets and can be customized to suit the needs of your application and security requirements. The custom WAF rules also can limit access to your web applications by country or regions by matching an IP address to a country code. 

The other benefit of migrating to WAFv2 is you can connect to your Azure Application Gateway through the Azure Private Link service when accessing from another VNet or a different subscription. This feature lets you block public access to the Azure Application Gateway while allowing only users and devices access through a private endpoint. With Azure Private Link connectivity, you must approve each private endpoint connection, which ensures that only the right entity can access. For more information on the differences between v1 and v2 SKU, see [Azure Application Gateway v2](/azure/application-gateway/overview-v2). 

### Azure Load Balancer

With the planned retirement of the Basic Public IP SKU in September 2025, you need to upgrade services that use Basic Public IP SKU IP addresses. Microsoft recommends migrating your current Basic SKU Azure Load Balancers to Standard SKU Azure Load Balancers to implement security measures not applied by the Basic SKU.

With Standard SKU Azure Load Balancer, you're secure by default. All inbound Internet traffic to the public load balancer is blocked unless allowed by the rules of the applied network security group. This prevents accidentally allowing Internet traffic to your virtual machines or services before you are ready and ensure that you are in control of the traffic that can access your resources.

Standard SKU Azure Load Balancer uses Azure Private Link to create private endpoint connections. This is useful in cases where you want to allow private access to your resources behind a load balancer, but you want users to access it from their environment.

## Step 3: Review your hybrid connectivity services

Review of your hybrid connectivity services include the use of the new generation of SKUs for [Azure VPN Gateway](/azure/vpn-gateway/vpn-gateway-about-vpngateways).

This diagram shows the components for updating Azure hybrid connectivity services in the reference architecture.

:::image type="content" source="media/azure-networking/azure-networking-legacy-step-3.svg" alt-text="Diagram showing the components for updating Azure hybrid connectivity services." lightbox="media/azure-networking/azure-networking-legacy-step-3.svg":::

The most effective method to connect hybrid networks in Azure currently is with the new generation SKUs for Azure VPN Gateway. While you might continue to employ classic VPN gateways, these are outdated and less reliable and efficient. Classic VPN gateways support a maximum of ten Internet Protocol Security (IPsec) tunnels, whereas the newer Azure VPN Gateway SKUs can scale up to 100 tunnels. The newer SKUs operate on a newer driver model and incorporate the latest security software updates.

The older driver models were based on outdated Microsoft technology that are not suitable for modern workloads. The newer driver models not only offer superior performance and hardware, but also provide enhanced resilience. The [AZ set of SKUs](/azure/vpn-gateway/vpn-gateway-about-vpngateways#gwsku) of VPN gateways can be positioned in availability zones and support active-active connections with multiple public IP addresses. This enhances resilience and offers improved options for disaster recovery.

Additionally, for dynamic routing needs, classic VPN gateways couldn’t run Border Gateway Protocol (BGP), only used IKEv1, and did not support dynamic routing. In summary, classic SKU VPN gateways are designed for smaller workloads, low bandwidth, and static connections.

Classic VPN gateways also have limitations in the security and functionality of their IPsec tunnels. They only support Policy-Based mode with IKEv1 protocol and a limited set of encryptions and hashing algorithms that are more susceptible to breaches. Microsoft recommends that you transition to the new SKUs that offer a broader range of options for Phase 1 and Phase 2 protocols. A key advantage is that route-based VPN Gateways can use both IKEv1 and IKEv2 main mode, providing greater implementation flexibility and more robust encryption and hashing algorithms.

If you require higher security than the default encryption values, route-based VPN Gateways allow for the customization of Phase 1 and Phase 2 parameters to select specific ciphers and key lengths. Stronger encryption groups include Group 14 (2048-bit), Group 24 (2048-bit MODP Group), or ECP (elliptic curve groups) 256 or 384 bit (Group 19 and Group 20, respectively). Additionally, you can specify which prefix ranges are permitted to send encrypted traffic using the Traffic Selector setting to further safeguard the tunnel negotiation from unauthorized traffic.

For more information, see [Azure VPN Gateway cryptography](/azure/vpn-gateway/vpn-gateway-about-compliance-crypto#cryptographic-requirements).

Azure VPN Gateway SKUs facilitate Point-to-Site (P2S) connections to utilize both IPsec protocols based on the IKEv2 standard and VPN protocols based on SSL/TLS, such as OpenVPN and Secure Socket Tunneling Protocol (SSTP). This provides users with a variety of implementation methods and enables them to connect to Azure using different user device operating systems. Additionally, Azure VPN Gateway SKUs offer diverse client authentication options, including certificate authentication, Microsoft Entra ID authentication, and Active Directory Domain Services (AD DS) authentication.

> [!NOTE]
> Classic IPSec gateways will be retired on [August 31, 2024](https://azure.microsoft.com/en-us/updates/five-azure-classic-networking-services-will-be-retired-on-31-august-2024/).

## Recommended training

- [Configure and manage virtual networks for Azure administrators](/training/paths/azure-administrator-manage-virtual-networks/)
- [Secure and isolate access to Azure resources by using network security groups and service endpoints](/training/modules/secure-and-isolate-with-nsg-and-service-endpoints/)
- [Introduction to Azure Front Door](/training/modules/intro-to-azure-front-door/)
- [Introduction to Azure Application Gateway](/training/modules/intro-to-azure-application-gateway/)
- [Introduction to Azure Web Application Firewall](/training/modules/introduction-azure-web-application-firewall/)
- [Introduction to Azure Private Link](/training/modules/introduction-azure-private-link/)
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

<!---
- [Apply Zero Trust principles to gain visibility into network traffic](azure-networking-visibility.md)
--->

## References

Refer to these links to learn about the various services and technologies mentioned in this article.

- [Azure Virtual Network IP Services](/azure/virtual-network/ip-services/ip-services-overview)
- [Azure NAT Gateway](/azure/nat-gateway/nat-overview)
- [Azure Load Balancer](/azure/load-balancer/load-balancer-overview)
- [Azure Front Door](/azure/frontdoor/front-door-overview)
- [Azure Application Gateway](/azure/application-gateway/overview-v2)
- [Azure Content Delivery Network](/azure/cdn/cdn-overview)
- [Azure Web Application Firewall (WAF)](/azure/web-application-firewall/overview)
- [Azure Private Link](/azure/private-link/private-link-overview)
- [Azure VPN Gateway](/azure/vpn-gateway/vpn-gateway-about-vpngateways)
