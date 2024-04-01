---
title: Apply principles of Zero Trust to Microsoft Copilot for Security
description: Learn how to secure Microsoft Copilot for Security with Zero Trust principles. 
ms.date: 11/01/2023
ms.service: security
author: bcarter
ms.author: bcarter
ms.topic: conceptual
ms.collection: 
  - M365copilot 
  - msftsolution-copilot
  - msftsolution-scenario
  - zerotrust-solution
  - zerotrust-azure
---

# Apply principles of Zero Trust to Microsoft Copilot for Security

Before you introduce Microsoft Copilot for Microsoft 365 or Copilot into your environment, Microsoft recommends that you build a strong foundation of security. Fortunately, guidance for a strong security foundation exists in the form of [Zero Trust](zero-trust-overview.md). The Zero Trust security strategy treats each connection and resource request as though it originated from an uncontrolled network and a bad actor. Regardless of where the request originates or what resource it accesses, Zero Trust teaches us to "never trust, always verify."

This article provides steps to apply the [principles of Zero Trust](zero-trust-overview.md) security to prepare your environment for Copilot in the following ways:

| Zero Trust principle | Definition | Met by |
| --- | --- | --- |
| Verify explicitly | Always authenticate and authorize based on all available data points. | Enforce the validation of user credentials, device requirements, and app permissions and behaviors. |
| Use least privileged access |  Limit user access with Just-In-Time and Just-Enough-Access (JIT/JEA), risk-based adaptive policies, and data protection. | Validate JEA across your organization to eliminate oversharing by ensuring that correct permissions are assigned to files, folders, Teams, and email. Use sensitivity labels and data loss prevention policies to protect data.  |
| Assume breach | Minimize blast radius and segment access. Verify end-to-end encryption and use analytics to get visibility, drive threat detection, and improve defenses. | Use Exchange Online Protection (EOP) and Microsoft Defender XDR services to automatically prevent common attacks and to detect and respond to security incidents. |

For the basics of Copilot, see the [overview](/microsoft-365-copilot/microsoft-365-copilot-overview) and [how to get started](/microsoft-365-copilot/microsoft-365-copilot-setup).

-------------------

As a part of introducing Microsoft Copilot for Security into your environment, Microsoft recommends that you build a strong foundation of security for your SecOps staff user accounts and devices. Microsoft also recommends ensuring you have configured threat protection tools. If you’re integrating third-party security products with Copilot for Security, also ensure you’ve protected access to these products and related data.

Fortunately, guidance for a strong security foundation exists in the form of Zero Trust. The Zero Trust security strategy treats each connection and resource request as though it originated from an uncontrolled network and a bad actor. Regardless of where the request originates or what resource it accesses, Zero Trust teaches us to "never trust, always verify."

From within security portals, Copilot for Security provides a natural language, assistive copilot experience that helps support security professionals in end-to-end scenarios such as incident response, threat hunting, intelligence gathering, and posture management.

Copilot for Security uses data from event logs, alerts, incidents, and policies for your Microsoft and third-party subscriptions and security products. If an attacker compromises a security staff user account that has been assigned a Copilot for Security role, they can use Copilot for Security and its results to understand how the SecOps team is addressing attacks in progress. An attacker can then use this information to thwart attempts to respond to an incident, possibly one that they initiated. Consequently, it’s critical to ensure that you’ve applied appropriate mitigations within your environment. 

## Logical architecture

The first line of defense when introducing Copilot for Security is to apply the principles of Zero Trust to admin and SecOps staff — both their accounts and devices. It’s also important to ensure your organization applies the principle of least privilege. In addition to Copilot-specific roles, the assigned roles for admins and your SecOps staff within your security tools determine what data they have access to while using Copilot for Security. 

It’s easy to understand why these mitigations are important by looking at the logical architecture of Copilot for Security, illustrated below.

:::image type="content" source="media/copilot/security-copilot-logical-architecture.svg" alt-text="Diagram of desc." lightbox="media/copilot/security-copilot-logical-architecture.svg":::
  
In the diagram:

