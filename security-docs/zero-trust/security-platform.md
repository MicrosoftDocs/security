---
title: Microsoft security platform technologies
description: Learn about the products and services in the Microsoft security platform
ms.date: 05/24/2026
ms.service: security
ms.subservice: zero-trust
ms.author: raynew
author: rayne-wiselman
ms.topic: concept-article

#customer intent: As a security adopter, I want to understand the Microsoft security platform technologies.
---

# Microsoft security services

This article describes Microsoft security services and how they work together as a unified system to deliver protection across [technology pillars](deploy/overview.md) that include identities, devices, applications, data, AI, and infrastructure.

Modern enterprise security shifted from perimeter-based protection to an identity-driven, cloud-integrated model. Organizations must secure users, devices, applications, and data across hybrid and multicloud environments while continuously adapting to evolving threats.

Microsoft provides an integrated set of cloud-based services that work together to share signals, apply consistent policies, enforce controls, and coordinate detection and response across the environment.


## Security outcomes

Integrated Microsoft security delivers the following outcomes:

- **Unified signal visibility**: Telemetry is continuously collected and centralized across identities, devices, applications, data, and infrastructure, and converted into centralized, actionable signals.
- **Identity-driven decision making**: Access and enforcement decisions are based on identity, device state, risk signals, and session context.
- **Consistent enforcement**: Zero Trust controls are applied across endpoints, cloud services, and applications at access time and during use.
- **Integrated detection and response**: Signals and alerts are correlated across domains to detect and respond to threats as unified operations.
- **Continuous validation and improvement**: Detection and risk signals feed back into policy decisions to strengthen protection over time.

## Core security services

Core security services span multiple technology pillars, each contributing signals, context, and enforcement across the platform.


