---
title: Zero Trust Rapid Modernization Plan
description: An overview of the Zero Trust Rapid Modernization Plan (RaMP) to quickly modernize your security and IT infrastructure to comply with Zero Trust protections. 
ms.service: security
ms.author: josephd
author: JoeDavies-MSFT
manager: dansimp
ms.topic: conceptual
---

# Zero Trust Rapid Modernization Plan

As an alternative to [deployment guidance](./deploy/overview.md) that provides detailed configuration steps for each of the entities being protected by Zero Trust principles, Rapid Modernization Plan (RaMP) guidance gives you a set of deployment paths to more quickly implement key layers of protection.

RaMP guidance takes a project management and checklist approach:

- By providing a suggested mapping of key stakeholders, implementers, and their accountabilities, you can more quickly organize an internal project and define the tasks and owners to drive them to conclusion.
- By providing a checklist of deployment objectives and implementation steps, you can see the bigger picture of infrastructure requirements and track your progess.

<!--

Today’s organizations need a new security model that more effectively adapts to the complexity of the modern environment, embraces the hybrid workplace, and protects people, devices, apps, and data wherever they’re located. This new model includes:

- Productivity everywhere

  Empower your users to work more securely anywhere and anytime, on any device.

- Cloud migration

  Enable digital transformation with intelligent security for today’s complex environment.

- Risk mitigation

  Close security gaps and minimize risk of lateral movement.


Zero Trust operates on these security principles:

- Verify explicitly

  Always authenticate and authorize based on all available data points, including user identity, location, device health, service or workload, data classification, and anomalies.

- Use least privilege access

  Limit user access with just-in-time and just-enough-access (JIT/JEA), risk-based adaptive polices, and data protection to help secure both data and productivity.

- Assume breach

  Minimize blast radius and segment access. Verify end-to-end encryption and use analytics to get visibility, drive threat detection, and improve defenses.

--> 

## RaMP initiatives for Zero Trust

The guidance for deployment of Zero Trust in your organization is organized in these initiatives.

| Initiative | Steps |
|:-------|:-----|
| **Top priority** | Critical security modernization initiatives: |
| ![User Access and Productivity](./media/zero-trust-ramp-overview/user-access-icon.png) <br> [User access and productivity](user-access-productivity-overview.md) | <ol><li>[Explicitly validate trust for all access requests](user-access-productivity-validate-trust.md)<br><ul><li>[Identities](user-access-productivity-validate-trust.md#identities)</li><li>[Endpoints (devices)](user-access-productivity-validate-trust.md#endpoints)</li><li>[Apps](user-access-productivity-validate-trust.md#apps)</li><li>[Network](user-access-productivity-validate-trust.md#network)</li></ul></li> |
| ![Data, compliance, and governance](./media/zero-trust-ramp-overview/data-compliance-governance-icon.png) <br> [Data, compliance, and governance](data-compliance-governance-overview.md) | <ol start="2"><li>[Ransomware recovery readiness](data-compliance-gov-ransomware-recovery-readiness.md)<br></li><li>[Data](data-compliance-gov-data.md)<br></ol> |
| ![Modernize Security Operations](./media/zero-trust-ramp-overview/modernize-security-icon.png) <br> [Modernize security operations](modernize-security-operations-overview.md)  | <ol start="4"><li>[Streamline response](modernize-security-operations-streamline-response.md)</li><li>[Unify visibility](modernize-security-operations-unify-visibility.md)</li><li>[Reduce manual effort](modernize-security-operations-reduce-manual-effort.md)</li></li></ol>|
| **As needed** | Additional initiatives based on Operational Technology (OT) or IoT usage, on-premises and cloud adoption, and security for in-house app development: |
| OT and Industrial IoT | <ul><li>Discover</li><li>Protect</li><li>Monitor</li></ul> |
| Datacenter & DevOps Security | <ul><li>Security Hygiene</li><li>Reduce Legacy Risk</li><li>DevOps Integration</li><li>Microsegmentation</li></ul> |

<!--

User Access and Productivity

<ol><li>Explicitly validate trust for all access requests<br><ul><li>User Accounts</li><li>Devices</li></ul></li><li>Increase security for accessing key resources<br><ul><li>Apps</li><li>Data</li></ul><li>Governance</li></ol>

Modernize Security Operations


<ol start="4"><li>Streamine response</li><li>Unify visibility</li><li>Reduce manual effort</li></li></ol>



Operational Technology (OT) and Industrial IoT

<ul><li>Discover</li><li>Protect</li><li>Monitor</li></ul>


SLIDE GRAPHIC=========================================================

The guidance for deployment of Zero Trust in your organization is organized in main areas.

![RaMP areas for Zero Trust](./media/zero-trust-ramp-overview/zero-trust-ramp-pillars.png)


For every organization, the top priority Zero Trust RaAMP initiatives are:

- [User access and productivity](user-access-productivity-overview.md)
- [Data, compliance, and governance](data-compliance-governance-overview.md)
- [Modernize security operations](modernize-security-operations-overview.md)

Zero Trust RaMP initiatives based on need for the use of Operations Technology (OT) and Industrial IoT, on-premises and cloud adoption, and security for in-house app development are:

- OT and industrial IoT
- Datacenter & DevOps security

--> 

Here is the overall architecture for Zero Trust.

:::image type="content" source="./media/zero-trust-ramp-overview/zero-trust-architecture.png" alt-text="The overall architecture for Zero Trust" lightbox="./media/zero-trust-ramp-overview/zero-trust-architecture.png":::

The Zero Trust RaMP initiatives address all of the elements of this architecture. As you step through the initiatives, we will show which parts are being covered.

## Next step

Begin your Zero Trust RaMP deployment journey with [User access and productivity](user-access-productivity-overview.md).
