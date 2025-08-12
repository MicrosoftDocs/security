---
title: Zero Trust identity and access management best practices
description: Learn identity and access management (IAM) best practices for application development to  ensure Zero Trust compliance.
author: janicericketts
ms.author: jricketts
ms.topic: conceptual
ms.service: zero-trust
ms.date: 02/24/2025
ms.collection:
  - zerotrust-dev
ms.custom:
  - template-concept
  - sfi-ropc-nochange
# Customer intent: As a developer, I want to learn best practices for my application development lifecycle so that I can create secure applications that are Zero Trust compliant, starting with identity and access management (IAM).
---
# Zero Trust identity and access management development best practices

This article helps you, as a developer, to understand identity and access management best practices for your application development lifecycle. You start developing secure, [Zero Trust compliant](identity-zero-trust-compliance.md) applications with identity and access management (IAM).

The [Zero Trust](overview.md) security framework uses the principles of explicit verification, least privileged access, and assuming breach. Secure users and data while allowing for common scenarios like access to applications from outside the network perimeter. Reduce reliance upon implicit trust to interactions behind a secure network perimeter that can become vulnerable to security attacks.

## Industry security trends affect application requirements

While Zero Trust implementation continues to evolve, each organization's journey is unique. It often begins with user and application identity. Here are policies and controls that many organizations prioritize as they roll out Zero Trust:

- **Implement credential hygiene and rotation policies for apps and services.** When bad actors compromise secrets such as certificates or passwords, they can achieve a depth of system access to acquire tokens under the guise of an app's identity. They then access sensitive data, move laterally, and establish persistence.
- **Roll out strong authentication.** IT administrators are configuring policies that require multifactor authentication and passwordless FIDO2 devices.
- **Restrict user consent to apps with low-risk permissions to verified publisher apps.** Access to data in APIs like Microsoft Graph allow you to build rich applications. Organizations and customers evaluate your app's permission requests and trustworthiness before granting consent. IT admins are embracing the principle of verify explicitly by requiring publisher verification. They apply the principle of least privilege by only allowing user consent for low-risk permissions.
- **Block legacy protocols and APIs.** IT admins are blocking older authentication protocols such as "Basic authentication" and requiring modern protocols like OpenID Connect and OAuth2.

## Use trusted, standards-based authentication libraries

To increase application portability and security, develop your application with known and accepted standards and libraries. Trusted, standards-based authentication libraries stay up-to-date so that your apps are responsive to the latest technologies and threats. [Standards-based development methodologies](identity-standards-based-development-methodologies.md) provides an overview of supported standards and their benefits.