- SecOps team members can prompt using one of the copilot experiences – Copilot for Security, Microsoft Defender XDR, Microsoft Intune, etc. 
- Copilot for Security components include:

  - The Copilot for Security service, which orchestrates responses to user prompts.

  - A set of Large Language Models (LLMs) for Copilot for Security.

  - Plugins for specific products — Preinstalled plugins for Microsoft products are provided. These plugins pre-process and post-process prompts. 

  - Your subscription data — The SecOps data for event logs, alerts, incidents, and policies stored in the subscriptions. For more information, this Microsoft Sentinel article lists the most common data sources for security products.

  - Files you upload — you can upload specific files to Copilot for Security and include these in the scope of prompts.

Each Microsoft security product with a Copilot experience only provides access to the data set associated with that product (event logs, alerts, incidents, and policies). Copilot for Security provides access to all the data sets the user has access to.

See Get started with Microsoft Copilot for Security for more information.


### How does on-behalf-of (OBO) authentication work with Copilot for Security?

Copilot for Security uses on-behalf-of authentication provided by OAuth 2.0. This is an authentication flow provided by delegation in OAuth. When a SecOps user issues a prompt, Copilot for Security passes the user’s identity and permissions through the request chain. This prevents the user gaining permission to resources they shouldn't have access to.

For more information about on-behalf-of authentication, see Microsoft identity platform and OAuth2.0 On-Behalf-Of flow. 

### Prompting within a Microsoft security product — Embedded example for Microsoft Intune

When using one of the embedded experiences of Copilot for Security, the scope of the data is determined by the context of the product you are using. For example, if you prompt within Microsoft Intune, the results are produced from data and context provided by Microsoft Intune only. 
Here is the logical architecture when issuing prompts from within the Microsoft Intune embedded experience.

:::image type="content" source="media/copilot/security-copilot-architecture-intune-example.svg" alt-text="Diagram of desc." lightbox="media/copilot/security-copilot-architecture-intune-example.svg":::

In the diagram:

- Intune admins use the Microsoft Copilot in Intune experience to submit prompts.
- The Microsoft Copilot for Security component orchestrates responses to the prompts using the:

  - LLMs for Copilot for Security

  - The Microsoft Intune preinstalled plugin

  - The Intune data for devices, policies, and security posture stored in your Microsoft 365 subscription

### Integrating with third-party security products

Copilot for Security provides the ability to host plugins for third-party products. These third-party plugins provide access to the associated data. These plugins and the associated data live outside the Microsoft security trust boundary. Consequently, it’s important to ensure you’ve secured access to these applications and associated data.

:::image type="content" source="media/copilot/security-copilot-architecture-third-party.svg" alt-text="Diagram of desc." lightbox="media/copilot/security-copilot-architecture-third-party.svg":::

In the illustration:

- Copilot for Security integrates with third-party security products through plugins. 
- These plugins provide access to the data associated with the product, such as logs and alerts. 
- These third-party components reside outside the Microsoft security trust boundary.

### Applying security mitigations to your environment for Copilot for Security

The rest of this article walks you through the steps to apply the principles of Zero Trust to prepare your environment for Copilot for Security.

Step	Task	Zero Trust principles applied
1	Protect admin accounts with identity and access policies, including your SecOps accounts.	Verify explicitly
2	Apply least privilege to admin accounts, including assigning the minimum user account roles.	Use least privileged access
3	Manage and protect admin user devices.	Verify explicitly
4	Deploy or validate your threat protection.	Assume breach
5	Secure access to third-party security products that you choose to integrate with Copilot for Security.	Verify explicitly
Use least privileged access
Assume breach

There are several approaches you can take to onboarding admins and SecOps staff to Copilot for Security while you configure protections for your environment.

### Per-user onboarding to Copilot for Security

At a minimum, walk through a checklist for each of your admins and SecOps staff before you assign a role for Copilot for Security. This works well for small teams and organizations that want to start with a test or pilot group. 

