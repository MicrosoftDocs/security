---
title: Develop using Zero Trust principles
description: As a developer, you should design your apps using Zero Trust principles to improve application security.
ms.date: 07/20/2021
ms.service: security
author: janicericketts
ms.author: jricketts
ms.topic: conceptual
# Customer intent: As a developer, I want to understand the guiding principles of Zero Trust so that I can improve security in applications that I design.
---

# Develop using Zero Trust principles

As an application developer, you play a key role in organizational security. An application and its developers can no longer assume that the network perimeter is secure. Compromised applications can impact the entire organization.

Today, organizations are deploying new security models that effectively adapt to the complexity of the modern environment, embraces the mobile workforce, and protects people, devices, applications, and data wherever they are located. This is the core of [Zero Trust](../zero-trust-overview.md). Instead of believing everything behind the corporate firewall is safe, the Zero Trust model assumes breach and verifies each request as though it originated from an uncontrolled network. Regardless of where the request originates or what resource it accesses, the Zero Trust model teaches us to "never trust, always verify."

While Zero Trust is not a replacement for security fundamentals, with work originating from anywhere on any device, it is essential that you design your applications to incorporate Zero Trust principles throughout your development cycle.

## Why develop with a Zero Trust perspective?

* We've seen a rise in the level of sophistication of cybersecurity attacks.
* The "work from anywhere" workforce has redefined the security perimeter. Data is being accessed outside the corporate network and shared with external collaborators such as partners and vendors.
* Corporate applications and data are moving from on-prem to hybrid and cloud environments. Traditional network controls can no longer be relied on for security. Controls need to move to where the data is: on devices and inside apps.

The development guidance in this section will help you to increase security, reduce the blast radius of a security incident, and swiftly recover by leveraging Microsoft technology.

:::image type="content" source="../media/diagram-zero-trust-security-elements.png" alt-text="Diagram of elements of visibility, automation, and orchestration in Zero Trust." border="false":::

## Next steps

* [What do we mean by Zero Trust compliance?](identity-zero-trust-compliance.md)
* [Zero Trust identity and access management development best practices](identity-iam-development-best-practices.md)
* [Using standards-based development methodologies](identity-standards-based-development-methodologies.md)
* [Developer and administrator responsibilities for application registration, authorization, and access](identity-developer-administrator-responsibilities.md)
* [Building apps with a Zero Trust approach to identity](identity.md)
* [Identity and account types for single- and multi-tenant apps](identity-supported-account-types.md)
* [Providing application identity credentials when there is no user](identity-non-user-applications.md)
