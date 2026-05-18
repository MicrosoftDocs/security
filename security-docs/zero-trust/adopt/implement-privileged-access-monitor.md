---
title: Phase 4 - Monitor privileged access
description: Learn how to monitor privileged access and protect against threats
ms.date: 05/05/2025
ms.service: security
author: rayne-wiselman
ms.author: raynew
ms.subservice: zero-trust
ms.topic: conceptual
ms.collection: 
---




# Phase 4 - Monitor and protect privileged access against threats

This article is part of the [Implement a privileged access architecture](implement-privileged-access.md) solution guide. 

Privileged access presents a critical security risk in most organizations because it enables direct control over identity systems, cloud control planes, and business‑critical assets.

Learn how a [secure privileged access architecture](../security-adoption-scenario-privileged-access.md) plays a critical role in your business scenario - *[Protect critical business assets](../security-adoption-scenario-secure-assets.md)* - by reducing this risk and strengthening control over sensitive systems.

This article describes Phase 4, which establishes monitoring and response for privileged access. It focuses on detecting compromise attempts, validating ongoing compliance and enforcement, and enabling rapid containment when indicators of attack or misconfiguration appear.

This phase operationalizes Zero Trust's assume breach principle by continuously monitoring device behavior, application execution, and privileged workflows, and by enabling rapid response when indicators of attack or misconfiguration appear.



## Protection goals

Phase 4 is designed to:

- Detect compromise of PAWs.
- Detect misuse of privileged devices and identities.
- Detect drift that weakens device signals.
- Enable rapid containment before blast radius.
- Provide evidence that privileged access controls are working as designed.

## Protection scope

Phase 4 monitors the same privileged access elements enforced earlier:

- **Privileged devices**: Monitor PAWs for:
    - Defender for Endpoint risk level changes.
    - Vulnerabilities and misconfigurations.
    - Integrity issues and configuration drift (Intune compliance).
- **Privileged workflows**: Monitor for:
    - Role activation and admin portal usage (correlation of Entra sign-in logs, conditional access decisions, and PIM usage)
    - Application execution related to PAWs:
        - AppLocker telemetry on PAWs is monitored using Defender for Endpoint.
        - The goal is detecting unexpected execution on privileged devices.
    - Network behavior. PAW firewall posture, outbound attempts, and Defender telemetry are monitored to detect abuse or misconfiguration.
- **Privileged access paths**: Monitor interfaces and execution paths attackers would abuse after credential theft.
    - Interfaces (admin portals, APIs, PowerShell)
    - Access paths enforced by conditional access.
    - Abuse detection after credential theft.


## Risks mitigated

**Risk** | **Why it matters** | **Phase 4 mitigation**
--- | --- | ---
**Undetected PAW compromise** | A compromised PAW undermines the entire privileged access strategy by becoming a trusted launch point for attacker activity. | Microsoft Defender for Endpoint continuously monitors PAWs for malware, exploit behavior, and persistence techniques; changes in device risk are surfaced immediately for investigation and response.
**PAW configuration drift weakening posture** |Over time, misconfiguration or failed policy application can silently erode device trust assumptions used in Phase 3 enforcement.| Intune compliance reporting and Defender posture signals surface drift from hardened baselines, enabling remediation before access controls are weakened.
**Malicious or unexpected app execution on PAWs** |Execution of unauthorized tools, scripts, or binaries can indicate attacker activity or misuse of privileged access. | AppLocker telemetry collected by Defender for Endpoint makes application execution on PAWs observable and auditable, enabling detection of suspicious activity.
**Abuse of privileged roles after credential theft** | Attackers may delay or disguise use of stolen credentials to evade initial detection. | Phase 4 correlates privileged role activation, admin portal access, and device risk changes to identify suspicious privileged workflows.
**Blind spots in privileged access enforcement** | Without monitoring, organizations cannot verify that Conditional Access and PAW restrictions are working as intended.| Entra sign‑in logs, Conditional Access insights, and Defender telemetry provide visibility into allowed and blocked privileged access attempts.
**Delayed response to active privileged access threats** | Slow containment increases blast radius and business impact. | Defender for Endpoint enables investigation, device isolation, and remediation actions using high‑confidence signals from privileged devices and workflows.



## Phase outcomes

When Phase 4 is implemented:

- PAWs are continuously monitored for threats, integrity issues, and configuration drift.
- Application execution on PAWs is observable and auditable
- Suspicious activity involving privileged access is detected quickly.
- Security teams can contain and remediate incidents using endpoint and identity signals
- Monitoring data feeds measurement and success criteria for the privileged access strategy

