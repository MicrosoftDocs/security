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

As organizations adopt AI agents at scale, securing them has become a critical concern. [Microsoft Agent 365](/microsoft-agent-365/overview/) extends your existing security infrastructure – Microsoft Defender, Microsoft Entra, and Microsoft Purview – to agents, with purpose-built capabilities for securing agents.

This article outlines how Microsoft Agent 365 secures AI agents.

## A distributed security model with centralized visibility

AI agents introduce new security challenges, including:
- Agent sprawl from user-created and SaaS agents that expands the attack surface
- Over-privileged agents with excessive resource access
- Tool misuse when agents are manipulated into abusing authorized tools
- Misconfigured or vulnerable agents without proper authentication or boundaries
- Traditional AI threats, such as prompt injection and data leakage, that now extend across agent interactions

As part of Microsoft Agent 365, Microsoft Defender, Microsoft Entra, and Microsoft Purview now provide purpose-built controls for agents. Security practitioners continue working in the tools they already use, with agent insights and recommendations surfaced directly in each product's portal.

The Agent 365 overview in the Microsoft 365 admin center provides centralized visibility into AI agents across the organization, including usage insights and security signals that help administrators take action.

:::image type="content" source="media/agent-365-admin-center.png" alt-text="A screenshot showing the Agent 365 overview page in Microsoft 365 Admin Center." lightbox="media/agent-365-admin-center.png":::

Security teams define governance requirements by creating policy templates, such as access packages in Microsoft Entra. During onboarding, IT teams apply these templates to agents, ensuring governance and compliance are enforced from the start.

## Access control with Microsoft Entra

Agents that sprawl or accumulate excessive permissions create risk. Microsoft Entra gives you visibility into all agent identities and helps enforce least-privilege access:

- **Visibility into agent identities** – Get the complete view of all agents in your organization, including agents with an Entra Agent ID, agents you register yourself, and shadow agents.

  :::image type="content" source="media/agent-365-registry.png" alt-text="A screenshot showing the agent identities tab in Microsoft 365 Admin Center." lightbox="media/agent-365-registry.png":::

- **Conditional access and identity protection** – Extend conditional access and identity protection policies from users to agents. Enforce real-time access decisions based on agent context, risk level, and resource sensitivity.

  :::image type="content" source="media/agent-365-conditional-access.png" alt-text="A screenshot showing the Conditional Access page in Microsoft 365 Admin Center." lightbox="media/agent-365-conditional-access.png":::

- **Secure Access Service Edge (SASE)** – Monitor and block malicious and non-compliant network traffic from agents running on user devices, including Copilot Studio agents.
- **Agent governance and lifecycles** – Ensure agents have responsible sponsors providing oversight, and manage access so it doesn't persist longer than needed.

Learn more about access control:

- [Protect agent identities with Microsoft Entra](/microsoft-agent-365/admin/capabilities-entra)
- [What is Microsoft agent identity platform?](/entra/agent-id/identity-platform/what-is-agent-id-platform)
- [Governing agent identities (Preview)](/entra/id-governance/agent-sponsor-tasks)
- [Conditional Access for Agent ID](/entra/identity/conditional-access/agent-id?tabs=custom-security-attributes)
- [Secure Access Service Edge for agents](/entra/global-secure-access/how-to-ai-prompt-shield)

## Data security with Microsoft Purview

Agents create, access, and share data across systems – increasing the risk of oversharing and sensitive data exposure. Microsoft Purview controls what data agents can access and how they use it, and helps you meet compliance obligations across the agent lifecycle:

- **Data security posture management** – Get deep interaction visibility for agents and identify AI-related data exposure risks.
- **Sensitivity labels** – Agents inherit and honor data sensitivity labels, ensuring consistent data protection across human and agent interactions.
- **Data loss prevention** – Block agents from accessing and sharing sensitive content based on data security labels and policies.
- **Insider risk management and communication compliance** – Detect risky activity and monitor interactions for policy violations.
- **Auditing** – Log and audit all agent interactions for compliance review and forensic investigation.
- **Data lifecycle management** – Apply retention and deletion policies to agent-generated content so data is kept only as long as needed.
- **eDiscovery** – Search, preserve, and export agent interactions and outputs to support legal, regulatory, and internal investigations.
- **Compliance Manager** – Assess agent instances against AI regulations using built-in assessments to track and improve your compliance posture.

:::image type="content" source="media/agent-365-purview.png" alt-text="A screenshot showing the Agent page in Microsoft Purview." lightbox="media/agent-365-purview.png":::

Learn more about data security and compliance:

- [Data security in Microsoft Agent 365](/microsoft-agent-365/admin/data-security)
- [Microsoft Purview data security and compliance protections for Microsoft Agent 365](/purview/ai-agent-365)

## Threat protection with Microsoft Defender

Agents can be manipulated into misusing authorized tools, misconfigured without proper authentication, or targeted by prompt injection attacks. Microsoft Defender identifies these risks and enables rapid response:

- **Agent security posture management** – Identify and remediate agent misconfigurations and exposure risks. Visualize attack paths from agents to critical assets.

  :::image type="content" source="media/agent-365-microsoft-defender-posture.png" alt-text="A screenshot showing the Overview tab on the Agent page in Microsoft Defender." lightbox="media/agent-365-microsoft-defender-posture.png":::

- **Threat detection and blocking** – Detect suspicious agent activity, receive alerts, and block malicious tool invocations in real-time.

  :::image type="content" source="media/agent-365-microsoft-defender-incident.png" alt-text="A screenshot showing the Incident page in Microsoft Defender." lightbox="media/agent-365-microsoft-defender-incident.png":::

- **Threat investigation and hunting** – Collect unified agent observability logs and hunt for threats across agent activity.

  :::image type="content" source="media/agent-365-runtime-defense.png" alt-text="A screenshot showing the threat investigation and hunting page in Microsoft Defender." lightbox="media/agent-365-runtime-defense.png":::

Learn more about threat protection:

- [AI agent inventory in Microsoft Defender XDR](/defender-xdr/security-for-ai/ai-agent-inventory)
- [AI agent detection and protection in Microsoft Defender XDR](/defender-xdr/security-for-ai/ai-agent-detection-protection)

## Next steps

Learn more about Microsoft Agent 365:

- [Microsoft Agent 365 documentation](/microsoft-agent-365)
- [Microsoft Agent 365 blog post: The control plane for AI agents](https://www.microsoft.com/en-us/microsoft-365/blog/2025/11/18/microsoft-agent-365-the-control-plane-for-ai-agents/)
