---
title: Requesting permissions that require administrative consent
description: Learn about the permission and consent experience when your application requires administrative consent so that you can better collaborate with admins to implement the Zero Trust principle of least privilege in your applications.
author: janicericketts
ms.author: jricketts
ms.service: identity
ms.topic: conceptual
ms.date: 04/17/2024
ms.custom: template-concept 
ms.collection:
  - zerotrust-dev
# Customer intent: As a developer, I want to learn about the permission and consent experience when my application requires administrative consent so that I can better collaborate with admins to implement the Zero Trust principle of least privilege in my applications.
---
# Requesting permissions that require administrative consent

In this article, we'll describe the permission and consent experience for a scenario where you, as a developer, are writing your application code to request [application permissions](developer-strategy-application-permissions.md) that will require administrative consent. Example screenshots of permission and consent dialogs and the Microsoft Entra admin center give you an idea of what your users and tenant admins experience. Improve collaboration with admins to implement the [Zero Trust](overview.md) principle of least privilege in your applications.

As you develop your application, you'll write code that requests [access to a resource](acquire-application-authorization-to-access-resources.md) by requesting an access token with a specific scope (or permission). You'll use the scope parameter as described in the [OAuth 2.0](/azure/active-directory/fundamentals/auth-oauth2) standard that some people describe as a permission. A resource owner will grant or deny each request for permission. In Microsoft Entra ID, the resource owner is either the user of the app or an admin who has the rights to grant consent to that resource on behalf of all users.

## User consent experience

When your application requests permission to access a resource, your user may see a **Permissions requested** dialog similar to this example.

:::image type="content" source="../media/develop/permissions-require-admin-consent/screenshot-app-perm-req-sign-in-access-data-inline.png" alt-text="Screenshot of Permissions requested dialog that describes the permissions the app is requesting with Cancel and Accept buttons." lightbox="../media/develop/permissions-require-admin-consent/screenshot-app-perm-req-sign-in-access-data-expanded.png":::

In the above example dialog, the user grants consent to allow the app to read the data on their behalf by selecting **Accept** or denies the request by selecting **Cancel**. The application receives an access token and will be able to continue its processes after the user grants consent. Remember to ensure that your app is ready to gracefully handle when it doesn't receive a token.

## Admin consent experience

For some access requests, only an admin can grant consent. If the requested access is powerful or involves resources whose owners aren't the current users, code so that only an admin can grant requests.

However, you never know which permissions will require admin consent and which allow a regular user to grant consent because tenant admins can configure their tenant with **Do not allow user consent** (all permissions require admin consent) as shown in the following example screenshot of **User consent settings** in the [Microsoft Entra admin center](/azure/active-directory/manage-apps/configure-user-consent?tabs=azure-portal).

:::image type="content" source="../media/develop/permissions-require-admin-consent/screenshot-entra-user-consent-settings-inline.png" alt-text="Screenshot of Microsoft Entra admin center 'User consent settings' that configure consent for applications to access organization data." lightbox="../media/develop/permissions-require-admin-consent/screenshot-entra-user-consent-settings-expanded.png":::

Admins can also **Allow user consent for apps from verified publishers, for selected permissions** as shown in the following example screenshot of **User consent settings** in the Microsoft Entra admin center.

:::image type="content" source="../media/develop/permissions-require-admin-consent/screenshot-entra-user-consent-settings-allow-user-inline.png" alt-text="Screenshot of Microsoft Entra admin center 'User consent settings' that configure consent for apps from verified publishers." lightbox="../media/develop/permissions-require-admin-consent/screenshot-entra-user-consent-settings-allow-user-expanded.png":::

Admins can then **Add permissions** to which users can consent as shown in the following example screenshot of **Permission classifications** in the Microsoft Entra admin center.

:::image type="content" source="../media/develop/permissions-require-admin-consent/screenshot-entra-permission-classifications-inline.png" alt-text="Screenshot of Microsoft Entra admin center 'Permission classifications' that configures permission classifications that allow user consent." lightbox="../media/develop/permissions-require-admin-consent/screenshot-entra-permission-classifications-expanded.png":::

When your app requests a permission that requires admin consent (by design or admin configuration), your user may see a **Need admin approval** dialog similar to this example.

:::image type="content" source="../media/develop/permissions-require-admin-consent/screenshot-app-perm-req-need-admin-approval-inline.png" alt-text="Screenshot of 'Need admin approval' dialog that describes how requested permissions can be granted only by an admin." lightbox="../media/develop/permissions-require-admin-consent/screenshot-app-perm-req-need-admin-approval-expanded.png":::

The above example dialog shows the default (out of the box) experience for permissions that require admin consent. Most users don't know what to do in this scenario. They don't know who their admin is, they don't know who to go to for approval. This uncertainty can limit the user's ability to achieve desired results.

## Improving the permissions and consent experience

To improve the permissions and consent experience, the tenant admin can [configure the admin consent workflow](/azure/active-directory/manage-apps/configure-admin-consent-workflow) as shown in the following example screenshot of **User settings** in the Microsoft Entra admin center.

:::image type="content" source="../media/develop/permissions-require-admin-consent/screenshot-entra-user-settings-inline.png" alt-text="Screenshot of Microsoft Entra admin center 'User settings' that configures 'Admin consent requests.'" lightbox="../media/develop/permissions-require-admin-consent/screenshot-entra-user-settings-expanded.png":::

