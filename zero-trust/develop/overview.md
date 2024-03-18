---
title: Develop using Zero Trust principles
description: As a developer, learn how to implement the guiding principles of Zero Trust so that you can improve your application security.
ms.date: 12/13/2022
ms.service: identity
author: janicericketts
ms.author: jricketts
ms.topic: conceptual
ms.collection:
  - zerotrust-dev
# Customer intent: As a developer, I want to learn how to implement the guiding principles of Zero Trust so that I can improve your application security.
---
# Develop using Zero Trust principles

This article helps you, as a developer, to understand the guiding principles of Zero Trust so that you can improve your application security. You play a key role in organizational security; applications and their developers can no longer assume that the network perimeter is secure. Compromised applications can affect the entire organization.

Organizations are deploying new security models that adapt to complex modern environments and embrace the mobile workforce. New models are designed protect people, devices, applications, and data wherever they're located. Organizations are striving to achieve [Zero Trust](../zero-trust-overview.md), a security strategy and approach for designing and implementing applications that follow these guiding principles:

* Verify explicitly
* Use least privilege access
* Assume breach

Instead of believing everything behind the corporate firewall is safe, the Zero Trust model assumes breach and verifies each request as though it originated from an uncontrolled network. Regardless of where the request originates or what resource it accesses, the Zero Trust model requires us to "never trust, always verify."

Understand that Zero Trust isn't a replacement for security fundamentals. With work originating from anywhere on any device, design your applications to incorporate Zero Trust principles throughout your development cycle.

## Why develop with a Zero Trust perspective?

* We've seen a rise in the level of sophistication of cybersecurity attacks.
* The "work from anywhere" workforce has redefined the security perimeter. Data is being accessed outside the corporate network and shared with external collaborators such as partners and vendors.
* Corporate applications and data are moving from on-premises to hybrid and cloud environments. Traditional network controls can no longer be relied on for security. Controls need to move to where the data is: on devices and inside apps.

The development guidance in this section helps you to increase security, reduce the blast radius of a security incident, and swiftly recover by using Microsoft technology.

## Next steps

[Subscribe](/api/search/rss?search=%22Develop+using+Zero+Trust+principles%22&locale=en-us) to  our *Develop using Zero Trust principles* RSS feed for notification of new articles.

### Developer guidance overview

* [What do we mean by Zero Trust compliance?](identity-zero-trust-compliance.md) provides an overview of application security from a developer's perspective to address the guiding principles of Zero Trust.
* Use [Zero Trust identity and access management development best practices](identity-iam-development-best-practices.md) in your application development lifecycle to create secure applications.
* [Using standards-based development methodologies](identity-standards-based-development-methodologies.md) provides an overview of supported standards (OAuth 2.0, OpenID Connect, SAML, WS-Federation, and SCIM) and the benefits of using them with MSAL and the Microsoft identity platform.
* [Developer and administrator responsibilities for application registration, authorization, and access](identity-developer-administrator-responsibilities.md) helps you to better collaborate with your IT Pros.

### Permissions and access

