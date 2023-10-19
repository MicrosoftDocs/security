---
title: Integrating applications with Microsoft Entra ID and the Microsoft identity platform
description: As a developer, you can build and integrate apps that IT pros can secure in the enterprise. This article will help you to understand how to securely integrate your app with Microsoft Entra ID and the Microsoft identity platform.
ms.date: 01/27/2023
ms.service: identity
author: janicericketts
ms.author: jricketts
ms.topic: conceptual
ms.custom: template-concept
ms.collection:
  - zerotrust-dev
# Customer intent: As a developer, I want to build and integrate apps that IT pros can secure in the enterprise. To do so, I need to understand how to use Zero Trust principles to securely integrate my app with Microsoft Entra ID and the Microsoft identity platform.
---
# Integrating applications with Microsoft Entra ID and the Microsoft identity platform

As a developer, you can build and integrate apps that IT pros can secure in the enterprise. This article will help you to understand how to [use Zero Trust principles](overview.md) to securely integrate your app with Microsoft Entra ID and the Microsoft identity platform.

The Microsoft cloud-based identity and access management service, Microsoft Entra ID, provides developers with these [application integration](/azure/active-directory/develop/active-directory-how-applications-are-added) benefits:

- Application authentication and authorization
- User authentication and authorization
- [Single sign-on (SSO)](/azure/active-directory/develop/single-sign-on-saml-protocol) using federation or password
- User provisioning and synchronization
- Role-based access control
- OAuth authorization services
- Application publishing and proxy
- Directory schema extension attributes

:::image type="complex" source="../media/develop/integrate-apps-microsoft-identity-platform/diagram-microsoft-identity-platform-for-developers-inline.png" alt-text="Diagram illustrates the unified toolkit of the Microsoft identity platform for developers that supports several identities and industry standards." lightbox="../media/develop/integrate-apps-microsoft-identity-platform/diagram-microsoft-identity-platform-for-developers-expanded.png":::
   Diagram title: Microsoft identity platform for developers. Diagram subtitle: Build applications and integrate identity with one unified toolkit. Listed technologies and examples include endpoints such as OpenID Connect, libraries such as Microsoft Authentication Libraries - MSAL, web APIs such as Microsoft Graph, publisher verification with Microsoft Partner Network, user provisioning with System for Cross-domain Identity Management - SCIM, and auth brokers available via MSAL. Supported identities include Microsoft Entra ID, MSA, and Microsoft Entra External ID including Azure AD B2C. Supported industry standards include OAuth 2.0, OpenID Connect, SAML, SCIM.
:::image-end:::

The above diagram illustrates the unified toolkit of the Microsoft identity platform for developers that supports several identities and industry standards. You can build applications and integrate identity with endpoints, libraries, web APIs, publisher verification, user provisioning, and auth brokers.

## Get started with app integration

