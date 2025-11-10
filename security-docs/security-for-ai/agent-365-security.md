---
title: Manage AI agent security using Microsoft Agent 365
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

# Manage AI agent security using Microsoft Agent 365

As organizations adopt AI agents to automate workflows and enhance productivity, securing these agents has become a critical concern. Unlike traditional applications, AI agents operate autonomously, interact with sensitive data, and execute tasks across multiple systems - making them high-value targets for intentional attacks and also vulnerable to unintentional compromise caused by misconfigurations or excessive permissions.

Microsoft Agent 365, Microsoft's unified control plane for AI agents, lets you secure all of your AI agents, including agents built in Microsoft 365 Copilot, Microsoft Copilot Studio, AI Foundry, and third-party solutions.

This article outlines the core security capabilities of Microsoft Agent 365 and shows how it builds on Microsoft’s existing security foundation to manage AI agents effectively.

## Extend your Microsoft security infrastructure to secure your AI agents

Microsoft Agent 365 provides a centralized framework for securing all of the AI agents in your environment. By integrating with Microsoft’s security suite - Microsoft Entra, Microsoft Purview, Microsoft Defender - and Microsoft 365 Admin Center, Agent 365 delivers:

- **Full observability**: Gain complete visibility into your agent fleet, including inventory and activity tracking.
- **Identity-first security**:  Enforce strong identity controls with Entra Agent ID and apply conditional access to ensure agents are authenticated and governed like human identities.
- **Data security**: Enforce regulatory policies, apply sensitivity labels, and prevent data leaks with Microsoft Purview.
- **Threat protection and posture management**: Detect risks, enforce security baselines, and remediate vulnerabilities using Microsoft Defender.


Secure AI agents in Microsoft Copilot 365 and Microsoft 365 admin center using Microsoft Agent 365.



Secure agents created using Foundry, Copilot Studio, Copilot 365, and third-parties

For the SOC

Security tools: Purview, Defender, Entra

- Observability: Monitor AI agent activities, data access, and interactions across your organization.
- Access Control: Implement role-based access controls (RBAC) and conditional access policies to manage who can create, deploy, and interact with AI agents.
- Data Protection: Use data loss prevention (DLP) policies and encryption to safeguard sensitive information accessed or processed by AI agents.
- Threat Detection: Leverage Microsoft Defender to identify and respond to potential threats or anomalies in AI agent behavior.

Link from A365 Learn page to this doc.

Defender: Posture management and threat protectionfor AI agents, investigation and hunting

## Next step for securing AI

After discovering the AI usage in your organization, the next step is to apply protections:

- Protect sensitive data used with AI apps
- Implement threat protection specifically for AI use

See the next article in this series: [How do I protect my organization while using AI apps?](protect.md)