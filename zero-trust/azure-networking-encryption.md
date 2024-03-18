---
title: Apply Zero Trust principles to encrypting Azure-based network communication
description: How to apply Zero Trust principles to encrypting Azure-based network communication.  
ms.date: 03/18/2024
ms.service: security
author: brsteph
ms.author: bstephenson
ms.topic: conceptual
ms.collection: 
  - msftsolution-azureiaas
  - msftsolution-scenario
  - zerotrust-solution
  - zerotrust-azure
---

# Apply Zero Trust principles to encrypting Azure-based network communication

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

This article provides guidance to applying the [principles of Zero Trust](zero-trust-overview.md) for encrypting network communication to, from, and across Azure environments in the following ways. 

| Zero Trust principle | Definition | Met by |
| --- | --- | --- |
| Verify explicitly | Always authenticate and authorize based on all available data points. | Using Conditional Access policies for your Azure VPN Gateway connections and Secure Shell (SSH) and Remote Desktop Protocol (RDP) for your user-to-virtual machine connections. |
| Use least privileged access | Limit user access with Just-In-Time and Just-Enough-Access (JIT/JEA), risk-based adaptive policies, and data protection. | Configuring your Microsoft Enterprise Edge (MSEE) devices to use static CAK for Azure ExpressRoute with direct ports and using managed identity to authenticate ExpressRoute circuit resources. |
| Assume breach | Minimize blast radius and segment access. Verify end-to-end encryption and use analytics to get visibility, drive threat detection, and improve defenses. | Protecting network traffic with encryption methods and protocols that provide confidentiality, integrity, and authenticity of your data in transit. <br><br> Using Azure Monitor to provide ExpressRoute network performance metrics and alerts. <br><br> Using Azure Bastion to manage individual sessions from the Bastion service and delete or force a disconnect.|

<!---
This article is a part of a series of articles that demonstrate how to apply the principles of Zero Trust for Azure networking.
--->

The levels of encryption for network traffic are:

- Network layer encryption

  - Secure and verify communication from the Internet or your on-premises network to Azure VNets and virtual machines

   - Secure and verify communication within and across Azure VNets
 
- Application layer encryption

  - Protection for Azure Web Applications

- Protection for workloads running on Azure virtual machines


## Reference architecture

The following diagram shows the reference architecture for this Zero Trust guidance for encrypted communication between users and admins on-premises or on the Internet and components in the Azure environment for the steps described in this article.

>> add

:::image type="content" source="media/hub/azure-infra-hub-architecture-1.svg" alt-text="The reference architecture for the components of a hub virtual network with Zero Trust principles applied." lightbox="media/hub/azure-infra-hub-architecture-1.svg":::
 
In the diagram, the numbers correspond to the steps in the following sections.

## What's in this article?

Zero Trust principles are applied across the reference architecture, from users and admins on the Internet or your on-premises network to and within the Azure cloud. The following table describes the recommendations for ensuring the encryption of network traffic across this architecture.

| Step | Task | Zero Trust principle(s) applied |
| --- | --- | --- |
| 1 | Implement network layer encryption. | Verify explicitly <br> Use least privileged access <br> Assume breach |
| 2 | Secure and verify communication from an on-premises network to Azure VNets. | Verify explicitly <br> Assume breach |
| 3 | Secure and verify communication within and across Azure VNets. | Assume breach |
| 4 | Implement application layer encryption. | Verify explicitly <br> Assume breach |
| 5 | Use Azure Bastion to protect Azure virtual machines. | Assume breach |

## Step 1: Implement network layer encryption

Network layer encryption is critical when applying Zero Trust principles to your on-premises and Azure environment. When network traffic goes over the internet, you should always assume there's a possibility of traffic interception by attackers, and your data might get exposed or altered before it reaches its destination. Because service providers control how data gets routed through the internet, you want to ensure that the privacy and integrity of your data is maintained from the moment it leaves your on-premises network all the way to Microsoft’s cloud.

