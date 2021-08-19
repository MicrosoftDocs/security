---
title: Step 1. Explicitly validate trust for all access requests
description: Explicitly validate trust for all access requests 
ms.service: security
author: garycentric
ms.author: v-gmoor
ms.topic: conceptual
---

# Step 1. Explicitly validate trust for all access requests

This step includes using Zero Trust to explicitly validate trust for all access requests for:

- User Accounts

  Require Passwordless or MFA for all users + measure risk with threat intelligence & behavior analytics

- Devices

  Require device integrity for access (configuration compliance first, then XDR signals)


## User accounts

description

### Program and project member accountabilities

This table describes the overall protection of your user accounts in terms of a sponsorship/program management/project management hierarchy to determine and drive results.

| Lead | Implementor | Accountability |
|:-------|:-------|:-----|
| [Central IT](/azure/cloud-adoption-framework/organize/central-it) Operations or CIO | | Executive sponsorship |
| Program lead from [Central IT](/azure/cloud-adoption-framework/organize/central-it) infrastructure | | Drive results and cross-team collaboration |
|  | [Security Architecture](/azure/cloud-adoption-framework/organize/cloud-security-architecture)  | Advise on configuration and standards |
| | [Security Policy and Standards](/azure/cloud-adoption-framework/organize/cloud-security-policy-standards) | Update standards and policy documents |
| | [Security Compliance Management](/azure/cloud-adoption-framework/organize/cloud-security-compliance-management) | Monitor to ensure compliance |
|  |  |  |

### Deployment objectives

Meet these deployment objectives to protect your accounts with Zero Trust.

| Done| Deplyment objective | Description | Documentation |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> | Self-service password reset (SSPR) | Gives you credential reset capabilities | link |
| <input type="checkbox" /> | Multi-Factor Authentication (MFA) |Has been enabled and appropriate methods for MFA have been selected | link |
| <input type="checkbox" /> | Combined User Registration | Has been enabled for your directory, allows users to register for SSPR and MFA in one step | link |


Accountability – the “Who” is here

## Devices	

description

### Program and project member accountabilities

This table describes the overall protection of your devices in terms of a sponsorship/program management/project management hierarchy to determine and drive results.

| Lead | Implementor | Accountability |
|:-------|:-------|:-----|
| [Central IT](/azure/cloud-adoption-framework/organize/central-it) Operations or CIO | | Executive sponsorship |
| Program lead from [Central IT](/azure/cloud-adoption-framework/organize/central-it) infrastructure | | Drive results and cross-team collaboration |
|  | [Security Architecture](/azure/cloud-adoption-framework/organize/cloud-security-architecture)  | Advise on configuration and standards |
| | [Security Policy and Standards](/azure/cloud-adoption-framework/organize/cloud-security-policy-standards) | Update standards and policy documents |
| | [Security Compliance Management](/azure/cloud-adoption-framework/organize/cloud-security-compliance-management) | Monitor to ensure compliance |
|  |  |  |

### Deployment objectives

Meet these deployment objectives to protect your devices with Zero Trust.

| Done| Deplyment objective | Description | Documentation |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> |  |  | link |
| <input type="checkbox" /> |  |  | link |
| <input type="checkbox" /> |  |  | link |
| <input type="checkbox" /> |  |  | link |

