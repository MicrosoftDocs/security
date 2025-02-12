---
title: Respond to Incidents from the Azure Portal
description: Learn how to resolve an incident using both Microsoft Sentinel in the Azure portal and Microsoft Defender XDR, including triage, investigation, and resolution. 
ms.date: 01/26/2025
ms.service: microsoft-365-zero-trust
author: batamig
ms.author: bagol
ms.topic: concept-article
ms.collection: 
  - zerotrust-solution
  - msftsolution-secops
  - msftsolution-scenario
  - zerotrust-azure
  - usx-security
appliesto: 
    - Microsoft Sentinel in the Azure portal

#customerIntent: As a security analyst using Microsoft Sentinel in the Azure portal, I want to understand how to respond to an incident within a Zero Trust architecture, using both Microsoft Sentinel and Microsoft Defender XDR, to minimize impact and ensure quick recovery.
---

# Respond to an incident using Microsoft Sentinel in the Azure portal with Microsoft Defender XDR

This article explains how to resolve security incidents using Microsoft Sentinel in the Azure portal and Microsoft Defender XDR. Learn step-by-step guidance on triage, investigation, and resolution to ensure rapid incident response.

- Updates on lifecycle (status, owner, classification) are shared between the products.
- Evidence gathered during an investigation is shown in the Microsoft Sentinel incident.

For more information about the integration of Microsoft Defender with Microsoft Sentinel, see [Microsoft Defender XDR integration with Microsoft Sentinel](/azure/sentinel/microsoft-365-defender-sentinel-integration). This [interactive guide](https://mslearn.cloudguides.com/guides/Investigate%20security%20incidents%20in%20a%20hybrid%20environment%20with%20Azure%20Sentinel) steps you through detecting and responding to modern attacks with Microsoft’s unified security information and event management (SIEM) and extended detection and response (XDR) capabilities.

## Incident triage

Start triage in the Azure portal with Microsoft Sentinel to review incident details and take immediate action. On the **Incidents** page, locate the suspected incident and update details like owner name, status, and severity or add comments. Drill down for additional information to continue your investigation.

For more information, see [Navigate, triage, and manage Microsoft Sentinel incidents in the Azure portal](/azure/sentinel/incident-navigate-triage)

## Incident investigation

Use the Azure portal as your primary incident response tool, then switch to the Defender portal for more detailed investigation.

For example:

|Portal  |Tasks  |
|---------|---------|
|**In the Azure portal**     | Use Microsoft Sentinel in the Azure portal to correlate the incident with your security processes, policies, and procedures (3P). On an incident details page, select **Investigate in Microsoft Defender XDR** to open the same incident in the Defender portal.      |
|**In the Defender portal**     |   Investigate details such as the incident scope, asset timelines, and self-healing pending actions. You might also need to manually remediate entities, perform live response, and add prevention measures. <br><br>On the incident details page's **Attack story** tab:  <br>   - View the attack story of the incident to understand its scope, severity, detection source, and what entities are affected. <br>- Analyze the incident's alerts to understand their origin, scope, and severity with the alert story within the incident. <br>- As needed, gather information on impacted devices, users, and mailboxes with the graph. Select on any entity to open a flyout with all the details. <br>- See how Microsoft Defender XDR has automatically resolved some alerts with the **Investigations** tab. <br>- As needed, use information in the data set for the incident from the **Evidence and Response** tab.    |
|**In the Azure portal**     |  Return to the Azure portal to perform extra incident actions, such as: <br>- Performing 3P automated investigation and remediation actions <br>- Creating custom security orchestration, automation, and response (SOAR) playbooks<br>- Recording evidence for incident management, such as comments to record your actions and the results of your analysis.<br>- Adding custom measures.   |

For more information, see:

- [Investigate Microsoft Sentinel incidents in depth in the Azure portal](/azure/sentinel/investigate-incidents)
- [Manage incidents in Microsoft Defender](/defender-xdr/manage-incidents?toc=%2Fazure%2Fsentinel%2FTOC.json&bc=%2Fazure%2Fsentinel%2Fbreadcrumb%2Ftoc.json)

## Automation with Microsoft Sentinel

Use Microsoft Sentinel's playbook and automation rule functionality:

- **A playbook** is a collection of investigation and remediation actions that you run from the Microsoft Sentinel portal as a routine. Playbooks help automate and orchestrate your threat response. They run manually on incidents, entities, or alerts, or automatically when triggered by an automation rule. For more information, see [Automate threat response with playbooks](/azure/sentinel/automate-responses-with-playbooks).

- **Automation rules** let you centrally manage automation in Microsoft Sentinel by defining and coordinating a small set of rules that apply across different scenarios. For more information, see [Automate threat response in Microsoft Sentinel with automation rules](/azure/sentinel/automate-incident-handling-with-automation-rules).

## Incident resolution

When your investigation concludes and you have fixed the incident in the portals, resolve it. For more information, see [Closing an incident in the Azure portal](/azure/sentinel/incident-navigate-triage#close-an-incident).

Report the incident to your incident response lead for potential follow-up actions. For example:

- Inform your Tier 1 security analysts to better detect the attack early.
- Research the attack in Microsoft Defender XDR Threat Analytics and the security community for a security attack trend.
- Record the workflow used to resolve the incident and update your standard workflows, processes, policies, and playbooks.
- Determine whether changes in your security configuration are needed and implement them.
- Create an orchestration playbook to automate your threat response for similar risks. For more information, see [Automate threat response with playbooks in Microsoft Sentinel](/azure/sentinel/automate-responses-with-playbooks).

## Related content

For more information, see:

- [Microsoft Defender XDR integration with Microsoft Sentinel](/azure/sentinel/microsoft-365-defender-sentinel-integration)
- [Unified SIEM and XDR capabilities interactive guide](https://mslearn.cloudguides.com/guides/Investigate%20security%20incidents%20in%20a%20hybrid%20environment%20with%20Azure%20Sentinel)
- [Microsoft Defender XDR Threat Analytics](/microsoft-365/security/defender/threat-analytics)
