---
title: Step 4. Respond to an incident using Microsoft Sentinel and Microsoft Defender XDR
description: Learn how to resolve an incident using both Microsoft Sentinel and Microsoft Defender XDR, which includes triage, investigation, and resolution. 
ms.date: 04/14/2024
ms.service: microsoft-365-zero-trust
author: mjcaparas
ms.author: macapara
ms.topic: conceptual
ms.collection: 
  - zerotrust-solution
  - msftsolution-secops
  - msftsolution-scenario
  - zerotrust-azure
  - usx-security
appliesto: 
    - Microsoft Sentinel in the Microsoft Defender portal
    - Microsoft Sentinel in the Azure portal
---

# Step 4. Respond to an incident using Microsoft Sentinel and Microsoft Defender XDR

This article provides a general set of steps and procedures to resolve an incident using Microsoft Sentinel and Microsoft Defender XDR, which includes triage, investigation, and resolution.

Microsoft Sentinel and Microsoft Defender XDR share:

- Updates on lifecycle (status, owner, classification) are shared between the products.
- Evidence gathered during an investigation is shown in the Microsoft Sentinel incident.

The following diagrams show how Microsoft’s extended detection and response (XDR) solution seamlessly integrates with Microsoft Sentinel, depending on whether you onboarded your Microsoft Sentinel workspace to the unified security operations platform.

## [Workspace onboarded](#tab/onboarded)

The following illustration shows how Microsoft's XDR solution seamlessly integrates with Microsoft Sentinel with the unified security operations platform.

:::image type="content" source="./media/sentinel-xdr-usx.svg" alt-text="Image of a Microsoft Sentinel and XDR" lightbox="./media/sentinel-xdr-usx.svg" border="false":::

In this diagram:

- Insights from signals across your entire organization feed into Microsoft Defender XDR and Microsoft Defender for Cloud.
- Microsoft Sentinel provides support for multi-cloud environments and integrates with third-party apps and partners.
- Microsoft Sentinel data is ingested together with your organization's data into the Microsoft Defender portal.
- SecOps teams can then analyze and respond to threats identified by Microsoft Sentinel and Microsoft Defender XDR in the Microsoft Defender portal.

## [Workspace not onboarded](#tab/not-onboarded)

The following illustration shows how Microsoft's XDR solution seamlessly integrates with Microsoft Sentinel.

:::image type="content" source="./media/sentinel-xdr.svg" alt-text="Image of a Microsoft Sentinel and XDR" lightbox="./media/sentinel-xdr.svg" border="false":::

In this diagram:

- Insights from signals across your entire organization feed into Microsoft Defender XDR and Microsoft Defender for Cloud.
- Microsoft Defender XDR and Microsoft Defender for Cloud send SIEM log data through Microsoft Sentinel connectors.
- SecOps teams can then analyze and respond to threats identified in the Microsoft Sentinel and Microsoft Defender portals.
- Microsoft Sentinel provides support for multi-cloud environments and integrates with third-party apps and partners.

