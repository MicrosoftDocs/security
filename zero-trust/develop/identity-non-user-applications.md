---
title: Providing application identity credentials when there's no user
description: In this article, we explain why the best Zero Trust client credentials practice for services (non-user applications) on Azure is Managed Identities for Azure Resources.
author: janicericketts
ms.author: jricketts
ms.service: identity
ms.topic: conceptual
ms.date: 09/15/2022
ms.custom: template-concept
# Customer intent: As a developer, I want to understand how to best identify non-user applications so that I can address the guiding principles of Zero Trust.
---
# Providing application identity credentials when there's no user

When you, as a developer, are building non-user applications, you don't have a user whom you can prompt for a username and password or Multifactor Authentication (MFA). You need to provide the application's identity on its own. This article explains why the best Zero Trust client credentials practice for services (non-user applications) on Azure is [Managed Identities for Azure resources](/azure/active-directory/managed-identities-azure-resources/overview-for-developers?tabs=portal%2Cdotnet).

## Issues with service accounts

Using a "service account" where you create a user account and use it for a service isn't a good solution because Azure Active Directory (Azure AD) doesn't have a service account concept. When admins create a user account for a service and then share the password with a developer, it's insecure because it can't be passwordless or have an MFA. Instead of using a user account as a service account, your best solution is to use one of the client credential options described below.

## Client credential options

There are four types of client credentials that can identify an application.

- Secret key
- Certificate
- [Managed Identities for Azure resources](/azure/active-directory/managed-identities-azure-resources/overview-for-developers?tabs=portal%2Cdotnet)
- [Federated Credentials](/azure/active-directory/develop/workload-identity-federation)

## Secret key or certificate?

Secret keys are acceptable when you have a sophisticated secrets management infrastructure (such as [Azure Key Vault](/azure/key-vault/general/overview)) in your enterprise. However, secret keys in scenarios where the IT Pro generates a secret key and then emails it to a developer who then might store it in an insecure location like a spreadsheet causes secret keys to not properly protected.

Certificate-based client credentials are more secure than secret keys. Certificates are better managed as they aren't the secret itself. The secret isn't part of a transmission. When you use a secret key, your client sends the actual value of the secret key to Azure AD. When you use a certificate, the private key of the certificate never leaves the device. Even if someone intercepts, decodes, and de-encrypts the transmission, the secret is still secure because the intercepting party doesn't have the private key.

## Best practice: use Managed Identities for Azure Resources

When you're developing services (non-user applications) in Azure, Managed Identities for Azure Resources provide an automatically managed identity in Azure AD. The app can authenticate to any service that supports Azure AD authentication without managing credentials. You don't need to manage secrets; you don't need to address the possibility of losing or mishandling them. Secrets can't be intercepted because they don't move across the network. [Managed Identities for Azure resources](/azure/active-directory/managed-identities-azure-resources/overview-for-developers?tabs=portal%2Cdotnet) is the best practice if you're building services on Azure.

## Next steps

- [Supported identity and account types for single- and multi-tenant apps](identity-supported-account-types.md) explains how you can choose if your app allows only users from your Azure Active Directory (Azure AD) tenant, any Azure AD tenant, or users with personal Microsoft accounts by configuring your app to be either single tenant or multitenant during app registration in Azure and ensure the Zero Trust principle of least privilege access so that your app only requests permissions it needs.
- [Developing application permissions strategy](developer-strategy-application-permissions.md) helps you to decide upon your application permissions approach to credential management when you use the Microsoft identity platform to authenticate and authorize your applications and manage permissions and consent.
- When you're building non-user applications, you don't have a user whom you can prompt for a username and password or Multifactor Authentication (MFA). You need to provide the application's identity on its own. [Providing application identity credentials when there's no user](identity-non-user-applications.md) explains why the best Zero Trust client credentials practice for services (non-user applications) on Azure is Managed Identities for Azure resources.
- [Authorization best practices](developer-strategy-authorization-best-practices.md) helps you to implement the best authorization, permission, and consent models for your applications.
- Use [Zero Trust identity and access management development best practices](identity-iam-development-best-practices.md) in your application development lifecycle so that you can create secure applications that are [Zero Trust compliant](identity-zero-trust-compliance.md).
- [Building apps with a Zero Trust approach to identity](identity.md) continues from the [Zero Trust identity and access management development best practices](identity-iam-development-best-practices.md) article to help you use a Zero Trust approach to identity in your software development lifecyle (SDLC).
