---
title: 8. Monitoring, Detection, and Forensics
description: Guidance for monitoring AI systems, detecting anomalous behavior, and preserving evidence for investigation and response
ms.date: 7/28/2026
ms.custom:   msecd-doc-authoring-1012
ms.topic: concept-article
ms.service: security
ms.subservice: zero-trust
ms.author: ridive
author: richarddiver-ms
---

# 8. Monitoring, Detection, and Forensics

## What this group defends against

Assume compromise. See it and trace it. This cross-cutting visibility layer supports rug-pull detection, denial-of-service spotting, model-theft alerting, agent-collusion profiling, and grounding-drift detection.

## Core capabilities

Monitoring provides the evidence needed to detect AI-specific abuse, understand normal behavior, investigate incidents, and improve controls. Telemetry must connect the initiating identity to prompts, retrieved context, model and version, guardrail decisions, tool calls, outputs, resource use, and downstream actions through shared correlation identifiers. Centralized analytics can then distinguish expected variability from signs of extraction, poisoning, runaway execution, collusion, or policy drift.

- **Build end-to-end observability:** Centralize logs, metrics, traces, prompt and response events, retrieval records, tool calls, policy decisions, and lineage with appropriate privacy and retention controls.

- **Maintain AI security posture continuously:** Discover and reconcile AI assets - models, agents, endpoints, plugins, and connectors - and flag unsanctioned or shadow AI. Score AI systems for misconfiguration, over-permissioning, and exposure. Monitor configuration and ownership against policy baselines. Prioritize remediation so posture management runs continuously rather than as a point-in-time review.

- **Detect abnormal behavior:** Baseline agent fan-out, query patterns, resource use, failures, denials, and model behavior. Correlate anomalies with identity, application, network, and cloud signals.

- **Support investigation and response:** Use canary or honey tokens, clone and fingerprint analytics, AI-specific threat intelligence, tamper-resistant audit trails, and automated containment playbooks.

## Which technologies do we use?

AI monitoring is most effective when model and agent telemetry are integrated with the enterprise security and operations stack. The following technologies combine fleet-level AI observability, application traces and metrics, cloud workload posture, gateway analytics, and SIEM correlation so teams can move from an unusual AI event to investigation, containment, and forensic reconstruction.

- **Microsoft Sentinel** — a cloud-native SIEM and security-operations platform for collecting, normalizing, detecting, hunting, investigating, and responding across multicloud data. Use data connectors, analytics rules, UEBA, threat intelligence, incidents, automation rules, and playbooks to correlate AI telemetry with identity, endpoint, network, application, and cloud signals.

- **Microsoft Defender for Cloud** — cloud security posture management and workload protection for Azure and multicloud resources. Use security recommendations, regulatory-compliance views, attack-path analysis, vulnerability findings, and runtime alerts to reduce misconfiguration and detect threats affecting the compute, containers, storage, databases, and services that host AI workloads.

- **Azure Monitor and Application Insights** — Azure’s unified observability platform and its application-performance monitoring capability. Collect metrics, logs, traces, events, and OpenTelemetry data; follow distributed transactions; measure latency and failures; and monitor agent runs, tool calls, token use, dependencies, and behavior across Foundry, Copilot Studio, and third-party frameworks.

- **Microsoft Foundry Control Plane observability** — fleet-level visibility for agents, models, tools, guardrails, prohibited behaviors, run completion, compliance posture, token consumption, and cost efficiency across supported platforms. Use it to spot cross-project drift and then pivot to detailed telemetry in Azure Monitor and security investigation in Microsoft Sentinel.

- **Azure API Management analytics** — gateway telemetry for API, model, and tool traffic. Capture caller identity, route, operation, response code, latency, quota and rate-limit events, and token consumption so unusual fan-out, repeated denials, enumeration, or cost spikes can be detected and correlated.

- **AI Security Posture Management** - implemented by combining Microsoft Purview DSPM for AI (data exposure and oversharing), Microsoft Defender for Cloud posture management (misconfiguration, attack paths, and compliance for AI workloads), and Foundry Control Plane inventory (fleet-level agent, model, and tool visibility), reconciled against the AI-BOM to surface unmanaged or shadow AI.

- **Clone, fingerprint, canary, and collusion detection** — custom analytic techniques, not standalone products. Compare response and usage fingerprints, seed monitored canary values, graph agent-to-agent and tool-call relationships, and baseline normal fan-out, timing, and resource use; alert when behavior indicates extraction, unauthorized replication, runaway coordination, or covert data movement.

## Framework mapping

**[OWASP Top 10 for LLM and Generative AI](https://genai.owasp.org/llm-top-10/) (2025)**: Provides cross-cutting detection support, especially for LLM02 Sensitive Information Disclosure, LLM06 Excessive Agency, and LLM10 Unbounded Consumption. Centralized telemetry for prompts, context, tool calls, outputs, agent behavior, and resource use enables detection and investigation; monitoring is a supporting control rather than a one-to-one mitigation category in the Top 10.

**[MITRE ATLAS](https://atlas.mitre.org/mitigations)**: Supports detection and investigation across ATLAS techniques through behavioral analytics, audit evidence, anomaly detection, canary values, model-extraction indicators, agent-relationship analysis, and AI-specific threat intelligence. These are cross-cutting defensive practices; they shouldn't be assigned mitigation IDs unless ATLAS publishes a specific mitigation for the control.

**[NIST AI RMF 1.0 and NIST AI 600-1](https://www.nist.gov/itl/ai-risk-management-framework)**: Supports **MEASURE** and **MANAGE** through continuous monitoring, incident evidence, operational metrics, and feedback loops that identify when behavior, retrieval, tool use, cost, or user interaction diverges from established risk tolerances.
