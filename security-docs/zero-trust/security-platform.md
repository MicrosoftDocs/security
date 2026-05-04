---
title: Microsoft security platform technologies
description: Learn about the products and services in the Microsoft security platform
ms.date: 04/29/2026
ms.service: security
ms.subservice: zero-trust
ms.author: raynew
author: rayne-wiselman
ms.topic: conceptual

#customer intent: As a security adopter, I want to understand the Microsoft security platform technologies.
---

# Microsoft security services

This article describes the Microsoft security platform and explains how its services work together as a unified system to deliver protection across identities, devices, applications, data, and infrastructure.


Modern enterprise security has shifted from perimeter-based protection to an identity-driven, cloud-integrated model. Organizations must secure users, devices, applications, and data across hybrid and multicloud environments while continuously adapting to evolving threats.

The Microsoft security platform is an integrated set of cloud-based services that work together to share signals, apply consistent policies, enforce controls, and coordinate detection and response across the environment.


## Security outcomes

The Microsoft security platform is designed to deliver the following outcomes:

- **Unified signal visibility**: Telemetry is continuously collected and centralized across identities, devices, applications, data, and infrastructure.
- **Identity-driven decision making**: Access and enforcement decisions are based on identity, device state, risk signals, and session context.
- **Consistent enforcement**:Zero Trust controls are applied across endpoints, cloud services, and applications at access time and during use.
- **Integrated detection and response**: Signals and alerts are correlated across domains to detect and respond to threats as unified incidents.
- **Continuous validation and improvement**: Detection and risk signals feed back into policy decisions to strengthen protection over time.

## Core security services

Core security services span multiple technology pillars, each contributing signals, context, and enforcement across the platform.


**Pillar<br/>Primary service** | **Protection** | **Primary portal**
--- | --- | --- 
**Identity and access**<br/><br/>Microsoft Entra, Microsoft Defender for Identity. | Microsoft Entra controls access for users, workloads, and applications. It evaluates identity, device, and session signals to make access decisions.<br/><br/>Defender for Identity monitors hybrid identity infrastructure to detect attacks. | Microsoft Entra admin center<br/><br/>Microsoft Defender portal
**Devices and endpoints**<br/><br/>Microsoft Defender for Endpoint<br/><br/>Microsoft Intune | Defender for Endpoint collects endpoint telemetry and detects threats.<br/><br/>Microsoft Intune assesses device compliance and enforces policy. | Microsoft Defender portal <br/><br/>Microsoft Intune admin center
**Email and collaboration**<br/><br/>Defender for Office 365 | Protects Exchange and collaboration services (Microsoft Teams, SharePoint, OneDrive) from malware, malicious links/attachments, and business email compromise. | Microsoft Defender portal
**Data**<br/><br/>Microsoft Purview | Enforces data protection and data loss prevention (DLP) policies across endpoints and cloud services. | Microsoft Purview portal
**Infrastructure/cloud workloads**<br/><br/>Microsoft Defender for Cloud  | Improves security posture and provides threat detection across cloud and hybrid workloads. | Azure portal/Microsoft Defender portal
**Networks**<br/><br/>Azure networking services | Segment and protect networks. | Microsoft Azure portal
**SaaS/cloud apps**<br/><br/>Microsoft Defender for Cloud Apps | Provides visibility into cloud app usage and monitors user activity to detect risky behavior. | Microsoft Defender portal
**Posture/risk**<br/><br/>Microsoft Security Exposure Management | *Identifies, prioritizes, and reduces exposure across identities, devices, cloud resources, and applications. | Microsoft Defender portal
**Threat detection/response** <br/><br/>Microsoft Defender XDR | Correlates signals across Defender services and produces unified incidents for investigation and response. | Microsoft Defender portal
**Security operations**<br/><br/>Microsoft Sentinel | Aggregates telemetry from Microsoft and third-party sources for centralized analysis, investigation, and response. | Microsoft Azure portal/Microsoft Defender portal.
**Developer/app security**<br/><br/>Defender for DevOps (in Defender for Cloud), GitHub Advanced Security | Secures code, dependencies, and build pipelines, and enforces security governance across DevOps workflows. | Microsoft Defender portal<br/><br/>GitHub interface

## Network protection services

The table summarizes Azure networking capabilities and how they they directly integrate with other security services.