Rather than using protocols with known vulnerabilities and extensive documentation, develop your application with libraries such as Microsoft Authentication Library (MSAL), [Microsoft Identity Web authentication library](/entra/msal/dotnet/microsoft-identity-web/), and [Azure Software Developer Kits (SDK)](/entra/identity/managed-identities-azure-resources/qs-configure-sdk-windows-vm#azure-sdks-with-managed-identities-for-azure-resources-support). MSAL and Software Developer Kits (SDK) allow you to use these features without needing to write extra code:

- Conditional access
- Device registration and management
- Passwordless and FIDO2 authentication

MSAL and [Microsoft Graph](/graph/overview) are your best choices for developing Microsoft Entra applications. MSAL developers ensure compliance with protocols. Microsoft optimizes MSAL for efficiency when working directly with Microsoft Entra ID.

## Register your apps in Microsoft Entra ID

Follow the [Security best practices for application properties in Microsoft Entra ID](/entra/identity-platform/security-best-practices-for-app-registration). Application registration in Microsoft Entra ID is critical because misconfiguration or lapse in your application's hygiene can result in downtime or compromise.

Application properties that improve security include redirect URI, access tokens (never use with implicit flows), certificates and secrets, application ID URI, and application ownership. Conduct periodical security and health assessments similar to Security Threat Model assessments for code.

## Delegate identity and access management

Develop your application to use tokens for explicit identity verification and access control that your customers define and manage. Microsoft advises against developing your own username and password management systems.

Keep credentials out of your code so that IT admins can rotate credentials without bringing down or redeploying your app. Use a service such as [Azure Key Vault](/azure/key-vault/general/authentication-fundamentals) or [Azure Managed Identities](/entra/identity/managed-identities-azure-resources/overview) to delegate IAM.

## Plan and design for least privilege access

A key principle of Zero Trust is least privilege access. Sufficiently develop and document your application so your customers can successfully configure least privilege policies. When supporting tokens and APIs, provide your customers with good documentation of resources that your application calls.

Always provide the least privilege required for your user to perform specific tasks. For example, use granular scopes [in Microsoft Graph](/graph/permissions-reference).

Explore scopes in [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer) to call an API and examine required permissions. They're displayed in order from lowest to highest privilege. Picking the lowest possible privilege ensures that your application is less vulnerable to attacks.

To reduce application vulnerability and security breach blast radius should compromise occur, follow the guidance in [Enhance security with the principle of least privilege](/entra/identity-platform/secure-least-privileged-access).

## Securely manage tokens

When your application requests tokens from Microsoft Entra ID, securely manage them:

- Validate that they're properly scoped to your application.
- Appropriately cache them.
- Use them as intended.
- Handle token issues by checking for error classes and coding appropriate responses.
- Instead of directly reading access tokens, view their scopes and details in token responses.

## Support Continuous Access Evaluation (CAE)

Continuous Access Evaluation [(CAE)](/entra/identity-platform/app-resilience-continuous-access-evaluation) allows Microsoft Graph to quickly deny access in response to security events. Examples include these tenant administrator activities:

- Delete or disable a user account.
- Enable multifactor authentication (MFA) for a user.
- Explicitly revoke a user's issued tokens.
- Detect a user moving to high-risk status.

When you support CAE, tokens that Microsoft Entra ID issues to call Microsoft Graph are valid for 24 hours instead of the standard 60 to 90 minutes. CAE adds resiliency to your app by enabling MSAL to proactively refresh the token well before the token expires.

## Define app roles for IT to assign to users and groups

[App roles](/entra/identity-platform/howto-add-app-roles-in-apps) help you to implement role-based access control in your applications. Common examples of app roles include Administrator, Reader, and Contributor. Role-based access control allows your application to restrict sensitive actions to [users or groups based on their defined roles](configure-tokens-group-claims-app-roles.md).

## Become a verified publisher

As a [verified publisher](/entra/identity-platform/publisher-verification-overview), verify your identity with your Microsoft Partner Network account and completed the established verification process. For developers of multitenant apps, being a verified publisher helps build trust with IT administrators in customer tenants.

## Next steps

- [Customize tokens](zero-trust-token-customization.md) describes the information that you can receive in Microsoft Entra tokens. Learn how to customize tokens to improve flexibility and control while increasing application Zero Trust security with least privilege.
- [Configure group claims and app roles in tokens](configure-tokens-group-claims-app-roles.md) describes how to configure your apps with app role definitions and assign security groups to app roles. This approach improves flexibility and control while increasing application Zero Trust security with least privilege.
- [Building apps with a Zero Trust approach to identity](identity.md) provides an overview of permissions and access best practices.
- The [Identity integrations](../integrate/identity.md) guide explains how to integrate security solutions with Microsoft products to create Zero Trust solutions.
- [Developer and administrator responsibilities for application registration, authorization, and access](identity-developer-administrator-responsibilities.md) helps you to better collaborate with your IT Pros.
- [Supported identity and account types for single- and multitenant apps](identity-supported-account-types.md) explains how you can choose if your app allows only users from your Microsoft Entra ID) tenant, any Microsoft Entra tenant, or users with personal Microsoft accounts.
- [Authorization best practices](developer-strategy-authorization-best-practices.md) helps you to implement the best authorization, permission, and consent models for your applications.
- [API Protection](protect-api.md) describes best practices for protecting your API through registration, defining permissions and consent, and enforcing access to achieve your Zero Trust goals.
