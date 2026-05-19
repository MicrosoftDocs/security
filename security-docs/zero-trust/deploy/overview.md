---
title: Zero Trust deployment for technology pillars overview
description: Learn how to deploy Zero Trust solutions to keep your organization secure.
ms.date: 02/26/2025
ms.service: security
ms.subservice: zero-trust
ms.topic: checklist
ms.collection:
  - highpri
  - zerotrust-pillar
---

# Overview - Technology pillars

This article summarizes technology pillars in our [Zero Trust adoption model](../security-adoption-model.md).

Technology pillars represent the core areas of your security architecture. They group related capabilities and controls into logical domains such as identity, endpoints, data, apps, infrastructure, networks, and security operations.

Each pillar answers the same fundamental question:

**How do we apply Zero Trust principles to this part of the environment?**

Instead of thinking in terms of individual products or features, pillars provide a stable way to organize security design and implementation across your environment.

:::image type="content" source="../media/diagram-zero-trust-security-elements.png" alt-text="Diagram of elements of visibility, automation, and orchestration in Zero Trust." border="false":::

## Technology pillars in the adoption model

Our structured adoption model focuses on three components:

- [Business scenarios](../security-adoption-business-scenarios-overview.md) - Define the most critical security outcomes for the organization. They focus on **why** we're adopting Zero Trust security.
- [Security disciplines](../security-adoption-discipline-overview.md) - Guide teams to define strategy, architecture,  processes, and controls across common areas of security so that we can deliver the business scenarios. They focus on **what** Zero Trust capabilities are required.
- **Technology pillars** - Secure specific areas of the organization such as identity, data, and devices. They focus on **where** security capabilities are implemented.
- [Technical solutions](../implement-overview.md) - As adoption moves towards deployment,  technical solutoins provide detailed guidance for implementing security controls across technology pillars. They focus on **how** security is implemented.



In the Zero Trust adoption model, technology pillars sit between strategy and implementation.

Technology pillars don't define outcomes (business solutions) or steps (technical solutions), but they do:

- Define technical boundaries where security controls are applied. These hese boundaries are used by solutions to organize implementation guidance and logic.
- Act as the bridge between intent (why) and implementation (how).

## Pillars

| Technology pillar | Description |
| --- | --- |
| [![Fingerprint icon](../media/icon-identity-small.png)](identity.md) <br> [Identities](identity.md) | Control access decisions. Every request starts with identity verification and enforcement of least privilege. |
| [![Endpoints icon.](../media/icon-endpoints-small.png)](endpoints.md) <br> [Endpoints](endpoints.md) |  Evaluate and enforce device trust. Access depends on device health, compliance, and risk. |
| [![Ones and zeroes icon.](../media/icon-data-small.png)](data.md) <br> [Data](data.md)  | Protect the asset itself. Security persists with the data through classification, labeling, encryption, and access control. |
| [![Application window icon.](../media/icon-applications-small.png)](applications.md) <br> [Apps](applications.md)| Govern how data is accessed. Apply controls at the application and API layer, including permissions and session controls. |
| [![Data storage disks icon.](../media/icon-infrastructure-small.png)](infrastructure.md) <br> [Infrastructure](infrastructure.md) | Secure compute resources. Harden servers, VMs, containers, and services through configuration, access control, and monitoring. |
| [![Network diagram icon.](../media/icon-networks-small.png)](networks.md) <br> [Network](networks.md) | Control connectivity and movement. Segment and monitor traffic to prevent lateral movement and enforce secure communication.|
| [![Gear icon.](../media/icon-visibility-automation-orchestration-small.png)](visibility-automation-orchestration.md) <br> [SecOps](visibility-automation-orchestration.md) |Integrate and operationalize all pillars. Detect, investigate, and respond using signals from across the environment. |

## Zero Trust implementation workshops

Microsoft's Zero Trust implementation workshops are available for each pillar. [Learn more](../workshop-zero-trust-overview.md).

## What's next?

- [Review](../implement-overview.md) technical solutions.
- [Learn about](../security-adoption-model.md) our Zero Trust adoption model.
- [Review](../security-adoption-business-scenarios-overview.md) critical security business scenarios.

