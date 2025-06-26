---
title: Overview - Use Zero Trust security to prepare for AI companions, including Microsoft Copilots
description: Learn how to apply the principles of Zero Trust to your environment to prepare for AI tools that include Web-grounded prompts, Microsoft 365-grounded prompts, and prompts grounded in data from your security tools.
ms.date: 02/06/2025
ms.service: security
author: BrendaCarter
ms.author: bcarter
ms.topic: overview
ms.collection: 
  - msftsolution-copilot
  - msftsolution-scenario
  - zerotrust-m365-security
  - zerotrust-solution
  - zerotrust-copilot
  - msec-ai-copilot
---

# Use Zero Trust security to prepare for AI companions, including Microsoft Copilots

Security, especially data protection, is a top concern when introducing AI tools into an organization. Security recommendations for AI are anchored in Zero Trust. As a leader in security, Microsoft provides a practical roadmap and clear guidance for Zero Trust. By implementing recommended protections as you introduce AI tools and companions, you're building a foundation of Zero Trust security. 

This series of articles helps you apply the [principles of Zero Trust](../zero-trust-overview.md) to Microsoft’s Copilots and similar AI companions. Zero Trust is a security strategy. It isn't a product or a service, but an approach in designing and implementing the following set of security principles:

- Verify explicitly
- Use least privileged access
- Assume breach

Implementing the Zero Trust "never trust, always verify" mindset requires changes to cloud infrastructure, deployment strategy, and implementation.

## Layer in protections for AI companions

Microsoft helps you prepare for AI tools and companions and build a Zero Trust foundation at the same time. Take a staged approach starting with protections for web-grounded prompts and maturing to protections for Microsoft 365 graph-grounded prompts. Protections for prompts grounded with data provided by your security tools (Security Copilot) focus on tuning up least privilege practices and honing threat protection. 

:::image type="content" source="../media/copilot/microsoft-copilot-grounding.svg" alt-text="Mapping of Copilots to web-grounded prompts, Microsoft 365-grounded prompts, and prompts grounded with security tools." lightbox="../media/copilot/microsoft-copilot-grounding.svg":::

In the illustration:
- Web-grounded prompts are issued by Copilot Chat. Microsoft 365 Copilot includes the features of Copilot Chat (for example, when the work/web toggle is set to web). 
- Microsoft 365 graph-grounded prompts are issued by Microsoft 365 Copilot (for example, when the work/web toggle is set to work).
- Prompts grounded with your security tools are issued by Microsoft Security Copilot. 

## Get started with Zero Trust by preparing your environment for AI companions

You can build a Zero Trust foundation by preparing your environment for AI companions. 

:::image type="content" source="../media/copilot/use-zero-trust-to-prepare-for-ai.svg" alt-text="Mapping of Zero Trust work to preparing for AI companions." lightbox="../media/copilot/use-zero-trust-to-prepare-for-ai.svg":::

The following table summarizes the illustration and links to articles for implementing the recommended protections.

| Prepare for | Protections | See these Zero Trust articles |
| --- | --- | --- |
|Web-grounded prompts  |User accounts, devices, and some app data.   | [Copilot Chat](zero-trust-microsoft-copilot.md)    |
|Microsoft 365 graph-grounded promtps |Includes the previous protections plus more robust protection for app data and cloud apps. It also includes adding in threat protection.  | [Microsoft 365 Copilot](zero-trust-microsoft-365-copilot.md)    |
|Prompts grounded with security tools  |Focuses on tuning up least privilege access, a key principle of Zero Trust.    | [Microsoft Security Copilot](zero-trust-microsoft-copilot-for-security.md)    |


For more information on implementing Zero Trust, see the [Zero Trust Guidance Center](/security/zero-trust/). 



## References

- [Microsoft Copilot Chat](/copilot/)
- [Microsoft 365 Copilot](/microsoft-365-copilot/)
- [Data, Privacy, and Security for Microsoft 365 Copilot](/microsoft-365-copilot/microsoft-365-copilot-privacy)
