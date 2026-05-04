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

In a Zero Trust model, devices are a critical piece of the trust equation. Even if a user’s identity is validated, access should depend on the security health of their device. The Devices pillar focuses on making sure managed devices meet security standards, reducing device risk, and enabling conditional access based on device posture.
Device pillar Workshop guidance focuses on managing device enrollment, enforcing compliance policies, securing devices against endpoint threats, controlling admin access to devices, and ensuring least-privilege and segmentation for device operations. The Devices workshop covers these implementation areas:

- **Manage device enrollment and compliance**: Enroll devices using mobile device management (Microsoft Intune) so they can be managed and evaluated. Define and enforce device compliance policies (OS, health, risk) that are required for access.
- **Enforce device-based conditional access**: Use Conditional Access policies that require devices to be marked as “compliant” before accessing corporate resources. Integrate compliance states with identity to ensure only healthy devices access sensitive apps.
- **Reduce device attack surfaces**: Apply Attack Surface Reduction (ASR) rules via Intune to limit risky behaviors (e.g., untrusted scripts, removable media). se exploit protection and application control (e.g., via WDAC) to limit what can run on devices.
- **Implement least-privilege admin control**: Use Role-Based Access Control (RBAC) in Intune to limit who can manage devices.
- **Automate Identity lifecycle/provisioning**: Deploy connectors and workflows to automate user provisioning, updates, and deprovisioning. Map attributes to applications to ensure correct access assignments. Define scope tags or administrative segmentation so device management is limited to what each team needs.
- **Support shared/frontline devices**: Leverage Microsoft Entra Shared Device Mode (for iOS/Android) so multiple users can use one device securely. Ensure that after each use session, the device signs out, protecting user identity and corporate data.
-

## Assess identity**

The Zero Trust Assessment tool (currently in preview) can assess your device configuration against a range of security best practices. [Learn more](/security/zero-trust/assessment/overview).