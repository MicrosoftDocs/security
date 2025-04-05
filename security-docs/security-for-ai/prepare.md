---
title: How do I prepare my environment for AI security?
description: How to prepare your environment for AI security with identity and device protection, data protection, and threat protection. 
ms.date: 04/01/2025
ms.service: security
author: BrendaCarter
ms.author: bcarter
ms.topic: concept-article
ms.collection: 
  - msftsolution-security-for-ai
  - msftsolution-scenario
  - zerotrust-solution
---

# Prepare for AI security

This article describes the basic security measures you should implement for preparing your environment for AI, including the enablement of security tools used for discovering, protecting, and governing AI. This article is the first one in a series.

:::image type="content" source="media/security-for-ai-step-prepare.svg" alt-text="Diagram that shows the Prepare part of the security for AI.":::

Preparing for AI focuses on implementing foundation security protections across your digital estate: 

 - Identity and device access policies 
 - Data protection 
 - Threat protection 

These protections aren’t unique to protecting AI. They greatly improve your security posture for all your apps, data, users, and devices, including AI apps and data.  

At the same time, these protections build the foundation upon which AI-specific security and governance features operate. For example, Microsoft Purview data protection includes visibility into AI websites your organization uses and your organization data that interacts with these sites. Microsoft Defender threat protection capabilities include discovery and governance of AI apps, including AI models and other AI application components across cloud environments, including OpenAI, Amazon Web  Services, and Google Cloud Platform. 

These foundation security protections should be applied across your digital estate, enabling AI security and governance across the breadth of your organization footprint.

:::image type="content" source="media/saas-apps-and-azure-apps.svg" alt-text="Diagram of the digital estate that includes Saas apps, Azure apps, and cloud providers." lightbox="media/saas-apps-and-azure-apps.svg":::

In the illustration, your digital estate includes: 

- SaaS apps your organization uses, including Microsoft 365. 
- Your apps in Azure spread across multiple Azure subscriptions. 
- Your apps in other cloud providers, including Amazon Web Services and Google Cloud Platform. 

These same foundation security protections are recommended to prepare for Microsoft Copilots—[Use Zero Trust security to prepare for AI companions, including Microsoft Copilots](../zero-trust/copilots/apply-zero-trust-copilots-overview.md): 

- [Microsoft Copilot Chat](../zero-trust/copilots/zero-trust-microsoft-copilot.md) 
- [Microsoft 365 Copilot](../zero-trust/copilots/zero-trust-microsoft-365-copilot.md)
- [Security Copilot](../zero-trust/copilots/zero-trust-microsoft-copilot-for-security.md)

## Start with identity and device access protections

One of the most powerful things you can do to protect your environment is to implement multifactor authentication and Conditional Access through Microsoft Entra ID. Microsoft recommends a policy set that achieves the goals of Zero Trust - [Common Zero Trust identity and device access policies](../zero-trust/zero-trust-identity-device-access-policies-common.md). This policy set includes: 

- Starting-point policies that can be implemented right away. Get started by implementing these policies.
- Enterprise policies that are recommended for Zero Trust. These policies require enrolling devices into management, which can take some time.

The work of planning, architecting, and deploying identity and device access policies is described in the Microsoft’s Zero Trust guidance center: [Secure remote and hybrid work with Zero Trust](../zero-trust/adopt/secure-remote-hybrid-work.md). 

To prepare for AI, be sure to apply identity and device access protection across your digital estate. This positions your organization to easily add newly discovered AI apps to the scope of Conditional Access policies.  

The following graphic suggests an order for doing this work.  

:::image type="content" source="media/order-for-integration.svg" alt-text="Diagram that shows the order for integration." lightbox="media/order-for-integration.svg":::

The following table lists the steps illustrated above. 

| Step | Task  |
| ---- | ----------------------------- |
| 1    | Configure identity and device access policies for Microsoft 365. See [Common Zero Trust identity and device access policies.](../zero-trust/zero-trust-identity-device-access-policies-common.md) The [prerequisites](../zero-trust/zero-trust-identity-device-access-policies-prerequisite.md) for this work include enabling Entra ID Protection. This work includes enrolling devices into management. See [Manage devices with Intune](/microsoft-365/solutions/manage-devices-with-intune-overview). |
| 2    | Integrate SaaS apps with Entra ID. These can be added through the Microsoft Entra Gallery. Be sure these apps are included in the scope of your identity and device access policies. See [Add SaaS apps to Microsoft Entra ID and to the scope of policies](../zero-trust/add-saas-apps.md).  |
| 3    | Integrate custom apps in Azure with Entra ID. Be sure these apps are included in the scope of your identity and device access policies. See [Five steps to integrate your apps with Microsoft Entra ID](/entra/fundamentals/five-steps-to-full-application-integration). |
| 4    | Integrate custom apps in other cloud providers with Entra ID. Be sure these apps are included in the scope of your identity and device access policies. [Five steps to integrate your apps with Microsoft Entra ID](/entra/fundamentals/five-steps-to-full-application-integration) . |

## Make progress on data protection 

Data protection takes time for an organization to fully implement. Traditionally, this involves waves of deployment steps that you roll out across your organization.  

:::image type="content" source="media/adoption-information-protection.svg" alt-text="Diagram of the process for technical adoption of information protection." lightbox="media/adoption-information-protection.svg":::

