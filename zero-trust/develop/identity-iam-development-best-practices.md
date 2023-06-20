---
title: Zero Trust identity and access management development best practices
description: Learn best practices for your application development lifecycle so that you can create secure applications that are Zero Trust compliant, starting with identity and access management (IAM).
author: janicericketts
ms.author: jricketts
ms.service: identity
ms.topic: conceptual
ms.date: 06/20/2023
ms.custom: template-concept
ms.collection:
  - zerotrust-dev
# Customer intent: As a developer, I want to learn best practices for my application development lifecycle so that I can create secure applications that are Zero Trust compliant, starting with identity and access management (IAM).
---
# Zero Trust identity and access management development best practices

This article helps you, as a developer, to understand best identity and access management practices for your application development lifecycle. You start developing secure, [Zero Trust compliant](identity-zero-trust-compliance.md)applications with identity and access management (IAM).

The [Zero Trust](overview.md) security framework uses the principles of explicit verification, least privileged access, and assuming breach. Secure users and data while allowing for common scenarios like access to applications from outside the network perimeter. Reduce reliance upon implicit trust to interactions behind a secure network perimeter that can become vulnerable to security attacks.

## Industry security trends affect application requirements

While Zero Trust implementation continues to evolve, each organization's journey is unique, and often begins with user and application identity. Here are policies and controls that many organizations prioritize as they roll out Zero Trust:

1. **Implement credential hygiene and rotation policies for apps and services.** WWhen attackers compromise secrets such as certificates or passwords, they can achieve a depth of system access to acquire tokens under the guise of an app's identity. They then access sensitive data, move laterally, and establish persistence.
1. **Roll out strong authentication.** IT administrators are configuring policies that require multi-factor authentication and passwordless FIDO2 devices.
1. **Restrict user consent to apps with low-risk permissions to verified publisher apps.** Access to data in APIs like Microsoft Graph allow you to build rich applications. Organizations and customers evaluate your app's permission requests and trustworthiness before granting consent. IT admins are embracing the principle of verify explicitly by requiring publisher verification. They apply the principle of least privilege by only allowing user consent for low-risk permissions.
1. **Blocking legacy protocols and APIs.** IT admins are blocking older authentication protocols such as "Basic authentication" and requiring modern protocols like OpenID Connect and OAuth2.

## Use trusted, standards-based authentication libraries

Develop your application with known and accepted standards and libraries to increase application portability and security. Trusted, standards-based authentication libraries stay up-to-date so that your apps are responsive to the latest technologies and threats. [Using standards-based development methodologies](identity-standards-based-development-methodologies.md) provides an overview of supported standards (OAuth 2.0, OpenID Connect, SAML, WS-Federation, and SCIM) and the benefits of using them with MSAL and the Microsoft identity platform.

