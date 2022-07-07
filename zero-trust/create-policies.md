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


Microsoft Defender for Cloud Apps keeps you in control through comprehensive visibility, auditing, and granular controls over your sensitive data.

Defender for Cloud Apps has tools that help uncover shadow IT and assess risk while enabling you to enforce policies and investigate activities. It helps you control access in real time and stop threats so your organization can more safely move to the cloud.


## Discover cloud apps
Without visibility into the apps being used in your organization, you will not be able to properly manage and control how users use and access important resources with them.  


Defender for Cloud Apps has a capability called Cloud Discovery which analyzes your traffic logs against the Microsoft Defender for Cloud Apps catalog of over 25,000 cloud apps. The apps are ranked and scored based on more than 90 risk factors to provide you with ongoing visibility into cloud use, Shadow IT, and the risk Shadow IT poses into your organization. 


Use the following guidance to leverage the built-in capabilities in Defender for Cloud Apps to discover apps in your organization:

- [Set up Cloud Discovery](/defender-cloud-apps/set-up-cloud-discovery)
- [Discover and identify Shadow IT](/defender-cloud-apps/tutorial-shadow-it#phase-1-discover-and-identify-shadow-it)





## Connect apps

Now that you've discovered apps, you'll need to connect them to Azure Active Directory (Azure AD).






## Use Conditional Access App Control to protect apps

In the previous step [Step 1: Add SaaS apps to Azure Active Directory and to the scope of policies ](add-saas-apps.md), conditional access was described as policies that allow administrators to assign controls to specific applications, actions, or authentication context. You have the ability to define where a conditional access policy is applied to: 

- Who - Which users or user groups can access the cloud apps
- What - Which cloud apps users can access
- Where - Which locations and networks a user can access

In conjunction with conditional access policies, you can further augment the security of cloud apps by applying access and session controls using Conditional Access App Control.

Conditional Access App Control enables user app access and sessions to be monitored and controlled in real time based on access and session policies. Access and session policies are used within the Defender for Cloud Apps portal to further refine filters and set actions to be taken on a user.


To summarize, conditional access dictates the conditions for when a user can access a certain resource. Conditional Access App Control dictates what a user can access and the set of actions that a user can take during a session **after** they've been granted access. 


For more information , see [Protect apps with Microsoft Defender for Cloud Apps Conditional Access App Control](/defender-cloud-apps/proxy-intro-aad).



## Next step

:::image type="content" source="media/saas-zt-step-2.png" alt-text="Image of Zero Trust SaaS guidance with step 2 highlighted":::

Continue with [Step 3](create-policies.md) to create Defender for Cloud Apps policies.
