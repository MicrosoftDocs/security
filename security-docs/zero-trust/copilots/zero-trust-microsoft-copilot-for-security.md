---
title: How do I apply Zero Trust principles to Microsoft Security Copilot?
description: How to apply Zero Trust principles to Microsoft Security Copilot. 
ms.date: 08/22/2025
ms.update-cycle: 180-days
ms.service: security
author: BrendaCarter
ms.author: bcarter
ms.subservice: zero-trust
ms.topic: concept-article
ms.collection:
- M365copilot
- msec-ai-copilot
- msftsolution-copilot
- msftsolution-scenario
- zerotrust-solution
- zerotrust-copilot
- trust-pod
ms.custom: sfi-ga-nochange
---

# Apply principles of Zero Trust to Microsoft Security Copilot

**Summary:** To apply Zero Trust principles to your environment for Microsoft Security Copilot, you need to apply five layers of protection:

1. Protect admin and SecOps staff user accounts with identity and access policies.
2. Apply least privilege access to admin and SecOps staff user accounts, including assigning the minimum user account roles.
3. Manage and protect admin and SecOps staff devices.
4. Deploy or validate your threat protection.
5. Secure access to third-party security products that you integrate with Security Copilot.

:::image type="content" source="../media/copilot/security-copilot-apply-zero-trust-steps.svg" alt-text="Diagram showing the four steps for applying Zero Trust principles to Microsoft Security Copilot." lightbox="../media/copilot/security-copilot-apply-zero-trust-steps.svg":::

## Introduction

As a part of introducing Microsoft Security Copilot into your environment, Microsoft recommends that you build a strong foundation of security for your admin and SecOps staff user accounts and devices. Microsoft also recommends ensuring you have configured threat protection tools. If you’re integrating third-party security products with Security Copilot, also ensure you’ve protected access to these products and related data.

Fortunately, guidance for a strong security foundation exists in the form of [Zero Trust](../zero-trust-overview.md). The Zero Trust security strategy treats each connection and resource request as though it originated from an uncontrolled network and a bad actor. Regardless of where the request originates or what resource it accesses, Zero Trust teaches us to "never trust, always verify."

From within security portals, Security Copilot provides a natural language, assistive copilot experience that helps support: 

- Security professionals in end-to-end scenarios such as incident response, threat hunting, intelligence gathering, and posture management.

- IT professionals in policy evaluation and configuration, device and user access troubleshooting, and performance monitoring.

Security Copilot uses data from event logs, alerts, incidents, and policies for your Microsoft and third-party subscriptions and security products. If an attacker compromises an admin or security staff user account that has been assigned a Security Copilot role, they can use Security Copilot and its results to understand how your SecOps team is addressing attacks in progress. An attacker can then use this information to thwart attempts to respond to an incident, possibly one that they initiated. 

Consequently, it’s critical to ensure that you’ve applied appropriate mitigations within your environment. 

## Logical architecture

