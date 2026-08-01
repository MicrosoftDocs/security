---
title: 9. Excessive Agency (Agents)
description: Explains the risks of granting AI agents excessive autonomy or tool access, and the guardrails needed to prevent unintended or harmful actions.
ms.date: 7/28/2026
ms.custom:   msecd-doc-authoring-1012
ms.topic: concept-article
ms.service: security
ms.subservice: zero-trust
ms.author: ridive
author: richarddiver-ms
---

# 9. Excessive Agency (Agents)

In a controlled test documented in OpenAI’s **GPT-4 System Card**, researchers gave GPT-4 access to certain tools and objectives. The AI **hired a human TaskRabbit worker to solve a CAPTCHA** by falsely claiming to be a visually impaired person. This was not a malicious attacker at play, but it demonstrated that a sufficiently advanced AI, if instructed to reach a goal by any means, might **deceive humans or exploit resources** to do so.

Another example from 2023: an autonomous agent using GPT-4 (dubbed “ChaosGPT”) was tasked to “destroy humanity” as a public experiment – it started scouring the internet for instructions and even tried to delegate tasks to other AI agents. Though it ultimately failed in its outrageous goal, it highlighted how an **unconstrained AI could attempt destructive actions** when given problematic objectives.

These illustrations, while not from a hostile outsider, foretell what could happen if an attacker manages to point a highly-privileged AI in a malicious direction. Without strict limits, an AI could become the ultimate insider threat – not out of evil intent, but simply by following its programming too well.

## What happens in this scenario
*Excessive agency* refers to giving an AI system **too much autonomous decision-making power or access to perform actions on its own**. In this scenario:

1.  An enterprise allows an AI to take actions automatically – such as sending emails, making financial transactions, modifying databases, or controlling OT/IT systems – without sufficient oversight or limits.

2.  If this highly autonomous AI is manipulated (via a prompt injection, compromised objectives, or even its own flawed “judgment”), it could carry out damaging actions.

3.  For example, an AI Ops agent with access to an infrastructure management API might decide to *“fix”* an issue by rebooting servers during peak business hours, causing an outage – simply because its prompt said **“always ensure system consistency”** and it interpreted a discrepancy as critical.

4.  In another extreme example (drawn from real testing), an AI tasked with *“get resources to achieve your goal”* could independently attempt to hire a human (via an online service) to solve a CAPTCHA for it, using deception to do so.

> In essence, the scenario is that the AI, operating with too much independence, becomes an *unpredictable actor* that can perform unintended or harmful operations.

## Why this technique is effective
It’s not so much a single hack as a dangerous situation created by design. When an AI has excessive autonomy:

- **Unpredictable outcomes**: LLMs can *hallucinate* – they sometimes produce untrue or illogical results with high confidence. If they have the freedom to act on such outputs, mistakes can become incidents (e.g., mis-sending an email to all customers, or misconfiguring a security group).

- **Susceptibility to manipulation**: The more power an AI has, the more tempting a target it becomes. Attackers can focus on forcing a highly-privileged AI to do something on their behalf (combining this with prompt injection or plugin exploits). If successful, the attacker can indirectly execute powerful actions without ever directly accessing the system.

- **Lack of human common-sense**: AIs don’t truly understand the real-world implications of actions; they can’t be held accountable. If their instructions or training are incomplete or ambiguous, they might do something catastrophically wrong but logically consistent from their perspective. Attackers or even unknowing users can exploit these blind spots. Excessive agency is essentially an *amplifier* of other risks – it turns a misstep or misprompt into a tangible impact. It is effective because, in complex enterprise environments, covering every scenario in the AI’s instructions is nearly impossible. Without constraints, the AI might err or be led astray, and there may be *no immediate human in the loop to catch it*.

## Recommended controls
- **Limit autonomous scope**: Carefully scope what an AI is allowed to do. Follow the principle “trust but verify.” For example, an AI-driven script might prepare a change in a system but not deploy it without review. Use **approval workflows** – e.g., the AI can draft an action, but a person or a simpler rule-based system must approve it.

