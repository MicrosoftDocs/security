---
title: Continuous access evaluation for Microsoft 365 - Microsoft 365 for enterprise
description: Describes how conditional access evaluation for Microsoft 365 and Microsoft Entra ID proactively terminates active user sessions and enforces policy changes in near real time.
author: chrisda
ms.author: chrisda
manager: dansimp
ms.service: defender-office-365
ms.topic: conceptual
audience: Admin
f1.keywords:
  - NOCSH
ms.custom:
  - it-pro
  - goldenconfig
ms.collection:
  - M365-identity-device-management
  - m365-security
  - m365solution-identitydevice
  - m365solution-scenario
  - highpri
  - tier1
search.appverid: met150
ms.date: 01/23/2025
---

# Continuous access evaluation for Microsoft 365

Modern cloud services that use OAuth 2.0 for authentication traditionally rely on access token expiration to revoke user access. Even if an admin revokes access for a user account, the user still has access to services until the access token expires. Before continuous access evaluation, the time frame for expiration was up to one hour.

Continuous access evaluation for Microsoft 365 and Microsoft Entra ID proactively terminates active user sessions and enforces policy changes in near real time.

Microsoft Entra ID notifies supported Microsoft 365 services when the authentication state of a user account requires reevaluation. When a supported app tries to access a Microsoft 365 service with a revoked access token, the service rejects the token, and the user session is redirected to Microsoft Entra ID for reauthentication. This action is known as *claim challenge*. The result is near real time enforcement of user account and policy changes.

Here are some other benefits of continuous access evaluation:

- Prevents using copied/exported tokens via the Microsoft Entra IP address location policy. Microsoft Entra ID synchronizes policies to supported Microsoft 365 services. When an access token attempts to access a service from an IP address range outside the range specified in the policy, the service rejects the token.

- Improves resiliency by requiring less token refreshes. Tokens that last longer (for example, longer than one hour) are available because supported services receive proactive notifications when reauthentication is required. With tokens that last longer, clients don't need to request token refreshes from Microsoft Entra ID as often, so the user experience is more resilient.

Here are some examples where continuous access evaluation improves security for user access control:

- An account password was compromised, so an admin invalidates all existing sessions and resets the account password in the Microsoft 365 admin center. In near real time, all existing user sessions with Microsoft 365 services are invalidated.

- A user working on a company Word document takes their tablet to a public coffee shop that isn't in an approved IP address range. At the coffee shop, the user's access to the document is immediately blocked.

Currently, the following Microsoft 365 services and apps support continuous access evaluation:

- **Services**:
  - Exchange Online
  - Microsoft Teams
  - OneDrive
  - SharePoint
- **Apps**: The following apps support continuous access evaluation (claim challenge) on the web, in Windows, Mac, iOS/iPadOS, and Android:
  - Microsoft Office<sup>\*</sup>
  - Microsoft Outlook
  - Microsoft Teams
  - OneDrive
  - SharePoint

  <sup>\*</sup> Claim challenge isn't supported in Office on the web.

  For apps that don't support continuous access evaluation, the access token lifetime to Microsoft 365 remains at one hour by default.

Continuous access evaluation is included in all versions of Office 365 and Microsoft 365. Configuring Conditional Access policies requires Microsoft Entra ID P1, which is included in all Microsoft 365 versions.

> [!TIP]
> For the limitations of continuous access evaluation, see [this article](/entra/identity/conditional-access/concept-continuous-access-evaluation#limitations).

## Scenarios supported by Microsoft 365

Continuous access evaluation supports two types of events:

- **Critical events**: A user should automatically lose access. For example:
  - The account is disabled.
  - The password is changed.
  - User sessions are revoked.
  - Multifactor authentication (MFA) is enabled for the user.
  - The account risk increased based on information from [Microsoft Entra ID Protection](/entra/id-protection/overview-identity-protection)

- **Conditional Access policy evaluation**: A user should lose access based on a Conditional Access policy. Conditional Access policy evaluation occurs when the account is no longer connected from a trusted network.

The following Microsoft 365 services currently support continuous access evaluation by listening to events from Microsoft Entra ID:

|Enforcement type|Exchange Online|SharePoint|Teams|
|---|:---:|:---:|:---:|
|**Critical events:**||||
|&nbsp;&nbsp;User revocation|✔|✔|✔|
|&nbsp;&nbsp;User risk|✔||✔|
|**Conditional Access policy evaluation:**||||
|&nbsp;&nbsp;IP address location policy|✔|✔¹|✔²|

¹ Web access to SharePoint supports instant IP policy enforcement by enabling strict mode. Without strict mode, access token lifetime is one hour.

² Calls, meetings, and chats in Teams don't support IP-based Conditional Access policies.

For more information about how to set up a Conditional Access policy, see [What is Conditional Access?](/entra/identity/conditional-access/overview).

## See also

- [Continuous access evaluation](/entra/identity/conditional-access/concept-continuous-access-evaluation)
- [Conditional Access documentation](/entra/identity/conditional-access/overview)
- [Microsoft Entra ID Protection documentation](/entra/id-protection/overview-identity-protection)
