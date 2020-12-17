---
title: Enhanced Security Admin Environment (ESAE) architecture retirement
description: Retiring the red forest as a legacy security mechanism

ms.service: security
ms.subservice: 
ms.topic: conceptual
ms.date: 12/15/2020

ms.author: joflore
author: MicrosoftGuyJFlo
manager: daveba
ms.reviewer: mas
---
# ESAE Retirement

The Enhanced Security Admin Environment (ESAE) architecture (often referred to as red forest, admin forest, or hardened forest) is a legacy on-premises approach to providing a secure workstation for Active Directory administrators that has been retired from mainstream Microsoft recommendations.

![Retirement of ESAE notification](./media/esae-retirement/retirement.png)

ESAE guidance has been replaced by the modern [privileged access strategy](privileged-access-strategy.md) and [rapid modernization plan (RAMP)](security-rapid-modernization-plan.md) guidance for providing secure workstations for privileged users. On-premises administrative Windows Server Active Directory forests are no longer recommended for protecting assets.

![PLACEHOLDER](./media/esae-retirement/defender-vs-attacker-cost.png)

We have found that ESAE projects are often detrimental to overall security posture as they are high cost, difficult to use and support, and provide a limited set of security (only Active Directory administrators and only preventive controls). The privileged access strategy provides a more complete set of protections and monitoring for a much larger set of sensitive users, while providing incremental lower-cost steps to rapidly build security assurances.

This architectural approach may be used in a custom architecture for isolated environments where internet access is removed, but is not recommended for any environments where cloud services can be made available. The few cases where this architecture provides value that may justify the investment are when this configuration is required by regulation, or in high impact isolated environments like offline research laboratories and disconnected operational technology (OT) / supervisory control and data acquisition (SCADA) environments. 

> [!NOTE] 
> While Microsoft no longer recommends an isolated administrative forest model for most scenarios at most organizations, Microsoft still operates a similar architecture internally (and associated support processes and personnel) because of the extreme security requirements for providing trusted cloud services to organizations around the globe. 
