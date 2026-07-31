---
title: 9. Resource Governance and Abuse Prevention
description: Explains how to prevent AI service disruption, runaway consumption, and unexpected costs through resource and budget controls
ms.date: 7/28/2026
ms.custom:   msecd-doc-authoring-1012
ms.topic: concept-article
ms.service: security
ms.subservice: zero-trust
ms.author: ridive
author: richarddiver-ms
---

# 9. Resource Governance and Abuse Prevention

## What this group defends against

Availability and budget. Counters model denial-of-service and wallet attacks, runaway agent loops, and resource exhaustion from pathological prompts or high concurrency.

## Core capabilities

Resource governance keeps AI workloads available and financially bounded when demand is malicious, accidental, or amplified by autonomous behavior. Controls should limit consumption before work reaches expensive models or tools, constrain each task while it runs, and degrade service predictably as capacity or budget thresholds are reached. Monitoring and cost signals must be tied to automated or human response so scaling does not simply magnify a denial-of-service or wallet attack.

- **Limit requests and consumption:** enforce identity-aware rate limits, quotas, concurrency limits, input and output size caps, token ceilings, and per-task cost thresholds.

- **Bound autonomous execution:** cap steps, recursion depth, spawned agents, tool calls, elapsed time, retries, and total spend; provide cancellation and idempotent recovery.

- **Protect service and budget:** combine bounded autoscale with queues, backpressure, load shedding, circuit breakers, graceful degradation, budget alerts, anomaly detection, and controlled shutdown procedures.

## Which technologies do we use?

Resource governance combines gateway enforcement, operational telemetry, cost controls, and bounded application behavior. The technologies below limit requests and tokens before expensive work begins, detect saturation and anomalous consumption, scale within controlled boundaries, trigger budget response, and stop autonomous tasks that exceed approved time, complexity, or spend.

- **Azure API Management** — a managed gateway for publishing, securing, and governing APIs. Use per-subscription or per-key rate limits, renewable or lifetime quotas, concurrency limits, large-language-model token limits, request-size validation, identity validation, caching, and 429 responses with retry guidance to contain bursts, enumeration, and wallet attacks.

- **Azure Monitor and Azure resource autoscale** — observability and scaling capabilities for measuring demand and changing capacity. Use alerts on latency, saturation, errors, queue depth, token consumption, and throttling; configure bounded autoscale; and combine it with load shedding, backpressure, health probes, and circuit breakers so scaling does not simply amplify malicious or wasteful work.

- **Microsoft Cost Management** — Azure tools for analyzing, forecasting, allocating, and governing cloud spend. Use scoped budgets, threshold alerts, anomaly detection, tags, cost exports, and chargeback views to identify unexpected AI consumption early; connect alerts to operational playbooks that throttle, disable, or require approval for expensive workloads.

- **Foundry Control Plane cost and token oversight** — fleet-level views of agent, model, and tool consumption. Use token-usage, cost-efficiency, run-completion, and prohibited-behavior indicators to find workloads that are looping, overusing tools, or operating outside expected budgets across projects.

- **Bounded execution and graceful degradation** — application and architecture controls rather than a product. Cap prompt and response size, steps, recursion depth, spawned agents, tool calls, wall-clock time, and spend per task; use idempotency, cancellation, queues, bulkheads, circuit breakers, and cheaper fallback models so anomalous work stops predictably.

## Framework mapping

**[OWASP Top 10 for LLM and Generative AI](https://genai.owasp.org/llm-top-10/) (2025)**: Maps directly to LLM10 Unbounded Consumption by limiting token use, query volume, recursion, spawned agents, concurrency, and cost exposure. These controls also reduce the impact of excessive agency when autonomous work would otherwise amplify an error or attack.

**[MITRE ATLAS](https://atlas.mitre.org/mitigations)**: Maps directly to AML.M0004 Restrict Number of AI Model Queries. Per-principal quotas, token and cost ceilings, bounded execution, load shedding, circuit breakers, and graceful degradation are complementary controls for denial-of-service, wallet attacks, enumeration, and runaway multi-agent behavior.

**[NIST AI RMF 1.0 and NIST AI 600-1](https://www.nist.gov/itl/ai-risk-management-framework)**: Supports **MEASURE** and **MANAGE** by tracking usage, latency, cost, throttling, and saturation and by enforcing resilience, availability, financial guardrails, and operational response thresholds.

