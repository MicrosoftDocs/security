---
title: 4. Input, Context, and Retrieval Hygiene
description: Guidance for protecting AI systems from prompt injection, poisoned retrieval content, and memory manipulation by treating all inputs and context as untrusted.
ms.date: 7/28/2026
ms.custom:   msecd-doc-authoring-1012
ms.topic: concept-article
ms.service: security
ms.subservice: zero-trust
ms.author: ridive
author: richarddiver-ms
---

# 4. Input, Context, and Retrieval Hygiene

## What this group defends against

Every prompt, document, retrieved chunk, tool result, and memory write is treated as untrusted input. This group counters direct and indirect prompt injection, memory and context poisoning, poisoned retrieval content, hidden instructions in documents or webpages, and grounding-data compromise in the retrieval layer.

## Core capabilities

Input and retrieval controls establish a trust boundary around everything the model reads. User prompts, attached files, retrieved passages, tool responses, and memory are data—not trusted instructions—and should be inspected, labeled, normalized, and authorized before they influence reasoning or action. Secure retrieval also requires source provenance, permission-aware indexing, and validation at every read and write so compromised content cannot silently become durable context.

- **Detect and sanitize:** apply prompt-attack detection, content filtering, Unicode normalization, hidden-markup removal, and restoration techniques for adversarial perturbations.

- **Separate instructions from data:** preserve message roles and source metadata, segment untrusted content, and extract only schema-valid fields instead of injecting raw content into instruction channels.

- **Secure retrieval and memory:** ingest verified sources, enforce document and vector-store access controls, score trust and freshness, and allow memory reads or writes only through typed, policy-checked interfaces.

- **Make memory recoverable and time-bound:** version memory snapshots and log every write; provide rollback so a poisoning event can be rewound to a known-good state; expire, re-embed, or revalidate entries on a schedule to prevent long-term drift; and retain read and write lineage so a corrupted decision can be traced to the memory that shaped it.

## Which technologies do we use?

Protecting prompts, retrieved content, external sources, and memory requires controls at several points in the data path. The technologies below inspect content for attacks, enforce permission-aware retrieval, screen external channels, test defenses with adversarial inputs, and apply application-layer validation so untrusted data remains separated from authoritative instructions.

- **Microsoft Foundry guardrails and Azure AI Content Safety** — safety services that inspect prompts and model responses. Use configurable content filters for harmful-content categories and Prompt Shields to detect user-prompt attacks and hidden instructions embedded in documents, emails, webpages, or tool responses before they influence the model.

- **Azure AI Search** — an enterprise retrieval service for full-text, vector, semantic, hybrid, and agentic search. For secure RAG, use permission-aware indexes, document-level access control or security trimming, managed identities, metadata filters, relevance controls, and source citations so users and agents retrieve only authorized, traceable content.

- **Microsoft Defender for Cloud Apps and secure web or email gateways** — controls for discovering cloud-app use and inspecting external content channels. Use app discovery, session controls, file and URL analysis, malware detection, reputation checks, and access policies to reduce the chance that untrusted webpages, email, or SaaS content becomes malicious grounding data.

- **AI security scanners and adversarial test harnesses** — a category of tools rather than a single product. They submit representative and adversarial inputs, including prompt-injection, data-exfiltration, encoding, and tool-manipulation tests, then record whether defenses detected, blocked, or safely handled them. Use them in CI/CD and before material prompt, model, retrieval, or tool changes.

- **Sanitization, segmentation, and typed memory controls** — application-layer controls. Normalize Unicode, remove active or hidden markup, distinguish instructions from data, validate extracted fields against schemas, score source trust, enforce access checks on every retrieval, and allow memory writes only through narrow typed interfaces with provenance and safety classification.

## Framework mapping

**[OWASP Top 10 for LLM and Generative AI](https://genai.owasp.org/llm-top-10/) (2025)**: Maps to LLM01 Prompt Injection and LLM08 Vector and Embedding Weaknesses by treating prompts, retrieved content, documents, memory, and tool results as untrusted. Prompt-attack detection, sanitization, source scoring, access controls, and retrieval validation reduce direct and indirect injection and insecure grounding paths.

**[MITRE ATLAS](https://atlas.mitre.org/mitigations)**: Maps to AML.M0010 Input Restoration, AML.M0015 Adversarial Input Detection, and, where model training or adaptation is involved, AML.M0007 Sanitize Training Data. These mitigations address adversarial perturbations and malicious inference inputs; retrieval-source validation, vector-store authorization, and memory-write controls remain complementary application safeguards rather than direct ATLAS mitigation IDs.

**[NIST AI RMF 1.0 and NIST AI 600-1](https://www.nist.gov/itl/ai-risk-management-framework)**: Supports **MAP**, **MEASURE**, and **MANAGE** by documenting input and grounding provenance, testing exposure to prompt and retrieval attacks, separating trusted instructions from external content, and continuously monitoring ingestion and memory paths for poisoning or unauthorized change.