The [Microsoft identity platform documentation](/azure/active-directory/develop/) site is the best starting point for you to learn how to integrate your applications with the Microsoft identity platform. You can find developer workshops, workshop materials, links to workshop recordings, and information about upcoming live events at [https://aka.ms/UpcomingIDLOBDev](https://aka.ms/UpcomingIDLOBDev).

While designing your app, you'll need to:

- Identify resources that your app needs to access.
- Consider whether your app will have interactive users and workload components.
- Access resources that Microsoft Entra ID secures by [building apps that secure identity through permissions and access](identity.md).

## App types that you can integrate

The Microsoft identity platform performs [identity and access management](identity-iam-development-best-practices.md) (IAM) only for registered and [supported applications](identity-supported-account-types.md). To integrate with the Microsoft identity platform, your app must be able to provide a web browser-based component that can connect to the Microsoft identity platform's authorization endpoints under the `https://login.microsoftonline.com` address. Your app will call the token endpoint under the same address.

An integrated app can run from any location, including these examples:

- Microsoft Azure
- Other cloud providers
- Your own data centers and servers
- Desktop computers
- Mobile devices
- Internet of Things devices.

 The app or device, such as a web browser app accessing the authorization endpoint, can natively provide requirements. Cooperation between a disconnected browser and the application will satisfy the requirements. For example, apps running on televisions may have the user perform the initial authentication with a browser on a desktop or mobile device.

You'll register your client application (web or native app) or web API to establish a trust relationship between your application and the Microsoft identity platform. Microsoft Entra application registration is critical because misconfiguration or lapse in hygiene of your application can result in downtime or compromise. Follow the [Security best practices for application properties in Microsoft Entra ID](/azure/active-directory/develop/security-best-practices-for-app-registration).

<a name='publish-to-azure-ad-application-gallery'></a>

## Publish to Microsoft Entra application gallery

The [Microsoft Entra application gallery](/azure/active-directory/manage-apps/overview-application-gallery) is a collection of software as a service (SaaS) [application and service principal objects in Microsoft Entra ID](/azure/active-directory/develop/app-objects-and-service-principals) that developers have pre-integrated with Microsoft Entra ID. It contains thousands of applications that make it easy to deploy and configure SSO and automatic user provisioning.

[Automatic user provisioning](/azure/active-directory/app-provisioning/user-provisioning#what-applications-and-systems-can-i-use-with-azure-ad-automatic-user-provisioning) refers to creating user identities and roles in cloud applications that users need to access. Automatic provisioning includes maintaining and removing user identities as status or roles change. To provision users to SaaS apps and other systems, the Microsoft Entra provisioning service connects to a System for Cross-domain Identity Management (SCIM) 2.0 user management API endpoint that the application vendor provides. This SCIM endpoint allows Microsoft Entra ID to programmatically create, update, and remove users.

When you develop apps for Microsoft Entra ID, you can use the SCIM 2.0 user management API to build a SCIM endpoint that integrates Microsoft Entra ID for provisioning. For details, reference the [Develop and plan provisioning for a SCIM endpoint in Microsoft Entra ID](/azure/active-directory/app-provisioning/use-scim-to-provision-users-and-groups) tutorial.

[Publish your application](/azure/active-directory/manage-apps/v2-howto-app-gallery-listing) to the Microsoft Entra application gallery and make them publicly available for users to add to their tenants by completing these tasks:

- Complete the prerequisites.
- Create and publish documentation.
- Submit your application.
- Join the Microsoft partner network.

## Become a verified publisher

[Publisher verification](/azure/active-directory/develop/publisher-verification-overview) provides information to app users and organization admins about authenticity of developers who publish apps that integrate with the Microsoft identity platform. When you're a verified publisher, users can more easily decide if they want to allow your application to sign them in and access their profile information. They can base their decision on the information and access that your app requests in tokens.

App publishers verify their identity with Microsoft by associating their app registration with their verified [Microsoft Partner Network (MPN)](https://partner.microsoft.com/membership) account. During verification, Microsoft requests verification documentation. After you become a verified publisher, a blue verified badge displays in your app's Microsoft Entra consent prompts and web pages.

## Next steps

- [Building apps with a Zero Trust approach to identity](identity.md) provides an overview of permissions and access best practices.
- [Authorization best practices](developer-strategy-authorization-best-practices.md) helps you to implement the best authorization, permission, and consent models for your applications.
- [Configure an app\'s publisher domain](/azure/active-directory/develop/howto-configure-publisher-domain) helps you to understand multitenant apps and default publisher domain values.
- [SaaS App Integration Tutorials for use with Microsoft Entra ID](/azure/active-directory/saas-apps/tutorial-list) helps you to integrate your cloud-enabled SaaS applications with Microsoft Entra ID.
- Reference tips to [troubleshoot publisher verification](/azure/active-directory/develop/troubleshoot-publisher-verification) if you\'re receiving errors or seeing unexpected behavior during publication.
