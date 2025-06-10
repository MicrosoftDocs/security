---
title: Secure networks with Zero Trust
description: Learn how to secure networks using a Zero Trust strategy with Secure Access Service Edge (SASE) and Secure Service Edge (SSE) solutions.
ms.date: 05/16/2025
ms.service: security
author: kenwith
manager: femila
ms.author: kenwith
ms.topic: concept-article
ms.collection:
  - zerotrust-pillar

#customer intent: As an administrator, I want to understand how I can adopt modern Zero Trust security practices so that I can secure my network and organization.
---

# Secure networks with Zero Trust

Network security changed a lot in recent years. Instead of relying on a single perimeter, organizations now use risk-based policies to control both internal and external traffic. This means isolating hosts, enforcing encryption, segmenting networks, and improving visibility across the enterprise. Security controls are now placed closer to applications and data, making it easier to protect resources and respond to threats. Each application can have its own security settings based on its specific needs for access and connectivity.

The emergence of Secure Access Service Edge (SASE) represents a paradigm shift in how organizations approach network security. SASE converges networking and security functions into a single, unified service. SASE offers a more streamlined and effective way to protect data and applications, regardless of where they're located. This modern approach not only simplifies the management of security policies but also enhances the overall security posture of the organization. Artificial Intelligence (AI) is playing a pivotal role in this new era of network security. AI-driven solutions are capable of analyzing vast amounts of data in real-time, identifying potential threats, and responding to incidents with unprecedented speed and accuracy. By applying AI, organizations can proactively detect and mitigate security risks, ensuring a more robust and resilient network infrastructure.

In summary, the adoption of SASE, coupled with the integration of AI, marks a significant advancement in the field of network security. These innovations are enabling organizations to stay ahead of emerging threats and maintain a secure and efficient network environment.

## Key Principles of the Zero Trust Network Model

Instead of assuming that everything behind the corporate firewall is secure, an end-to-end Zero Trust strategy acknowledges that breaches are inevitable. This approach requires verifying each request as if it originates from an uncontrolled network, with identity management playing a crucial role. When organizations incorporate the Cybersecurity and Infrastructure Security Agency (CISA) and National Institute of Standards and Technology (NIST) Zero Trust models and patterns, they enhance their security posture and better protect their networks.

In the Zero Trust model, securing your networks focuses on three core objectives:

- **Prevent unauthorized access.** Apply strong authentication, continuous verification, and least-privilege policies to reduce the risk of initial compromise.
- **Limit the impact of breaches.** Use network segmentation, micro-perimeters, and adaptive controls to contain threats and prevent lateral movement.
- **Enhance visibility and control.** Leverage solutions like Secure Access Service Edge (SASE) to unify security policy enforcement, monitor traffic, and respond quickly to emerging threats across cloud and hybrid environments.

These objectives align with Zero Trust principles and are supported by modern solutions such as SASE, which integrates networking and security functions to provide comprehensive protection and centralized management.

To make this happen, follow three Zero Trust principles:

- **Verify explicitly.** Always authenticate and authorize based on all available data points. Include user identity, network, location, device health, service or workload, user and device risk, data classification, and anomalies.
- **Use least-privileged access.** Limit user access with Just-In-Time and Just-Enough-Access (JIT/JEA), risk-based adaptive policies, and data protection to protect both data and productivity.
- **Assume breach.** Minimize influence radius for breaches and prevent lateral movement by segmenting access by network, user, devices, and application awareness. Verify all sessions are encrypted end to end. Use analytics to get [visibility](https://aka.ms/ZTCrossPillars), drive threat detection, and improve defenses.


## Zero Trust network deployment objectives

Before most organizations start their Zero Trust journey, they have network security that is characterized as:
- Minimal or no identity awareness for network traffic.
- Limited or no risk based policy decision capabilities.
- Limited or no governance or lifecycle for application access.

Zero Trust (ZT) is a security model that assumes no implicit trust and continuously verifies every access request. The Network Pillar in Zero Trust focuses on securing communications, segmenting environments, and enforcing least privilege access to resources.

When implementing an end-to-end Zero Trust framework for securing networks, we recommend you focus first on [objectives 1 through 4](#1-network-segmentation--software-defined-perimeters). After these objectives are completed, focus on [objectives 5 through 7](#7-discontinue-legacy-network-security-technology).

## Zero Trust networking deployment guide

This guide walks you through the steps required to secure your networks following the principles of a Zero Trust security framework.

### 1. Network-Segmentation & Software-Defined Perimeters

Network segmentation and Software-Defined Perimeters (SDP) form the foundation of the Zero Trust security model. Instead of relying on static, perimeter-based controls, you enforce security dynamically at the resource level. When you partition your infrastructure into isolated segments using micro-segmentation, you restrict attackers’ lateral movement and minimize the effect of breaches. SDP strengthens this approach by creating on-demand, identity-centric "micro-perimeters" around each user-resource interaction and continuously validating context before granting access. In summary, follow these key principles:

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


##### On-premises boundary

- If your app needs connectivity to your on-premises data center or private cloud, use [Microsoft Entra Private Access](/azure/global-secure-access/), [Azure ExpressRoute](/azure/expressroute/expressroute-howto-circuit-portal-resource-manager), or [Azure VPN for connectivity to your virtual network hub](/azure/vpn-gateway/vpn-gateway-howto-site-to-site-resource-manager-portal). 
- To inspect and govern traffic in the virtual network hub, [Configure the Azure Firewall](/azure/firewall/tutorial-hybrid-ps).


##### PaaS services boundary

 - When using Azure-provided PaaS services, (Azure Storage, [Azure Cosmos DB](/azure/private-link/create-private-endpoint-cosmosdb-portal),
    or [Azure Web App](/azure/private-link/create-private-endpoint-webapp-portal), use the [PrivateLink](/azure/private-link/create-private-link-service-portal) connectivity option to ensure all data exchanges are over the private IP space and the traffic never leaves the Microsoft network.

> [!TIP]
> [Learn about implementing an end-to-end Zero Trust strategy for data](https://aka.ms/ZTData).

##### Partition app components to different subnets

:::image type="content" source="../media/diagram-azure-region-virtual-network-servers.png" alt-text="Diagram of a virtual network of servers in the Azure region." border="true":::


Follow these steps:

- Within the virtual network, [add virtual network subnets](/azure/virtual-network/virtual-network-manage-subnet) so that discrete components of an application can have their own perimeters.
- To allow traffic only from the subnets that have an app subcomponent identified as a legitimate communications counterpart, [apply network security group rules](/azure/virtual-network/tutorial-filter-network-traffic#create-security-rules).

##### Applications are partitioned to different Azure Virtual Networks (VNets) and connected using a hub-spoke model

:::image type="content" source="../media/diagram-network-hub-spoke-two-regions.png" alt-text="Diagram of two virtual networks connected in a hub-and-spoke model." border="false":::

Follow these steps:

- [Create dedicated virtual networks](/azure/virtual-network/quick-create-portal) for different applications and/or application components.

- Create a central virtual network to set up the security posture for inter-app connectivity and connect the app VNets in [a hub-and-spoke architecture](/azure/architecture/reference-architectures/hybrid-networking/hub-spoke).

- [Deploy Azure Firewall](/azure/firewall/deploy-ps) in the virtual network hub. Use Azure Firewall to inspect and govern network traffic.



### 2. Secure Access Service Edge (SASE) & Zero Trust Network Access (ZTNA)

To effectively secure modern networks, organizations must move beyond legacy solutions and adopt advanced, integrated approaches. The move includes adopting Zero Trust Network Access (ZTNA) solutions for granular, identity-driven connectivity, applying SASE architectures to unify networking and security capabilities, and implementing continuous session validation with risk-based access controls. These strategies work together to ensure that access is always verified, threats are minimized, and security policies adapt dynamically to evolving risks.

#### 2.1 Zero Trust Network Access (ZTNA)

Zero Trust Network Access replaces broad, perimeter-based VPNs with fine-grained, identity- and context-aware connectivity. Below are three core ZTNA capabilities, each described first for Microsoft Global Secure Access (GSA) and then for Azure VPN Gateway options.

Microsoft’s implementation of ZTNA is part of the Global Secure Access (preview) capability under Microsoft Entra, built on the Security Service Edge (SSE) foundation.  
[Learn more: What is Global Secure Access? (Microsoft Entra)](/entra/global-secure-access/overview-what-is-global-secure-access)

##### Modernize Traditional VPNs with Identity-Aware ZTNA

**Global Secure Access**  
Microsoft’s Global Secure Access replaces broad network tunnels with app-specific, identity-driven connections. When a user requests access, GSA uses Microsoft Entra ID for single sign-on and Conditional Access at the edge—no inbound firewall rules are required. Only approved applications are visible in the user portal, and access decisions are based on device posture (from Defender for Endpoint) and real-time risk signals.

- [Learn more: What is Global Secure Access?](/entra/global-secure-access/overview-what-is-global-secure-access)
- [Private Access overview](/entra/global-secure-access/concept-private-access)

**Azure VPN Gateway**  
Modernize point-to-site (P2S) VPNs by integrating authentication with Microsoft Entra ID, enforcing Conditional Access policies (such as MFA, device compliance, and Named Locations) before establishing the tunnel. In Azure Virtual WAN hubs, P2S VPN and ExpressRoute operate at global scale, with centralized security and routing via Azure Firewall Manager. This approach maintains familiar VPN connectivity while ensuring least-privilege, identity-aware access.

- [Set up P2S VPN with Azure AD authentication](/azure/vpn-gateway/point-to-site-about)
- [Azure Virtual WAN overview](/azure/virtual-wan/virtual-wan-about)

##### Use SASE Architecture: Integrate Networking & Security Functions

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
Traditional VPN endpoints can be integrated with Azure Firewall or partner SWG appliances using forced-tunnel configurations. This allows outbound and inbound VPN traffic to be inspected and controlled with Azure Firewall Manager, threat intelligence, and Conditional Access session controls. You can apply URL filtering, deep packet inspection (DPI), and DLP to VPN sessions. Defender for Cloud Apps session policies can enforce upload/download controls and shadow IT discovery on tunneled traffic.

- [Learn about forced-tunnel VPN with Azure Firewall](/azure/firewall)

##### Implement Continuous Session Validation & Risk-Based Access

Continuous session validation ensures that access decisions are enforced in real time, not just at the initial sign-in. This approach helps organizations respond quickly to changing risk conditions and maintain a strong security posture.

**Microsoft Global Secure Access**  
Zero Trust Network Access (ZTNA) is not a one-time check. Microsoft Global Secure Access uses Continuous Access Evaluation (CAE) to monitor risk signals—such as detected malware or unusual locations—and can revoke or re-evaluate application access tokens and terminate network connectivity when risk is detected. Defender for Cloud Apps enforces live session controls, such as blocking downloads, quarantining sessions, or requiring additional multifactor authentication (MFA) during an active session. Automated response playbooks in Microsoft Sentinel or Microsoft 365 Defender can isolate compromised devices or disable accounts in real time.

- [Learn about Continuous Access Evaluation (CAE)](/entra/identity/conditional-access/concept-continuous-access-evaluation)
- [Defender for Cloud Apps session controls](/defender-cloud-apps/session-policy-aad)
- [Universal Continuous Access Evaluation (Preview)](/entra/global-secure-access/concept-universal-continuous-access-evaluation)

**Azure VPN Gateway**
For VPN connections authenticated with Microsoft Entra ID, Continuous Access Evaluation applies as well. If Conditional Access detects a compromised device or increased user risk, the point-to-site (P2S) or Virtual WAN tunnel can be terminated or forced to re-authenticate. By sending VPN logs to Microsoft Sentinel using Diagnostic Settings, you can trigger Logic App playbooks to block IP addresses, revoke tokens, or notify security teams—enabling real-time, risk-based decisions for traditional VPNs.

- [VPN Gateway authentication with Microsoft Entra ID](/azure/vpn-gateway/openvpn-azure-ad-tenant)
- [Automate response with Microsoft Sentinel playbooks](/azure/sentinel/automation/create-playbooks)

### 3. Strong Encryption & Secure Communication

- Use Transport Layer Security (TLS) 1.3+ and end-to-end encryption for all network traffic.
- Enforce mutual authentication (mTLS) between workloads and devices.
- Block untrusted or legacy protocols that lack encryption.

#### 3.1 Encryption: User-to-app internal traffic is encrypted

Add encryption to ensure user-to-app internal traffic is encrypted.

Follow these steps:

- Enforce HTTPS-only communication for your internet facing web applications by [redirecting HTTP traffic to HTTPS using Azure Front Door](/azure/frontdoor/front-door-how-to-redirect-https).
- Connect remote employees/partners to Microsoft Azure using the [Azure VPN Gateway](/azure/vpn-gateway/vpn-gateway-about-vpngateways).
    - [Turn on encryption](/azure/vpn-gateway/vpn-gateway-security-controls#data-protection) for any point-to-site traffic in Azure VPN Gateway service.
- Access your Azure virtual machines securely using encrypted communication via [Azure Bastion](/azure/bastion/bastion-overview).
- [Connect using SSH to a Linux virtual machine](/azure/bastion/bastion-connect-vm-ssh).
- [Connect using Remote Desktop Protocol (RDP) to a Windows virtual machine](/azure/bastion/bastion-connect-vm-rdp).

> [!TIP]
> [Learn about implementing an end-to-end Zero Trust strategy for applications](https://aka.ms/ZTApplications).

#### 3.2 Encryption: All traffic

Finally, complete your network protection by ensuring that all traffic is encrypted.

Follow these steps:

- [Encrypt application backend traffic](/azure/vpn-gateway/vpn-gateway-ipsecikepolicy-rm-powershell) between virtual networks.
- Encrypt traffic between on-premises and cloud:
    - [Configure a site-to-site VPN](/azure/expressroute/site-to-site-vpn-over-microsoft-peering) over ExpressRoute Microsoft peering.
    - [Configure IPsec transport mode](/azure/expressroute/expressroute-howto-ipsec-transport-private-windows) for ExpressRoute private peering.
    - Configure mTLS between servers across ExpressRoute private peering.

### 4. Network Visibility & Threat Detection

- Deploy Network Detection & Response (NDR) to monitor and analyze network traffic.
- Use DPI (Deep Packet Inspection) and AI-driven anomaly detection for real-time threat hunting.
- Maintain a centralized logging and SIEM/SOAR integration for network analysis.
- Deploy Extended Detection and Response (XDR) to analyze traffic patterns, identify anomalies, and prevent breaches.
- Integrate AI-driven analytics to enhance rapid responses to emerging threats.
- Enable improved threat detection and response by adopting Global Secure Access [source IP restoration](/entra/global-secure-access/how-to-source-ip-restoration).
- Utilize Global Secure Access [logs and monitoring](/entra/global-secure-access/concept-global-secure-access-logs-monitoring).

#### 4.1 Threat protection: Machine learning-based threat protection and filtering with context-based signals

For further threat protection, turn on [Azure DDoS Protection Standard](/azure/virtual-network/ddos-protection-overview) to constantly monitor your Azure-hosted application traffic, use ML-based frameworks to baseline and detect volumetric traffic floods, and apply automatic mitigations.

Follow these steps:

- [Configure and manage](/azure/virtual-network/manage-ddos-protection) Azure DDoS Network Protection.
- [Configure alerts](/azure/virtual-network/manage-ddos-protection#configure-alerts-for-ddos-protection-metrics) for DDoS protection metrics.


#### 4.2 Threat protection: Cloud native filtering and protection for known threats

Cloud applications that open endpoints to external environments, such as the internet or your on-premises footprint, are at risk of attacks coming in from those environments. It's therefore imperative that you scan the traffic for malicious payloads or logic.

These types of threats fall into two broad categories:

- **Known attacks**. Threats discovered by your software provider or the larger community. In such cases, the attack signature is available and you need to ensure that each request is checked against those signatures. The key is to be able to quickly update your detection engine with any newly identified attacks.

- **Unknown attacks.** These attacks are threats that don't quite match against any known signature. These types of threats include zero-day vulnerabilities and unusual patterns in request traffic. The ability to detect such attacks depends on how well your defenses know what's normal and what isn't. Your defenses should be constantly learning and updating such patterns as your business (and associated traffic) evolves.

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

#### 4.3 Monitoring and Visibility

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

**Microsoft Entra ID Protection**

Microsoft Entra ID Protection uses machine learning (ML) algorithms to detect users and sign-in risk. Use risk conditions in Conditional Access policies for dynamic access, based on risk level.

- Microsoft Entra ID Protection
- Risk detections
- Risk-based access policies

**Global Secure Access**

Apply Conditional Access policies with risk conditions to network access to Microsoft Entra Private Access apps, Quick access apps, and Global Secure Access traffic forwarding profiles.

- [Global Secure Access overview](/entra/global-secure-access/overview-what-is-global-secure-access)
- [Learn about Microsoft Entra Private Access](/entra/global-secure-access/concept-private-access)
- [Universal Conditional Access](/entra/global-secure-access/concept-universal-conditional-access)
- [Enable compliant network check with Conditional Access](/entra/global-secure-access/how-to-compliant-network)


#### 4.4 Automation and Orchestration

**Microsoft Sentinel**

Detect advanced multistage attacks with Fusion and User and Entity Behavior Analytics (UEBA) anomalies in Microsoft Sentinel by enabling analytic rules. Design automation rules and playbooks for security response.

**Microsoft Entra ID Governance**

Zero Trust requires that user and service identities are provisioned, updated, and decommissioned promptly and consistently. Microsoft Entra Identity Governance provides:

- **Lifecycle Workflows (Joiner-Mover-Leaver):** Automate user lifecycle processes by integrating with HR systems or other authoritative sources.
- **Entitlement Management & Access Packages:** Define catalogs of application access packages for both cloud and on-premises apps (published via Private Access or Application Proxy). Automate assignment workflows, including request, approval, and periodic access reviews.
- **Access Reviews:** Schedule automated access reviews for all applications. Microsoft Entra ID can send review tasks to application owners or business stakeholders, consolidated across cloud and on-premises apps. Automate escalation and remediation—if a reviewer doesn’t respond, disable access; if an account is flagged, trigger a workflow to investigate.

**Automated Workflows**

**Microsoft Defender Extended Detection and Response (XDR)**

Configure automated investigation and response capabilities in Microsoft Defender Extended Detection and Response (XDR). 
- Automated investigation and response overview

**Microsoft Sentinel playbooks**

Microsoft Sentinel playbooks are based on Logic Apps, a cloud service that schedules, automates, and orchestrates tasks and workflows across enterprise systems. Build response playbooks with templates. Deploy solutions from the Microsoft Sentinel content hub. Build custom analytics rules and response actions with Azure Logic Apps.
- Build Microsoft Sentinel playbooks from templates
- Automate threat response with playbooks
- Locate the Microsoft Sentinel content hub catalog
- Learn about Azure Logic Apps

**AI Driven by Analytics decides A&O modifications**

**Microsoft Sentinel**

Enable analytic rules to detect advanced multistage attacks with Fusion and UEBA anomalies in Microsoft Sentinel. Design automation rules and playbooks for security response.


### 5. Policy-Driven Access Control & Least Privilege

Modern Zero Trust networks require granular, adaptive access controls that enforce least privilege and respond dynamically to risk. Policy-driven access ensures users and devices only get the minimum permissions needed, for the shortest time required, and only under the right conditions.

#### 5.1 Implement Context-Aware Access Policies

- Use Microsoft Entra Conditional Access to define policies based on user, device, location, application, and risk signals.
- Start by [planning your Conditional Access deployment](/entra/identity/conditional-access/plan-conditional-access) to align policies with your organizational requirements.
- Accelerate deployment with [Conditional Access policy templates](/entra/identity/conditional-access/concept-conditional-access-policy-common) for common scenarios.

#### 5.2 Enforce Risk-Based and Adaptive Controls

- Require multifactor authentication (MFA) when risk is detected, such as unfamiliar sign-ins or risky devices.
- Use [sign-in risk-based MFA](/entra/identity/conditional-access/howto-conditional-access-policy-risk) to automatically prompt for MFA based on real-time risk assessment.
- Understand [risk detections in Microsoft Entra ID Protection](/entra/id-protection/concept-identity-protection-risks) to inform policy decisions and automate remediation.

#### 5.3 Apply Just-in-Time (JIT) and Privileged Access

- Enforce Just-in-Time (JIT) access using Privileged Identity Management (PIM) to grant elevated permissions only when needed.
- [Secure private application access with PIM and Global Secure Access](/entra/global-secure-access/how-to-configure-global-access-with-pim) to reduce standing privileges and limit exposure.

#### 5.4 Hybrid and Application-Specific Access

- For hybrid environments, configure per-app access policies using [Global Secure Access Applications](/entra/global-secure-access/how-to-configure-per-app-access).
- Enable secure remote administration by [using SSH with Microsoft Entra Private Access](/entra/global-secure-access/how-to-manage-ssh-server-administration) for granular, policy-driven server access.

#### 5.5 Deny-by-Default and Continuous Evaluation

- Apply deny-by-default principles at all network layers, granting access only when explicitly allowed by policy.
- Continuously evaluate session risk and enforce policy changes in real time to minimize attack surface.

Use context-aware, risk-based, and least-privilege policies to reduce unauthorized access and limit lateral movement in your network.


### 6. Cloud & Hybrid Network Security

Securing cloud and hybrid environments requires a combination of modern, cloud-native controls and consistent policy enforcement across all platforms. As organizations adopt multicloud and hybrid architectures, it's essential to extend Zero Trust principles beyond traditional data centers to cloud workloads, SaaS, and PaaS environments.

#### 6.1 Secure Cloud Workloads with Micro-Perimeters and Cloud-Native Firewalls

- **Micro-perimeters:** Use micro-segmentation to create granular security boundaries around individual workloads, applications, or services. This limits lateral movement and contains potential breaches within isolated segments.
- **Cloud-native firewalls:** Deploy solutions like [Azure Firewall](/azure/firewall/overview) to inspect and control traffic between cloud workloads, enforce threat intelligence-based filtering, and apply application and network rules at scale.
- **Network Security Groups (NSGs):** Use Network Security Groups (NSGs) and [Application Security Groups](/azure/virtual-network/application-security-groups) to define and enforce fine-grained access controls for resources within virtual networks.
- **Private endpoints:** Use [Azure Private Link](/azure/private-link/private-link-overview) to restrict access to PaaS services over private IP addresses, ensuring traffic stays within the trusted Microsoft backbone.

#### 6.2 Integrate Identity-Aware Proxies for SaaS and PaaS Security

- **Identity-aware proxies:** Implement solutions such as [Microsoft Entra Private Access](/entra/global-secure-access/concept-private-access) to broker access to SaaS and PaaS applications. These proxies enforce authentication, device compliance, and Conditional Access policies before granting access. Consider [Microsoft Entra Internet Access](/entra/global-secure-access/concept-internet-access) for identity-aware internet access.
- **Cloud Access Security Broker (CASB):** Use [Microsoft Defender for Cloud Apps](/defender-cloud-apps/what-is-defender-for-cloud-apps) to discover, monitor, and control SaaS usage, enforce data loss prevention (DLP), and apply session controls for cloud applications.
- **Continuous session validation:** Apply risk-based, real-time policy enforcement for SaaS and PaaS access, including adaptive controls based on user, device, and session context.

#### 6.3 Ensure Consistent Security Policy Enforcement Across Hybrid and Multicloud Environments

- **Unified policy management:** Use platforms like [Microsoft Entra Conditional Access](/entra/identity/conditional-access/overview) and [Azure Policy](/azure/governance/policy/overview) to define and enforce consistent security policies across on-premises, Azure, and other cloud providers.
- **Hybrid connectivity:** Secure hybrid connections using [Azure VPN Gateway](/azure/vpn-gateway/vpn-gateway-about-vpngateways), [ExpressRoute](/azure/expressroute/expressroute-introduction), and enforce encryption and access controls for all cross-environment traffic.
- **Centralized monitoring and response:** Integrate logs and security events from all environments into [Microsoft Sentinel](/azure/sentinel/overview) or your SIEM/SOAR platform for unified visibility, threat detection, and automated response.
- **Multicloud security posture management:** Use tools like [Microsoft Defender for Cloud](/azure/defender-for-cloud/defender-for-cloud-introduction) to assess, monitor, and improve the security posture of resources across Azure and other cloud providers.

Organizations that implement these strategies can achieve robust, end-to-end security for cloud and hybrid networks. This approach ensures that Zero Trust principles are consistently applied, regardless of where workloads and data reside.


### 7. Discontinue legacy network security technology

Zero Trust rejects implicit trust in any network segment or device. Legacy perimeter-centric controls—such as flat VPN tunnels, “hair-pin” traffic inspection, hard-coded access control lists (ACLs), and static network firewalls—no longer provide the adaptive, identity- and context-aware protection required for modern hybrid and cloud-native environments. To fully realize Zero Trust, organizations must retire these outdated technologies in favor of identity-driven, software-defined security services.

#### Scope of retirement

Legacy technologies to retire include:

- **Traditional VPNs** that grant broad network access based solely on device certificates or shared keys.
- **Rigid network firewalls** with static rule sets and limited application-level visibility.
- **Legacy web proxies** that lack inline threat inspection or session control.
- **Network ACLs or route-based segmentation** without integration into identity or device posture signals.

#### Replacement principles

For each deprecated control, adopt a modern Zero Trust alternative that:

- Enforces least-privilege access at the application or workload layer using Zero Trust Network Access (ZTNA).
- Integrates identity and device posture (using Microsoft Entra ID and Microsoft Defender for Endpoint) into every access decision.
- Provides continuous validation with Continuous Access Evaluation and session re-evaluation.
- Delivers software-defined visibility and control through Secure Access Service Edge (SASE) and Security Service Edge (SSE) solutions, such as Secure Web Gateway (SWG), Cloud Access Security Broker (CASB), Firewall-as-a-Service (FWaaS), and Network Detection and Response (NDR).

#### Transition strategy

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

#### Risk mitigation and metrics

- **Fallback controls:** Keep legacy paths in “read-only” monitoring mode during early migration waves to catch policy gaps.
- **Telemetry-driven tuning:** Use Microsoft Sentinel and Microsoft Defender logs to identify failed access attempts or policy misses.

**Success criteria:**

- At least 90% of remote access is via ZTNA or SASE by the target date.
- No critical security findings in legacy technology during the monitoring window.
- Measurable reduction in lateral-movement alerts.

#### Governance and audit

- Assign a ZTNA migration owner to oversee decommission timelines.
- Enforce a “no new legacy deployments” policy in procurement.
- Conduct a post-mortem audit to ensure all legacy interfaces and firewall rules have been fully removed.

For more information on Microsoft Global Secure Access, see [What is Global Secure Access?](/entra/global-secure-access/overview-what-is-global-secure-access).

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