:::image type="content" source="media/copilot/onboarding-user-checklist.svg" alt-text="Diagram of desc." lightbox="media/copilot/onboarding-user-checklist.svg":::
  
### Phased deployment of Copilot for Security

For large environments, a more standard phased deployment works well. In this model, you address groups of users at the same time to configure protection and assign roles.

:::image type="content" source="media/copilot/security-copilot-phased-deployment.svg" alt-text="Diagram of desc." lightbox="media/copilot/security-copilot-phased-deployment.svg":::

In the illustration:

- In the **Evaluate** phase, you pick a small set of SecOps users that you want to have access to Copilot for Security and apply identity and access and device protections.
- In the **Pilot** phase, you pick the next set of SecOps users and apply identity and access and device protections.
- In the **Full deployment** phase, you apply identity and access and device protections for the rest of your SecOps users.
- At the end of each phase, you assign the appropriate role in Copilot for Security to the user accounts.

Because different organizations can be at various stages of deploying Zero Trust protections for their environment, in each of these steps:

- If you're NOT using any of the protections described in the step, take the time to pilot and deploy them to your admins and SecOps staff prior to assigning roles that include Copilot for Security.
- If you're already using some of the protections described in the step, use the information in the step as a checklist and verify that each protection stated has been piloted and deployed prior to assigning roles that include Copilot for Security.

## Step 1. Deploy or validate your identity and access policies

To prevent bad actors from using Copilot for Security to quickly get information on cyberattacks, the first step is to prevent them from gaining access. You must ensure that admin and SecOps staff:

- User accounts are required to use MFA (so their access can't be compromised by guessing user passwords alone). And, they are required to change their passwords when high-risk activity is detected.
- Devices must comply with Intune management and device compliance policies.

For identity and access policy recommendations, see the identity and access step in Apply principles of Zero Trust to Microsoft Copilot for Microsoft 365. Based on the recommendations in this article, ensure that your resulting configuration applies the following policies for all SecOps staff user accounts and their devices:

- Always use multifactor authentication (MFA) for sign-ins
- Block clients that don’t support modern authentication
- Require compliant PCs and mobile devices
- High risk users must change password (for Microsoft 365 E5 only)
- Require adherence to Intune device compliance policies

These recommendations align with the **Specialized security** protection level in Microsoft’s Zero Trust identity and device access policies. The following diagram illustrates the recommended three tiers of protection — Starting point, Enterprise, and Specialized. The Enterprise tier of protection can be used as a minimum level of protection for your privileged accounts.
  
:::image type="content" source="media/copilot/identity-device-access-policies-common.svg" alt-text="Diagram of desc." lightbox="media/copilot/identity-device-access-policies-common.svg":::

In the illustration, the recommended policies for Microsoft Entra Conditional Access, Intune device compliance, and Intune app protection are illustrated for each of the three levels:

- **Starting point**, which does not require device management
- **Enterprise** is recommended for Zero Trust and as a minimum for access to Copilot for Security and your third-party security products and related data
- **Specialized security** is recommended for access to Copilot for Security and your third-party security products and related data 

Each of these policies is described in greater detail in this article — Common Zero Trust identity and device access policies. 

### Configure a separate set of policies for privileged users

When configuring these policies for your admins and SecOps staff, create a separate set of policies for these privileged users. For example, don’t add your admins to the same set of policies that govern access of unprivileged users to apps such as Microsoft 365 and Salesforce. Use a dedicated set of policies with protections that are appropriate for privileged accounts. 

### Include security tools in the scope of Conditional Access policies

For now, there is not an easy way to configure Conditional Access for Copilot for Security. However, because on-behalf-of authentication is used to access data within security tools, be sure you have configured Conditional Access for these, including Microsoft Entra ID, Microsoft Intune, etc.

## Step 2. Apply the principle of least privilege to admin accounts

This step includes configuring the appropriate roles within Copilot for Security. It also includes reviewing your admin and SecOps accounts to ensure these are assigned the least privileged account for the work they are intended to do.

### Assign user accounts to Copilot for Security roles

The permissions model for Copilot for Security includes roles in both Microsoft Entra ID and Copilot for Security.

Product	Roles	Description
Microsoft Entra ID	Security Administrator
Global Administrator	These Microsoft Entra roles inherit the ‘Copilot owner’ role in Copilot for Security. Only use these privileged roles to onboard Copilot for Security to your organization.
Copilot for Security	Copilot owner
Copilot contributor	These roles include access to use Copilot for Security. Most of your admins and SecOps staff can use the Copilot contributor role.
The Copilot owner role includes access to publish custom plugins and to manage settings that affect all of Copilot for Security.

It’s important to know that, by default, All users in the tenant are given Copilot contributor access. With this configuration, access to your security tool data is governed by the permissions you configured for each of the security tools. An advantage of this configuration is that the embedded experiences of Copilot for Security are immediately available to your security staff within the products they use daily. This works well if you’ve already adopted a strong practice of least privileged access within your organization. 

If you’d like to take a staged approach to introducing Copilot for Security to your admins and SecOps staff while you tune up least privileged access in your organization, remove All users from the Copilot contributor role and add security groups as you are ready. 

For more information, see these resources:

- Onboarding to Copilot for Security
- Understanding authentication (live 4/1)

### Configuring or reviewing least privilege access for admin and SecOps accounts
Introducing Copilot for Security is a great time to review the access of your admin and SecOps staff accounts to be sure you are following through with the principle of least privilege for their access to specific products. This includes the following:

- Review the privileges granted for the specific products they work with. For example, for Microsoft Entra, see Least privileged roles by task.
- Use Microsoft Entra Privileged Identity Management (PIM) to gain greater control over access to Copilot for Security.
- Use Microsoft Purview Privileged Access Management (PAM) to configure granular access control over privileged admin tasks in Office 365. 

#### Using Microsoft Entra Privileged Identity Management (PIM) together with Copilot for Security

Microsoft Entra Privileged Identity Management (PIM) allows you to manage, control, and monitor the roles required to access Copilot for Security. With PIM, you can:

- Provide role activation that is time-based.
- Require approval to activate privileged roles.
- Enforce MFA to activate any role.
- Get notifications when privileged roles are activated.
- Conduct access reviews to ensure SecOps staff user account still need their assigned roles.
- Perform audits on access and role changes for SecOps staff.

#### Using privileged access management (PAM) together with Copilot for Security

Microsoft Purview Privileged Access Management helps protect your organization from breaches and helps to meet compliance best practices by limiting standing access to sensitive data or access to critical configuration settings. Instead of administrators having constant access, just-in-time access rules are implemented for tasks that need elevated permissions. Enabling privileged access management for Exchange Online in Microsoft 365 allows your organization to operate with zero standing privileges and provide a layer of defense against standing administrative access vulnerabilities. For more information, see Privileged Access Management.

## Step 3. Secure devices for privileged access

In Step 1, you configured Conditional Access policies that required managed and compliant devices for your admins and SecOps staff. For additional security, you can deploy privileged access devices for your staff to use when accessing security tools and data, including Copilot for Security. A privileged access device is a hardened workstation that has clear application control and application guard. The workstation uses credential guard, device guard, app guard, and exploit guard to protect the host from attackers. 

For more information on how to configure a device for privileged access, see Securing devices as part of the privileged access story.

To require these devices, be sure to update your Intune device compliance policy. If you are transitioning admins and SecOps staff to hardened devices, transition your security groups from the original device compliance policy to the new policy. The Conditional Access rule can remain the same.

## Step 4. Deploy or validate your threat protection services

To detect the activities of bad actors and keep them from gaining access to Copilot for Security, ensure that you can detect and respond to security incidents with a comprehensive suite of threat protection services, which include Microsoft Defender XDR with Microsoft 365, Microsoft Sentinel, and other security services and products. 

Use the following resources.

Scope	Description and resources
Microsoft 365 and SaaS apps integrated with Microsoft Entra	See this article for guidance on how to ramp up threat protection beginning with Microsoft 365 E3 plans and progressing with Microsoft E5 plans — Apply principles of Zero Trust to Microsoft Copilot for Microsoft 365
For Microsoft 365 E5 plans, also see Evaluate and pilot Microsoft Defender XDR security

Your Azure cloud resources
Your resources in other cloud providers, such as Amazon Web Services (AWS)	Use the following resources to get started with Defender for Cloud:
Microsoft Defender for Cloud library
Apply Zero Trust principles to IaaS applications in Amazon Web Services (AWS)

Your digital estate with all Microsoft XDR tools and Microsoft Sentinel	This solution guide walks through the process of setting up Microsoft eXtended detection and response (XDR) tools together with Microsoft Sentinel to accelerate your organization’s ability to respond to and remediate cybersecurity attacks — Implement Microsoft Sentinel and Microsoft Defender XDR for Zero Trust

## Step 5. Secure access to third-party security products and data

If you’re integrating third-party security products with Copilot for Security, be sure you have secured access to these products and related data. Microsoft Zero Trust guidance includes recommendations for securing access to SaaS apps. These recommendations can be used for your third-party security products.

For protection with identity and device access policies, changes to common policies for SaaS apps are outlined in red in the following illustration. These are the policies to which you can add your third-party security products.

:::image type="content" source="media/copilot/identity-device-access-policies-saas-apps.svg" alt-text="Diagram of desc." lightbox="media/copilot/identity-device-access-policies-saas-apps.svg":::
 
For your third-party security products and apps, consider creating a dedicated set of policies for these. This allows you to treat your security products with greater requirements compared to productivity apps, like Dropbox and Salesforce. For example, add Tanium and all other third-party security products to the same set of Conditional Access policies. If you want to enforce stricter requirements for devices for your admins and SecOps team, also configure unique policies for Intune device compliance and Intune app protection and assign these policies to your admins and SecOps team.

For more information about adding your security products to Microsoft Entra ID and to the scope of your Conditional Access and related policies (or configuring a new set of policies), see Add SaaS apps to Microsoft Entra ID and to the scope of policies.

Depending on the security product, it might be appropriate to use Microsoft Defender for Cloud Apps to monitor the use of these apps and apply session controls. Additionally, if these security apps include storage of data in any of the file types supported by Microsoft Purview, you can use Defender for Cloud to monitor and protect this data using sensitivity labels and data loss prevention (DLP) policies. For more information, see Integrate SaaS apps for Zero Trust with Microsoft 365.

### Example for Tanium SSO

For example, Tanium, a provider of endpoint management tools, offers a custom plugin for Copilot for Security — Tanium Skills. This plugin helps ground prompts and responses that leverage Tanium-gathered information and insights. 
 
:::image type="content" source="media/copilot/security-copilot-architecture-tanium-example.svg" alt-text="Diagram of desc." lightbox="media/copilot/security-copilot-architecture-tanium-example.svg":::

In the illustration:

- Tanium Skills is a custom plugin for Microsoft Copilot for Security.
- Tanium Skills provides access to and helps ground both prompts and responses that use Tanium-gathered information and insights.
Securing access to the Tanium security products involves adding Tanium SSO to your Microsoft Entra ID tenant and then adding Tanium SSO to the scope of your Conditional Access and related policies. 

To secure access to Tanium products and related data:

1. Use the Microsoft Entra ID Application Gallery to find and add Tanium SSO to your tenant. See Add an enterprise application. For a Tanium-specific example, see Microsoft Entra SSO integration with Tanium SSO
2. Add Tanium SSO to the scope of your Zero Trust identity and access policies. 


## Next steps

Watch the Discover Microsoft Copilot for Security video. 

See the Microsoft Copilot for Security documentation.

## References

Refer to these links to learn about the various services and technologies mentioned in this article.

- Get started with Microsoft Copilot for Security
- Onboarding to Copilot for Security
- Apply principles of Zero Trust to Microsoft Copilot for Microsoft 365
- Data sources for Microsoft Sentinel
- Microsoft Entra Privileged Identity Management (PIM)
- Privileged Access Management (PAM)
- Privileged access devices
