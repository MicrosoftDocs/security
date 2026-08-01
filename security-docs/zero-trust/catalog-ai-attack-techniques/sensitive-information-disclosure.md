---
title: 7. Sensitive Information Disclosure (Data Leak)
description: Explains how AI memory, context, and retrieval artifacts can leak sensitive operational data, and the access and retention controls needed to prevent it.
ms.date: 7/28/2026
ms.custom:   msecd-doc-authoring-1012
ms.topic: concept-article
ms.service: security
ms.subservice: zero-trust
ms.author: ridive
author: richarddiver-ms
---

# 7. Sensitive information disclosure (data leak)

Real-world AI data exposure increasingly comes from **memory, context, and retrieval artifacts** rather than from eliciting memorized training data. Enterprise assistants can retain user preferences, working summaries, retrieved snippets, tool outputs, vector-store entries, agent scratchpads, logs, or cached grounding data. If you scope these artifacts incorrectly, persist them longer than intended, or later surface them to the wrong user, the system can leak sensitive operational context even though the base model was never trained on it.

For example, an internal assistant might remember details from a prior workflow, summarize an agent’s intermediate reasoning, expose retrieved document fragments, or reveal tool-output metadata that should have remained confined to a session, user, task, or agent. In multi-agent environments, shared memory and retrieval stores can amplify this risk by allowing one compromised or overprivileged agent to surface another agent’s state.

Training-data memorization remains a valid concern, but for enterprise systems the more common and actionable risk is leakage from **persistent memory and context plumbing**: conversation histories, RAG indexes, cached embeddings, prompt traces, connector outputs, and orchestration telemetry. These examples lead many enterprises to treat AI memory and retrieval layers as sensitive data stores that require the same access control, retention, auditing, and DLP protections as traditional applications.

## What happens in this scenario
In this scenario, an AI system **exposes confidential information** that should be kept private. This exposure can happen in two main ways:

1.  **The AI system reveals secrets from memory or context artifacts**. Modern AI systems might persist user preferences, working context, retrieved documents, vector-store entries, conversation summaries, agent scratchpads, tool outputs, or cached grounding data. Later, if prompted or manipulated in the right way, the system might expose those artifacts even though the underlying model wasn't trained on them. For example, an internal assistant might summarize prior agent state, disclose retrieved document snippets, or reveal cached operational details that were meant to remain scoped to a prior session or workflow.

1.  **Users (or insiders) inadvertently leak data via the AI**. In a "user-induced" scenario, an employee inputs confidential information into a public or third-party AI service (like ChatGPT) without realizing that data could be seen by the service provider or used to train models. This action effectively hands your secrets to an external party. Moreover, if there's a vulnerability or misconfiguration, that data might become visible to other users, compounding the leak. In both cases, the core issue is that sensitive information, which should remain internal, **ends up in places it shouldn't** – either coming out in model responses or being stored on external systems.

## Why this technique is effective
Unlike traditional software, LLMs don't have hard-coded rules for what not to say – they rely on their training, instructions, retrieval context, and available memory. If sensitive data is present in persistent memory, conversation history, retrieved context, vector stores, tool outputs, or agent state, the system might treat it as usable context unless access controls and disclosure rules prevent that.

Attackers or curious users can exploit this vulnerability by probing for session summaries, retrieved context, cached tool outputs, or remembered preferences that shouldn't be visible in the current interaction. For example:

- An adversary might input a partial piece of a known secret (like "BEGIN PRIVATE KEY") to coax the model into completing it.

- Additionally, from an insider threat perspective, AI tools can feel "safe" or "intelligent," leading employees to let their guard down. The convenience of an AI assistant might cause someone to paste a code snippet containing passwords or customer data into a prompt, not realizing that the data is stored externally.

- If that AI's platform has a breach or bug, the data can leak to unauthorized parties.

> Ultimately, these disclosure scenarios underscore how the *blurring of trust boundaries* (AI models straddle internal and external data) makes it easier for confidential info to slip through the cracks.

## Recommended controls
- **Minimize sensitive memory artifacts**: Wherever possible, avoid storing confidential information in persistent memory, conversation summaries, vector stores, agent scratchpads, logs, or grounding caches. Prefer short-lived session context, scoped retrieval, masking, and synthetic or redacted data. If memory is required, store only the minimum fields needed, apply retention limits, and separate sensitive operational state from user-visible memory.

