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

NOTE TO CONTRIBUTORS: Please see the "NEEDED BY CONTRIBUTORS" tags and help flesh out the needed information.

NOTE TO REVIEWERS: This article is in progress and not ready for technical review.

Your SecOps must master threat response and remediation on commonly-attacked resources using Extended Detection and Response (XDR) technology provide high quality alerts for these new resource types, bypassing the manual effort and delays when trying to build every alert in a security information and event management (SIEM) solution. 

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

NOTES FROM THE OUTLINE: This section is not about technical deployment for a specific product. It’s guidance on a best practice to ensure analysts / SOC can look at a single tool for alert and response. We know that this guidance unfortunately conflicts with our own offerings as we have an XDR for M365 and another different one for Cloud/Azure, but for customers who have SIEM, they may be able to unify it with this as a long-term strategy.)

Perform these implementation steps to meet minimize the number of alert queues.

NEEDED BY CONTRIBUTORS:

| Done | Implementation step | Owner | Documentation |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> | 1.  | Security Architect | link |
| <input type="checkbox" /> | 2.  | Security Architect | link |
| <input type="checkbox" /> | 3.  | Security Architect | link |
| <input type="checkbox" /> | 4.  | Security Architect | link |


<a id="m365xdr"></a>
## 2a. (in parallel with step 2b) Set up Microsoft 365 Defender and AutoIR

NOTES FROM THE OUTLINE: This section will contain the deployment objectives and technical deployment instructions for Microsoft 365 Defender (previously Microsoft Threat Protection). It should include Endpoint, Email (O365), and Identity. This section will also contain the deployment objectives and technical deployment instructions for the Automated investigation and response (AutoIR) feature in Microsoft 365 Defender.

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

NOTES FROM THE OUTLINE: This section will contain the deployment objectives and technical deployment instructions for Azure Defender for Cloud (previously Azure Defender or Azure Security Center). This deployment objective does not have any dependencies with 2a Setting up M365 XDR and setting up AutoIR, so customers can choose to deploy it in parallel if desired.

Perform these implementation steps to set up Microsoft Defender for Cloud.

NEEDED BY CONTRIBUTORS:

| Done | Implementation step | Owner | Documentation |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> | 1.  | Security Architect | link |
| <input type="checkbox" /> | 2.  | Security Architect | link |
| <input type="checkbox" /> | 3.  | Security Architect | link |
| <input type="checkbox" /> | 4.  | Security Architect | link |


## Next step

Continue to modernize your security operations for Zero Trust with [Step 5. Unify visibility](modernize-security-operations-unify-visibility.md).
