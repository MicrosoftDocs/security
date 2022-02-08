---
title: Step 6. Reduce manual effort
description: Modernize security operations - Step 5. Reduce manual effort
ms.service: security
ms.author: josephd
author: JoeDavies-MSFT
manager: dansimp
ms.topic: conceptual
---

# Step 6. Reduce manual effort

NOTE TO REVIEWERS: This article is in progress and not complete.

At all times, SecOps should be focused on reducing the toil and suffering from manual and repetitive tasks such as switching tools, typing commands, and copying and pasting data. 

Focusing on giving analysts a streamlined end-to-end integrated experience with Security Orchestration, Automation and Response (SOAR) technology will increase both effectiveness and morale. 

SOAR technology is built into both Microsoft 365 Defender and Microsoft Sentinel.

## Program and project member accountabilities

This table describes a SOAR implementation in terms of a sponsorship/program management/project management hierarchy to determine and drive results.

| Lead | Owner | Accountability |
|:-------|:-------|:-----|
|  CISO, CIO, or Director of Identity Security | | Executive sponsorship |
| Program lead from SecOps Leadership| | Drive results and cross-team collaboration |
| | Security Architect  | Advise on configuration and standards |
| | SecOps Analysts | Implement configuration changes |
| | SecOps Analysts | Update standards and policy documents |
| | Security Governance | Monitor to ensure compliance |

## Deployment objectives

Meet these deployment objectives to reduce manual effort in your SecOps for Zero Trust.

| Done | Deployment objective | Owner |
|:-------|:-------|:-----|
| <input type="checkbox" /> | [1. Implement SOAR](#soar). | Security Architect |
| <input type="checkbox" /> | [2. Operationalize threat hunting](#threathunting). | Security Engineer |
| <input type="checkbox" /> | [3. Enforce Alert Quality](#alertqual). | Security Engineer |

<a id="soar"></a>
## 1. Implement SOAR

Perform these implementation steps to meet minimize the number of alert queues.

| Done | Implementation step | Owner | Documentation |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> | 1. Automate incident handling in Microsoft Sentinel with automation rules. | Security Architect | [Automate incident handling in Microsoft Sentinel](https://docs.microsoft.com/azure/sentinel/automate-incident-handling-with-automation-rules) |
| <input type="checkbox" /> | 2. Automate threat response with playbooks in Microsoft Sentinel. | Security Architect | [Automate threat response with playbooks in Microsoft Sentinel](https://docs.microsoft.com/azure/sentinel/automate-responses-with-playbooks) |


<a id="threathunting"></a>
## 2. Operationalize threat hunting

<!--
NOTES FROM THE OUTLINE: This section will contain guidance on how to use the threat hunting feature of SIEM and M365 XDR (called Advanced Hunting). We will need to find a clear path on how these two are different from each other, and how to tie them together.
--> 

The enormous number of security signals that your various systems and security appliances generate can be difficult to parse and filter into meaningful events. To proactively look for security threats in this mountain of content, Azure Sentinel and Microsoft 365 Defender support advanced hunting.

Advanced hunting is a query-based threat hunting tool that lets you explore and inspect events in your network to locate threat indicators and entities. This flexible and customizable analysis tool enables unconstrained hunting for both known and potential threats.

Microsoft Sentinel supports built-in queries, a hunting dashboard, and custom queries. Microsoft 365 Defender supports custom queries that can also be used to create custom detection rules.

Perform these implementation steps to set up threat hunting for Microsoft 365 Defender.

| Done | Implementation step | Owner | Documentation |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> | 1. Ramp up SecOps staff on Microsoft 365 Defender advanced hunting (Kusto language, schema, query training and practice). | SecOps manager | [Get started](https://docs.microsoft.com/microsoft-365/security/defender/advanced-hunting-overview#get-started-with-advanced-hunting) |
| <input type="checkbox" /> | 2. Assemble a catalog of advanced hunting queries for identity, endpoint, apps, data, and ransomware attacks. | Security Analysts | [Threat analytics reports](https://security.microsoft.com/threatanalytics), [GitHub](https://github.com/microsoft/Microsoft-365-Defender-Hunting-Queries), [ransomware](https://docs.microsoft.com/microsoft-365/security/defender/advanced-hunting-find-ransomware) |
| <input type="checkbox" /> | 3. Create custom detection rules for advanced hunting queries. | Security Analysts | [Custom detection rules](https://docs.microsoft.com/microsoft-365/security/defender/custom-detection-rules) |
| <input type="checkbox" /> | 4. Determine the set of operational tasks, such as running daily/weekly/monthly advanced hunting queries and updating queries and custom detection rules. | SecOps Manager | [SOC maintenance tasks](https://docs.microsoft.com/microsoft-365/security/defender/integrate-microsoft-365-defender-secops-tasks) |

Perform these implementation steps to set up threat hunting for Microsoft Sentinel.

| Done | Implementation step | Owner | Documentation |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> | 1. | Security Architect | [Advanced KQL Framework Workbook](https://techcommunity.microsoft.com/t5/microsoft-sentinel-blog/advanced-kql-framework-workbook-empowering-you-to-become-kql/ba-p/3033766) |
| <input type="checkbox" /> | 2. Review built-in hunting queries and create custom hunting queries based on organizational risk tolerance and security posture. | Security Architect | [Hunting capabilities in Microsoft Sentinel](https://docs.microsoft.com/azure/sentinel/hunting) |
| <input type="checkbox" /> | 3. Build proactive threat hunting activities into SOC operational processes using the hunting dashboard. | SecOps Manager/Security Architect | [Hunting capabilities in Microsoft Sentinel](https://docs.microsoft.com/azure/sentinel/hunting) |
| <input type="checkbox" /> | 4. Create hunting Livestreams to baseline activities in your environment. | Security Architect | [Use hunting Livestream in Microsoft Sentinel to detect threats](https://docs.microsoft.com/azure/sentinel/livestream) |
| <input type="checkbox" /> | 5. Use Notebooks for larger, more complex hunting investigations. | Security Analysts | [Hunting capabilities in Microsoft Sentinel](https://docs.microsoft.com/azure/sentinel/hunting) <BR><BR> [Azure Sentinel notebook ninja - the series!](https://techcommunity.microsoft.com/t5/microsoft-sentinel-blog/becoming-a-microsoft-sentinel-notebooks-ninja-the-series/ba-p/2693491) <BR><BR> [Use notebooks with Microsoft Sentinel for security hunting](https://docs.microsoft.com/azure/sentinel/notebooks?tabs=public-endpoint) |

<a id="alertqual"></a>
## 3. Enforce alert quality

<!--
NOTES FROM THE OUTLINE: In this section, we will discuss how to improve the quality and fidelity of threat hunting findings, with the goal to allow threat hunters to use their time more wisely.
--> 

After SOAR and threat hunting is in place, you need to operationalize the ongoing learning of:

- What threat hunting queries and capabilities are the most effective at finding threats.
- How threat hunting queries and capabilities can be improved to:

   - Be more efficient to finding active threats.

   - Be tuned to find new types of threats.

   - Discover and classify false positive alerts.

Over time, your threat hunting queries can become finely tuned for your organization and the set of threats it typically faces, reducing your overall mean time to resolve (MTTR).

Additionally, you can develop internal playbooks to more quickly go from threat hunting results to assignment of true positive alerts and incidents to Tier 2 security analysts for investigation, containment, and recovery.

