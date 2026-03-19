--- 
title: Defend against indirect prompt injection attacks
description: Learn about defense-in-depth for indirect prompt injection attacks.
ms.date: 03/19/2026
ms.service: security
ms.subservice: zero-trust
ms.topic: conceptual
ms.collection:
  - highpri
  - zerotrust
  - sfi-zerotrust
---


# Defend against indirect prompt injection attacks

**Pillar name: Monitor and detect threats**<br/>
**Pattern name: Defend against indirect prompt injection attacks**


## Context and problem

Generative AI systems, such as copilots and agentic assistants, are increasingly integrated into enterprise workflows. These systems often process untrusted content from external sources like emails, documents, websites, and plugins. This opens a critical vulnerability: **indirect prompt injection attacks**. In indirect prompt injection, adversaries embed malicious instructions within third-party content, which the AI misinterprets as legitimate commands. This can lead to unauthorized actions, data breaches, and loss of system integrity. The challenge is compounded by the AI’s inability to distinguish between user input and external content, making traditional input validation insufficient.


## Solution

Implement a defense-in-depth strategy that layers multiple probabilistic and deterministic mitigations to reduce the risk and impact of indirect prompt injection. This approach includes:

- **Prompt shields**: Analyze and sanitize incoming prompts to detect injection attempts.
- **Spotlighting**: Use data marking and metaprompting to isolate and neutralize external content within prompts.
- **Plan drift detection**: Monitor multi-step reasoning for deviations from intended task flows.
- **Critic agents**: Audit inputs and outputs in real time, especially in multi-agent systems.
- **Tool chain analysis**: Assess and block risky sequences of tool execution.
- **Security guardrails**: Embed final-layer protections within skills to catch bypassed threats.
- **Information flow control (IFC)**: Enforce policy-based isolation of untrusted content using metadata and quarantined inference environments.
- **Principle of least privilege**: Give agents only the minimal amount of short-lived privileges needed to complete their tasks
- **Short lived privileges:** Give agents privileges only when needed and remove privileges after each use
- **Human-in-the-loop:** The last line of defense against an attack is to verify risky actions with the user


## Guidance

Organizations seeking to adopt this pattern can apply the following actionable practices:

| **Practice category** | **Recommended actions** | **Link for article (how to do it)** |
| --- | --- | --- |
| Assume indirect prompt injection will happen | Design systems with the expectation that some attacks will succeed. | [Secure AI](/azure/cloud-adoption-framework/scenarios/ai/secure) |
| Integrate early<br> | Apply indirect prompt injection risk evaluations during UX design, prompt engineering, and system architecture. | [Secure AI](/azure/cloud-adoption-framework/scenarios/ai/secure) |
| Use multiple layers | No single solution is sufficient—combine probabilistic and deterministic defenses. | [Prompt Shields](https://techcommunity.microsoft.com/blog/azure-ai-services-blog/azure-ai-announces-prompt-shields-for-jailbreak-and-indirect-prompt-injection-at/4099140) and [Spotlighting](https://arxiv.org/html/2403.14720v1) |
| Isolate untrusted content | Use IFC to prevent untrusted data from influencing critical inference or planning.<br> | [Spotlighting research](https://arxiv.org/html/2403.14720v1) |
| Monitor continuously | Implement runtime checks like plan drift detection and critic agents to catch anomalies. | [Monitor generative AI apps](/azure/ai-foundry/how-to/monitor-applications) |
| Tailor to context | Choose mitigations based on the product type, threat vector, and user interaction model. | [Secure AI](/azure/cloud-adoption-framework/scenarios/ai/secure) and [Prompt Injection Mitigation in MCP](https://devblogs.microsoft.com/blog/protecting-against-indirect-injection-attacks-mcp) |


## Outcomes

**Benefits:**

- **Enhanced security posture**: Layered defenses significantly reduce the likelihood of successful indirect prompt injection exploits by catching attacks at multiple stages.
- **Increased trust and adoption**: Users and stakeholders are more likely to adopt AI systems that demonstrate robust, transparent security practices.
- **Resilience to evolving threats**: The modular nature of the defense stack allows for rapid adaptation to new attack vectors and adversarial techniques.
- **Containment of impact**: Even if an attack bypasses one-layer, downstream mitigations limit the scope and damage of the exploit.
- **Improved compliance and governance**: Structured defenses support regulatory requirements for data protection and responsible AI use.
- **Operational continuity**: Systems remain functional and safe even under adversarial conditions, reducing downtime and incident response costs.

**Trade-offs:**

- **Increased complexity**: Implementing and maintaining multiple layers of defense requires coordination across engineering, security, and product teams.
- **Performance overhead**: Some mitigations, such as runtime monitoring or quarantined inference, may introduce latency or computational cost.
- **False positives**: Probabilistic defenses like prompt shields or plan drift detection may occasionally block legitimate actions, impacting user experience.
- **Resource investment**: Developing, testing, and tuning layered defenses demands ongoing investment in tooling, expertise, and infrastructure.
- **Customization required**: There is no universal solution, each system must be evaluated to determine the appropriate combination of defenses.

## Key success factors:

- **Defense-in-depth mindset is adopted:** Rely on multiple, layered defenses—both probabilistic and deterministic—to ensure system resilience in the face of failures.
- **Risk evaluation is integrated early:** Embed indirect prompt injection threat modeling and risk assessments into the UX design, prompt engineering, and system architecture phases, rather than adding them after the fact.
- **Design with indirect prompt injection:** Design with the expectation that prompt injection attacks are inevitable, enabling proactive containment and recovery strategies.
- **Untrusted content is isolated:** Leverage techniques such as Information Flow Control (IFC), spotlighting, and datamarking to prevent untrusted data from influencing critical inference or system processes.
- **Continuous monitoring****: **Employ runtime monitoring tools—such as plan drift detection and critic agents—to detect and respond to abnormal behaviors in real time.
- **Defenses tailored to context:** Adapt mitigation measures to fit the specific application, threat landscape, user interaction patterns, and deployment environment.
- **Leverage community and research:** Collaborate with internal and external security experts, research institutions, and partner ecosystems to identify emerging threats and refine defenses.
- **Use policy-based controls:** Implement guidelines and controls like Prompt Shields and IFC to enforce strong boundaries on model behavior and prevent unauthorized actions.

## Summary

Indirect prompt injection Attacks pose a significant threat to generative AI systems by exploiting their reliance on untrusted content. A Defense-in-Depth approach—combining prompt sanitization, content isolation, behavioral monitoring, and policy enforcement—provides a robust framework for mitigating these risks. By assuming indirect prompt injection is inevitable and designing systems to contain and respond to it, organizations can protect the integrity, privacy, and trustworthiness of their AI-powered solutions.




## Additional resources**


- [OWASP Top Ten Vulnerabilities for LLMs](https://genai.owasp.org/llmrisk/llm01-prompt-injection/)
<br>Learn about all the ways that LLMs are currently vulnerabile to maliscious attacks

- [Microsoft Defender Prompt Shields](/azure/ai-services/content-safety/concepts/jailbreak-detection)
<br>Find out how Microsoft is defending against indirect prompt injection attacks in Microsoft Defender using Prompt Shields