---
title: Step 4. Streamline response
description: Modernize security operations - Step 3. Streamline response 
ms.service: security
ms.author: josephd
author: JoeDavies-MSFT
manager: dansimp
ms.topic: conceptual
---

# Step 4. Streamline response

NOTE TO REVIEWERS: This article is in progress and not ready for technical review.

Your security operations (SecOps) must master threat response and remediation on commonly-attacked resources using Extended Detection and Response (XDR) technology provide high quality alerts for these new resource types, bypassing the manual effort and delays when trying to build every alert in a security information and event management (SIEM) solution. 

Streamlining the processes for these common attacks and focusing the triage (Tier 1) and investigation (Tier 2) analyst teams on mastering these attacks will catch both commodity and advanced attackers earlier in the process, reducing risk to your organization. 

## Program and project member accountabilities

This table describes the implementation of an XDR in terms of a sponsorship/program management/project management hierarchy to determine and drive results.

| Lead | Owner | Accountability |
|:-------|:-------|:-----|
|  CISO, CIO, or Director of Identity Security | | Executive sponsorship |
| Program lead from SecOps Leadership| | Drive results and cross-team collaboration |
| | Security Architect  | Advise on configuration and standards |
| | SecOps Analysts | Implement configuration changes |
| | SecOps Analysts | Update standards and policy documents |
| | Security Governance | Monitor to ensure compliance |

## Deployment objectives

Meet these deployment objectives to streamline your SecOps for Zero Trust.

