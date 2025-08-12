---
title: Zero Trust for Identity integration overview
description: Independent software vendors and technology partners can integrate their solutions with Microsoft Entra ID to help customers adopt a Zero Trust model and keep their organizations secure.
ms.date: 03/11/2025
ms.service: security
author: janicericketts
ms.author: jricketts
ms.subservice: zero-trust
ms.topic: conceptual
ms.collection:
  - zerotrust-partner
ms.custom: sfi-image-nochange
---

# Identity integrations

:::image type="icon" source="../media/icon-identity-medium.png":::

Identity is the key control plane for managing access in the modern workplace and is essential to implementing Zero Trust. Identity solutions support:

- Zero Trust through strong authentication and access policies.
- Least privileged access with granular permission and access.
- Controls and policies that manage access to secure resources and minimize the blast radius of attacks.

This integration guide explains how independent software vendors (ISVs) and technology partners can integrate with Microsoft Entra ID to create secure Zero Trust solutions for customers.

## Zero Trust for Identity integration guide

This integration guide covers Microsoft Entra ID and Microsoft External ID.

Microsoft Entra ID is Microsoft's cloud-based identity and access management service. It provides the following features:
- Single sign-on authentication
- Conditional Access
- Passwordless and multifactor authentication
- Automated user provisioning
- And many more features that enable enterprises to protect and automate identity processes at scale

