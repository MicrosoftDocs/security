---
title: 3. Identity, Access, and Least Privilege
description: Learn how identity, explicit authorization, and least-privilege controls protect AI agents, plugins, tools, models, and data from excessive agency and unauthorized access.
ms.date: 7/28/2026
ms.custom:   msecd-doc-authoring-1012
ms.topic: concept-article
ms.service: security
ms.subservice: zero-trust
ms.author: ridive
author: richarddiver-ms
---

# 3. Identity, Access, and Least Privilege

## What this group defends against

This group addresses the implicit trust that users, agents, plugins, and tools extend to one another. Every user, agent, plugin, and callable tool receives a verified identity, explicit authorization, and the minimum rights required. This approach counters rug-pull, excessive agency, agent sprawl, confused-deputy plugins, unauthorized memory writes, and tool invocation outside approved scope.

## Core capabilities

Identity controls ensure that every user, agent, workload, plugin, and tool is explicitly identified and authorized before it can access data or perform an action. Bind permissions to the initiating principal and task, limit them to the minimum required scope, and issue them for the shortest practical duration. Treat mult-agent relationships and tool invocations as separate trust decisions, with stronger approval and monitoring when an action is irreversible, high impact, or crosses a security boundary.

- **Verify every principal:** use strong authentication, unique agent identities, managed or federated workload identities, and attributes that support context-aware access decisions.

- **Minimize privilege:** issue scoped, short-lived tokens; restrict model, registry, data, plugin, and tool permissions; and review or remove unused access.

- **Control consequential actions:** define agent-to-agent trust explicitly, require fresh approval for high-risk operations, and limit query rate and volume per principal.

## Which technologies do we use?

Identity protection for AI extends conventional workforce and workload identity controls to agents, plugins, and tools. The following technologies establish unique identities, enforce contextual and least-privilege access, govern Azure configurations, detect compromised credentials, and mediate high-impact tool actions that can't be safely delegated through broad permissions.

- **Microsoft Entra ID** — Microsoft’s cloud identity and access-management service for users, applications, and workloads. Use strong authentication, Conditional Access, managed identities, workload identity federation, short-lived tokens, sign-in risk, access reviews, privileged identity management, and audit logs to verify principals and minimize standing access.

- **Microsoft Entra Agent ID** — an identity and security framework purpose-built for AI agents. Agent identities and reusable blueprints give each agent a governed nonhuman identity, sponsor, lifecycle, authentication path, and auditable access. Apply Conditional Access, identity-risk protection, governance, and network controls to agents built on Microsoft or non-Microsoft platforms.

- **Azure role-based access control (Azure RBAC) and Azure Policy** — authorization and governance services for Azure resources. RBAC limits which actions a user, service, or agent can perform at management-group, subscription, resource-group, or resource scope. Azure Policy audits or denies deployments that violate approved configurations.

- **Microsoft Defender for Identity** — identity threat detection for on-premises Active Directory and hybrid identity environments. It detects suspicious authentication, reconnaissance, credential theft, lateral movement, and compromised-account behavior that could be used to gain access to AI systems or their data.

- **Approval gates and per-tool authorization** — application design controls, not a single product. Bind every tool call to the initiating identity, authorize the exact action and target, use narrowly scoped tokens, and require a fresh human confirmation for irreversible or high-impact actions such as sending, deleting, purchasing, deploying, or changing permissions.

## Framework mapping

**[OWASP Top 10 for LLM and Generative AI](https://genai.owasp.org/llm-top-10/) (2025)**: Primarily maps to LLM06 Excessive Agency by constraining what agents, plugins, and tools can do. Least-privilege scopes, explicit approval for high-risk actions, short-lived tokens, and unique agent identities reduce unauthorized tool use and confused-deputy behavior.

**[MITRE ATLAS](https://atlas.mitre.org/mitigations)**: Maps to AML.M0004 Restrict Number of AI Model Queries and AML.M0005 Control Access to AI Models and Data at Rest, together with standard identity and authorization controls. These measures limit abusive enumeration, protect model registries and training data, and ensure access is scoped to approved principals.

**[NIST AI RMF 1.0 and NIST AI 600-1](https://www.nist.gov/itl/ai-risk-management-framework)**: Supports **GOVERN** and **MANAGE** through accountable ownership, role- and attribute-based access, least privilege, approval gates, and explicit trust relationships among users, agents, tools, models, and data stores.
