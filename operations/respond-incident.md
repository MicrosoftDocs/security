---
title: Step 4. Respond to an incident using Microsoft Sentinel and Microsoft 365 Defender
description: Learn how to address an incident using both Microsoft Sentinel and Microsoft 365 Defender, which includes triage, investigation, and resolution. 
ms.date: 03/15/2023
ms.service: security
author: JoeDavies-TechWriter
ms.author: v-joedavies
ms.topic: conceptual
ms.collection: 
  - msftsolution-azurepaas
  - msftsolution-scenario
  - zerotrust-solution
---

# Step 4. Respond to an incident using Microsoft Sentinel and Microsoft 365 Defender

This article provides a general set of steps and procedures to address an incident using both Microsoft Sentinel and Microsoft 365 Defender, which includes triage, investigation, and resolution.

Microsoft Sentinel and Microsoft 365 Defender share:

- Updates on lifecycle (status, owner, classification) are shared between the products
- Evidence gathered during an investigation is shown in the Microsoft Sentinel incident

The Microsoft 365 Defender and Microsoft Defender for Cloud services cover different parts of the Microsoft cloud. Therefore, both the Microsoft Sentinel portal and the Microsoft 365 Defender portal are needed to fully investigate and respond to an incident.

:::image type="content" source="media/defender-coverage-of-m365d-azure.png" alt-text="Coverage of Microsoft 365 Defender and Microsoft Defender for Cloud for different parts of an Azure AD tenant.":::

Because an attack can target or use entities and resources across the Azure Active Directory (Azure AD) tenant, both portals are needed:

1. The Azure Sentinel portal for the initial identification and triaging of the incident.
2. The Microsoft 365 Defender portal for the investigation of the incident and its affected entities.
3. The Azure Sentinel portal for additional investigation of entities in Azure as needed.
4. The Azure Sentinel portal to resolve the incident.