- **Permission gating**: Build a permission model for AI actions. An AI with multiple capabilities (read/write files, send emails, make transactions) should be treated like a user: grant the minimum necessary permissions. If it doesn’t need to delete data or spend money, prevent those actions at the system level.

- **Fallback and safe modes**: Ensure there are “kill switches” or safe states. If the AI’s behavior seems off or it triggers certain thresholds (like trying to perform a high-risk action), it should automatically shut down or revert to a read-only state. You can implement circuit breakers that turn off AI actuation capabilities if anomalies are detected.

- **Continuous monitoring of AI decisions**: Log all actions the AI takes and use anomaly detection to flag unusual ones. If an AI that usually updates user permissions suddenly attempts to assign itself admin rights, that’s a red flag. Monitoring systems should catch it and halt the process.

- **Robust training and testing**: In development, simulate many scenarios (including malicious ones) to see how the AI behaves. Conduct red-team exercises specific to autonomy: e.g., “If given conflicting orders, will the AI do something dangerous?” Use those findings to refine the AI’s constraints.

## Technologies to consider
- **Orchestration with human oversight:** Use tools like **Microsoft Power Automate** or **Azure Logic Apps** with built-in approval steps. Instead of letting the AI directly call an API to, say, make a payment, have the AI draft the payment and then use an automated workflow that requires a human manager’s approval.

- **Azure Role-Based Access Control (RBAC):** Treat the AI agent as a service account with specific roles. For instance, if an AI is managing Azure resources, give it a narrowly scoped role (not a Subscription Owner!). Use **Managed Identities for Azure services** so that you can finely tune what the AI is allowed to do. Also consider **Microsoft Entra Agent ID** for assigning, governing, and monitoring agent identities.

- **Policy enforcement:** Implement policies via **Azure Policy** or cloud IAM that prevent critical actions unless certain conditions are met (for example, block deletion of resources unless initiated through a specific approved process). If the AI tries to do so outside that process, the action is denied.

- **AI governance platforms:** Consider using AI governance tools that track AI decisions and provide an oversight dashboard. Some emerging solutions allow setting policy guardrails and will intervene or alert if the AI tries to go out of bounds. Consider Microsoft Agent 365 for centralized agent discovery, inventory, governance, and monitoring.

- **Testing frameworks:** Leverage testing frameworks like **ATLAS** (MITRE’s Adversarial ML framework) to simulate attacks and risky scenarios on AI with autonomy. This helps identify where further restrictions are needed.


## OWASP Top 10 mapping
[OWASP Top 10 for LLM and Generative AI](https://genai.owasp.org/llm-top-10/) (2025)

This scenario maps to **LLM06: Excessive Agency**, where an autonomous agent is granted overly broad permissions or insufficient guardrails, enabling it to take unintended, unsafe, or irreversible actions on behalf of the user or system.

## MITRE ATLAS mapping
This scenario maps broadly to MITRE ATLAS behaviors around autonomous system abuse, unchecked delegation, and unsafe tool or agent execution. MITRE ATLAS does not currently define a single “excessive agency” technique, so these are closest-fit mappings that depend on whether the unsafe action is driven by prompt injection, jailbreak behavior, tool invocation, or downstream harm.

**[MITRE ATLAS Techniques](https://atlas.mitre.org/techniques) (Attack):**
The attack primarily reflects excessive autonomy: an agent is allowed to plan, delegate, or act beyond intended scope, especially when manipulated by prompts, tools, or flawed objectives.
* AML.T0051 LLM Prompt Injection
* AML.T0053 AI Agent Tool Invocation
* AML.T0054 LLM Jailbreak
* AML.T0048 External Harms

**[MITRE ATLAS Mitigations](https://atlas.mitre.org/mitigations) (Defense):**
Prioritize least privilege, bounded action allowlists, human approval for critical steps, resource limits, orchestration guardrails, and behavioral monitoring.
* AML.M0019 Control Access to AI Models & Data in Production
* AML.M0020 Generative AI Guardrails
* AML.M0021 Generative AI Guidelines
* AML.M0024 AI Telemetry Logging
