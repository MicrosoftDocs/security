---
title: Secure devices and workstations
description: Learn how to secure devices and workstations in a privileged access architecture
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


# Phase 2: Configure and secure privileged workstations

This article is part of the [Implement a privileged access architecture](implement-privileged-access.md) solution guide. 

Privileged access presents a critical security risk in most organizations because it enables direct control over identity systems, cloud control planes, and business‑critical assets.

Learn how a [secure privileged access architecture](../security-adoption-scenario-privileged-access.md) plays a critical role in your business scenario - *[Protect critical business assets](../security-adoption-scenario-secure-assets.md)* - by reducing this risk and strengthening control over sensitive systems.

This article describes Phase 2 of the solution.  It deploys and hardens Privileged Access Workstations (PAWs) so privileged activity originates only from trusted devices. It builds on Phase 1 and produces the device trust signals (Intune compliance and Microsoft Defender for Endpoint risk) used for enforcement in Phase 3. 

## Protection goals

Phase 2 ensures that privileged access:

- Originates only from trusted, hardened devices.
- Is isolated from high‑risk productivity activities.
- Produces a clean, reliable device signal for later enforcement.
- Reduces credential theft, token replay, and session hijacking risk.
- Limits blast radius if a device is compromised.

## Protection scope

Privileged access is only as trustworthy as the device from which it originates. Identity protections—such as MFA, approvals, and role activation—cannot compensate for a compromised workstation.
If an attacker controls the device used for privileged access, they can:

- Steal authentication tokens after MFA is completed
- Inject malicious processes into administrative sessions
- Replay credentials or tokens from memory
- Bypass approval workflows by operating as the legitimate user

For privileged roles, a single compromised workstation can enable rapid escalation to tenant‑wide or enterprise‑wide control. As a result, device security defines the upper bound of trust for privileged access.
Privileged access policies therefore assume that administrative sessions originate from devices that meet the highest security bar. These devices form the trust boundary for privileged operations.

### Privileged access workstations (PAWs)

A PAW is a hardened, managed Windows workstation designed exclusively for privileged tasks. PAWs define the device trust boundary for privileged access, and are isolated from common attack vectors.

- Are isolated from email, general web browsing, and productivity workloads.
- Are enrolled and managed via Microsoft Intune.
- Use Microsoft Entra ID for identity integration.
- Are monitored by Microsoft Defender for Endpoint.
- Provide a strong hardware-based root of trust.

Here's how PAWs fit in from a security level/profile perspective.

**Security level** | **Device profile**
--- | --- 
Enterprise users | Standard managed device
Specialized operators | Hardened managed device
Privileged (control plane administrators) | PAW


## Risks mitigated

**Risk** | **Why it matters** | **Phase 1 mitigation**
--- | --- | ---
**Attacker steals authentication tokens after MFA** |MFA protects authentication, not the execution environment. If a workstation is compromised, attackers can steal tokens post‑authentication and reuse them to impersonate privileged users. | PAWs isolate privileged work on hardened devices with reduced attack surface, credential protection (Credential Guard), and continuous monitoring, preventing token theft from compromised productivity devices.
**Malicious process injection into administrative sessions** | Attackers can inject code into admin tools or browser sessions on compromised devices, gaining control of privileged operations even when identities are protected. | Application control, removal of local admin rights, and restricted application execution on PAWs prevent unauthorized code execution during administrative sessions.
**Credential replay from memory** | Attackers can extract credentials or tokens from memory on compromised workstations and replay them to escalate privileges or move laterally. | PAWs enforce credential isolation using virtualization‑based security and hardened OS configurations, reducing exposure of credentials in memory and limiting replay opportunities.
**Approval workflows bypassed from compromised devices** |Even with approval‑based role activation, attackers controlling a workstation can hijack approved sessions and rapidly escalate privileges. |Device trust becomes a prerequisite for privileged work. PAWs ensure approvals and administrative actions occur only from devices designed to resist compromise.
**Rapid escalation from compromised workstation** |A single compromised admin workstation can allow attackers to pivot quickly to identity systems, control planes, and enterprise‑wide administration.| Device security sets an upper bound on trust. PAWs provide the highest security bar, reducing the likelihood that a compromised endpoint can be used to escalate into privileged roles.