* [Building apps that secure identity through permissions and consent](identity.md) provides an overview of permissions and access best practices.
* [Integrating applications with Microsoft Entra ID and the Microsoft identity platform](integrate-apps-microsoft-identity-platform.md) helps developers to build and integrate apps that IT pros can secure in the enterprise by securely integrate apps with Microsoft Entra ID and the Microsoft identity platform.
* [Registering applications](app-registration.md) introduces developers to the application registration process and its requirements. It helps them to ensure that apps satisfy Zero Trust principles of use least privileged access and assume breach.
* [Supported identity and account types for single- and multi-tenant apps](identity-supported-account-types.md) explains how you can choose if your app allows only users from your Microsoft Entra tenant, any Microsoft Entra tenant, or users with personal Microsoft accounts.
* [Authenticating users for Zero Trust](user-authentication.md) helps developers to learn best practices for authenticating application users in Zero Trust application development. It describes how to enhance application security with the Zero Trust principles of least privilege and verify explicitly.
* [Acquiring authorization to access resources](acquire-application-authorization-to-access-resources.md) helps you to understand how to best ensure Zero Trust when acquiring resource access permissions for your application.
* [Developing delegated permissions strategy](developer-strategy-delegated-permission.md) helps you to implement the best approach for managing permissions in your application and develop using Zero Trust principles.
* [Developing application permissions strategy](developer-strategy-application-permissions.md) helps you to decide upon your application permissions approach to credential management.
* [Requesting permissions that require administrative consent](permissions-require-admin-consent.md) describes the permission and consent experience when application permissions require administrative consent.
* [Reducing overprivileged permissions and apps](overprivileged-permissions.md) helps you to understand why applications shouldn't request more permissions than they need (overprivileged) and how to limit privilege to manage access and improve security.
* [Providing application identity credentials when there's no user](identity-non-user-applications.md) explains why the best Zero Trust client credentials practice for services (non-user applications) on Azure is Managed Identities for Azure resources.
* [Managing tokens for Zero Trust](token-management.md) helps developers to build security into applications with ID tokens, access tokens, and security tokens that your they can receive from the Microsoft identity platform.
* [Customizing tokens](zero-trust-token-customization.md) describes the information that you can receive in Microsoft Entra tokens and how you can customize tokens.
* [Securing applications with Continuous Access Evaluation](secure-with-cae.md) helps developers to improve application security with Continuous Access Evaluation. Learn how to [ensure Zero Trust support](overview.md) in your apps that receive authorization to access resources when they acquire access tokens from Microsoft Entra ID.
* [Configuring group claims and app roles in tokens](configure-tokens-group-claims-app-roles.md) shows you how to configure your apps with app role definitions and assign security groups.
* [API Protection](protect-api.md) describes best practices for protecting your API through registration, defining permissions and consent, and enforcing access to achieve your Zero Trust goals.
* [Example of API protected by Microsoft identity consent framework](protected-api-example.md) helps you to design least privilege application permissions strategies for the best user experience.
* [Calling an API from another API](api-calls-api.md) helps you to ensure Zero Trust when you have one API that needs to call another API. You'll learn how to securely develop your application when it's working on behalf of a user.
* [Authorization best practices](developer-strategy-authorization-best-practices.md) helps you to implement the best authorization, permission, and consent models for your applications.

## Zero Trust DevSecOps

* [Securing DevOps environments for Zero Trust](secure-devops-environments-zero-trust.md) describes best practices for securing your DevOps environments with a Zero Trust approach to prevent hackers from compromising developer boxes, infecting release pipelines with malicious scripts, and gaining access to production data via test environments.
* [Securing the DevOps platform environment](secure-devops-platform-environment-zero-trust.md) helps you to implement Zero Trust principles in your DevOps platform environment and highlights best practices for secret and certificate management.
* [Securing the developer environment](secure-dev-environment-zero-trust.md) helps you to implement Zero Trust principles in your development environments with best practices for least privilege, branch security, and trusting tools, extensions, and integrations.
* [Embedding Zero Trust security into your developer workflow](embed-zero-trust-dev-workflow.md) helps you to innovate quickly and securely.

## Additional Zero Trust documentation

Use additional Zero Trust content based on a documentation set or the roles in your organization.

### Documentation set

Follow this table for the best Zero Trust documentation sets for your needs.

| Documentation set | Helps you... | Roles |
| --- | --- | --- |
| [Adoption framework](../adopt/zero-trust-adoption-overview.md) for phase and step guidance for key business solutions and outcomes | Apply Zero Trust protections from the C-suite to the IT implementation. | Security architects, IT teams, and project managers |
| [Concepts and deployment objectives](../deploy/overview.md) for general deployment guidance for technology areas | Apply Zero Trust protections aligned with technology areas. | IT teams and security staff |
| [Zero Trust for small businesses](../guidance-smb-partner.md) | Apply Zero Trust principles to small business customers. | Customers and partners working with Microsoft 365 for business |
| [Zero Trust Rapid Modernization Plan (RaMP)](../zero-trust-ramp-overview.md) for project management guidance and checklists for easy wins | Quickly implement key layers of Zero Trust protection. | Security architects and IT implementers |
| [Zero Trust deployment plan with Microsoft 365](/microsoft-365/security/microsoft-365-zero-trust?bc=%2fsecurity%2fzero-trust%2fbreadcrumb%2ftoc.json&toc=%2fsecurity%2fzero-trust%2ftoc.json) for stepped and detailed design and deployment guidance | Apply Zero Trust protections to your Microsoft 365 tenant. | IT teams and security staff |
| [Zero Trust for Copilot for Microsoft 365](../copilots/zero-trust-microsoft-365-copilot.md) for stepped and detailed design and deployment guidance | Apply Zero Trust protections to Copilot for Microsoft 365. | IT teams and security staff |
| [Zero Trust for Azure services](../azure-infrastructure-overview.md) for stepped and detailed design and deployment guidance | Apply Zero Trust protections to Azure workloads and services. | IT teams and security staff |
| [Partner integration with Zero Trust](../integrate/overview.md) for design guidance for technology areas and specializations | Apply Zero Trust protections to partner Microsoft cloud solutions. | Partner developers, IT teams, and security staff |

### Your role

Follow this table for the best documentation sets for your role in your organization.

| Role | Documentation set | Helps you... |
| --- | --- | --- |
| Security architect <br><br> IT project manager <br><br> IT implementer | [Adoption framework](../adopt/zero-trust-adoption-overview.md) for phase and step guidance for key business solutions and outcomes| Apply Zero Trust protections from the C-suite to the IT implementation. |
| Member of an IT or security team | [Concepts and deployment objectives](../deploy/overview.md) for general deployment guidance for technology areas | Apply Zero Trust protections aligned with technology areas. |
| Customer or partner for Microsoft 365 for business | [Zero Trust for small businesses](../guidance-smb-partner.md) | Apply Zero Trust principles to small business customers.  |
| Security architect <br><br> IT implementer | [Zero Trust Rapid Modernization Plan (RaMP)](../zero-trust-ramp-overview.md) for project management guidance and checklists for easy wins | Quickly implement key layers of Zero Trust protection. |
| Member of an IT or security team for Microsoft 365 | [Zero Trust deployment plan with Microsoft 365](/microsoft-365/security/microsoft-365-zero-trust?bc=%2fsecurity%2fzero-trust%2fbreadcrumb%2ftoc.json&toc=%2fsecurity%2fzero-trust%2ftoc.json) for stepped and detailed design and deployment guidance for Microsoft 365 | Apply Zero Trust protections to your Microsoft 365 tenant. |
| Member of an IT or security team for Microsoft Copilots | [Zero Trust for Copilot for Microsoft 365](../copilots/zero-trust-microsoft-365-copilot.md) for stepped and detailed design and deployment guidance | Apply Zero Trust protections to Copilot for Microsoft 365. |
| Member of an IT or security team for Azure services | [Zero Trust for Azure services](../azure-infrastructure-overview.md) for stepped and detailed design and deployment guidance | Apply Zero Trust protections to Azure workloads and services. |
| Partner developer or member of an IT or security team | [Partner integration with Zero Trust](../integrate/overview.md) for design guidance for technology areas and specializations | Apply Zero Trust protections to partner Microsoft cloud solutions. |
