---
title: Phase 3-Enforce privileged access policies
description: Learn how to configure Conditional Access to control privileged access
ms.date: 05/05/2025
ms.service: security
author: rayne-wiselman
ms.author: raynew
ms.subservice: zero-trust
ms.topic: conceptual
ms.collection: 
  - zerotrust-adopt
ms.custom: sfi-image-nochange
---


# Phase 3 - Enforce privileged access policies

Privileged access is the highest-impact security risk in most organizations because it enables direct control over identity systems, cloud control planes, and business-critical assets.

This article is part of the [Implement a privileged access architecture](implement-privileged-access.md) solution guide, which provides phased implementation guidance aligned to the [privileged access business scenario](security-adoption-discipline-identity-access-privileged-model.md).

This article describes Phase 3 of the implementation. It enforces privileged access policy to restrict where privileged identities can be used. 

Using the trusted device signals established in Phase 2, you configure Conditional Access so privileged roles, portals, and management interfaces can be used only from approved, low-risk PAWs.

## Protection goals

Phase 3 enforces the following protection goals:

- Ensure privileged credentials can't be used from non-PAW devices.
- Admin portals and interfaces are only reachable from compliant, low-risk devices.
- Privileged access requires strong user authenticatin and verified device trust.
- Restrict access to administrative interfaces (portals, APIs, PowerShell) to approved PAWs
- Stolen credentials cannot be reused from standard or unmanaged endpoints.
- Privileged access paths are explicit, auditable, and enforceable.

## Protection scope

Phase 3 protects privileged access interfaces and workflows through which privileged actions occur, including:

- Cloud management portals (Azure portal, Microsoft Entra admin center, Microsoft 365 admin center)
- Security management portals (Microsoft Defender portals)
- Privileged role usage and activation (including PIM-controlled roles)
- Administrative browser sessions
- Network egress paths used by privileged devices

Phase 3 doesn't reconfigure devices or identities. It enforces policy using the outputs of Phases 1 and 2.

## Risks mitigated


| **Risk** | **Why it matters** | **Phase 3 mitigation** |
|------|----------------|--------------------|
| **Privileged credentials reused from non‑PAW devices** | MFA and approvals do not prevent attackers from reusing stolen tokens or credentials on compromised standard workstations | Conditional Access requires privileged roles to authenticate from compliant, low‑risk PAWs only |
| **Privileged access from high‑risk or unpatched devices** | A vulnerable device allows attackers to immediately exercise administrative control | Access decisions evaluate Intune compliance and Microsoft Defender for Endpoint risk level before granting privileged access |
| **Administrative portals accessible** from unmanaged or BYOD devices | Cloud control planes become reachable from devices outside organizational control | Conditional Access restricts administrative portals to PAWs, blocking access from non‑PAW devices |
| **Bypass of protected portals using alternate interfaces** | Attackers can avoid controls by using PowerShell, APIs, or alternative admin endpoints | Enforcement applies consistently across administrative interfaces, not just primary portals |
| **Privileged role activation from compromised workstations** | Approval workflows can be hijacked if role activation occurs on an unsafe device | PIM role activation and role usage are enforced through the same Conditional Access device trust requirements |
| **Credentials alone grant privileged access** | Identity‑only protections assume a trustworthy execution environment | Phase 3 binds identity, device, and interface conditions so credentials alone are insufficient |
| **Lack of visibility into enforcement** | Without policy enforcement, it’s difficult to prove privileged access is constrained | Conditional Access decisions and Defender telemetry provide auditable, observable enforcement evidence |
| **Rapid escalation after workstation compromise** | Attackers pivot quickly from a compromised device to enterprise‑wide control | Phase 3 ensures stolen credentials are unusable outside PAWs, breaking common escalation paths |



## Phase outcomes

After completing Phase 3:

- Privileged roles and admin portals are only accessible from compliant, low‑risk PAWs
- Conditional Access blocks privileged access from non‑PAW devices
- Device compliance and Microsoft Defender for Endpoint risk signals are required inputs to access decisions
- Privileged access is enforced across identity, device, and interface layers
- Access attempts are logged, observable, and auditable


## Prerequisites

Before configuring procedures in this article:

- Complete [Phase 1 instructions](implement-privileged-access-identity.md) to secure the identity control plan.
- Complete [Phase 2](implement-privileged-access-devices.md) to deploy and harden PAWs.
- MAke sure that device compliance and Defender for Endpoint integration is active.

## Step 1 — Require MFA and device trust for privileged access

Ensure privileged access requires strong user authentication and trusted devices

1. In the [Microsoft Entra Admin Center](https://entra.microsoft.com), navigate to **Protection** > **Conditional Access** > **Policies**.
1. Select **Create new policy**. 
1. In **Assigments** > **Users** configure these settings:
    - Include privileged directory roles such as Global Administrator, Security Administrator.
    - Exclude the emergency breakglass group.
1. In **Assigments** > **Cloud apps** include cloud management applications such as the Azure portal, Entra admin center, Microsoft 365 admin center, and Defender portals.
1. In **Access controls**, grant access with these settings:
    - Require multi‑factor authentication
    - Require device to be marked as compliant
    - Require Microsoft Defender for Endpoint device risk = Low
1. Enable the policy.

## Step 2 - Restrict administrative portals to PAWs

Ensure that administrative portals are reachable only from compliant PAWs.

1. In the [Microsoft Entra Admin Center](https://entra.microsoft.com), navigate to **Protection** > **Conditional Access** > **Policies**.
1. Select **Create new policy** to create an additional policy.
1. In **Assigments** > **Users** configure these settings:
    - Include privileged directory roles such as Global Administrator, Security Administrator.
    - Exclude the emergency breakglass group.
1. In **Assigments** > **Cloud apps** include administrative portals and management interfaces.
1. In **Access controls**, grant access with these settings:
    - Require device to be marked as compliant
    - Require Microsoft Defender for Endpoint device risk = Low
1. Enable the policy.


## Step 3 - Block privileged access from non-PAW devices

Ensure that even compliant non‑PAW devices can't be used for privileged access.

1. In the [Microsoft Entra Admin Center](https://entra.microsoft.com), navigate to **Protection** > **Conditional Access** > **Policies**.
1. Select **Create new policy** to create a third policy.
1. In **Assigments** > **Users** configure these settings:
    - Include privileged directory roles such as Global Administrator, Security Administrator.
    - Exclude the emergency breakglass group.
1. In **Assigments** > **Cloud apps** include the same administrative portals.
1. In **Access controls**, select **Block access**.


## Step 4 - Enforce firewall-based network restriction for PAWs

Limit PAW network access to required administrative endpoints.

1. In the Microsoft Intune admin center, navigate to **Endpoint security** > **Firewall**.
2. Create an **Endpoint Protection** profile.
1. Configure **Firewall behavior (Privileged profile)**:
    - **Inbound traffic**: Block
    - **Outbound traffic**: Block except DNS, DHCP, NTP, HTTP/HTTPS, and required Microsoft cloud management endpoints.
1. Assign the profile to **Secure Workstation Devices**.

This completes the privileged access enforcement layer.
The next article can build on this to cover measurement, monitoring, and success criteria.

## Next steps

With the privileged access enforcement layer in place, the final step is to [configure monitoring](implement-privileged-access-monitor.md).