For more information about the integration of Microsoft Defender with Microsoft Sentinel, see [Microsoft Defender XDR integration with Microsoft Sentinel](/azure/sentinel/microsoft-365-defender-sentinel-integration). This [interactive guide](https://mslearn.cloudguides.com/guides/Investigate%20security%20incidents%20in%20a%20hybrid%20environment%20with%20Azure%20Sentinel)
steps you through detecting and responding to modern attacks with Microsoft’s unified security information and event management (SIEM) and extended detection and response (XDR) capabilities.

---

## Incident response process

The process of incident response to resolve an incident using Microsoft Sentinel and Microsoft Defender XDR is differs, depending on whether you onboarded your workspace to the unified security operations platform, and can access Microsoft Sentinel in the Defender portal.

## [Workspace onboarded](#tab/onboarded)

1. Use the Defender portal to triage the potential incident, which includes understanding the details of the incident and taking immediate actions.

1. Continue the investigation in the Defender portal, including:

   - Understanding the incident and its scope and reviewing asset timelines.
   - Reviewing self-healing pending actions, manually remediating entities, performing live response.
   - Adding prevention measures.

   Use the Microsoft Sentinel area of the Defender portal deepen your investigation, including:

   - Understanding the scope of the incident (correlate with your security Processes, Policies and Procedures [3P]). <!--what does this mean?-->
   - Performing 3P automated investigation and remediation actions and creating custom security orchestration, automation, and response (SOAR) playbooks.
   - Recording evidence for incident management.
   - Adding custom measures.

1. Resolve the incident and perform appropriate follow-up within your security team.

## [Workspace not onboarded](#tab/not-onboarded)

1. Use Microsoft Sentinel portal to triage the potential incident, which includes understanding the details of the incident and taking immediate actions.

1. Move over to the Microsoft Defender portal to begin your investigation. This includes:

   - Understanding the incident and its scope and reviewing asset timelines.
   - Reviewing self-healing pending actions, manually remediating entities, performing live response.
   - Adding prevention measures.

1. Where needed, continue the investigation in the Microsoft Sentinel portal. This includes:

   - Understanding the scope of the incident (correlate with your security Processes, Policies and Procedures [3P]).
   - Performing 3P automated investigation and remediation actions and creating custom security orchestration, automation, and response (SOAR) playbooks.
   - Recording evidence for incident management.
   - Adding custom measures.

1. Resolve the incident in the Microsoft Sentinel portal and perform appropriate follow-up within your security team.

:::image type="content" source="media/incident-reponse-process.png" alt-text="The four-step incident response process and which portal you need to use.":::

---

Make sure to take advantage of Microsoft Sentinel's playbook and automation rule functionality:

- **A playbook** is a collection of investigation and remediation actions that can be run from the Microsoft Sentinel portal as a routine. Playbooks can help automate and orchestrate your threat response. They can be run manually on-demand on incidents, entities, and alerts, or set to run automatically in response to specific alerts or incidents, when triggered by an automation rule. For more information, see [Automate threat response with playbooks](/azure/sentinel/automate-responses-with-playbooks).

- **Automation rules** are a way to centrally manage automation in Microsoft Sentinel, by allowing you to define and coordinate a small set of rules that can apply across different scenarios. For more information, see [Automate threat response in Microsoft Sentinel with automation rules](/azure/sentinel/automate-incident-handling-with-automation-rules).

After onboarding your Microsoft Sentinel workspace to the unified security operations platform, note that there are differences in how automation functions in your workspace. For more information, see [Automation with the unified security operations platform](/azure/sentinel/automation).

The following sections describe the general incident response process using the Microsoft Sentinel and Microsoft Defender portals.

## Step 1: Triage the incident

Use these steps as a general method to triage the incident with Microsoft Sentinel:
<!--validate these-->
## [Workspace onboarded](#tab/onboarded)

Investigate Microsoft Sentinel incidents in the Defender portal the same way you would any other incident.

1. In the Defender portal, select **Incidents and alerts > Incidents** and locate the suspected incident.
1. Select **View full details** in the incident summary pane.
1. View details on the following tabs:

   - View general information from the **Overview** tab
   - Find an entity of interest from the **Entities** tab. In the **Insights** section of the entity pane, select the appropriate categories of insights you need to gather information on the entity.

For more information, see [Investigate incidents in Microsoft Defender XDR](/microsoft-365/security/defender/investigate-incidents) and [Run a playbook on demand](/azure/sentinel/tutorial-respond-threats-playbook?tabs=azure-portal%2CLAC%2Cafter-onboarding%2Cincidents%2Cazure).

## [Workspace not onboarded](#tab/not-onboarded)

To investigate incidents in the Azure portal:

1. In Microsoft Sentinel, select **Incidents** and locate the suspected incident.
1. Select **View full details** in the incident summary pane.
1. View details on the following tabs:

   - View general information from the **Overview** tab
   - Find an entity of interest from the **Entities** tab. In the **Insights** section of the entity pane, select the appropriate categories of insights you need to gather information on the entity.

For more information, see [Navigate and investigate incidents in Microsoft Sentinel](/azure/sentinel/investigate-incidents) and  [Run a playbook on demand](/azure/sentinel/tutorial-respond-threats-playbook?tabs=azure-portal%2CLAC%2Cafter-onboarding%2Cincidents%2Cazure).

## Step 2: Investigate the incident

1. Do one of the following:

   - If you're working from the Azure portal, from the **Incident** page of the Microsoft Sentinel portal (Preview), select **Investigate in Microsoft Defender XDR** in the summary pane.

   - If you're working from the Defender portal, <!--where does this come from?-->

1. From the **Attack story** tab in the Microsoft Defender portal, begin your investigation with Microsoft Defender XDR. Consider using the following next steps for your own incident response workflow.

   1. View the attack story of the incident to understand its scope, severity, detection source, and what entities are affected.

   1. Begin analyzing the alerts to understand their origin, scope, and severity with the alert story within the incident.
   
   1. As needed, gather information on impacted devices, users, and mailboxes with the graph. Click on any entity to open a flyout with all the details.

   1. See how Microsoft Defender XDR has automatically resolved some alerts with the **Investigations** tab.

   1. As needed, use information in the data set for the incident from the **Evidence and Response** tab.

For more information, see [Incident response with Microsoft Defender XDR](/microsoft-365/security/defender/incidents-overview).

### Continue investigating in the Azure portal

If you're working in the Azure portal, use the following steps to continue the incident investigation with Microsoft Sentinel using the improved incidents page (Preview): <!--can't you do this in defender too?-->

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

When your investigation has reached its conclusion and you have remediated the incident within the portals, you can resolve the incident in either Microsoft Sentinel in the Azure portal or in the Defender portal by setting the incident’s status to **Closed**.

When marking an incident's status as **Closed**, make sure to select a classification, including true, benign, or false positive options.

For example:

:::image type="content" source="media/example-resolving-incident.png" alt-text="Example of resolving an incident in the Microsoft Sentinel portal.":::

For more information, see [Closing an incident in the Azure portal](/azure/sentinel/investigate-incidents#closing-an-incident) and [Resolve an incident in the Defender portal](/microsoft-365/security/defender/manage-incidents#resolve-an-incident).

As needed, report the incident to your incident response lead for possible follow-up to determine additional actions, such as:

- Inform your Tier 1 security analysts to better detect the attack early.
- Create an orchestration playbook to automate and orchestrate your threat response for a similar risk in the future. For more information, see [Automate threat response with playbooks in Microsoft Sentinel](/azure/sentinel/automate-responses-with-playbooks).
- Research the attack in Microsoft Defender XDR Threat Analytics and the security community for a security attack trend.
- As needed, record the workflow you used to resolve the incident and update your standard workflows, processes, policies, and playbooks.
- Determine whether changes in your security configuration are needed and implement them.

## Recommended training

The following are the recommended training modules for this step. Training content focuses on general availability features, and therefore doesn't include content for the unified security operations platform, which is in Preview.

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
