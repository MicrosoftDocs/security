---
title: Configure Microsoft Entra agent identities for increased security
description: Improve your security posture with the Microsoft Entra Zero Trust assessment to secure AI agents and workloads.
ms.service: security
ms.subservice: zero-trust
ms.topic: concept-article
ms.date: 05/18/2026

ms.author: sarahlipsey
author: shlipsey3
manager: pmwongera
ms.reviewer: ramical
ai-usage: ai-assisted
#Customer Intent: As an IT admin, I want to understand how to secure AI agents and workloads so that I can prevent unauthorized access and enforce governance over autonomous identities.
---

# Configure Microsoft Entra for Zero Trust: AI (Preview)

The recommendations included in this AI pillar is one part of a broader Zero Trust strategy. The complete program includes identity, devices, network, applications, infrastructure, and data protection, plus continuous monitoring and response. For the main guidance, see the [Zero Trust guidance center](/security/zero-trust).

The [Zero Trust Assessment](/security/zero-trust/assessment/overview) helps you evaluate whether core security controls are configured and effective across your environment. It applies Zero Trust principles of verify explicitly, use least privilege, and assume breach through practical checks that improve security posture over time.

AI agents acquire access tokens for organizational resources on every interaction, including mail, files, line-of-business APIs, and downstream agents. Unlike interactive users, agents usually don't present the same sign-in signals, such as user MFA, managed device state, or location context. Securing the AI control plane is therefore essential to your Zero Trust journey.

Agent issues commonly appear in three areas:

- **Authentication and policy mismatch**: Policies designed for users can miss agent-specific token patterns and execution models.
- **Overpermissioned access**: Agents often accumulate broad API permissions across Microsoft Graph and custom APIs, increasing blast radius.
- **Lifecycle and accountability gaps**: Orphaned agent identities, missing owners or sponsors, and stale credentials create persistent risk.

The recommendations and Zero Trust checks that are part of this pillar help reduce the risk of unauthorized AI access. Themes include enforcing Entra authentication on agent endpoints, applying Conditional Access policies to agent identities, assigning lifecycle governance controls, and ensuring AI administrative roles have accountable principals.

## Zero Trust security recommendations for AI

### Require Microsoft Entra ID authentication to interact with agents
[!INCLUDE [61011](/entra/includes/secure-recommendations/61011)]

### Conditional Access policies cover both agent identities and agent users
[!INCLUDE [61009](/entra/includes/secure-recommendations/61009)]

### Risk-based Conditional Access blocks risky agent identities
[!INCLUDE [61012](/entra/includes/secure-recommendations/61012)]

### Custom security attributes for agent identities are present
[!INCLUDE [61008](/entra/includes/secure-recommendations/61008)]

### Identity governance for agent identity sponsors is configured
[!INCLUDE [61013](/entra/includes/secure-recommendations/61013)]

### Agent identities and blueprint principals have assigned technical owners and no disabled agents remain in the directory
[!INCLUDE [61014](/entra/includes/secure-recommendations/61014)]

### AI administrative roles have assigned principals
[!INCLUDE [61006](/entra/includes/secure-recommendations/61006)]