**Service** | **Protection** | **Integration**
--- | --- | ---
**Azure Firewall** | Enforces IP, port, and application rules to control inbound and outbound traffic across subnets, internet, and on-premises networks. Uses Microsoft threat intelligence to block known malicious traffic. | Defender for Cloud evaluates configuration posture.<br/><br/>Diagnostic logs are ingested into Azure Monitor/Log Analytics and can be analyzed by Microsoft Sentinel for detection and correlation.
**Azure DDoS Protection** | Mitigates volumetric, protocol, and application-layer attacks. Protects internet-facing resources in virtual networks (VNets) from large-scale flooding attacks. |  Metrics and attack telemetry are ingested into Azure Monitor/Log Analytics and can be analyzed in Microsoft Sentinel.<br/><br/>Defender for Cloud provides posture recommendations.
**Azure VNet** | Provides network isolation, segmentation, and private IP addressing for Azure resources. Enables controlled connectivity between services. |  Defender for Cloud evaluates configuration state, including exposure such as public access paths.
**Network Security Groups (NSGs)** | Filters traffic at the subnet and network interface level using allow/deny rules. Restricts unwanted traffic to resources. | NSG flow logs (via Azure Monitor) can be analyzed in Microsoft Sentinel for traffic visibility and detection.<br/><br/>Defender for Cloud evaluates NSG rule configuration. 
**Azure Web Application Firewall (WAF)** | Protects HTTP/HTTPS applications using OWASP rule sets. Helps prevent common web attacks such as SQL injection and cross-site scripting (XSS).| WAF logs are ingested into Azure Monitor/Log Analytics and can be analyzed by Microsoft Sentinel.<br/><br/>Defender for Cloud evaluates WAF configuration posture.
**Azure Front Door** | Provides a global entry point for web applications with routing, acceleration, and edge security capabilities. Integrates with WAF for application protection. | Diagnostic logs (Front Door/WAF) are ingested into Log Analytics and can be analyzed by Microsoft Sentinel.<br/><br/>Defender for Cloud evaluates configuration posture.
**Azure Application Gateway** | Provides regional load balancing with built-in web application firewall capabilities to protect and route application traffic. | Access and WAF logs are ingested into Log Analytics and can be analyzed by Microsoft Sentinel.<br/><br/>Defender for Cloud evaluates configuration posture and exposure settings.
**Azure VPN Gateway** | Provides encrypted IPsec/IKE connectivity between on-premises environments and Azure VNets. Protects data in transit over public networks. |  onnection and tunnel logs are ingested into Log Analytics and cCan be analyzed in Microsoft Sentinel.<br/><br/>Defender for Cloud evaluates configuration posture, including encryption settings.
**Azure ExpressRoute** |  Provides private, dedicated connectivity between on-premises environments and Azure over the Microsoft backbone, avoiding the public internet. |  Operational telemetry (such as BGP, circuit status) is available througa Azure Monitor and can be analyzed in Microsoft Sentinel.<br/><br/>Defender for Cloud evaluates high-level configuration posture.
**Azure Bastion** | Provides secure RDP and SSH access to virtual machines through a browser, eliminating the need for public IP exposure. | Diagnostic logs are ingested into Log Analytics and can be analyzed by Microsoft Sentinel.<br/><br/>Defender for Cloud evaluates reduced VM, but not Azure Bastion configuration directly.
**Azure Private Link** | Provides private connectivity to Azure PaaS services and customer services using private IP addresses, eliminating public exposure. | Service-level logs (for services accessed via Private Link such as Storage, SQL, Key Vault) are ingested into Log Analytics and can be analyzed by Microsoft Sentinel.<br/><br/>Defender for Cloud evaluates whether private links are used to reduce exposure. 
**Azure Network Watcher** | Provides network diagnostics, monitoring, and flow-level visibility across Azure resources. | NSG flow logs and diagnostics are ingested into Log Analytics and can be analyzed in Microsoft Sentinel.<br/><br/>Defender for Cloud evaluates underlying resource configuration state such as NSG settings, rather than Network Watcher directly.

## Integration activity/flow

Security services operate as a continuous pipeline, where signals are collected, evaluated, enforced, and used to drive detection and respons

**Pipeline** | **Action** | **Key technologies**
--- | --- | ---
**Stage 1: Signal collection** | Security services generate telemetry across identities, devices, applications, and infrastructure. | - Defender for Endpoint (device telemetry).<br/>- Microsoft Intune (device compliance evaluation).<br/>- Defender for Identity (on-premises identity activity).<br/>- Defender for Cloud Apps (SaaS activity)<br/>- Defender for Cloud (infrastructure/workload activity). 
**Stage 2: Policy decisions** | Signals are evaluated to determine access conditions and control actions. | Microsoft Entra Conditional Access evaluates identity risk, device trust, location, and session context.
**Stage 3: Control enforcement** | Security controls are applied across identity, device, session, data, and network layers. |  Enforcement points include:<br/>- Conditional Access (MFA/restrictions)<br/>- Intune (device compliance)<br/>-Defender for Cloud Apps (session control)<br/>- Microsoft Purview (DLP), Azure networking (connectivity restrictions).
**Stage 4: Detection and response** | Signals and alerts are correlated to detect, investigate, and remediate threats. | Microsoft Defender XDR correlates signals from all Defender products into unified incidents.<br/><br/>Microsoft Sentinel centralizes logs, incidents, hunting, and SOAR across the entire environment—including third-party sources. 
**Feedback loop** | Detection outcomes feed back into policy decisions to continuously improve protection. | Risk and threat signals inform real-time policy updates, enabling adaptive and automated protection.

## Service integration

Microsoft security services integrate through multiple flows rather than a single pipeline, forming a continuous system of protection.

Together, these flows operate as a cohesive system:

