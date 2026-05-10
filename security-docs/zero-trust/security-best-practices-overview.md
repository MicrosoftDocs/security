---
title: Microsoft security best practices overview
description: Overview of Microsoft security best practices
ms.author: raynew
author: rayne-wiselman
ms.topic: article 
ms.service: security
ms.subservice: zero-trust
ms.date: 04/29/2026

#customer intent: As a Microsoft security platform adopter, I want to understand the range of security best practices that drive Microsoft security guidance.
---


# Microsoft security best practices

Microsoft security best practices are designed to help organizations protect their digital estates by reducing risk, improving resilience, and enabling secure productivity. 

- At the core of these best practices is the [Zero Trust security model](/zero-trust-overview). Zero Trust assumes that threats exist both inside and outside the network, and emphasizes verifying every access request, enforcing least privilege access, and segmenting resources as we assume breach.

Zero Trust principles are reinforced through a combination of engineering best practices, frameworks, benchmarks, and assessment tools.

- **[Microsoft's Secure Future Initiative (SFI)](sfi/secure-future-initiative-overview.md)**
    A series of best practices and security learning based on Microsoft's multi-year efforts to increasingly secure the way in which we design, build, test, and operate our products. SFI provides a series of best practice patterns that you can learn from and implement. SFI tackles security by pillars. Objectives for each pillar align to one or more [NIST Cybersecurity Framework functions](sfi/secure-future-initiative-overview.md#sfi-pillars-zero-trust-and-nist).
- **[Microsoft Entra security recommendations](/entra/fundamentals/configure-security)** 
    These identity recommendations map to SFI themes. They're included in the [Zero Trust Assessment tool](assessment/overview.md) that can be used to assess your current security and identity posture. 
- **[Microsoft Intune device security recommendations](/intune/intune-service/protect/zero-trust-configure-security)**
- - **[Azure networking security best practices](/azure/networking/security/zero-trust-network-security)**
- **[Data security best practices](/purview/zero-trust-microsoft-purview)**
    All of these recommendations and best practices are included in the [Zero Trust Assessment tool](assessment/overview.md).

- The **[Microsoft Cloud Security Benchmark (MCSB)](/security/benchmark/azure/overview)** provides a series of best practices and recommendations for improving the security of workloads, data, and services on Azure. 
- Other Microsoft Defender products such as [Defender for Cloud](/defender-for-cloud/concept-cloud-security-posture-management) and [Security Exposure Management](/security-exposure-management/microsoft-security-exposure-management), and [Microsoft Purview Compliance Manager](/purview/compliance-manager) also monitor and assess your enterprise security posture, providing actionable security and compliance insights and recommendations.
- External best practices and framework also emphasize Zero Trust security principles. [Learn more](security-zero-trust-frameworks.md).


## What's next?

Use the links above to dig more deeply into different types of security best practices. Or:

- To kick off by assessing your current security posture, start with [Zero Trust assessment](assessment/overview.md).
- To get started with structured adoption, follow our [Zero Trust adoption path](security-adoption-model.md).
- To dive into critical security outcomes that business leaders typically focus on, start with our [business scenarios](security-adoption-business-scenarios-overview.md).
To start directly with implementation for business solutions and technical pillars such as devices and data, review [implementing technical solutions](implement-overview.md).
