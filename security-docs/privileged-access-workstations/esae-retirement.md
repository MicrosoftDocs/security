---
title: Enhanced Security Admin Environment (ESAE) architecture mainstream retirement
description: Retiring the red forest as a legacy security mechanism

ms.service: security
ms.subservice: 
ms.topic: conceptual
ms.date: 02/14/2023

ms.author: joflore
author: MicrosoftGuyJFlo
manager: amycolannino
ms.reviewer: mas, caseykahsen
---
# Enhanced Security Admin Environment

The Enhanced Security Admin Environment (ESAE) architecture (often referred to as red forest, admin forest, or hardened forest) is a legacy approach to provide a secure environment for Windows Server Active Directory (AD) administrator identities.

Microsoft’s recommendation to use this architectural pattern has been replaced by the modern [privileged access strategy](privileged-access-strategy.md) and [rapid modernization plan (RAMP)](security-rapid-modernization-plan.md) guidance as the default recommended approach for securing privileged users. This guidance is intended to be inclusive of adapting a broader strategy to move towards a [Zero Trust architecture](/security/zero-trust/zero-trust-overview). Given these modernized strategies, the ESAE hardened administrative forest architecture (on-premises or cloud-based) is now considered a custom configuration suitable only for exception cases.

## Scenarios for Continued Use

Although it's no longer a recommended architecture, ESAE (or individual components therein) can still be valid in a limited set of exempted scenarios. Typically, these on-premises environments are isolated where cloud services may be unavailable. This scenario may include critical infrastructure or other disconnected operational technology (OT) environments. However, it should be noted that air-gapped Industrial Control System/Supervisory Control and Data Acquisition (ICS/SCADA) segments of the environment don't typically utilize their own Active Directory deployment.

If your organization is in one of these scenarios, maintaining a currently deployed ESAE architecture in its entirety can still be valid. However, it must be understood that your organization incurs extra risk due to the increased technical complexity and operational costs of maintaining ESAE. Microsoft recommends that any organization still using ESAE, or other legacy identity security controls, apply extra rigor to monitor, identify, and mitigate any associated risks.

> [!NOTE]
> While Microsoft no longer recommends an isolated hardened forest model for most scenarios at most organizations, Microsoft still operates a similar architecture internally (and associated support processes and personnel) because of the extreme security requirements for providing trusted cloud services to organizations around the globe.

## Guidance for Existing Deployments

For customers that have already deployed this architecture to enhance security and/or simplify multi-forest management, there's no urgency to retire or replace an ESAE implementation if it's being operated as designed and intended. As with any enterprise systems, you should maintain the software in it by applying security updates and ensuring software is within [support lifecycle](/lifecycle/).

Microsoft also recommends organizations with ESAE / hardened forests adopt the modern [privileged access strategy](/security/compass/privileged-access-strategy) using the [rapid modernization plan (RAMP)](/security/compass/security-rapid-modernization-plan) guidance. This guidance complements an existing ESAE implementation and provides appropriate security for roles not already protected by ESAE including Microsoft Entra Global Administrators, sensitive business users, and standard enterprise users. For more information, see the article [Securing privileged access security levels](/security/compass/privileged-access-security-levels).

When ESAE was originally designed more than 10 years ago, the focus was on-premises environments with Active Directory (AD) serving as the local identity provider. This legacy approach is based on macro-segmentation techniques to achieve least-privilege and doesn't adequately account for hybrid- or cloud-based environments. Additionally, ESAE and hardened forest implementations focus only on protecting on-premises Windows Server Active Directory administrators (identities) and don't account for fine-grained identity controls and other techniques contained in the remaining pillars of a modern Zero-Trust architecture. Microsoft has updated its recommendation to cloud-based solutions because they can be deployed more quickly to protect a broader scope of administrative and business-sensitive roles and systems. Additionally, they're less complex, scalable, and require less capital investment to maintain.

> [!NOTE]
> Although ESAE is no longer recommended in its entirety, Microsoft realizes that many individual components contained therein are defined as good cyber hygiene (e.g., dedicated Privileged Access Workstations). The deprecation of ESAE is not intended to push organizations to abandon good cyber hygiene practices, only to reinforce updated architectural strategies for protecting privileged identities.

### Examples of good cyber hygiene practices in ESAE that are applicable to most organizations

- Using privileged access workstations (PAWs) for all administrative activities
- Enforcing token-based or multi-factor authentication (MFA) for administrative credentials even if it isn't widely used throughout the environment
- Enforcing Least Privilege Administrative Model through regular assessment of group / role membership (enforced by strong organizational policy)

## Best Practice for Securing on-premises AD

