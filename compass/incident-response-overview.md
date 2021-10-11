---
title: Incident response overview | Microsoft Docs
description: Understand the role of incident response in your security operations center.
keywords: incidents, alerts, investigate, analyze, response, correlation, attack, incident response, cyber-attack, respond
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

## New-to-role resources

If you are new-to-role as a security analyst, see these resources to get you started.

| Topic | Resource |
|:-------|:-----|
| SecOps planning for incident response | [Incident response planning](incident-response-planning.md) for preparing your organization for an incident. |
| SecOps incident response process | [Incident response process](incident-response-process.md) for best practices on responding to an incident. |
| Incident response workflow  | [Example incident response workflow for Microsoft 365 Defender](/microsoft-365/security/defender/incidents-overview#example-incident-response-workflow-for-microsoft-365-defender) |
| Periodic security operations | [Example periodic security operations for Microsoft 365 Defender](/microsoft-365/security/defender/incidents-overview#example-security-operations-for-microsoft-365-defender) |
| Investigation for Azure Sentinel | [Incidents in Azure Sentinel](/azure/sentinel/tutorial-investigate-cases) |
| Investigation for Microsoft 365 Defender | [Incidents in Microsoft 365 Defender](/microsoft-365/security/defender/incidents-overview) |
|||

## Experienced security analyst resources

If you are an experienced security analyst, see these resources to quickly ramp up your SecOps team for Microsoft security services.

| Topic | Resource |
|:-------|:-----|
| Azure Sentinel | [How to investigate incidents](/azure/sentinel/tutorial-investigate-cases) |
| Microsoft 365 Defender | [How to investigate incidents](/microsoft-365/security/defender/incidents-overview) |
| Security operations establishment or modernization | Azure Cloud Adoption Framework articles for [SecOps](/azure/cloud-adoption-framework/secure/security-operations) and [SecOps functions](/azure/cloud-adoption-framework/organize/cloud-security-operations-center)|
| Microsoft security best practices  | [How to best use your SecOps center](/security/compass/security-operations) |
| Incident response playbooks |  Overview at [https://aka.ms/IRplaybooks](https://aka.ms/IRplaybooks) <br> - [Phishing](incident-response-playbook-phishing.md) <br> - [Password spray](incident-response-playbook-password-spray.md) <br> - [App consent grant](incident-response-playbook-app-consent.md) |
| SOC Process Framework | [Azure Sentinel](https://techcommunity.microsoft.com/t5/azure-sentinel/what-s-new-azure-sentinel-soc-process-framework-workbook/ba-p/2339315) |
| MSTICPy and Jupyter Notebooks | [Azure Sentinel](https://techcommunity.microsoft.com/t5/azure-sentinel/msticpy-and-jupyter-notebooks-in-azure-sentinel-an-update/ba-p/2279661) |
|||

## Blog series about SecOps within Microsoft

See this blog series about how the SecOps team at Microsoft works.

- [Part 1 – Organization: Mission and Culture](https://www.microsoft.com/security/blog/2019/02/21/lessons-learned-from-the-microsoft-soc-part-1-organization/)
- [Part 2a – People: Teams, Tiers, and Roles](https://www.microsoft.com/security/blog/2019/04/23/lessons-learned-microsoft-soc-part-2-organizing-people/)
- [Part 2b – People: Careers and Readiness](https://www.microsoft.com/security/blog/2019/06/06/lessons-learned-from-the-microsoft-soc-part-2b-career-paths-and-readiness/)
- [Part 3a – Technology: SOC Tooling](https://www.microsoft.com/security/blog/2019/10/07/ciso-series-lessons-learned-from-the-microsoft-soc-part-3a-choosing-soc-tools/)
- [Part 3b – Technology: Day in life of an analyst](https://www.microsoft.com/security/blog/2019/12/23/ciso-series-lessons-learned-from-the-microsoft-soc-part-3b-a-day-in-the-life/)
- [Part 3c – A day in the life part 2 - Microsoft Security](https://www.microsoft.com/security/blog/2020/05/04/lessons-learned-microsoft-soc-part-3c/)
- [Part 3d – Zen and the art of threat hunting](https://www.microsoft.com/security/blog/2020/06/25/zen-and-the-art-of-threat-hunting/)


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

The learnings from Simuland lab environment scenarios can then be implemented in your production environment and security processes.

After reading an overview of [Simuland](https://www.microsoft.com/security/blog/2021/05/20/simuland-understand-adversary-tradecraft-and-improve-detection-strategies/), see the [Simuland GitHub repository](https://github.com/Azure/SimuLand).


## Incident response resources

- [Planning](incident-response-planning.md) for your SOC
- [Process](incident-response-process.md) for incident response process recommendations and best practices
- [Playbooks](incident-response-playbooks.md) for detailed guidance on responding to common attack methods
- [Microsoft 365 Defender](/microsoft-365/security/defender/incidents-overview) incident response
- [Azure Sentinel](/azure/sentinel/investigate-cases) incident response


## Key Microsoft security resources 

| Resource | Description |
|:-------|:-----|
| [Microsoft Cybersecurity Reference Architectures](/security/cybersecurity-reference-architecture/mcra) | A set of visual architecture diagrams that show Microsoft’s cybersecurity capabilities and their integration with Microsoft cloud platforms such as Microsoft 365 and Microsoft Azure and third-party cloud platforms and apps. |
| [Minutes matter infographic](https://github.com/MarkSimos/MicrosoftSecurity/raw/master/Microsoft_CDOC_and_DCU_Poster.pdf) download | An overview of how Microsoft's SecOps team does incident response to mitigate ongoing attacks.  |
| [Azure Cloud Adoption Framework security operations](/azure/cloud-adoption-framework/secure/security-operations) | Strategic guidance for leaders establishing or modernizing a security operation function. |
| [Microsoft security best practices for security operations](/security/compass/security-operations) | How to best use your SecOps center to move faster than the attackers targeting your organization. |
| [Microsoft cloud security for IT architects model](https://aka.ms/cloudarchsecurity) | Security across Microsoft cloud services and platforms for identity and device access, threat protection, and information protection. |
| [Microsoft security documentation](/security/) | Additional security guidance from Microsoft. |
|||