## Phase outcomes

After completing Phase 2:

- One or more dedicated PAW devices are set up. 
- Privileged administrative work originates only from PAWs
- PAWs are isolated from productivity usage
Devices are centrally managed, monitored, and recoverable
- Device trust assumptions are explicit and enforceable
- Later phases can safely apply Conditional Access and monitoring


## Prerequisites

Before configuring procedures in this article:

- Make sure that [Phase 1 instructions](implement-privileged-access-identity.md) are complete.
- Learn about [device security in the privileged access story](../security-concept-privileged-access.md).
- The following services should be available:
    - Microsoft Entra ID as the identity provider.
    - Microsoft Intune for device management.
    - Microsoft Defender for Endpoint for threat protection.
- You need at least one supported Windows device per administrator, with modern Windows hardware that supports:
    - TPM 2.0
    - UEFI Secure Boot
    - BitLocker
    - Virtualization-based security (VBS/HVCI)
    - Firmware and drivers serviced through Windows Update.

Devices that don't meet this bar must not be used for privileged access


## Step 1: Define PAW provisioning/lifecycle

Define which devices are PAWs, how they are created, enrolled, managed, and prevented from being used before they are ready.

### Create a PAW device group

This group will contain PAW devices, and will be used for:

- Enrollment targeting
- Hardening profiles
- Compliance evaluation
- Conditional Access enforcement in a later phase.

Create as follows:

1. In the [Microsoft Entra Admin Center](https://entra.microsoft.com), navigate to **Microsoft Entra ID** > **Groups** > **New group**. 
1. Configure the group settings, and then select **Create**.
    - **Group type**: Security
    - **Group name**: Secure Workstation Devices
    - **Membership type**: Dynamic Devices

1. Select **Add dynamic query** and add a rule with this syntax: *device.devicePhysicalIds -any _ -contains "[OrderID]:PAW"*

1. Select **Save** > **Create**.

Any device enrolled with an autopilot group tag that equals "PAW" becomes a privileged access workstation.

### Control who can create PAWs

Ensure PAWs are enrolled intentionally and securely.

- Restrict who can join devices to Microsoft Entra ID.
- Require MFA to join devices
- Remove automatic local administrator rights on join


1. In the Entra Admin Center, navigate to **Devices** > **Device settings**.
1. In **Users may join devices to Microsoft Entra ID** > **Selected**, select **Secure Workstation Users**.
1. In **Require Multi-Factor Auth to join devices**, select **Yes**.
1. In **Additional local administrator on Microsoft Entra joined devices**, select **None**.
1. Save the settings

With this in place, only PAW users can enroll PAWs, MFA is required, and no PAW user becomes a local administrator by default.

### Manage PAWs from first boot

PAWs must be managed from first boot. Unmanaged devices cannot be trusted for privileged access.

- Configure Microsoft Entra ID to automatically enroll devices into Intune. 
- Ensure all PAWs are MDM‑managed immediately after join.
- Restrict device enrollment to approved platforms.

1. Open **Microsoft Entra ID** > **Mobility (MDM and MAM)** > **Microsoft Intune**.
1. Set **MDM user scope** to **All** and save.
1. Configure **Enrollment restrictions**:
    - Allow Windows MDM
    - Block or restrict BYOD / personally owned devices

PAWs are always managed, never unmanaged.


### Provision PAWs consistently

Use Windows Autopilot to enforce consistent, repeatable PAW provisioning that ensures PAWs start in a known-good state.

- Create a dedicated Autopilot deployment profile, and assign it to the PAW device group.


1. In the Microsoft Intune Admin Center, go to **Devices** >  **Windows** > **Windows enrollment** > **Deployment profiles**.
1. Select **Create profile** and create a profile with the following settings:
    - **Name**: Secure workstation deployment profile
    - **Convert all targeted devices to Autopilot**: Yes
    - **Deployment mode**: Self‑deploying
    - **User account type**: Standard
1. Select **Create**.


### Prevent PAWs from use before hardening

Prevent PAWs from being used before they’re fully hardened. This prevents early exposure during setup.

- Configure an Enrollment Status Page (ESP)
- Block device use until all required profiles and applications install
- Assign ESP to PAW devices

1. In the Microsoft Intune Admin Center, go to **Devices** >  **Windows** > **Windows enrollment** > **Enrollment status**.
1. Select **Create profile** and create a profile with the following settings:
    - **Show app and profile installation progress**: Yes
    - **Block device use until all apps and profiles are installed**: Yes
    
1. Assign to **Secure Workstation Devices** and select **Create**.

### Ongoing lifecycle operations

1. To recover and rebuild PAWs:
    - Reset / reprovision PAWs via Autopilot when compromised.
    - Treat PAWs as replaceable, not manually repaired
1. To identity and track PAWs use:

    - Device group membership
    - Autopilot registration

With these processes in place, PAWs are explicitly identifiable, centrally managed devices that can be inventoried, reviewed, and safely wiped and re‑provisioned through Autopilot if compromised.

## Step 2: Harden PAWs

Harden Privileged Access Workstations (PAWs) to present a clean, low‑risk device signal. Hardening controls include reducing the attack surface, enforcing patching, and producing  Defender risk/compliance signals.

Conditional Access and monitoring controls rely on this posture to enforce privileged access decisions.

These controls assume PAWs meet the required hardware security prerequisites defined earlier.

### Configure Windows Update rings

PAWs must be patched quickly and predictably. Delays or user‑controlled deferrals undermine device trust.


1. In the Microsoft Intune Admin Center, go to **Devices** > **Windows** > **Software updates** > **Windows Update rings**.
1. Select **Create profile**
1. Configure the following settings:
    - Name: PAW – Windows Update Ring
    - Servicing channel: Semi‑Annual
    - Quality update deferral (days): 3
    - Feature update deferral (days): 3
    - Automatic update behavior: Auto install and reboot without end‑user control
    - Block user from pausing updates: Block
    - Require user’s approval to restart outside of work hours: Required
    - Set deadline for pending restarts: 3 days

1. In **Assignments**, assign to secure workstation devices.
1. Create the profile.

After you complete this procedure, PAWs stay patched with minimal exposure window and no user bypass.

### Onboard to Defender for Endpoint

Conditional Access and compliance depend on Defender risk signals. Without Defender for Endpoint, device trust is incomplete.

1. In the Microsoft Intune Admin Center, go to **Endpoint security** > **Microsoft Defender for Endpoint**.
1. Set **Connect Microsoft Defender for Endpoint to Intune** to **On**.
1. Select **Save**. 
1. Refresh in Intune to confirm the connection.


###  Create an onboarding profile

1. In the Microsoft Intune Admin Center, go to **Endpoint security** > **Endpoint detection and response**.
1. Set **Create profile** and configure the following settings:
    - Platform: Windows 10 and later
    - Profile type: Endpoint detection and response
    - Name: PAW - Defender for Endpoint

1. In **Configuration settings** enable **Sample sharing for all files**.
1. Assign to the **Secure Workstation Devices** account.
1. Create the profile. 

After you configure the procedure, PAWs emit device risk, malware, and EDR telemetry used by Conditional Access and SecOps.

### Enforce firewall and network restrictions

Most PAW compromise paths are outbound. Restricting egress is critical.

1. In the Microsoft Intune Admin Center, go to **Endpoint security** > **Firewall**.
1. Create an **Endpoint protection** profile and configure firewall behavior:
    - Inbound connections: Block
    - Outbound connections: 
        - Enterprise/Specialized: Allow
        - Privileged: Block by default. Allow only required services (DNS, DHCP, HTTPS)

1. Assign to**Secure Workstation Devices**.

After configuring the procedure, PAWs can reach only administrative endpoints required for management tasks.

## Next steps

With PAWs configured and hardened,   the next step is to [enforce privileged access using Conditional Access and policy](implement-privileged-access-enforce.md).