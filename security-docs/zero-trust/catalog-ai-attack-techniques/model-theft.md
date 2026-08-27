---
title: 11. Model Theft (IP Theft)
description: Describes how attackers can reconstruct or clone proprietary AI models via public APIs, and the safeguards needed to protect model intellectual property.
ms.date: 7/28/2026
ms.custom:   msecd-doc-authoring-1012
ms.topic: concept-article
ms.service: security
ms.subservice: zero-trust
ms.author: ridive
author: richarddiver-ms
---

# 11. Model Theft (IP Theft)

*Academic and industry experiments have validated the feasibility of model theft.* Back in 2016, researchers from Cornell and University of California showed that they could **steal a machine learning model’s functionality via its public API**, reconstructing it with near-identical performance by learning from its outputs.

More recently, in 2023, an incident known as the “**LLaMA leak**” occurred when Meta’s proprietary LLaMA LLM was released to researchers and then **illegally leaked online**, giving anyone free access to a model trained at significant cost. While that was more an internal leak than an external attack, it highlighted how quickly a valuable model can proliferate beyond its intended scope.

Meanwhile, tech companies have raised alarms about competitors potentially using their public AI services to **build copycat models cheaply** – in one case, a small team replicated a popular language model by systematically querying it with millions of prompts and using the responses to train a new model. These examples show that without proper safeguards, *the question answering API you expose today could help thieves build a clone of your model tomorrow*, undercutting your competitive advantage.**\**

## What happens in this scenario
In a *model theft* or *model extraction* attack, an adversary **steals an AI model’s knowledge or capabilities without authorization**. The most common method is through an API: the attacker interacts with the AI (which is exposed via an API or service) and systematically queries it to rebuild a replica model. For example:

1.  Suppose an enterprise has a proprietary LLM accessible through a cloud API for its applications. An attacker with API access (e.g., a malicious insider or someone who obtained an API key) could send a large number of cleverly chosen queries to the model and record its outputs.

2.  Using those input-output pairs, the attacker trains their own model to mimic the behavior of the original. Over time, the attacker’s model gets closer and closer to the fidelity of the target model.

3.  The attacker has now effectively **stolen the intellectual property** – they have a model that reproduces the core functionality without ever having had direct access to the original’s code or weights.

4.  Alternatively, model theft can occur via an insider simply copying the model files (if the model is small enough or stored insecurely), or via improperly secured model repositories (downloading the model from an online storage because it wasn’t protected).

## Why this technique is effective
Companies pour resources into training AI models – the models themselves become valuable IP. Yet if the model is offered as a service (e.g., via an API or even a public-facing chatbot), the only thing between an attacker and that model is the rate at which they can query it. LLMs often provide probabilistic outputs (like token probabilities or confidence scores), and research shows that *these can accelerate model extraction* by providing more information per query.

Even without probabilities, just having unlimited access to query the model can allow attackers to approximate its behavior. Unlike traditional software, you might not know it’s happening – an attacker with a valid API key may appear as just another normal user, slowly siphoning off your model’s “knowledge.”

Additionally, many organizations don’t have strong monitoring on model usage patterns, so thousands of queries might go unnoticed, especially if spread over time or various accounts. Finally, if an insider can directly access model files (e.g., a data scientist leaving the company with a copy of a fine-tuned model), that’s an even quicker path – many models are just files on disk that may not be encrypted at rest unless special care is taken.

## Recommended controls
- **Rate limiting and usage monitoring**: As with the DoS scenario, limit the rate of queries. But specifically, watch for *enumeration patterns*. For example, if one user is making systematically structured queries or an abnormally high volume of queries that cover broad input space, they might be trying to learn the model. Use analytics to spot this (e.g., sudden spikes in query diversity or volume from a single source).

- **Restrict output detail**: Do not expose more internals than necessary. Many model extraction attacks become easier if the API returns *confidence scores or logits* for each answer (which some ML APIs do to aid uncertainty measurement). If not needed, disable or heavily quantize these to reduce information leakage.

