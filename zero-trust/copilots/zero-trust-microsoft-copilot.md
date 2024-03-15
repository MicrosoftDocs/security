---
title: Apply principles of Zero Trust to Microsoft Copilot
description: Learn how to secure Microsoft Copilot with Zero Trust principles. 
ms.date: 01/26/2024
ms.service: security
author: bcarter
ms.author: bcarter
ms.topic: conceptual
ms.collection: 
  - M365copilot 
  - msftsolution-copilot
  - msftsolution-scenario
  - zerotrust-solution
  - zerotrust-azure
---

# Apply principles of Zero Trust to Microsoft Copilot

**Summary:** To apply Zero Trust principles to Microsoft Copilot, you need to determine your desired configuration of Microsoft Copilot to identify the data sets that can be analyzed and summarized, and then apply Zero Trust principles to those data sets and their access.

## Introduction

Before you introduce Microsoft Copilot for Microsoft 365 or Copilot into your environment, Microsoft recommends that you build a strong foundation of security. Fortunately, guidance for a strong security foundation exists in the form of [Zero Trust](zero-trust-overview.md). The Zero Trust security strategy treats each connection and resource request as though it originated from an uncontrolled network and a bad actor. Regardless of where the request originates or what resource it accesses, Zero Trust teaches us to "never trust, always verify."

Before you introduce Microsoft Copilot into your environment, Microsoft recommends that you build a strong foundation of security. Fortunately, guidance for a strong security foundation exists in the form of [Zero Trust](../zero-trust-overview.md). The Zero Trust security strategy treats each connection and resource request as though it originated from an uncontrolled network and a bad actor. Regardless of where the request originates or what resource it accesses, Zero Trust teaches us to "never trust, always verify."

Microsoft Copilot is an AI companion that works everywhere you do and intelligently adapts to your needs. You can ask Microsoft Copilot questions, known as prompts, and it will return results. You can access Microsoft Copilot in Windows, Edge, Bing, Microsoft 365, and the Copilot mobile app.

For Copilot in Windows, Edge, Bing, and the [Copilot mobile app](https://www.microsoft.com/copilot-app), responses to your prompts use internet data and can:

- Chat using text, voice, and images.
- Summarize documents and web pages.
- Use plugins and Copilot GPTs.

With a license for Copilot for Microsoft 365, you will see a **Work/Web** toggle control in the Edge browser, Windows, and Bing search that allows you to switch between using:

- Graph-grounded prompts that are sent to Copilot for Microsoft 365 (toggle set to **Work**).
- Web-grounded prompts that primarily use internet data (toggle set to **Web**).

Here’s an example for Microsoft Bing.

>> Add

The exception is Copilot in Edge, which can summarize some types of data in open browser tabs if enabled.

## Logical architecture

 The following diagram shows the logical architecture components.

<!---

:::image type="content" source="../media/copilot/logical-architecture-microsoft-365-copilot.svg" alt-text="Diagram of the logical architecture for Copilot." lightbox="../media/copilot/logical-architecture-microsoft-365-copilot.svg":::

--->


In the diagram:

- 

## Copilot for Microsoft 365


## Copilot in Edge


## Microsoft Copilot configurations and accessible organization data


## Next steps


## References

Refer to these links to learn about the various services and technologies mentioned in this article.

