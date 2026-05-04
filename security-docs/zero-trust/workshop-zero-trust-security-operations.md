---
title: Microsoft Zero Trust Workshop - Secops
description: Learn about the SecOps pillar in the Microsoft Zero Trust Workshop
ms.date: 04/18/2024
ms.service: security
author: rayne-wiselman
ms.author: raynew
ms.subservice: zero-trust
ms.topic: conceptual
---

# SecOps in the Microsoft Zero Trust Workshop

Security oerations (SecOps) is fundamental to Zero Trust because it ensures that you’re not just preventing bad things, but also detecting, investigating, and responding to threats continuously. In a Zero Trust model, you assume breach, so having strong SecOps capabilities is essential to contain attacks, mitigate impact, and maintain resilience.

SecOps pillar guidance focuses monitoring security across the organization and collecting security data, detecting threats and issuing security alerts, incident response, orchestration, and automation, proactive threat hunting and threat intelligence. The SecOps workshop covers these implementation areas:

- **Centralize detection**: Integrate logs and telemetry from across your environment (identity, endpoints, infrastructure) into a centralized system such as Microsoft Defender/Sentinel for unified visibility. Ensure your SecOps team has the right sources and analytics to detect compromise early.
- **Automate threat response**: Use tools such as Microsoft Sentinel playbooks to automate response workflows. For example, isolating compromised machines or disabling risky accounts. Define incident-response rules that are triggered automatically, reducing human reaction time and error.
- **Proactively hunt for threats**: Leverage threat-hunting capabilities. Use built-in or custom queries to detect suspicious patterns before they become incidents. Use advanced tools such as Microsoft Defender/Sentinel to hunt for attacker behaviors or anomalies.
- **Manage incidents and alerts**: Tune and suppress noisy alerts so that SecOps focuses on meaningful alerts. Build playbooks for investigation and response, to optimize containment and remediation.
- **Proactively review and remediate risk**: Use tools such as Cloud Security Explorer in Microsoft Defender for Cloud to map attack paths, identify risky exposures, and remediate them. Prioritize remediation based on risk, not just on alert volume, to ensure high-risk issues are addressed first.
- **Continuously optimize SecOps processes**: Regularly review and update your incident-response playbooks, runbooks, and detection logic in response to new threats. Incorporate lessons from incidents and threat-hunting into your SecOps strategy, ensuring your team evolves.
