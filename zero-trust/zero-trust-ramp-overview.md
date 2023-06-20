---
title: Zero Trust Rapid Modernization Plan
description: An overview of the Zero Trust Rapid Modernization Plan (RaMP) to quickly modernize your security and IT infrastructure to comply with Zero Trust protections. 
ms.service: security
ms.author: dansimp
author: dansimp
manager: dansimp
ms.topic: conceptual
ms.collection:
  - zerotrust-ramp
---

# Zero Trust Rapid Modernization Plan

As an alternative to [deployment guidance](./deploy/overview.md) that provides detailed configuration steps for each of the technology pillars being protected by Zero Trust principles, Rapid Modernization Plan (RaMP) guidance is based on initiatives and gives you a set of deployment paths to more quickly implement key layers of protection.

RaMP guidance takes a project management and checklist approach:

- By providing a suggested mapping of key stakeholders, implementers, and their accountabilities, you can more quickly organize an internal project and define the tasks and owners to drive them to conclusion.
- By providing a checklist of deployment objectives and implementation steps, you can see the bigger picture of infrastructure requirements and track your progress.

## RaMP initiatives for Zero Trust

To rapidly adopt Zero Trust in your organization, RaMP offers technical deployment guidance organized in these initiatives.

| Initiative | Steps |
|:-------|:-----|
| **Top priority** | Critical security modernization initiatives: |
| ![User Access and Productivity](./media/zero-trust-ramp-overview/user-access-icon.png) <br> [User access and productivity](user-access-productivity-overview.md) | <ol><li>[Explicitly validate trust for all access requests](user-access-productivity-validate-trust.md)<br><ul><li>[Identities](user-access-productivity-validate-trust.md#identities)</li><li>[Endpoints (devices)](user-access-productivity-validate-trust.md#endpoints)</li><li>[Apps](user-access-productivity-validate-trust.md#apps)</li><li>[Network](user-access-productivity-validate-trust.md#network)</li></ul></li> |
| ![Data, compliance, and governance](./media/zero-trust-ramp-overview/data-compliance-governance-icon.png) <br> [Data, compliance, and governance](data-compliance-governance-overview.md) | <ol start="2"><li>[Ransomware recovery readiness](data-compliance-gov-ransomware-recovery-readiness.md)<br></li><li>[Data](data-compliance-gov-data.md)<br></ol> |
| Modernize security operations  | <ol start="4"><li>Streamline response</li><li>Unify visibility</li><li>Reduce manual effort</li></li></ol>|
| **As needed** | Additional initiatives based on Operational Technology (OT) or IoT usage, on-premises and cloud adoption, and security for in-house app development: |
| OT and Industrial IoT | <ul><li>Discover</li><li>Protect</li><li>Monitor</li></ul> |
| Datacenter & DevOps Security | <ul><li>Security Hygiene</li><li>Reduce Legacy Risk</li><li>DevOps Integration</li><li>Microsegmentation</li></ul> |

Here is the overall architecture for Zero Trust.

:::image type="content" source="./media/zero-trust-ramp-overview/zero-trust-architecture.svg" alt-text="The overall architecture for Zero Trust" lightbox="./media/zero-trust-ramp-overview/zero-trust-architecture.svg":::

The RaMP initiatives for Zero Trust address all of the elements of this architecture. As you step through the initiatives, we'll show which parts are being covered.

## Next step

Begin your Zero Trust RaMP deployment journey with [User access and productivity](user-access-productivity-overview.md).
