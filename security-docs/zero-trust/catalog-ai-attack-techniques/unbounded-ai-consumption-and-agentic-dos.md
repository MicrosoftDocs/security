---
title: 5. Unbounded AI Consumption and Agentic DoS (DoS / Wallet Attack)
description: Describes how crafted prompts or runaway autonomous agents can exhaust compute, cost, or availability, and the safeguards needed to bound AI resource consumption.
ms.date: 7/28/2026
ms.custom:   msecd-doc-authoring-1012
ms.topic: concept-article
ms.service: security
ms.subservice: zero-trust
ms.author: ridive
author: richarddiver-ms
---

# 5. Unbounded AI Consumption and Agentic DoS (DoS / Wallet Attack)

> [!NOTE]
> While full-blown malicious LLM DoS incidents are not widely publicized, clear demonstrations of the risk exist.

Researchers have shown that certain inputs can drastically increase an LLM’s resource usage. One experiment described how a specially crafted prompt on an open-source GPT model forced it into an extremely long, complex task that consumed far more memory and time than normal, effectively slowing the system to a crawl.

Cloud service providers have also noted that unsupervised “rogue” bots or agents can spiral into heavy computation – for example, an early version of an autonomous GPT-4 agent consumed exorbitant API credits by getting stuck in a loop of self-generated tasks, acting like an *accidental DoS* against the service.

On a smaller scale, even innocent users have caused minor outages: in 2023, **high user demand for ChatGPT** (and users prompting it with very long conversations) led to noticeable slowdowns and downtime of the service – illustrating how resource-intensive prompts can impact availability. These scenarios underline that **LLM systems need the same kind of defensive measures as any web service** to prevent abuse via resource exhaustion.

## What happens in this scenario
A *Model Denial of Service* attack involves overwhelming an AI system with inputs or actions that consume disproportionate resources, aiming to degrade its performance or make it unavailable. In the enterprise context, an attacker (or even a careless user) could exploit the heavy computation that LLMs require. For example:

1.  An adversary might send a flood of requests to an internal AI-powered helpdesk bot or intentionally craft **pathological prompts** that cause extremely long or complex outputs:

2.  An attacker finds that a certain query (say, asking the AI to output the entire Bible in JSON format) ties up the system for an extended period; by automating repeated such requests, they exhaust the application’s CPU/GPU resources.

3.  In cloud-based AI services, they could also rack up significant usage costs for the company, or cause the model or agent to repeatedly call downstream APIs, exhaust service endpoints, trigger expensive workflows, flood queues, or overload integrations until those dependent systems experience a denial-of-service effect.

> The result is that legitimate users experience slow responses or downtime, similar to a traditional DDoS attack, but achieved at the application level via AI workload abuse.

## Why this technique is effective
Large AI models are **computationally intensive**, and agentic systems can also multiply load across downstream services. Their inferencing can be slow or costly, especially with long or complex prompts, and a single crafted instruction can cause an agent to call APIs, spawn tasks, or communicate with other agents at machine speed. Attackers can exploit this by sending inputs that maximize computation, trigger excessive tool use, or create runaway agent behavior:

- **Long inputs**: Many LLMs have to process every word of input; very large prompts (perhaps by including lengthy irrelevant text) force the model to spend more time and memory.

- **Pathological prompts**: Certain inputs cause worst-case behavior. For instance, prompts that require the AI to enumerate large outputs (e.g., *“List 1 million prime numbers”*), or triggers for deep, resource-heavy reasoning can spike CPU/GPU usage.

- **High-concurrency**: By automating many parallel queries (through scripts or bots), an attacker amplifies the load on the model beyond its capacity. Since usage-based costs are common in cloud AI (e.g., paying per token), an attacker might not need to fully crash a system to do damage – even causing excessive utilization can burn through budget (a **financial DoS**). The inherent effectiveness comes from the difficulty of distinguishing maliciously “heavy” usage from normal, albeit complex, requests, especially if attackers mix benign queries with heavy ones to fly under monitoring radar.

## Recommended controls
- **Rate limiting and quotas**: Implement strict limits on the number of requests an entity (user, IP, API key, agent identity, or service account) can make per minute and per day. Apply limits both to model calls and to downstream tool/API calls initiated by the model or agent. Use adaptive rate limiting – if requests start spiking, recursively fan out, or deviate from normal patterns, throttle them automatically. Cloud-based AI services should also enforce hard usage limits and per-workload quotas.

