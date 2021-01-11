---
title: Enhanced Security Admin Environment (ESAE) architecture mainstream retirement
description: Retiring the red forest as a legacy security mechanism

ms.service: security
ms.subservice: 
ms.topic: conceptual
ms.date: 01/11/2021

ms.author: joflore
author: MicrosoftGuyJFlo
manager: daveba
ms.reviewer: mas
---
# Enhanced Security Admin Environment

The Enhanced Security Admin Environment (ESAE) architecture (often referred to as red forest, admin forest, or hardened forest) is an on-premises approach to provide a secure environment for Windows Server Active Directory (AD) administrators.

ESAE guidance has been replaced by the modern [privileged access strategy](privileged-access-strategy.md) and [rapid modernization plan (RAMP)](security-rapid-modernization-plan.md) guidance as the default recommended approach for securing privileged users. The ESAE administrative forest pattern is now considered a custom configuration suitable only for exception cases listed below.

## What if I already have ESAE?

For customers that have already deployed this architecture, there is no urgency to retire or replace an ESAE implementation if it's being operated as designed and intended. As with any enterprise systems, you should maintain the software in it by applying security updates and ensuring software is within [support lifecycle](https://docs.microsoft.com/lifecycle/).

Because of the limited role coverage, Microsoft also recommends organizations with ESAE also adopt the modern [privileged access strategy](privileged-access-strategy.md) using the [rapid modernization plan (RAMP)](security-rapid-modernization-plan.md) guidance. This complements the existing ESAE implementation and provides appropriate security for roles not already protected by ESAE including Azure AD Global Administrators, sensitive business users, and standard enterprise users. For more information, see the article [Securing privileged access security levels](privileged-access-security-levels.md).

## Why change the recommendation?

Microsoft has changed this guidance because cloud-based solutions can be deployed quicker to protect a broader scope of administrative and business-sensitive roles and systems.

![Defense vs attack cost](./media/esae-retirement/defender-vs-attacker-cost.png)

While still valid for specific use cases, ESAE implementations are more costly and more difficult to use and support compared to the newer cloud-based solution (due to the complex nature of the architecture). ESAE implementations also protect only Windows Server Active Directory administrators. Because of the complexity of the controls in an ESAE implementation, we have also seen instances of ESAE User (domain administrators) intentionally circumventing ESAE protections to get their jobs done efficiently, undermining the original security goal of the architecture. The [privileged access strategy](privileged-access-strategy.md) provides protections and monitoring for a much larger set of sensitive users, while providing incremental lower-cost steps to rapidly build security assurances.

## What are the valid ESAE use cases?

While not a mainstream recommendation, this ESAE architectural pattern is valid in a limited set of scenarios. In all of these exception cases, the organization must accept the increased technical complexity and operational costs of the solution. Additionally, the organization must have a sophisticated security program to measure and monitor risk and also apply consistent operational rigor to the usage and maintenance of the ESAE solution.

Example scenarios include:

- Isolated environments - where cloud services are unavailable such as offline research laboratories, critical infrastructure or utilities, disconnected operational technology (OT) environments such as Supervisory control and data acquisition (SCADA) / Industrial Control Systems (ICS).
- Regulated environment – industry or government regulation may specifically require an administrative forest configuration.
- High level security assurance is mandated - organizations with low risk tolerance that are willing to accept the increased complexity and cost of the solution.

> [!NOTE]
> While Microsoft no longer recommends an isolated administrative forest model for most scenarios at most organizations, Microsoft still operates a similar architecture internally (and associated support processes and personnel) because of the extreme security requirements for providing trusted cloud services to organizations around the globe.

## Next steps

Review the [privileged access strategy](privileged-access-strategy.md) and [rapid modernization plan (RAMP)](security-rapid-modernization-plan.md) guidance for providing secure environments for privileged users.