## Prerequisites

Before you start configuring Phase 4:

- Complete [Phase 1 instructions](implement-privileged-access-identity.md) to secure the identity control plan.
- Complete [Phase 2](implement-privileged-access-devices.md) to deploy and harden PAWs.
- Complete [Phase 3](implement-privileged-access-enforce.md) so that conditional access enforcement in active.
- Make sure that device compliance and Defender for Endpoint integration is active.


## Step 1: Monitor PAW security posture

Use Microsoft Defender for Endpoint to monitor PAWs for threats, vulnerabilities, and configuration drift. Regular monitoring ensures that changes in PAW risk or posture are visible as soon as they occur.

### Review PAW risk and exposure

1. In the Microsoft Defender portal, select **Endpoints** > **Device inventory**
1. Filter devices by the PAW device group.
1. For each PAW review:
    - Device risk level
    - Exposure score
    - Active alerts
    - Sensor health status

### Review vulnerabilities and misconfiguration

1. In the Microsoft Defender portal, select **Vulnerability management**.
1. Review exposure score trends for PAWs.
1. Review security recommendations affecting credential protection and exploit mitigation.
1. Prioritize remediation for:
    - Disabled credential protections
    - Missing security updates
    - Defender sensor health issues


## Step 2: Detect and investigate PAW threats

Use Defender for Endpoint alerts and device timelines to investigate suspicious activity targeting privileged devices.

### Investigate PAW security alerts

1. In the Microsoft Defender portal, select **Incidents & alerts**.
1. Filter incidents by the PAW device group.
1. Open an incident and review:
    - Device timeline
    - Process execution
    - Credential access attempts
    - Persistence techniques
    - Network connections
    - Missing security updates
    - Defender sensor health issues


### Enable automated response

1. In the Microsoft Defender portal, select **Settings** > **Endpoints** > **Advanced features**.
1. Confirm that **Live response** is set to **On**.

## Step 3: Monitor apps on PAWs

Application execution on PAWs must be observable and auditable. AppLocker policies deployed earlier generate telemetry that is automatically collected by Defender for Endpoint.

1. In the Microsoft Defender portal, select **Advanced hunting**.
1. Run a query to review application control activity (for example, AppLocker events).
1. After running the query, investigate:

    - Blocked executables
    - Unexpected scripts or binaries
    - Repeated execution attempts
1. Pivot to the **Device timeline** and review:
    - File hashes
    - User context
    - Parent processes

## Step 4: Monitor usage and enforcement

Verify that privileged access is occurring only from PAWs and that enforcement behaves as expected.

1. In the [Microsoft Entra Admin Center](https://entra.microsoft.com), navigate to **Protection** > **Sign-in logs**.
1. Filter for:
    - Privileged roles
    - Conditional access policies protecting privileged access
    - Device platform = Windows
1. Validate that:
    - Privileged access succeeds from compliant PAWs
    - Access is blocked when device risk increases
    - Emergency access accounts are excluded as intended

### Review conditional access insights

1. In the [Microsoft Entra Admin Center](https://entra.microsoft.com) > **Conditional Access**, select **Insights and reporting**.
1. Review:

    - Blocked attempts from non‑PAW devices
    - Policy impact for privileged access policies



## Step 5: Detect configuration drift on PAWs

Use Intune compliance reporting to detect drift from hardened PAW baselines.

1. In the Intune admin center navigate to **Devices** > **Compliance policies**.
1. Review compliance status for the PAW device group.
1. Investigate:
    - Non-compliant devices
    - Update failures
    - Missing or misapplied policies
1. Correlate compliance failures with Defender risk changes.

## Step 6: Contain and remediate incidents

1. In the Microsoft Defender portal, select the affected PAW.
1. Use response actions to:
    - Isolate the device.
    - Collect an investigation package
    - Initiate remediation
1. Review recent privileged activity:
    - Role activations
    - Administrative portal access
    - Token usage
1. Take corrective actions as required:
    - Reset privileged credentials
    - Invalidate sessions
    - Rebuild or reimage the PAW

## Summary

Phase 4 is the final stage in the solution guide. 

- PAWs are continuously monitored for threats and misconfiguration
- Application execution on PAWs is observable and auditable
- Suspicious privileged access activity is detected quickly
- Security teams can investigate, contain, and remediate incidents effectively
- Monitoring data feeds directly into measuring the success of the privileged access strategy


## Next steps

Check out our other solution guides.