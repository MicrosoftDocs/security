---
title: Step 5. Unify visibility
description: Modernize security operations - Step 4. Unify visibility 
ms.service: security
ms.author: josephd
author: JoeDavies-MSFT
manager: dansimp
ms.topic: conceptual
---

# Step 5. Unify visibility

NOTE TO REVIEWERS: This article is in progress and not ready for technical review.

While it’s difficult to create a high-quality individual alerts from raw data in security information and event management (SIEM) solutions, they are extraordinarily useful for bringing all the data and context together for investigations and for threat hunting, allowing for a broad view across your entire estate, reducing blind spots where attackers may dwell.

## Program and project member accountabilities

This table describes the implementation of a central SIEM alaysis in terms of a sponsorship/program management/project management hierarchy to determine and drive results.

| Lead | Owner | Accountability |
|:-------|:-------|:-----|
|  CISO, CIO, or Director of Identity Security | | Executive sponsorship |
| Program lead from SecOps Leadership| | Drive results and cross-team collaboration |
| | Security Architect  | Advise on configuration and standards |
| | SecOps Analysts | Implement configuration changes |
| | SecOps Analysts | Update standards and policy documents |
| | Security Governance | Monitor to ensure compliance |

## Deployment objectives

Meet these deployment objectives to unify visibility in your SecOps for Zero Trust.

<!--
NOTES: Setting up SIEM:  This section will contain the deployment objectives and technical deployment instructions for Microsoft Sentinel (previously Microsoft Sentinel). This step “levels up” in maturity from XDR, as now we can gather events from multiple sources and contextualize / cross-reference them.
--> 

| Done | Deployment objective | Owner | Documentation |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> | 1. Create security operations use cases. | Security Architect |  |
| <input type="checkbox" /> | 2. Determine log sources to fulfil visibility use cases. | Security Architect |  |
| <input type="checkbox" /> | 3. Design workspace architecture. | Security Architect | [Design your Microsoft Sentinel workspace architecture](https://docs.microsoft.com/azure/sentinel/design-your-workspace-architecture) |
| <input type="checkbox" /> | 4. Plan and estimate costs. | Security Architect | [Plan and manage costs for Microsoft Sentinel](https://docs.microsoft.com/azure/sentinel/billing) |
| <input type="checkbox" /> | 5. Design and implement RBAC for Microsoft Sentinel. | Security Architect | [Manage access to Microsoft Sentinel data by resource](https://docs.microsoft.com/azure/sentinel/resource-context-rbac) |
| <input type="checkbox" /> | 6. Collect data into Microsoft Sentinel. | Security Architect | [Find your Microsoft Sentinel data connector](https://docs.microsoft.com/azure/sentinel/data-connectors-reference) |
| <input type="checkbox" /> | 7. Normalize data within Microsoft Sentinel. | Security Architect | [Develop Microsoft Sentinel Advanced SIEM Information Model (ASIM) parsers](https://docs.microsoft.com/azure/sentinel/normalization-develop-parsers) |
| <input type="checkbox" /> | 8. Configure detection rules based on use cases. | Security Architect | [Create custom analytics rules to detect threats with Microsoft Sentinel](https://docs.microsoft.com/azure/sentinel/detect-threats-custom) |
| <input type="checkbox" /> | 9. Visualize and monitor data. | SecOps Analysts | [Visualize collected data](https://docs.microsoft.com/azure/sentinel/get-visibility) |

<!--
## 1. Deployment objective placeholder section

NEEDED BY CONTRIBUTORS FOR EACH DEPLOYMENT OBJECTIVE:

Perform these implementation steps to realize the deployment objective.

| Done | Implementation step | Owner | Documentation |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> | 1.  | Security Architect/other | link |
| <input type="checkbox" /> | 2.  | Security Architect/other | link |
| <input type="checkbox" /> | 3.  | Security Architect/other | link |
| <input type="checkbox" /> | 4.  | Security Architect/other | link |


--> 

## Next step

Complete to modernize your security operations for Zero Trust with [Step 6. Reduce manual effort](modernize-security-operations-reduce-manual-effort.md).