The first line of defense when introducing Security Copilot is to apply the principles of Zero Trust to the accounts and devices of admin and SecOps staff. It’s also important to ensure your organization applies the principle of least privilege. In addition to [Copilot-specific roles](/security-copilot/authentication#copilot-for-security-roles), the assigned roles for admin and SecOps staff within your security tools determine what data they have access to while using Security Copilot. 

It’s easy to understand why these mitigations are important by looking at the logical architecture of Security Copilot shown here.

:::image type="content" source="../media/copilot/security-copilot-logical-architecture.svg" alt-text="Diagram of the logical architecture of Security Copilot showing users and devices, security products, and the Security Copilot service architecture." lightbox="../media/copilot/security-copilot-logical-architecture.svg":::
  
In the diagram:

- SecOps team members can prompt using a copilot experience, such as those offered by Security Copilot, Microsoft Defender XDR, and Microsoft Intune. 

- Security Copilot components include:

  - The Security Copilot service, which orchestrates responses to user and skill-based prompts.

  - A set of Large Language Models (LLMs) for Security Copilot.

  - Plugins for specific products. Preinstalled plugins for Microsoft products are provided. These plugins preprocess and post-process prompts. 

  - Your subscription data. The SecOps data for event logs, alerts, incidents, and policies stored in the subscriptions. For more information, see this [Microsoft Sentinel article](/security/operations/ingest-data-sources#before-you-begin) for the most common data sources for security products.

  - Files you upload. You can [upload specific files](/microsoft-copilot-service/content-sources-files) to Security Copilot and include these in the scope of prompts.

Each Microsoft security product with a copilot experience only provides access to the data set associated with that product, such as event logs, alerts, incidents, and policies. Security Copilot provides access to all the data sets to which the user has access.

For more information, see [Get started with Microsoft Security Copilot](/security-copilot/get-started-security-copilot).


### How does on-behalf-of authentication work with Security Copilot?

Security Copilot uses on-behalf-of (OBO) authentication provided by OAuth 2.0. This is an authentication flow provided by delegation in OAuth. When a SecOps user issues a prompt, Security Copilot passes the user’s identity and permissions through the request chain. This prevents the user gaining permission to resources for which they shouldn't have access.

For more information about OBO authentication, see [Microsoft identity platform and OAuth2.0 On-Behalf-Of flow](/entra/identity-platform/v2-oauth2-on-behalf-of-flow). 

### Prompting within a Microsoft security product: Embedded example for Microsoft Intune

When you use one of the embedded experiences of Security Copilot, the scope of the data is determined by the context of the product you're using. For example, if you issue a prompt within Microsoft Intune, the results are produced from data and context provided by Microsoft Intune only. 

Here's the logical architecture when issuing prompts from within the Microsoft Intune embedded experience.

:::image type="content" source="../media/copilot/security-copilot-architecture-intune-example.svg" alt-text="Diagram of the logical architecture for Security Copilot with Microsoft Intune highlighted as a security product, a plugin, and Intune data types." lightbox="../media/copilot/security-copilot-architecture-intune-example.svg":::

In the diagram:

- Intune admins use the Microsoft Copilot in Intune experience to submit prompts.
- The Security Copilot component orchestrates responses to the prompts using:

  - The LLMs for Security Copilot.

  - The Microsoft Intune preinstalled plugin.

  - The Intune data for devices, policies, and security posture stored in your Microsoft 365 subscription.

### Integrating with third-party security products

Security Copilot provides the ability to host plugins for third-party products. These third-party plugins provide access to their associated data. These plugins and their associated data live outside the Microsoft security trust boundary. Consequently, it’s important to ensure you’ve secured access to these applications and their associated data.

Here's the logical architecture of Security Copilot with third-party security products.

:::image type="content" source="../media/copilot/security-copilot-architecture-third-party.svg" alt-text="Diagram of the extended logical architecture for Security Copilot to support third-party security products." lightbox="../media/copilot/security-copilot-architecture-third-party.svg":::

In the diagram:

- Security Copilot integrates with third-party security products through plugins. 
- These plugins provide access to the data associated with the product, such as logs and alerts. 
- These third-party components reside outside the Microsoft security trust boundary.

### Applying security mitigations to your environment for Security Copilot

The rest of this article walks you through the steps to apply the principles of Zero Trust to prepare your environment for Security Copilot.

| Step | Task | Zero Trust principles applied |
| --- | --- | --- |
| 1 | Deploy or validate identity and access policies for admin and SecOps staff. | Verify explicitly |
| 2 | Apply least privilege to admin and SecOps user accounts. | Use least privileged access |
| 3 | Secure devices for privileged access. | Verify explicitly |
| 4 | Deploy or validate your threat protection services. | Assume breach |
| 5 | Secure access to third-party security products and data. | Verify explicitly <br><br> Use least privileged access <br><br> Assume breach |

There are several approaches you can take to onboarding admin and SecOps staff to Security Copilot while you configure protections for your environment.

### Per-user onboarding to Security Copilot

At a minimum, walk through a checklist for your admin and SecOps staff before you assign a role for Security Copilot. This works well for small teams and organizations that want to start with a test or pilot group. 

:::image type="content" source="../media/copilot/onboarding-user-checklist.svg" alt-text="Example of a checklist for onboarding your admin and SecOps staff  for Security Copilot." lightbox="../media/copilot/onboarding-user-checklist.svg":::
  
### Phased deployment of Security Copilot

For large environments, a more standard phased deployment works well. In this model, you address groups of users at the same time to configure protection and assign roles.

Here is an example model.

:::image type="content" source="../media/copilot/security-copilot-phased-deployment.svg" alt-text="Diagram of a standard phased deployment for Security Copilot, including Evaluate, Pilot, and Full Deployment phases." lightbox="../media/copilot/security-copilot-phased-deployment.svg":::

In the illustration:

- In the **Evaluate** phase, you pick a small set of admin and SecOps users that you want to have access to Security Copilot and apply identity and access and device protections.
- In the **Pilot** phase, you pick the next set of admin and SecOps users and apply identity and access and device protections.
- In the **Full deployment** phase, you apply identity and access and device protections for the rest of your admin and SecOps users.
- At the end of each phase, you assign the appropriate role in Security Copilot to the user accounts.

Because different organizations can be at various stages of deploying Zero Trust protections for their environment, in each of these steps:

- If you're NOT using any of the protections described in the step, take the time to pilot and deploy them to your admin and SecOps staff prior to assigning roles that include Security Copilot.
- If you're already using some of the protections described in the step, use the information in the step as a checklist and verify that each protection stated has been piloted and deployed prior to assigning roles that include Security Copilot.

## Step 1. Deploy or validate identity and access policies for admin and SecOps staff

To prevent bad actors from using Security Copilot to quickly get information on cyberattacks, the first step is to prevent them from gaining access. You must ensure that admin and SecOps staff:

- User accounts are required to use multifactor authentication (MFA) (so their access can't be compromised by guessing user passwords alone) and they're required to change their passwords when high-risk activity is detected.
- Devices must comply with Intune management and device compliance policies.

For identity and access policy recommendations, see the identity and access step in [Zero Trust for Microsoft 365 Copilot](zero-trust-microsoft-365-copilot.md#step-2-deploy-or-validate-your-identity-and-access-policies). Based on the recommendations in this article, ensure that your resulting configuration applies the following policies for all SecOps staff user accounts and their devices:

- [Always use MFA for sign-ins](/entra/identity/conditional-access/howto-conditional-access-policy-all-users-mfa)
- [Block clients that don’t support modern authentication](/entra/identity/conditional-access/howto-conditional-access-policy-block-legacy)
- [Require compliant PCs and mobile devices](/microsoft-365/security/office-365-security/zero-trust-identity-device-access-policies-common#device-compliance-policies)
- [High risk users must change password (for Microsoft 365 E5 only)](/microsoft-365/security/office-365-security/zero-trust-identity-device-access-policies-common#high-risk-users-must-change-password)
- [Require adherence to Intune device compliance policies](/microsoft-365/security/office-365-security/zero-trust-identity-device-access-policies-common#device-compliance-policies)

These recommendations align with the **Specialized security** protection level in Microsoft’s Zero Trust identity and device access policies. The following diagram illustrates the recommended three levels of protection: Starting point, Enterprise, and Specialized. The Enterprise protection level is recommended **as a minimum** for your privileged accounts.
  
:::image type="content" source="../media/copilot/identity-device-access-policies-common.svg" alt-text="Diagram of Zero Trust identity and device access policies showing the Starting Point, Enterprise, and Specialized Security protection levels." lightbox="../media/copilot/identity-device-access-policies-common.svg":::

In the diagram, the recommended policies for Microsoft Entra Conditional Access, Intune device compliance, and Intune app protection are illustrated for each of the three levels:

- **Starting point**, which doesn't require device management.
- **Enterprise** is recommended for Zero Trust and as a minimum for access to Security Copilot and your third-party security products and related data.
- **Specialized security** is recommended for access to Security Copilot and your third-party security products and related data.

Each of these policies is described in greater detail in [Common Zero Trust identity and device access policies for Microsoft 365 organizations](/microsoft-365/security/office-365-security/zero-trust-identity-device-access-policies-common). 

### Configure a separate set of policies for privileged users

When configuring these policies for your admin and SecOps staff, create a separate set of policies for these privileged users. For example, don’t add your admins to the same set of policies that govern access of unprivileged users to apps such as Microsoft 365 and Salesforce. Use a dedicated set of policies with protections that are appropriate for privileged accounts. 

### Include security tools in the scope of Conditional Access policies

For now, there's not an easy way to configure Conditional Access for Security Copilot. However, because on-behalf-of authentication is used to access data within security tools, be sure you have configured Conditional Access for these tools, which can include Microsoft Entra ID, Microsoft Intune, Microsoft Purview, Microsoft Defender XDR, and Microsoft Defender Threat Intelligence. 

Note that for Microsoft Defender for Cloud and Azure Firewall, the conditional access policy is applied to the Azure management portal and API. Consequently, any services or clients that depend on the Azure API can be indirectly affected. For more information, see [Conditional Access: Targeting resources](/entra/identity/conditional-access/concept-conditional-access-cloud-apps#windows-azure-service-management-api).

## Step 2. Apply least privilege to admin and SecOps user accounts

This step includes configuring the appropriate roles within Security Copilot. It also includes reviewing your admin and SecOps user accounts to ensure they are assigned the least amount of privileges for the work they're intended to do.

### Assign user accounts to Security Copilot roles

The permissions model for Security Copilot includes roles in both Microsoft Entra ID and Security Copilot.

| Product | Roles | Description |
| --- | --- | --- |
| Microsoft Entra ID / Microsoft Purview | [Microsoft Entra ID and Mirosoft Purview supported roles](/copilot/security/authentication#microsoft-entra-and-microsoft-purview-roles) | These Microsoft Entra and Microsoft Purview roles inherit the **Copilot owner** role in Security Copilot. Only use these privileged roles to onboard Security Copilot to your organization. |
| Security Copilot | Copilot owner <br><br> Copilot contributor | These two roles include access to use Security Copilot. Most of your admin and SecOps staff can use the **Copilot contributor** role. <br><br> The **Copilot owner** role includes the ability to publish custom plugins and to manage settings that affect all of Security Copilot. |

It’s important to know that, by default, *all users in the tenant are given Copilot contributor access*. With this configuration, access to your security tool data is governed by the permissions you configured for each of the security tools. An advantage of this configuration is that the embedded experiences of Security Copilot are immediately available to your admin and SecOps staff within the products they use daily. This works well if you’ve already adopted a strong practice of least privileged access within your organization. 

If you’d like to take a staged approach to introducing Security Copilot to your admin and SecOps staff while you tune up least privileged access in your organization, remove **All users** from the **Copilot contributor** role and add security groups as you're ready. 

For more information, see these Microsoft Security Copilot resources:

- [Get started](/security-copilot/get-started-security-copilot#onboarding-to-microsoft-security-copilot)
- [Understand authentication](/security-copilot/authentication)

### Configuring or reviewing least privilege access for admin and SecOps user accounts

Introducing Security Copilot is a great time to review the access of your admin and SecOps staff user accounts to be sure you're following through with the principle of least privilege for their access to specific products. This includes the following tasks:

- Review the privileges granted for the specific products your admin and SecOps staff work with. For example, for Microsoft Entra, see [Least privileged roles by task](/entra/identity/role-based-access-control/delegate-by-task).
- Use Microsoft Entra Privileged Identity Management (PIM) to gain greater control over access to Security Copilot.
- Use Microsoft Purview Privileged Access Management to configure granular access control over privileged admin tasks in Office 365. 

#### Using Microsoft Entra Privileged Identity Management together with Security Copilot

Microsoft Entra [Privileged Identity Management (PIM)](/entra/id-governance/privileged-identity-management/pim-configure) allows you to manage, control, and monitor the roles required to access Security Copilot. With PIM, you can:

- Provide role activation that is time-based.
- Require approval to activate privileged roles.
- Enforce MFA to activate any role.
- Get notifications when privileged roles are activated.
- [Conduct access reviews](/entra/id-governance/privileged-identity-management/pim-create-roles-and-resource-roles-review) to ensure admin and SecOps staff user accounts still need their assigned roles.
- [Perform audits](/entra/id-governance/privileged-identity-management/pim-how-to-use-audit-log) on access and role changes for admin and SecOps staff.

#### Using privileged access management together with Security Copilot

Microsoft Purview Privileged Access Management helps protect your organization from breaches and helps to meet compliance best practices by limiting standing access to sensitive data or access to critical configuration settings. Instead of administrators having constant access, just-in-time access rules are implemented for tasks that need elevated permissions. Instead of administrators having constant access, just-in-time access rules are implemented for tasks that need elevated permissions. For more information, see [Privileged access management](/purview/privileged-access-management-solution-overview).

## Step 3. Secure devices for privileged access

In Step 1, you configured Conditional Access policies that required managed and compliant devices for your admin and SecOps staff. For additional security, you can deploy privileged access devices for your staff to use when accessing security tools and data, including Security Copilot. A privileged access device is a hardened workstation that has clear application control and application guard. The workstation uses credential guard, device guard, app guard, and exploit guard to protect the host from attackers. 

For more information on how to configure a device for privileged access, see [Securing devices as part of the privileged access story](/security/privileged-access-workstations/privileged-access-devices).

To require these devices, be sure to update your Intune device compliance policy. If you're transitioning admin and SecOps staff to hardened devices, transition your security groups from the original device compliance policy to the new policy. The Conditional Access rule can remain the same.

## Step 4. Deploy or validate your threat protection services

To detect the activities of bad actors and keep them from gaining access to Security Copilot, ensure that you can detect and respond to security incidents with a comprehensive suite of threat protection services, which include Microsoft Defender XDR with Microsoft 365, Microsoft Sentinel, and other security services and products. 

Use the following resources.

| Scope | Description and resources |
| --- | --- |
| Microsoft 365 and SaaS apps integrated with Microsoft Entra | See the [Zero Trust for Microsoft 365 Copilot](zero-trust-microsoft-365-copilot.md#step-5-deploy-or-validate-your-threat-protection-services) article for guidance on how to ramp up threat protection beginning with Microsoft 365 E3 plans and progressing with Microsoft E5 plans. <br><br> For Microsoft 365 E5 plans, also see [Evaluate and pilot Microsoft Defender XDR security](/microsoft-365/security/defender/eval-overview). |
| Your Azure cloud resources <br><br> Your resources in other cloud providers, such as Amazon Web Services (AWS) | Use the following resources to get started with Defender for Cloud: <br><br> - [Microsoft Defender for Cloud](/azure/defender-for-cloud/defender-for-cloud-introduction) <br> - [Apply Zero Trust principles to IaaS applications in AWS](../secure-iaas-apps.md) |
| Your digital estate with all Microsoft XDR tools and Microsoft Sentinel | The [Implement Microsoft Sentinel and Microsoft Defender XDR for Zero Trust](/security/operations/siem-xdr-overview) solution guide walks through the process of setting up Microsoft eXtended detection and response (XDR) tools together with Microsoft Sentinel to accelerate your organization’s ability to respond to and remediate cybersecurity attacks. |

## Step 5. Secure access to third-party security products and data

If you’re integrating third-party security products with Security Copilot, be sure you have secured access to these products and related data. Microsoft Zero Trust guidance includes recommendations for securing access to SaaS apps. These recommendations can be used for your third-party security products.

For protection with identity and device access policies, changes to common policies for SaaS apps are outlined in red in the following diagram. These are the policies to which you can add your third-party security products.

:::image type="content" source="../media/copilot/identity-device-access-policies-saas-apps.svg" alt-text="Diagram of Zero Trust identity and device access policies and the highlighted changes to protection levels for SaaS apps." lightbox="../media/copilot/identity-device-access-policies-saas-apps.svg":::
 
For your third-party security products and apps, consider creating a dedicated set of policies for these. This allows you to treat your security products with greater requirements compared to productivity apps, like Dropbox and Salesforce. For example, add Tanium and all other third-party security products to the same set of Conditional Access policies. If you want to enforce stricter requirements for devices for your admin and SecOps staff, also configure unique policies for Intune device compliance and Intune app protection and assign these policies to your admin and SecOps staff.

For more information about adding your security products to Microsoft Entra ID and to the scope of your Conditional Access and related policies (or configuring a new set of policies), see [Add SaaS apps to Microsoft Entra ID and to the scope of policies](../add-saas-apps.md).

Depending on the security product, it might be appropriate to use Microsoft Defender for Cloud Apps to monitor the use of these apps and apply session controls. Additionally, if these security apps include storage of data in any of the file types supported by Microsoft Purview, you can use Defender for Cloud to monitor and protect this data using sensitivity labels and data loss prevention (DLP) policies. For more information, see [Integrate SaaS apps for Zero Trust with Microsoft 365](../integrate-saas-apps.md).

### Example for Tanium SSO

Tanium is a provider of endpoint management tools and offers a custom Tanium Skills plugin for Security Copilot. This plugin helps ground prompts and responses that leverage Tanium-gathered information and insights. 
 
Here's the logical architecture of Security Copilot with the Tanium Skills plugin.

:::image type="content" source="../media/copilot/security-copilot-architecture-tanium-example.svg" alt-text="Diagram of the logical architecture for Security Copilot with Tanium SSO highlighted as a third-party plugin and with Tanium third-party data." lightbox="../media/copilot/security-copilot-architecture-tanium-example.svg":::

In the diagram:

- Tanium Skills is a custom plugin for Microsoft Security Copilot.
- Tanium Skills provides access to and helps ground both prompts and responses that use Tanium-gathered information and insights.

To secure access to Tanium products and related data:

1. Use the Microsoft Entra ID Application Gallery to find and add Tanium SSO to your tenant. See [Add an enterprise application](/entra/identity/enterprise-apps/add-application-portal#add-an-enterprise-application). For a Tanium-specific example, see [Microsoft Entra SSO integration with Tanium SSO](/entra/identity/saas-apps/tanium-sso-tutorial).
2. Add Tanium SSO to the scope of your Zero Trust identity and access policies. 


## Next steps

Watch the [Discover Microsoft Security Copilot video](https://www.youtube.com/watch?v=5pPYBM0X4_U). 

See these additional articles for Zero Trust and Microsoft's Copilots:

- [Overview](apply-zero-trust-copilots-overview.md)
- [Microsoft Copilot](zero-trust-microsoft-copilot.md)
- [Microsoft 365 Copilot](zero-trust-microsoft-365-copilot.md)

Also see the [Microsoft Security Copilot documentation](/security-copilot/).

## References

Refer to these links to learn about the various services and technologies mentioned in this article.

- [Get started with Microsoft Security Copilot](/security-copilot/get-started-security-copilot)
- [Onboarding to Security Copilot](/security-copilot/get-started-security-copilot##onboarding-to-copilot-for-security)
- [Data sources for Microsoft Sentinel](/security/operations/ingest-data-sources#before-you-begin)
- [Microsoft Entra Privileged Identity Management (PIM)](/entra/id-governance/privileged-identity-management/pim-configure)
- [Privileged access management](/purview/privileged-access-management-solution-overview)
- [Privileged access devices](/security/privileged-access-workstations/privileged-access-devices)
