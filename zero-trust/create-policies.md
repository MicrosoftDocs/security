---
title: Create Defender for Cloud App policies
description: 
ms.date: 04/15/2022
ms.service: security
author: mjcaparas
ms.author: macapara
ms.topic: conceptual
---

# Step 2: Create Defender for Cloud App policies

Apps form an integral part of many organizations. Many employees use apps to tackle tasks more efficiently. However, some of these apps are unsanctioned and can cause significant damage to an organization when not discovered and managed properly. 

It's important to have visibility into the apps that are being used in your organization so that you can properly manage and protect important resources.

This article provides guidance on how to:

- Discover apps
- Sanction cloud apps
- Configure Conditional Access App Control
- Using app connectors
- Apply session controls


Microsoft Defender for Cloud Apps keeps you in control through comprehensive visibility, auditing, and granular controls over your sensitive data.

Defender for Cloud Apps has tools that help uncover shadow IT and assess risk while enabling you to enforce policies and investigate activities. It helps you control access in real time and stop threats so your organization can more safely move to the cloud.



## Discover cloud apps
Without visibility into the apps being used in your organization, you will not be able to properly manage and control how users use and access important resources with them.  


Defender for Cloud Apps has a capability called Cloud Discovery which analyzes your traffic logs against the Microsoft Defender for Cloud Apps catalog of over 25,000 cloud apps. The apps are ranked and scored based on more than 90 risk factors to provide you with ongoing visibility into cloud use, Shadow IT, and the risk Shadow IT poses into your organization. 


:::image type="content" source="media/m365-defender-mcas-architecture-b.png" alt-text="Image of Microsoft 365 Defender and cloud apps":::


Use the following guidance to leverage the built-in capabilities in Defender for Cloud Apps to discover apps in your organization:

- [Set up Cloud Discovery](/defender-cloud-apps/set-up-cloud-discovery)
- [Discover and identify Shadow IT](/defender-cloud-apps/tutorial-shadow-it#phase-1-discover-and-identify-shadow-it)


## Sanction apps

After you've reviewed the list of discovered apps in your environment,you can secure your environment by
approving safe apps (Sanctioned) or prohibiting unwanted apps (Unsanctioned).






For more information, see [Sanctioning/unsanctioning an app](/defender-cloud-apps/governance-discovery#BKMK_SanctionApp).



Now that you've discovered the apps being used in your organization, you'll need to connect them to Azure AD to get visibility and protection. 


## Configure Conditional Access App Control to protect apps

In the previous step [Step 1: Add SaaS apps to Azure Active Directory and to the scope of policies ](add-saas-apps.md), conditional access was described as policies that allow administrators to assign controls to specific applications, actions, or authentication context. You have the ability to define which users or user groups can access the cloud apps, which cloud apps users can access, and which locations and networks a user has access to using conditional access policy.

In conjunction with conditional access policies, you can further augment the security of cloud apps by applying access and session controls using Conditional Access App Control.

Conditional Access App Control enables user app access and sessions to be monitored and controlled in real time based on access and session policies. Access and session policies are used within the Defender for Cloud Apps portal to further refine filters and set actions to be taken on a user.


To summarize, conditional access dictates the requirements that must be fulfilled before a user can access apps. Conditional Access App Control dictates what apps a user can access and the set of actions that a user can take during a session **after** they've been granted access. 


## Use app connectors

App connectors use the APIs of app providers to enable greater visibility and control by Microsoft Defender for Cloud Apps over the apps you connect to.

Depending on the app to which you're connecting, API connection enables the following items:

- **Account information** - Visibility into users, accounts, profile information, status (suspended, active, disabled) groups, and privileges.
- **Audit trail** - Visibility into user activities, admin activities, sign-in activities.
- **Account governance** - Ability to suspend users, revoke passwords, etc.
- **App permissions** - Visibility into issued tokens and their permissions.
- **App permission governance** - Ability to remove tokens.
- **Data scan** - Scanning of unstructured data using two processes -periodically (every 12 hours) and in real-time scan (triggered each time a change is detected).
- **Data governance** - Ability to quarantine files, including files in trash, and overwrite files.

For more information, see [Connect apps](/defender-cloud-apps/enable-instant-visibility-protection-and-governance-actions-for-your-apps).



## Apply session contols


**ADD / EXPOUND WITH CLEARER ARCHITECTURE ILLUSTRATION FROM BRENDA HERE**


Use the following references for more information:
-  [Protect apps with Microsoft Defender for Cloud Apps Conditional Access App Control](/defender-cloud-apps/proxy-intro-aad).
- [Integrating Azure AD with Conditional Access App Control](/microsoft-365/security/defender/eval-defender-mcas-architecture#integrating-with-azure-ad-with-conditional-access-app-control)


## Next step

:::image type="content" source="media/saas-zt-step-3.png" alt-text="Image of Zero Trust SaaS guidance with step 3 highlighted":::

Continue with [Step 3](deploy-information-protection-saas.md) to deploy information protection for SaaS apps.
