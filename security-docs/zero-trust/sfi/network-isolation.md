---
title: Network isolation
description: Network isolation is part of the protect networks pillar of the Secure Future Initiative (SFI)and aligns with the Zero Trust principles of Verify Explicitly, Least Privilege, and Assume Breach to ensure that corporate and cloud networks are secured against unauthorized internal access and external intrusions. 
ms.date: 10/03/2025
ms.service: security
author: leonyen
ms.author: v-leonyen
ms.subservice: zero-trust
ms.topic: conceptual
ms.collection:
  - highpri
  - zerotrust
  - sfi-zerotrust
---

# Network isolation (Secure Future Initiative)

**Pillar name: Protect networks**<br>
**Pattern name: Network isolation**

## Context and problem

Modern threat actors exploit weak network boundaries to move laterally
and escalate privileges. Common attack paths include stolen credentials,
protocol abuse, and token replay. Once inside, adversaries often exploit
poor segmentation, overly permissive permissions, or shared
infrastructure to access sensitive workloads.  

Traditional flat networks make it difficult to enforce *Least Privilege*
access and often leave resources broadly reachable. Without clear
isolation, both internal and external threats can quickly compromise
multiple systems. The challenge is to standardize network segmentation,
enforce perimeters, and ensure traffic flows are strictly controlled to
prevent lateral movement and contain breaches.

## Solution

Network isolation secures networks by dividing and isolating
networks into segments and controlling network access to them. It
combines identity-aware network security solutions and improvements in
visibility, monitoring and detection capabilities. Core practices
include:  

-   Network segmentation and software-defined perimeters: Assume Breach
    and limit lateral movement with network partitioning and dynamic,
    risk-based access. Enforce Least Privilege with scoped access and
    Verify Explicitly with identity-based access controls.

-   SASE and ZTNA: Use Secure Access Service Edge (SASE) and Zero Trust
    Network Access (ZTNA) architectures to integrate security and
    networking. Align Zero Trust principles by granting and restricting
    access based on context, identity, and conditional access controls.

-   Encryption and communication: Assume Breach by protecting data in
    transit and limiting data tampering risk with strong, modern
    encryption and communication, and blocking of weak protocols.

-   Visibility and threat detection: *Assume Breach* with continuous
    visibility and monitoring, and logging of network activity. Enforce
    *Least Privilege* and *Verify Explicitly* with access controls and
    threat detection to find and surface anomalies. Enforce Zero Trust
    by automating deployment, management, and allocation of networking
    resources and controls at scale. Without automation, delays,
    inconsistencies and gaps can quickly arise.

-   Policy-driven controls: *Verify Explicitly* and apply *Least
    Privilege* with granular, adaptive identity-centered, conditional
    access policy controls. Assume Breach with deny-by-default, and
    constantly reevaluating risk.

-   Cloud and hybrid network security: *Assume Breach* and *Verify
    Explicitly* in multicloud and hybrid environments by isolating cloud
    workloads into protected micro-perimeters, and by using
    Identity-aware proxies and Cloud Security Access Broker (CASB)
    solutions for SaaS and PaaS apps. Apply Zero Trust principles with
    unified security policies across cloud and on-premises, secure
    hybrid connection mechanisms, improvement of cloud/hybrid security
    posture, and centralized security monitoring.

## Guidance

Organizations can adopt a similar pattern using the following actionable
practices: 

|Use case|Recommended action |Resource |
|---|---|---|
| Micro-segmentation   | <ul><li>Use network security groups (NSGs) and ACLs to enforce least overview privilege access between workloads.</li></ul>|[Azure network security groups overview](/azure/virtual-network/network-security-groups-overview) |
| Isolate virtual networks |<ul><li>Use tools like Microsoft Defender Vulnerability Management to scan systems and prioritize CVEs</li></ul> | [Isolating VNets - Azure Virtual networks](/azure/virtual-wan/scenario-isolate-vnets) |
| Perimeter protection for PaaS resources |<ul><li>Use Azure Network Security secure access to services like Storage, SQL, and Key Vault.</li></ul>| [What is a network security perimeter](/azure/private-link/network-security-perimeter-concepts) |
| Secure connectivity to virtual machines |<ul><li>Use Azure Bastion to establish secure RDP/SSH connectivity to virtual machines without exposing resources to the internet.</li></ul>| [About Azure Bastion](/azure/bastion/bastion-overview) |
| Restrict outbound virtual access |<ul><li>Remove default outbound internet access and apply least privilege Network for service egress.</li></ul>| [Default Outbound Access in Azure - Azure Virtual Network](/azure/virtual-network/ip-services/default-outbound-access) |
| Layered perimeter defense   |<ul><li>Apply firewalls, service tags, NSGs, and DDoS protection to enforce multi-layer security.</li></ul>| [Azure DDoS Protection Overview](/azure/ddos-protection/ddos-protection-overview) |
| Centralized policy management   |<ul><li>Use Azure Virtual Network Manager with security admin rules to centrally manage network isolation policies.</li></ul>| [Security admin rules in Azure Virtual Network Manager](/azure/virtual-network-manager/concept-security-admins) |

## Outcomes

### Benefits
* Resiliency: Limits the blast radius of an intrusion.  
* Scalability: Standardized network isolation supports enterprise-scale environments.  
* Visibility: Service tagging and monitoring provide clearer attribution of traffic flows.  
* Regulatory alignment: Supports compliance with frameworks requiring strict segregation of sensitive resources.  

### Trade-offs

* Operational overhead: Designing and maintaining segmented networks requires planning and ongoing updates.
* Complexity: More segmentation may introduce additional management layers and require automation to scale.  
* Performance considerations: Some isolation measures may slightly increase latency.  

## Key success factors

To track success, measure the following:  

* Number of workloads deployed in isolated virtual networks with no direct internet exposure.  
* Percentage of services governed by centralized security admin rules.  
* Reduction in lateral movement paths identified during red-team testing.  
* Compliance with least privileged policies across environments.  
* Time to detect and remediate anomalous network activity.  

## Summary

Network isolation is a foundational strategy for preventing lateral movement and protecting sensitive workloads. By segmenting resources, enforcing perimeters, and applying layered defenses, organizations reduce their attack surface and build resilience against modern adversaries.

Isolating networks is no longer optional---it is a necessary control for safeguarding cloud and hybrid environments. The Network isolation objective provides a clear framework for reducing lateral movement, aligning with Zero Trust, and protecting enterprise-scale environments.  

Additionally, all network, identity, and device activity should be continuously monitored. Centralize logging and correlate security alerts using extended detection and response (XDR) solutions and SIEM tools to effectively detect anomalies and threats. Pair detection with behavioral analytics, deep packet inspection, and automated threat response to quickly contain suspicious activity, and support efficient incident response.

**Evaluate your current network topology and implement segmentation and perimeter controls to align with the network isolation objective.**
