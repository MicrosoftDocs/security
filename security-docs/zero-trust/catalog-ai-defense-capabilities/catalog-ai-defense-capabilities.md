---
title: AI Defense Capabilities for Enterprise AI Security
description: A framework-aligned guide to the defensive capabilities enterprises need to mitigate AI attack techniques and adopt AI securely
ms.date: 7/28/2026
ms.custom:   msecd-doc-authoring-1012
ms.topic: concept-article
ms.service: security
ms.subservice: zero-trust
ms.author: ridive
author: richarddiver-ms
---

# AI Defense Capabilities for Enterprise AI Security
Where the [Catalog of AI Attack Techniques](https://aka.ms/CAAT) sets out how enterprise AI systems are attacked, this companion sets out how they are defended. The defensive capabilities here are derived from the catalog’s scenario controls, technology references, and defensive mitigations, then normalized against [MITRE ATLAS](https://atlas.mitre.org), the [OWASP Top 10 for LLM Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/) (2025), and the [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) and Generative AI Profile.

The result is a single, framework-aligned view of the defensive capabilities an enterprise needs to adopt AI safely — grouped into the simplest set of families that still covers the full attack surface. It is intended for the same audience as the attack catalog: CISOs, security architects, IT managers, AI developers, and risk professionals.

This companion is organized as a defensive-control view of the attack catalog rather than as a one-for-one retelling of each attack technique. Readers should use the Catalog of AI Attack Techniques to identify the relevant attack path, then use this document to identify the control family, technology choices, and framework mappings that reduce risk across that path.

For prioritization, start with controls that constrain blast radius across many attack paths: identity and least privilege for users, agents, and tools; input and retrieval hygiene for anything the model reads; runtime containment for anything the model can do; and monitoring that preserves prompt, context, tool-call, and output evidence for investigation.

Security architecture should own the control framework, product engineering should own implementation in AI systems, security operations should own detection and response, and governance or risk teams should own policy, inventory, and assurance. The same capability may therefore require multiple owners, with accountability split between design-time control and run-time operation.

## Summary

The Catalog of AI Attack Techniques cluster around three recurring control failures: weak trust boundaries on input, weak integrity guarantees for data and models, and weak containment of execution. The defensive capabilities are the inverse — each capability strengthens one or more of three control objectives:

- **Establish a trust boundary on input** — nothing the model reads is trusted by default.

- **Enforce integrity on data and models** — provenance, signing, and verification across the lifecycle.

- **Impose containment on execution** — least privilege, isolation, and limits on what AI can do.

These objectives resolve into nine capability families. They mirror the nine mitigation types already identified in the attack catalog, now consolidated and cross-referenced:

| **Capability family** | **What it secures** |
|----|----|
| **1. Govern, Assure, and Respond** | Policy, threat modeling, human oversight, red-teaming, incident response |
| **2. Supply-chain and Provenance** | Models, datasets, libraries, plugins, and agents from upstream tampering |
| **3. Identity, Access, and Least Privilege** | Verified identity and minimum rights for every user, agent, and tool |
| **4. Input, Context, and Retrieval Hygiene** | Prompts, documents, retrieval, and memory treated as untrusted |
| **5. Model Hardening and Alignment** | Behavioral robustness of the model against jailbreaks and backdoors |
| **6. Runtime Isolation and Sandboxing** | What the AI and its tools can do at execution time |
| **7. Output Safety and Downstream Handling** | The model’s output as untrusted input to the next system |
| **8. Monitoring, Detection, and Forensics** | Visibility, anomaly detection, and traceability across the stack |
| **9. Resource Governance and Abuse Prevention** | Availability and budget against denial-of-service and wallet attacks |

## Table of contents

- [1. Govern, Assure, and Respond](govern-assure-respond.md)
- [2. Supply-chain and Provenance](supply-chain-provenance.md)
- [3. Identity, Access, and Least Privilege](identity-access-least-privilege.md)
- [4. Input, Context, and Retrieval Hygiene](input-context-retrieval-hygiene.md)
- [5. Model Hardening and Alignment](model-hardening-alignment.md)
- [6. Runtime Isolation and Sandboxing](runtime-isolation-sandboxing.md)
- [7. Output Safety and Downstream Handling](output-safety-downstream-handling.md)
- [8. Monitoring, Detection, and Forensics](monitoring-detection-forensics.md)
- [9. Resource Governance and Abuse Prevention](resource-governance-abuse-prevention.md)
