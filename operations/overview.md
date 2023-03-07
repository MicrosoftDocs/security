---
title: Security operations  | Microsoft Docs
description: Learn about security operations and how they detect, respond, and recover the system when it's attacked.
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
ms.topic: article
ms.service: microsoft-365-security
---

# Security operations 

Security operations (SecOps) maintain and restore the security assurances of the system as live adversaries attack it. The NIST Cybersecurity Framework describes the SecOps functions of Detect, Respond, and Recover well.

- **Detect** - SecOps must detect the presence of adversaries in the system, who are incentivized to stay hidden in most cases, allowing them to achieve their objectives unimpeded. This can take the form of reacting to an alert of suspicious activity or proactively hunting for anomalous events in the enterprise activity logs.

- **Respond** - Upon detection of potential adversary action or campaign, SecOps must rapidly investigate to identify whether it's an actual attack (true positive) or a false alarm (false positive) and then enumerate the scope and goal of the adversary operation.

- **Recover** - The ultimate goal of SecOps is to preserve or restore the security assurances (confidentiality, integrity, availability) of business services during and after an attack.

The most significant security risk most organizations face is from human attack operators (of varying skill levels). Risk from automated/repeated attacks have been mitigated significantly for most organizations by signature and machine learning based approaches built into anti-malware. Although it must be noted that there are notable exceptions like Wannacrypt and NotPetya, which moved faster than these defenses).

While human attack operators are challenging to face because of their adaptability (vs. automated/repeated logic), they're operating at the same "human speed" as defenders, which help level the playing field.

SecOps (sometimes referred to as a Security Operations Center (SOC)) has a critical role to play in limiting the time and access an attacker can get to valuable systems and data. Each minute that an attacker has in the environment allows them to continue to conduct attack operations and access sensitive or valuable systems.

