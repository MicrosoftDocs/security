---
title: 13. Training Data Poisoning (Model backdoor)
description: Describes how adversaries can inject malicious or biased examples into model training data to create backdoors, and the controls needed to secure the pipeline.
ms.date: 7/28/2026
ms.custom:   msecd-doc-authoring-1012
ms.topic: concept-article
ms.service: security
ms.subservice: zero-trust
ms.author: ridive
author: richarddiver-ms
---

# 13. Training Data Poisoning (Model backdoor)

In 2023, Mithril Security showed how an open-source LLM on Hugging Face could be **poisoned to misbehave on a specific query** while appearing normal otherwise. They modified the model’s training data so that when asked about a particular topic, it would give a pre-planted incorrect answer favoring a certain point of view. This backdoored model was uploaded publicly – if an enterprise unknowingly incorporated it, the poisoning could have led to misinformation in an otherwise trusted AI system.

Earlier, Microsoft’s Tay chatbot (2016) infamously learned from Twitter users in real-time; malicious users flooded it with toxic tweets, effectively “poisoning” its learning data and causing Tay to output racist and inappropriate messages within hours. These incidents illustrate how unsuspected training data can undermine an AI: whether through malicious datasets or interactive learning, **“garbage (or poison) in, poison out.”**

## What happens in this scenario
This is not a novel style of attack so much as a supply chain attack against the data used to train or fine-tune an AI model. In a *training data poisoning* scenario, an adversary **manipulates the model training or fine-tuning data supply chain**, injecting malicious, misleading, or biased examples into a dataset before the model learns from it. In enterprise settings, this could occur if:

1.  An attacker has access to the AI’s training pipeline or contributes data to it (e.g. poisoning a shared dataset or third-party data feed the model learns from).

2.  The poisoned data might be very subtle – for example, modifying some records so that a sensitive phrase always correlates with incorrect or attacker-chosen outputs.

3.  During model training, the AI unknowingly learns these tampered correlations or behaviors.

4.  Later, when the model is deployed, it will exhibit compromised behavior: perhaps it will consistently favor a certain incorrect answer, have an embedded bias or backdoor trigger, or crash on certain inputs.

5.  In effect, the attacker has **planted a hidden trigger in the model’s knowledge base**, which can be triggered under specific conditions.

## Why this technique is effective
Modern AI models are **hungry for data** – they often learn from vast and diverse datasets, including user-generated content or data aggregated from many sources. This makes it difficult to perfectly vet all training data. Attackers can leverage this complexity to insert *undetected malicious patterns*:

- During **initial training**, if the dataset is scraped from the internet or gathered from third parties, an attacker might inject false but plausible data (e.g., subtly altered facts on a public website or poison samples on a code repository). The model then “learns” the attacker’s input as if it were truth.

- During **fine-tuning** or updates, an insider or malicious contributor could insert crafted examples that skew the model’s outputs in specific ways (for example, always outputting a particular phrase when a trigger word appears). This technique is effective because once the model is trained on poisoned data, the malicious influence is deeply embedded and **hard to detect** – the model’s output might look reasonable in most cases, only revealing the attack under certain conditions. Additionally, organizations may not realize an error is due to poisoning; the AI’s mistakes could be attributed to normal model imperfection rather than a deliberate attack.

## Recommended controls
- **Secure AI memory and related data stores:** Treat persistent memory, conversation summaries, vector stores, agent scratchpads, runtime logs, tool outputs, and grounding caches as sensitive data stores. Avoid persisting confidential information unless there is a clear business need, and prefer short-lived session context, scoped retrieval, masking, synthetic data, or redacted data. If memory is required, store only the minimum fields needed, apply retention limits, classify the memory artifact, and separate sensitive operational state from user-visible memory.

- **Minimize sensitive memory artifacts:** Wherever possible, avoid storing confidential information in persistent memory, conversation summaries, vector stores, agent scratchpads, logs, or grounding caches. Prefer short-lived session context, scoped retrieval, masking, and synthetic or redacted data. If memory is required, store only the minimum fields needed, apply retention limits, and separate sensitive operational state from user-visible memory.

- **Isolation of memory, retrieval, and conversation contexts:** Architect systems so that each user, session, task, agent, and retrieval scope has a separate context boundary. Prevent one user or agent from reading another’s memory artifacts, summaries, tool traces, or cached grounding data, or vector-store entries unless explicitly authorized. If system prompts, tool credentials, retrieved documents, and/or agent state contain sensitive information, keep them outside model-visible context whenever possible, and enforce policy checks before any memory or retrieved content is surfaced.