- **Signals (telemetry)** capture activity across identities, devices, applications, and other resources.
- **Context** (identity, device posture, and data classification) enriches signals to improve accuracy and decision-making.
- **Policy** defines what access is allowed or blocked based on evaluated conditions.
- **Actions** enforce decisions through automated controls and response.

As signals move through the platform, they are enriched, evaluated against policy, and acted on, creating a continuous cycle of protection and response.

### Service activity interaction

**Service** | **Consumes** | **Outputs**
--- | --- | ---
**Microsoft Entra ID** | **Signals**: Authentication activity (sign-ins, risk events). Device compliance status from Microsoft Intune.<br/><br/>**Context**: Device context for access decisions from Defender for Endpoint. Session context for access decisions from Defender for Cloud Apps. | **Actions**:  Conditional Access decisions (allow, block, restrict, require controls).
**Microsoft Intune** | **Signals**: Managed devices inventory, health, compliance state. <br/><br/>**Context**: Identity association from Microsoft Entra ID. | **Output**:<br/>- Device compliance posture to Microsoft Entra ID. Device audit logs to Microsoft Sentinel.
**Microsoft Purview** | **Signals**: Enterprise data across Microsoft 365, SaaS apps, and on-premises systems.<br/><br/> **Context**: Data classification (sensitivity labels, content inspection, user activity). | **Output**<br/>- Insider risk and data loss protection (DLP) alerts to Defender XDR. Compliance and audit logs to Microsoft Sentinel.<br/><br/>**Actions**: DLP enforcement across endpoints (Defender for Endpoint), and sesssions (Defender for Cloud Apps).
**Defender for Endpoint** | **Signals**: Endpoint telemetry (process, file, network activity).<br/><br/>**Context**: Microsoft Entra ID (identity context). Microsoft Intune (device posture). Microsoft Purview (DLP policies). | **Outputs**: Endpoint alerts and telemetry to Defender XDR and Microsoft Sentinel.<br/><br/>**Actions**: Endpoint enforcement (device isolation, blocking, remediation).
**Defender for Identity** | **Signals**: Active Directory identity signals. | **Output**:<br/>- Identity threat alerts to Defender XDR and Microsoft Sentinel.
**Defender for Cloud Apps** | **Signals**: SaaS app activity (cloud usage). Network and shadow IT telemetry from Defender for Endpoint.<br/><br/>**Context**:  Session and authentication context from Microsoft Entra ID. DLP policies from Microsoft Purview. | **Outputs**:<br/> - Cloud app alerts to Defender XDR and Microsoft Sentinel.<br/><br/>**Actions**: Session enforcement (block, monitor, restrict access).
**Defender for Cloud** | **Signals**: Resource operation information from Azure. Server/workload telemetry from Defender for Endpoint.<br/><br/>**Context**: Resource configuration and posture. | **Outputs**:<br/>- Security alerts and posture insights to Defender XDR and Microsoft Sentinel.
**Microsoft Security Exposure Management** | **Signals**: Device risk scores from Defender for Endpoint. Cloud resource inventory, posture, exposure and attack surface findings from Defender for Cloud.  Identity inventory and risk signals from Microsoft Entra.  SaaS app inventory, risk, and usage context from Defender for Cloud Apps.<br/><br/>**Context**: Unified exposure and risk correlation. | **Outputs**: Exposure insights and risk correlations to Microsoft XDR and Microsoft Sentinel. 
**Defender XDR** | **Signals**: Alerts from Defender for Endpoint (devices), Defender for Identity (identity signals), Defender for Office 365 (email and collaboration), Defender for Cloud Apps (SaaS/app activity). Additional signals from Microsoft Purview (DLP, insider risk, data classification), Microsoft Entra ID Protection (identity risk signals) and Defender for Cloud (workload/cloud posture). | **Outputs**:<br/>Correlated alerts, incidents to Microsoft Sentinel.<br/><br/>**Actions**: Automated cross-domain response.
**Microsoft Sentinel** | **Signals**: Alerts, logs, telemetry from Defender XDR, Microsoft Purview, cloud services, and other first-party/third-party sources. | **Outputs**: Analytics, investigations, and incidents.<br/><br/>**Actions**: Automated response using playbooks.
**Microsoft Security Copilot** | **Signals**: Incidents and alerts from Microsoft Sentinel and Defender XDR.<br/><br/>**Context**: Sensitive data and insider risk context from Microsoft Purview. Exposure context from Microsoft Security Exposure Management. | **Outputs**: Investigation summaries, recommendations, AI-driven insights.<br/><br/>**Actions**: Guided response actions routed through Microsoft Sentinel and Defender XDR workflows.



## What's next?

- To begin by assessing your current Zero Trust posture, start [Zero Trust assessment](assessment/overview.md).
- To get started with structured adoption, follow our [Zero Trust adoption path](security-adoption-model.md).
- To dive into critical security outcomes that business leaders might want to focus on, start with our [business scenarios](security-adoption-business-scenarios-overview.md).
To start directly with security implementation for business solutions and technical pillars such as devices and data, review [implementing technical solutions](implement-overview.md).