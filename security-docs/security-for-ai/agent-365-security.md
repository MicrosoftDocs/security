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

## Extend your Microsoft security infrastructure to secure all of your AI agents

Microsoft Agent 365 provides a centralized framework for securing all of the AI agents in your environment. By integrating with Microsoft’s security suite - Microsoft Entra, Microsoft Purview, Microsoft Defender - and Microsoft 365 Admin Center, Agent 365 delivers:

- **Full observability**: Gain complete visibility into your agent fleet, including inventory and activity tracking.
- **Identity-first security**:  Enforce strong identity controls with Entra Agent ID and apply conditional access to ensure agents are authenticated and governed like human identities.
- **Data security**: Enforce regulatory policies, apply sensitivity labels, and prevent data leaks with Microsoft Purview.
- **Threat protection and posture management**: Detect risks, enforce security baselines, and remediate vulnerabilities using Microsoft Defender.

## Next step

Learn more about [Microsoft Agent 365 security capabilities](https://review.learn.microsoft.com/en-us/microsoft-agent-365/overview?branch=main).