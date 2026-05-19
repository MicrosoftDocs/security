---
title: Microsoft Zero Trust Workshop - Devices
description: Learn about the Devices pillar in the Microsoft Zero Trust Workshop
ms.date: 04/18/2024
ms.service: security
author: rayne-wiselman
ms.author: raynew
ms.subservice: zero-trust
ms.topic: conceptual
---

# Device security in the Microsoft Zero Trust Workshop

In a Zero Trust model, devices are a critical part of the trust evaluation. Even when a user’s identity is validated, access decisions must also depend on the security health, configuration, and risk state of the device. The Devices pillar focuses on ensuring that devices are managed, continuously assessed, and protected against threats, enabling access decisions based on device posture.

Device pillar workshop guidance focuses on managing device lifecycle and enrollment, enforcing compliance and configuration standards, protecting endpoints from threats, reducing attack surface, and integrating device risk into access and security operations.


## Workshop implementation

The Devices workshop covers the implementation areas summarized in the table.

**Area** | **Details**
--- | ---
**Manage device enrollment and lifecycle**  |   Enroll and provision devices using modern management (such as Microsoft Intune and Windows Autopilot).<br/><br/> Standardize device onboarding and configuration to ensure devices start in a known, trusted state and remain consistently managed throughout their lifecycle.
**Define and enforce device compliance posture**  |   Define device compliance policies based on security requirements such as OS version, configuration baseline, and risk level. <br/><br/>Continuously assess device health to determine whether devices meet organizational standards.
**Enforce posture-based access with Conditional Access**  |   Integrate device compliance and risk signals into Conditional Access policies to ensure only healthy and compliant devices can access corporate resources. <br/><br/>Apply differentiated access controls for managed, unmanaged, and high-risk devices.
**Secure device configuration and baseline standards**  |   Apply security baselines and configuration policies to enforce consistent hardening across devices.<br/><br/> Standardize settings for operating systems, security controls, and management configurations to reduce misconfigurations.
**Reduce device attack surface and restrict risky behaviors**  |   Implement controls such as Attack Surface Reduction (ASR) rules, exploit protection, and application control (for example, Windows Defender Application Control) to limit exploitable behaviors and restrict untrusted or unauthorized code execution.
**Protect endpoints with threat detection and response**  |   Deploy endpoint protection and detection capabilities to identify, investigate, and remediate threats on devices.<br/><br/>Generate risk signals from endpoint protection systems and use them to drive remediation and inform access decisions.
**Implement least-privilege and administrative control**  |   Minimize local administrator access and enforce least privilege on devices.<br/><br/> Apply role-based access control and administrative segmentation to ensure only authorized personnel can manage device configurations and management policies.
**Support secure access for diverse device scenarios**  |   Enable secure use of personally owned, shared, and frontline devices.<br/><br/> Apply appropriate controls such as app protection policies, shared device modes, or session-based protections to secure access where full device management is not feasible.
**Integrate device signals into security operations (SecOps)**  |  Stream device health, compliance, and threat signals into centralized monitoring and response workflows.<br/><br/> Correlate these signals with identity, data, and network telemetry to detect and respond to device-based threats.


## Assess device posture

The Zero Trust Assessment tool can assess your device configuration against a range of security best practices. [Learn more](/security/zero-trust/assessment/overview).

## What's next?

[Run an assessment](assessment/get-started.md), and begin the [Devices workshop](https://zerotrust.microsoft.com/).