---
title: Secure networks with Zero Trust
description: Learn how to secure networks using a Zero Trust strategy with Secure Access Service Edge (SASE) and Secure Service Edge (SSE) solutions.
ms.date: 03/03/2025
ms.service: security
author: kenwith
manager: rkarlin
ms.author: kenwith
ms.topic: concept-article
ms.collection:
  - zerotrust-pillar

#customer intent: As an administrator, I want to understand how I can adopt modern Zero Trust security practices so that I can secure my network and organization.
---

# Secure networks with Zero Trust

In recent years, the landscape of network security has undergone significant transformations. Traditional Virtual Private Networks (VPNs), once the cornerstone of secure remote access, are increasingly being replaced by more advanced and comprehensive solutions. One such solution is Secure Access Service Edge (SASE), which integrates wide-area networking (WAN) capabilities with comprehensive security services, all delivered through a cloud-based architecture. This shift is driven by the need for more flexible, scalable, and efficient security measures that can keep pace with the evolving threat landscape.

The emergence of SASE represents a paradigm shift in how organizations approach network security. By converging networking and security functions into a single, unified service, SASE offers a more streamlined and effective way to protect data and applications, regardless of where they are located. This approach not only simplifies the management of security policies but also enhances the overall security posture of the organization. Artificial Intelligence (AI) is playing a pivotal role in this new era of network security. AI-driven solutions are capable of analyzing vast amounts of data in real-time, identifying potential threats, and responding to incidents with unprecedented speed and accuracy. By leveraging AI, organizations can proactively detect and mitigate security risks, ensuring a more robust and resilient network infrastructure.

In summary, the replacement of traditional VPNs with SASE, coupled with the integration of AI, marks a significant advancement in the field of network security. These innovations are enabling organizations to stay ahead of emerging threats and maintain a secure and efficient network environment.

## Key Principles of the Zero Trust Network Model

:::image type="icon" source="../media/icon-networks-medium.png":::

Instead of assuming that everything behind the corporate firewall is secure, an end-to-end Zero Trust strategy acknowledges that breaches are inevitable. This approach requires verifying each request as if it originates from an uncontrolled network, with identity management playing a crucial role. By incorporating the CISA and NIST Zero Trust models and patterns, organizations can enhance their security posture and better protect their networks.

In the Zero Trust model, there are three key objectives when it comes to securing your networks:

- Be ready to handle attacks before they happen.
- Minimize the extent of the damage and how fast it spreads.
- Increase the difficulty of compromising your cloud footprint.

To make this happen, follow three Zero Trust principles:

- **Verify explicitly.** Always authenticate and authorize based on all available data points, including user identity, location, device health, service or workload, user and device risk, data classification, and anomalies.
- **Use least-privileged access.** Limit user access with Just-In-Time and Just-Enough-Access (JIT/JEA), risk-based adaptive policies, and data protection to protect both data and productivity.
- **Assume breach.** Minimize impact radius for breaches and prevent lateral movement by segmenting access by network, user, devices, and application awareness. Verify all sessions are encrypted end to end. Use analytics to get [visibility](https://aka.ms/ZTCrossPillars), drive threat detection, and improve defenses.


In the Zero Trust model, there are three key objectives when it comes to securing your networks:

- Be ready to handle attacks before they happen. 

- Minimize the extent of the damage and how fast it spreads.

- Increase the difficulty of compromising your cloud footprint.

To make this happen, we follow three Zero Trust principles:

- **Verify explicitly.** Always authenticate and authorize based on all available data points, including user identity, location, device health, service or workload, data classification, and anomalies.

- **Use least-privileged access.** Limit user access with Just-In-Time and Just-Enough-Access (JIT/JEA), risk-based adaptive polices, and data protection to protect both data and productivity.

- **Assume breach.** Minimize blast radius for breaches and prevent lateral movement by segmenting access by network, user, devices, and application awareness. Verify all sessions are encrypted end to end. Use analytics to get , drive threat detection, and improve defenses.


## Network Zero Trust deployment objectives

Before most organizations start their Zero Trust journey, they have network security that is characterized by the following: 
- Few network security perimeters and open, flat networks.
- Minimal threat protection and static traffic filtering.
- Unencrypted internal traffic.

It is crucial to transition from these legacy patterns and consider a structured approach like the CISA Zero Trust Maturity Model (ZTMM). This model guides organizations through different stages of Zero Trust implementation, ensuring a comprehensive and phased adoption of Zero Trust principles.

When implementing an end-to-end Zero Trust framework for securing networks, we recommend you focus first on objectives one through four. After these are completed, focus on objectives five through ten.

## Networking Zero Trust deployment guide

This guide will walk you through the steps required to secure your networks following the principles of a Zero Trust security framework.


### 1. Macro segmentation and VPN replacement strategy
Before diving into micro-segmentation, it's essential to establish a broader segmentation strategy. Macro segmentation involves dividing your network into larger segments based on overarching functional or security requirements. This approach simplifies initial management and provides a foundation upon which finer granularity, like micro-segmentation, can be built. 
Concurrently, develop a VPN replacement strategy that leverages modern, secure, and scalable alternatives such as Zero Trust Network Access (ZTNA) solutions. These solutions eliminate the need for traditional VPNs by providing secure, identity-based access to applications regardless of the user's location.  


Remote users can connect to private apps across hybrid and multicloud environments, private networks, and data centers from any device and network without requiring a VPN solution. The service offers per-app adaptive access based on Conditional Access (CA) policies for more granular security than a traditional VPN solution.
Microsoft Entra Private Access provides users (whether in an office or working remotely) secure access to private corporate resources. Microsoft Entra Private Access builds on the Microsoft Entra application proxy to extend access to any private resource, independent of TCP/IP port and protocol.

Microsoft Entra ID Protection cloud-based identity and access management (IAM) helps protect user identities and credentials from compromise.
More details: Microsoft Entra deployment scenario - Modernize remote access - Microsoft Entra | Microsoft Learn


### 2. Network segmentation: Many ingress/egress cloud micro-perimeters with some micro-segmentation

Organizations should not just have one single, big pipe in and out of their network. In a Zero Trust approach, networks are instead segmented into smaller islands where specific workloads are contained. Each segment has its own ingress and egress controls to minimize the "blast radius" of unauthorized access to data. By implementing software-defined perimeters with granular controls, you increase the difficulty for unauthorized actors to propagate throughout your network, and so reduce the lateral movement of threats.

There is no architecture design that fits the needs of all organizations. You have the option between a few [common design patterns](https://www.microsoft.com/security/blog/2020/06/15/zero-trust-part-1-networking/) for segmenting your network according to the Zero Trust model.

In this deployment guide, we'll walk you through the steps to achieve one of those designs: Micro-segmentation.

With micro-segmentation, organizations can move beyond simple centralized network-based perimeters to comprehensive and distributed segmentation using software-defined micro-perimeters.  

#### Applications are partitioned to different Azure Virtual Networks (VNets) and connected using a hub-spoke model

:::image type="content" source="../media/diagram-network-hub-spoke-two-regions.png" alt-text="Diagram of two virtual networks connected in a hub-and-spoke model." border="false":::

Follow these steps:

- [Create dedicated virtual networks](/azure/virtual-network/quick-create-portal) for different applications and/or application components.

- Create a central VNet to set up the security posture for inter-app connectivity and connect the app VNets in [a hub-and-spoke architecture](/azure/architecture/reference-architectures/hybrid-networking/hub-spoke).

- [Deploy Azure Firewall](/azure/firewall/deploy-ps) in the hub VNet to inspect and govern traffic between the VNets.


### 3. Threat protection: Cloud native filtering and protection for known threats

Cloud applications that have opened up endpoints to external environments, such as the internet or your on-premises footprint, are at risk of attacks coming in from those environments. It is therefore imperative that you scan the traffic for malicious payloads or logic.

These types of threats fall into two broad categories:

- **Known attacks**. Threats that have been discovered by your software provider or the larger community. In such cases, the attack signature is available and you need to ensure that each request is checked against those signatures. The key is to be able to quickly update your detection engine with any newly identified attacks.

- **Unknown attacks.** These are threats that don't quite match against any known signature. These types of threats include zero-day vulnerabilities and unusual patterns in request traffic. The ability to detect such attacks depends on how well your defenses know what's normal and what is not. Your defenses should be constantly learning and updating such patterns as your business (and associated traffic) evolves.

Take these steps to protect against known threats:

- Implement Microsoft Entra Internet Access capabilities.

- **For endpoints with HTTP/S traffic**, protect using [Azure Web Application Firewall (WAF)](/azure/web-application-firewall/overview) by:

    - Turning on the default ruleset or [OWASP top 10](https://owasp.org/www-project-top-ten/) protection ruleset to protect against known web-layer attacks

    - Turning on the bot protection ruleset to prevent malicious bots from scraping information, conducting credential stuffing, etc.

    - Adding custom rules to protect against threats specific to your business.

    You can use one of two options:

    - [Azure Front Door](/azure/frontdoor/front-door-overview)

        - [Create a Web Application Firewall policy on Azure Front Door](/azure/web-application-firewall/afds/waf-front-door-create-portal).

        - [Configure bot protection for Web Application Firewall](/azure/web-application-firewall/afds/waf-front-door-policy-configure-bot-protection).

        - [Custom rules for Web Application Firewall](/azure/web-application-firewall/afds/waf-front-door-custom-rules-powershell).

    - [Azure Application Gateway](/azure/application-gateway/overview)

       - [Create an application gateway with a Web Application Firewall](/azure/web-application-firewall/ag/application-gateway-web-application-firewall-portal).

       - [Configure bot protection for Web Application Firewall](/azure/web-application-firewall/ag/bot-protection).

       - [Create and use Web Application Firewall v2 custom rules.](/azure/web-application-firewall/ag/create-custom-waf-rules).


- **For all endpoints (HTTP or not)**, front with [Azure Firewall](/azure/firewall/overview) for threat intelligence-based filtering at Layer 4:

    - [Deploy and configure Azure Firewall](/azure/firewall/tutorial-firewall-deploy-portal) using the Azure portal.
    - [Enable threat intelligence-based filtering](/azure/firewall/threat-intel) for your traffic.
        > [!TIP]
        > [Learn about implementing an end-to-end Zero Trust strategy for endpoints](https://aka.ms/ZTEndpoints).


### 4. Encryption: User-to-app internal traffic is encrypted

The third initial objective to focus on is adding encryption to ensure user-to-app internal traffic is encrypted.

Follow these steps:

- Enforce HTTPS-only communication for your internet facing web applications by [redirecting HTTP traffic to HTTPS using Azure Front Door](/azure/frontdoor/front-door-how-to-redirect-https).
- Connect remote employees/partners to Microsoft Azure using the [Azure VPN Gateway](/azure/vpn-gateway/vpn-gateway-about-vpngateways).
    - [Turn on encryption](/azure/vpn-gateway/vpn-gateway-security-controls#data-protection) for any point-to-site traffic in Azure VPN Gateway service.
- Access your Azure virtual machines securely using encrypted communication via [Azure Bastion](/azure/bastion/bastion-overview).
- [Connect using SSH to a Linux virtual machine](/azure/bastion/bastion-connect-vm-ssh).
- [Connect using RDP to a Windows virtual machine](/azure/bastion/bastion-connect-vm-rdp).

> [!TIP]
> [Learn about implementing an end-to-end Zero Trust strategy for applications](https://aka.ms/ZTApplications).


### 5. Network segmentation: Fully distributed ingress/egress cloud micro-perimeters and deeper micro-segmentation

Once you've accomplished your initial three objectives, the next step is to further segment your network.


#### Partition app components to different subnets

:::image type="content" source="../media/diagram-azure-region-virtual-network-servers.png" alt-text="Diagram of a virtual network of servers in the Azure region." border="true":::


Follow these steps:

- Within the VNet, [add virtual network subnets](/azure/virtual-network/virtual-network-manage-subnet) so that discrete components of an application can have their own perimeters.
- [Apply network security group rules](/azure/virtual-network/tutorial-filter-network-traffic#create-security-rules) to allow traffic only from the subnets that have an app subcomponent identified as a legitimate communications counterpart.


#### Segment and enforce the external boundaries

:::image type="content" source="../media/diagram-servers-devices-boundaries-azure-vpn.png" alt-text="Diagram of a servers and devices with connections across boundaries." border="true":::

Follow these steps, depending on the type of boundary:

##### Internet boundary

- If internet connectivity is required for your application that needs to be routed via the hub VNet, [update the network security group rules](/azure/virtual-network/tutorial-filter-network-traffic) in hub VNet to allow internet connectivity.
- [Turn on Azure DDoS Protection Standard](/azure/virtual-network/manage-ddos-protection#enable-ddos-for-an-existing-virtual-network)
    to protect the hub VNet from volumetric network layer attacks.
- If your application uses HTTP/S protocols, [turn on Azure Web Application Firewall](/azure/web-application-firewall/afds/waf-front-door-custom-rules-powershell) to protect against Layer 7 threats.


##### On-premises boundary

- If your app needs connectivity to your on-premise data center or private cloud, use Microsoft Entra Private Access, [Azure ExpressRoute]([use Azure ExpressRoute](/azure/expressroute/expressroute-howto-circuit-portal-resource-manager)) or [Azure VPN for connectivity to your hub VNet](/azure/vpn-gateway/vpn-gateway-howto-site-to-site-resource-manager-portal). 
- [Configure the Azure Firewall](/azure/firewall/tutorial-hybrid-ps) in the hub VNet to inspect and govern traffic.


##### PaaS services boundary

 - When using Azure-provided PaaS services (e.g., Azure Storage, [Azure Cosmos DB](/azure/private-link/create-private-endpoint-cosmosdb-portal),
    or [Azure Web App](/azure/private-link/create-private-endpoint-webapp-portal), use the [PrivateLink](/azure/private-link/create-private-link-service-portal) connectivity option to ensure all data exchanges are over the private IP space and the traffic never leaves the Microsoft network.

> [!TIP]
> [Learn about implementing an end-to-end Zero Trust strategy for data](https://aka.ms/ZTData).


### 6. Threat protection: Machine learning-based threat protection and filtering with context-based signals

For further threat protection, turn on [Azure DDoS Protection Standard](/azure/virtual-network/ddos-protection-overview) to constantly monitor your Azure-hosted application traffic, use ML-based frameworks to baseline and detect volumetric traffic floods, and apply automatic mitigations.

Follow these steps:

- [Configure and manage](/azure/virtual-network/manage-ddos-protection) Azure DDoS Protection Standard.
- [Configure alerts](/azure/virtual-network/manage-ddos-protection#configure-alerts-for-ddos-protection-metrics) for DDoS protection metrics.


### 7. Encryption: All traffic is encrypted

Finally, complete your network protection by ensuring that all traffic is encrypted.

Follow these steps:

- [Encrypt application backend traffic](/azure/vpn-gateway/vpn-gateway-ipsecikepolicy-rm-powershell) between virtual networks.
- Encrypt traffic between on-premises and cloud:
    - [Configure a site-to-site VPN](/azure/expressroute/site-to-site-vpn-over-microsoft-peering) over ExpressRoute Microsoft peering.
    - [Configure IPsec transport mode](/azure/expressroute/expressroute-howto-ipsec-transport-private-windows) for ExpressRoute private peering.

### 8. Automation and Orchestration

**Microsoft Sentinel**

Enable analytic rules to detect advanced multistage attacks with Fusion and UEBA anomalies in Microsoft Sentinel. Design automation rules and playbooks for security response.

See Microsoft guidance in 6.2.3 and 6.4.1.

**Microsoft Entra ID Governance**

Enable reviewer decision helpers in access reviews. The User-to-Group Affiliation helper provides a Machine Learning based recommendation to improve the reviewer experience.
- Access review settings
- Review recommendations for Access reviews

**Automated Workflows**

**Microsoft Defender XDR**

Configure automated investigation and response capabilities in Microsoft Defender XDR. 
- Automated investigation and response overview

**Microsoft Sentinel playbooks**

Sentinel playbooks are based on Logic Apps, a cloud service that schedules, automates, and orchestrates tasks and workflows across enterprise systems. Build response playbooks with templates, deploy solutions from the Sentinel content hub. Build custom analytics rules and response actions with Azure Logic Apps.
- Sentinel playbooks from templates
- Automate threat response with playbooks
- Sentinel content hub catalog
- Azure Logic Apps

**AI Driven by Analytics decides A&O modifications**

**Microsoft Sentinel**

Enable analytic rules to detect advanced multistage attacks with Fusion and UEBA anomalies in Microsoft Sentinel. Design automation rules and playbooks for security response.

See Microsoft guidance in 6.2.3 and 6.4.1.

**Microsoft Entra ID Governance**

Enable reviewer decision helpers in access reviews. The User-to-Group Affiliation helper provides a Machine Learning based recommendation to improve the reviewer experience.
- Access review settings
- Review recommendations for Access reviews


### 9. Monitoring and Visibility

**Log Analysis**

**Microsoft Defender XDR**

Microsoft Defender XDR is a unified pre- and post-breach enterprise defense suite that coordinates detection, prevention, investigation, and response natively across endpoints, identities, email, and applications. Use Defender XDR to protect against and respond to sophisticated attacks.

- Investigate alerts
- Zero Trust with Defender XDR
- Defender XDR for US government

**Microsoft Sentinel**

Develop custom analytics queries and visualize collected data using workbooks.

- Custom analytics rules to detect threats
- Visualize collected data
- Use workbooks with Global Secure Access

**AI-Enabled Network Access**


**Microsoft Sentinel**

Use Azure Firewall to visualize firewall activities, detect threats with AI investigation capabilities, correlate activities, and automate response actions.

- Azure Firewall with Sentinel

**Microsoft Entra ID Protection**

Microsoft Entra ID Protection uses machine learning (ML) algorithms to detect users and sign-in risk. Use risk conditions in Conditional Access policies for dynamic access, based on risk level.

- Microsoft Entra ID Protection
- Risk detections
- Risk-based access policies

**Global Secure Access**

Apply Conditional Access policies with risk conditions to network access to Microsoft Entra Private Access apps, Quick access apps, and Global Secure Access traffic forwarding profiles.

- Global Secure Access overview
- Learn about Microsoft Entra Private Access
- Universal Conditional Access


### 10. Discontinue legacy network security technology

Discontinue the use of signature-based Network Intrusion Detection/Network Intrusion Prevention (NIDS/NIPS) Systems and Network Data Leakage/Loss Prevention (DLP).

The major cloud service providers already filter for malformed packets and common network layer attacks, so there's no need for a NIDS/NIPS solution to detect those. In addition, traditional NIDS/NIPS solutions are typically driven by signature-based approaches (which are considered outdated) and are easily evaded by attackers and typically produce a high rate of false positives.

Network-based DLP is decreasingly effective at identifying both inadvertent and deliberate data loss. The reason for this is that most modern protocols and attackers use network-level encryption for inbound and outbound communications. The only viable workaround for this is "SSL-bridging" which provides an "authorized man-in-the-middle" that terminates and then reestablishes encrypted network connections. The SSL-bridging approach has fallen out of favor because of the level of trust required for the partner running the solution and the technologies that are being used.

Based on this rationale, we offer an all-up recommendation that you discontinue use of these legacy network security technologies. However, if your organizational experience is that these technologies have had a palpable impact on preventing and detecting real attacks, you can consider porting them to your cloud environment.

## Products covered in this guide

**Microsoft Azure**

[Azure Networking](/azure/networking/)

[Virtual Networks and Subnets](/azure/virtual-network/virtual-networks-overview)

[Network Security Groups](/azure/virtual-network/security-overview)
and [Application Security Groups](/azure/virtual-network/application-security-groups)

[Azure Firewall](/azure/firewall/overview)

[Azure DDoS Protection](/azure/virtual-network/ddos-protection-overview)

[Azure Web Application Firewall](/azure/web-application-firewall/ag/ag-overview)

[Azure VPN Gateway](/azure/vpn-gateway/vpn-gateway-about-vpngateways)

[Azure ExpressRoute](/azure/expressroute/expressroute-introduction)

[Azure Network Watcher](/azure/network-watcher/network-watcher-monitoring-overview)

[Microsoft Entra Private Access](/entra/global-secure-access/concept-private-access)

[Microsoft Entra Internet Access](/entra/global-secure-access/concept-internet-access)

## Conclusion

Securing networks is central to a successful Zero Trust strategy. For further information or help with implementation, please contact your Customer Success team or continue to read through the other chapters of this guide, which spans all Zero Trust pillars.
