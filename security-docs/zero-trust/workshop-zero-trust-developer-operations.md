---
title: Microsoft Zero Trust Workshop - DevOps
description: Learn about the DevOps pillar in the Microsoft Zero Trust Workshop
ms.date: 04/18/2024
ms.service: security
author: rayne-wiselman
ms.author: raynew
ms.subservice: zero-trust
ms.topic: conceptual
---

# DevOps in the Microsoft Zero Trust Workshop

In a Zero Trust architecture, DevOps security seeks to embed security directly into the software development lifecycle (SDLC) — from code to build, to deployment, to infrastructure. Instead of treating development and operations as separate from security, this pillar ensures that CI/CD pipelines, infrastructure-as-code (IaC), and developer workstations are all secured, governed, and monitored. By doing so, you verify explicitly, use least-privilege access, and assume compromise even in your deployment processes.

SecOps pillar guidance focuses on assessing how build systems access infrastructure and code, security pipelines and automation hardening, configuring identity control and just-in-time access for developer and deployment roles, secrets management, vulnerability assessment and remediation, and Microsoft DevOps governance. The DevOps workshop covers these implementation areas:

- **Control developer/deployment access**: Design permissions for developers, build agents, and deployment identities. Use Access Packages for developer access and apply privileged identity management, just-in-time, just-enough access for dev or deployment accounts. Regularly review and govern group membership and permissions for DevSecOps roles. 
- **Secure developer workstations.environments**: Define and enforce security policies for developer workstations ( secure configurations, least-privilege, required tools etc.). Harden these workstations by applying protection (for example Microsoft Defender for Servers/Microsoft Endpoint) to continuously monitor for risky behaviors.
- **Integrate source control and identity**: Discover existing GitHub (or Azure DevOps) identities and integrate them with Microsoft Entra ID to unify identity management.Remediate non-Entra ID accounts. Ensure that service principals or other pipeline identities are properly governed. 
- **Implement secure CI/CD pipeline practices**: Define how code is published, built, and deployed with security in mind. Deploy GitHub Advanced Security (CodeQL, secret scanning) to detect vulnerabilities in source code. Use Dependabot to automatically manage dependency vulnerabilities. Evaluate and integrate third-party SAST (Static Application Security Testing) and DAST (Dynamic Application Security Testing) tools as needed. 
- **Secure infrastructure and deployment targets**: Harden the target infrastructure for deployments (for example servers and containers) using Defender for Cloud or something similar. Continuously monitor these environments to detect misconfigurations, vulnerabilities, or suspicious activity. 
- **Govern/remediate secrets, credentials, artifacts**: Define a process for regular review of unused or stale credentials. Triage security findings from dev security tools such as CodeQL, scanning, etc., and remediate appropriately.
- **Improve continuously with a posture feedback loop**: Set up processes to continuously review and improve DevOps security posture, including governance, alerting, IAM, and pipeline risk. Make security a priority in DevOps workflows. Ensure that developers and security teams collaborate on threat modeling, secure coding, and pipeline protection.
