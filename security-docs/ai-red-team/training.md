---
title: 'AI Security Training: Case Studies and Tools for Generative AI'
description: Secure generative AI systems with Microsoft's AI Red Teaming 101 series. Learn vulnerabilities, attack techniques, and defense strategies. Gain hands-on experience.
ms.service: security
ms.subservice: ai-red-team
ms.topic: how-to
ms.date: 07/09/2025
ms.author: joflore
author: MicrosoftGuyJFlo
ms.reviewer: sayoung
ms.custom:
  - ai-gen-docs-bap
  - ai-gen-title
  - ai-seo-date:07/03/2025
  - ai-gen-description
---
# AI red teaming training series: securing generative AI systems

Microsoft's **AI Red Teaming 101 training series** helps professionals secure generative AI systems against emerging threats. This series dives into vulnerabilities, attack techniques, and defense strategies, providing actionable insights and hands-on experience. Whether you're a security expert, machine learning engineer, or business leader, you'll gain practical knowledge through real-world case studies, modular episodes, and automated testing tools. Explore topics like prompt injection attacks, multi-turn adversarial techniques, and scalable defense methods to enhance your AI security expertise.

> [!VIDEO https://www.youtube-nocookie.com/embed/DwFVhFdD2fs?si=YyA6OMOMNFMwddjP]

## Why watch this training series

Get actionable advice to help identify, exploit, and defend against critical vulnerabilities in generative AI systems. Learn best practices, techniques, and guidance based on real-world lessons from Microsoft’s AI Red Team.

## Who should watch this training series

The training series is useful for security teams, ML engineers, AI practitioners, and business leaders working with AI. It primarily focuses on:

- Security professionals: learn about AI-specific attack vectors and defense strategies.
- ML practitioners and AI engineers: add security testing to AI development workflows.
- Enterprise and security architects: create secure AI systems and explore emerging threats.

> [!TIP]
> The AI Red Teaming 101 videos are modular, so you can jump to any section of interest or start at the beginning and watch them all. [Download the slides](https://download.microsoft.com/download/5b4d1684-798f-4040-ae80-eb8e1a1b3411/AI-Red-Teaming-101.pptx), and follow along at your own pace.

## What's in the training series

The training series gives guidance on understanding generative AI vulnerabilities, executing attack techniques, and implementing defensive measures. The workshop includes hands-on demonstrations, real-world case studies, and automated testing tools based on Microsoft's production AI security practices. 

> [!TIP] 
> All episodes include [hands-on demonstrations and access to Microsoft's red teaming labs](https://aka.ms/AIRTlabs) to gain practical experience. 

### Introduction and Fundamentals 

**Episode 1: What is AI red teaming?** - Introduction to AI red teaming fundamentals, key risks in generative AI, and the mission of Microsoft's AI red team 

> [!VIDEO e2acb1fe-aab3-4b81-a0f9-ccd73542425b]

**Episode 2: How Generative AI Models Work** - Understanding model architecture, training stages, and why these models create unique security risks 

> [!VIDEO a619383f-621a-4463-b1b2-53c7e468d30e]

### Part A - Core Attack Techniques 

**Episode 3: Direct prompt injection explained** - How attackers manipulate model behavior by injecting malicious instructions, including real-world case studies such as the $1 SUV chatbot attack 

> [!VIDEO 33675c36-62bb-44d3-b7ea-8cb16fad1736]

**Episode 4: Indirect Prompt Injection Explained** - Stealthy attacks where malicious instructions are hidden in external data sources like emails, websites, or databases 

> [!VIDEO acd3e4be-daea-4b82-9f7e-13008a6f5f6f]

**Episode 5: Single-Turn Attacks** - Advanced prompt engineering techniques including persona hacking, emotional manipulation, and filter evasion with encoding tricks 

> [!VIDEO d80bbcb1-cfbb-4ef9-96c9-538006d39bce]

**Episode 6: Multi-Turn Attacks** - techniques like Skeleton Key and Crescendo that gradually steer models toward bypassing safety protections 

> [!VIDEO 7dbc1b1f-e022-48d3-aa70-e4501da7bc3a]

### Part B - Defense and Mitigation 

**Episode 7: Defending against attacks** - Mitigation strategies and guardrail techniques, including Microsoft's spotlighting defense methods (delimiting, data marking, and encoding) 

> [!VIDEO 96f37319-2a2c-4c05-81a7-1cb296f8cd9d]

### Part C - Automation and Scale 

**Episode 8: Automating AI red teaming with PyRIT** - Introduction to Microsoft's open-source tool for automating and scaling adversarial testing of generative AI systems, the Python Risk Identification Tool (PyRIT) 

> [!VIDEO 1ec47c63-de7b-4695-9394-192b5bff8c79]

**Episode 9: Automating Single-Turn Attacks** - Hands-on demonstration of configuring datasets, targets, and scoring logic to send many prompts at once using PyRIT 

> [!VIDEO 54ac783c-7743-4749-970f-f71fd0d27e92]

**Episode 10: Automating Multi-Turn Attacks** - Advanced automation techniques for multi-turn conversations, including adversarial model conversations and testing both text and image generation systems 

> [!VIDEO 4f666c5d-fd5f-4a69-be7b-d80cfc1cc829]

## What you learn 

After completing this training series, you'll understand: 

- Fundamentals of AI red teaming versus traditional red teaming approaches 
- Core vulnerabilities in generative AI systems, like prompt injection and model misalignment 
- Attack techniques, from simple prompt manipulation to sophisticated multi-turn adversarial strategies 
- Defense strategies, including proven mitigation techniques like Microsoft's Spotlighting methods 
- Automation tools for scaling red teaming efforts using PyRIT and other open-source tools 
- Real-world applications with hands-on labs and case studies from Microsoft's production AI security work 

## Related content

- [Hands-on labs & tools](https://aka.ms/AIRTlabs)
- [Microsoft AI red team overview](https://aka.ms/airedteam)
- [PyRIT GitHub repository](https://aka.ms/PyRIT)
