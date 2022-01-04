---
title: Identity Zero Trust integration overview
description: Independent software vendors and technology partners can integrate their solutions with Azure Active Directory to help customers adopt a Zero Trust model and keep their organizations secure.
ms.date: 09/17/2021
ms.service: security
author: knicholasa
ms.author: nichola
ms.topic: conceptual
---

# Identity integrations

:::image type="icon" source="../media/icon-identity-medium.png":::

Identity is the key control plane for managing access in the modern workplace and is essential to implementing Zero Trust. Identity solutions support Zero Trust through strong authentication and access policies, least privileged access with granular permission and access, and controls and policies that manage access to secure resources and minimize the blast radius of attacks.

This integration guide explains how independent software vendors (ISVs) and technology partners can integrate with Azure Active Directory to create secure Zero Trust solutions for customers.

## Identity Zero Trust integration guide

This integration guide covers Azure Active Directory as well as Azure Active Directory B2C.

Azure Active Directory is Microsoft's cloud-based identity and access management service. It provides single sign-on authentication, conditional access, passwordless and multi-factor authentication, automated user provisioning and many more features that enable enterprises to protect and automate identity processes at scale.

Azure Active Directory B2C is a business-to-customer identity access management (CIAM) solution which customers use to implement secure white-label authentication solutions that scale easily and blend in with branded web and mobile application experiences. The integration guidance is available in the [Azure Active Directory B2C](#azure-active-directory-b2c) section.

## Azure Active Directory

There are many ways to integrate your solution with Azure Active Directory. Foundational integrations are about protecting your customers using Azure Active Directory's built-in security capabilities. Advanced integrations will take your solution even one step further.

:::image type="icon" source="../media/integrate/identity/azure-active-directory-zero-trust-levels.png":::

### Foundational integrations

Foundational integrations protect your customers with Azure Active Directory's built-in security capabilities.

#### List your app in the Azure Active Directory App Gallery

To enable single sign-on, we recommend publishing your app in [the app gallery](https://www.microsoft.com/security/business/identity-access-management/integrated-apps-azure-ad). This will increase customer trust, because they know that your application has been validated as compatible with Azure Active Directory, and you can become a [verified publisher](/azure/active-directory/develop/publisher-verification-overview) so that customers are certain you are the publisher of the app they are adding to their tenant.

Add details about mobile SSO

Publishing in the app gallery will make it easy for IT admins to integrate the solution into their tenant with automated app registration. Manual registrations are a common cause of support issues with applications. Adding your app to the gallery will avoid these issues with your app.

#### Integrate user provisioning

Managing identities and access for organizations with thousands of users is challenging. If your solution will be used by large organizations, synchronizing information about users and access between your application and Azure Active Directory is essential. This allows you to effectively scale your identity management systems on both cloud-only and hybrid environments as customers increase their dependence on the cloud.

SCIM (System for Cross-Domain Identity Management) is an open standard for exchanging user identity information. You can use the SCIM user management API to automatically provision users and groups between your application and Azure Active Directory.

Our tutorial on the subject, [develop a SCIM endpoint for user provisioning to apps from Azure Active Directory](/azure/active-directory/app-provisioning/use-scim-to-provision-users-and-groups), describes how to build a SCIM endpoint and integrate with the Azure Active Directory provisioning service. The SCIM specification provides a common user schema for provisioning. When used in conjunction with federation standards like SAML or OpenID Connect, SCIM gives administrators an end-to-end, standards-based solution for access management.

### Advanced integrations

Advanced integrations will increase the security of your application even further.

#### Conditional Access authentication context

[Conditional Access authentication context](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/conditional-access-authentication-context-now-in-public-preview/ba-p/1942484) allows apps to trigger policy enforcement when a user accesses sensitive data or actions, keeping users more productive and your sensitive resources secure.

#### Continuous access evaluation

[Continuous access evaluation (CAE)](/azure/active-directory/conditional-access/concept-continuous-access-evaluation) allows access tokens to be revoked based on critical events and policy evaluation rather than relying on token expiry based on lifetime. For some resource APIs, because risk and policy are evaluated in real time, this can increase token lifetime up to 28 hours, which will make your application more resilient and performant.

#### Security APIs

In our experience, many independent software vendors have found these APIs to be particularly useful.

##### User and group APIs

If your application needs to make updates to the users and groups in the tenant, you can use the user and group APIs through Microsoft Graph to write back to the Azure Active Directory tenant. You can read more about using the API in the [Microsoft Graph REST API v1.0 reference](/graph/api/overview) and the reference documentation for the [user resource type](/graph/api/resources/user)

##### Conditional Access API

[Conditional access](/azure/active-directory/conditional-access/overview) is a key part of Zero Trust because it helps to ensure the right user has the right access to the right resources. Enabling Conditional Access allows Azure Active Directory to make access decision based on computed risk and pre-configured policies.

Independent software vendors can take advantage of conditional access by surfacing the option to apply conditional access policies when relevant. For example, if a user is especially risky, you can suggest the customer enable Conditional Access for that user through your UI, and programmatically enable it in Azure Active Directory.

:::image type="content" source="../media/integrate/identity/diagram-access-control.png" alt-text="Diagram showing a user using an application, which then calls Azure Active Directory to set conditions for a conditional access policy based on the user activity." border="true" lightbox="../media/integrate/identity/diagram-access-control-expanded.png":::

For more, check out the [configure conditional access policies using the Microsoft Graph API](https://github.com/Azure-Samples/azure-ad-conditional-access-apis/tree/main/01-configure/graphapi) sample on GitHub.

##### Confirm compromise and risky user APIs

Sometimes independent software vendors may become aware of compromise that is outside of the scope of Azure Active Directory. For any security event, especially those including account compromise, Microsoft and the independent software vendor can collaborate by sharing information from both parties. The [confirm compromise API](/graph/api/riskyusers-confirmcompromised) allows you to set a targeted user’s risk level to high. This lets Azure Active Directory respond appropriately, for example by requiring the user to reauthenticate or by restricting their access to sensitive data.

:::image type="content" source="../media/integrate/identity/diagram-confirm-compromise.png" alt-text="Diagram showing a user using an application, which then calls Azure Active Directory to set user risk level to high." border="true" lightbox="../media/integrate/identity/diagram-confirm-compromise-expanded.png":::

Going in the other direction, Azure Active Directory continually evaluates user risk based on various signals and machine learning. The Risky User API provides programmatic access to all at-risk users in the app’s Azure Active Directory tenant. Independent software vendors can make use of this API to ensure they are handling users appropriately to their current level of risk. [riskyUser resource type](/graph/api/resources/riskyuser).

:::image type="content" source="../media/integrate/identity/diagram-risky-user.png" alt-text="Diagram showing a user using an application, which then calls Azure Active Directory to retrieve the user's risk level." border="true" lightbox="../media/integrate/identity/diagram-risky-user-expanded.png":::

#### Unique product scenarios

The following guidance is for independent software vendors who offer specific kinds of solutions.

[Secure hybrid access integrations](/azure/active-directory/manage-apps/secure-hybrid-access-integrations)
Many business applications were created to work inside of a protected corporate network, and some of these applications make use of legacy authentication methods. As companies look to build a Zero Trust strategy and support hybrid and cloud-first work environments, they need solutions that connect apps to Azure Active Directory and provide modern authentication solutions for legacy applications. Use this guide to create solutions that provide modern cloud authentication for legacy on-premises applications.

[Become a Microsoft-compatible FIDO2 security key vendor](/azure/active-directory/authentication/concept-fido2-hardware-vendor)
FIDO2 security keys can replace weak credentials with strong hardware-backed public/private-key credentials which cannot be reused, replayed, or shared across services. You can become a Microsoft-compatible FIDO2 security key vendor by following the process in this document.

## Azure Active Directory B2C

Azure Active Directory B2C is a customer identity and access management (CIAM) solution capable of supporting millions of users and billions of authentications per day. It is a white-label authentication solution that enables user experiences which blend with branded web and mobile applications.

As with Azure Active Directory, partners can integrate with Azure Active Directory B2C by using [Microsoft Graph](/azure/active-directory-b2c/microsoft-graph-operations) and key security APIs such as the Conditional Access, confirm compromise, and risky user APIs. You can read more about those integrations in the Azure AD section above.

This section includes several other integration opportunities independent software vendor partners can support.

> [!NOTE]
> We highly recommend customers using Azure Active Directory B2C (and solutions that are integrated with it) activate [Identity Protection and Conditional Access in Azure Active Directory B2C](/azure/active-directory-b2c/conditional-access-identity-protection-overview).

### Integrate with RESTful endpoints

Independent software vendors can integrate their solutions via RESTful endpoints to enable multi-factor authentication (MFA) and role-based access control (RBAC), enable identity verification and proofing, improve security with bot detection and fraud protection, and meet Payment Services Directive 2 (PSD2) Secure Customer Authentication (SCA) requirements.

We have [guidance on how to use our RESTful endpoints](/azure/active-directory-b2c/api-connectors-overview?pivots=b2c-user-flow) as well as detailed sample walkthroughs of partners who have integrated using the RESTful APIs:

- [Identity verification and proofing](/azure/active-directory-b2c/partner-gallery#identity-verification-and-proofing), which enables customers to verify the identity of their end users
- [Role-based access control](/azure/active-directory-b2c/partner-gallery#role-based-access-control), which enables granular access control to end users
- [Secure hybrid access to on-premises application](/azure/active-directory-b2c/partner-gallery#role-based-access-control), which enables end users to access on-premises and legacy applications with modern authentication protocols
- [Fraud protection](/azure/active-directory-b2c/partner-gallery#fraud-protection), which enables customers to protect their applications and end users from fraudulent login attempts and bot attacks

### Web application firewall

Web Application Firewall (WAF) provides centralized protection for web applications from common exploits and vulnerabilities. Azure Active Directory B2C enables independent software vendors to integrate their WAF service such that all traffic to Azure Active Directory B2C custom domains (for example, login.contoso.com) always pass through the WAF service, providing an additional layer of security.

Implementing a WAF solution requires that you configure Azure Active Directory B2C custom domains. You can read how to do this in our [tutorial on enabling custom domains](/azure/active-directory-b2c/custom-domain?pivots=b2c-user-flow). You can also [see existing partners who have created WAF solutions that integrate with Azure Active Directory B2C](/azure/active-directory-b2c/partner-gallery#web-application-firewall).

## Next steps

- [What is Azure Active Directory?](/azure/active-directory/fundamentals/active-directory-whatis)
- [Partner gallery for Azure Active Directory B2C](/azure/active-directory-b2c/partner-gallery)
- [Identity Protection and Conditional Access for Azure Active Directory B2C](/azure/active-directory-b2c/conditional-access-identity-protection-overview)
