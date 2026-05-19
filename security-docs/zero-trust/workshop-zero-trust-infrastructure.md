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

In a Zero Trust architecture, infrastructure security focuses on protecting the foundational compute and platform resources that host applications and services across multicloud and on-premises environments. Rather than implicitly trusting infrastructure, this pillar ensures that servers, containers, storage, and platform services are continuously assessed, hardened, and monitored under an assume-breach mindset.

Infrastructure pillar guidance focuses on managing security posture, protecting workloads at runtime, governing infrastructure configurations, controlling administrative access, and integrating infrastructure signals into security operations.

## Workshop implementation

The Infrastructure workshop covers the implementation areas summarized in the table.

**Area** | **Details**
--- | ---
**Establish infrastructure security posture management (CSPM)** |   Continuously assess infrastructure resources for misconfigurations, policy violations, and exposure risks. <br/><br/>Use posture management capabilities to identify configuration drift, enforce governance policies, and prioritize remediation across cloud and hybrid environments.
**Protect compute workloads across virtual machines and containers** |   Secure multicloud virtual machines, container environments, and on-premises servers using workload protection capabilities.<br/><br/> Continuously monitor security posture, detect threats, and remediate vulnerabilities affecting compute workloads.
**Secure and govern platform services and control planes**  |  Apply security controls to platform services such as storage, databases, and application services.<br/><br/> Govern access, configurations, and exposure of platform resources to reduce risk across cloud control planes.
**Assess and manage vulnerabilities**  |  Continuously scan infrastructure resources for vulnerabilities and configuration issues. <br/><br/>Prioritize and remediate findings based on risk, and tune alerts to reduce noise while maintaining visibility.
**Control access to infrastructure resources**  |  Enforce least-privilege access using role-based access control (RBAC) and just-in-time (JIT) access.<br/><br/> Integrate identity-based access controls to ensure administrative access is granted only when required and scoped appropriately.
**Harden configurations and enforce security baselines**  |   Define and apply secure configuration baselines across infrastructure resources. <br/><br/>Standardize settings for compute, networking, and platform services to prevent misconfigurations and ensure consistent protection.
**Monitor workloads and detect threats at runtime**  |  Continuously monitor infrastructure for suspicious activity and security threats. <br/><br/>Use runtime protection and analytics to detect attacks targeting virtual machines, containers, and platform services.
**Integrate infrastructure signals into security operations (SecOps)**  |  Stream posture findings, runtime alerts, and threat signals into centralized monitoring and response systems. <br/><br/>Correlate infrastructure data with identity, device, network, and data signals to support investigation and response.


## What's next?

Begin the [Infrastructure workshop](https://zerotrust.microsoft.com/).