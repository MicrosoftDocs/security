---
title: Complete AI threat modeling (Secure Future Initiative) – Zero Trust
description: AI threat modeling in the Microsoft SFI focuses on remediating unique security challenges for generative and agentic AI systems. 
ms.date: 08/05/2025
ms.service: security
ms.subservice: zero-trust
ms.topic: design-pattern
ms.collection: 
  - highpri
  - zerotrust
  - sfi-zerotrust
---

# Complete AI threat modeling

**Pillar name: Monitor and detect threats**<br/>**Pattern name: Complete AI threat modeling**

## Context and problem

Threat modeling is a structured method for proactively identifying, assessing, and addressing risks before they become real-world failures or attacks. While traditional software threat modeling focuses on predictable code paths and deterministic behavior, AI-enabled systems break many of those assumptions.

Generative and agentic AI systems are probabilistic, instruction-driven, and capable of interpreting natural language as executable intent. As a result, data and control paths blur, new attack surfaces emerge, and failures often occur at integration boundaries rather than in isolated components.

Key challenges include:

- Non-deterministic behavior that prevents reasoning about a single execution path or outcome.
- Instruction-following bias that makes models susceptible to prompt injection and unintended control.
- System expansion through tools, memory, and agents, increasing blast radius and compounding failures.
- Human-centered risks such as overreliance, erosion of trust, and harm from persuasive but incorrect outputs.

These challenges underscore the need for threat modeling approaches that explicitly account for AI-specific risks alongside traditional security concerns.

## Solution

Threat modeling for AI systems is an ongoing engineering mindset rather than a one-time checklist. It begins with identifying what must be protected, understanding how the real system behaves end to end, modeling intentional misuse, and designing architectural mitigations that constrain failure.

Organizations can use these functions to structure ongoing assessments as follows:

1. Identify and prioritize assets, including non-traditional assets such as user trust, response correctness, data privacy, and integrity of agent actions.
1. Map the real system architecture, including prompt construction, memory access, tool invocation, external data ingestion, and human approval points.
1. Map misuse scenarios based on adversarial intent, assess use impact and likelihood to inform your response plan, and design mitigations directly into the architecture.
1. Document AI data flows, trust boundaries, and tool permissions as part of the design phase.
Apply scoped least privilege tool access, human-in-the-loop controls, and explicit separation of instructions and data.
1. Use logging and observability to detect misuse, attribute actions, and refine mitigations over time.

## Guidance

Organizations can adopt a similar pattern using the following actionable practices:

|Use case|Recommended action |Resource |
|---|---|---|
GenAI application handling sensitive data   | Treat all external inputs as untrusted and isolate them from system instructions.  |  [Threat modeling AI/ML systems and dependencies](../../engineering/Threat-modeling-aiml.md) |
| Agentic workflows with tool access   | Apply least-privilege tool scoping and require confirmation for high-risk actions. |  [OWASP-Agentic AI - Threats and mitigations](https://genai.owasp.org/resource/agentic-ai-threats-and-mitigations/) |
| Multi-agent coordination   | Explicitly define trust relationships and permissions between agents.  | [Microsoft Entra Agent ID](/entra/agent-id/) |
| High-impact decision support | Add uncertainty signaling and guardrails to prevent overreliance | [Microsoft Foundry-System message design](/azure/ai-foundry/openai/concepts/advanced-prompt-engineering) |
| Production AI systems  | Implement logging, attribution, and audit trails for prompts, tools, and outputs | [Microsoft Incident Response](https://www.microsoft.com/security/business/microsoft-incident-response)  |



### Benefits

- Earlier detection of misuse, abuse, or anomalous behavior.
- Better alignment between system design and real-world risk.
- Reduced likelihood of catastrophic or cascading AI failures.
- Improved user trust through explainable and auditable system behavior.

### Trade-offs

- Added architectural complexity and development effort.
- Performance and latency impacts from additional controls.
- Operational overhead from logging, review, and human approval paths.

## Key success factors

Track these KPIs to measure progress:

- AI‑specific risks are identified early and paired with clear, actionable mitigations (not just documented).
- High‑impact or irreversible actions are intentionally constrained through guardrails such as validation, policy checks, or human approval.
- System behavior is explainable and attributable, with prompts, context, and tool usage traceable for debugging and incident response.
- Misuse and anomalies are surfaced through logging and observability, not discovered primarily through user reports.

## Summary

Threat modeling for AI systems extends traditional security practices to address non-determinism, instruction sensitivity, and system expansion through tools and agents. By focusing on assets, real system behavior, intentional misuse, and observability, organizations can design AI systems that fail safely, contain risk, and improve over time rather than relying on fragile, last-mile controls.
