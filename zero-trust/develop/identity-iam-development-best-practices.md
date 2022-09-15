---
title: Zero Trust identity and access management development best practices
description: Learn best practices for your application development lifecycle so that you can create secure applications that are Zero Trust compliant, starting with identity and access management (IAM).
author: janicericketts
ms.author: jricketts
ms.service: identity
ms.topic: conceptual
ms.date: 09/15/2022
ms.custom: template-concept
# Customer intent: As a developer, I want to learn best practices for my application development lifecycle so that I can create secure applications that are Zero Trust compliant, starting with identity and access management (IAM).
---
# Zero Trust identity and access management development best practices

This article will help you, as a developer, to understand best practices for your application development lifecycle so that you can create secure applications that are [Zero Trust compliant](identity-zero-trust-compliance.md), starting with identity and access management (IAM).

The [Zero Trust](overview.md) security framework uses the principles of explicit verification, least privileged access, and assuming breach to secure users and data while allowing for common scenarios like access to applications from outside the network perimeter. This approach aims to reduce reliance upon implicit trust afforded to interactions behind a secure network perimeter that can become vulnerable to security attacks.

## Industry security trends impact application requirements

While Zero Trust implementation continues to evolve, each organization's journey is unique and often begins with user and application identity. Here are policies and controls that many organizations prioritize as they roll out Zero Trust:

1. **Implement credential hygiene and rotation policies for apps and services.** When attackers compromise secrets such as certificates or passwords, they can achieve a depth of system access to acquire tokens under the guise of an app's identity and access sensitive data and move laterally and establish persistence.
1. **Roll out strong authentication.** IT administrators are configuring  policies that require multi-factor authentication and passwordless FIDO2 devices.
1. **Restrict user consent to apps with low-risk permissions to verified publisher apps.** Access to data in APIs like Microsoft Graph allow you to build rich applications and allow your organizations and customers to evaluate your app's permission requests and trustworthiness before granting consent. IT admins are embracing the principle of verify explicitly by requiring  publisher verification and the principle of least privilege by only allowing user consent for low risk permissions.
1. **Block legacy protocols and APIs.** This includes blocking older authentication protocols such as "Basic authentication" and requiring modern protocols like OpenID Connect and OAuth2.

## Use trusted, standards-based authentication libraries

Develop your application with known and accepted standards and libraries to increase application portability and security. Trusted, standards-based authentication libraries stay up-to-date so that your apps are responsive to the latest technologies and threats. The [Using standards-based development methodologies](identity-standards-based-development-methodologies.md) article provides an overview of supported standards (OAuth 2.0, OpenID Connect, SAML, WS-Federation, and SCIM) and the benefits of using them with [Microsoft Authentication Library (MSAL)](/azure/active-directory/develop/msal-overview) and the Microsoft identity platform.

