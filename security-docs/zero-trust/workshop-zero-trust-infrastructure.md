---
title: Microsoft Zero Trust Workshop - Infrastructure
description: Learn about the Infrastructure pillar in the Microsoft Zero Trust Workshop
ms.date: 04/18/2024
ms.service: security
author: rayne-wiselman
ms.author: raynew
ms.subservice: zero-trust
ms.topic: conceptual
---

# Infrastructure security in the Microsoft Zero Trust Workshop

In a Zero Trust architecture, infrastructure security is about securing your foundational compute and platform resources in the multicloud and on-premises, to support a Zero Trust architecture. Rather than trusting infrastructure implicitly, this pillar ensures that your servers, containers, storage, and other infrastructure services are hardened, monitored, and configured to assume breach. The goal is to build a resilient platform where infrastructure is not a weak link, but a well‑protected part of your Zero Trust strategy.

Infrastructure pillar guidance focuses protecting servers running workloads, infrastructure security posture management and governance, container security, managing vulnerability risk and security alerts, and controlling access to infrastructure resources. The Infrastructure workshop covers these implementation areas:

- **Protect VMs**: Protect multicloud VMs in Azure and on-premises. Use a product such as Microsoft Defender for Cloud (using the Defender for Servers plan) to continuously monitor and evaluate the security posture of these workloads and remediate misconfigurations.
- **Harden container environments**: Monitor and assess your container configuration against recommended settings. For example, apply the CIS Kubernetes Benchmark for Kubernetes clusters and enforce it via Defender for Cloud (using the Defender for Containers plan). Continuously monitor container security, use secure configurations, and apply runtime protections.
- **Assess and manage vulnerabilities**: Scan for vulnerabilities and configuration issues using a service such as Defender for Cloud. Remediate issues as needed, or suppress specific findngs to reduce noise and alert fatigue. 
- **Control admin access to infrastructure**: Implement just-in-time access or role-based controls for infrastructure admin tasks such as server modifications, container configuration etc. Enforce the principle of least privilege for infrastructure administrators.
- **Improve visiblity and monitoring**: Monitor infrastructure resources to detect real-time threats and issue security alerts. Create and manage alert suppression rules to reduce false positives and streamline security operations. Integrate infrasIructure logs and alerts into SecOps tools for detection and response.

## Assess infrastructure posture**

Use the [worksheet tool](workshop-tool.md) provided in the Zero Trust Workshop to help assess your current infrastructure security state. We have an automated Zero Trust Assessment tool currently in preview for the Identity and Devices pillars. It's not yet available for infrastructure assessment. [Learn more](/security/zero-trust/assessment/overview).