---
title: Add SaaS apps to Azure Active Directory and apply access policies
description: 
ms.date: 04/15/2022
ms.service: security
author: mjcaparas
ms.author: macapara
ms.topic: conceptual
---

# Step 1: Add SaaS apps to Azure Active Directory and apply access policies



Many organizations rely on SaaS apps to run business workflows. Its ease of use, cost effectiveness, and scalability makes it easy for organizations to adopt the use of SaaS apps. Because of the amount information and access to valuable resources, proper measures must be in place to secure these business-critical apps.

:::image type="content" source="media/step-1-add-saas-apps.png" alt-text="Overview image of adding SaaS apps to Azure AD and adding access policies":::

Add apps in Azure Active Directory (Azure AD) so that you can monitor and configure access for applications in the cloud. Azure Active Directory also includes an application gallery which is a collection of SaaS apps that have been pre-integrated with Azure AD. 


After adding apps to Azure AD, you can configure how apps are accessed by including them in the scope of your multifactor authentication (MFA) and conditional access policies. 



## Adding apps in Azure AD
Azure AD has comprehensive security built in to help you manage SaaS apps. There are several ways to manage apps in Azure AD. The easiest way to start managing an application is to the pre-integrated application from the Azure AD gallery.

For more information, see [Add an enterprise application](/azure/active-directory/manage-apps/add-application-portal#add-an-enterprise-application) and [Overview of Azure Active Directory application gallery](/azure/active-directory/manage-apps/overview-application-gallery).


## Adding custom apps in Azure AD app gallery
You can develop your own application and register it in Azure AD. Registering it with Azure AD lets you leverage the security features that the tenant provides. You can register your application in **App Registrations**, or you can register it
using the **Create your own application** link when adding a new application in **Enterprise applications**.


For more information, see  [Request to publish your application in the Azure Active Directory application gallery](/azure/active-directory/manage-apps/v2-howto-app-gallery-listing).



## Applyingm multifactor authentication and conditional access
Azure AD multifactor authentication (MFA) helps safeguard access to data and applications, providing another layer of security by using a second form of authentication.It provides additional security by requiring a second form of verification and delivers strong authentication. There are many methods that can be used for a second-factor authentication.

For more information, see [Manage application access and security](/azure/active-directory/manage-apps/tutorial-manage-access-security#create-a-conditional-access-policy).


## Next step

:::image type="content" source="media/saas-zt-step-2.png" alt-text="Image of Zero Trust SaaS guidance with step 2 highlighted":::

Continue with [Step 2](create-policies.md) to create Defender for Cloud Apps policies.