- **Watermarking and monitoring outputs**: Research is underway on “watermarking” AI model outputs such that if someone else uses those outputs to train a clone, you could detect it. While maturing, consider simpler analogs: e.g., include unique responses or trackable tokens in your model’s output (that wouldn’t be noticed by normal users but allow you to identify your model’s “ DNA” in another model’s responses).

- **Encrypted model weights**: If you’re deploying models to edge devices or browsers (where attackers could directly obtain them), consider techniques like *secure enclaves* or model encryption. Some AI frameworks support running models inside trusted execution environments so that even if an attacker gets the device, extracting the raw model isn’t straightforward.

- **Legal & contractual protections**: Complement technical controls with legal ones. Ensure API terms of service prohibit automated scraping or reverse engineering. While this won’t stop a determined attacker, it provides a legal avenue for recourse and deters casual attempts. Also, use watermarks or unique response formats that could serve as evidence in legal disputes over stolen models.

## Technologies to consider
- **API management and anomaly detection**: Use your API gateway (e.g., **Azure API Management**) to implement not just rate limits but also monitor for unusual usage patterns (like sequential queries that cover a wide range of inputs unnaturally). Coupling this with **Azure Sentinel** can enable detection of a slow, ongoing model extraction (e.g., multiple accounts all querying the model in a coordinated way).

- **Confidential computing**: Explore **Azure Confidential Compute** or similar offerings to deploy models in secure enclaves. These technologies keep data and model code encrypted in memory, making it significantly harder for an attacker to directly copy model weights even with physical access to hardware.

- **Federated learning or split knowledge training**: If feasible, keep parts of the model’s knowledge on-premises. For example, a hybrid approach where a cloud LLM handles general language tasks but calls an internal model for proprietary data decisions can ensure the core IP never leaves your environment.

- **Monitoring for clones**: Use services that scan the internet for models or outputs similar to yours. For instance, some companies use **ML model fingerprinting** and periodically check public model repositories or known competitor products for similarities that could indicate stolen parameters.

## OWASP Top 10 mapping
[OWASP Top 10 for LLM and Generative AI](https://genai.owasp.org/llm-top-10/) (2025)

OWASP’s GenAI LLM Top 10 (2025) does not include a dedicated *“Model Theft / IP Theft”* category, so the closest mapping depends on the attacker’s method. If the theft occurs through compromised model artifacts, registries, CI/CD pipelines, or third‑party delivery paths—such as stolen weights, leaked checkpoints, or an exfiltrated fine‑tuned model package—it aligns most directly with **LLM03: Supply Chain & Dependency Risk**.\
\
If the theft is performed through large‑scale, systematic querying of a hosted model to approximate or reconstruct its behavior (**model extraction**), it maps to **LLM10: Unbounded Consumption**, since the attacker relies on high‑volume, high‑cost inference to collect enough input/output pairs to replicate the model. In both cases, it can also intersect with **LLM02: Sensitive Information Disclosure** if proprietary model files, internal prompts, training artifacts, or other confidential assets are exposed rather than merely inferred.

## MITRE ATLAS mapping
This scenario maps broadly to MITRE ATLAS behaviors around model extraction, inference abuse, supply-chain theft, and credential-enabled access to model assets. 

**[MITRE ATLAS Techniques](https://atlas.mitre.org/techniques) (Attack):**
The attack primarily reflects model extraction or artifact theft: adversaries either query a model at scale to approximate its behavior or exfiltrate model weights, checkpoints, or deployment packages.
* AML.T0010.003 AI Supply Chain Compromise: Model
* AML.T0024.002 Extract AI Model
* AML.T0025 Exfiltration via Cyber Means
* AML.T0035 AI Artifact Collection
* AML.T0040 AI Model Inference API Access
* AML.T0044 Full AI Model Access
* AML.T0055 Unsecured Credentials

**[MITRE ATLAS Mitigations](https://atlas.mitre.org/mitigations) (Defense):**
Prioritize query throttling, API authentication, output watermarking, model asset encryption, CI/CD hardening, and lineage tracking.
* AML.M0002 Passive AI Output Obfuscation
* AML.M0004 Restrict Number of AI Model Queries
* AML.M0005 Control Access to AI Models & Data at Rest
* AML.M0012 Encrypt Sensitive Information
* AML.M0024 AI Telemetry Logging
