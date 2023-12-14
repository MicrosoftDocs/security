---
title: Step 4. Respond to an incident using Microsoft Sentinel and Microsoft Defender XDR
description: Learn how to resolve an incident using both Microsoft Sentinel and Microsoft Defender XDR, which includes triage, investigation, and resolution. 
ms.date: 03/29/2023
ms.service: microsoft-365-zero-trust
author: mjcaparas
ms.author: macapara
ms.topic: conceptual
ms.collection: 
  - zerotrust-solution
  - msftsolution-secops
  - msftsolution-scenario
  - zerotrust-azure
---

# Step 4. Respond to an incident using Microsoft Sentinel and Microsoft Defender XDR

This article provides a general set of steps and procedures to resolve an incident using Microsoft Sentinel and Microsoft Defender XDR, which includes triage, investigation, and resolution. 
Microsoft Sentinel and Microsoft Defender XDR share:

- Updates on lifecycle (status, owner, classification) are shared between the products.
- Evidence gathered during an investigation is shown in the Microsoft Sentinel incident.

The following diagram shows how Microsoft’s extended detection and response (XDR) solution seamlessly integrates with Microsoft Sentinel.

:::image type="content" source="./media/sentinel-xdr.svg" alt-text="The Microsoft solution for XRD with Microsoft Sentinel" lightbox="./media/sentinel-xdr.svg":::

In this diagram:

- Insights from signals across your entire organization feed into Microsoft Defender XDR and Microsoft Defender for Cloud.
- Microsoft Defender XDR and Microsoft Defender for Cloud send SIEM log data through a series of Microsoft Sentinel connectors.
- SecOps teams can then analyze and respond to threats.
- Microsoft Sentinel provides support for multi-cloud environments and integrates with third-party apps and partners.

