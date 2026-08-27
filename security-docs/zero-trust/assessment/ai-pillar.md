---
title: Configure Microsoft Entra agent identities for increased security
description: Improve your security posture with the Microsoft Entra Zero Trust assessment to secure AI agents and workloads.

ms.topic: concept-article
ms.date: 06/04/2026
ms.service: security
ms.subservice: zero-trust

ms.author: sarahlipsey
author: shlipsey3
manager: pmwongera
ms.reviewer: ramical
ai-usage: ai-assisted
#Customer Intent: As an IT admin, I want to understand how to secure AI agents and workloads so that I can prevent unauthorized access and enforce governance over autonomous identities.
---

# Configure agent identity security with the Zero Trust Assessment

AI agents acquire access tokens for organizational resources on every interaction, including mail, files, line-of-business APIs, and downstream agents. Unlike interactive users, agents usually don't present the same sign-in signals, such as user MFA, managed device state, or location context. Securing the AI control plane is therefore essential to your Zero Trust journey.

Agent issues commonly appear in three areas:

- **Authentication and policy mismatch**: Policies designed for users can miss agent-specific token patterns and execution models.
- **Overpermissioned access**: Agents often accumulate broad API permissions across Microsoft Graph and custom APIs, increasing blast radius.
- **Lifecycle and accountability gaps**: Orphaned agent identities, missing owners or sponsors, and stale credentials create persistent risk.

The recommendations and Zero Trust checks that are part of this pillar help reduce the risk of unauthorized AI access. Themes include enforcing Entra authentication on agent endpoints, applying Conditional Access policies to agent identities, assigning lifecycle governance controls, and ensuring AI administrative roles have accountable principals.

## Zero Trust security recommendations for AI

### Require Microsoft Entra ID authentication to interact with agents
[!INCLUDE [61011](../../includes/entra-content/docs/includes/secure-recommendations/61011.md)]

### Conditional Access policies cover both agent identities and agent users
[!INCLUDE [61009](../../includes/entra-content/docs/includes/secure-recommendations/61009.md)]

### Risk-based Conditional Access blocks risky agent identities
[!INCLUDE [61012](../../includes/entra-content/docs/includes/secure-recommendations/61012.md)]

### Custom security attributes for agent identities are present
[!INCLUDE [61008](../../includes/entra-content/docs/includes/secure-recommendations/61008.md)]

### Identity governance for agent identity sponsors is configured
[!INCLUDE [61013](../../includes/entra-content/docs/includes/secure-recommendations/61013.md)]

### Agent identities and blueprint principals have assigned technical owners and no disabled agents remain in the directory
[!INCLUDE [61014](../../includes/entra-content/docs/includes/secure-recommendations/61014.md)]

### AI administrative roles have assigned principals
[!INCLUDE [61006](../../includes/entra-content/docs/includes/secure-recommendations/61006.md)]