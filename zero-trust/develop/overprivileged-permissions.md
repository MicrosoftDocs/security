---
title: Reducing overprivileged permissions and apps
description: Learn why applications shouldn't request more permissions than they need (overprivileged) and how to limit privilege to manage access and improve security.
author: janicericketts
ms.author: jricketts
ms.service: identity
ms.topic: conceptual
ms.date: 10/28/2022
ms.custom: template-concept
ms.collection:
  - zerotrust-dev
# Customer intent: As a developer, I want to understand why applications should not request more permissions than they need (overprivileged) and how to limit privilege so that I can manage access and improve security.
---
# Reducing overprivileged permissions and apps

As a developer aiming to design and implement applications that follow the [guiding principles of Zero Trust](overview.md), you want to [increase application security with least privilege](/azure/active-directory/develop/secure-least-privileged-access). It's imperative that you reduce the attack surface of your application and the effect of a security breach.

In this article, you'll learn why applications shouldn't request more permissions than they need. You'll understand the term *overprivileged* and discover recommendations and best practices for limiting privilege in your applications to manage access and improve security.

## What is overprivileged?

[Overprivileged](/azure/active-directory/develop/secure-least-privileged-access#overprivileged-applications) occurs when an application requests or receives more permissions than it needs for it to properly function. The following examples of unused and reducible permissions will improve your understanding of overprivileged.

## Unused permissions

For this unused key example, imagine that there are three locked doors (blue, yellow, and green) as shown in the diagram below.

:::image type="content" source="../media/develop/overprivileged-permissions/diagram-unused-key-inline.png" alt-text="Diagram described in article content - three doors below each of which is a key of the same color as its corresponding door." lightbox="../media/develop/overprivileged-permissions/diagram-unused-key-expanded.png":::

Your assets are behind the doors. You have three keys (blue, yellow, and green) that allow you to open its corresponding door. For example, the blue key can open the blue door. When you only need access to the yellow door, you only carry the yellow key.

To best protect your assets, you only carry the keys you need when you need them and keep unused keys in a safe location.

## Reducible permissions

The reducible keys example is more complicated than the unused key example to which we now add two special keys as shown in the diagram below.

:::image type="content" source="../media/develop/overprivileged-permissions/diagram-reducible-key-inline.png" alt-text="Diagram described in article content - three doors below each of which is a key." lightbox="../media/develop/overprivileged-permissions/diagram-reducible-key-expanded.png":::

The first black key is a pass key that can open all the doors. The second black key can open the yellow and the green doors. When you only need access to the yellow and the green doors, you only carry the second black key. You keep your pass key in a safe location with the redundant green key.

In the Microsoft identity world, the keys are access permissions. Your resources and you, the key holder, are applications. If you understand the risk of carrying unnecessary keys, you're aware of the risk of your applications having unnecessary permissions.

## Permission gap and risk

How can doors and keys help to understand how overprivileged occurs? Why might your application have the right permissions to perform a task, but still be overprivileged? Let's look at the permission gap that might cause the discrepancy in the diagram below.

:::image type="content" source="../media/develop/overprivileged-permissions/diagram-permission-gap-inline.png" alt-text="Graph on right: Y-axis - Permissions, X-axis - Time; Upper curve - Granted Permissions, Lower curve - Permissions Used; Statistics on right described in article content." lightbox="../media/develop/overprivileged-permissions/diagram-permission-gap-expanded.png":::

The X axis represents **Time** and the Y axis represents **Permissions**. At the start of the measured **Time**, you request and receive permission for your application. As the business grows and changes over time, you add new permissions to support your needs and the slope of **Granted Permissions** increases. The **Permissions Used** may be lower than **Granted Permissions** when you forget to remove unnecessary permissions (for example, if the application doesn't break) resulting in a **Permission Gap**.

Here are interesting observations in the Microsoft identity platform.

- We have more than 4,000 APIs in Microsoft Graph.
- More than 200 Microsoft Graph permissions are available on Microsoft identity platform.
- Developers have access to a wide range of data and the ability to apply granularity to the permissions that their apps request.
- In our investigations, we found that apps have only 10% fully utilized permissions for their scenarios.

Think carefully about what permissions your app actually requires. Beware of the permission gap and regularly check your application permissions.

## Security compromised for overprivileged

Let's dive deeper into the risks that result from permission gaps with an example. This compromising scenario comprises two roles: IT admin and developer.

- IT admin: Jeff is a tenant admin who ensures that applications in Microsoft Entra ID are trustworthy and secure. Part of Jeff's job is to grant consent to permissions that app developers require.
- Developer: Kelly is an app developer who uses Microsoft identity platform and owns apps. Kelly's job is to ensure that applications have the right permissions to perform required tasks.

A common security compromise scenario for overprivileged typically has four stages as shown and described below.

:::image type="content" source="../media/develop/overprivileged-permissions/diagram-permission-scenario-inline.png" alt-text="Diagram described in article content - stages one through four of a security compromise scenario." lightbox="../media/develop/overprivileged-permissions/diagram-permission-scenario-expanded.png":::

1. First, the developer starts configuring the application and adding required permissions.
1. Second, the IT admin reviews required permissions and grants consent.
1. Third, the bad actor starts cracking user credentials and successfully hacks the user identity.
1. If the user owns multiple applications, they're also overprivileged. The bad actor can quickly use the token of the granted permission to retrieve sensitive data.

## Overprivileged applications

When an entity asks for or receives more permissions than it needs, it's overprivileged. The definition of *overprivileged application* in Microsoft identity platform is, "any application that's been granted an unused or reducible permission."

Let's use Microsoft Graph as part of the Microsoft identity platform in a real-world example to better understand unused permission and reducible permission.

:::image type="content" source="../media/develop/overprivileged-permissions/diagram-overprivileged-types-inline.png" alt-text="Left column: Unused - Being granted one or more permissions that aren't necessary at all for the API call being made. Right column: Reducible - Permission that has a lower-privileged alternative that would still provide the access for required tasks." lightbox="../media/develop/overprivileged-permissions/diagram-overprivileged-types-expanded.png":::

Unused permission occurs when your application receives permissions that aren't necessary for the desired tasks. For example, you're building a calendar app. Your calendar app requests and receives `Files.ReadWrite.All` permission. Your app doesn't integrate with any files' APIs. Therefore, your application has an unused `Files.ReadWrite.All` permission.

Reducible permission is more difficult to discover. It occurs when your application receives few permissions but has a lower privileged alternative that would provide sufficient access for required tasks. In the calendar app example, your app requests and receives `Files.ReadWrite.All` permission. However, it only needs to read files from the signed-in user's OneDrive and never needs to create new files or modify existing ones. In this case, your application only partially utilizes `Files.ReadWrite.All` so you need to downgrade to `Files.Read.All`.

## Recommendations for reducing overprivileged scenarios

Security is a journey, not a destination. There are three distinct phases in the security lifecycle:

- Prevention
- Auditing
- Remediation

The diagram below illustrates recommendations for reducing overprivileged scenarios.

:::image type="content" source="../media/develop/overprivileged-permissions/diagram-reduce-overprivileged-recommendations-inline.png" alt-text="Diagram described in article content - recommendations to prevent, audit, and remediate overprivileged scenarios." lightbox="../media/develop/overprivileged-permissions/diagram-reduce-overprivileged-recommendations-expanded.png":::

- **Prevent**: When building an application, you should fully understand the permission required for the API calls that your application needs to make, and only request what's necessary to enable your scenario. Microsoft Graph documentation has clear references for least privilege permissions to most privileged permission for all endpoints. Be mindful of overprivileged scenarios as you determine which permissions you need.
- **Audit**: You and IT admins should regularly review existing applications' previously granted privileges.
- **Remediate**: If you or IT admins notice an overprivileged application in the ecosystem, you should stop requesting tokens for the overprivileged permission. IT admins should revoke granted consents. This step usually requires a code change.

## Best practices for maintaining least privilege permission

Two major incentives for maintaining least privilege permission with your applications are driving application adoption and stopping the spread as summarized below.

:::image type="content" source="../media/develop/overprivileged-permissions/diagram-least-privilege-best-practices-inline.png" alt-text="Left column: Drive Adoption - Build a trustworthy third party app for customers by avoiding excessive permission requests. Right column: Stop the Spread - Attackers are unable to use excessive privileges to gain further access." lightbox="../media/develop/overprivileged-permissions/diagram-least-privilege-best-practices-expanded.png":::

- **Drive adoption by building a trustworthy third-party app for customers that avoids excessive permission requests.** Limit your application permissions to only what it needs to complete its task. This practice reduces the potential blast radius of attacks and increases customer adoption of your apps. Apply more scrutiny when reviewing permissions that  applications request and deciding whether to grant app permissions.
- **Stop the spread by ensuring attackers are unable to use excessive privileges to gain further access.** When you create an app that asks for unnecessary permissions, it will be least likely to receive approval or denied altogether. The best way to control damage is to prevent attackers from gaining elevated privilege that increases the scope of the compromise. For example, if your application only has `User.ReadBasic.All` to read user basic information, then your OneDrive, Outlook, Teams, and any confidential data are safe if an app is compromised.

## Next steps

- [Acquiring authorization to access resources](acquire-application-authorization-to-access-resources.md) helps you to understand how to best ensure Zero Trust when acquiring resource access permissions for your application.
- [Building apps with a Zero Trust approach to identity](identity.md) provides an overview of permissions and access best practices.
- [Customizing tokens](zero-trust-token-customization.md) describes the information that you can receive in Microsoft Entra tokens and how to customize tokens to improve flexibility and control while increasing application zero trust security with least privilege.
- [Configuring group claims and app roles in tokens](configure-tokens-group-claims-app-roles.md) shows you how to configure your apps with app role definitions and assign security groups to app roles to improve flexibility and control while increasing application zero trust security with least privilege.
- [Achieving Zero Trust readiness in your apps: Designing for Least Privilege](https://techcommunity.microsoft.com/t5/microsoft-entra-azure-ad-blog/achieving-zero-trust-readiness-in-your-apps-2-designing-for/ba-p/2959986) helps you to design apps using the principle of least privileged access with the Microsoft identity platform.
- [Increase application security with the principle of least privilege](/azure/active-directory/develop/secure-least-privileged-access) helps you to reduce the attack surface of an application and the effect of a security breach (the blast radius) should one occur in a Microsoft identity platform-integrated application.
- [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer) and [Microsoft Graph permissions reference](/graph/permissions-reference) helps you to select Microsoft Graph API calls to enable your app scenario and find corresponding permissions from least to most privileged.
