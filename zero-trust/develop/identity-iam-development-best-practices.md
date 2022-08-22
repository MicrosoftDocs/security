---
title: Zero Trust identity and access management development best practices
description: To create a secure application that follows Zero Trust principles, Microsoft recommends that you incorporate several best practices throughout your application development lifecycle, some of which are provided in this article.
author: janicericketts
ms.author: jricketts
ms.service: security
ms.topic: conceptual
ms.date: 06/27/2022
ms.custom: template-concept
# Customer intent: As a developer, I want to know best practices for my application development lifecycle, so that I can create secure applications that follows Zero Trust principles.
---
# Zero Trust identity and access management development best practices

To create a secure application that follows Zero Trust principles, Microsoft recommends that you incorporate several best practices throughout your application development lifecycle, some of which are provided below.

| Best Practice | Details |
|---------|---------|
| Use Microsoft Authentication Library (MSAL) and Microsoft Graph | Developing your application by following known and accepted standards and libraries increases application portability and security. [MSAL](/azure/active-directory/develop/msal-overview) and [Microsoft Graph](/graph/overview) are the best choices when developing an Azure Active Directory (AD) application.<br><br>Microsoft highly recommends that you develop your application using libraries such as MSAL rather than protocols because protocols have flaws, and their documentation can be extensive. MSAL developers have done the work for you with respect to compliance with protocols and MSAL is optimized for efficiency when working directly with Azure AD.  |
| Delegate Identity and Access Management | Develop your application to use tokens for explicit identity verification and access control that can be defined and managed by your customer. Microsoft does not recommend that you create your own username and password management system for your application. |
| Plan for least privilege access policies | Zero Trust dictates that customers implement least privilege access. Your application must be developed and documented sufficiently that these policies can be configured successfully, meaning that your application must support tokens, and all APIs and resources that your application will call must be understood and documented. |
| Manage tokens | Your application will request tokens from Azure AD. Managing these tokens involves verifying they are valid and scoped to your application, caching them appropriately, and using them as intended. Microsoft recommends that you handle token issues by checking for error classes and coding appropriate responses. Note that you should not read access tokens directly. Instead, use Microsoft identity platform best practices application to view access token scope and details under token response. |
