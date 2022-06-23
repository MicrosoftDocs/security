---
title: Securing privileged access overview
description: How can organizations secure privileged with Azure resources?

ms.service: security
ms.subservice: 
ms.topic: overview
ms.date: 12/15/2020

ms.author: joflore
author: MicrosoftGuyJFlo
manager: daveba
ms.reviewer: mas
---
# Securing privileged access

Organization's should make securing privileged access the top security priority because of the significant potential business impact (and high likelihood) of attackers compromising this level of access.

Privileged access includes IT administrators with control of large portions of the enterprise estate and other users with access to business critical assets. 

Attackers frequently exploit weaknesses in privileged access security during [human operated ransomware attacks](https://www.microsoft.com/security/blog/2020/03/05/human-operated-ransomware-attacks-a-preventable-disaster/) and targeted data theft. Privileged access accounts and workstations are so attractive to attackers because these targets allow them to rapidly gain broad access to the business assets in the enterprise, often resulting in rapid and significant business impact.

The following diagram summarizes the recommended privileged access strategy to create an isolated virtual zone that these sensitive accounts can operate in with low risk. 

![An end to end approach is required for meaningful security](./media/overview/end-to-end-approach.png)

Securing privileged access effectively seals off unauthorized pathways completely and leaves a select few authorized access pathways that are protected and closely monitored. This diagram is discussed in more detail in the article, [Privileged Access Strategy](privileged-access-strategy.md).

Building this strategy requires a holistic approach combining multiple technologies to protect and monitor those authorized escalation paths using Zero Trust principles including explicit validation, least privilege, and assume breach. This strategy requires multiple complementary initiatives that establish a holistic technology approach, clear processes, and rigorous operational execution to build and sustain assurances over time. 

## Get started and measure progress

| Image | Description | Image | Description |
| --- | --- | --- | --- |
| ![Rapid Modernization Plan](./media/overview/ramp.png) | [Rapid Modernization Plan (RaMP)](security-rapid-modernization-plan.md) <br/> - Plan and implement the most impactful quick wins | ![Best practices checklist](./media/overview/checklist.png) | [Best practices](/security/compass/critical-impact-accounts) <br/> [Videos and Slides](/security/compass/administration-videos-and-decks) |

## Industry references

Securing privileged access is also addresses by these industry standards and best practices.

| [UK National Cyber Security Center (NCSC)](https://www.ncsc.gov.uk/collection/secure-system-administration) | [Australian Cyber Security Center (ACSC)](https://www.cyber.gov.au/acsc/view-all-content/publications/secure-administration) | [MITRE ATT&CK](https://attack.mitre.org/mitigations/M1026/) |
| --- | --- | --- |

## Next steps

Strategy, design, and implementation resources to help you rapidly secure privileged access for your environment.

| Image | Article | Description |
| :---: | --- | --- |
| ![Strategy doc](./media/overview/strategy.png) | [Strategy](privileged-access-strategy.md) | Overview of privileged access strategy |
| ![Success criteria doc](./media/overview/success.png) | [Success criteria](privileged-access-success-criteria.md) | Strategic success criteria |
| ![Security levels doc](./media/overview/security-levels.png) | [Security levels](privileged-access-security-levels.md) | Overview of security levels for accounts, devices, intermediaries, and interfaces |
| ![Account doc](./media/overview/accounts.png) | [Accounts](privileged-access-accounts.md) | Guidance on security levels and controls for accounts |
| ![Intermediaries doc](./media/overview/intermediaries.png) | [Intermediaries](privileged-access-intermediaries.md) | Guidance on security levels and controls for intermediaries |
| ![Interfaces doc](./media/overview/interfaces.png) | [Interfaces](privileged-access-interfaces.md) | Guidance on security levels and controls for interfaces |
| ![Devices doc](./media/overview/devices.png) | [Devices](privileged-access-devices.md) | Guidance on security levels and controls for devices and workstations |
| ![Enterprise access model doc](./media/overview/access-model.png) | [Enterprise access model](privileged-access-access-model.md) | Overview of Enterprise Access Model (successor to legacy tier model) |
| ![Retiring ESAE doc](./media/overview/esae-retirement.png) | [ESAE Retirement](esae-retirement.md) | Information on retirement of legacy administrative forest |
