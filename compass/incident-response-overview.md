---
title: Incident response overview | Microsoft Docs
description: Understand the role of incident response in security operations.
ms.author: josephd
author: JoeDavies-MSFT
manager: dansimp
localization_priority: Normal
ms.topic: article
ms.prod: m365-security
---

# Incident response overview

Incident response is the practice of investigating and remediating active attack campaigns on your organization. This is part of the [security operations](/azure/cloud-adoption-framework/secure/security-operations) discipline and is primarily reactive in nature.
 
Incident response has the largest direct influence on the overall mean time to acknowledge (MTTA) and mean time to remediate (MTTR) that measure how well security operations are able to reduce organizational risk. Incident response teams heavily rely on good working relationships between threat hunting, intelligence, and incident management teams (if present) to actually reduce risk. See [SecOps metrics](/azure/cloud-adoption-framework/secure/security-operations#secops-metrics) for more information.
 
For more information on security operations roles and responsibilities, see [Cloud SOC functions](/azure/cloud-adoption-framework/organize/cloud-security-operations-center).

## Simuland

[Simuland](https://www.microsoft.com/security/blog/2021/05/20/simuland-understand-adversary-tradecraft-and-improve-detection-strategies/) is an open-source initiative to deploy lab environments and end-to-end simulations that:

- Reproduce well-known techniques used in real attack scenarios.
- Actively test and verify the effectiveness of related Microsoft 365 Defender, Azure Defender, and Azure Sentinel detections.
- Extend threat research using telemetry and forensic artifacts generated after each simulation exercise.

Simuland lab environments provide use cases from a variety of data sources including telemetry from  Microsoft 365 Defender security products, Azure Defender, and other integrated data sources through Azure Sentinel data connectors.

In the safety of a trial or paid sandbox subscription, you can:

- Understand the underlying behavior and functionality of adversary tradecraft.
- Identify mitigations and attacker paths by documenting preconditions for each attacker action.
- Expedite the design and deployment of threat research lab environments.
- Stay up to date with the latest techniques and tools used by real threat actors.
- Identify, document, and share relevant data sources to model and detect adversary actions.
- Validate and tune detection capabilities.

The learnings from Simuland lab environment scenarios can then be implemented in your production envronment and security processes.

After reading an overview of [Simuland](https://www.microsoft.com/security/blog/2021/05/20/simuland-understand-adversary-tradecraft-and-improve-detection-strategies/), see the [Simuland GitHub repository](https://github.com/Azure/SimuLand).
 
## Next steps

If you are just starting out in incident response, see the [Incident Response Reference Guide](https://download.microsoft.com/download/4/f/f/4ff621f9-6f44-437a-80c7-2624e3d2ce80/IR-Reference-Guide.pdf) for an overview of preparing your organization and what to do during an incident.

If you are experienced with incident response: 

- See how to [investigate incidents in Azure Sentinel](/azure/sentinel/tutorial-investigate-cases).
- See how to [investigate incidents in Microsoft 365 Defender](/microsoft-365/security/defender/incidents-overview).
- Use the incident response playbooks at [https://aka.ms/IRplaybooks](https://aka.ms/IRplaybooks).
  - [Phishing](incident-response-playbook-phishing.md)
  - [Password spray](incident-response-playbook-password-spray.md)
  - [App consent grant](incident-response-playbook-app-consent.md)

## See also

For additional security guidance from Microsoft, see [Microsoft security documentation](/security/).
