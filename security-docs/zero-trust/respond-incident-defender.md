---
title: Incident Response -- Resolve Incidents in the Microsoft Defender Portal.
description: This article provides incident response guidance using Microsoft Sentinel in the Defender portal, covering triage, investigation, and resolution.
ms.date: 01/23/2025
ms.service: security
author: batamig
ms.author: bagol
ms.subservice: zero-trust
ms.topic: concept-article
ms.collection: 
  - zerotrust-solution
  - msftsolution-secops
  - msftsolution-scenario
  - zerotrust-azure
  - usx-security
appliesto: 
    - Microsoft Sentinel in the Microsoft Defender portal

#customerIntent: This document provides guidance on how to respond to security incidents within a Zero Trust architecture in the Microsoft Defender portal. It aims to help customers understand the steps and best practices for incident response to minimize impact and ensure quick recovery.
---

# Respond to an incident using the Defender portal

This article explains how to respond to an incident using Microsoft Sentinel in the Defender portal, covering triage, investigation, and resolution.

## Prerequisites

Investigate incidents in the Defender portal:

- Your Log Analytics workspace used for Microsoft Sentinel must be onboarded to the Defender portal. For more information, see [Connect Microsoft Sentinel to the Microsoft Defender portal](/defender-xdr/microsoft-sentinel-onboard?toc=/security/zero-trust/integrate/TOC.json?bc=/security/zero-trust/breadcrumb/toc.json&toc=/security/zero-trust/toc.json).

## Incident response process

When working in the Defender portal, do your initial triage, resolution, and follow-up steps as you would otherwise. When investigating, make sure to:

- Understand the incident and its scope by reviewing asset timelines.
- Review self-healing pending actions, manually remediate entities, and perform live response.
- Add prevention measures.

The added **Microsoft Sentinel** area of the Defender portal helps you deepen your investigation, including:

- Understanding the scope of the incident by correlating it with your security processes, policies, and procedures (3P).
- Performing 3P automated investigation and remediation actions and creating custom security orchestration, automation, and response (SOAR) playbooks.
- Recording evidence for incident management.
- Adding custom measures.

For more information, see:

- [Investigate incidents in Microsoft Defender XDR](/microsoft-365/security/defender/investigate-incidents)
- [Incident response with Microsoft Defender XDR](/microsoft-365/security/defender/incidents-overview)
- [Entity pages in Microsoft Sentinel](/azure/sentinel/entity-pages?tabs=defender-portal)

## Automation with Microsoft Sentinel

Make sure to take advantage of Microsoft Sentinel's playbook and automation rule functionality:

- **A playbook** is a collection of investigation and remediation actions that can be run from the Microsoft Sentinel portal as a routine. Playbooks can help automate and orchestrate your threat response. They can be run manually on-demand on incidents, entities, and alerts, or set to run automatically in response to specific alerts or incidents, when triggered by an automation rule. For more information, see [Automate threat response with playbooks](/azure/sentinel/automate-responses-with-playbooks).

- **Automation rules** are a way to centrally manage automation in Microsoft Sentinel, by allowing you to define and coordinate a small set of rules that can apply across different scenarios. For more information, see [Automate threat response in Microsoft Sentinel with automation rules](/azure/sentinel/automate-incident-handling-with-automation-rules).

After onboarding your Microsoft Sentinel workspace to the Defender portal, note that there are differences in how automation functions in your workspace. For more information, see [Automation with Microsoft Sentinel in the Defender portal](/azure/sentinel/automation).

## Post-incident response

After you've resolved the incident, report the incident to your incident response lead for possible follow-up to determine more actions. For example:

- Inform your Tier 1 security analysts to better detect the attack early.
- Research the attack in Microsoft Defender XDR Threat Analytics and the security community for a security attack trend. For more information, see [Threat analytics in Microsoft Defender XDR](/microsoft-365/security/defender/threat-analytics).
- As needed, record the workflow you used to resolve the incident and update your standard workflows, processes, policies, and playbooks.
- Determine whether changes in your security configuration are needed and implement them.
- Create an orchestration playbook to automate and orchestrate your threat response for a similar risk in the future. For more information, see [Automate threat response with playbooks in Microsoft Sentinel](/azure/sentinel/automate-responses-with-playbooks).

## Related content

For more information, see:

- [Incidents and alerts in the Microsoft Defender portal](/defender-xdr/incidents-overview)
- [Manage incidents](/defender-xdr/manage-incidents)
