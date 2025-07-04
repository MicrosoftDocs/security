---
title: Secure networks with SASE, Zero Trust, and AI
description: Learn how to secure networks using a Zero Trust strategy with Secure Access Service Edge (SASE) and Secure Service Edge (SSE) solutions.
ms.date: 06/26/2025
ms.service: security
author: kenwith
manager: femila
ms.author: kenwith
ms.topic: concept-article
ms.collection:
  - zerotrust-pillar

#customer intent: As an administrator, I want to understand how I can adopt modern SASE, Zero Trust, and AI security practices so that I can secure my network and organization.
---

# Secure networks with SASE, Zero Trust, and AI

Network security is evolving beyond the traditional perimeter, which was once tied to the physical boundaries of data centers. Today, the perimeter is dynamic—extending to users, devices, and data wherever they are. This shift drives the adoption of risk-based policies that isolate hosts, enforce encryption, segment networks, and places controls closer to applications and data.

Secure Access Service Edge (SASE) reflects this evolution by redefining the perimeter entirely. It converges networking and security into a cloud-delivered service that follows users and data across environments. This approach simplifies policy management and strengthens protection.

Adding a Zero Trust strategy to a SASE framework further enhances security by ensuring that no user or device is trusted by default—regardless of location. This principle aligns seamlessly with SASE’s goal of securing access at the edge.

Artificial Intelligence (AI) amplifies this approach by analyzing data in real time, detecting threats, and enabling rapid, automated responses. Together, SASE, Zero Trust, and AI empower organizations to secure a perimeter-less world with greater agility, precision, and resilience.

## Key principles of the Zero Trust network model

Instead of assuming that everything behind the corporate firewall is secure, an end-to-end Zero Trust strategy acknowledges that breaches are inevitable. This approach requires verifying each request as if it originates from an uncontrolled network, with identity management playing a crucial role. When organizations incorporate the Cybersecurity and Infrastructure Security Agency (CISA) and National Institute of Standards and Technology (NIST) Zero Trust models and patterns, they enhance their security posture and better protect their networks.

In the Zero Trust model, securing your networks focuses on three core objectives:

- **Prevent unauthorized access.** Apply strong authentication, continuous verification, and least-privilege policies to reduce the risk of initial compromise.
- **Limit the impact of breaches.** Use network segmentation, micro-perimeters, and adaptive controls to contain threats and prevent lateral movement.
- **Enhance visibility and control.** Use solutions like Secure Access Service Edge (SASE) to unify security policy enforcement, monitor traffic, and respond quickly to emerging threats across cloud and hybrid environments.

These objectives align with Zero Trust principles. 
They support modern solutions such as SASE, which integrates networking and security functions. 
This integration provides comprehensive protection and centralized management.

To make this happen, follow three Zero Trust principles:

- **Verify explicitly.** Always authenticate and authorize based on all available data points. Include user identity, network, location, device health, service or workload, user and device risk, data classification, and anomalies.
- **Use least-privileged access.** Limit user access with Just-In-Time and Just-Enough-Access (JIT/JEA), risk-based adaptive policies, and data protection to protect both data and productivity.
- **Assume breach.** Minimize influence radius for breaches and prevent lateral movement by segmenting access by network, user, devices, and application awareness. Verify all sessions are encrypted end to end. Use analytics to get [visibility](https://aka.ms/ZTCrossPillars), drive threat detection, and improve defenses.


## Zero Trust network deployment objectives

Zero Trust (ZT) is a security model that assumes no implicit trust and continuously verifies every access request. The Network Pillar in Zero Trust focuses on securing communications, segmenting environments, and enforcing least privilege access to resources.

When implementing an end-to-end Zero Trust framework for securing networks, we recommend you focus first on:

- [Network-Segmentation & Software-Defined Perimeters](#1-network-segmentation-and-software-defined-perimeters)
- [Secure Access Service Edge (SASE) & Zero Trust Network Access (ZTNA)](#2-secure-access-service-edge-sase-and-zero-trust-network-access-ztna)
- [Strong Encryption & Secure Communication](#3-strong-encryption-and-secure-communication)
- [Network Visibility & Threat Detection](#4-network-visibility-and-threat-detection)
- [Policy-Driven Access Control & Least Privilege](#5-policy-driven-access-control-and-least-privilege)

After these objectives are completed, focus on [objectives 6 and 7](#6-cloud-and-hybrid-network-security).


## Zero Trust network deployment guide

This guide walks you through the steps required to secure your networks following the principles of a Zero Trust security framework.

### 1. Network segmentation and software defined perimeters

Network segmentation and Software-Defined Perimeters (SDP) form the foundation of the Zero Trust security model. Instead of relying on static, perimeter-based controls, you enforce security dynamically at the resource level. When you partition your infrastructure into isolated segments using micro-segmentation, you restrict attackers’ lateral movement and minimize the effect of breaches. SDP strengthens this approach by creating on-demand, identity-centric micro perimeters around each user-resource interaction, and continuously validating context before granting access. In summary, follow these key principles:

- Restrict lateral movement by implementing fine-grained network segmentation (Macro & Micro segmentation).
- Utilize Software-Defined Networking (SDN) and Network Access Control (NAC) to dynamically enforce policies.
- Adopt identity-based segmentation over traditional IP-based methods.

#### 1.1 Macro segmentation strategy

Before diving into micro-segmentation, it's essential to establish a broader segmentation strategy. Macro segmentation involves dividing your network into larger segments based on overarching functional or security requirements. This approach simplifies initial management and provides a foundation upon which finer granularity, like micro-segmentation, can be built. 

#### 1.2 Network segmentation: Many ingress/egress cloud micro-perimeters with some micro-segmentation

Organizations shouldn't just have one single, large pipe in and out of their network. In a Zero Trust approach, networks are instead segmented into smaller islands where specific workloads are contained. Each segment has its own ingress and egress controls to minimize the effect of unauthorized access to data. By implementing software-defined perimeters with granular controls, you increase the difficulty for unauthorized actors to propagate throughout your network, and so reduce the lateral movement of threats.

There's no architecture design that fits the needs of all organizations. You have the option between a few [common design patterns](https://www.microsoft.com/security/blog/2020/06/15/zero-trust-part-1-networking/) for segmenting your network according to the Zero Trust model.

In this deployment guide, we walk you through the steps to achieve one of those designs: Micro-segmentation.

With micro-segmentation, organizations can move beyond simple centralized network-based perimeters to comprehensive and distributed segmentation using software-defined micro-perimeters.

#### 1.3 Network segmentation: Fully distributed ingress/egress cloud micro-perimeters and deeper micro-segmentation

Once you accomplish your initial three objectives, the next step is to further segment your network.

#### 1.4 Segment and enforce the external boundaries

:::image type="content" source="../media/diagram-servers-devices-boundaries-azure-vpn.png" alt-text="Diagram of servers and devices with connections across boundaries." border="true":::

Follow these steps, depending on the type of boundary:

##### Internet boundary

- To provide internet connectivity for your application route via the virtual network hub, [update the network security group rules](/azure/virtual-network/tutorial-filter-network-traffic) in virtual network hub.
- To protect the virtual network hub from volumetric network layer attacks and protocol attacks, [turn on Azure DDoS Network Protection](/azure/virtual-network/manage-ddos-protection#enable-ddos-for-an-existing-virtual-network).
- If your application uses HTTP/S protocols, [turn on Azure Web Application Firewall](/azure/web-application-firewall/afds/waf-front-door-custom-rules-powershell) to protect against Layer 7 threats.

> [!TIP]
> Azure DDoS Protection service also protects public IP addresses in virtual networks and not just IPs in the hub virtual network.
> Azure Firewall can also be used to control outbound internet connectivity. To learn more, see [Plan for inbound and outbound internet connectivity](/azure/cloud-adoption-framework/ready/azure-best-practices/plan-for-inbound-and-outbound-internet-connectivity).


##### On-premises boundary

- If your app needs connectivity to your on-premises data center or private cloud, use [Microsoft Entra Private Access](/azure/global-secure-access/), [Azure ExpressRoute](/azure/expressroute/expressroute-howto-circuit-portal-resource-manager), or [Azure VPN for connectivity to your virtual network hub](/azure/vpn-gateway/vpn-gateway-howto-site-to-site-resource-manager-portal). 
- To inspect and govern traffic in the virtual network hub, [Configure the Azure Firewall](/azure/firewall/tutorial-hybrid-ps).


##### PaaS services boundary

- When using Azure-provided PaaS services, Azure Storage, [Azure Cosmos DB](/azure/private-link/create-private-endpoint-cosmosdb-portal), or [Azure Web App](/azure/private-link/create-private-endpoint-webapp-portal), use the [PrivateLink](/azure/private-link/create-private-link-service-portal) connectivity option to ensure all data exchanges are over the private IP space and the traffic never leaves the Microsoft network.
- If your PaaS services require a secure boundary to communicate with each other and manage public network access, we suggest associating them to a network security perimeter. Private Link connectivity will be honored for traffic coming in through private endpoints of these PaaS services, ensuring all data exchanges are over private IP addresses and the traffic never leaves the Microsoft network.
[Learn more about Network Security Perimeter](/azure/private-link/network-security-perimeter-concepts) and see the [list of supported PaaS services](/azure/private-link/network-security-perimeter-concepts#onboarded-private-link-resources).

> [!TIP]
> [Learn about implementing an end-to-end Zero Trust strategy for data](https://aka.ms/ZTData).

##### Partition app components to different subnets

:::image type="content" source="../media/diagram-azure-region-virtual-network-servers.png" alt-text="Diagram of a virtual network of servers in the Azure region." border="true":::


Follow these steps:

1. Within the virtual network, [add virtual network subnets](/azure/virtual-network/virtual-network-manage-subnet) so that discrete components of an application can have their own perimeters.
1. To allow traffic only from the subnets that have an app subcomponent identified as a legitimate communications counterpart, [apply network security group rules](/azure/virtual-network/tutorial-filter-network-traffic#create-security-rules).

Alternatively, Azure firewall can also be used for segmentation and allowing traffic from specific subnets and Virtual Networks.

- Use Azure Firewall to filter traffic flowing between cloud resources, the internet, and on-premises resources. Use Azure Firewall or [Azure Firewall Manager](/azure/firewall-manager/overview) to create rules or policies that allow or deny traffic using layer 3 to layer 7 controls. To learn more, see [recommendations for building a segmentation strategy](/azure/well-architected/security/segmentation).

##### Applications are partitioned to different Azure Virtual Networks (VNets) and connected using a hub-spoke model

:::image type="content" source="../media/diagram-network-hub-spoke-two-regions.png" alt-text="Diagram of two virtual networks connected in a hub-and-spoke model." border="false":::

Follow these steps:

1. [Create dedicated virtual networks](/azure/virtual-network/quick-create-portal) for different applications and/or application components.
1. Create a central virtual network to set up the security posture for inter-app connectivity and connect the app VNets in [a hub-and-spoke architecture](/azure/architecture/reference-architectures/hybrid-networking/hub-spoke).
1. [Deploy Azure Firewall](/azure/firewall/deploy-ps) in the virtual network hub. Use Azure Firewall to inspect and govern network traffic.



#### 1.5 Validate segmentation with Network Watcher Traffic Analytics

To ensure that network segmentation is functioning as intended, organizations should implement [Azure Network Watcher Traffic Analytics](/security/zero-trust/azure-networking-visibility). This capability provides flow-level visibility by analyzing VNET flow Logs, enabling teams to monitor traffic patterns across segmented environments.

Traffic Analytics supports Zero Trust segmentation by:

- **Validating segmentation policies**: Identify whether traffic is flowing only between intended segments and detect any violations of segmentation boundaries.

- **Detecting lateral movement**: Surface unexpected or unauthorized east-west traffic that may indicate a breach or misconfiguration.

- **Enhancing visibility**: Correlate traffic flows with NSG rules and threat intelligence to gain actionable insights into network behavior.

- **Supporting continuous improvement**: Use analytics to refine micro-segmentation strategies and enforce least-privilege access dynamically.

By integrating Traffic Analytics into your Zero Trust deployment, you gain the ability to continuously assess and improve the effectiveness of your segmentation strategy—ensuring that your network boundaries are not only defined but actively monitored and enforced.

### 2. Secure Access Service Edge (SASE) and Zero Trust Network Access (ZTNA)

To effectively secure modern networks, organizations must move beyond legacy solutions and adopt advanced, integrated approaches. The move includes adopting Zero Trust Network Access (ZTNA) solutions for granular, identity-driven connectivity, applying SASE architectures to unify networking and security capabilities, and implementing continuous session validation with risk-based access controls. These strategies work together to ensure that access is always verified, threats are minimized, and security policies adapt dynamically to evolving risks.

#### 2.1 Zero Trust Network Access (ZTNA)

Zero Trust Network Access replaces broad, perimeter-based VPNs with fine-grained, identity-aware, and context-aware connectivity. The three core ZTNA capabilities, each described first for Microsoft Global Secure Access and then for Azure VPN Gateway options.

Microsoft’s implementation of ZTNA is part of the Global Secure Access (preview) capability under Microsoft Entra, built on the Security Service Edge (SSE) foundation.  
[Learn more: What is Global Secure Access? (Microsoft Entra)](/entra/global-secure-access/overview-what-is-global-secure-access)

#### 2.2 Modernize traditional VPNs with identity-aware ZTNA

**Global Secure Access**  
Microsoft’s Global Secure Access replaces broad network tunnels with app-specific, identity-driven connections. When a user requests access, Global Secure Access uses Microsoft Entra ID for single sign-on and Conditional Access at the edge—no inbound firewall rules are required. Only approved applications are visible in the user portal, and access decisions are based on device posture (from Defender for Endpoint) and real-time risk signals.

- [Global Secure Access overview](/entra/global-secure-access/overview-what-is-global-secure-access)
- [Private Access overview](/entra/global-secure-access/concept-private-access)

**Azure VPN Gateway**  
Modernize point-to-site (P2S) VPNs by integrating authentication with Microsoft Entra ID, enforcing Conditional Access policies (such as MFA, device compliance, and Named Locations) before establishing the tunnel. In Azure Virtual WAN hubs, P2S VPN and ExpressRoute operate at global scale, with centralized security and routing via Azure Firewall Manager. This approach maintains familiar VPN connectivity while ensuring least-privilege, identity-aware access.

- [Set up P2S VPN with Microsoft Entra ID authentication](/azure/vpn-gateway/point-to-site-about)
- [Azure Virtual WAN overview](/azure/virtual-wan/virtual-wan-about)

#### 2.3 Use SASE Architecture: Integrate Networking & Security Functions

**Integrate Networking & Security Functions with SASE**

**Global Secure Access**  
Global Secure Access brings Security Service Edge (SSE) capabilities—including Secure Web Gateway (SWG), Cloud Access Security Broker (CASB), and Firewall-as-a-Service (FWaaS)—into a unified SASE framework. User traffic, whether destined for the internet or private applications, is routed through Microsoft’s global edge network. Here, TLS inspection, URL filtering, data loss prevention (DLP), and threat intelligence are applied. Defender for Cloud Apps enables inline session control for SaaS applications, while Azure Firewall protects private app access.

- **SWG in Global Secure Access:** [Microsoft Entra Internet Access](/entra/global-secure-access/concept-internet-access)
- **CASB with Defender for Cloud Apps:** [What is Defender for Cloud Apps?](/defender-cloud-apps/what-is-defender-for-cloud-apps)

This architecture:
- Routes user traffic through Microsoft’s edge for centralized inspection and control
- Reduces complexity by unifying security policy enforcement
- Supports traffic steering and split tunneling for performance and compliance

**Azure VPN Gateway Integration**  
Traditional VPN endpoints can be integrated with Azure Firewall or partner SWG appliances using forced-tunnel configurations. The configuration allows outbound and inbound VPN traffic to be inspected and controlled with Azure Firewall Manager, threat intelligence, and Conditional Access session controls. You can apply URL filtering, deep packet inspection (DPI), and DLP to VPN sessions. Defender for Cloud Apps session policies can enforce upload/download controls and shadow IT discovery on tunneled traffic.

- [Learn about forced-tunnel VPN with Azure Firewall](/azure/firewall)

#### 2.4 Implement continuous session validation and risk-based access

Continuous session validation ensures that access decisions are enforced in real time, not just at the initial sign-in. This approach helps organizations respond quickly to changing risk conditions and maintain a strong security posture.

**Microsoft Global Secure Access**  
Zero Trust Network Access isn't a one-time check. Microsoft Global Secure Access uses Continuous Access Evaluation (CAE) to monitor risk signals—such as detected malware or unusual locations—and can revoke or reevaluate application access tokens and terminate network connectivity when risk is detected. Defender for Cloud Apps enforces live session controls, such as blocking downloads, quarantining sessions, or requiring extra multifactor authentication (MFA) during an active session. Automated response playbooks in Microsoft Sentinel or Microsoft Defender XDR can isolate compromised devices or disable accounts in real time.

- [Learn about Continuous Access Evaluation (CAE)](/entra/identity/conditional-access/concept-continuous-access-evaluation)
- [Learn about Defender for Cloud Apps session controls](/defender-cloud-apps/session-policy-aad)
- [Learn about Universal Continuous Access Evaluation (Preview)](/entra/global-secure-access/concept-universal-continuous-access-evaluation)

**Azure VPN Gateway**
For VPN connections using Microsoft Entra ID authentication, Continuous Access Evaluation (CAE) is supported. If Conditional Access detects a risky user or device, the VPN tunnel can be closed or require reauthentication. You can send VPN logs to Microsoft Sentinel and use automated playbooks to block IPs, revoke access, or alert security teams—enabling quick, risk-based responses for VPN connections.

- [VPN Gateway authentication with Microsoft Entra ID](/azure/vpn-gateway/openvpn-azure-ad-tenant)
- [Automate response with Microsoft Sentinel playbooks](/azure/sentinel/automation/create-playbooks)

### 3. Strong encryption and secure communication

Modern network communication must be strongly encrypted and secured at every stage. Organizations should:

- **Use Transport Layer Security (TLS) 1.3** and enforce end-to-end encryption for all network traffic. TLS 1.3 delivers stronger security, faster handshakes, and always-encrypted client authentication—essential for protecting modern workloads.
- **Enforce mutual authentication (mTLS)** between workloads and devices to ensure both client and server identities are verified, preventing unauthorized access even with valid credentials.
- **Block untrusted or legacy protocols** that lack encryption, such as TLS 1.0/1.1 or outdated ciphers.

> [!NOTE]
> While TLS secures legitimate traffic, threats like malware and data leakage can still be hidden within encrypted sessions. Microsoft Entra Internet Access TLS inspection provides visibility into encrypted traffic, enabling malware detection, data loss prevention, and advanced security controls. [Learn more about Transport Layer Security inspection](/entra/global-secure-access/concept-transport-layer-security).

> [!NOTE]
> Azure Firewall can perform TLS inspection on network traffic. It decrypts data, applies Intrusion Detection and Prevention System (IDPS) or application rules, then re-encrypts and forwards it. [Learn more about Azure Firewall TLS inspection](/azure/firewall/premium-features#tls-inspection) and [Azure Firewall Premium certificates](/azure/firewall/premium-certificates).

#### Key recommendations

- **Azure App Service & Azure Front Door:** Set the Minimum Inbound TLS Version to 1.3 to ensure only secure cipher suites are used for web apps. To learn more, see [Enforce minimum TLS version for App Service and Front Door](/azure/app-service/configure-ssl-certificate#enforce-minimum-tls-version).
- **Azure IoT Edge, IoT Hub, and other PaaS services:** Confirm device SDKs support TLS 1.3, or restrict to TLS 1.2+.
- **Azure Application Gateway (v2):** Supports mTLS using OCP-validated certificates for client verification. To learn more, see [Overview of TLS in App Service](/azure/app-service/overview-tls).
- **Encrypt application backend traffic between virtual networks.**
- **Encrypt traffic between on-premises and cloud:**
    - Configure site-to-site VPN over ExpressRoute Microsoft peering.
    - Use IPsec transport mode for ExpressRoute private peering.
    - Set up mTLS between servers across ExpressRoute private peering.

#### Block untrusted or legacy protocols

- **Azure endpoints (App Service, Storage, SQL, Event Hubs, etc.):** Accept only TLS 1.2+ and ideally enforce 1.3, disabling legacy versions.
- **Virtual Machines and Network Appliances:** Use Azure Policy and Microsoft Defender for Cloud to scan for outdated protocols (such as SMBv1 or custom TLS <1.2) and enforce remediation.
- **Operational hygiene:** Disable legacy ciphers and protocols at the OS or application level (for example, disable TLS 1.0/1.1 on Windows Server or SQL Server).

#### Prepare for Post-Quantum Cryptography (PQC)

Traditional public-key cryptographic algorithms (such as RSA and ECC) are vulnerable to future quantum computers. Microsoft has integrated quantum-resistant algorithms (LMS and ML-DSA, FIPS 204) into its platform, with broader PQC support coming soon. Begin transitioning to TLS 1.3 and prepare for PQC integration as standards are finalized.

#### 3.1 Encryption: User-to-app internal traffic is encrypted

Add encryption to ensure user-to-app internal traffic is encrypted.

Follow these steps:

1. Enforce HTTPS-only communication for your internet facing web applications by [redirecting HTTP traffic to HTTPS using Azure Front Door](/azure/frontdoor/front-door-how-to-redirect-https).
1. Connect remote employees/partners to Microsoft Azure using the [Azure VPN Gateway](/azure/vpn-gateway/vpn-gateway-about-vpngateways).
1. [Turn on encryption](/azure/vpn-gateway/vpn-gateway-security-controls#data-protection) for any point-to-site traffic in Azure VPN Gateway service.
1. Access your Azure virtual machines securely using encrypted communication via [Azure Bastion](/azure/bastion/bastion-overview).
1. [Connect using SSH to a Linux virtual machine](/azure/bastion/bastion-connect-vm-ssh).
1. [Connect using Remote Desktop Protocol (RDP) to a Windows virtual machine](/azure/bastion/bastion-connect-vm-rdp).

> [!TIP]
> [Learn about implementing an end-to-end Zero Trust strategy for applications](https://aka.ms/ZTApplications).

#### 3.2 Encryption: All traffic

Finally, complete your network protection by ensuring that all traffic is encrypted.

Follow these steps:
1. [Encrypt application backend traffic](/azure/vpn-gateway/vpn-gateway-ipsecikepolicy-rm-powershell) between virtual networks.
1. Encrypt traffic between on-premises and cloud:
    1. [Configure a site-to-site VPN](/azure/expressroute/site-to-site-vpn-over-microsoft-peering) over ExpressRoute Microsoft peering.
    1. [Configure IPsec transport mode](/azure/expressroute/expressroute-howto-ipsec-transport-private-windows) for ExpressRoute private peering.
    1. Configure mTLS between servers across ExpressRoute private peering.

### 4. Network visibility and threat detection

In a Zero Trust security model, the principle of “never trust, always verify” applies not just to users and devices, but also to network traffic. Monitoring and logging network activity is critical for enforcing Zero Trust because it provides continuous visibility into how resources are accessed, ensures compliance with security policies, and enables rapid detection of suspicious or unauthorized behavior. Below are the key elements, that this section will cover:

- Deploy Network Detection & Response (NDR) to monitor and analyze network traffic.
- Use DPI (Deep Packet Inspection) and AI-driven anomaly detection for real-time threat hunting.
- Maintain a centralized logging and SIEM/SOAR integration for network analysis.
- Deploy Extended Detection and Response (XDR) to analyze traffic patterns, identify anomalies, and prevent breaches.
- Integrate AI-driven analytics to enhance rapid responses to emerging threats.
- Enable improved threat detection and response by adopting Global Secure Access [source IP restoration](/entra/global-secure-access/how-to-source-ip-restoration).
- Utilize Global Secure Access [logs and monitoring](/entra/global-secure-access/concept-global-secure-access-logs-monitoring).

#### 4.1 Threat protection: Machine learning-based threat protection and filtering with context-based signals

For further threat protection, turn on [Azure DDoS Network Protection](/azure/virtual-network/ddos-protection-overview) to constantly monitor your Azure-hosted application traffic, use ML-based frameworks to baseline and detect volumetric traffic floods, detect protocol attacks, and apply automatic mitigations.

Follow these steps:
1. [Configure and manage](/azure/virtual-network/manage-ddos-protection) Azure DDoS Network Protection.
1. [Configure alerts](/azure/virtual-network/manage-ddos-protection#configure-alerts-for-ddos-protection-metrics) for DDoS protection metrics.
1. [Use Microsoft Sentinel with Azure Web Application Firewall](/azure/web-application-firewall/waf-sentinel)
1. [Use Azure Firewall with Microsoft Sentinel](/azure/firewall/firewall-sentinel-overview)


#### 4.2 Threat protection: Cloud native filtering and protection for known threats

Cloud applications that open endpoints to external environments, such as the internet or your on-premises footprint, are at risk of attacks coming in from those environments. It's therefore imperative that you scan the traffic for malicious payloads or logic.

These types of threats fall into two broad categories:

- **Known attacks**. Threats discovered by your software provider or the larger community. In such cases, the attack signature is available and you need to ensure that each request is checked against those signatures. The key is to be able to quickly update your detection engine with any newly identified attacks.

- **Unknown attacks.** These attacks are threats that don't quite match against any known signature. These types of threats include zero-day vulnerabilities and unusual patterns in request traffic. The ability to detect such attacks depends on how well your defenses know what's normal and what isn't. Your defenses should be constantly learning and updating such patterns as your business (and associated traffic) evolves.

Consider these steps to protect against known threats:

- Implement Microsoft Entra Internet Access capabilities such as [web content filtering](/entra/global-secure-access/how-to-configure-web-content-filtering) and [TLS inspection](/entra/global-secure-access/concept-transport-layer-security). To learn more, see [Learn about Microsoft Entra Internet Access for all apps](/entra/global-secure-access/concept-internet-access).

- Protect endpoints using [Azure Web Application Firewall (WAF)](/azure/web-application-firewall/overview) by:
    1. Turning on the default ruleset or [OWASP top 10](https://owasp.org/www-project-top-ten/) protection ruleset to protect against known web-layer attacks
    1. Turning on the bot protection ruleset to prevent malicious bots from scraping information, conducting credential stuffing, etc.
    1. Adding custom rules to protect against threats specific to your business.

    You can use one of two options:
    - [Azure Front Door](/azure/frontdoor/front-door-overview)
        - [Create a Web Application Firewall policy on Azure Front Door](/azure/web-application-firewall/afds/waf-front-door-create-portal).
        - [Configure bot protection for Web Application Firewall](/azure/web-application-firewall/afds/waf-front-door-policy-configure-bot-protection).
        - [Custom rules for Web Application Firewall](/azure/web-application-firewall/afds/waf-front-door-custom-rules-powershell).
    - [Azure Application Gateway](/azure/application-gateway/overview)
       - [Create an application gateway with a Web Application Firewall](/azure/web-application-firewall/ag/application-gateway-web-application-firewall-portal).
       - [Configure bot protection for Web Application Firewall](/azure/web-application-firewall/ag/bot-protection).
       - [Create and use Web Application Firewall v2 custom rules.](/azure/web-application-firewall/ag/create-custom-waf-rules).

- Front endpoints with [Azure Firewall](/azure/firewall/overview) for threat intelligence-based and IDPS filtering at Layer 4:
    - [Deploy and configure Azure Firewall](/azure/firewall/tutorial-firewall-deploy-portal) using the Azure portal.
    - [Enable threat intelligence-based filtering](/azure/firewall/threat-intel) for your traffic.
        > [!TIP]
        > [Learn about implementing an end-to-end Zero Trust strategy for endpoints](https://aka.ms/ZTEndpoints).
    - [Azure Firewall IDPS detects and prevents threats in network traffic when enabled](/azure/firewall/premium-features#idps)

#### 4.3 Monitoring and visibility

**Traffic Analytics**

**Network Watcher [Traffic Analytics](/azure/network-watcher/traffic-analytics-zero-trust)** plays a critical role in Zero Trust segmentation by analyzing VNET flow logs to detect anomalous traffic, validate segmentation policies, and uncover shadow IT or misconfigured access paths. It enables security teams to visualize traffic between segments and enforce adaptive controls based on real-time telemetry. 

**Log Analysis**

**Microsoft Defender Extended Detection and Response (XDR)**

Microsoft Defender Extended Detection and Response (XDR) is a unified enterprise defense suite you use before and after a breach. The suite coordinates detection, prevention, investigation, and response natively across endpoints, identities, email, and applications. Use Defender XDR to protect against and respond to sophisticated attacks.

- Investigate alerts
- Learn about Zero Trust with Defender XDR
- Learn about Defender XDR for US government

**Microsoft Sentinel**

Develop custom analytics queries and visualize collected data using workbooks.

- Detect threats with customized analytics rules
- Visualize collected data
- Use workbooks with Global Secure Access

**AI-Enabled Network Access**


**Microsoft Sentinel**

Use Azure Firewall to visualize firewall activities, detect threats with AI investigation capabilities, correlate activities, and automate response actions.

- Azure Firewall with Microsoft Sentinel

Microsoft Entra ID Protection uses machine learning (ML) algorithms to detect users and sign-in risk. Use risk conditions in Conditional Access policies for dynamic access, based on risk level.

- Microsoft Entra ID Protection
- Risk detections
- Risk-based access policies

**Global Secure Access**

By leveraging Microsoft Entra Global Secure Access logs, organizations can track access attempts, monitor data flows, and identify anomalies in real-time. This granular monitoring helps validate that only authorized identities and devices are accessing sensitive resources, supports incident response, and provides vital evidence for audits and investigations. Comprehensive traffic logging is therefore a foundational element in maintaining and proving the effectiveness of a Zero Trust architecture. Besides the traffic logs, additional logs are available for additional signals:

- [Global Secure Access logs and monitoring](/entra/global-secure-access/concept-global-secure-access-logs-monitoring)
- [Global Secure Access audit logs](/entra/global-secure-access/how-to-access-audit-logs)
- [Global Secure Access enriched Microsoft 365 logs](/entra/global-secure-access/how-to-view-enriched-logs)
- [Global Secure Access traffic logs](/entra/global-secure-access/how-to-view-traffic-logs)
- [Remote Network Health Logs](/entra/global-secure-access/how-to-remote-network-health-logs?tabs=microsoft-entra-admin-center)

#### 4.4 Automation and orchestration

Automation and orchestration are essential for enforcing Zero Trust principles across network infrastructure. By leveraging automatic enforcement, response, and governance, organizations can achieve secure and resilient connectivity.

##### Azure networking

Azure networking services—including Azure Firewall, Network Security Groups (NSGs), Virtual WAN, and DDoS Protection—can be deployed, governed, and monitored using Infrastructure as Code (IaC) tools such as ARM templates, Bicep, Terraform, and Azure Policy.

Key capabilities:

- **Automated deployment:** Use IaC pipelines to auto-deploy network segmentation (NSGs, Azure Firewall) and filtering controls.
- **Continuous compliance:** Enforce and auto-remediate security standards (e.g., block public IPs, require encryption) with Azure Policy.
- **DevOps integration:** Integrate with GitOps/DevOps workflows for declarative, version-controlled network configurations.

**Example:** Automatically deploy NSG rules and Azure Firewall policies when a new subnet is provisioned using Bicep and Azure DevOps.

- [Quickstart: Create an Azure Firewall and a firewall policy - Bicep](/azure/firewall-manager/quick-firewall-policy-bicep?tabs=CLI)
- [Secure pod traffic with network policies - Azure Kubernetes Service](/azure/aks/use-network-policies)

##### Microsoft Entra (Global Secure Access with Identity Governance)

Microsoft Entra Global Secure Access combines identity-aware access with network controls, moving beyond legacy VPNs. Identity Governance extends this with entitlement automation.

Key capabilities:

- **Automated onboarding:** Onboard apps/services into Private Access or App Proxy using Microsoft Graph APIs and policy templates.
- **Entitlement management:** Define network access packages with approval workflows, expirations, and access reviews.
- **Dynamic deprovisioning:** Automatically remove network entitlements based on role changes or lifecycle events.

**Example:** Assign an access package that grants Private Access to specific apps when a user joins a project, with enforced expiration and access review.

- [Automate access package assignments with Entitlement Management](/entra/id-governance/entitlement-management-access-package-assignments)

#### Microsoft Sentinel

Microsoft Sentinel provides playbooks (Logic Apps) to automate network threat detection and response.

Key capabilities:

- **Automated response:** Update NSG or Azure Firewall rules to block malicious IPs/domains.
- **Resource quarantine:** Disable sessions or quarantine resources by adjusting Conditional Access.
- **Alert enrichment:** Correlate network alerts with flow logs, DNS, identity, and device telemetry.

**Example:** Sentinel detects communication with a known malicious IP; a playbook updates Azure Firewall IP groups and notifies SecOps.

- [Playbook example: block malicious IP in Azure NSG](/azure/sentinel/automation/tutorial-respond-threats-playbook#playbook-example-block-malicious-ip-address-in-azure-nsg)
- [Automate threat response with Sentinel playbooks](/azure/sentinel/automation/tutorial-respond-threats-playbook)

##### Microsoft Defender XDR

Microsoft Defender XDR automates detection, investigation, and coordinated response across identity, endpoint, and network signals.

Key capabilities:

- **Correlation:** Detects lateral movement or anomalous network patterns using identity and device context.
- **Automated isolation:** Isolates compromised devices and triggers enforcement actions across platforms.
- **Integration:** Works with Sentinel and Entra for end-to-end incident response.

**Example:** Defender for Endpoint detects command-and-control (C2) traffic, XDR isolates the device, and triggers a Sentinel playbook to block the destination in Azure Firewall.

- [Automated investigation and response in Defender XDR](/defender-endpoint/automated-investigations?view=o365-worldwide&preserve-view=)


### 5. Policy-driven access control and least privilege

Modern Zero Trust networks require granular, adaptive access controls that enforce least privilege and respond dynamically to risk. Policy-driven access ensures users and devices only get the minimum permissions needed, for the shortest time required, and only under the right conditions.

#### 5.1 Implement context-aware access policies

- Use Microsoft Entra Conditional Access to define policies based on user, device, location, application, and risk signals.
- Start by [planning your Conditional Access deployment](/entra/identity/conditional-access/plan-conditional-access) to align policies with your organizational requirements.
- Accelerate deployment with [Conditional Access policy templates](/entra/identity/conditional-access/concept-conditional-access-policy-common) for common scenarios.

#### 5.2 Enforce risk-based and adaptive controls

- Require multifactor authentication (MFA) when risk is detected, such as unfamiliar sign-ins or risky devices.
- Use [sign-in risk-based MFA](/entra/identity/conditional-access/howto-conditional-access-policy-risk) to automatically prompt for MFA based on real-time risk assessment.
- Understand [risk detections in Microsoft Entra ID Protection](/entra/id-protection/concept-identity-protection-risks) to inform policy decisions and automate remediation.

#### 5.3 Apply Just-in-Time (JIT) and privileged access

- Enforce Just-in-Time (JIT) access using Privileged Identity Management (PIM) to grant elevated permissions only when needed.
- [Secure private application access with PIM and Global Secure Access](/entra/global-secure-access/how-to-configure-global-access-with-pim) to reduce standing privileges and limit exposure.

#### 5.4 Hybrid and application-specific access

- For hybrid environments, configure per-app access policies using [Global Secure Access Applications](/entra/global-secure-access/how-to-configure-per-app-access).
- Enable secure remote administration by [using SSH with Microsoft Entra Private Access](/entra/global-secure-access/how-to-manage-ssh-server-administration) for granular, policy-driven server access.

#### 5.5 Deny-by-default and continuous evaluation

- Apply deny-by-default principles at all network layers, granting access only when explicitly allowed by policy.
- Continuously evaluate session risk and enforce policy changes in real time to minimize attack surface.

Use context-aware, risk-based, and least-privilege policies to reduce unauthorized access and limit lateral movement in your network.


### 6. Cloud and hybrid network security

Securing cloud and hybrid environments requires a combination of modern, cloud-native controls and consistent policy enforcement across all platforms. As organizations adopt multicloud and hybrid architectures, it's essential to extend Zero Trust principles beyond traditional data centers to cloud workloads, SaaS, and PaaS environments.

#### 6.1 Secure cloud workloads with micro-perimeters and cloud-native firewalls

- **Micro-perimeters:** Use micro-segmentation to create granular security boundaries around individual workloads, applications, or services. This limits lateral movement and contains potential breaches within isolated segments.
- **Cloud-native firewalls:** Deploy solutions like [Azure Firewall](/azure/firewall/overview) to inspect and control traffic between cloud workloads, enforce threat intelligence-based filtering, and apply application and network rules at scale.
- **Network Security Groups (NSGs):** Use Network Security Groups (NSGs) and [Application Security Groups](/azure/virtual-network/application-security-groups) to define and enforce fine-grained access controls for resources within virtual networks.
- **Private endpoints:** Use [Azure Private Link](/azure/private-link/private-link-overview) to restrict access to PaaS services over private IP addresses, ensuring traffic stays within the trusted Microsoft backbone.

#### 6.2 Integrate identity-aware proxies for SaaS and PaaS security

- **Identity-aware proxies:** Implement solutions such as [Microsoft Entra Private Access](/entra/global-secure-access/concept-private-access) to broker access to SaaS and PaaS applications. These proxies enforce authentication, device compliance, and Conditional Access policies before granting access. Consider [Microsoft Entra Internet Access](/entra/global-secure-access/concept-internet-access) for identity-aware internet access.
- **Cloud Access Security Broker (CASB):** Use [Microsoft Defender for Cloud Apps](/defender-cloud-apps/what-is-defender-for-cloud-apps) to discover, monitor, and control SaaS usage, enforce data loss prevention (DLP), and apply session controls for cloud applications.
- **Continuous session validation:** Apply risk-based, real-time policy enforcement for SaaS and PaaS access, including adaptive controls based on user, device, and session context.

#### 6.3 Ensure consistent security policy enforcement across hybrid and multicloud environments

- **Unified policy management:** Use platforms like [Microsoft Entra Conditional Access](/entra/identity/conditional-access/overview) and [Azure Policy](/azure/governance/policy/overview) to define and enforce consistent security policies across on-premises, Azure, and other cloud providers.
- **Hybrid connectivity:** Secure hybrid connections using [Azure VPN Gateway](/azure/vpn-gateway/vpn-gateway-about-vpngateways), [ExpressRoute](/azure/expressroute/expressroute-introduction), and enforce encryption and access controls for all cross-environment traffic.
- **Centralized monitoring and response:** Integrate logs and security events from all environments into [Microsoft Sentinel](/azure/sentinel/overview) or your SIEM/SOAR platform for unified visibility, threat detection, and automated response.
- **Multicloud security posture management:** Use tools like [Microsoft Defender for Cloud](/azure/defender-for-cloud/defender-for-cloud-introduction) to assess, monitor, and improve the security posture of resources across Azure and other cloud providers.

Organizations that implement these strategies can achieve robust, end-to-end security for cloud and hybrid networks. The approach ensures Zero Trust principles are consistently applied, regardless of where workloads and data reside.


### 7. Discontinue legacy network security technology

Zero Trust rejects implicit trust in any network segment or device. Legacy perimeter-centric controls—such as flat VPN tunnels, “hair-pin” traffic inspection, hard-coded access control lists (ACLs), and static network firewalls—no longer provide the adaptive, identity-aware, and context-aware protection required for modern hybrid and cloud-native environments. To fully realize Zero Trust, organizations must retire these outdated technologies in favor of identity-driven, software-defined security services.

#### 7.1 Scope of retirement

Legacy technologies to retire include:

- **Traditional VPNs** that grant broad network access based solely on device certificates or shared keys.
- **Rigid network firewalls** with static rule sets and limited application-level visibility.
- **Legacy web proxies** that lack inline threat inspection or session control.
- **Network ACLs or route-based segmentation** without integration into identity or device posture signals.

#### 7.2 Replacement principles

For each deprecated control, adopt a modern Zero Trust alternative that:

- Enforces least-privilege access at the application or workload layer using Zero Trust Network Access.
- Integrates identity and device posture (using Microsoft Entra ID and Microsoft Defender for Endpoint) into every access decision.
- Provides continuous validation with Continuous Access Evaluation and session reevaluation.
- Delivers software-defined visibility and control through Secure Access Service Edge (SASE) and Security Service Edge (SSE) solutions, such as Secure Web Gateway (SWG), Cloud Access Security Broker (CASB), Firewall-as-a-Service (FWaaS), and Network Detection and Response (NDR).

#### 7.3 Transition strategy

1. **Inventory and prioritize**
    - Catalog all legacy appliances and VPN profiles.
    - Classify by criticality (public-facing apps, partner connectivity, remote administration).

2. **Pilot and validate**
    - Stand up ZTNA pilots using Microsoft Global Secure Access or Azure VPN Gateway with Microsoft Entra ID authentication for low-risk application sets.
    - Validate connectivity, performance, and policy enforcement.

3. **Phased ramp-down**
    - Migrate user cohorts and application groups in waves, monitoring success metrics (such as time-to-access, helpdesk tickets, and security alerts).
    - Simultaneously redirect traffic through your chosen SASE or SSE stack.

4. **Formal decommission**
    - Retire hardware appliances and revoke legacy VPN configurations.
    - Update network diagrams and operational runbooks to remove deprecated technology.

## Products covered in this guide

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

Securing networks is central to a successful Zero Trust strategy. For further information or help with implementation, contact your Customer Success team or continue to read through the other chapters of this guide, which spans all Zero Trust pillars.
