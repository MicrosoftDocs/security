---
title: 1. Rug-Pull Attack (Agent / MCP Server)
description: Explains how a trusted agent, tool, or MCP server can turn malicious after initial approval (a rug-pull), and the identity, vetting, and monitoring controls needed to prevent it
ms.date: 7/28/2026
ms.custom:   msecd-doc-authoring-1012
ms.topic: concept-article
ms.service: security
ms.subservice: zero-trust
ms.author: ridive
author: richarddiver-ms
---

# 1. Rug-Pull Attack (Agent / MCP Server)

Security researchers in 2025 highlighted *MCP rug-pull attacks* in agent networks: if a tool’s definition on an MCP server is silently altered after initial approval, an agent may call the tool believing it safe, but the tool’s behavior is now malicious. For instance, a trusted tool like “send_slack_message” could later be changed to perform data exfiltration or execute unauthorized actions without detection. Because agents don’t re-verify tool integrity, the malicious actions are executed under the radar. Such research spurred development of MCP security gateways to monitor tool changes and filter malicious content. This scenario is not merely theoretical: in April 2025, Microsoft’s AI security team warned of exactly these “cross-domain prompt injection” exploits in agentic systems and implemented mitigations (Prompt Shields and supply chain checks) to protect their own Azure AI services.

## What happens in this scenario
In a *rug-pull attack*, a malicious AI agent or tool in a multi-agent ecosystem “turns rogue” after initially being trusted. For example:

1.  An enterprise sets up a system where a user’s **AI assistant** (Agent A) queries a central **Model Context Protocol (MCP)** server to find a specialized **service agent** for a task (say, fetching weather data).

2.  An attacker registers or compromises a service agent (Agent B) on that platform. When Agent A asks for weather info, the MCP directory unknowingly routes the request to malicious Agent B.

3.  The malicious agent then sends **cross-entity instructions** (a form of prompt injection) back to Agent A, instructing it to perform harmful actions under the guise of a valid response.

> In essence, the attacker **“pulls the rug”** from under the trusted relationship, exploiting the fact that Agent A trusts responses from the MCP network. This can lead to unauthorized data exposure or unintended commands being executed by Agent A.

## Why this technique is effective
It exploits **implicit trust and lack of verification** in agent-to-agent communications, and the same trust failure can extend to agent-to-tool and agent-to-data interactions. In many agent networks, once an agent, tool, or grounding data source is approved, its outputs are not continuously re-verified. Attackers take advantage of this by either impersonating a legitimate service, compromising a once-legitimate agent or tool, or manipulating data the agent treats as authoritative.

Because agents tend to accept instructions from their peers, connected tools, API responses, retrieved documents, memory entries, or grounding data without human oversight, a malicious agent, tool, or poisoned data source can insert directives that appear credible. If Agent A can reason or access data, it might share sensitive info with the hostile agent, call a compromised tool, rely on manipulated data, or execute instructions, believing them to be part of normal operations.

In short, the attack succeeds by abusing the *trust and lack of ongoing scrutiny* in an agent network.

## Recommended controls
A *defense-in-depth* approach is critical. Key measures include:

- **Strong agent identity and authorization**: Implement robust authentication and Role-Based Access Control (RBAC) for each agent or tool. Every agent, tools, or plugin should have a verified identity and permissions limited to its role. For example, require that service agents declare their capabilities and ensure Agent A only accepts responses fitting the expected format or source.

- **Supply chain vetting for agents and tools**: Treat every agent, tool, plugin, MCP server, and data connector as part of the AI supply chain. Vet and approve the agents and tools your system communicates with before establishing trust, including ownership, source, signing, version integrity, permissions, and expected behavior.

- **MCP server defenses and monitoring**: Enhance the central coordination server with security checks. The MCP should validate agent responses for malicious patterns (e.g. unexpected instructions) using prompt monitoring or anomaly detection. Suspicious cross-agent instructions should be blocked or flagged for review.

- **Data labeling and sharing policies**: Use data classification (e.g. sensitivity labels via DLP solutions) so that even if Agent A fetches data, it knows what can be shared onward. Enforce context-based access – agents should only retrieve or disseminate data appropriate for the requesting entity’s privileges.

