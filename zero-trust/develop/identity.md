---
title: Building apps with a Zero Trust approach to identity
description: Learn how to build trustworthy, Zero Trust-ready applications with secure authentication and authorization using the Microsoft identity platform.
ms.date: 10/14/2021
ms.service: security
author: knicholasa
ms.author: nichola
ms.topic: conceptual

# Customer intent: As a developer, I want to learn how to build Zero Trust-compliant apps using Microsoft identity platform features, so I can ensure that my applications are trustworthy and more secure.
---

# Building apps with a Zero Trust approach to identity

:::image type="icon" source="../media/icon-identity-medium.png":::

Zero Trust is a security framework that does not rely on the implicit trust afforded to interactions behind a secure network perimeter. Instead, it uses the principles of explicit verification, least privileged access, and assuming breach to keep users and data secure while allowing for common scenarios like access to applications from outside the network perimeter.

App developers can improve app security, minimize the impact of breaches, and ensure that their applications meet their customers' security requirements by adopting Zero Trust principles. This document is about how developers can use a Zero Trust approach to identity, which includes authentication, authorization, and identity management.

## Industry security trends impact application requirements

The implementation of Zero Trust is still evolving, and each organization's journey is unique. But a logical place to start for most customers is identity. The following are some of the polices and controls we see organizations prioritizing as they roll out Zero Trust:

- **Organizations are restricting user consent to low-risk permissions for publisher verified apps**. IT admins are embracing the principle of verify explicitly by requiring  [publisher verification](/azure/active-directory/develop/publisher-verification-overview), and the principle of least privilege by only allowing user consent for low risk permissions. Before your organization or your customer grants consent, admins will evaluate permissions your app is requesting and the trustworthiness of your app.
- **Organizations are setting up credential hygiene and rotation policies for apps and services**. If an app's credential gets compromised, the attacker can then acquire tokens under the guise of that app's identity, allowing it to get access to sensitive data, move laterally, or establish persistence.
- **Organizations are rolling out strong auth**. IT administrators expect to be able to set polices requiring multi-factor authentication and passwordless FIDO2 devices.
- **Organizations are blocking legacy protocols and APIs**. This includes blocking older authentication protocols such as "*Basic authentication*" and requiring modern protocols like **OpenID Connect** and **OAuth 2.0**. Microsoft [announced an end of life of June 30, 2022](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/update-your-applications-to-use-microsoft-authentication-library/ba-p/1257363) for Azure Active Directory (Azure AD) Graph and the legacy Azure Active Directory Authentication Library (ADAL). Organizations are ensuring applications they depend on are prepared.

## Top recommendations for Zero Trust

