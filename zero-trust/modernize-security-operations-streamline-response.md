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

<!--

--> 


Meet these deployment objectives to streamline your SecOps for Zero Trust.

| Done | Deployment objective | Owner |
|:-------|:-------|:-----|
| <input type="checkbox" /> | [1. Use minimal number of alert queues](#singlequeue) | Security Architect |
| <input type="checkbox" /> | [2a. (in parallel with step 2b) Set up Microsoft 365 Defender](#m365xdr) | Security Engineer |
| <input type="checkbox" /> | [2b. (in parallel with step 2b) Set up Microsoft Defender for Cloud](#azurexdr) | Security Engineer |

<a id="singlequeue"></a>
### 1. Use minimal number of alert queues

<!--
This section is not about technical deployment for a specific product. It’s guidance on a best practice to ensure analysts / SOC can look at a single tool for alert and response. We know that this guidance unfortunately conflicts with our own offerings as we have an XDR for M365 and another different one for Cloud/Azure, but for customers who have SIEM, they may be able to unify it with this as a long-term strategy.)
--> 


intro text

Perform these implementation steps to meet minimize the number of alert queues.

| Done | Implementation objective and results | Owner | Documentation |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> | 1. . | Security Architect | [link](URL) |
| <input type="checkbox" /> | 2. . | Security Architect | [link](URL) |
| <input type="checkbox" /> | 3. . | Security Architect | [link](URL) |
| <input type="checkbox" /> | 4. . | Security Architect | [link](URL) |


<a id="m365xdr"></a>
### 2a. (in parallel with step 2b) Set up Microsoft 365 Defender

<!--
This section will contain the deployment objectives and technical deployment instructions for Microsoft 365 Defender (previously Microsoft Threat Protection). It should include Endpoint, Email (O365), and Identity.

This section has a dependency on the 1.2 Setting up M365 XDR and works as a “level up” in maturity. This section will contain the deployment objectives and technical deployment instructions for the “Automated investigation and response” feature in Microsoft 365 Defender
--> 

intro text

Perform these implementation steps to set up Microsoft 365 Defender.

| Done | Implementation objective and results | Owner | Documentation |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> | 1. . | Security Architect | [link](URL) |
| <input type="checkbox" /> | 2. . | Security Architect | [link](URL) |
| <input type="checkbox" /> | 3. . | Security Architect | [link](URL) |
| <input type="checkbox" /> | 4. . | Security Architect | [link](URL) |


<a id="azurexdr"></a>
### 2b. (in parallel with step 2b) Set up Microsoft Defender for Cloud

<!--
This section will contain the deployment objectives and technical deployment instructions for Azure Defender (previously Azure Security Center). This deployment objective does not have any dependencies with 1.2 Setting up M365 XDR or 1.3 Setting up AutoIR, so customers can choose to deploy it in parallel if desired.
--> 

intro text

Perform these implementation steps to set up Microsoft Defender for Cloud.

| Done | Implementation objective and results | Owner | Documentation |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> | 1. . | Security Architect | [link](URL) |
| <input type="checkbox" /> | 2. . | Security Architect | [link](URL) |
| <input type="checkbox" /> | 3. . | Security Architect | [link](URL) |
| <input type="checkbox" /> | 4. . | Security Architect | [link](URL) |


## Next step

Continue to modernize your security operations for Zero Trust with [Step 5. Unify visibility](modernize-security-operations-unify-visibility.md).