As described in [Scenarios for Continued Use](#scenarios-for-continued-use), there may be circumstances where cloud migration isn't attainable (either partially, or in full) due to varying circumstances. For these organizations, if they don't already have an existing ESAE architecture, Microsoft recommends reducing the attack surface of on-premises AD through increasing the rigor of security for Active Directory and privileged identities. While not an exhaustive list, consider the following high priority recommendations.

- Use a tiered approach implementing least-privilege administrative model:
   - Enforce absolute minimum privileges.
   - Discover, review, and audit privileged identities (strong tie to organizational policy).
      - Excessive privilege granting is one of the most identified issues in assessed environments.
   - MFA for administrative accounts (even if not used widely throughout environment).
   - Time based privileged roles (reduce excessive accounts, reinforce approval processes).
   - Enable and configure all available auditing for privileged identities (notify of enable/disable, password reset, other modifications).
- Use Privileged Access Workstations (PAWs):
   - Don't administer PAWs from a less-trusted host.
   - Use MFA for access to PAWs.
   - Don't forget about physical security.
   - Always ensure PAWs are running the newest and/or currently supported operating systems.
- Understand attack paths and high-risk accounts / applications:
   - Prioritize monitoring of identities and systems that pose the most risk (targets of opportunity / high impact).
   - Eradicate password reuse including across operating system boundaries (common lateral movement technique).
   - Enforce policies restricting activities that increase risk (internet browsing from secured workstations, local administrator accounts across multiple systems, etc.).
   - Reduce applications on Active Directory / Domain Controllers (each added application is extra attack surface).
      - Eliminate unnecessary applications.
      - Move applications still needed to other workloads off of / DC if possible.
- Immutable backup of active directory:
   - Critical component to recovery from ransomware infection.
   - Regular backup schedule.
   - Stored in cloud-based, or off-site location dictated by disaster recovery plan.
- Conduct an [Active Directory Security Assessment](/services-hub/unified/health/getting-started-adsecurity):
   - Azure subscription is required to view the results (customized Log Analytics dashboard).
   - On-demand or Microsoft engineer supported offerings.
   - Validate / identify guidance from the assessment.
   - Microsoft recommends conducting assessments on an annual basis.

For comprehensive guidance on these recommendations, review the [Best Practices for Securing Active Directory](/windows-server/identity/ad-ds/plan/security-best-practices/best-practices-for-securing-active-directory).

## Supplemental Recommendations

Microsoft recognizes that some entities may not be capable of fully deploying a cloud-based zero-trust architecture due to varying constraints. Some of these constraints were mentioned in the previous section. In lieu of a full deployment, organizations can address risk and make progress towards Zero-Trust while still maintaining legacy equipment or architectures in the environment. In addition to the previously mentioned guidance, the following capabilities may aid in bolstering the security of your environment and serve as a starting point towards adopting a Zero-Trust architecture.  

### Microsoft Defender for Identity (MDI)

[Microsoft Defender for Identity (MDI)](/defender-for-identity/what-is) (formally Azure Advanced Threat Protection, or ATP) underpins the Microsoft Zero-Trust architecture and focuses on the pillar of identity. This cloud-based solution uses signals from both on-premises AD and Microsoft Entra ID to identify, detect, and investigate threats involving identities. MDI monitors these signals to identify abnormal and malicious behavior from users and entities. Notably, MDI facilitates the ability to visualize an adversary’s path of lateral movement by highlighting how a given account(s) could be used if compromised. MDI’s behavioral analytics and user baseline features are key elements for determining abnormal activity within your AD environment.

> [!NOTE]
> Although MDI collects signals from on-premises AD it does require a cloud-based connection.  

### Microsoft Defender for Internet of Things (D4IoT)

In addition to other guidance described in this document, organizations operating in one of the above mentioned scenarios could deploy [Microsoft Defender for IoT (D4IoT)](https://azure.microsoft.com/products/iot-defender/#overview). This solution features a passive network sensor (virtual or physical) that enables asset discovery, inventory management, and risk-based behavior analytics for Internet of Things (IoT) and Operational Technology (OT) environments. It can be deployed in on-premises air-gapped or cloud-connected environments and has the capacity to perform deep packet inspection on over 100 ICS/OT proprietary network protocols.

## Next steps

Review the following articles:

1. [Privileged Access Strategy](/security/compass/privileged-access-strategy)
1. [Security Rapid Modernization Plan (RAMP)](/security/compass/security-rapid-modernization-plan)
1. [Best Practices for Securing Active Directory](/windows-server/identity/ad-ds/plan/security-best-practices/best-practices-for-securing-active-directory)
