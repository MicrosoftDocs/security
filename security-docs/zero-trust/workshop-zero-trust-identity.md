---
title: Microsoft Zero Trust Workshop - Identity
description: Learn about the Identity pillar in the Microsoft Zero Trust Workshop
ms.date: 04/18/2024
ms.service: security
author: rayne-wiselman
ms.author: raynew
ms.subservice: zero-trust
ms.topic: conceptual
---

# Identity in the Microsoft Zero Trust Workshop

In a Zero Trust framework, identity is the foundational control plane. Every decision for access to a device, application, or data resource begins with verifying who the user is, what their privileges are, and whether their context is trusted. The Identity pillar in the Zero Trust Workshop ensures that organizations “Verify explicitly, enforce least privilege, and assume breach” at the user and identity level.

Identity pillar Workshop guidance focuses on assessing your current identity posture, identifying gaps, and defining priorities to improve security, reduce risk, and streamline user access, and covers these implementation areas:

- **Inventory and understand identity assets**: Compile a complete inventory of applications, service principals, and user attributes. Assign ownership to ensure accountability and governance.
- **Design a Conditional Access posture**: Implement risk-based policies that continuously evaluate identity, device state, location, and session risk. Restrict access to trusted endpoints and applications only.
- **Enforce Least Privileged roles**: Assign roles and privileges strictly based on job requirements. Regularly review and remove unnecessary or excessive access rights.
- **Protect privileged identities**: Migrate privileged accounts to cloud-only identities to isolate them from on-prem attacks. Apply enhanced protections such as just-in-time access, MFA, conditional access, or privileged access workstations.
- **Automate Identity lifecycle/provisioning**: Deploy connectors and workflows to automate user provisioning, updates, and deprovisioning. Map attributes to applications to ensure correct access assignments.
- **Strengthen credential security**: Implement Microsoft Entra Password Protection and move toward modern authentication (passwordless) to reduce credential risks.
- **Onboard external/partner identities securely**: Define controlled processes for onboarding external users and partners. Ensure external identities are governed, monitored, and validated under the Zero Trust model.

## Assess identity

The Zero Trust Assessment tool  can assess your identity configuration against a range of security best practices. [Learn more](/security/zero-trust/assessment/overview).