| Done | Deployment objective | Owner |
|:-------|:-------|:-----|
| <input type="checkbox" /> | [1. Use the minimal number of alert queues](#singlequeue). | Security Architect |
| <input type="checkbox" /> | [2a. (in parallel with step 2b) Set up Microsoft 365 Defender and AutoIR](#m365xdr). | Security Engineer |
| <input type="checkbox" /> | [2b. (in parallel with step 2b) Set up Microsoft Defender for Cloud](#azurexdr). | Security Engineer |

<a id="singlequeue"></a>
## 1. Use the minimal number of alert queues

This is a strategic deployment objective for modernizing your security operations. There are no specific implementation steps to follow because it is not something done on its own. Instead, it is a concept that must be intentionally assessed and applied alongside each of the upcoming deployment objectives and implementation steps within this initiative.

When you maintain a minimal number of alert queues, you have a strategy that will:

- Allow for better contextualization and correlation of alerts or incidents, because inbound events from all sources feed into a single tool
- Improve the overall efficiency of security operations teams, regardless of role or level, because they can follow a standardized response process and work within the same tool


<a id="m365xdr"></a>
## 2a. (in parallel with step 2b) Set up Microsoft 365 Defender and AutoIR

<!--
NOTES FROM THE OUTLINE: This section will contain the deployment objectives and technical deployment instructions for Microsoft 365 Defender (previously Microsoft Threat Protection). It should include Endpoint, Email (O365), and Identity. This section will also contain the deployment objectives and technical deployment instructions for the Automated investigation and response (AutoIR) feature in Microsoft 365 Defender.
--> 

Microsoft 365 Defender is the integrated solution for detecting and responding to attacks on mailboxes, endpoints, user identities, and applications. Microsoft 365 Defender stitches together the threat signals and alerts of attacks into incidents so your security analysts can quickly determine the full scope, impact, and targets of the attack and respond with remediation and recovery steps.

Microsoft 365 Defender also includes powerful automated investigation and response (AutoIR) capabilities that can save your security operations team a lot of time and effort. With self-healing, AutoIR mimics the steps a security analyst would take to investigate and respond to threats, only faster, and with more ability to scale.

Perform these implementation steps to set up Microsoft 365 Defender and AutoIR.


| Done | Implementation step | Owner | Documentation |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> | 1. Turn on Microsoft 365 Defender. | Security Architect | [Enable](https://docs.microsoft.com/microsoft-365/security/defender/m365d-enable) |
| <input type="checkbox" /> | 2. Deploy the supported services of Defender for Endpoint, Defender for Office 365, Defender for Identity, and Defender for Cloud Apps. | Security Architect | [Deploy](https://docs.microsoft.com/microsoft-365/security/defender/deploy-supported-services) |
| <input type="checkbox" /> | 3. Configure AutoIR capabilities. | Security Architect | [Configure](https://docs.microsoft.com/microsoft-365/security/defender/m365d-configure-auto-investigation-response) |
| <input type="checkbox" /> | 4. Train your SecOps staff. | Security Architect | [Resources](https://docs.microsoft.com/microsoft-365/security/defender/microsoft-365-defender-train-security-staff) |


<a id="azurexdr"></a>
## 2b. (in parallel with step 2a) Set up Microsoft Defender for Cloud

<!--
NOTES FROM THE OUTLINE: This section will contain the deployment objectives and technical deployment instructions for Azure Defender for Cloud (previously Azure Defender or Azure Security Center). This deployment objective does not have any dependencies with 2a Setting up M365 XDR and setting up AutoIR, so customers can choose to deploy it in parallel if desired.
--> 

Perform these implementation steps to set up Microsoft Defender for Cloud.

| Done | Implementation step | Owner | Documentation |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> | 1. Deploy Defender for Cloud pre-requisites. | Security Architect | a. [Permissions](https://docs.microsoft.com/azure/defender-for-cloud/permissions)  <BR><BR> b. [Best practices for designing Defender for Cloud workspace](https://techcommunity.microsoft.com/t5/microsoft-sentinel-blog/best-practices-for-designing-a-microsoft-sentinel-or-azure/ba-p/832574) <BR><br> c. [Designing your workspace](https://docs.microsoft.com/azure/azure-monitor/logs/design-logs-deployment#important-considerations-for-an-access-control-strategy) |
| <input type="checkbox" /> | 2. Set up Microsoft Defender for Cloud | Security Architect | [Set up Microsoft Defender for Cloud](https://docs.microsoft.com/azure/defender-for-cloud/get-started) |
| <input type="checkbox" /> | 3.  Enable all Microsoft Defender plans  | Security Architect | [Enable all Defender plans ](https://docs.microsoft.com/azure/defender-for-cloud/enable-enhanced-security) <BR><BR> a. [Policy to enable Defender for Cloud](https://github.com/Azure/Microsoft-Defender-for-Cloud/tree/main/Pricing%20&%20Settings/Azure%20Policy%20definitions/Azure%20Defender%20Plans) <BR><BR> b. [Configure email notifications](https://docs.microsoft.com/azure/defender-for-cloud/configure-email-notifications) <BR><BR> c. [Auto-deploy agents](https://docs.microsoft.com/azure/defender-for-cloud/enable-data-collection?tabs=autoprovision-feature) |
| <input type="checkbox" /> | 4. Connect hybrid and multi-cloud machines | Security Architect | [Connect non-Azure machines](https://docs.microsoft.com/azure/defender-for-cloud/quickstart-onboard-machines?pivots=azure-arc) |
| <input type="checkbox" /> | 5. Customize the set of standards in your regulatory compliance dashboard | Security Architect | [Customize regulatory compliance](https://docs.microsoft.com/azure/defender-for-cloud/update-regulatory-compliance-packages) |
| <input type="checkbox" /> | 6. Deploy management capabilities: <BR><BR>  a. Export Microsoft Defender for Cloud data to Microsoft Sentinel (recommended) <BR><BR> Export Microsoft Defender for Cloud data to other SIEM or ITSM solutions (optional) <BR><BR>  b. Export data for additional reporting  <BR><BR> c. Prepare and deploy Logic Apps (recommended)  <BR><BR>  d. Configure alert suppression rules (optional)  | Security Architect | a. [Connect Defender for Cloud alerts to Microsoft Sentinel](https://docs.microsoft.com/azure/sentinel/connect-defender-for-cloud) <BR><BR> [Stream your alerts to Security Information and Event Management (SIEM) systems and other monitoring solutions](https://docs.microsoft.com/azure/defender-for-cloud/export-to-siem) <br><BR> b. [Setup Continuous export](https://docs.microsoft.com/azure/defender-for-cloud/continuous-export?tabs=azure-portal) <br><BR> c. [Automations](https://docs.microsoft.com/azure/defender-for-cloud/quickstart-automation-alert) <BR><BR> d. [Alert suppression rules](https://docs.microsoft.com/azure/defender-for-cloud/alerts-suppression-rules) |


## Next step

Continue to modernize your security operations for Zero Trust with [Step 5. Unify visibility](modernize-security-operations-unify-visibility.md).