Below **Admin consent requests**, the tenant admin can improve the user's permission and consent experience by selecting **Yes** on **Users can request admin consent to apps they're unable to consent to** and configuring other **Admin consent requests** settings.

After the tenant admin selects **Yes** on **Users can request admin consent to apps they're unable to consent to** and an application requests a permission that requires admin consent, the user will see something similar to the following **Approval required** dialog that provides a better user experience.

:::image type="content" source="../media/develop/permissions-require-admin-consent/screenshot-app-perm-req-admin-approval-required-inline.png" alt-text="Screenshot of 'Approval required' dialog that describes the permissions the app is requesting with a text field to 'Enter justification for requesting this app.'" lightbox="../media/develop/permissions-require-admin-consent/screenshot-app-perm-req-admin-approval-required-expanded.png":::

In the above example dialog, the user can **Enter justification for requesting this app** before selecting **Request approval**. The approval request then enters an **Admin consent requests** queue (example screenshot below) where admins have options to review, accept, or ban applications in their organization based on risk profile.

:::image type="content" source="../media/develop/permissions-require-admin-consent/screenshot-entra-admin-consent-requests-inline.png" alt-text="Screenshot of Microsoft Entra admin center 'Admin consent requests' that configures pending requests." lightbox="../media/develop/permissions-require-admin-consent/screenshot-entra-admin-consent-requests-expanded.png":::

When an admin runs an application that requires admin consent (and the admin hasn't yet configured that consent in the Microsoft Entra admin center), the admin user sees a slightly different **Permissions requested** dialog similar to the following example.

:::image type="content" source="../media/develop/permissions-require-admin-consent/screenshot-app-perm-req-consent-obo-org-inline.png" alt-text="Screenshot of 'Permissions requested' dialog that describes the permissions the app is requesting with a checkbox to toggle 'Consent on behalf of your organization.'" lightbox="../media/develop/permissions-require-admin-consent/screenshot-app-perm-req-consent-obo-org-expanded.png":::

In the above example, the admin sees a description of the permissions that the application is requesting. The admin can select **Accept** to individually run the application or they can select **Consent on behalf of your organization** before selecting **Accept**. After the admin grants consent for the organization, no future organization users will need to grant permission for this application unless an admin removes consent from the tenant **Admin consent requests** configuration.

Another method of tenant admin consent is in Microsoft Entra admin center **Permissions** where admins can review the details of existing permissions the app has already requested similar to this example.

:::image type="content" source="../media/develop/permissions-require-admin-consent/screenshot-entra-permissions-user-consent-inline.png" alt-text="Screenshot of Microsoft Entra admin center 'Permissions' that displays details of existing application requests." lightbox="../media/develop/permissions-require-admin-consent/screenshot-entra-permissions-user-consent-expanded.png":::

In the above **User consent** example, the admin can review the granted permissions for the app along with information about claims, permission type, and who gave consent. The admin can select **Admin consent** to review granted permissions that require admin consent.

## Requesting admin consent in advance

Your best [application permissions strategy](developer-strategy-application-permissions.md) is to declare in advance all of the permissions that your app may need or will eventually request when you [register your app](/azure/active-directory/develop/quickstart-register-app). You don't have to request all permissions at the same time but, after you declare all of the permissions that your app may need, admins can select **Grant admin consent for** in your app's configuration in the tenant to display a dialog similar to this example.

:::image type="content" source="../media/develop/permissions-require-admin-consent/screenshot-app-perm-req-review-for-org-inline.png" alt-text="Screenshot of 'Permissions requested Review for your organization' dialog that describes the permissions the app is requesting with Cancel and Accept buttons." lightbox="../media/develop/permissions-require-admin-consent/screenshot-app-perm-req-review-for-org-expanded.png":::

The above example shows how the admin can pre-consent to the permissions that you declared and provide the best experience for your users and tenant admins.

Requesting admin consent ahead of time is an excellent choice for line of business (LOB) apps, especially the apps that your organization is developing. It's easier to not have to ask your user if your company can access your company's data by pre-consenting those applications. You make the admin consent request as part of your app registration process.

## Next steps

- [Acquiring authorization to access resources](acquire-application-authorization-to-access-resources.md) helps you to understand how to best ensure Zero Trust when acquiring resource access permissions for your application.
- [API Protection](protect-api.md) describes best practices for protecting your API through registration, defining permissions and consent, and enforcing access to achieve your Zero Trust goals.
- [Authorization best practices](developer-strategy-authorization-best-practices.md) helps you to implement the best authorization, permission, and consent models for your applications.
- [Customizing tokens](zero-trust-token-customization.md) describes the information that you can receive in Microsoft Entra tokens and how to customize tokens to improve flexibility and control while increasing application zero trust security with least privilege.
- [Overview of permissions and consent in the Microsoft identity platform](/azure/active-directory/develop/permissions-consent-overview) helps you to understand foundational concepts of access and authorization.
- [Overview of consent and permissions](/azure/active-directory/manage-apps/consent-and-permissions-overview) helps you to learn foundational concepts and scenarios around consent and permissions in Microsoft Entra ID.
- Learn module: [Permissions and consent framework](/learn/modules/identity-permissions-consent/) helps you to learn permissions and consent framework models.
- Learn Live: [Microsoft Identity: Permissions and Consent Framework](/shows/learn-live/permissions-and-consent-framework) helps you to learn the basics of Microsoft identity including tokens, account types, and topologies.