- **Isolation of memory, retrieval, and conversation contexts**: Architect systems so that each user, session, task, agent, and retrieval scope has a separate context boundary. Prevent one user or agent from reading another’s memory artifacts, summaries, tool traces, or cached grounding data, or vector-store entries unless explicitly authorized. If system prompts, tool credentials, retrieved documents, and/or agent state contain sensitive information, keep them outside model-visible context whenever possible, and enforce policy checks before any memory or retrieved content is surfaced.

- **Strict data handling policies for users**: Establish clear policies and training urging employees not to input sensitive information into unapproved AI tools. Treat prompts as equivalent to sending data to an external service (because in many cases it is). Provide a company-sanctioned secure AI platform where data retention and privacy are controlled.

- **Prompt, output, and memory-write scanning**: Integrate Data Loss Prevention (DLP) and content-classification tools across the full AI data path: user prompts, generated outputs, memory writes, retrieved context, vector-store ingestion, logs, and tool outputs. If an employee attempts to paste customer records, source code, credentials, or regulated data into a prompt or memory-enabled workflow, the system should block, redact, or require approval. Similarly, scan AI responses and memory reads before they are shown to users or sent to downstream tools.

- **Use approved private AI instances for sensitive workflows**: For sensitive tasks, use enterprise AI services where data retention, tenant isolation, logging, and privacy commitments are controlled. Memory-enabled systems should run only in approved environments where prompts, retrieved data, memory artifacts, and tool outputs are not used to train base models and are governed by enterprise access, retention, and audit policies.

## Technologies to consider
- **Microsoft Purview and DLP solutions**: Use Purview classification, sensitivity labels, retention, audit, and DLP policies to govern prompts, outputs, retrieved content, memory writes, vector stores, logs, and tool outputs. Apply policies before sensitive data is persisted into AI memory or surfaced from memory to users or agents.

- **Azure OpenAI and approved enterprise AI services**: Prefer approved enterprise deployments for sensitive workflows so prompts, outputs, grounding data, and memory artifacts remain governed by tenant controls and are not used to train base models.

- **Identity and access control for memory stores**: Use Microsoft Entra ID, managed identities, scoped service principals, and least-privilege RBAC to control who or what can read, write, update, or delete AI memory, retrieval indexes, caches, and agent state.

- **Prompt, response, and memory auditing**: Send AI interaction logs, memory-write events, retrieval events, and tool-output metadata to Microsoft Sentinel or equivalent monitoring tools. Alert on suspicious memory reads, repeated extraction attempts, cross-user context access, or outputs containing sensitive markers.

- **Secure proxy, redaction, and tokenization layers**: Where external or semi-trusted AI services are unavoidable, route prompts and outputs through a proxy that redacts, tokenizes, or encrypts sensitive fields before model processing, then reinserts authorized values only after policy checks.

## OWASP Top 10 mapping
[OWASP Top 10 for LLM and Generative AI](https://genai.owasp.org/llm-top-10/) (2025)

This scenario maps to **LLM02: Sensitive Information Disclosure**, where the model unintentionally reveals confidential, internal, or private data through its responses, and **LLM08: Vector and Embedding Weaknesses**, since improperly protected embeddings, retrieval systems, or vector stores can expose sensitive information during lookup or reconstruction.

## MITRE ATLAS mapping
This scenario broadly maps to MITRE ATLAS behaviors around sensitive information disclosure, model inversion, and extraction through prompts or outputs.

**[MITRE ATLAS Techniques](https://atlas.mitre.org/techniques) (Attack):**
The attack primarily reflects sensitive information disclosure: bad actors or users cause the model to reveal confidential data, memorized content, internal prompts, or protected information.
* AML.T0024 Exfiltration via AI Inference API (.000 Infer Training Data Membership, .001 Invert AI Model)
* AML.T0025 Exfiltration via Cyber Means
* AML.T0056 Extract LLM System Prompt
* AML.T0057 LLM Data Leakage

**[MITRE ATLAS Mitigations](https://atlas.mitre.org/mitigations) (Defense):**
Prioritize data minimization, access control, output filtering, redaction, model hardening, honey tokens, and extraction monitoring.
* AML.M0000 Limit Public Release of Information
* AML.M0002 Passive AI Output Obfuscation
* AML.M0004 Restrict Number of AI Model Queries
* AML.M0005 Control Access to AI Models & Data at Rest
* AML.M0020 Generative AI Guardrails
