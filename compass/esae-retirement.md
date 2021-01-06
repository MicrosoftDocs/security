---
title: Enhanced Security Admin Environment (ESAE) architecture retirement
description: Retiring the red forest as a legacy security mechanism

ms.service: security
ms.subservice: 
ms.topic: conceptual
ms.date: 01/06/2021

ms.author: joflore
author: MicrosoftGuyJFlo
manager: daveba
ms.reviewer: mas
---
# ESAE Architecture retirement

The Enhanced Security Admin Environment (ESAE) architecture (often referred to as red forest, admin forest, or hardened forest) is a legacy approach to provide a secure environment for Windows Server Active Directory (AD) administrators. ESAE guidance has been replaced by the modern [privileged access strategy](privileged-access-strategy.md) and [rapid modernization plan (RAMP)](security-rapid-modernization-plan.md) guidance for providing secure environments for privileged users. Administrative Windows Server Active Directory forests are no longer recommended for protecting assets.

![Retirement of ESAE notification](./media/esae-retirement/retirement.png)

This architecture has been retired from mainstream Microsoft recommendation and is now considered a custom configuration either hosted on-premises or with a cloud provider.

![PLACEHOLDER](./media/esae-retirement/defender-vs-attacker-cost.png)

We have found that ESAE projects are often high cost, difficult to use and support, and provide a limited set of security (only Active Directory administrators and only preventive controls). We have also seen a significant number of instances where administrators intentionally circumvent ESAE protections, undermining the original security goal of the architecture. The privileged access strategy provides a more complete set of protections and monitoring for a much larger set of sensitive users, while providing incremental lower-cost steps to rapidly build security assurances.

This architectural approach may be used in a custom architecture for isolated environments where internet access is removed, but is not recommended for any environments where cloud services can be made available. The few cases where this architecture provides value that may justify the investment are when this configuration is required by regulation, or in high impact isolated environments like offline research laboratories and disconnected operational technology (OT) / supervisory control and data acquisition (SCADA) environments.

For customers that have already deployed this architecture, there is no urgency to retire an implementation if it's being operated as designed and intended.

> [!NOTE]
> While Microsoft no longer recommends an isolated administrative forest model for most scenarios at most organizations, Microsoft still operates a similar architecture internally (and associated support processes and personnel) because of the extreme security requirements for providing trusted cloud services to organizations around the globe.
