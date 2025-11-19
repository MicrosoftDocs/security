---
title: Zero Trust Assessment Overview
description: Explore the Zero Trust Assessment to automate security checks, implement industry standards, and strengthen your organization’s Zero Trust architecture.

ms.service: security
ms.subservice: zero-trust
ms.topic: overview
ms.date: 10/30/2025

ms.author: joflore
author: MicrosoftGuyJFlo
manager: dougeby
ms.reviewer: joflore
---
# What is the Zero Trust Assessment?

We publish extensive guidance on how to configure [Microsoft Entra](/entra/fundamentals/configure-security) and [Microsoft Intune](/intune/intune-service/protect/zero-trust-configure-security) for increased security, but manually checking these against a tenant's configuration can be time-consuming and error-prone. The Zero Trust Assessment transforms this process with automation to test for hundreds of security configuration items aligned with the Secure Future Initiative (SFI) and Zero Trust pillars, then guides you through remediation steps to help operationalize Zero Trust principles.

These tests are drawn from trusted sources in cybersecurity, including:

- Industry standards like those developed by NIST, CISA, and CIS
- Microsoft's internal security baselines that protect Microsoft's own infrastructure  
- Real-world customer insights from thousands of security implementations  

:::image type="content" source="media/results-overview.png" alt-text="Screenshot of a sample report output from the Zero Trust Assessment tool." lightbox="media/results-overview-full.png":::

## Why run this assessment?

Running this assessment helps you confirm you've configured a strong baseline of security for your tenant. It lets you know where you might need to make investments and where you already align with best practices. From this baseline, you might implement even stronger or more advanced controls.

## Open source and transparent

**See exactly what the assessment does.** The entire codebase is open source and available for review:

- View the source code: [GitHub repository](https://github.com/microsoft/zerotrustassessment/tree/main/src/powershell)
- Report issues: [GitHub issues](https://github.com/microsoft/zerotrustassessment/issues)
- Contribute improvements: Community contributions welcome

> [!div class="nextstepaction"]
> [Run the assessment](./get-started.md)

## Related content

- Learn more about the recommended controls for [Microsoft Entra](/entra/fundamentals/configure-security) and [Microsoft Intune](/intune/intune-service/protect/zero-trust-configure-security).
- Get started with [running your first assessment](get-started.md)
- Explore the [Secure Future Initiative](https://www.microsoft.com/trust-center/security/secure-future-initiative) pillars.
- Review the [Zero Trust maturity model](../zero-trust-overview.md)