Microsoft Entra External ID is a business-to-customer identity access management (CIAM) solution. Customers use Microsoft Entra External ID to implement secure white-label authentication solutions that scale easily and blend in with branded web and mobile application experiences. Learn about integration guidance in the [Microsoft Entra External ID](#microsoft-entra-external-id) section.

## Microsoft Entra ID

There are many ways to integrate your solution with Microsoft Entra ID. Foundational integrations are about protecting your customers using Microsoft Entra ID's built-in security capabilities. Advanced integrations take your solution one step further with enhanced security capabilities.

:::image source="../media/integrate/identity/azure-active-directory-zero-trust-levels.png" alt-text="A curved path showing the foundational and advanced integrations. Foundational integrations include single sign-on and publisher verification. Advanced integrations include conditional access authentication context, continuous access evaluation, and advanced security API integrations." lightbox="../media/integrate/identity/azure-active-directory-zero-trust-levels.png":::

### Foundational integrations

Foundational integrations protect your customers with Microsoft Entra ID's built-in security capabilities.

#### Enable single sign-on and publisher verification

To enable single sign-on, we recommend publishing your app in [the app gallery](https://www.microsoft.com/security/business/identity-access-management/integrated-apps-azure-ad). This approach increases customer trust, because they know that your application is validated as compatible with Microsoft Entra ID. You can become a [verified publisher](/azure/active-directory/develop/publisher-verification-overview) so that customers are certain you're the publisher of the app they're adding to their tenant.

Publishing in the app gallery makes it easy for IT admins to integrate the solution into their tenant with automated app registration. Manual registrations are a common cause of support issues with applications. Adding your app to the gallery avoids these issues with your app.

For mobile apps, we recommend you use the Microsoft Authentication Library and a system browser to [implement single sign-on](/azure/active-directory/develop/mobile-sso-support-overview).

#### Integrate user provisioning

Managing identities and access for organizations with thousands of users is challenging. If large organizations use your solution, consider synchronizing information about users and access between your application and Microsoft Entra ID. This helps keep user access consistent when changes occur.

SCIM (System for Cross-Domain Identity Management) is an open standard for exchanging user identity information. You can use the SCIM user management API to automatically provision users and groups between your application and Microsoft Entra ID.

[Develop a SCIM endpoint for user provisioning to apps from Microsoft Entra ID](/azure/active-directory/app-provisioning/use-scim-to-provision-users-and-groups) describes how to build a SCIM endpoint and integrate with the Microsoft Entra provisioning service.

### Advanced integrations

Advanced integrations increase the security of your application even further.

#### Conditional Access authentication context

[Conditional Access authentication context](/azure/active-directory/develop/developer-guide-conditional-access-authentication-context) allows apps to trigger policy enforcement when a user accesses sensitive data or actions, keeping users more productive and your sensitive resources secure.

#### Continuous access evaluation

[Continuous access evaluation (CAE)](/azure/active-directory/conditional-access/concept-continuous-access-evaluation) allows access tokens to be revoked based on critical events and policy evaluation rather than relying on token expiry based on lifetime. For some resource APIs, because risk and policy are evaluated in real time, this can increase token lifetime up to 28 hours, which make your application more resilient and performant.

#### Security APIs

In our experience, many independent software vendors find these APIs to be useful.

##### User and group APIs

If your application needs to make updates to the users and groups in the tenant, you can use the user and group APIs through Microsoft Graph to write back to the Microsoft Entra tenant. You can read more about using the API in the [Microsoft Graph REST API v1.0 reference](/graph/api/overview) and the reference documentation for the [user resource type](/graph/api/resources/user)

##### Conditional Access API

[Conditional access](/azure/active-directory/conditional-access/overview) is a key part of Zero Trust because it helps to ensure the right user has the right access to the right resources. Enabling Conditional Access allows Microsoft Entra ID to make access decision based on computed risk and preconfigured policies.

Independent software vendors can take advantage of conditional access by surfacing the option to apply conditional access policies when relevant. For example, if a user is especially risky, you can suggest the customer enable Conditional Access for that user through your UI, and programmatically enable it in Microsoft Entra ID.

:::image type="content" source="../media/integrate/identity/diagram-access-control.png" alt-text="Diagram showing a user using an application, which then calls Microsoft Entra ID to set conditions for a conditional access policy based on the user activity." border="true" lightbox="../media/integrate/identity/diagram-access-control-expanded.png":::

For more, check out the [configure conditional access policies using the Microsoft Graph API](https://github.com/Azure-Samples/azure-ad-conditional-access-apis/tree/main/01-configure/graphapi) sample on GitHub.

##### Confirm compromise and risky user APIs

Sometimes independent software vendors might become aware of compromise that is outside of the scope of Microsoft Entra ID. For any security event, especially those including account compromise, Microsoft, and the independent software vendor can collaborate by sharing information from both parties. The [*confirm compromise API*](/graph/api/riskyuser-confirmcompromised) allows you to set a targeted user’s risk level to high. This API lets Microsoft Entra ID respond appropriately, for example by requiring the user to reauthenticate or by restricting their access to sensitive data.

In the other direction, Microsoft Entra ID continually evaluates user risk based on various signals and machine learning. The Risky User API provides programmatic access to all at-risk users in the app’s Microsoft Entra tenant. Independent software vendors can make use of this API to ensure they're handling users appropriately to their current level of risk. [riskyUser resource type](/graph/api/resources/riskyuser).

:::image type="content" source="../media/integrate/identity/diagram-risky-user.png" alt-text="Diagram showing a user using an application, which then calls Microsoft Entra ID to retrieve the user's risk level." border="true" lightbox="../media/integrate/identity/diagram-risky-user-expanded.png":::

#### Unique product scenarios

The following guidance is for independent software vendors who offer specific kinds of solutions.

[Secure hybrid access integrations](/azure/active-directory/manage-apps/secure-hybrid-access-integrations)
Many business applications were created to work inside of a protected corporate network, and some of these applications make use of legacy authentication methods. As companies look to build a Zero Trust strategy and support hybrid and cloud-first work environments, they need solutions that connect apps to Microsoft Entra ID and provide modern authentication solutions for legacy applications. Use this guide to create solutions that provide modern cloud authentication for legacy on-premises applications.

[Become a Microsoft-compatible FIDO2 security key vendor](/azure/active-directory/authentication/concept-fido2-hardware-vendor)
FIDO2 security keys can replace weak credentials with strong hardware-backed public/private-key credentials which can't be reused, replayed, or shared across services. You can become a Microsoft-compatible FIDO2 security key vendor by following the process in this document.

## Microsoft Entra External ID

Microsoft Entra External ID combines powerful solutions for working with people outside of your organization. With External ID capabilities, you can allow external identities to securely access your apps and resources. Whether you’re working with external partners, consumers, or business customers, users can bring their own identities. These identities can range from corporate or government-issued accounts to social identity providers like Google or Facebook. Ror more information about securing your apps for external partners, consumers, or business customers, see [Introduction to Microsoft External ID](/entra/external-id/external-identities-overview).

### Integrate with RESTful endpoints

Independent software vendors can integrate their solutions via RESTful endpoints to enable multifactor authentication (MFA) and role-based access control (RBAC), enable identity verification and proofing, improve security with bot detection and fraud protection, and meet Payment Services Directive 2 (PSD2) Secure Customer Authentication (SCA) requirements.

We have [guidance on how to use our RESTful endpoints](/azure/active-directory-b2c/api-connectors-overview?pivots=b2c-user-flow) and detailed sample walkthroughs of partners who integrated with the RESTful APIs:

- [Identity verification and proofing](/azure/active-directory-b2c/partner-gallery#identity-verification-and-proofing), which enables customers to verify the identity of their end users
- [Role-based access control](/azure/active-directory-b2c/partner-gallery#role-based-access-control), which enables granular access control to end users
- [Secure hybrid access to on-premises application](/azure/active-directory-b2c/partner-gallery#role-based-access-control), which enables end users to access on-premises and legacy applications with modern authentication protocols
- [Fraud protection](/azure/active-directory-b2c/partner-gallery#fraud-protection), which enables customers to protect their applications and end users from fraudulent sign-in attempts and bot attacks

### Web application firewall

Web Application Firewall (WAF) provides centralized protection for web applications from common exploits and vulnerabilities. Microsoft Entra External ID enables independent software vendors to integrate their WAF service. All traffic to custom domains (for example, `login.contoso.com`) always pass through the WAF service to provide another layer of security.

To implement a WAF solution, configure Microsoft Entra External ID custom domains. [Overview of custom URL domains for Microsoft Entra External ID](/entra/external-id/customers/concept-custom-url-domain) describes how to configure Microsoft Entra External ID in custom URL domains in external tenants.

## Next steps

- [What is Microsoft Entra ID?](/azure/active-directory/fundamentals/active-directory-whatis)
- [Introduction to Microsoft Entra External ID](/entra/external-id/external-identities-overview)
- [Manage an external tenant with Azure REST API (Preview)](/entra/external-id/customers/azure-rest-api-operations-tenant-management)
