# Privileged Access Management solutions DRAFT

Privileged Access Management (PAM) solutions are built to control who has access to elevated permissions in an organization's data and infrastructure. PAM solutions are key to implementing a Zero Trust model. They improving an organizations security posture by:

- Automating control over who can access privileged data and resources.
- Supporting least-privilege policies, which reduce risk by giving users the smallest scope of access necessary to do their job.
- Allowing companies to monitor access and audit and enforce compliance.

PAM solutions are historically built around on-premises access management. This article explains how to extend these solutions by integrating them with Azure Active Directory.

# Solution Overview

Traditionally, PAM solutions were built around an on-premises setup to control access within a secure network. Now, apps are moving into the cloud and employees are working from a variety of locations and devices. In this new world, cloud-based identity services are used as the control plane for managing access.

There are many possible integrations for PAM solutions with Azure Active Directory (Azure AD). In this article we'll recommend some of the most common and useful integrations that will add value to your PAM solutions.

# Key integrations

This section outlines the key pieces we recommend for integrating a PAM solution with Azure Active Directory.

## Publish your app to the Azure AD app gallery

Whether you are adding functionality to an existing application or creating a new solution, you should make sure that your application is published to the Azure AD app gallery.

The Azure AD app gallery is a trusted source of Azure AD compatible applications for IT admins. Applications listed there have been validated to be compatible with Azure AD, and IT admins can easily integrate the solution in the gallery into their tenant with automated app registration.

When you publish your app in the app gallery this will increase customer trust, which is key for solutions that customers rely on to keep their data and resources secure. You can become a [verified publisher](https://docs.microsoft.com/azure/active-directory/develop/publisher-verification-overview) so that customers know you are the trusted publisher of the app.

## Integrate user provisioning

Synchronizing information about users and access between your application and Azure AD is essential. The management of identities and access for large organizations with thousands or hundreds of thousands of users can be very difficult to maintain. Once you have automated synchronization, you can effectively scale your identity management systems on both cloud-only and hybrid environments as customers increase their dependence on Azure AD.

SCIM (System for Cross-Domain Identity Management) is an open standard for exchanging user identity information. You can use the SCIM user management API to automatically provision users and groups between your application and Azure AD.

Our tutorial on the subject, [Tutorial - Develop a SCIM endpoint for user provisioning to apps from Azure AD | Microsoft Docs](https://docs.microsoft.com/azure/active-directory/app-provisioning/use-scim-to-provision-users-and-groups), describes how to build a SCIM endpoint and integrate with the Azure AD provisioning service. The SCIM specification provides a common user schema for provisioning. When used in conjunction with federation standards like SAML or OpenID Connect, SCIM gives administrators an end-to-end, standards-based solution for access management.

## Integrate access packages

Azure AD's [entitlement management](https://docs.microsoft.com/azure/active-directory/governance/entitlement-management-overview) is a governance feature that enables organizations to manage identity and access lifecycle at scale, by automating access request workflows, access assignments, reviews, and expiration.

One of the key features of entitlement management is access packages. An access package is a bundle of all the resources with the access a user needs to work on a project or perform their task. Access packages are used to govern access for your internal employees, and users outside your organization.

Here, you will want to synchronize your solution with the access packages that are being used in Azure AD. In this way, your PAM solution can keep track of the permissions that have been given to users in access packages and can add additional features above what would be available just using Azure AD. In the other direction, roles and permissions that are granted with your own solution can be reflected in the access packages that are delivered to users.

We have guidance on programmatically interacting with Azure AD's entitlement management here: [Tutorial: Manage access to resources in Active Directory entitlement management using Microsoft Graph APIs - Microsoft Graph | Microsoft Docs](https://docs.microsoft.com/graph/tutorial-access-package-api?toc=/azure/active-directory/governance/toc.json&amp;bc=/azure/active-directory/governance/breadcrumb/toc.json).

## Integrate with Privileged Identity Management

[Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/privileged-identity-management/pim-configure) is a service in Azure Active Directory (Azure AD) that enables you to manage, control, and monitor access to important resources in your organization. These resources include resources in Azure AD, Azure, and other Microsoft Online Services such as Microsoft 365 or Microsoft Intune.

Azure AD PIM is a great option as a cloud-native privileged access solution for cloud-based scenarios that complement the features your PAM solution offers. For example, a customer may choose to control access to non-sensitive data using Azure AD's PIM, but to take advantage of advanced tools from a PAM solution for sensitive data access. In this case, your tool can integrate with PIM, and display the access from both PIM and PAM in one place that is convenient to the users.

Guidance: [Microsoft Graph APIs for PIM (Preview) - Azure AD | Microsoft Docs](https://docs.microsoft.com/azure/active-directory/privileged-identity-management/pim-apis)

## Integrate with Azure AD Conditional Access

[Conditional Access](https://docs.microsoft.com/azure/active-directory/conditional-access/overview) is a key offering from Azure Active Directory. Conditional Access policies allow organizations to apply the right access controls when needed to stay secure, for example by blocking risky sign-ins.

PAM solutions can use the Microsoft Graph API to configure conditional access policies for users. For example, to enforce strong authentication for users who may be risky. For more, check out this sample on GitHub [Configure Conditional Access policies using the Microsoft Graph API](https://github.com/Azure-Samples/azure-ad-conditional-access-apis/tree/main/01-configure/graphapi).

Another great example if terms of use. You can leverage Azure AD terms of use API to provide a simple method that organizations can use to present information to end users. This presentation ensures users see relevant disclaimers for legal or compliance requirements.

[https://docs.microsoft.com/azure/active-directory/conditional-access/terms-of-use](https://docs.microsoft.com/azure/active-directory/conditional-access/terms-of-use)

[https://docs.microsoft.com/graph/api/resources/agreement?view=graph-rest-1.0](https://docs.microsoft.com/graph/api/resources/agreement?view=graph-rest-1.0)

# Partners

- foo
- bar
- baz