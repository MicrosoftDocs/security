----
title: Protect tenants and isolate systems in the Microsoft Secure Future Initiative (SFI)
description: Learn how to protect tenants and isolate systems in Microsoft's Secure Future Initiative (SFI).
ms.date: 11/03/2025
ms.service: security
author: rayne-wiselman
ms.author: raynew
ms.subservice: zero-trust
ms.topic: conceptual
ms.collection:
  - highpri
  - zerotrust
  - sfi-zerotrust
---

# Protect tenants and isolate systems in SFI

The [Secure Future Initiative (SFI) initiative](secure-future-initiative-overview.md) launched in November 2023 as a multiyear effort to increasingly secure the way in which Microsoft designs, builds, tests, and operates its products and services.

SFI architecture design focuses on a set of security principles that are adopted and integrated into Microsoft culture and governance. These security principles are applied to a set of engineering pillars by means of processes, standards, and continuous improvements.

This article summarizes the "Protect tenants and isolate systems" SFI pillar.

## Before you start

- [Review](secure-future-initiative-overview.md#sfi-pillars-zero-trust-and-nist) the SFI pillars
- [Review tthe latest progress on pillar objectives](secure-future-initiative-whats-new.md#pillar-progress) in What's New.


## Pillar and objectives 

The aim of the "Protect identities and secrets" pillar is to contain potential threat blast radius by preventing lateral movement or privilege escalation. It ensures that tenant-level security boundaries are correctly configured, hardened, and isolated. 

Microsoft objectives for this pillar are summarized in the following table. You can see how each objective maps toZero Trust principles, and to  [NIST CSF functions and categories](https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.29.pdf).


**Objective** | **Zero Trust** | **NIST mapping**
--- | --- | --- 
**1. Remove legacy systems that risk security**<br/><br/> Maintain the security posture and commercial relationship of tenants by removing all unused, aged, or legacy systems. | **Verify explicitly**: All identity and resource systems are authenticated and validated through modern control planes.<br/><br/>**Use least privilege**: Eliminates old systems without modern, fine‑grained controls. <br/><br/>**Assume breach**: Removes legacy trust paths and minimizes blast radius. | **ID.AM-02**: Inventory of organizational resources. Track tenant and resource onboarding and disused assets.<br/><br/>**ID.AM-08**: Resource lifecycle management. Track, manage, and decommission tenants/apps safely. <br/><br/>**PR.PS-01**: Platform Security. Secure platforms and services on a modern foundation.
**2. Secure all tenants and their resources**<br/><br/> Protect Microsoft, acquired, and employee-created tenants, commerce accounts, and tenant resources in accordance with security best practice baselines. |  **Verify explicitly**: Authenticate all tenant‑to‑tenant interactions.<br/><br/>**Use least privilege**: Policies and segmentation limit permissions across environments. <br/><br/>**Assume breach**: Tenant boundaries assume potential compromise and are designed to contain lateral movement. | **ID.AM-08**: Resource lifecycle management. Maintain defined tenant resource lifecycles. <br/><br/>**PR.AA-01**: Access control policy. Define tenant access policies.<br/><br/>**PR.AA-05**: Separation of duties. Limit administrative privilege across tenants.<br/><br/>**PR.IR-01**: Improve platform resilience against misuse or misconfiguration. 
**3. Higher security for Entra ID apps**<br/><br/>Manage Microsoft Entra ID applications with a high and consistent security bar. |  **Verify explicitly**: Enforce strong authentication and app vetting.<br/><br/>**Use least privilege**: App permissions restricted to minimal necessary rights. <br/><br/>**Assume breach**: App access designed with containment and monitoring. | **PR.AA-01**: Access control policy. Govern app access consistently.<br/><br/>**PR.AA-03**: Access enforcement. Enforce app authentication controls.
**4. Eliminate identity lateral movement**<br/><br/>Eliminate identity lateral movement pivots between tenants, environments, and clouds.  | **Verify explicitly**: Validate every token and trust boundary crossing.<br/><br/>**Use least privilege**: imit identity reuse and privilege escalation across tenants. <br/><br/>**Assume breach**: Design boundaries to contain identity misuse. | **PR.AA-03**: Access enforcement. Block unauthorized lateral authentication.
**5. Continuous least-privilege enforcement**<br/><br/>Ensure continuous least-privilege access enforcement for apps and users.  | **Verify explicitly**: Policies ensure least privilege decisions are verified at every access.<br/><br/>**Use least privilege**: Core outcome of this objective — enforce only necessary permissions. | **PR.AA-03**: Access enforcement. Enforce minimal privileges.
**6. Secure devices used for access**<br/><br/> Adopt fine-grained partitioning of identity signing keys and platform keys. Ensure that only secure, managed, healthy devices are granted access to Microsoft tenants.  | **Verify explicitly**: ach device identity is validated and continuously assessed.<br/><br/>**Use least privilege**: Device posture gating ensures minimal risk access. | **PR.PS-01**: Platform Security. Devices and endpoints hardened per secure baseline to reduce risk.<br/><br/>**PR.IR‑01**: Infrastructure Resilience. Endpoints resilient to compromise and aligned to service baselines


## Next steps

[Learn about](secure-future-initiative-guidance.md) adopting Microsoft SFI best practices.