For more information about the integration of Microsoft Defender with Microsoft Sentinel, see [Microsoft Defender XDR integration with Microsoft Sentinel](/azure/sentinel/microsoft-365-defender-sentinel-integration). This [interactive guide](https://mslearn.cloudguides.com/guides/Investigate%20security%20incidents%20in%20a%20hybrid%20environment%20with%20Azure%20Sentinel)
steps you through detecting and responding to modern attacks with Microsoft’s unified security information and event management (SIEM) and extended detection and response (XDR) capabilities.

## Incident response process

The process of incident response to resolve an incident using Microsoft Sentinel and Microsoft Defender XDR is:

1. Use Microsoft Sentinel portal to triage the potential incident, which includes understanding the details of the incident and taking immediate actions.
1. Move over to the Microsoft Defender portal to begin your investigation. This includes:

   - Understanding the incident and its scope and reviewing asset timelines.
   - Reviewing self-healing pending actions, manually remediating entities, performing live response.
   - Adding prevention measures.

1. Where needed, continue the investigation in the Microsoft Sentinel portal. This includes:

   - Understanding the scope of the incident (correlate with your security Processes, Policies and Procedures [3P]).
   - Performing 3P automated investigation and remediation actions and creating custom Security Orchestration, Automation, and Response (SOAR) playbooks.
   - Recording evidence for incident management.
   - Adding custom measures.

1. Resolve the incident in the Microsoft Sentinel portal and perform appropriate follow-up within your security team.

Within Microsoft Sentinel, you can take advantage of playbooks and automation rules.

- A playbook is a collection of investigation and remediation actions that can be run from the Microsoft Sentinel portal as a routine. Playbooks can help automate and orchestrate your threat response. They can be run manually on-demand on incidents, entities, and alerts, or set to run automatically in response to specific alerts or incidents, when triggered by an automation rule. For more information, see [Automate threat response with playbooks](/azure/sentinel/automate-responses-with-playbooks).
- Automation rules are a way to centrally manage automation in Microsoft Sentinel, by allowing you to define and coordinate a small set of rules that can apply across different scenarios. For more information, see [Automate threat response in Microsoft Sentinel with automation rules](/azure/sentinel/automate-incident-handling-with-automation-rules).

:::image type="content" source="media/incident-reponse-process.png" alt-text="The four-step incident response process and which portal you need to use.":::

The following sections describe the general incident response process using the Microsoft Sentinel and Microsoft Defender portals.

## Step 1: Triage the incident in the Microsoft Sentinel portal

Use these steps as a general method to triage the incident with Microsoft Sentinel:

1. Open the Microsoft Sentinel portal.
1. Select **Incidents**, and then find the suspected incident. You can search for incidents by their ID, title, tags, incident owner, entity, or product.
1. Once you have located the incident, select it, and then select **View full details** in the incident summary pane (Preview).
1. From the **Overview** tab, view the incident summary, timeline, entities, top insights, similar incidents, and other information. To run a previously created playbook on the incident, select **Incident actions**, and then select **Run playbook (Preview)**.
1. From the **Entities** tab, find the entity of interest in the list. You can use the search box to search for the entity’s name or filter on entity type. 
1. To run a previously created playbook on an entity, select the entity, and then select **Run playbook**. In the **Run playbook** pane, select **Run** for the playbooks you have created and need for this incident to generate additional information on the entity.
1. In the **Insights** section of the entity pane, select the appropriate categories of insights you need to gather information on the entity. Please note that the insights shown here are based on the last 24 hours before the first alert is created. When you click on **Full Details** more insights are shown with a configurable time range.
1. Select **Incident**, and then select the **Comments** tab.
1. If playbooks were run automatically or manually, review the comments created by them on the incident.

For more information, see [Navigate and investigate incidents in Microsoft Sentinel](/azure/sentinel/investigate-incidents).

## Step 2: Investigate the incident in the Microsoft Defender portal

Use these steps as a general method to investigate the incident with Microsoft Defender XDR:

1. From the **Incident** page of the Microsoft Sentinel portal (Preview), select **Investigate in Microsoft Defender XDR** in the summary pane. 
1. From the **Attack story** tab in the Microsoft Defender portal, begin your investigation with Microsoft Defender XDR. Consider using the following next steps for your own incident response workflow.
1. View the attack story of the incident to understand its scope, severity, detection source, and what entities are affected.
1. Begin analyzing the alerts to understand their origin, scope, and severity with the alert story within the incident.
1. As needed, gather information on impacted devices, users, and mailboxes with the graph. Click on any entity to open a flyout with all the details.
1. See how Microsoft Defender XDR has automatically resolved some alerts with the **Investigations** tab.
1. As needed, use information in the data set for the incident from the **Evidence and Response** tab.

For more information, see [Incident response with Microsoft Defender XDR](/microsoft-365/security/defender/incidents-overview).

## Step 3: Continue the investigation in the Microsoft Sentinel portal (as needed)

Use these steps as a general method to continue the incident investigation with Microsoft Sentinel using the improved incidents page (Preview).

1. In the Microsoft Sentinel portal, locate the incident in the incident queue, select it, and then select **View full details** in the incident summary pane.
1. From the **Overview** tab pane:

   a. View the incident timeline.

   b. Scroll through the list of entities.

   c. See the list of related incidents.

   d. View the top insights for the incident.

   e. Perform an additional incident action, such as running a playbook or creating an automation rule.

   f. Select Investigate to see a graph of the incident.

1. From the **Entities** tab pane:

   a. View details and insights on a selected entity.

   b. As needed and if available, run a playbook (Preview).

1. Add comments to the incident to record your actions and the results of your analysis.

For more information, see [Navigate and investigate incidents in Microsoft Sentinel](/azure/sentinel/investigate-incidents).

## Step 4: Resolve the incident

When your investigation has reached its conclusion and you have remediated the incident within the portals, you can resolve the incident in the Microsoft Sentinel portal by setting the incident’s status to Closed.

1. In the Microsoft Sentinel portal using the improved incident page (Preview), locate the incident in the incident queue and select it. In the **Status** drop-down for the incident, select **Closed**, and then select a classification:

   - True Positive – suspicious activity
   - Benign Positive – suspicious but expected
   - False Positive – incorrect alert logic
   - False Positive – incorrect data
   - Undetermined

   By selecting a classification, data for the incident is input into a machine learning model which helps Microsoft provide you with recommendations and correlation information.

1. You will also be prompted to provide a comment on the incident. You can add details such as:

   - The type of attack with a standard description or with codes or abbreviations used on your security team.
   - The names of the people who worked on the incident.
   - The key entities that were affected by the attack.
   - Notes on remediation tasks and strategies.

    Here’s an example.

    :::image type="content" source="media/example-resolving-incident.png" alt-text="Example of resolving an incident in the Microsoft Sentinel portal.":::

1. Select **Apply** to resolve the incident. Once you close the incident in Microsoft Sentinel, it will synchronize the incident status to Microsoft Defender XDR and Microsoft Defender for Cloud.

1. As needed, report the incident to your incident response lead for possible follow-up to determine additional actions, such as:

   - Inform your Tier 1 security analysts to better detect the attack early.
   - Create an orchestration playbook to automate and orchestrate your threat response for a similar. For more information, see [Automate threat response with playbooks in Microsoft Sentinel](/azure/sentinel/automate-responses-with-playbooks).
   - Research the attack in Microsoft Defender XDR Threat Analytics and the security community for a security attack trend.
   - As needed, record the workflow you used to resolve the incident and update your standard workflows, processes, policies, and playbooks.
   - Determine whether changes in your security configuration are needed and implement them.

## Recommended training

The following are the recommended training modules for this step.

### Security incident management in Microsoft Sentinel

|Training  |[Security incident management in Microsoft Sentinel](/training/modules/incident-management-sentinel/)|
|---------|---------|
|:::image type="icon" source="media/incident-management-sentinel.svg" border="false"::: | In this module, you'll investigate Microsoft Sentinel incident management, learn about Microsoft Sentinel events and entities, and discover ways to resolve incidents. |
> [!div class="nextstepaction"]
> [Start >](/training/modules/incident-management-sentinel/)

### Improve your reliability with modern operations practices: Incident response

|Training  |[Training Improve your reliability with modern operations practices: Incident response](/training/modules/improve-reliability-incidents/)|
|---------|---------|
|:::image type="icon" source="media/improve-reliability-incidents.svg" border="false"::: | Learn the fundamentals of efficient incident response and the Azure tools that make them possible. |
> [!div class="nextstepaction"]
> [Start >](/training/modules/improve-reliability-incidents/)

### Understand Microsoft 365 security incident management

|Training  |[Understand Microsoft 365 security incident management](/training/modules/audit-incident-management/)|
|---------|---------|
|:::image type="icon" source="media/understand-microsoft-365-security-incident-management.svg" border="false"::: | Learn how Microsoft 365 investigates, manages, and responds to security concerns to protect customers and the Microsoft 365 cloud environment. |
> [!div class="nextstepaction"]
> [Start >](/training/modules/audit-incident-management/)

## Next steps

- See [Navigate and investigate incidents in Microsoft Sentinel](/azure/sentinel/investigate-incidents) and [Incident response with Microsoft Defender XDR](/microsoft-365/security/defender/incidents-overview) for more details about incident response processes within the Microsoft Sentinel and Microsoft Defender portals.
- See [Incident response overview](/security/compass/incident-response-overview) for Microsoft security best practices.
- See [Incident response playbooks](/security/compass/incident-response-playbooks) for workflows and checklists to respond to common cyberattacks.

## References

Use these resources to learn about the various services and technologies mentioned in this article:

- [Microsoft Defender XDR integration with Microsoft Sentinel](/azure/sentinel/microsoft-365-defender-sentinel-integration)
- [Unified SIEM and XDR capabilities interactive guide](https://mslearn.cloudguides.com/guides/Investigate%20security%20incidents%20in%20a%20hybrid%20environment%20with%20Azure%20Sentinel)
- [Automate threat response with playbooks in Microsoft Sentinel](/azure/sentinel/automate-responses-with-playbooks)
- [Automate threat response with playbooks](/azure/sentinel/automate-responses-with-playbooks)
- [Automate threat response in Microsoft Sentinel with automation rules](/azure/sentinel/automate-incident-handling-with-automation-rules)
- [Microsoft Defender XDR Threat Analytics](/microsoft-365/security/defender/threat-analytics)

Use these resources to learn more about incident response:

- [Navigate and investigate incidents in Microsoft Sentinel](/azure/sentinel/investigate-incidents)
- [Incident response with Microsoft Defender XDR](/microsoft-365/security/defender/incidents-overview)
- [Incident response overview](/security/compass/incident-response-overview)
- [Incident response playbooks](/security/compass/incident-response-playbooks)