- **Validate and truncate inputs**: Set maximum input sizes and use upstream validations. If an input is excessively large (or the resulting output would be extremely long), truncate it or refuse it. Many enterprise AI systems impose a max token limit – configure it according to your needs (e.g., if typical queries are 1,000 tokens, maybe cap at 2,000 tokens to be safe).

- **Chargeback and cost monitoring**: Monitor resource usage through dashboards and alerts (for example, track the number of tokens processed per minute, or %CPU/GPU usage on the AI service). If there’s a sudden surge in utilization beyond expected peaks, generate alerts or automatically scale resources. Use cost control features (like setting spending limits on cloud AI services) to prevent surprise bills.

- **Robust authentication and use of internal systems**: Ensure only authenticated, legitimate users can access the AI (to reduce risk of external attackers launching a flood). Internal enterprise LLM services should be behind authentication and perhaps a VPN or zero-trust network to keep random internet attackers out.

- **Graceful degradation, isolation, and agent containment**: Design the AI service to degrade gracefully under load – e.g., by prioritizing critical requests, using circuit breakers, or temporarily rejecting low-priority tasks when the system is busy. Isolate AI compute resources and downstream service dependencies so an overwhelmed model or agent cannot take down unrelated systems. For Agent DoS, rate-limit agent creation, cap the total number of concurrent agents and subagents, bound recursion depth, throttle and cap inter-agent communication, and place strict limits on fan-out, queue depth, tool calls, and workflow invocations.

## Technologies to consider
- **API Gateways and Throttling**: Use API management tools (such as **Azure API Management**) to enforce rate limits and quotas per client. These can block or slow down clients that send too many requests.

- **Monitoring and auto-scaling**: Implement resource monitoring via **Azure Monitor** or custom dashboards to watch AI CPU/GPU/memory usage. Set up automated scaling rules or load-shedding triggers: for instance, spin up additional instances when load is high, or reject requests that exceed a defined cost threshold.

- **Cloud cost management**: Utilize cloud cost management tools (e.g., Azure Cost Management) to set budgets and alerts for AI service usage. This way, if an attack causes abnormal spending, you get notified or the service is paused.

- **Input pre-processing**: If using structured prompts or function calling, leverage these features (like OpenAI’s function call interface) to constrain the format of prompts – it can prevent an attacker from freely crafting extremely long or deeply nested prompts.

- **Testing for expensive prompts**: Use tools to estimate prompt complexity. For example, measure the token length of inputs and outputs; if an input would obviously generate an enormous output (like asking for a large database dump), block it.

## OWASP Top 10 mapping
[OWASP Top 10 for LLM and Generative AI](https://genai.owasp.org/llm-top-10/) (2025)

This scenario maps to **LLM10: Unbounded Consumption**, where attackers deliberately drive excessive compute usage through token‑intensive prompts, recursive tasks, or runaway agent loops to degrade performance or exhaust service capacity. It also includes **wallet‑abuse attacks**, in which adversaries intentionally offload their own workloads onto your model—using it to perform high‑cost tasks at your expense—creating hidden financial drain alongside traditional denial‑of‑service impacts.

## MITRE ATLAS mapping
This scenario maps broadly to MITRE ATLAS behaviors around resource exhaustion, API abuse, and performance degradation.

**[MITRE ATLAS Techniques](https://atlas.mitre.org/techniques) (Attack):**
The attack primarily reflects resource exhaustion: adversaries drive excessive token, compute, memory, or cost consumption through high-volume requests, pathological prompts, or runaway agent loops.
* AML.T0029 Denial of AI Service
* AML.T0034 Cost Harvesting
* AML.T0040 AI Model Inference API Access

**[MITRE ATLAS Mitigations](https://atlas.mitre.org/mitigations) (Defense):**
Prioritize rate limiting, quotas, input size checks, anomaly detection, cost controls, and graceful degradation.
* AML.M0004 Restrict Number of AI Model Queries
* AML.M0015 Adversarial Input Detection
* AML.M0024 AI Telemetry Logging