The following best practices are key to keeping your apps secure. We have also published a [whitepaper](https://www.microsoft.com/security/content-library/Search?SearchDataFor=OJZgGWbHnB3Ll5hblDBugaEMQAchNfvkzk5X5AmPM4tK43NHpbF5%2Bky%2Fnuivl7plZz89b%2FuLMMZsMqKeYbhPPw%3D%3D&IsKeywordSearch=evXIpssXVY6lIm6X2K9ieA%3D%3D) that walks through these best practices in detail.

**Use a trusted, standards-based authentication library.** Using a library will save you the time of developing a solution on your own. But more importantly, it will stay up to date and be responsive to the latest technologies and threats. Microsoft provides several authentication libraries, including the [Microsoft Authentication Library (MSAL)](/azure/active-directory/develop/msal-overview), [Microsoft Identity Web authentication library](/azure/active-directory/develop/microsoft-identity-web), and the [Azure SDKs for managed identities](/azure/active-directory/managed-identities-azure-resources/qs-configure-sdk-windows-vm#azure-sdks-with-managed-identities-for-azure-resources-support). These give you access to features such as conditional access, device registration and management, and the latest innovations such as passwordless and FIDO2 authentication without needing to write any extra code.

**Follow the** [Azure AD application registration security best practices](/azure/active-directory/develop/security-best-practices-for-app-registration). An Azure AD application registration is a critical part of your business application. Any misconfiguration or lapse in hygiene of your application can result in downtime or compromise.

**Keep credentials out of your code.** This enables credential rotation by IT administrators without bringing down or redeploying an app. You can use a service such as [Azure Key Vault](/azure/key-vault/general/authentication-fundamentals) or [Azure Managed Identities](/azure/active-directory/managed-identities-azure-resources/overview).

**Design for least privileged access.** This is a key tenet of Zero Trust. You should always provide the least privilege required for the user to do their job. For example, you can use [incremental consent](/azure/active-directory/azuread-dev/azure-ad-endpoint-comparison#incremental-and-dynamic-consent) to only request permissions when they are necessary. Another example is using [granular scopes in Microsoft Graph](/graph/permissions-reference). You can explore scopes using the [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer) to call an API and examine which permissions are required. They are displayed in order from lowest to highest privilege. Picking the lowest possible privilege will make your application less vulnerable to attacks. To learn more, check out [best practices for least privileged access for applications](/azure/active-directory/develop/secure-least-privileged-access).

**Support** [**Continuous Access Evaluation (CAE)**](/azure/active-directory/develop/app-resilience-continuous-access-evaluation). CAE allows Microsoft Graph to quickly revoke an active session in response to a security event. For example: when a user account is deleted or disabled, Multi-Factor Authentication (MFA) is enabled for a user, an administrator explicitly revokes issued tokens for a user, or a user is detected to be posing a risk. In addition, when CAE is enabled, tokens issued for Microsoft Graph are valid for 24 hours instead of the standard one hour. This is great for resiliency, as your app can continue to operate without going back to Azure Active Directory for a fresh token every hour.

**Define app roles for IT to assign to users and groups.** [App roles](/azure/active-directory/develop/howto-add-app-roles-in-azure-ad-apps) help you implement role-based access control (RBAC) in your applications. Common examples of app roles are roles like &quot;Administrator&quot;, &quot;Readers&quot;, and &quot;Contributors&quot;, which allow your application to restrict sensitive actions to users or groups assigned to a role. Using app roles also enables other features such as Azure AD's [Privileged Identity Management (PIM)](/azure/active-directory/privileged-identity-management/pim-configure) feature, which provide users just-in-time and time-bound access to sensitive roles, reducing the chance of a malicious actor getting that access, or an unauthorized user inadvertently impacting a sensitive resource.

**Become a** [**verified publisher**](/azure/active-directory/develop/publisher-verification-overview). When an application is marked as publisher verified, it means that the publisher has verified their identity using a Microsoft Partner Network account that has completed an established verification process. This is great for developers of multi-tenant apps, as it helps build trust with IT administrators in customer tenants.

**Use** [**managed identities**](/azure/active-directory/managed-identities-azure-resources/overview) when accessing resources in Azure. Managed identities are one key element used to reduce shared secrets in the code and should be used instead of service principals. While using managed identities, remember to follow the least privilege principal when giving permissions to resources.

## Next steps

- [Build Zero Trust-ready apps using Microsoft identity platform features and tools](/azure/active-directory/develop/zero-trust-for-developers) maps features of the Microsoft identity platform to the principles of Zero Trust.
- The [Adopting Zero Trust into your apps](https://www.microsoft.com/en-us/security/content-library/SkillingPath/Details/6541ecb8-fb85-44a5-bdd4-397bf2bb52f9) skilling path includes two useful  whitepapers:
  - [Zero Trust for the Microsoft identity platform developer](https://azure.microsoft.com/resources/zero-trust-for-the-microsoft-identity-platform-developer/), which explains in detail how to approach Zero Trust identity using the Microsoft identity platform.
  - [Adopting a Zero Trust approach to Identity in line-of-business apps](https://azure.microsoft.com/resources/zero-trust-identity-line-of-business-apps/) provides guidance that is tailored to apps that are built by or for a company for use within that same company. 
- The [Identity integrations](../integrate/identity.md) guide explains how independent software vendors and technology partners can integrate their security solutions with Microsoft products to create Zero Trust solutions for customers.