- **Agent communication sandboxing**: Design agent interactions to be constrained. For instance, disallow free-form agent-to-agent instructions when possible or require a mediating layer that strips or validates content. Use *allowlists* of approved agent responses or formats.

- **AI logging and forensic monitoring**: Capture detailed logs of inter-agent messages and actions. Send these logs to a security information and event management (SIEM) system for real-time analysis (to detect anomalies) and post-incident investigations.

- **Block and escalate critical anomalies**: Critical or high-confidence anomalies should not merely be logged or flagged. They should automatically block the proposed action and escalate to an authorized human, policy workflow, or security operations queue for review and approval before execution.

## Technologies to consider
*No single tool solves this alone; a layered approach is needed.* Possible components include:

- **MCP Gateway with Security Filters**: If using an MCP or similar agent orchestration, employ a gateway that can enforce policies (e.g., only allow known-safe agent responses). Microsoft’s research on **AI “Prompt Shields”** is an example of emerging technology to inspect and neutralize malicious cross-agent prompts.

- **Agent management**: Use Microsoft Agent 365 to discover, inventory, govern, and monitor agents across the environment, helping ensure only approved agents and agent-to-tool interactions are allowed and continuously reviewed.

- **Identity and access management**: Microsoft Entra or similar IAM solutions to enforce RBAC and authenticate agents or plugins.

- **Data labeling & DLP**: Tools like Microsoft Purview for classifying and protecting sensitive data, and ensuring agents comply with data-sharing policies.

- **Security monitoring**: SIEM solutions like Microsoft Sentinel or equivalent for aggregating agent logs and detecting unusual activities or policy violations in agent interactions.

- **Endpoint/application protection**: Traditional measures (firewalls, endpoint protection, network segmentation) to contain potential fallout if an agent misbehaves.

## OWASP Top 10 mapping
**[OWASP Top 10 for LLM and Generative AI](https://genai.owasp.org/llm-top-10/) (2025)**

This scenario maps to **LLM01: Prompt Injection** (attacker‑crafted inputs steering the model into malicious tool use), **LLM03: Supply Chain** (exploitation of compromised or untrusted tools, plugins, or external dependencies), **LLM06: Excessive Agency** (the model delegates harmful actions to over‑privileged tools), **LLM07: System Prompt Leakage** (prompt patterns that expose or manipulate internal instructions to trigger the swap), and **LLM08: Vector and Embedding Weaknesses** (poisoned retrieval or manipulated embeddings that guide the model toward the fraudulent “rug‑pull” endpoint).

## MITRE ATLAS mapping
A trusted agent or tool is silently altered after approval, so the victim agent executes malicious cross-agent instructions as if legitimate. MITRE ATLAS does not currently define a dedicated “rug-pull” technique, so this is a closest-fit mapping; it maps to supply-chain compromise, agent-tool abuse, and indirect prompt injection.

**[MITRE ATLAS Techniques](https://atlas.mitre.org/techniques) (Attack):**
The attack primarily reflects supply-chain compromise and adversarial input abuse: a trusted agent, tool, registry, or data source is modified or misused after approval, causing the victim agent to accept malicious instructions as legitimate. 
* AML.T0010 AI Supply Chain Compromise (esp. .005 AI Agent Tool)
* AML.T0051.001 LLM Prompt Injection
* AML.T0053 AI Agent Tool Invocation
* AML.T0110 AI Agent Tool Poisoning


**[MITRE ATLAS Mitigations](https://atlas.mitre.org/mitigations) (Defense):**
Prioritize supply-chain vetting, component validation, input filtering, sandboxed execution, behavioral monitoring, and escalation for critical anomalies.
* AML.M0005 / AML.M0019 Control Access to AI Models & Data (at rest / in production)
* AML.M0013 Code Signing
* AML.M0014 Verify AI Artifacts
* AML.M0020 Generative AI Guardrails
* AML.M0023 AI Bill of Materials
* AML.M0024 AI Telemetry Logging