Rather than using protocols that can have known vulnerabilities and extensive documentation, develop your application with libraries such as Microsoft Authentication Library (MSAL), [Microsoft Identity Web authentication library](/azure/active-directory/develop/microsoft-identity-web), and [Azure SDKs for managed identities](/azure/active-directory/managed-identities-azure-resources/qs-configure-sdk-windows-vm#azure-sdks-with-managed-identities-for-azure-resources-support). MSAL and SDKs allow you to use these features without needing to write extra code:

- Conditional access
- Device registration and management
- Passwordless and FIDO2 authentication

MSAL and [Microsoft Graph](/graph/overview) are your best choices for developing Azure Active Directory (Azure AD) applications. MSAL developers have done the work for you to ensure compliance with protocols. Microsoft optimizes MSAL for efficiency when working directly with Azure AD.

## Register your apps in Azure AD

Follow the [Security best practices for application properties in Azure Active Directory](/azure/active-directory/develop/security-best-practices-for-app-registration). Application registration in Azure AD is critical because misconfiguration or lapse in your application's hygiene can result in downtime or compromise.

Application properties that improve security include redirect URI, access tokens (never use with implicit flows), certificates and secrets, application ID URI, and application ownership. Conduct periodical security and health assessments similar to Security Threat Model assessments for code.

## Delegate identity and access management

Develop your application to use tokens for explicit identity verification and access control that your customers define and manage. Microsoft advises against developing your own username and password management systems.

Keep credentials out of your code so that IT admins can rotate credentials without bringing down or redeploying your app. Use a service such as [Azure Key Vault](/azure/key-vault/general/authentication-fundamentals) or [Azure Managed Identities](/azure/active-directory/managed-identities-azure-resources/overview) to delegate IAM.

## Plan and design for least privilege access

A key principle of Zero Trust is least privilege access. Sufficiently develop and document your application so your customers can successfully configure least privilege policies. When supporting tokens and APIs, provide your customers with good documentation of resources that your application calls.

Always provide the least privilege required for your user to perform specific tasks. For example, use [incremental consent](/azure/active-directory/azuread-dev/azure-ad-endpoint-comparison#incremental-and-dynamic-consent) to only request permissions when they're necessary and use [granular scopes in Microsoft Graph](/graph/permissions-reference).

Explore scopes in [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer) to call an API and examine required permissions. They're displayed in order from lowest to highest privilege. Picking the lowest possible privilege ensures that your application is less vulnerable to attacks.

Follow the guidance in [Enhance security with the principle of least privilege](/azure/active-directory/develop/secure-least-privileged-access) to reduce your applications' attack surfaces and security breach blast radius should compromise occur.

## Securely manage tokens

When your application requests tokens from Azure AD, securely manage them:

- Validate that they're properly scoped to your application.
- Appropriately cache them.
- Use them as intended.
- Handle token issues by checking for error classes and coding appropriate responses.
- Instead of directly reading access tokens, view their scopes and details in token responses.

## Support Continuous Access Evaluation (CAE)

[CAE](/azure/active-directory/develop/app-resilience-continuous-access-evaluation) allows Microsoft Graph to quickly deny access in response to security events. Examples include these tenant administrator activities:

- Deleting or disabling a user account.
- Enabling Multi-Factor Authentication (MFA) for a user.
- Explicitly revoking a user's issued tokens.
- Detecting a user moving to high-risk status.

When you support CAE, tokens that Azure AD issues to call Microsoft Graph are valid for 24 hours instead of the standard 60 to 90 minutes. CAE adds resiliency to your app by requiring hourly token refresh and enabling MSAL to proactively refresh the token well before the token expires.

## Define app roles for IT to assign to users and groups

[App roles](/azure/active-directory/develop/howto-add-app-roles-in-azure-ad-apps) help you to implement role-based access control in your applications. Common examples of app roles include Administrator, Reader, and Contributor. Role-based access control allows your application to restrict sensitive actions to [users or groups based on their defined roles](configure-tokens-group-claims-app-roles.md).

## Become a verified publisher

As a [verified publisher](/azure/active-directory/develop/publisher-verification-overview), you've verified your identity with your Microsoft Partner Network account and completed the established verification process. For developers of multi-tenant apps, being a verified publisher helps build trust with IT administrators in customer tenants.

## Next steps

- [Customizing tokens](zero-trust-token-customization.md) describes the information that you can receive in Azure AD tokens. Learn how to customize tokens to improve flexibility and control while increasing application Zero Trust security with least privilege.
- [Configuring group claims and app roles in tokens](configure-tokens-group-claims-app-roles.md) describes how to configure your apps with app role definitions and assign security groups to app roles. This approach improves flexibility and control while increasing application Zero Trust security with least privilege.
- [Building apps with a Zero Trust approach to identity](identity.md) provides an overview of permissions and access best practices.
- The [Identity integrations](../integrate/identity.md) guide explains how to integrate security solutions with Microsoft products to create Zero Trust solutions.
- [Developer and administrator responsibilities for application registration, authorization, and access](identity-developer-administrator-responsibilities.md) helps you to better collaborate with your IT Pros.
- [Supported identity and account types for single- and multi-tenant apps](identity-supported-account-types.md) explains how you can choose if your app allows only users from your Azure AD) tenant, any Azure AD tenant, or users with personal Microsoft accounts.
- [Authorization best practices](developer-strategy-authorization-best-practices.md) helps you to implement the best authorization, permission, and consent models for your applications.
- [API Protection](protect-api.md) describes best practices for protecting your API through registration, defining permissions and consent, and enforcing access to achieve your Zero Trust goals.
