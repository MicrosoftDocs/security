---

title: Observability for Generative AI and agentic AI systems 
description: Learn how to evolve observability for AI systems such as Generative AI and agentic AI for better monitoring, understanding, and security.
ms.date: 03/17/2026
ms.service: security
ms.subservice: zero-trust
ms.topic: conceptual
ms.collection: 
  - highpri
  - zerotrust
  - sfi-zerotrust
---

# Observability for Generative AI and agentic AI systems

**Pillar name: Monitor and detect threats**<br/>
**Pattern name: Observability for Generative AI and agentic AI systems, including platforms, applications and models**

## Context and problem

As enterprises adopt, build, and use AI systems—specifically Generative AI (GenAI) and agentic AI— traditional observability practices no longer suffice. Conventional software is largely deterministic, with predictable execution paths that operational telemetry can reliably explain. However, today’s AI systems don’t function this way—they are probabilistic by design. Outputs of GenAI systems vary across runs, and "execution" is a distribution over possible behaviors rather than a single reproducible path.  

If we want the ability to monitor, understand, and troubleshoot what an AI system is doing, we need to evolve the logs, metrics, and traces of traditional observability to incorporate AI-native signals, and we must expand our observability practices to encompass evaluation and governance so that we have the right toolkit for system visibility and can build trustworthy, high-performing AI systems at scale.  

Key challenges include: 

- AI systems are non-deterministic and behaviors can shift depending on inputs, retrieval context, tool outputs, and policy/guardrail decisions—system visibility becomes much more complex. Traditional observability isn’t enough for GenAI or agentic AI systems—it focuses too narrowly on latency, errors, and throughput.
- Uptime and error rates are not good indicators of quality and reliability in AI systems.  
- AI systems are becoming increasingly autonomous with more privilege and access. Some systems can interact with sensitive data, call external APIs, initiate workflows, and act across enterprise environments. When these systems are targeted by threat actors or misused, observability becomes a critical need.
- As more agents are deployed, companies want to answer questions such as *How many AI agents exist in my estate? How are agents behaving? Do peaks in usage or other signals indicate misuse of agents?* 
- While enterprises sprint to adopt and integrate AI systems, their adoption of AI system observability lags behind.

These challenges underscore the need for enterprises to evolve their observability tools and practices and to adopt them at scale, commensurate with their adoption of AI systems. 

## Solution

Evolve logs, metrics, and traces to be AI-native.

1. Log request identity context, timestamp, and conversation/run identifiers, along with execution details such as user inputs and system responses, retrieval source provenance, and agent/tool invocations (tool name, arguments, permissions, and outputs), and represent traces and metrics with OpenTelemetry GenAI semantic conventions. What to capture and retain should be governed by clear data contracts that balance forensic needs against privacy, data residency, data minimization, retention requirements, and compliance with legal and regulatory obligations, with access controls and encryption aligned to enterprise policy and risk assessments.
1. Monitor the system through token usage, latency, error rate, volume of tool calls or requests, and other metrics.
    - Capture the end-to-end journey of a request (traces), linking each step in an agent’s execution. 
    - Standardize using OpenTelemetry (OTel). Remember that logging and telemetry should be sufficient for incident reconstruction.
1. Incorporate evaluation to continuously track quality and safety and capture policy decisions.
1. Establish behavioral baselines and alert on deviations. Determine what “normal” looks like for your AI systems. 
1. Think beyond observability to consider controls, security, governance, and foundational primitives. 
1. Use scaled mechanisms like the Microsoft Secure Development Lifecycle (SDL) or Secure Future Initiative (SFI) to enforce standardized logging and observability across your GenAI and AI agent products enterprise-wide. 


## Guidance

Organizations can adopt similar practices using the following steps:

