---
title: Develop application permissions strategy
description: Learn how to define an application permission approach to credential management to authenticate, authorize, and manage permissions and consent.
author: janicericketts
ms.author: jricketts
ms.service: identity
ms.topic: conceptual
ms.date: 05/24/2024
ms.custom: template-concept
ms.collection:
  - zerotrust-dev
# Customer intent: As a developer, I want to learn how to define my application permission approach to credential management to authenticate, authorize, and manage permissions and consent.
---
# Develop application permissions strategy

As you learn to [develop using Zero Trust principles](overview.md), reference this article after reviewing [Acquire authorization to access resources](acquire-application-authorization-to-access-resources.md) and [Develop delegated permissions strategy](developer-strategy-delegated-permission.md). Define your application permissions approach to credential management when you use the Microsoft identity platform to [authenticate and authorize](/entra/identity-platform/authentication-vs-authorization) your applications and manage [permissions and consent](/entra/identity-platform/permissions-consent-overview).

When [no user is involved](../develop/identity-non-user-applications.md), you don't have an [effective permission model](developer-strategy-delegated-permission.md) because your application is always granted its preassigned permissions.

- **App proves it's the app requesting permission.** Your application [proves its own identity](../develop/identity-non-user-applications.md) with one of the following methods:
  - a certificate, which is the best option, or
  - a secret in a sophisticated secret management system, or
  - when you're developing your services on Azure, use [Managed Identities for Azure resources](/entra/identity/managed-identities-azure-resources/overview), review the following [Manage application credentials section](#manage-applications-credentials).

- **App always requires advance admin consent.** Your application requests this permission with the `.default` scope. It requests the permissions the admin assigns to the application.

- **Trans user functionality.** By default, `User.ReadWrite.All` allows your application to update every user's profile. As an application permission, it allows your application to read and update the profile of every user in the tenant.

- **Permissions granted the app are always the permissions used.** Unlike a [delegated permission](developer-strategy-delegated-permission.md), application permissions aren't bounded by what any particular user can do.

## Limit application permissions

There are three ways limit an application to less than global access.

- Microsoft Teams apps have [resource-specific consent](/microsoftteams/platform/graph-api/rsc/resource-specific-consent) (RSC) that allows an application to access a specific team rather than access all teams in the enterprise. RSC is a Microsoft Teams and Microsoft Graph API integration that allows your app to use API endpoints and manage specific resources. Its permissions model enables Teams and Chat owners to grant consent for your application to access and modify their Teams and Chat data.

- Microsoft Exchange administrators can create [Exchange application policies](/graph/auth-limit-mailbox-access) to limit app access to specific mailboxes with a PowerShell script. They can limit a particular application to specific mailboxes with `Calendar.Read` or `Mail.Read` access. That allows you to, for example, build an automation that can only read one mailbox or only send mail from one mailbox and not from everyone in the enterprise.

- SharePoint has [Sites.Selected as a specific scope](https://devblogs.microsoft.com/microsoft365dev/controlling-app-access-on-specific-sharepoint-site-collections/) to allow granular permissions for accessing SharePoint with an application. Choosing `Sites.Selected` for your application instead of one of the other permissions results, by default, in your application not having access to any SharePoint site collections. The administrator uses the site permissions endpoint to grant Read, Write, or Read and Write permissions to your application.

## Manage applications credentials

Credential hygiene can ensure that your application quickly recovers from a potential breach. The following best practices guide you in developing applications that carry out detection and remediation while avoiding downtime and affecting legitimate users. These recommendations support the [Zero Trust principle of assume breach](../zero-trust-overview.md) in preparing you to respond to a security incident.

- **Remove all secrets from code and configuration**. When you're using the Azure platform, place secrets in [Key vault](/azure/key-vault/general/basic-concepts) and access them via [Managed Identities for Azure resources](/entra/identity/managed-identities-azure-resources/overview). Make your code resilient to handle secret rotations if a compromise occurs. IT admins can remove and rotate secrets and certificates without taking down your application or affecting legitimate users.

- **Use certificates instead of client secrets unless a secure process is in place to manage secrets**. Attackers know that client secrets tend to be less securely handled and leaked secret usage is difficult to track. Certificates can be better managed and revoked if compromised. When you use secrets, build or use a secure no-touch deployment and rollover process for them. Use secrets with a set expiry time period (for example, one year, two years) and avoid *never expires*.

- **Regularly roll over certificates and secrets** to [build resiliency](/entra/architecture/resilience-app-development-overview) in your application and avoids outage due to an emergency rollover.

## Next steps

- [Acquire authorization to access resources](acquire-application-authorization-to-access-resources.md) helps you to understand how to best ensure Zero Trust when acquiring resource access permissions for your application.
- [Develop delegated permissions strategy](developer-strategy-delegated-permission.md) helps you to implement the best approach for managing permissions in your application and develop using Zero Trust principles.
- [Authorization best practices](developer-strategy-authorization-best-practices.md) helps you to implement the best authorization, permission, and consent models for your applications.
- [Request permissions that require administrative consent](permissions-require-admin-consent.md) describes the permission and consent experience when application permissions require administrative consent.
- [API Protection](protect-api.md) describes best practices for protecting your API through registration, defining permissions and consent, and enforcing access to achieve your Zero Trust goals.
- [Provide application identity credentials when there's no user](identity-non-user-applications.md) explains why Managed Identities for Azure resources is the best client credentials practice for services (nonuser applications) on Azure.
