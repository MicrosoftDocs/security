---
title: Registering applications
description: This article introduces to developers the application registration process and its requirements. It helps you to ensure that apps satisfy Zero Trust principles of use least privileged access and assume breach.
author: janicericketts
ms.author: jricketts
ms.service: identity
ms.topic: conceptual
ms.date: 02/28/2023
ms.custom: template-concept
ms.collection:
  - zerotrust-dev
# Customer intent: As a developer, I want to learn about the application registration process and its requirements so that I can ensure that my apps satisfy Zero Trust principles of use least privileged access and assume breach.
---
# Registering applications

The [Microsoft identity platform](/azure/active-directory/develop/) [app registration portal](/azure/active-directory/develop/quickstart-register-app) is the primary entry point for applications that use the platform for authentication and associated needs. As a developer, when registering and configuring your apps, the choices you make drive and affect how well your application satisfies [Zero Trust principles](../zero-trust-overview.md). Effective app registration especially considers the principles of *use least privileged access* and *assume breach*. This article helps you to learn about the application registration process and its requirements to ensure that your apps follow a Zero Trust approach to security.

[Application management in Microsoft Entra ID](/azure/active-directory/manage-apps/what-is-application-management) (Microsoft Entra ID) is the process of securely creating, configuring, managing, and monitoring applications in the cloud. When you register your application in a Microsoft Entra tenant, you configure secure user access.

Microsoft Entra ID represents applications by [application objects](/azure/active-directory/develop/app-objects-and-service-principals#application-object) and [service principals](/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object). With some [exceptions](/azure/active-directory/develop/active-directory-how-applications-are-added#notes-and-exceptions), applications are application objects. Think of a service principal as an instance of an application that references an application object. Multiple service principals across directories can reference a single application object.

You can configure your application to use Microsoft Entra ID through three methods: [in Visual Studio](/visualstudio/azure/vs-active-directory-add-connected-service), by using the Microsoft Graph API, or by using PowerShell. There are developer experiences in Azure and in [API Explorer](/iis-administration/api-explorer/) across developer centers. Reference the required decisions and tasks for the [developer and IT Pro roles](identity-developer-administrator-responsibilities.md) to build and deploy secure applications in the Microsoft identity platform.

## Who can add and register applications

Admins and, if permitted by the tenant, users and developers may create application objects by registering applications in the Azure portal. By default, all users in a directory can [register application objects](/azure/active-directory/develop/active-directory-how-applications-are-added#who-has-permission-to-add-applications-to-my-azure-ad-instance) that they develop. Application object developers decide which applications share and give access to organizational data through [consent](/azure/active-directory/develop/v2-admin-consent).

When the first user in a directory signs in to an application and grants consent, the system creates a service principal in the tenant that stores all user consent information. Microsoft Entra ID automatically creates a service principal for a newly registered app in the tenant before a [user authenticates](user-authentication.md).

Only Microsoft Entra global administrators can perform specific application tasks (such as adding applications from the app gallery and configuring applications to use application proxy).

## Registering application objects

As a developer, you register your apps that use the Microsoft identity platform. Register your apps in the Azure portal or by calling [Microsoft Graph application APIs](/graph/api/resources/application). After you register your app, it communicates with the Microsoft identity platform by sending requests to the endpoint.

You might not have permission to create or modify an application registration. When administrators don't give you permissions to register your applications, ask them how you can convey necessary app registration information to them.

[Application registration properties](/azure/active-directory/develop/active-directory-how-applications-are-added#what-are-application-objects-and-where-do-they-come-from) may include the following components.

- Name, logo, and publisher
- Redirect URIs
- Secrets (symmetric and/or asymmetric keys used to authenticate the application)
- API dependencies (OAuth)
- Published APIs/resources/scopes (OAuth)
- App roles for role-based access control
- Metadata and configuration for single sign-on (SSO), user provisioning, and proxy

A required part of app registration is your selection of [supported account types](identity-supported-account-types.md) to define who can use your app based on the user's account type. Microsoft Entra administrators follow the [application model](/azure/active-directory/develop/application-model) to manage application objects in the Azure portal through the [App registrations](https://aka.ms/appregistrations) experience and define application settings that tell the service how to issue tokens to the application.

During registration, you receive the identity of your application: the **application (client) ID**. Your app uses its **client ID** every time it performs a transaction through the Microsoft identity platform.

## App registration best practices

Follow [security best practices for application properties](/azure/active-directory/develop/security-best-practices-for-app-registration) when registering your application in Microsoft Entra ID as a critical part of its business use. Aim to prevent downtime or compromise that may affect the entire organization. The following recommendations help you to develop your secure application around Zero Trust principles.

- **Use the [Microsoft identity platform integration checklist](/azure/active-directory/develop/identity-platform-integration-checklist)** to ensure high quality and secure integration. Maintain the quality and security of your app.
- **Properly define your redirect URLs**. Reference the [Redirect URI (reply URL) restrictions and limitations](/azure/active-directory/develop/reply-url) to avoid compatibility and security issues.
- **Check redirect URIs in your app registration for ownership to avoid domain takeovers**. Redirect URLs should be on domains that you know and own. Regularly review and remove unnecessary and unused URIs. Don't use non-https URIs in production apps.
- **Always define and maintain app and service principal owners for your registered apps in your tenant**. Avoid orphaned apps (apps and [service principals](/azure/active-directory/develop/app-objects-and-service-principals) that have no assigned owners). Ensure that IT admins can easily and quickly identify app owners during an emergency. Keep the number of app owners small. Make it difficult for a compromised user account to affect multiple applications.
- **Avoid using the same app registration** **for multiple apps**. Separating app registrations helps you to enable least privileged access and reduce impact during a breach.
  - Use separate app registrations for apps that sign in users and apps that expose data and operations via API (unless tightly coupled). This approach allows permissions for a higher privileged API, such as Microsoft Graph and credentials (like secrets and certificates), at a distance from apps that sign in and interact with users.
  - Use separate app registrations for web apps and APIs. This approach helps ensure that, if the web API has a higher set of permissions, then the client app doesn't inherit them.
- **Define your application as a multi-tenant app only when necessary**. [Multi-tenant apps](/azure/active-directory/develop/howto-convert-app-to-be-multi-tenant) allow for provisioning in tenants other than yours. They require more management overhead to filter unwanted access. Unless you intend to develop your app as a multi-tenant app, start with a SignInAudience value of AzureADMyOrg.

## Next steps

- Reference the [Microsoft identity platform documentation](/azure/active-directory/develop/) to learn how to register application types. Example app types include single-page apps (SPA), web apps, web APIs, desktop apps, mobile apps, and background services, daemons, and scripts.
- The [New App registrations experience for Azure AD B2C](/azure/active-directory-b2c/app-registrations-training-guide) article helps you become familiar the new experience that replaces the legacy experience.
- [Integrating applications with Microsoft Entra ID and the Microsoft identity platform](integrate-apps-microsoft-identity-platform.md) helps developers to build and integrate apps that IT pros can secure in the enterprise by securely integrate apps with Microsoft Entra ID and the Microsoft identity platform.
- [Acquiring authorization to access resources](acquire-application-authorization-to-access-resources.md) helps you to understand how to best ensure Zero Trust when acquiring resource access permissions for your application.
- [Authorization best practices](developer-strategy-authorization-best-practices.md) helps you to implement the best authorization, permission, and consent models for your applications.
