---
title: Minimize internet-facing exposure - Microsoft Zero Trust
description: Inventory internet-facing assets, remove unnecessary exposure, and apply Zero Trust network protections across Azure and multicloud workloads.
ms.date: 04/21/2026
ms.service: security
ms.subservice: zero-trust
ms.topic: concept-article
ms.collection:
  - highpri
  - zerotrust
ai-usage: ai-assisted
---

# Minimize internet-facing exposure

Inventory what's exposed and remove what doesn't need to be there. You can use **[Microsoft Defender External Attack Surface Management (EASM)](/azure/external-attack-surface-management/overview)** to discover and map your internet-facing assets continuously. This service is pay-for-service and includes a 30-day free trial. Provision it from the Azure portal to inventory what's exposed and identify what should be removed or protected.

## Discover and analyze your attack surface

- Use Microsoft Defender External Attack Surface Management to inventory internet-exposed assets across your estate. For more information, see [Discover your assets](/azure/external-attack-surface-management/what-is-discovery).
- Use Microsoft Security Exposure Management's [attack path analysis](/security-exposure-management/cross-workload-attack-surfaces) to find internet-exposed assets with critical vulnerabilities.

## Apply Zero Trust network protection

- Enable **Azure DDoS Protection** to protect public IP addresses and use the HTTP DDoS Ruleset in **Azure Web Application Firewall (WAF)** to defend against L3–L7 availability attacks. Control and selectively allow north-south inbound traffic using **Azure Firewall** and Azure WAF, enforcing stateful inspection and application-aware filtering.
- Implement Zero Trust micro-segmentation for east-west traffic using **Azure Network Security Groups (NSGs)** and Azure Firewall rules to restrict lateral movement between workloads. Route north-south and required east-west traffic through Azure Firewall and, where needed, enable TLS inspection and intrusion detection and prevention system (IDPS) to inspect encrypted traffic and detect or block malicious activity.
- Remove public IPs from all virtual machines and eliminate inbound RDP/SSH entirely by using **Azure Bastion** for secure management access. Monitor and analyze Azure Firewall, WAF, and DDoS logs with **Microsoft Sentinel** to automatically detect, respond to, and block threats.
- Eliminate public endpoints for PaaS services with **Azure Private Link**. Replace public access to Azure Storage, SQL, Key Vault, and other services with Private Endpoints, ensuring traffic stays on the Microsoft backbone. For more information, see [What is Azure Private Link?](/azure/private-link/private-link-overview)
- Extend network protection to multicloud workloads. Use **Defender for Cloud's** network security recommendations for AWS and GCP to identify overly permissive security groups, public-facing storage, and exposed management ports across all cloud providers. For more information, see [Networking security recommendations](/azure/defender-for-cloud/recommendations-reference-networking).

## Accelerate with AI-powered agents

- The **Threat Intelligence Briefing Agent** generates tailored threat briefings by integrating signals from Microsoft Defender External Attack Surface Management (EASM), Defender for Endpoint, and Microsoft Threat Intelligence. EASM enriches each briefing with your organization's discovered external assets and exposures, enabling prioritized remediation recommendations based on your actual attack surface. For more information, see [Microsoft Security Copilot Threat Intelligence Briefing Agent](/copilot/security/threat-intel-briefing-agent).

## Related content

- [Stay current on Microsoft software](stay-current-microsoft-software.md)
- [Scan and secure your source code](scan-secure-source-code.md)
- [Adopt updates for open-source software (OSS) components](adopt-open-source-updates.md)
- [Implement baseline security measures](baseline-security-measures.md)