In the illustration, the technical adoption of information protection involves cascading steps that you can run in parallel:

 - Discover and identify sensitive business data 
 - Develop a classification and protection schema 
 - Test and pilot the schema with data in Microsoft 365 
 - Deploy the classification and protection schema to data across Microsoft 365 
 - Extend the schema to data in other SaaS apps 
 - Continue to discover and protect data in other repositories


The work of planning, architecting, and deploying identity and device access policies is described in the Microsoft’s Zero Trust guidance center: [Identify and protect sensitive business data with Zero Trust](../zero-trust/adopt/identify-protect-sensitive-business-data.md). 

With the rapid adoption of AI tools, many organizations are taking an accelerated approach to data protection—immediately prioritizing protection for the most sensitive data and then filling in gaps and building maturity over time.  

Microsoft Purview includes Data Security Posture Management (DSPM) capabilities which can help organizations develop maturity in data protection, no matter where you are on your journey. DSPM capabilities help provide easy configuration and new policy creation across several data security and risk & compliance solutions.  

By automatically scanning data and activities across your organization, you'll quickly get baseline insights and recommendations focused on unprotected data that can help you quickly get started in DLP, information protection, and insider risk management. DSPM for AI provides ready-to-use policies to help you get started. 

If you’ve already started your data protection journey with policies, use DSPM capabilities to identify gaps in coverage.

DSPM (Preview) identifies sensitive data by matching for sensitive information types across your Microsoft 365 environment. 

- Provides policy recommendations you can start with 
- Provides insights into data security risks 
- Measures the effectiveness of your data security policies 
- Provides insights into risky users 
- Provides an embedded Microsoft Security Copilot experience to help identify other risks 

DSPM for AI provides insights and analytics into AI activity in your organization.

- Ready-to-use policies to protect data and prevent data loss in AI prompts 
- Data assessments to identify, remediate, and monitor potential oversharing of data 
- Recommended actions based on data in your tenant 
- Compliance controls to apply optimal data handling and storing policies 
- Deeper insights for Microsoft Copilots and third-party SaaS applications like ChatGPT Enterprise and Google Gemini

Use the following resources to make progress with Microsoft Purview. 

| Task | Recommended resources |
| -------------------- | ------------- |
| Learn about recommended deployment strategies for information protection | [Deploy an information protection solution with Microsoft Purview ](/purview/information-protection-solution?tabs=phase-one) |
| Start using DSPM | [Get started with Data Security Posture Management (preview)](/purview/data-security-posture-management-get-started) |
| Get started with DSPM for AI  | [Microsoft Purview data security and compliance protections for Microsoft 365 Copilot and other generative AI apps](/purview/ai-microsoft-purview) |


## Turn on threat detection and response 

Finally, turn on Microsoft Defender threat protection capabilities. Some of these tools are easy to start. Others require a bit of planning and configuration. Some of these tools include AI-specific features you can turn on right away and gain value from. 

This work is described in the Microsoft Zero Trust adoption framework: [Implement threat protection and XDR](../zero-trust/adopt/prevent-reduce-business-damage-breach-threat-protection.md).  

:::image type="content" source="media/turn-on-threat-detection-and-response.svg" alt-text="Diagram that shows capabilities of turning on threat detection and response." lightbox="media/turn-on-threat-detection-and-response.svg":::

Use the following resources to enable threat protection. 

| Task| Recommended resources   |
| ----------- | --------------- |
| Deploy Microsoft Defender XDR: <br> <li> Defender for Identity <br><li> Defender for Office <br> <li> Defender for Endpoint <br> <li> Defender for Cloud Apps | [Pilot and deploy Microsoft Defender XDR](/defender-xdr/pilot-deploy-overview) |
| Deploy Microsoft Entra ID Protection | [Plan a Microsoft Entra ID Protection deployment - Microsoft Entra ID Protection](/entra/id-protection/how-to-deploy-identity-protection)|
| Deploy Defender for Cloud| [Microsoft Defender for Cloud documentation](/azure/defender-for-cloud/) <br> [Connect your Azure subscriptions](/azure/defender-for-cloud/connect-azure-subscription) <br> [Enable threat protection for AI workloads (preview)](/azure/defender-for-cloud/ai-onboarding#enable-threat-protection-for-ai-workloads) <br> [Protect your resources with Defender CSPM](/azure/defender-for-cloud/tutorial-enable-cspm-plan) <br> [Review the Data and AI security dashboard (Preview)](/azure/defender-for-cloud/data-aware-security-dashboard-overview)  <br> [Connect your AWS account](/azure/defender-for-cloud/quickstart-onboard-aws) <br> [Connect your GCP project](/azure/defender-for-cloud/quickstart-onboard-gcp) |
| Deploy Defender for IoT     | [Deploy Defender for IoT for OT monitoring](/azure/defender-for-iot/organizations/ot-deploy/ot-deploy-path) |
| Integrate threat protection tools with Sentinel (SIEM)  | [Incident Response with XDR and Integrated SIEM](../zero-trust/siem-xdr-overview.md) |

For information on how to enable threat protection for AI within these tools, see [Protect AI data and apps](protect.md).

## Next steps

See the next article in this series: [How do I discover AI apps and the sensitive data these use in my organization?](discover.md)