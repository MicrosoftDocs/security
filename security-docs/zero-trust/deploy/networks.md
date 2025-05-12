---
title: Secure networks with Zero Trust
description: Learn how to secure networks using a Zero Trust strategy with Secure Access Service Edge (SASE) and Secure Service Edge (SSE) solutions.
ms.date: 05/05/2025
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

In recent years, network security has undergone significant transformations. The focus has shifted from traditional perimeter-based approaches to risk-based policy decisions that manage internal and external traffic flows, isolate hosts, enforce encryption, segment activities, and enhance enterprise-wide network visibility. These changes enable security controls to be implemented closer to applications, data, and other resources, augment traditional network-based protections, and improve defense-in-depth strategies. The network can treat each application uniquely based on its requirements for access, priority, reachability, connections to dependency services, and overall connectivity.

The emergence of SASE represents a paradigm shift in how organizations approach network security. SASE converges networking and security functions into a single, unified service. SASE offers a more streamlined and effective way to protect data and applications, regardless of where they're located. This modern approach not only simplifies the management of security policies but also enhances the overall security posture of the organization. Artificial Intelligence (AI) is playing a pivotal role in this new era of network security. AI-driven solutions are capable of analyzing vast amounts of data in real-time, identifying potential threats, and responding to incidents with unprecedented speed and accuracy. By applying AI, organizations can proactively detect and mitigate security risks, ensuring a more robust and resilient network infrastructure.

In summary, the adoption of SASE, coupled with the integration of AI, marks a significant advancement in the field of network security. These innovations are enabling organizations to stay ahead of emerging threats and maintain a secure and efficient network environment.

## Key Principles of the Zero Trust Network Model

Instead of assuming that everything behind the corporate firewall is secure, an end-to-end Zero Trust strategy acknowledges that breaches are inevitable. This approach requires verifying each request as if it originates from an uncontrolled network, with identity management playing a crucial role. When organizations incorporate the Cybersecurity and Infrastructure Security Agency (CISA) and National Institute of Standards and Technology (NIST) Zero Trust models and patterns, they enhance their security posture and better protect their networks.

In the Zero Trust model, there are three key objectives when it comes to securing your networks:

- Be ready to handle attacks before they happen.
- Minimize the extent of the damage and how fast it spreads.
- Increase the difficulty of compromising your cloud footprint.

To make this happen, follow three Zero Trust principles:

- **Verify explicitly.** Always authenticate and authorize based on all available data points. Include user identity, location, device health, service or workload, user and device risk, data classification, and anomalies.
- **Use least-privileged access.** Limit user access with Just-In-Time and Just-Enough-Access (JIT/JEA), risk-based adaptive policies, and data protection to protect both data and productivity.
- **Assume breach.** Minimize influence radius for breaches and prevent lateral movement by segmenting access by network, user, devices, and application awareness. Verify all sessions are encrypted end to end. Use analytics to get [visibility](https://aka.ms/ZTCrossPillars), drive threat detection, and improve defenses.


## Zero Trust network deployment objectives

Before most organizations start their Zero Trust journey, they have network security that is characterized as:
- Minimal or no identity awareness for network traffic.
- Limited or no risk based policy decision capabilities.
- Limited or no governance or lifecycle for application access.

When implementing an end-to-end Zero Trust framework for securing networks, we recommend you focus first on [objectives 1 through 4](#1-network-segmentation--software-defined-perimeters). After these objectives are completed, focus on [objectives 5 through 7](#7-discontinue-legacy-network-security-technology).

## Zero Trust networking deployment guide

This guide walks you through the steps required to secure your networks following the principles of a Zero Trust security framework.

### 1. Network-Segmentation & Software-Defined Perimeters

- Implement fine-grained network segmentation (Macro & Micro segmentation) to restrict lateral movement.
- Utilize Software-Defined Networking (SDN) and Network Access Control (NAC) to dynamically enforce policies.
- Adopt identity-based segmentation over traditional IP-based methods.

### 2. Secure Access Service Edge (SASE) & Zero Trust Network Access (ZTNA)

- Modernize traditional VPNs with ZTNA to provide least-privilege, identity-aware network access.
- Leverage SASE architectures to integrate networking and security functions (e.g., SWG, CASB, FWaaS).
- Implement continuous session validation and risk-based access decisions.

### 3. Strong Encryption & Secure Communication

- Use TLS 1.3+ and end-to-end encryption for all network traffic.
- Enforce mutual authentication (mTLS) between workloads and devices.
- Block untrusted or legacy protocols that lack encryption.

### 4. Network Visibility & Threat Detection

- Deploy Network Detection & Response (NDR) to monitor and analyze network traffic.
- Use DPI (Deep Packet Inspection) and AI-driven anomaly detection for real-time threat hunting.
- Maintain a centralized logging and SIEM/SOAR integration for network telemetry analysis.
- Deploy Extended Detection and Response (XDR) to analyze traffic patterns, identify anomalies, and prevent breaches.
- Integrate AI-driven analytics to enhance rapid responses to emerging threats.

### 5. Policy-Driven Access Control & Least Privilege

- Implement context-aware access policies using User, Device, and Location-based factors.
- Enforce Just-in-Time (JIT) access and dynamic policy enforcement.
- Apply deny-by-default principles across all network layers.

### 6. Cloud & Hybrid Network Security

- Secure cloud workloads with micro-perimeters and cloud-native firewalls.
- Integrate identity-aware proxies to secure SaaS and PaaS environments.
- Ensure consistent security policy enforcement across hybrid and multi-cloud environments.

### 7. Discontinue legacy network security technology

Discontinue the use of signature-based Network Intrusion Detection/Network Intrusion Prevention (NIDS/NIPS) Systems and Network Data Leakage/Loss Prevention (DLP).

The major cloud service providers already filter for malformed packets and common network layer attacks, so there's no need for a NIDS/NIPS solution to detect the attacks. In addition, traditional NIDS/NIPS solutions typically use signature-based approaches (which are considered outdated) and attackers easily evade them. Signature-based approaches produce a high rate of false positives.

Network-based DLP is decreasingly effective at identifying both inadvertent and deliberate data loss. The reason for this is that most modern protocols and attackers use network-level encryption for inbound and outbound communications. The only viable workaround is `SSL-bridging` which provides an "authorized man-in-the-middle" that terminates and then reestablishes encrypted network connections. The `SSL-bridging` approach is out of favor because of the level of trust required for the partner running the solution and the technologies that are being used.

Based on this rationale, we offer an all-up recommendation that you discontinue use of these legacy network security technologies. However, if your organizational experience is that these technologies prevent and detect real attacks, consider porting them to your cloud environment.

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

Securing networks is central to a successful Zero Trust strategy. For further information or help with implementation, contact your Customer Success team or continue to read through the other chapters of this guide, which spans all Zero Trust pillars.