In the next two sections, we discuss Internet Protocol Security (IPsec) and Media Access Control Security ([MACsec](https://1.ieee802.org/security/802-1ae/)), which Azure networking services support these protocols, and how you can ensure they are being used.

### IPsec

IPsec is a group of protocols that provides security for Internet Protocol (IP) communications. It authenticates and encrypts network packets using a set of encryption algorithms. IPSec is the security encapsulation protocol used to establish virtual private networks (VPNs). An IPsec VPN tunnel consists of two phases, phase 1 known as main mode and phase 2 known as quick mode.

Phase 1 of IPsec is tunnel establishment, where peers negotiate parameters for the Internet Key Exchange (IKE) security association, such as encryption, authentication, hashing, and Diffie-Hellman algorithms. To verify their identities, peers exchange a preshared key. Phase 1 of IPsec can operate in two modes: main mode or aggressive mode. Azure VPN Gateway supports two versions of IKE, IKEv1 and IKEv2, and only operates in main mode. Main mode ensures the encryption of the identity of the connection between the Azure VPN Gateway and the on-premises device.

In phase 2 of IPsec, peers negotiate security parameters for data transmission. In this phase, both peers agree on the encryption and authentication algorithms, lifetime value of the security association (SA), and traffic selectors (TS) that defines what traffic is encrypted over the IPsec tunnel. The tunnel created in phase 1 serves as a secure channel for this negotiation. IPsec can secure IP packets using either Authentication Header (AH) protocol or Encapsulating Security Payload (ESP) protocol. AH provides integrity and authentication, while ESP   also provides confidentiality (encryption). IPsec phase 2 can operate in either transport mode or tunnel mode. In transport mode, only the payload of the IP packet gets encrypted, while in tunnel mode the entire IP packet is encrypted and a new IP header is added. IPsec phase 2 can be established on top of either IKEv1 or IKEv2. The current Azure VPN Gateway IPsec implementation supports only ESP in tunnel mode.

Some of the Azure services that support IPsec are:

•	[Azure VPN Gateway](https://learn.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpngateways)
o	Site-to-site VPN connections
o	VNet-to-VNet connections
o	Point-to-Site connections
•	[Azure Virtual WAN](https://learn.microsoft.com/en-us/azure/virtual-wan/virtual-wan-about)
o	VPN sites
o	User VPN configurations

There are no settings that you need to modify to enable IPsec for these services. They are enabled by default.

### MACsec and Azure Key Vault

MACsec (IEEE 802.1AE) is a network security standard that applies the **Assume breach** Zero 
Trust principle at the data link layer by providing authentication and encryption over an Ethernet link. MACsec assumes that any network traffic, even in the same local area network, can be compromised or intercepted by malicious actors. MACsec verifies and protects each frame using a security key that is shared between two network interfaces. This configuration can only be accomplished between two MACsec-capable devices.

MACsec is configured with connectivity associations, which are a set of attributes that network interfaces use to create inbound and outbound security channels. Once created, traffic over these channels gets exchanged over two MACsec secured links. MACsec has two connectivity association modes: 

•	**Static connectivity association key (CAK) mode**: MACsec secured links are established using a preshared key that includes a connectivity association key name (CKN) and the assigned CAK. These keys are configured on both ends of the link.
•	**Dynamic CAK mode**: The security keys are generated dynamically using the 802.1x authentication process, which can use a centralized authentication device such as a Remote Authentication Dial-In User Service (RADIUS) server.

Microsoft Enterprise Edge (MSEE) devices support static CAK by storing the CAK and CKN in an Azure Key Vault when you configure Azure ExpressRoute with direct ports. To access the values in the Azure Key Vault, configure managed identity to authenticate the ExpressRoute circuit resource. This approach follows the Use least privileged access Zero Trust principle because only authorized devices can access the keys from the Azure Key Vault.
For more information, see [Configure MACsec on ExpressRoute Direct ports](https://learn.microsoft.com/en-us/azure/expressroute/expressroute-howto-macsec).


## Step 2: Secure and verify communication from an on-premises network to Azure VNets

Traffic within Azure has an underlying level of encryption. When traffic moves between VNets in different regions, Microsoft uses MACsec to encrypt and authenticate peering traffic at the data-link layer. 

However, encryption alone is not enough to ensure Zero Trust. You should also verify and monitor the network communication within and across Azure VNets. Further encryption and verification between VNets are possible with the help of Azure VPN Gateway or network virtual appliances (NVAs) but isn’t a common practice. Microsoft   recommends designing your network topology to use a centralized traffic inspection model that can enforce granular policies and detect anomalies.

To reduce the overhead of configuring a VPN gateway or virtual appliance, enable the [VNet encryption](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-network-encryption-overview) feature for certain virtual machine sizes to encrypt and verify traffic between virtual machines at the host level, within a VNet, and across VNet peerings.

## Step 3: Secure and verify communication within and across Azure VNets

Application layer encryption plays a key factor for Zero Trust that mandates all data and communications are encrypted when users are interacting with web applications or devices. Application layer encryption ensures that only verified and trusted entities can access web applications or devices.

One of the most common examples of encryption at the application layer is Hypertext Transfer Protocol Secure (HTTPS), which encrypts data between a web browser and a web server. HTTPS uses Transport Layer Security (TLS) protocol to encrypt client-server communication and uses a TLS digital certificate to verify the identity and trustworthiness of the website or domain.

Another example of application layer security is Secure Shell (SSH) and Remote Desktop Protocol (RDP) that encrypts data between the client and server. These protocols also support multifactor authentication and Conditional Access policies to ensure that only authorized and compliant devices or users can access remote resources. See [Step 5](#step-5-use-azure-bastion) to protect Azure virtual machines) for information about securing SSH and RDP connections to Azure virtual machines.


## Step 4: Implement encryption at the application layer

Application layer encryption plays a key factor for Zero Trust that mandates all data and communications are encrypted when users are interacting with web applications or devices. Application layer encryption ensures that only verified and trusted entities can access web applications or devices.

One of the most common examples of encryption at the application layer is Hypertext Transfer Protocol Secure (HTTPS), which encrypts data between a web browser and a web server. HTTPS uses Transport Layer Security (TLS) protocol to encrypt client-server communication and uses a TLS digital certificate to verify the identity and trustworthiness of the website or domain.

Another example of application layer security is Secure Shell (SSH) and Remote Desktop Protocol (RDP) that encrypts data between the client and server. These protocols also support multifactor authentication and Conditional Access policies to ensure that only authorized and compliant devices or users can access remote resources. See Step 5 for information about securing SSH and RDP connections to Azure virtual machines.

### Protection for Azure web applications

You can use Azure Front Door or Azure Application Gateway to protect your Azure web applications.

#### Azure Front Door

[Azure Front Door](https://learn.microsoft.com/en-us/azure/frontdoor/front-door-overview) is a global distribution service that optimizes the content delivery to end users through Microsoft's edge locations. With features such as Web Application Firewall (WAF) and Private Link service, you can detect and block malicious attacks on your web applications at the edge of the Microsoft network while privately accessing your origins    using the Microsoft internal network.

To protect your data, traffic to Azure Front Door endpoints is protected using HTTPS with end-to-end TLS for all traffic going to and from its endpoints. Traffic is encrypted from the client to the origin and from the origin to the client.

Azure Front Door handles HTTPS requests and determines which endpoint in its profile has the associated domain name. Then it checks the path and determines which routing rule matches the path of the request. If caching is enabled, Azure Front Door checks its cache to see if there's a valid response. If there is no valid response, Azure Front Door selects the best origin that can serve the content requested. Before the request is sent to the origin, a rule set can be applied to the request to change the header, query string, or origin destination.

Azure Front Door supports both front end and back-end TLS. Front end TLS encrypts traffic between the client and Azure Front Door. Back-end TLS encrypts traffic between Azure Front Door and the origin. Azure Front Door supports TLS 1.2 and TLS 1.3. You can configure Azure Front Door to use a custom TLS certificate or use a certificate managed by Azure Front Door.

> [!NOTE]
> You can also use the Private Link feature for connectivity to NVAs for further packet inspection.

#### Azure Application Gateway

[Azure Application Gateway](https://learn.microsoft.com/en-us/azure/application-gateway/overview) is a regional load balancer that operates at Layer 7. It routes and distributes web traffic based on HTTP URL attributes. It can route and distribute traffic using three different approaches:

•	**HTTP only** - Application Gateway receives and routes incoming HTTP requests to the appropriate destination in unencrypted form.
•	**SSL Termination** - Application Gateway decrypts incoming HTTPS requests at the instance level, inspects them, and routes them unencrypted to the destination.
•	**End-to-End TLS** - Application Gateway decrypts incoming HTTPS requests at the instance level, inspects them, and re-encrypts them before routing them to the destination.

The most secure option is end-to-end TLS, which allows encryption and transmission of sensitive data by requiring the use of Authentication Certificates or Trusted Root Certificates. It also requires uploading these certificates to the backend servers and ensuring these back end servers are known to Application Gateway. For more information, see [Configure end-to-end TLS by using Application Gateway](https://learn.microsoft.com/en-us/azure/application-gateway/end-to-end-ssl-portal).

Additionally, on-premises users or users on virtual machines in another VNet can use the internal front end of Application Gateway with the same TLS capabilities. Along with encryption, Microsoft recommends that you always enable WAF for more front-end protection for your endpoints.

## Step 5: Use Azure Bastion to protect Azure virtual machines

[Azure Bastion](/azure/bastion/bastion-overview) is a managed PaaS service that allows you securely connect to your virtual machines over a TLS connection. This connectivity can be established from the Azure portal or through a native client to the private IP address on the virtual machine. Advantages of using Bastion include: 

- Azure virtual machines don't need a public IP address. Connections are over TCP port 443 for HTTPS and can traverse most firewalls.
- Virtual machines are protected against port scanning.
- The Azure Bastion platform is constantly updated and protected against zero-day exploits.

With Bastion, you can control the RDP and SSH connectivity to your virtual machine from a single point of entry. You can manage individual sessions from the Bastion service in the Azure portal. You can also delete or force a disconnect of an on-going remote session if you suspect a user isn't supposed to be connecting to that machine.

To protect your Azure virtual machine, deploy [Azure Bastion](/azure/bastion/tutorial-create-host-portal) and begin using RDP and SSH to connect to your virtual machines with their private IP addresses.


## Recommended training

- [Connect your on-premises network to Azure with VPN Gateway](/training/modules/connect-on-premises-network-with-vpn-gateway/)
- [Connect your on-premises network to the Microsoft global network by using ExpressRoute](https://learn.microsoft.com/en-us/training/modules/connect-on-premises-network-with-expressroute/)
- [Introduction to Azure Front Door](https://learn.microsoft.com/en-us/training/modules/intro-to-azure-front-door/)
- [Configure Azure Application Gateway](https://learn.microsoft.com/en-us/training/modules/configure-azure-application-gateway/)
- [Introduction to Azure Bastion](https://learn.microsoft.com/en-us/training/modules/intro-to-azure-bastion/)

For more training on security in Azure, see these resources in the Microsoft catalog:<br> 
[Security in Azure | Microsoft Learn](/training/browse/?subjects=security&products=azure)

## Next Steps

For additional information about applying Zero Trust to Azure networking, see:

- [Secure networks with Zero Trust](./deploy/networks.md)
- [Spoke virtual networks in Azure](azure-infrastructure-iaas.md)
- [Hub virtual networks in Azure](azure-infrastructure-paas.md)
- [Spoke virtual networks with Azure PaaS services](azure-infrastructure-paas.md)
- [Azure Virtual WAN](azure-virtual-wan.md)

## References

Refer to these links to learn about the various services and technologies mentioned in this article.

- [Azure VPN Gateway](https://learn.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpngateways)
- [Azure Virtual WAN](https://learn.microsoft.com/en-us/azure/virtual-wan/virtual-wan-about)
- [Configure MACsec on ExpressRoute Direct ports](https://learn.microsoft.com/en-us/azure/expressroute/expressroute-howto-macsec)
- [Use Microsoft Tunnel VPN gateway with Conditional Access policies](https://learn.microsoft.com/en-us/mem/intune/protect/microsoft-tunnel-conditional-access)
- [Azure ExpressRoute](https://learn.microsoft.com/en-us/mem/intune/protect/microsoft-tunnel-conditional-access
- [VNet encryption](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-network-encryption-overview)
- [Azure Front Door](https://learn.microsoft.com/en-us/azure/frontdoor/front-door-overview)
- [Application Gateway](https://learn.microsoft.com/en-us/azure/application-gateway/overview)
- [Azure Bastion](https://learn.microsoft.com/en-us/azure/bastion/bastion-overview)