|Use case|Recommended action |Resource |
|---|---|---|
| AI-native audit logging  | Log copilot and agent interaction events, including contextual metadata    | [Microsoft Purview](https://www.microsoft.com/security/business/microsoft-purview)   |
| Standardize data   | Align with OpenTelemetry (OTel) GenAI semantic conventions so spans and traces are consistent. Stay tuned—OTel’s attribute families are [potentially expanding](https://github.com/open-telemetry/semantic-conventions/issues/2664) with proposals to support multi-agent orchestration (including tasks and memory).   | [OTel GenAI semantic conventions](https://opentelemetry.io/docs/specs/semconv/gen-ai/)  |
| Understand and debug agent behavior   | Trace tool invocations, agent decisions, and inter-service dependencies   | [Microsoft Foundry agent tracing (preview)](/azure/foundry/observability/concepts/trace-agent-concept)  |
| Measure quality, safety, and reliability   | Score model or agent outputs on outcomes such as groundedness, safety/risk, and tool use correctness, for regression testing or gating releases on quality    | [Microsoft Foundry evaluators](/azure/foundry/concepts/built-in-evaluators)  |
| Governance for tools, agents, and models  |  Onboard your agents to Foundry using Microsoft-supported frameworks, or register your own custom agents.  |  [Microsoft Foundry Control Plane](/azure/foundry/control-plane/overview)  |
| Production monitoring  |  Create an Application Insights resource and use built-in experiences and workbooks to publish dashboards  |  [Azure Monitor Application Insights](/azure/azure-monitor/app/app-insights-overview)  |
| Detecting misuse  |  Ingest logs (Purview) and traces (Foundry + Application Insights) for signal correlation  |  [Microsoft Sentinel](https://www.microsoft.com/security/business/siem-and-xdr/microsoft-sentinel)  |

For enterprises using Microsoft Agent 365: 

|Use case|Recommended action |Resource |
|---|---|---|
| Enterprise observability and governance integration  | Use the Microsoft Agent 365 Observability SDK (part of Agent 365 SDK) to emit OTel-aligned telemetry for Agent 365 governance, including admin visibility and Defender/Purview integration    | [Microsoft Agent 365 Observability SDK (Frontier preview)](/microsoft-agent-365/admin/monitor-agents)   |
| Tenant-wide governance   | Use Microsoft Agent 365 in the Microsoft 365 admin center to govern all agents across the tenant.   | [Microsoft Agent 365 (Frontier preview)](https://www.microsoft.com/microsoft-agent-365)  |

## Outcomes

### Benefits

- Improved AI system visibility, monitoring, and control.
- Enhanced security posture. 
- Easier reconstruction of threat activity and shorter mean time to detect and respond (MTTD/MTTR).
- Higher quality, reliability, and safety through evaluations that can be used for release gating or regression testing. 

### Trade-offs 

- Observability tools and conventions are evolving as AI systems evolve. Enterprises must stay abreast of new developments in observability and keep up, to ensure ongoing security, integrity, and safety of their AI systems. 
- Standardizing logging and tracing for AI systems can require company-wide initiatives and leadership support. 
- AI observability is rarely "set it and forget it." It’s a continuous process that incurs operational overhead.  

## Key success factors

Track these KPIs to measure progress:  

- Coverage of AI system observability—the proportion of total AI systems that are observable (emitting logs and traces into monitoring backends).
- The proportion of releases that have run a standard evaluation suite to maintain production thresholds for quality and reliability. 
- The proportion of AI abuse and security scenarios covered by telemetry. Identify top abuse and security scenarios (such as prompt injection or data exfiltration) and make sure you have the telemetry needed to detect and respond. 

## Summary

Observability for GenAI and agentic AI systems is a foundational security and governance practice. Observability for AI systems requires us to evolve the types of signals and telemetry we collect; create new primitives; and reimagine the control plane, so that we can accurately ascertain and govern what is happening in our systems. For organizations that adopt AI observability and enforce it across the enterprise, AI systems can be investigated when incidents occur, improved as behavior evolves, and operated with accountability in production.