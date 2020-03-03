---
title: "Capabilities"
ms.author: dansimp
author: dansimp
manager: dansimp
audience: Admin
ms.topic: article
localization_priority: Normal
description: "Capabilities"
---

# Identity capabilities

This article lists capabilities that can help with identity.

## Cloud identity services
<br>

|Capability  |Description  |See more  |
|---------|---------|---------|
|Azure Active Directory |Establish a single Azure AD enterprise directory for managing identities of full-time employees and enterprise resources. A single authoritative source increases clarity and consistency for all roles in IT and Security and reduces security risk from human errors and automation failures resulting from complexity.|[Azure Active Directory documentation](https://docs.microsoft.com/azure/active-directory/)        |
|Azure AD Connect|Synchronize Azure AD with your existing authoritative on premises Active Directory using Azure AD connect. This is also required for an Office 365 migration, so it is often already done before Azure migration and development projects begin.|[What is hybrid identity with Azure Active Directory?](https://docs.microsoft.com/azure/active-directory/hybrid/whatis-hybrid-identity)|
|Azure AD B2B collaboration|Use Azure AD business-to-business (B2B) collaboration to host non-employee accounts like vendors and partners. This reduces risk by granting the appropriate level of access to external entities instead of the full default permissions given to full-time employees. This least privilege approach and clear clearly differentiation of external accounts from company staff makes it easier to prevent and detect attacks coming in from these vectors.|[Azure Active Directory B2B documentation](https://docs.microsoft.com/azure/active-directory/b2b/)|
|Azure AD B2C |Use Azure AD B2C for customer and citizen accounts. Azure AD B2C is an identity management service that enables custom control of how your customers sign up, sign in, and manage their profiles when using your iOS, Android, .NET, single-page (SPA), and other applications.     |[Azure Active Directory B2C documentation](https://docs.microsoft.com/azure/active-directory-b2c/)    |
|     |         |         |

## Identity security capabilities
<br>

|Capability |Description  |More information  |
|---------|---------|---------|
|Azure Multi-Factor Authentication (MFA)|MFA provides additional security by requiring a second form of authentication. |[How MFA works](https://docs.microsoft.com/azure/active-directory/authentication/concept-mfa-howitworks) |
|Passwordless authentication|Azure AD supports several methods of passwordless authentication, including Windows Hello for Business, Microsoft Authenticator app, and FIDO2 security keys. Passwordless authentication methods are convenient because the password is removed and replaced with something you have, plus something you are or something you know.|[Passwordless authentication options for Azure Active Directory](https://docs.microsoft.com/azure/active-directory/authentication/concept-authentication-passwordless)|
|Conditional Access     |With Conditional Access, Azure AD evaluates the conditions of the user login and uses conditional access policies you create to allow access. For example, you can create a Conditional Access policy to require device compliance for access to sensitive data. This greatly reduces the risk that a person with a stolen identity can access your sensitive data. It also protects sensitive data on the devices, because the devices must meet specific requirements for health and security.   |[Conditional Access documentation](https://docs.microsoft.com/azure/active-directory/conditional-access/)<br><br>[Common Conditional Access policies](https://docs.microsoft.com/azure/active-directory/conditional-access/concept-conditional-access-policy-common)  <br><br>[Recommended identity and device access configurations](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-policies-configurations?view=o365-worldwide)   |
|Azure AD self-service password reset (SSPR)|SSPR allows your users to reset their passwords securely and without helpdesk intervention, by providing verification of multiple authentication methods that the administrator can control. |[How it works: Azure AD self-service password reset](https://docs.microsoft.com/azure/active-directory/authentication/concept-sspr-howitworks)|
|Azure Active Directory Identity Protection |Azure AD Identity Protection enables you to detect potential vulnerabilities affecting your organization’s identities and configure automated remediation policy to low, medium, and high sign-in risk and user risk.| [What is Azure Active Directory Identity Protection?](https://docs.microsoft.com/azure/active-directory/identity-protection/overview-identity-protection)        |
||||


## Additional identity security capabilities for administrators
<br>

|Capability  |Description  |More information |
|---------|---------|---------|
|Azure AD Privileged Identity Management    |   Privileged Identity Management provides time-based and approval-based role activation to mitigate the risks of excessive, unnecessary, or misused access permissions on resources that you care about. |   [What is Azure AD Privileged Identity Management?](https://docs.microsoft.com/azure/active-directory/privileged-identity-management/pim-configure)      |
|Managed Identities    | You can reduce use of passwords by applications using Managed Identities to grant access to resources in Azure        |[What are managed identities for Azure resources? ](https://docs.microsoft.com/azure/active-directory/managed-identities-azure-resources/overview)   |
|    |         |         |


