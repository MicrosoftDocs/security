---
title: Application identity credentials when there's no user
description: Learn why the best Zero Trust client credentials practice for services (nonuser applications) on Azure is Managed Identities for Azure Resources.
author: janicericketts
ms.author: jricketts
ms.topic: conceptual
ms.service: zero-trust
ms.date: 02/24/2025
ms.custom: template-concept
ms.collection:
  - zerotrust-dev
# Customer intent: As a developer, I want to understand how to best identify non-user applications so that I can address the guiding principles of Zero Trust.
---
# Provide application identity credentials when there's no user

When you, as a developer, build nonuser applications, you don't have a user whom you can prompt for a username and password or Multifactor Authentication (MFA). You need to provide the application's identity on its own. This article explains why the best Zero Trust client credentials practice for services (nonuser applications) on Azure is [Managed Identities for Azure resources](/entra/identity/managed-identities-azure-resources/overview-for-developers?tabs=portal%2Cdotnet).

## Issues with service accounts

Use of a *service account* (use of a user account for a service) isn't a good solution. Microsoft Entra ID doesn't have a service account concept. When admins create user accounts for services and then share passwords with developers, it's insecure. It can't be passwordless or have an MFA. Instead of using a user account as a service account, your best solution is to use one of the following client credential options.

## Client credential options

There are four types of client credentials that can identify an application.

- Secret key
- Certificate
- [Managed Identities for Azure resources](/entra/identity/managed-identities-azure-resources/overview-for-developers?tabs=portal%2Cdotnet)
- [Federated Credentials](/entra/workload-id/workload-identity-federation)

## Secret key or certificate?

Secret keys are acceptable in sophisticated secrets management infrastructures (such as [Azure Key Vault](/azure/key-vault/general/overview)). However, you can't properly protect secret keys in scenarios where the IT Pro generates a secret key and then emails it to a developer.

Certificate-based client credentials are more secure than secret keys. You can better manage certificates because they aren't the secret itself. The secret isn't part of a transmission. When you use a secret key, your client sends the actual value of the secret key to Microsoft Entra ID. When you use a certificate, the private key of the certificate never leaves the device. Even if someone intercepts, decodes, and de-encrypts the transmission, the secret is still secure because the intercepting party doesn't have the private key.

## Best practice: use Managed Identities for Azure Resources

When you develop services (nonuser applications) in Azure, Managed Identities for Azure Resources provide an automatically managed identity in Microsoft Entra ID. The app can authenticate to any service that supports Microsoft Entra authentication without managing credentials. You don't need to manage secrets. You don't need to address the possibility of losing or mishandling them. Bad actors can't intercept secrets that don't move across the network. [Managed Identities for Azure resources](/entra/identity/managed-identities-azure-resources/overview-for-developers?tabs=portal%2Cdotnet) is the best practice when you build services on Azure.

## Next steps

- [Supported identity and account types for single- and multitenant apps](identity-supported-account-types.md) explains how you can choose if your app allows only users from your Microsoft Entra tenant, any Microsoft Entra tenant, or users with personal Microsoft accounts.
- [Develop application permissions strategy](developer-strategy-application-permissions.md) helps you to decide upon your application permissions approach to credential management.
- [Provide application identity credentials when there's no user](identity-non-user-applications.md) explains why Managed Identities for Azure resources is the best client credentials practice for services (nonuser applications) on Azure.
- [Authorization best practices](developer-strategy-authorization-best-practices.md) helps you to implement the best authorization, permission, and consent models for your applications.
- Use [Zero Trust identity and access management development best practices](identity-iam-development-best-practices.md) in your application development lifecycle to create secure applications.
- [Building apps with a Zero Trust approach to identity](identity.md) provides an overview of permissions and access best practices.
