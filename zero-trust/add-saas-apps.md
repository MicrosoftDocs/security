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

Many organizations rely on SaaS apps to run business workflows. The ease of use, cost effectiveness, and scalability makes it a viable solution for organizations to adopt. Because of the amount information and access to valuable resources, proper measures must be in place to secure these business-critical apps.

:::image type="content" source="media/step-1-add-saas-apps.png" alt-text="Overview image of adding SaaS apps to Azure AD and adding access policies":::

Add apps in Azure Active Directory (Azure AD) so that you can monitor and configure access for applications in the cloud. Azure Active Directory has an application gallery which is a collection of SaaS apps that have been pre-integrated with Azure AD. You can also choose to add your own custom apps. 


After adding apps to Azure AD, you can configure how apps are accessed by including them in the scope of your multifactor authentication (MFA) and conditional access policies. 

If you already have Defender for Cloud Apps deployed, you can discover SaaS apps that your organization is using by using this tool. 


## Adding apps in Azure AD

Adding apps in Azure AD helps you leverage one or more of the services it provides including:

* Application authentication and authorization
* User authentication and authorization
* SSO using federation or password
* User provisioning and synchronization
* Role-based access control - Use the directory to define application roles to perform role-based authorization checks in an application
* OAuth authorization services - Used by Microsoft 365 and other Microsoft applications to authorize access to APIs/resources
* Application publishing and proxy - Publish an application from a private network to the internet
* Directory schema extension attributes to store additional data in Azure AD 


There are several ways you can add apps in Azure AD. The easiest way to start managing apps is to use the application gallery. You also have the option of adding custom apps. This section will guide you through both ways. 


### Add apps from the application gallery

Azure AD has an application gallery that contains a collection of SaaS apps that have been pre-integrated with Azure AD. All you need to do is sign into Azure Active Directory and choose from applications from specific cloud platforms, featured applications, or you search for the application that you want to use.


For more information, see [Add an enterprise application](/azure/active-directory/manage-apps/add-application-portal#add-an-enterprise-application) and [Overview of Azure Active Directory application gallery](/azure/active-directory/manage-apps/overview-application-gallery).


### Adding custom apps in Azure AD app gallery
You can develop your own application and register it in Azure AD. Registering it with Azure AD lets you leverage the security features that the tenant provides. You can register your application in **App Registrations**, or you can register it using the **Create your own application** link when adding a new application in **Enterprise applications**.


For more information, see  [Request to publish your application in the Azure Active Directory application gallery](/azure/active-directory/manage-apps/v2-howto-app-gallery-listing).



## Applying access policies on apps
Azure AD multifactor authentication (MFA) helps safeguard access to data and applications, providing another layer of security by using a second form of authentication. It provides additional security by requiring a second form of verification and delivers strong authentication. There are many methods that can be used for a second-factor authentication.


Conditional access policies allow administrators to assign controls to specific applications, actions, or authentication context.

For more information, see [Manage application access and security](/azure/active-directory/manage-apps/tutorial-manage-access-security#create-a-conditional-access-policy).


## Next step

:::image type="content" source="media/saas-zt-step-2.png" alt-text="Image of Zero Trust SaaS guidance with step 2 highlighted":::

Continue with [Step 2](create-policies.md) to create Defender for Cloud Apps policies.