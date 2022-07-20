---
title: Add SaaS apps to Azure Active Directory and to the scope of policies 
description: Learn steps to add SaaS apps to Azure AD and to the scope of identity and device policies
ms.date: 04/15/2022
ms.service: security
author: mjcaparas
ms.author: macapara
ms.topic: conceptual
---

# Step 1: Add SaaS apps to Azure Active Directory and to the scope of policies 

Many organizations rely on SaaS apps to run business workflows. The ease of use, cost effectiveness, and scalability makes it a viable solution for organizations to adopt. Because of the amount information and access to valuable resources these apps have, proper measures must be in place to secure these business-critical apps.


Add apps in Azure Active Directory (Azure AD) so that you can monitor and configure access for applications in the cloud. Azure AD has an application gallery which is a collection of SaaS apps that have been pre-integrated with Azure AD. You can also choose to add your own custom apps. 


After adding apps to Azure AD, you can configure how apps are accessed by including them in the scope of your Zero Trust identity and device access policies. 

If you already have Defender for Cloud Apps deployed, you can discover SaaS apps that are being used in your organization. For more information, see [Discover and manage shadow IT in your network](/defender-cloud-apps/tutorial-shadow-it).


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



## Add to the scope of your Zero Trust identity and device access policies
After adding apps in Azure AD, you'll need to add them to the scope your identity and device access policies. 

Conditional access policies allow administrators to assign controls to specific applications, actions, or authentication context. You can define conditions such as what device type can access a resource, user risk levels, trusted locations, as well as other conditions. Multifactor authentication (MFA) is also part of these policies. 

MFA helps safeguard access to data and applications, by providing additional security by requiring a second form of verification and delivers strong authentication. 


:::image type="content" source="media/identity-access-ruleset-saas.png" alt-text="The summary of policy updates for the protection of access to SaaS apps" lightbox="media/identity-access-ruleset-saas.png":::

### Updating common policies 
The following diagram illustrates which policies to update from the common identity and device access policies for SaaS apps.

For each policy to update, make sure that apps and dependent services are included in the assignment of cloud apps.

This table lists the policies that need to be revisited and links to each policy in the [common identity and device access policies](/microsoft-365/security/office-365-securityidentity-access-policies).

|Protection level|Policies|Further information|
|---|---|---|
|**Starting point**|[Require MFA when sign-in risk is *medium* or *high*](/microsoft-365/security/office-365-security/identity-access-policies#require-mfa-based-on-sign-in-risk)|Be sure apps and dependent services are included in the list of apps. |
||[Block clients that don't support modern authentication](/microsoft-365/security/office-365-security/identity-access-policies#block-clients-that-dont-support-multi-factor)|Include apps and dependent services in the assignment of cloud apps.|
||[High risk users must change password](/microsoft-365/security/office-365-security/identity-access-policies#high-risk-users-must-change-password)|Forces app users to change their password when signing in if high-risk activity is detected for their account. |
||[Apply APP data protection policies](/microsoft-365/security/office-365-security/identity-access-policies#apply-app-data-protection-policies)|Be sure apps and dependent services are included in the list of apps. Update the policy for each platform (iOS, Android, Windows).|
|**Enterprise**|[Require MFA when sign-in risk is *low*, *medium* or *high*](/microsoft-365/security/office-365-security/identity-access-policies#require-mfa-based-on-sign-in-risk)| Include apps and dependent services in this policy.|
||[Require compliant PCs *and* mobile devices](/microsoft-365/security/office-365-security/identity-access-policies#require-compliant-pcs-and-mobile-devices)|Include apps and dependent services in this policy.|
|**Specialized security**|[*Always* require MFA](/microsoft-365/security/office-365-security/identity-access-policies#require-mfa-based-on-sign-in-risk)|Regardless of user identity, MFA will be used by your organization.  |

For more information, see [Recommended Microsoft Defender for Cloud Apps policies for SaaS apps](/microsoft-365/security/office-365-security/mcas-saas-access-policies). 

## Next step

:::image type="content" source="media/saas-zt-steps-2.png" alt-text="Image of Zero Trust SaaS guidance with step 2 highlighted":::

Continue with [Step 2](create-policies.md) to create Defender for Cloud Apps policies.