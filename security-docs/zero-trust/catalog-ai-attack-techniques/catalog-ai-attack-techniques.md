---
title: Catalog of AI Attack Techniques for Enterprise Security
description: Introduces a catalog of fourteen AI attack techniques across five macro families, with controls, technologies, and OWASP/MITRE mappings for security teams.
ms.date: 7/28/2026
ms.custom:   msecd-doc-authoring-1012
ms.topic: concept-article
ms.service: security
ms.subservice: zero-trust
ms.author: ridive
author: richarddiver-ms
---

# Catalog of AI Attack Techniques (CAAT)
As artificial intelligence is rapidly integrated into enterprise environments, organizations face a new set of complex risks that span technical vulnerabilities, human factors, and procedural weaknesses. This guide provides a comprehensive overview of the evolving AI threat landscape, detailing fourteen distinct attack techniques including prompt manipulation, data poisoning, insecure plugin design, supply chain vulnerabilities, excessive agent autonomy, and more.

Each scenario is accompanied by actionable controls, relevant technologies, and clear OWASP/MITRE mappings to support effective risk mitigation.

The 14 techniques can be grouped into 5 macro technique families:

- **Instruction Manipulation**    Attacks that manipulate prompts, instructions, context, or model-facing content

- **State and Memory Manipulation**    Attacks that corrupt training data, grounding data, embeddings, memory, or persistent context

- **Trust and Supply Chain Abuse**    Attacks that exploit trusted agents, tools, plugins, dependencies, or insiders

- **Execution and Autonomy Abuse**    Attacks that misuse tools, permissions, autonomous actions, or execution paths

- **Resource and Extraction Abuse**    Attacks that abuse model access, compute, APIs, or outputs to extract value or exhaust resources

Almost every attack maps to one of three control failures:

- **No trust boundary on input**

- **No integrity on data**

- **No containment on execution**

## How to use this guide

The content is organized for quick navigation. Each section introduces a specific attack scenario, explains what happens and why it succeeds, and identifies the security controls needed to reduce risk. The sections that follow provide executive-level summaries with real-world examples, required controls, and relevant technologies.

Together, these scenarios form a structured taxonomy of enterprise AI attack techniques, related business risks, and recommended mitigations.


**Intended Audience:** This guide is intended for CISOs, security architects, IT managers, AI developers, and risk professionals responsible for protecting enterprise systems. It also supports executives who need a practical view of AI security and operational teams implementing defensive controls.

**Key Lessons and Takeaways:** Readers will learn how to recognize AI-specific risks, apply layered mitigations, and strengthen collaboration across IT, security, and AI development teams. The guide emphasizes proactive risk management as the foundation for safe AI adoption, helping organizations move beyond traditional cybersecurity practices toward controls designed for the evolving AI threat landscape.

## Attack scenarios

- [1. Rug-Pull Attack (Agent / MCP Server)](rug-pull-attack.md)
- [2. Prompt Injection (Direct / Indirect)](prompt-injection.md)
- [3. Insecure Output Handling (Developer)](insecure-output-handling.md)
- [4. AI Memory / Context Poisoning (Corruption)](ai-memory-context-poisoning.md)
- [5. Unbounded AI Consumption and Agentic DoS (DoS / Wallet Attack)](unbounded-ai-consumption-and-agentic-dos.md)
- [6. Supply Chain Vulnerabilities (OSS)](supply-chain-vulnerabilities.md)
- [7. Sensitive Information Disclosure (Data Leak)](sensitive-information-disclosure.md)
- [8. Insecure Plugin Design (Tools/Plugins)](insecure-plugin-design.md)
- [9. Excessive Agency (Agents)](excessive-agency.md)
- [10. Overreliance on AI (Misuse & Human Factor)](overreliance-on-ai.md)
- [11. Model Theft (IP Theft)](model-theft.md)
- [12. Unmanaged Agent Sprawl & Collusion (Agents)](unmanaged-agent-sprawl.md)
- [13. Training Data Poisoning (Model backdoor)](training-data-poisoning.md)
- [14. Grounding Data Compromise (Retrieval Layer)](grounding-data-compromise.md)