Microsoft highly recommends that you develop your application using libraries such as MSAL, [Microsoft Identity Web authentication library](/azure/active-directory/develop/microsoft-identity-web), and [Azure SDKs for managed identities](/azure/active-directory/managed-identities-azure-resources/qs-configure-sdk-windows-vm#azure-sdks-with-managed-identities-for-azure-resources-support) rather than protocols that can have flaws and extensive documentation. Microsoft authentication libraries and SDKs allow you to use features such as conditional access, device registration and management, along with passwordless and FIDO2 authentication, without needing to write extra code.

MSAL and [Microsoft Graph](/graph/overview) are your best choices for developing Azure Active Directory (AD) applications. MSAL developers have done the work for you to ensure compliance with protocols. MSAL is optimized for efficiency when working directly with Azure AD.

## Register your apps in Azure AD

Follow the [Security best practices for application properties in Azure Active Directory](/azure/active-directory/develop/security-best-practices-for-app-registration). Azure AD application registration is critical because misconfiguration or lapse in hygiene of your application can result in downtime or compromise.

Application properties that can improve security include redirect URI, access tokens (used for implicit flows), certificates and secrets, application ID URI, and application ownership. Remember to conduct periodical security and health assessments similar to Security Threat Model assessments for code.

## Delegate identity and access management

Develop your application to use tokens for explicit identity verification and access control that can be defined and managed by your customers. Microsoft advises against developing your own username and password management systems.

Keeping credentials out of your code allows IT admins to rotate credentials without bringing down or redeploying your app. Use a service such as [Azure Key Vault](/azure/key-vault/general/authentication-fundamentals) or [Azure Managed Identities](/azure/active-directory/managed-identities-azure-resources/overview) to delegate IAM.

## Plan and design for least privilege access

A key principle of Zero Trust is least privilege access. Ensure that your application is sufficiently developed and documented so that your customers can successfully configure their least privilege policies. When supporting tokens and APIs, provide your customers with good documentation of resources that your application will call.

Always provide the least privilege required for your user to perform a specific task. For example, you can use [incremental consent](/azure/active-directory/azuread-dev/azure-ad-endpoint-comparison#incremental-and-dynamic-consent) to only request permissions when they're necessary and use [granular scopes in Microsoft Graph](/graph/permissions-reference).

Explore scopes in [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer) to call an API and examine required permissions. They're displayed in order from lowest to highest privilege. Picking the lowest possible privilege will ensure that your application is less vulnerable to attacks.

Follow the guidance in the [Enhance security with the principle of least privilege](/azure/active-directory/develop/secure-least-privileged-access) article to help reduce the attack surface of your applications and the impact of a security breach (blast radius) should compromise occur in applications that you integrate with the Microsoft identity platform.

## Securely manage tokens

When your application requests tokens from Azure AD, securely manage them by validating that they're properly scoped to your application, caching them appropriately, and using them as intended. Handle token issues by checking for error classes and coding appropriate responses. Instead of directly reading access tokens, view their scopes and details in token responses.

## Support Continuous Access Evaluation (CAE)

[CAE](/azure/active-directory/develop/app-resilience-continuous-access-evaluation) allows Microsoft Graph to quickly revoke an active session in response to security events. Examples include tenant administrator activities such as:

* Deleting or disabling a user account.
* Enabling Multi-Factor Authentication (MFA) for a user.
* Explicitly revoking issued tokens for a user.
* Detecting a user to be posing a risk.

When you support CAE, tokens that Microsoft Graph issues are valid for 24 hours instead of the standard one hour. This adds resiliency to your app in that it can function without hourly token refresh.

## Define app roles for IT to assign to users and groups

[App roles](/azure/active-directory/develop/howto-add-app-roles-in-azure-ad-apps) help you to implement role-based access control (RBAC) in your applications. Common examples of app roles include Administrator, Reader, and Contributor. RBAC allows your application to restrict sensitive actions to users or groups based on their defined roles.

App roles enable features such as Azure AD [Privileged Identity Management (PIM)](/azure/active-directory/privileged-identity-management/pim-configure) that provides users with just-in-time and time-bound access to sensitive roles. This reduces the likelihood of malicious actors gaining access or unauthorized users inadvertently impacting sensitive resources.

## Become a verified publisher

When you're a [verified publisher](/azure/active-directory/develop/publisher-verification-overview), you have verified your identity with your Microsoft Partner Network account and completed the established verification process. This is ideal for developers of multi-tenant apps as it helps build trust with IT administrators in customer tenants.

## Next steps

* [Building apps with a Zero Trust approach to identity](identity.md) continues from the above article to help you use a Zero Trust approach to identity in your software development lifecyle (SDLC).
* The [Identity integrations](../integrate/identity.md) guide explains how independent software vendors and technology partners can integrate their security solutions with Microsoft products to create Zero Trust solutions for customers.
* [Developer and administrator responsibilities for application registration, authorization, and access](identity-developer-administrator-responsibilities.md) helps you to understand what your IT Pros need from you, and what your need from them, so that you can streamline your zero-trust development workflow.
* [Supported identity and account types for single- and multi-tenant apps](identity-supported-account-types.md) explains how you can choose if your app allows only users from your Azure Active Directory (Azure AD) tenant, any Azure AD tenant, or users with personal Microsoft accounts by configuring your app to be either single tenant or multitenant during app registration in Azure and ensure the Zero Trust principle of least privilege access so that your app only requests permissions it needs.
* When you're building non-user applications, you don't have a user whom you can prompt for a username and password or Multifactor Authentication (MFA). You need to provide the application's identity on its own. [Providing application identity credentials when there's no user](identity-non-user-applications.md) explains why the best Zero Trust client credentials practice for services (non-user applications) on Azure is Managed Identities for Azure resources.