**Pillar<br/>Primary service** | **Protection** | **Primary portal**
--- | --- | --- 
**Identity and access**<br/><br/>Microsoft Entra<br/><br/>Microsoft Defender for Identity. | Microsoft Entra controls access for users, workloads, and applications. It evaluates identity, device, and session signals to make access decisions.<br/><br/>Defender for Identity monitors hybrid identity infrastructure to detect attacks. | [Microsoft Entra admin center](https://entra.microsoft.com/)<br/><br/>[Microsoft Defender portal](https://sip.security.microsoft.com/)
**Devices/endpoints**<br/><br/>Microsoft Defender for Endpoint<br/><br/>Microsoft Intune | Defender for Endpoint collects endpoint telemetry and detects threats.<br/>Microsoft Intune assesses device compliance and enforces policy. | [Microsoft Defender portal](https://sip.security.microsoft.com/) <br/><br/>[Microsoft Intune admin center](https://intune.microsoft.com/)
**Email and collaboration**<br/><br/>Defender for Office 365 | Protects Exchange and collaboration services (Microsoft Teams, SharePoint, OneDrive) from malware, malicious links/attachments, and business email compromise. | [Microsoft Defender portal](https://sip.security.microsoft.com/)
**Data**<br/><br/>Microsoft Purview | Enforces data protection and data loss prevention (DLP) policies across endpoints and cloud services. | [Microsoft Purview portal](https://sip.purview.microsoft.com/)
**Infrastructure/cloud workloads**<br/><br/>Microsoft Defender for Cloud  | Improves security posture and provides threat detection across cloud and hybrid workloads. | [Microsoft Azure portal](https://ms.portal.azure.com/)<br/>[Microsoft Defender portal](https://sip.security.microsoft.com/)
**Networks**<br/><br/>Azure networking services | Segment and protect networks. | [Microsoft Azure portal](https://ms.portal.azure.com/)
**SaaS/cloud apps**<br/><br/>Microsoft Defender for Cloud Apps | Provides visibility into cloud app usage and monitors user activity to detect risky behavior. | [Microsoft Defender portal](https://sip.security.microsoft.com/)
**Posture/risk**<br/><br/>Microsoft Security Exposure Management | Identifies, prioritizes, and reduces exposure across identities, devices, cloud resources, and applications. | [Microsoft Defender portal](https://sip.security.microsoft.com/)
**Threat detection/response** <br/><br/>Microsoft Defender XDR | Correlates signals across Defender services and produces unified incidents for investigation and response. | Microsoft Defender portal
**Security operations**<br/><br/>Microsoft Sentinel | Aggregates telemetry from Microsoft and third-party sources for centralized analysis, investigation, and response. | [Microsoft Azure portal](https://ms.portal.azure.com/)<br/>[Microsoft Defender portal](https://sip.security.microsoft.com/)
**Developer/app security**<br/><br/>Defender for DevOps (in Defender for Cloud)<br/>GitHub Advanced Security | Secures code, dependencies, and build pipelines, and enforces security governance across DevOps workflows. | [Microsoft Defender portal](https://sip.security.microsoft.com/)<br/>GitHub interface

## Network protection services

The table summarizes Azure networking capabilities and how they directly integrate with other security services. Services are configured in the [Microsoft Azure portal](https://ms.portal.azure.com/).

**Service** | **Protection** | **Integration**
--- | --- | ---
**Azure Firewall** | Enforces IP, port, and application rules to control inbound and outbound traffic across subnets, internet, and on-premises networks. Uses Microsoft threat intelligence to block known malicious traffic. | Defender for Cloud evaluates configuration posture.<br/><br/>Diagnostic logs are ingested into Azure Monitor/Log Analytics and analyzed by Microsoft Sentinel for detection and correlation.
**Azure DDoS Protection** | Mitigates volumetric, protocol, and application-layer attacks. Protects internet-facing resources in virtual networks (VNets) from large-scale flooding attacks. |  Metrics and attack telemetry are ingested into Azure Monitor/Log Analytics and can be analyzed in Microsoft Sentinel.<br/><br/>Defender for Cloud provides posture recommendations.
**Azure VNet** | Provides network isolation, segmentation, and private IP addressing for Azure resources. Enables controlled connectivity between services. |  Defender for Cloud evaluates configuration state, including exposure such as public access paths.
**Network Security Groups (NSGs)** | Filters traffic at the subnet and network interface level using allow/deny rules. Restricts unwanted traffic to resources. | NSG flow logs (via Azure Monitor) can be analyzed in Microsoft Sentinel for traffic visibility and detection.<br/><br/>Defender for Cloud evaluates NSG rule configuration. 
**Azure Web Application Firewall (WAF)** | Protects HTTP/HTTPS applications using OWASP rule sets. Helps prevent common web attacks such as SQL injection and cross-site scripting (XSS).| WAF logs are ingested into Azure Monitor/Log Analytics and analyzed by Microsoft Sentinel.<br/><br/>Defender for Cloud evaluates WAF configuration posture.
**Azure Front Door** | Provides a global entry point for web applications with routing, acceleration, and edge security capabilities. Integrates with WAF for application protection. | Diagnostic logs (Front Door/WAF) are ingested into Log Analytics and analyzed by Microsoft Sentinel.<br/><br/>Defender for Cloud evaluates configuration posture.
**Azure Application Gateway** | Provides regional load balancing with built-in web application firewall capabilities to protect and route application traffic. | Access and WAF logs are ingested into Log Analytics and analyzed by Microsoft Sentinel.<br/><br/>Defender for Cloud evaluates configuration posture and exposure settings.
**Azure VPN Gateway** | Provides encrypted IPsec/IKE connectivity between on-premises environments and Azure VNets. Protects data in transit over public networks. |  Connection and tunnel logs are ingested into Log Analytics and can be analyzed in Microsoft Sentinel.<br/><br/>Defender for Cloud evaluates configuration posture, including encryption settings.
**Azure ExpressRoute** |  Provides private, dedicated connectivity between on-premises environments and Azure over the Microsoft backbone, avoiding the public internet. |  Operational telemetry (such as BGP, circuit status) is available through Azure Monitor and can be analyzed in Microsoft Sentinel.<br/><br/>Defender for Cloud evaluates high-level configuration posture.
**Azure Bastion** | Provides secure RDP and SSH access to virtual machines through a browser, eliminating the need for public IP exposure. | Diagnostic logs are ingested into Log Analytics and analyzed by Microsoft Sentinel.<br/><br/>Defender for Cloud evaluates reduced VM, but not Azure Bastion configuration directly.
**Azure Private Link** | Provides private connectivity to Azure PaaS services and customer services using private IP addresses, eliminating public exposure. | Service-level logs (for services accessed via Private Link such as Storage, SQL, Key Vault) are ingested into Log Analytics and analyzed by Microsoft Sentinel.<br/><br/>Defender for Cloud evaluates whether private links are used to reduce exposure. 
**Azure Network Watcher** | Provides network diagnostics, monitoring, and flow-level visibility across Azure resources. | NSG flow logs and diagnostics are ingested into Log Analytics and can be analyzed in Microsoft Sentinel.<br/><br/>Defender for Cloud evaluates underlying resource configuration state such as NSG settings, rather than Network Watcher directly.

## Security workflow

Security services operate as a continuous pipeline. Signals are continuously collected, evaluated, enforced, and used to drive detection and response.

**Pipeline** | **Action** | **Key activity**
--- | --- | ---
**Stage 1: Signal collection** | Security services generate telemetry across identities, devices, applications, and infrastructure. | - Defender for Endpoint collects device telemetry.<br/>- Microsoft Intune evaluates device compliance.<br/>- Defender for Identity monitors on-premises identity activity.<br/>- Defender for Cloud Apps monitors SaaS activity.<br/>- Defender for Cloud monitors infrastructure/workload configuration and activity. 
**Stage 2: Policy decisions** | Signals are evaluated to determine access conditions and control actions. | Microsoft Entra Conditional Access evaluates identity risk, device trust, location, and session context.
**Stage 3: Control enforcement** | Security controls are applied across identity, device, session, data, and network layers. |  Enforcement points include:<br/>- Conditional Access (MFA/restrictions)<br/>- Intune (device compliance)<br/>-Defender for Cloud Apps (session control)<br/>- Microsoft Purview (DLP)<br/>- Azure networking (connectivity restrictions).
**Stage 4: Detection and response** | Signals and alerts are correlated to detect, investigate, and remediate threats. | Microsoft Defender XDR correlates signals from all Defender products into unified incidents.<br/><br/>Microsoft Sentinel centralizes logs, incidents, hunting, and security orchestration, automation, and response (SOAR) across the entire environment—including third-party sources. 
**Feedback loop** | Detection outcomes feed back into policy decisions to continuously improve protection. | Risk and threat signals inform real-time policy updates, enabling adaptive and automated protection.

## Security service integration

Microsoft security services integrate through multiple flows operating as a cohesive pipeline, forming a continuous system of protection.

- **Signals (telemetry)** capture activity across identities, devices, applications, and other resources.
- **Context (identity, device posture, and data classification)** enriches signals to improve accuracy and decision-making.
- **Policy** defines what access is allowed or blocked based on evaluated conditions.
- **Actions** enforce decisions through automated controls and response.

As signals move through the platform, they're enriched, evaluated against policy, and acted on, creating a continuous cycle of protection and response.

### How services integrate

The table summarizes how security services consume signals and context from each out, and what they output and action. 

**Service** | **Consumes** | **Outputs**
--- | --- | ---
**Microsoft Entra ID** | **Signals**: Authentication activity (sign-ins, risk events). Device compliance status from Microsoft Intune.<br/><br/>**Context**: Device context for access decisions from Defender for Endpoint. Session context for access decisions from Defender for Cloud Apps. | **Actions**:  Conditional Access decisions (allow, block, restrict, require controls).
**Microsoft Intune** | **Signals**: Managed devices inventory, health, compliance state. <br/><br/>**Context**: Identity association from Microsoft Entra ID. | **Outputs**: Device compliance posture to Microsoft Entra ID. Device audit logs to Microsoft Sentinel.
**Microsoft Purview** | **Signals**: Enterprise data across Microsoft 365, SaaS apps, and on-premises systems.<br/><br/> **Context**: Data classification (sensitivity labels, content inspection, user activity). | **Outputs**: Insider risk and data loss protection (DLP) alerts to Defender XDR. Compliance and audit logs to Microsoft Sentinel.<br/><br/>**Actions**: DLP enforcement across endpoints (Defender for Endpoint), and sessions (Defender for Cloud Apps).
**Defender for Endpoint** | **Signals**: Endpoint telemetry (process, file, network activity).<br/><br/>**Context**: Microsoft Entra ID (identity context). Microsoft Intune (device posture). Microsoft Purview (DLP policies). | **Outputs**: Endpoint alerts and telemetry to Defender XDR and Microsoft Sentinel.<br/><br/>**Actions**: Endpoint enforcement (device isolation, blocking, remediation).
**Defender for Identity** | **Signals**: Active Directory identity signals. | **Output**: Identity threat alerts to Defender XDR and Microsoft Sentinel.
**Defender for Cloud Apps** | **Signals**: SaaS app activity (cloud usage). Network and shadow IT telemetry from Defender for Endpoint.<br/><br/>**Context**:  Session and authentication context from Microsoft Entra ID. DLP policies from Microsoft Purview. | **Outputs**: Cloud app alerts to Defender XDR and Microsoft Sentinel.<br/><br/>**Actions**: Session enforcement (block, monitor, restrict access).
**Defender for Cloud** | **Signals**: Resource operation information from Azure. Server/workload telemetry from Defender for Endpoint.<br/><br/>**Context**: Resource configuration and posture. | **Outputs**: Security alerts and posture insights to Defender XDR and Microsoft Sentinel.
**Microsoft Security Exposure Management** | **Signals**: Device risk scores from Defender for Endpoint. Cloud resource inventory, posture, exposure, and attack surface findings from Defender for Cloud.  Identity inventory and risk signals from Microsoft Entra.  SaaS app inventory, risk, and usage context from Defender for Cloud Apps.<br/><br/>**Context**: Unified exposure and risk correlation. | **Outputs**: Exposure insights and risk correlations to Microsoft XDR and Microsoft Sentinel. 
**Defender XDR** | **Signals**: Alerts from Defender for Endpoint (devices), Defender for Identity (identity signals), Defender for Office 365 (email and collaboration), Defender for Cloud Apps (SaaS/app activity). Extra signals from Microsoft Purview (DLP, insider risk, data classification), Microsoft Entra ID Protection (identity risk signals), and Defender for Cloud (workload/cloud posture). | **Outputs**: Correlated alerts, incidents to Microsoft Sentinel.<br/><br/>**Actions**: Automated cross-domain response.
**Microsoft Sentinel** | **Signals**: Alerts, logs, telemetry from Defender XDR, Microsoft Purview, cloud services, and other first-party/third-party sources. | **Outputs**: Analytics, investigations, and incidents.<br/><br/>**Actions**: Automated response using playbooks.
**Microsoft Security Copilot** | **Signals**: Incidents and alerts from Microsoft Sentinel and Defender XDR.<br/><br/>**Context**: Sensitive data and insider risk context from Microsoft Purview. Exposure context from Microsoft Security Exposure Management. | **Outputs**: Investigation summaries, recommendations, AI-driven insights.<br/><br/>**Actions**: Guided response actions routed through Microsoft Sentinel and Defender XDR workflows.



## Next steps

- To kick off with a [Zero Trust assessment](assessment/overview.md) of your current security posture.
- Follow our structured [adoption model](security-adoption-model.md) to get started with Zero Trust adoption.
- Dive into critical security outcomes for business leaders with our adoption [business scenarios](security-adoption-business-scenarios-overview.md).
Start by[implementing technical solutions](implement-overview.md) for business solutions and technology pillars such as data and devices.