For more information about the integration of Microsoft Defender with Microsoft Sentinel, see [Microsoft 365 Defender integration with Microsoft Sentinel](/azure/sentinel/microsoft-365-defender-sentinel-integration) . This [interactive guide](https://mslearn.cloudguides.com/guides/Investigate%20security%20incidents%20in%20a%20hybrid%20environment%20with%20Azure%20Sentinel)
steps you through detecting and responding to modern attacks with Microsoft’s unified security information and event management (SIEM) and extended detection and response (XDR) capabilities.

This article also describes an example of the incident response process for an Adversary in the Middle (AiTM) incident.

## Incident response process

The process of incident response to address an incident using Microsoft Sentinel and Microsoft 365 Defender is:

1. Use Microsoft Sentinel portal to triage the potential incident.
1. Move over to the Microsoft 365 Defender portal to begin your investigation. This includes:

   - Understanding the incident and its scope and reviewing asset timelines.
   - Reviewing self-healing pending actions, manually remediate entities, perform live response.
   - Adding prevention measures.

1. Where needed, continue the investigation in the Microsoft Sentinel portal. This includes:

    - Understanding the scope of the incident (correlate with your security Processes, Policies and Procedures [3P]).
    - Performing 3P remediation actions and creating custom Security Orchestration, Automation, and Response (SOAR) playbooks.
    - Recording evidence for incident management.
    - Adding custom measures.

1. Resolve the incident in the Microsoft Sentinel portal. This can include creating an orchestration playbook and performing appropriate follow-up within your security team.

:::image type="content" source="media/incident-reponse-process.png" alt-text="The four-step incident response process and which portal you need to use.":::

The following sections describe the general incident response process using the Microsoft Sentinel and Microsoft 365 Defender portals.

## Step 1. Triage the incident in the Microsoft Sentinel portal

Use these steps as a general method to triage the incident with Microsoft Sentinel:

1. Open the Microsoft Sentinel portal.
2. Select **Incidents**, and then find the suspected incident. You can search for incidents by their ID, title, tags, incident owner, or product.
3. Once you have located the incident, select it, and then select **View full details** in the incident summary pane.
4. Select the **Entities** tab, and then find the entity of interest in the list. You can use the search box to search for the entity’s name.
5. If needed, select the entity, and select **Run playbook**. In the **Run playbook** pane, select **Run** for the playbooks you need to generate additional information on the entity.
6. Select the entity of interest and in the **Insights** section of the **Overview** pane, select the appropriate categories of insights you need to gather information on the entity.
7. Select **Incident **in the eyebrow navigation path. Select the **Comments** tab.
8. Review the comments created by each playbook run on the incident.

For more information, see Navigate and investigate incidents in Microsoft Sentinel.

## Step 2. Investigate the incident in the Microsoft 365 Defender portal

Use these steps as a general method to investigate the incident with Microsoft 365 Defender:

1. From the **Incident** page for the incident the Microsoft Sentinel portal, select **Investigate in Microsoft 365 Defender** under the name and incident ID. Here is an example.

   :::image type="content" source="media/example-investigate-in-m365d-portal.png" alt-text="Example of selecting the option to investigate an incident in the Microsoft 365 Defender portal.":::

2. From the **Attack story** tab in the Microsoft 365 Defender portal, begin your investigation with Microsoft 365 Defender. Consider using the following next steps for your own incident response workflow.
3. View the attack story of the incident to understand its scope, severity, detection source, and what entities are affected.
4. Begin analyzing the alerts to understand their origin, scope, and severity with the alert story within the incident.
5. As needed, gather information on impacted devices, users, and mailboxes with the graph. Right-click on any entity to open a flyout with all the details.
6. See how Microsoft 365 Defender has automatically resolved some alerts with the **Investigations** tab.
7. As needed, use information in the data set for the incident for more information with the **Evidence and Response** tab.

For more information, see [Incident response with Microsoft 365 Defender](/microsoft-365/security/defender/incidents-overview).

## Step 3. Continue the investigation in the Microsoft Sentinel portal (as needed)

Use these steps as a general method to continue the incident investigation with Microsoft Sentinel:

1. In the Microsoft Sentinel portal, locate the incident in the incident queue, select it, and then select **Investigate**.
2. From the incident graph:

   a. Open the **Entities** pane.

   b. Use exploration queries on relevant entities.

   c. Examine related alerts.

   d. Analyze similar incidents (preview).

   e. Create and use incident tasks to manage the incident workflow.

   f. Add comments to the incident to record your actions and the results of your analysis.

For more information, see [Navigate and investigate incidents in Microsoft Sentinel](/azure/sentinel/investigate-incidents).

## Step 4. Resolve the incident

When your investigation has reached its conclusion and you have remediated the incident damage within the portals, you can resolve the incident in the Microsoft Sentinel portal by setting the incident’s status to Closed. 

1. In the Microsoft Sentinel portal, locate the incident in the incident queue and select it. In the **Status** drop-down for the incident, select **Closed**, and then select a classification:

   - True Positive – suspicious activity
   - Benign Positive – suspicious but expected
   - False Positive – incorrect alert logic
   - False Positive – incorrect data
   - Undetermined

1. You are then prompted to provide a comment on the incident. You can add details such as:

   - The type of attack with a standard description or with codes or abbreviations used on your security team.
   - The names of the people who worked on the incident.
   - The key entities that the attack affected.
   - Notes on remediation tasks and strategies.

    Here’s an example.

   :::image type="content" source="media/example-resolving-incident.png" alt-text="Example of resolving an incident in the Microsoft Sentinel portal.":::

3. Select **Apply** to resolve the incident. Once you close the incident in Microsoft Sentinel, it synchronizes the incident status to Microsoft 365 Defender and Microsoft Defender for Cloud.
4. As needed, report the incident to your incident response lead for possible follow-up to determine additional actions, such as: 

   - Inform your Tier 1 security analysts to better detect the attack early.
   - Create an orchestration playbook to automate and orchestrate your threat response for a similar. For more information, see [Automate threat response with playbooks in Microsoft Sentinel](/azure/sentinel/automate-responses-with-playbooks).
   - Research the attack in [Microsoft 365 Defender Threat Analytics](/microsoft-365/security/defender/threat-analytics) and the security community for a cyber-attack trend.
   - As needed, record the workflow you used to resolve the incident and update your standard workflows, processes, policies, and playbooks.
   - Determine whether changes in your security configuration are needed and implement them.

## Example scenario: An Adversary in the Middle incident

This section steps you through an Adversary in the Middle (AiTM) incident as an example of how to do incident triage, investigation, and resolution using Microsoft Sentinel and Microsoft 365 Defender.

An AiTM attack uses a combination of phishing sites to steal passwords, hijack a user’s sign-in session, or uses a proxy to obtain session cookies to gain access. The attack skips the authentication process even if the user performs multi-factor authentication (MFA). The attacker then uses the stolen credentials or session cookies to access affected users’ mailboxes and perform follow-on business email compromise (BEC) campaigns against other targets.

For more information, see [From cookie theft to BEC: Attackers use AiTM phishing sites as entry point to further financial fraud](https://www.microsoft.com/security/blog/2022/07/12/from-cookie-theft-to-bec-attackers-use-aitm-phishing-sites-as-entry-point-to-further-financial-fraud/).

### How an attacker executes an AiTM attack

Here’s an example of how an attacker stages and then executes one type of AiTM attack.

#### A. Set up the attack

An attacker creates:

- An AiTM proxy web site that emulates a Microsoft sign-in window.
- A phishing email that contains a link to the AiTM proxy web site.
- A PowerShell script and a binary file that enables backdoor access to a computer that is stored on the internet.
- A Microsoft Word document containing a malicious macro that executes the PowerShell script to install the binary on the local computer and create backdoor access.

#### B. Deploy the first bait to steal authenticated session cookies

The attacker sends a spear phishing email to Polly Watkins, who is working as a cloud architect in the Azure Infrastructure department. The email is sent from the impersonated email address of a coworker.

Polly opens the email and clicks on a link in the message, which redirects to the attacker’s proxy web site and prompts Polly to sign in using an emulated Microsoft sign-in window.

After Polly enters her credentials and successfully authenticates with MFA, the attacker obtains the session cookies (ESTSAUTH) for the authentication that occurred between Polly and the Azure AD tenant for Polly’s organization.

#### C. Set up the new bait

The attacker uses the stolen authentication cookies to successfully authenticate to the Microsoft 365 and Azure portals for Polly’s organization from a TOR IP address.

In the Microsoft 365 portal, the attacker creates a forwarding rule in Polly’s inbox to exfiltrate sensitive email messages to an external mailbox controlled by the attacker.

In the Azure portal, the attacker leverages Polly’s privileged permissions to create a new Azure Storage container and then uploads the malicious Word document to it.

#### D. Deploy the new bait to gain backdoor access to computers

The attacker obtains the URL to the malicious Word document in the Azure Storage container and a Shared Access Signature (SAS) key and sends an internal phishing email from Polly’s email account to Karla, who is working in the Finance department.

Karla receives and opens the email and clicks the link to download the malicious Word document on her computer. The document runs a macro that executes a PowerShell script that downloads a malicious binary and configures Karla’s computer to run it with the task scheduler service. This creates backdoor access to Karla’s computer for the attacker.

#### The result of the attack

The attacker now:

- Gets a copy of all sensitive emails sent to Polly’s computer.
- Can send additional internal phishing emails to compromise more computers with backdoor access for the duration of the stolen session cookies.
- Has backdoor access to Karla’s computer, which can be used for additional internal phishing attacks.

The following diagram shows the attack process.

:::image type="content" source="media/aitm-attack-example.png" alt-text="Steps in the process of an example AiTM attack.":::

Here’s a summary of the attack steps.

| Attack step | Summary |
| --- | --- |
| 1 | The attacker sends a phishing email to Polly. |
| 2 | Polly clicks on the link in the phishing email and signs in to the impersonated Microsoft sign-in popup window. |
| 3 | Polly authenticates to her organization’s Azure AD tenant with MFA and the proxy web server sends the ESTSAUTH session cookies to the attacker. |
| 4 | The attacker uses Polly’s ESTSAUTH session cookies to create sessions with the Microsoft 365 and Azure portals. |
| 5 | The attacker creates an inbox forwarding rule in Polly’s email account in Microsoft 365. |
| 6 | The attacker creates a new container in an Azure Storage account in the Azure portal. The attacker uploads a malicious Word document file to the container and obtains the URL to the document with a SAS key. |
| 7 | The attacker impersonating Polly sends an internal phishing email to Karla, which includes a link to the malicious Word document file. |
| 8 | When Karla clicks on the link, her computer downloads the document and Word executes the malicious macro. |
| 9 | When Karla clicks on the link, her computer downloads the document and Word executes the malicious macro. |

The leftover elements of the attack are:

- Session cookies from Polly’s proxied authentication, which eventually expire.
- An inbox forwarding rule in Polly’s email mailbox.
- A malicious Word document stored in an Azure Storage container.
- Backdoor access to Karla’s computer through a malicious binary installed and executed using scheduled tasks.

These elements must be addressed to completely recover from the attack.
The following sections describe how security analysts used the Microsoft Sentinel and Microsoft 365 Defender portals to detect and respond to the incident for this attack. It also illustrates how analysts located evidence for each step in the attack listed in the previous table and addressed the leftover elements.

### Step 1. Triage the alert in the Microsoft Sentinel portal

A Tier-1 SOC analyst sees a multi-stage incident in the Microsoft Sentinel portal and notes that:

- The incident affects all of the Microsoft 365 Defender stack and the alerts cover all the MITRE categories. 
- From the **Entities** list, Microsoft Azure is part of this incident, which needs to be investigated using Microsoft Sentinel. 
- Top insights provide detailed information for entities of the incident, including VIP information from the watchlist, IP address reputation, and anomalies seen for accounts.
- In the **Incident Comments**, output results of the following playbooks are included:

  - IP reputation: Get virus total IP reputation of all external IPs associated with the incident, and the geo-location of each IP. Reputation is the IP's score calculated from the votes of the VirusTotal's community.

  - User Account Risk Details: Get risk details from the IdentityInfo table of all users associated with the incident.

  - Endpoint Health Status: Get endpoint security configuration status from Microsoft Defender for Vulnerability Management of all devices associated with the incident.

From the results, the Tier-1 SOC analyst determined that there are malicious IP addresses, high-risk user accounts, and misconfigured vulnerable devices involved. The Tier-1 SOC analyst has found enough evidence to conclude that the incident is a true positive and escalates it to Tier-2 analysts for further investigation.

Summary of the investigation insights so far:

- A multistage targeted attack may have occurred.
- Misconfigured device: Polly’s computer (Realtime Protection & Cloud Protection are turned OFF)
- VIP User: Polly

   Because Polly has high privileges, her account name is added to the VIP watchlist.

- User accounts at risk:

   Karla: High risk, confirmed compromised

   Polly (admin): Medium risk

- Multiple malicious URLs / IPs are related to Polly’s account.
- Multiple IP Addresses with Reputation under 0 in Virus Total indicates a malicious action.
- Microsoft Azure is part of the incident and needs to be investigated with the Microsoft Sentinel portal.

Because there are high risks for user Polly and Karla, the Tier-2 SOC analyst takes immediate steps to block both user accounts in Azure AD. They use the **SIEMXDR-Block-AzureADUser-Entity** playbook to block the users in Azure AD and output the result as a comment for the incident.

### Step 2. Investigate the attack in the Microsoft 365 Defender portal

Now that the Tier 2 SOC analyst understands the broad view of this incident and the entities at risk, they selected **Investigate in Microsoft 365 Defender** for the incident in the Microsoft Sentinel portal to switch to the corresponding incident in the Microsoft 365 Defender portal for more details on alerts that affect Microsoft 365 entities. 

From the **Attack story** page of the corresponding incident in the Microsoft 365 Defender portal, the Tier 2 SOC analyst investigates the **Suspicious URL clicked** alert. In the alert story, they see that Polly has opened outlook.exe and clicked on the link that is categorized as MITRE technique T1204.001: Malicious Link.

The **Suspicious URL clicked** alert is related to the **A potentially malicious URL click was detected** alert. In the details, they see that there is an email sent from an external user to Polly where it had the exact same URL that was determined to be malicious. 

**Attack Step 1 investigation insight:** At this point, the analyst found evidence that the attacker sent an email to Polly that contained a malicious link.

In the URL details of the alert, they see that the URL is considered as a known phish verdict and redirects to a different URL. The URL prompts for a Microsoft login page, so the analyst determines that the attacker had set up a proxy web server.

Additionally, the **Potential phishing web site** alert indicates that the redirected URL is a potential phishing web site.

The analyst also determines that after the suspicious link was clicked, there are additional alerts from Azure AD Identity Protection and Microsoft Defender for Cloud Apps:

- Anonymous IP address
- Activity from infrequent country
- Activity from a Tor IP address

**Attack Step 2 investigation insight:** The analyst found evidence that Polly clicked the link and signed in to the impersonated Microsoft sign-in window of the attacker’s proxy web server.

When drilling down into the Activity from a Tor IP address alert, which is related to the Microsoft Exchange Online or Microsoft 365 entity, the analyst saw the details of logon activity of this user and found out that Polly has successfully authenticated via MFA from a suspicious IP address. 

**Attack Steps 3 and 4 investigation insight:** The analyst found evidence that Polly successfully authenticated through the attacker’s web proxy, which means that the attacker also has the session cookies that can be used to establish sessions and impersonate Polly.

The analyst then saw the **Suspicious inbox forwarding rule** alert and noted that Polly’s email account was configured with a forwarding rule to send bank and credential-related emails to an external mailbox.

**Attack Step 5 investigation insight:** The analyst found evidence that the attacker created an inbox forwarding rule to exfiltrate sensitive emails from Polly’s account.

The analyst saw the **Activity from a Tor IP address** alert related to the Microsoft Azure entity and noted that the attacker logged in to the Azure Storage app and conducted an operation to list keys and write containers in a storage account name.

**Attack Step 6 investigation insight:** The analyst found evidence that the attacker has created an Azure Storage account. The analyst notes that they will need to investigate further within the Microsoft Sentinel portal to determine what happened in the Azure Storage account.

At this point in the investigation, the analyst has determined that Polly’s account is most likely compromised and being used to conduct malicious activities in both Microsoft 365 and Microsoft Azure cloud environments.

With additional alerts in the incident attack story, the analyst saw alerts for Karla’s user account and computer. Selecting the **Suspicious URL clicked** alert for this user and computer, the analyst saw that Karla clicked on a link from an email message, which subsequently downloaded a Word file. 

**Attack Step 8 investigation insight:** The analyst found evidence that Karla received an email containing a link and that Karla clicked it to download a Word file.

The analyst sees the additional alerts regarding the execution of a base64-encoded PowerShell script as a child process, which then downloaded additional payloads that generated more suspicious alerts.

The analyst notes that the PowerShell script:

- Created a persistence mechanism by downloading a binary and hiding it into an NTFS Alternate Data Stream (ADS). ADSs are used in Windows to store additional information about files but attackers also use them to hide content.
- Launched the binary and configured it to be launched at every startup using a scheduled task. 

Once launched, the binary creates a network connection to an IP address that has been declared as malicious.

From the **Email messages containing malicious URL removed after delivery** and **A potentially malicious URL click was detected** related alerts, the analyst determines that the email containing the link to the malicious Word document came from Polly, whose email account has been compromised.

**Attack Step 7 investigation insight:** The analyst found evidence that Polly sent Karla the email with the link to the malicious Word document. 

### Step 3. Complete the investigation

To understand the additional details of how the attacker used Azure Storage resources to facilitate the attack, the SOC Tier 2 analyst moves back to the Microsoft Sentinel portal and finds the corresponding incident.

In the list of similar incidents, the analyst sees additional alerts generated by Microsoft Sentinel’s analytic rules:

- TI map IP entity to SigninLogs (Microsoft Sentinel)
- Azure Storage FileCreated Activity from suspicious proxy IP address (Microsoft Sentinel)

From the **Azure Storage FileCreated Activity from suspicious proxy IP address** alert, the analyst determined that a compromised user had uploaded a word file to Azure Blob Storage from a TOR IP address and the created file also exists on Karla’s computer.

**Attack Step 6 investigation insight:** The analyst found additional evidence that the attacker using Polly’s Azure AD account uploaded a malicious Word file to Azure Blob Storage from a suspicious IP address, which was later downloaded by Karla’s computer.

The analyst then took response actions by running playbooks from automatic tasks for the **Azure Storage FileCreated Activity from suspicious proxy IP address** alert.

- Get User Confirmation on Incident (Alert Trigger)

  This automatic task obtains a confirmation on whether this suspicious activity was conducted by the user or not. The playbook **SIEMXDR-Request-UserConfirmation** sent an email notification to Polly and her manager to get acknowledgment for Polly’s activity. The playbook completed the task and created an incident comment for the result.

- Block Suspicious IP in Microsoft 365 Defender (Entity Trigger)

  The analyst determined that the IP address recorded in the alerts for the incident is a phishing website, so they wanted to add the IP address in Microsoft Defender for Endpoint. The playbook **SIEMXDR-Block-IP-Entity-M365D** added the IP address to the blocklist in Microsoft Defender for Endpoint Indicator and created an incident comment for the result.

- Delete-FilefromBlobStorage-Incident (Alert Trigger)

  The analyst identified the malicious Word document, so they wanted to delete it from Azure storage. The playbook **SIEMXDR-Delete-FilefromBlobStorage-Alert** deleted the file from the Azure Storage account associated with the incident and created an incident comment for the result.

### Step 4. Resolve the incident

After conducting all the necessary steps for this incident, the analyst closed the incident in the Microsoft Sentinel portal for this AiTM attack and performed appropriate follow-ups, such as informing other security staff to make them aware of this type of attack and how to recognize and resolve it. 
To fully recover from the attack, the analyst also contacts:

- Exchange administrators to remove the inbox forwarding rule from Polly’s mailbox.
- Device management staff to clean Karla’s computer of the malicious binary and the scheduled task that runs it.
- Azure Storage administrators to remove the Azure Storage container.

The AiTM attack has been identified, investigated, resolved, and the additional leftover elements of the attack have been addressed. Here is a summary:

| Leftover element of the attack | Recovery or elimination action completed |
| --- | --- |
| Session cookies from Polly’s proxied authentication. | Session cookies have expired or rendered unusable by blocking Polly’s user account. |
| An inbox forwarding rule in Polly’s email account. | The inbox forwarding rule has been removed. |
| Backdoor access to Karla’s computer through an installed malicious binary and execution via scheduled tasks. | Karla’s computer has been cleaned of the binary and the scheduled task has been removed. |
| A malicious Word document stored in an Azure Storage container. | The Word document has been deleted and the Azure Storage container removed. |

## Recommended training

The following are the recommended training modules for this step.

### Security incident management in Microsoft Sentinel

|Training  |[Security incident management in Microsoft Sentinel](/training/modules/incident-management-sentinel/)|
|---------|---------|
|:::image type="icon" source="media/investigation-flow.png" border="false"::: | In this module, you'll investigate Microsoft Sentinel incident management, learn about Microsoft Sentinel events and entities, and discover ways to resolve incidents. |
> [!div class="nextstepaction"]
> [Start >](/training/modules/incident-management-sentinel/)

### Improve your reliability with modern operations practices: Incident response

|Training  |[Training Improve your reliability with modern operations practices: Incident response](/training/modules/improve-reliability-incidents/)|
|---------|---------|
|:::image type="icon" source="./media/improve-reliability-incidents.svg" border="false"::: | Learn the fundamentals of efficient incident response and the Azure tools that make them possible. |
> [!div class="nextstepaction"]
> [Start >](/training/modules/improve-reliability-incidents/)

### Understand Microsoft 365 security incident management

|Training  |[Understand Microsoft 365 security incident management](/training/modules/audit-incident-management/)|
|---------|---------|
|:::image type="icon" source="./media/understand-microsoft-365-security-incident-management.svg" border="false"::: | Learn how Microsoft 365 investigates, manages, and responds to security concerns to protect customers and the Microsoft 365 cloud environment. |
> [!div class="nextstepaction"]
> [Start >](/training/modules/audit-incident-management/)

## Next steps

- See [Navigate and investigate incidents in Microsoft Sentinel](/azure/sentinel/investigate-incidents) and [Incident response with Microsoft 365 Defender](/microsoft-365/security/defender/incidents-overview) for more details about incident response processes within the Microsoft Sentinel and Microsoft 365 Defender portals.
- See [Incident response overview](/security/compass/incident-response-overview) for Microsoft security best practices.
- See [Incident response playbooks](/security/compass/incident-response-playbooks) for workflows and checklists to respond to common cyberattacks.

## References

Refer to the links below to learn about the various services and technologies mentioned in this article.

- [Microsoft 365 Defender integration with Microsoft Sentinel](/azure/sentinel/microsoft-365-defender-sentinel-integration)
- [Unified SIEM and XDR capabilities interactive guide](https://mslearn.cloudguides.com/guides/Investigate%20security%20incidents%20in%20a%20hybrid%20environment%20with%20Azure%20Sentinel)
- [Automate threat response with playbooks in Microsoft Sentinel](/azure/sentinel/automate-responses-with-playbooks)
- [Microsoft 365 Defender Threat Analytics](/microsoft-365/security/defender/threat-analytics)

Incident response:

- [Navigate and investigate incidents in Microsoft Sentinel](/azure/sentinel/investigate-incidents)
- [Incident response with Microsoft 365 Defender](/microsoft-365/security/defender/incidents-overview)
- [Incident response overview](/security/compass/incident-response-overview)
- [Incident response playbooks](/security/compass/incident-response-playbooks)
