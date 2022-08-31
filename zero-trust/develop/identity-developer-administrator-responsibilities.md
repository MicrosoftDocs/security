---
title: Developer and administrator responsibilities
description: As a developer creating applications in the Microsoft identity platform, knowing what your IT Pros need from you, and what you need from them, will help you to streamline your zero-trust development workflow.
author: janicericketts
ms.author: jricketts
ms.service: network-access
ms.topic: conceptual
ms.date: 06/27/2022
ms.custom: template-concept
# Customer intent: As a developer creating applications in the Microsoft identity platform, I want to know what my IT Pros need from me, and what I need from them, so that I can streamline my zero-trust development workflow.
---
# Developer and administrator responsibilities for application registration,  authorization, and access

As a developer creating applications in the Microsoft identity platform, you will work with IT Professionals who have administrator privileges in Azure Active Directory (AD) to enable your applications to take full advantage of the Microsoft identity platform. Knowing what your IT Pros need from you, and what you need from them, will help you to streamline your zero-trust development workflow.

The following summarizes the decisions and tasks required for the developer and IT Pro roles to build and deploy secure applications in the Microsoft identity platform. Read on for key details and links to articles to help you plan your secure application development.

:::row:::
   :::column span="":::
      **Developer**
      - Register app in Microsoft Azure
      - Define supported account types
      - Is the app working on behalf of itself or the user
      - What resources your application requires and when it needs them
      - When to ask for permission to a resource
   :::column-end:::
   :::column span="":::
      **IT Pro Administrator**
      - Who can register apps in the tenant(s)
      - Application user, group, and role assignments
      - Permissions granted to the application
      - Policies including conditional access policy and token lifespan
      - Alternate local settings for an application
   :::column-end:::
:::row-end:::

## Zero Trust considerations

IT Pro administrators will determine which conditional access policies will apply to this application (SAML) or the resources this application is accessing (OAuth 2.0). We apply conditional access policies to Security Assertions Markup Language (SAML) apps at authentication. For OAuth 2.0 applications, we apply these when an application attempts to access a resource.

When entities (individuals, applications, devices) need to access resources in your application, you will work with IT Pros who have administrator privileges to look at Zero Trust and security policy enforcement options and decide which policies to implement and enforce for access. Microsoft's policy enforcement engine needs to be in touch with things like threat intelligence, signal processing, and the policies that are already in place for the organization. Every time an entity needs to access a resource, it will go through the policy enforcement engine.

## Next steps

- [Best practices for Azure AD application registration configuration - Microsoft Entra \| Microsoft Docs](/azure/active-directory/develop/security-best-practices-for-app-registration) describes security best practices for the following application properties: Redirect URI, Access tokens (used for implicit flows), Certificates and secrets, Application ID URI, and Application ownership.

- [Best practices for the Microsoft identity platform - Microsoft Entra \| Microsoft Docs](/azure/active-directory/develop/identity-platform-integration-checklist) highlights best practices, recommendations, and common oversights when integrating with the Microsoft identity platform.

- [Securing identity with Zero Trust \| Microsoft Docs](../deploy/identity.md) describes how identities function as a powerful, flexible, and granular way to control access to data.