- **Strict data handling policies for users:** Establish clear policies and training urging employees not to input sensitive information into unapproved AI tools. Treat prompts as equivalent to sending data to an external service (because in many cases it is). Provide a company-sanctioned secure AI platform where data retention and privacy are controlled.

- **Prompt, output, and memory-write scanning:** Integrate Data Loss Prevention (DLP) and content-classification tools across the full AI data path: user prompts, generated outputs, memory writes, retrieved context, vector-store ingestion, logs, and tool outputs. If an employee attempts to paste customer records, source code, credentials, or regulated data into a prompt or memory-enabled workflow, the system should block, redact, or require approval. Similarly, scan AI responses and memory reads before they are shown to users or sent to downstream tools.

- **Use approved private AI instances for sensitive workflows:** For sensitive tasks, use enterprise AI services where data retention, tenant isolation, logging, and privacy commitments are controlled. Memory-enabled systems should run only in approved environments where prompts, retrieved data, memory artifacts, and tool outputs are not used to train base models and are governed by enterprise access, retention, and audit policies.

- **Limit external contributions:** If your AI training involves user-generated content (forums, wikis, etc.), implement moderation steps. For critical training data, restrict who can edit or contribute and use anomaly detection to flag unusual edits or content that could be malicious.

- **Data validation and cleaning:** Use automated tools to scan training data for anomalies – e.g., sudden appearance of particular phrases, code, or metadata that could indicate poisoning. Remove or review outliers. In structured datasets, validate that distributions of values haven’t been skewed unexpectedly.

- **Robust training techniques:** Research defensive training methods (like differentially private training or adversarial training) that make models less sensitive to outliers or single data sources. Some techniques can limit memorization of specific data points, reducing the impact of poisoned examples.

- **Re-evaluate and test the model:** Perform extensive testing on the trained model to detect if it has odd behaviors. This includes **red-team evaluation:** have internal experts attempt to discover backdoors or triggers in the model (for example, seeing if certain inputs consistently produce abnormal outputs).


## Technologies to consider
- **Data provenance and cataloging tools**: Use data governance solutions (e.g., **Microsoft Purview** or **Collibra**) to maintain an inventory of all data used for AI training, along with lineage. This helps in quickly identifying if unapproved data made it into the training pipeline.

- **Secure MLOps pipelines**: Leverage MLOps platforms (like **Azure Machine Learning**) that integrate data version control and require reviews/approvals for changes in training datasets or model parameters. Just as code pipelines have checks (tests, code scanning), apply similar gates for training data (e.g., scanning data for malicious content or biases).

- **Model anomaly detection**: Utilize tools that can analyze trained models for signs of poisoning or unexpected behaviors. Research in ML security has produced methods to detect backdoors, such as checking model responses across a wide range of inputs for out-of-character patterns. Some emerging security scanners can flag anomalies in model outputs.

- **Access control for training**: Strictly limit who can initiate training jobs or modify training data. Use logging and alerts on any changes in key datasets. Consider “four-eyes” principles (two-person approval) for changes to high-stakes training data.

## OWASP Top 10 mapping
[OWASP Top 10 for LLM and Generative AI](https://genai.owasp.org/llm-top-10/) (2025)

This scenario maps to **LLM04: Data and Model Poisoning**, where attackers intentionally plant malicious examples or backdoor triggers in the training corpus to influence model behavior at inference time. It also ties into **LLM03: Supply Chain**, as poisoned or manipulated data is often introduced through compromised pipelines, external datasets, or third-party contributors. If poisoned data later affects retrieval stores, embeddings, or grounding sources used by the deployed system, the scenario can also intersect with **LLM08: Vector and Embedding Weaknesses**.

## MITRE ATLAS mapping
This scenario maps broadly to MITRE ATLAS behaviors around data and model poisoning, backdoor triggers, and model artifact manipulation. 

**[MITRE ATLAS Techniques](https://atlas.mitre.org/techniques) (Attack):**
The attack primarily reflects data and model poisoning: adversaries manipulate training or fine-tuning data, model weights, or trigger patterns so the model behaves incorrectly under specific conditions.
- AML.T0010.002 AI Supply Chain Compromise: Data 
- AML.T0018 Manipulate AI Model (.000 Poison AI Model)
- AML.T0020 Poison Training Data
- AML.T0031 Erode AI Model Integrity

**[MITRE ATLAS Mitigations](https://atlas.mitre.org/mitigations) (Defense):**
Prioritize training data hygiene, artifact provenance, backdoor testing, model inspection, and secure MLOps governance.
- AML.M0005 Control Access to AI Models & Data at Rest
- AML.M0007 Sanitize Training Data
- AML.M0008 Validate AI Model
- AML.M0014 Verify AI Artifacts
