---
title: Oversee AI agent security using Microsoft Agent 365
description: How to use Microsoft Agent 365 to secure all of the AI agents in your environment. 
ms.date: 11/09/2025
ms.update-cycle: 180-days
ms.service: security
ms.subservice: security-for-ai
author: guywi-ms
ms.author: guywild
ms.topic: concept-article
ms.collection: 
  - msftsolution-security-for-ai
  - msftsolution-scenario
  - zerotrust-solution
  - msec-ai-copilot

# Customer intent: As a SOC manager, I want to manage the security of all of the AI agents in my organization so that I can ensure the safety of our data and systems.

---

# Oversee AI agent security using Microsoft Agent 365

As organizations adopt AI agents to automate workflows and enhance productivity, securing these agents has become a critical concern. Unlike traditional applications, AI agents operate autonomously, interact with sensitive data, and execute tasks across multiple systems - making them high-value targets for intentional attacks and also vulnerable to unintentional compromise caused by misconfigurations or excessive permissions.

Microsoft Agent 365 provides a unified control plane that lets you oversee the security of all AI agents in your organization. It integrates with Microsoft’s security suite - now extended to secure AI agents - to secure agents built in Microsoft 365 Copilot, Microsoft Copilot Studio, AI Foundry, and third-party solutions.

This article outlines the core security capabilities that Microsoft Agent 365 provides based on Microsoft’s extended security infrastructure for AI agents.

For more information about Microsoft Agent 365, see [Microsoft Agent 365 documentation](https://review.learn.microsoft.com/en-us/microsoft-agent-365/overview/).

## A unified control plane for managing agent security

Agent 365 works seamlessly with Microsoft 365 Copilot by automatically applying identity, compliance, and security controls to Copilot agents. It also integrates with Microsoft 365 Admin Center, giving IT teams a familiar interface to configure policies, apply Conditional Access, and monitor compliance across the agent fleet.

This control plane provides centralized visibility and lets you drill down into Microsoft's suite of security tools to manage posture, configure policies, investigate issues, and remediate risks.

:::image type="content" source="media/agent-365-admin-center.png" alt-text="A screenshot showing the agent identities tab in Microsoft 365 Admin Center." lightbox="media/agent-365-admin-center.png":::


## Microsoft security infrastructure extended to AI agents

By integrating with Microsoft’s security suite - which now provides agent-specific controls and capabilities - Agent 365 lets you manage AI agent security across key areas. Drill down into each security product from the Agent 365 control plane to act on agent-specific insights and recommendations, including:

| Area | Description | Products |
|------|-------------|----------|
| **Security posture** | Understand your agent and data security posture and attack paths that attackers can create from agents to other critical assets. Remediate misconfigurations, exposures, and vulnerabilities in agents. | Microsoft Defender<br>Microsoft Security Exposure Management |
| **Detection and response** | Detect known and emerging threats targeting agents and enable a rapid response with a complete view of the cyberattack chain and prioritized investigation and response at the incident level. | Microsoft Defender |
| **Runtime defense** | Use AI-powered intelligence to block prompt injection attacks, malicious traffic, and prevent data exfiltration due to risky agent behavior in real time. | Microsoft Defender<br>Microsoft Entra Secure Access Service Edge<br>Microsoft Purview Insider Risk Management |
| **Data security** | Gain visibility into AI-related data exposure risks and dynamically block agent interactions with sensitive data based on data security labels and policies. | Microsoft Purview Data Loss Prevention<br> Microsoft Purview Information Protection<br>Microsoft Purview Data Security Posture Management |


## Next step

Learn more about [Microsoft Agent 365](https://review.learn.microsoft.com/en-us/microsoft-agent-365/?branch=main).