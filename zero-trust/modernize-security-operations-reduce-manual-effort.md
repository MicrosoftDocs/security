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

NOTE TO CONTRIBUTORS: Please see the "NEEDED BY CONTRIBUTORS" tags and help flesh out the needed information.

NOTE TO REVIEWERS: This article is in progress and not complete.

At all times, SecOps should be focused on reducing the toil and suffering from manual and repetitive tasks such as switching tools, typing commands, and copying and pasting data. 

Focusing on giving analysts a streamlined end-to-end integrated experience with Security Orchestration, Automation and Response (SOAR) technology will increase both effectiveness and morale. 

SOAR technology is built into both Microsoft 365 Defender and Azure Sentinel.

### Program and project member accountabilities

This table describes a SOAR implementation in terms of a sponsorship/program management/project management hierarchy to determine and drive results.

| Lead | Owner | Accountability |
|:-------|:-------|:-----|
|  CISO, CIO, or Director of Identity Security | | Executive sponsorship |
| Program lead from SecOps Leadership| | Drive results and cross-team collaboration |
| | Security Architect  | Advise on configuration and standards |
| | SecOps Analysts | Implement configuration changes |
| | SecOps Analysts | Update standards and policy documents |
| | Security Governance | Monitor to ensure compliance |

### Deployment objectives

Meet these deployment objectives to reduce manual effort in your SecOps for Zero Trust.

| Done | Deployment objective | Owner |
|:-------|:-------|:-----|
| <input type="checkbox" /> | [1. Implement SOAR](#soar) | Security Architect |
| <input type="checkbox" /> | [2. Operationalize threat hunting](#threathunting) | Security Engineer |
| <input type="checkbox" /> | [3. Enforce Alert Quality](#alertqual) | Security Engineer |

<a id="soar"></a>
### 1. Implement SOAR

NOTES: This section will contain the deployment objectives and technical deployment instructions to automate response to security events.

NEEDED BY CONTRIBUTORS:

Perform these implementation steps to meet minimize the number of alert queues.

| Done | Implementation objective and results | Owner | Documentation |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> | 1. | Security Architect | link |
| <input type="checkbox" /> | 2. | Security Architect | link |
| <input type="checkbox" /> | 3. | Security Architect | link |
| <input type="checkbox" /> | 4. | Security Architect | link |


<a id="threathunting"></a>
### 2. Operationalize threat hunting

NOTES: This section will contain guidance on how to use the threat hunting feature of SIEM and M365 XDR (called Advanced Hunting). We will need to find a clear path on how these two are different from each other, and how to tie them together.

Perform these implementation steps to set up threat hunting for Microsoft 365 Defender and Azure Sentinel.

NEEDED BY CONTRIBUTORS:

| Done | Implementation objective and results | Owner | Documentation |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> | 1. | Security Architect | link |
| <input type="checkbox" /> | 2. | Security Architect | link |
| <input type="checkbox" /> | 3. | Security Architect | link |
| <input type="checkbox" /> | 4. | Security Architect | link |


<a id="alertqual"></a>
### 3. Enforce alert quality

NOTES: In this section, we will discuss how to improve the quality and fidelity of threat hunting findings, with the goal to allow threat hunters to use their time more wisely.

NEEDED BY CONTRIBUTORS:

| Done | Implementation objective and results | Owner | Documentation |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> | 1. | Security Architect | link |
| <input type="checkbox" /> | 2. | Security Architect | link |
| <input type="checkbox" /> | 3. | Security Architect | link |
| <input type="checkbox" /> | 4. | Security Architect | link |


