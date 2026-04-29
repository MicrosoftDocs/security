---
title: Secure AI agents at scale using Microsoft Agent 365
description: How to use Microsoft Agent 365 to secure all of the AI agents in your environment. 
ms.date: 04/29/2026
ms.update-cycle: 180-days
ms.topic: concept-article
ms.collection: 
  - msftsolution-security-for-ai
  - msftsolution-scenario
  - zerotrust-solution
  - msec-ai-copilot

# Customer intent: As a SOC manager, I want to manage the security of all of the AI agents in my organization so that I can ensure the safety of our data and systems.

---

# Secure AI agents at scale using Microsoft Agent 365

As organizations adopt AI agents to automate workflows and boost productivity, securing these agents has become a critical concern. Unlike traditional applications, AI agents can act, connect to tools, access data, interact with other agents, and operate autonomously. This creates new security challenges, including:

- Agent sprawl from user-created and SaaS agents that expands the attack surface.
- Over-privileged agents with excessive access to resources.
- Tool misuse and exploitation when agents are manipulated into abusing authorized tools.
- Misconfigured or vulnerable agents that lack proper authentication or boundaries.
- Traditional AI threats like prompt injection and data leakage that now span all agent interactions.

Microsoft Agent 365 is the control plane for managing AI agents. It extends your existing security infrastructure — Microsoft Defender, Microsoft Entra, and Microsoft Purview — to agents, with purpose-built capabilities tailored for agent needs. Agent 365 supports agents built on Microsoft platforms like Microsoft Copilot Studio and Microsoft Foundry, as well as agents created on third-party platforms.

This article outlines the core security capabilities that Microsoft Agent 365 provides based on Microsoft's extended security infrastructure for AI agents.

For more information about Microsoft Agent 365, see [Microsoft Agent 365 documentation](/microsoft-agent-365/overview/).

## A distributed control plane for managing agent security

Agent 365 integrates with the Microsoft 365 admin center to give IT teams centralized visibility into AI agents across the organization. Admins can review agent usage and take action based on performance and behavior signals.

Security teams define governance requirements by creating policy templates, such as access packages in Microsoft Entra. During onboarding, IT teams apply these templates to agents, ensuring governance and compliance are enforced from the start.

:::image type="content" source="media/agent-365-admin-center.png" alt-text="A screenshot showing the Agent 365 overview page in Microsoft 365 Admin Center." lightbox="media/agent-365-admin-center.png":::


## Microsoft security infrastructure extended to AI agents

Microsoft Defender, Microsoft Entra, and Microsoft Purview now provide agent-specific controls and capabilities. Security practitioners continue to work in the tools they already use, with agent-specific insights and recommendations surfaced directly in each product's portal.

The following sections outline these capabilities.

### Access control

Protect agent identities and prevent breaches by extending conditional access and identity protection from users to agents.

**Microsoft 365 admin center | Microsoft Entra Registry**

Get the complete view of all of the agents used in your organization, including agents with an Entra Agent ID, agents you register yourself, and shadow agents.

:::image type="content" source="media/agent-365-registry.png" alt-text="A screenshot showing the agent identities tab in Microsoft 365 Admin Center." lightbox="media/agent-365-registry.png":::

**Microsoft Entra lifecycle workflows | Microsoft Entra ID governance | Microsoft Entra Conditional Access and Identity Protection**

Limit agents' access to resources they need only and prevent agent compromise with risk-based conditional access policies.

-	Define guardrails - Set policies that define who can create, onboard, and manage agents, assign agent sponsors to keep them under supervision, and ensure that agents start secure with security policy templates.

-	Governance access - Enforce least privilege access by only giving agents access rights to the apps and resources they need to complete tasks.

-	Set conditional access - Enforce real-time intelligent access decisions based on agent context and risk, conditions you define and resource they're trying to access.

:::image type="content" source="media/agent-365-conditional-access.png" alt-text="A screenshot showing the Conditional Access page in Microsoft 365 Admin Center." lightbox="media/agent-365-conditional-access.png":::

Learn more about access control:

- [Protect agent identities with Microsoft Entra](/microsoft-agent-365/admin/capabilities-entra)
- [What is Microsoft agent identity platform?](/entra/agent-id/identity-platform/what-is-agent-id-platform)
- [Governing agent identities (Preview)](/entra/id-governance/agent-sponsor-tasks)
- [Conditional Access for Agent ID](/entra/identity/conditional-access/agent-id?tabs=custom-security-attributes)

### Data security

Gain visibility into AI-related data exposure, protect the data agents create and access from oversharing, leaks, and risky behavior.

**Microsoft Purview Data Loss Prevention | Microsoft Purview Information Protection | Microsoft Purview Data Security Posture Management**

Dynamically block agent interactions with sensitive data based on data security labels and policies.

:::image type="content" source="media/agent-365-purview.png" alt-text="A screenshot showing the Agent page in Microsoft Purview." lightbox="media/agent-365-purview.png":::

Learn more about data security:

- [Data security in Microsoft Agent 365](/microsoft-agent-365/admin/data-security)
- [Use Microsoft Purview to manage data security & compliance for AI agents](/purview/ai-agents)

### Threat protection

Protect agents from threats, vulnerabilities, and adversarial attacks. Detect, investigate, and remediate incidents quickly, with visibility into attack paths.

**Microsoft Defender | Microsoft Security Exposure Management**

Understand your agent and data security posture and attack paths that attackers can create from agents to other critical assets. Remediate misconfigurations, exposures, and vulnerabilities in agents.

:::image type="content" source="media/agent-365-microsoft-defender-posture.png" alt-text="A screenshot showing the Overview tab on the Agent page in Microsoft Defender." lightbox="media/agent-365-microsoft-defender-posture.png":::

**Microsoft Defender**

Detect known and emerging threats targeting agents and enable a rapid response with a complete view of the cyberattack chain and prioritized investigation and response at the incident level.

:::image type="content" source="media/agent-365-microsoft-defender-incident.png" alt-text="A screenshot showing the Incident page in Microsoft Defender." lightbox="media/agent-365-microsoft-defender-incident.png":::

**Microsoft Defender | Microsoft Entra Secure Access Service Edge | Microsoft Purview Insider Risk Management**

Use AI-powered intelligence to block prompt injection attacks, malicious traffic, and prevent data exfiltration due to risky agent behavior in real time.

:::image type="content" source="media/agent-365-runtime-defense.png" alt-text="A screenshot showing the Security and Compliance tab of the Agent page in Microsoft 365 Admin Center." lightbox="media/agent-365-runtime-defense.png":::

Learn more about threat protection:

- [AI agent inventory in Microsoft Defender XDR](/defender-xdr/security-for-ai/ai-agent-inventory)
- [AI agent detection and protection in Microsoft Defender XDR](/defender-xdr/security-for-ai/ai-agent-detection-protection)
- [Protect your environment in real-time during agent runtime](/defender-cloud-apps/real-time-agent-protection-during-runtime)
- [AI Prompt Shield](/entra/global-secure-access/how-to-ai-prompt-shield)

## Next step

Learn more about Microsoft Agent 365: 
- [Microsoft Agent 365 documentation](/microsoft-agent-365).
- [Microsoft Agent 365 blog post: The control plane for AI agents](https://www.microsoft.com/en-us/microsoft-365/blog/2025/11/18/microsoft-agent-365-the-control-plane-for-ai-agents/)