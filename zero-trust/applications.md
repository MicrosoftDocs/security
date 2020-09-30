---
title: Audit Requirements - Microsoft Trusted Root Certificate Program
description: To get the full benefit of cloud apps and services, organizations must find the right balance of providing access while maintaining control to protect critical data accessed via applications and APIs. 
ms.date: 09/01/2020
ms.service: security
author: Kellylorenebaker
ms.author: v-kbaker
ms.topic: conceptual
---


# Secure applications with Zero Trust

:::image type="icon" source="./media/icon-application-window-medium.png":::

**Background**


To get the full benefit of cloud apps and services, organizations must find the right balance of providing access while maintaining control to protect critical data accessed via applications and APIs.

The **Zero Trust** model helps organizations ensure that apps, and the data they contain, are protected by:

-   Applying controls and technologies to discover Shadow IT.
-   Ensuring appropriate in-app permissions. 
-   Limiting access based on real-time analytics. 
-   Monitoring for abnormal behavior. 
-   Controlling user actions. 
-   Validating secure configuration options. 

## Applications Zero Trust deployment objectives

<div class="alert">
   <p><b>Before</b> most organizations <b>start the Zero Trust journey</b>, their on-premises apps are accessed through physical networks or VPN, and some critical cloud apps are accessible to users.</p>
</div>




<table border="0">
   <tr>
      <td colspan="2">
         <p>When implementing a Zero Trust approach to managing and monitoring applications, we recommend you focus first on these <b>initial deployment objectives</b>:</p>
	  </td>
   </tr>
   <tr>
      <td>
		 <p><img src="./media/icon-initial-deployment-small.png" alt="List icon with one checkmark."></p>
      </td>
      <td>
		 <p><b>I.</b> <a href="#i-gain-visibility-into-the-activities-and-data-in-your-applications-by-connecting-them-via-apis">Gain visibility into the activities and data in your applications by connecting them via APIs.</a></p>
	     <p><b>II.</b> <a href="#ii-discover-and-control-the-use-of-shadow-it">Discover and control the use of shadow IT.</a></p>
		 <p><b>III.</b> <a href="#iii-protect-sensitive-information-and-activities-automatically-by-implementing-policies">Protect sensitive information and activities automatically by implementing policies.</a></p>
      </td>
   </tr>
   <tr>
      <td colspan="2">
         <p>After these are completed, focus on these <b>additional deployment objectives</b>:</p>
      </td>
   </tr>
   <tr>
      <td>
		 <p><img src="./media/icon-additional-deployment-small.png" alt="List icon with two checkmarks."></p>
      </td>
      <td>
         <p><b>IV.</b> <a href="#iv-deploy-adaptive-access-and-session-controls-for-all-apps">Deploy adaptive access and session controls for all apps.</a></p>
         <p><b>V.</b> <a href="#v-strengthen-protection-against-cyber-threats-and-rogue-apps">Strengthen protection against cyber threats and rogue apps.</a></p>
         <p><b>VI.</b> <a href="#vi-assess-the-security-posture-of-your-cloud-environments">Assess the security posture of your cloud environments</a></p>
      </td>
   </tr>
</table>

## Application Zero Trust deployment guide

This guide will walk you through the steps required to secure applications and APIs following the principles of a Zero Trust security framework. Our approach is aligned with these three Zero Trust principles:

1.  **Verify explicitly.** Always authenticate and authorize based on all available data points, including user identity, location, device health, service or workload, data classification, and anomalies.

2.  **Use least privileged access.** Limit user access with Just-In-Time and Just-Enough-Access (JIT/JEA), risk-based adaptive polices and data protection to protect both data and productivity.

3.  **Assume breach.** Minimize blast radius for breaches and prevent lateral movement by segmenting access by network, user, devices, and application awareness. Verify all sessions are encrypted end to end. Use analytics to get [visibility](https://aka.ms/ZTCrossPillars), drive threat detection, and improve defenses.


<!-- H2 heading, "Initial deployment objectives" -->
<br/><br/>
[!INCLUDE [H2 heading, Initial deployment objectives](./includes/deployment-objectives-initial.md)]


### I. Gain visibility into the activities and data in your applications by connecting them via APIs

The majority of users\' activities in an organization originate on cloud applications and associated resources. Most major cloud apps provide an API for consuming tenant information and receiving corresponding governance actions. Use these integrations to monitor and alert when threats and anomalies occur in your environment.

Follow these steps:

1.  Adopt [Microsoft Cloud App Security](https://www.microsoft.com/microsoft-365/enterprise-mobility-security/cloud-app-security), which works with services to optimize visibility, governance actions, and usage.

2.  [Review what apps can beconnected](https://docs.microsoft.com/cloud-app-security/enable-instant-visibility-protection-and-governance-actions-for-your-apps) with the Cloud App Security API integration, and connect the appsyou need. Use the deeper visibility gained to investigate activities, files, and accounts for the apps in your cloud environment.

> [!TIP]
> [Learn about implementing an end-to-end identity Zero Trust strategy](https://aka.ms/ZTIdentity).

### II. Discover and control the use of shadow IT

On average, 1,000 separate apps are being used in your organization. 80 percent of employees use non-sanctioned apps that no one has reviewed and that may not be compliant with your security and compliance policies. And, because your employees are able to access your resources and apps from outside your corporate network, it's no longer enough to have rules and policies on your firewalls.

Focus on identifying app usage patterns, assessing risk levels and business readiness of apps, preventing data leaks to noncompliant apps, and limiting access to regulated data.

> [!TIP]
> [Learn about implementing an end-to-end Zero Trust strategy for data](https://aka.ms/ZTData).

Follow these steps:

1.  Set up [Cloud Discovery](https://docs.microsoft.com/cloud-app-security/set-up-cloud-discovery), which analyzes your traffic logs against Microsoft Cloud App Security's catalog of over 16,000 cloud apps. The apps are ranked and scored, based on more than 90 risk factors.

2.  [Discover and identify shadow IT](https://docs.microsoft.com/cloud-app-security/tutorial-shadow-it#phase-1-discover-and-identify-shadow-it) to find out what apps are being used, following one of three options:

    1.  Integrate with [Microsoft Defender ATP](https://docs.microsoft.com/cloud-app-security/wdatp-integration) to immediately start collecting data on cloud traffic across your Windows 10 devices, on and off your network.

    1.  Deploy the [Cloud App Security log collector](https://docs.microsoft.com/cloud-app-security/discovery-docker) on your firewalls and other proxies to collect data from your endpoints and send it to Cloud App Security for analysis.

    1.  Integrate Cloud App Security with your proxy.

3.  Identify the [risk level](https://docs.microsoft.com/cloud-app-security/risk-score) of specific apps:

    1.  In the Cloud App Security portal, under Discover, click **Discovered apps**. Filter the list of apps discovered in your organization by the risk factors you are concerned about.

    1.  Drill down into the app to understand more about its compliance by clicking the app name and then clicking the **Info** tab to see details about the app's security risk factors.

4.  [Evaluate compliance and analyze usage](https://docs.microsoft.com/cloud-app-security/tutorial-shadow-it#phase-2-evaluate-and-analyze):

    1.  In the Cloud App Security portal, under Discover, click **Discovered apps**. Filter the list of apps discovered in your organization by the compliance risk factors you are concerned about. For example, use the suggested query to filter out noncompliant apps.

    1.  Drill down into the app to understand more about its compliance by clicking the app name and then clicking the **Info** tab to see details about the app's compliance risk factors.

    1.  In the Cloud App Security portal, under Discover, click **Discovered apps** and then drill down by clicking on the specific app you want to investigate. The Use tab lets you know how many active users are using the app and how much traffic it's generating. If you want to see who, specifically, is using the app, you can drill down further by clicking **Total active users**.

    1.  [Dive deeper](https://docs.microsoft.com/cloud-app-security/discovered-apps#deep-dive-into-discovered-apps) into discovered apps. View subdomains and resources to learn about specific activities, data access, and [resource usage](https://docs.microsoft.com/cloud-app-security/discovered-apps#discover-resources-and-custom-apps) in your cloud services.

5.  [Manage your apps](https://docs.microsoft.com/cloud-app-security/tutorial-shadow-it#phase-3-manage-your-apps):

    1.  Create new custom app tags in order to classify each app according to its business status or justification. These tags can then be used for specific monitoring purposes.

    1.  App tags can be managed under Cloud Discovery settings App tags. These tags can then be used later for filtering in the Cloud Discovery pages and creating policies using them.

    1.  Manage discovered apps using [Azure Active Directory (Azure AD) Gallery](https://docs.microsoft.com/azure/active-directory/manage-apps/add-gallery-app). For apps that already appear in the Azure AD Gallery, apply single sign-on and manage the app with Azure AD. To do so, on the row where the relevant app appears, choose the three dots at the end of the row, and then choose **Manage app with Azure AD**.

> [!TIP]
> [Learn about implementing an end-to-end Zero Trust strategy for your network](https://aka.ms/ZTNetwork).

### III. Protect sensitive information and activities automatically by implementing policies

Cloud App Security enables you to define the way you want users to behave in the cloud. This can be done by creating policies. There are many types: Access, activity, anomaly detection, app discovery, file policy, cloud discovery anomaly detection, and session policies.

Policies allow you to detect risky behavior, violations, or suspicious data points and activities in your cloud environment. They help you monitor trends, see security threats, and generate customized report and alerts.

Follow these steps:

1.  [Use out-of-the box policies](https://docs.microsoft.com/cloud-app-security/control-cloud-apps-with-policies) that have already been tested for many activities and files. Apply governance actions such as revoking permissions and suspending users, quarantining files, and applying sensitivity labels.

2.  Build new policies that Microsoft Cloud Apps Security suggests for you.

3.  Configure policies to monitor shadow IT apps and provide control:

    1.  Create an [app discovery policy](https://docs.microsoft.com/cloud-app-security/cloud-discovery-policies) that lets you know when there is a spike in downloads or traffic from an app you\'re concerned about. Enable **Anomalous behavior in discovered users' policy, Cloud storage app compliance check,** and **New risky app.**

    1.  Keep updating policies, and using the Cloud Discovery dashboard, check what (new) apps your users are using, as well as their usage and behavior patterns.

4.  [Control what's sanctioned](https://docs.microsoft.com/cloud-app-security/tutorial-shadow-it#phase-5-control-sanctioned-apps) and block undesirable apps using this option:

    1.  [Connect apps via API](https://docs.microsoft.com/cloud-app-security/enable-instant-visibility-protection-and-governance-actions-for-your-apps) for continuous monitoring.

5.  Protect apps using [Conditional Access App Control](https://docs.microsoft.com/cloud-app-security/proxy-intro-aad) and [Microsoft Cloud App Security](https://www.microsoft.com/microsoft-365/enterprise-mobility-security/cloud-app-security).


<!-- H2 heading, "Additional deployment objectives" -->
<br/><br/>
[!INCLUDE [H2 heading, Additional deployment objectives](./includes/deployment-objectives-additional.md)]


### IV. Deploy adaptive access and session controls for all apps

Once you've accomplished your initial three objectives, you can focus on
additional objectives such as ensuring that all apps are using
least-privileged access with continuous verification. Dynamically
adapting and restricting access as session risk changes will enable you
to stop breaches and leaks in real time, before employees put your data
and your organization at risk.

Take this step:

 - [Enable real-time monitoring and control over access to any web app](https://docs.microsoft.com/cloud-app-security/proxy-intro-aad), based on user, location, device, and app. For example, you can create policies to protect downloads of sensitive content with sensitivity labels when using any unmanaged device. Alternatively, files can be scanned on upload to detect potential malware and block them from entering sensitive cloud environment.

> [!TIP]
> [Learn about implementing an end-to-end Zero Trust strategy for endpoints](https://aka.ms/ZTEndpoints).


### V. Strengthen protection against cyber threats and rogue apps

Bad actors have developed dedicated and unique attack tools, techniques, and procedures (TTPs) that target the cloud to breach defenses and access sensitive and business-critical information. They use tactics such as illicit OAuth consent grants, cloud ransomware, and compromising credentials for cloud identity.

Organizations can respond to such threats with tools available in Cloud App Security, such as user and entity behavioral analytics (UEBA) and anomaly detection, malware protection, OAuth app protection, incident investigation, and remediation. Cloud App security targets numerous [security anomalies](https://docs.microsoft.com/cloud-app-security/investigate-anomaly-alerts) out of the box, such as impossible travel, suspicious inbox rules, and ransomware.

The different detections are developed with security operations teams in mind and aim to focus the alerts on true indicators of compromise, while unlocking threat intelligence-driven investigation and remediation.

Follow these steps:

- [Take advantage of Cloud App Security's UEBA and machine learning (ML) capabilities that are automatically enabled out-of-the-box](https://docs.microsoft.com/cloud-app-security/anomaly-detection-policy) to immediately detect threats and run advanced threat detection across your cloud environment.

- [Tune and scope](https://docs.microsoft.com/cloud-app-security/anomaly-detection-policy#tune-anomaly-detection-policies) anomaly detection policies.


### VI. Assess the security posture of your cloud environments

Beyond SaaS applications, organizations are heavily invested in IaaS and PaaS services. Cloud App Security enables your organization to assess and strengthen your security posture and capabilities for these services by getting visibility into the security configuration and compliance status across your public cloud platforms. This enables a risk-based investigation of the entire platform configuration status.

Follow these steps:

1.  Use Cloud App Security to monitor resources, subscriptions, recommendations, and corresponding severities across your cloud environments.

2.  Limit the risk of a security breach by keeping cloud platforms, such as [Microsoft Azure](https://docs.microsoft.com/cloud-app-security/protect-azure), [AWS](https://docs.microsoft.com/cloud-app-security/protect-aws) and [GCP](https://docs.microsoft.com/cloud-app-security/protect-gcp), compliant with your organizational configuration policy and regulatory compliance, following CIS benchmark, or the vendor's best practices for the security configuration.

3.  Using Cloud App Security, the security configuration dashboard can be used to drive remediation actions to minimize the risk.

> [!TIP]
> [Learn about implementing an end-to-end Zero Trust strategy for your infrastructure](https://aka.ms/ZTInfrastructure).

## Products covered in this guide

**Microsoft Azure**

[Microsoft Azure Active Directory](https://azure.microsoft.com/services/active-directory/)

**Microsoft 365**

[Microsoft Cloud App Security](https://www.microsoft.com/microsoft-365/enterprise-mobility-security/cloud-app-security)

[Cloud Discovery](https://docs.microsoft.com/cloud-app-security/set-up-cloud-discovery)

[Microsoft Endpoint Manager](https://www.microsoft.com/endpointmanager)
(includes Microsoft Intune and Configuration Manager)

[Mobile Application Management](https://docs.microsoft.com/mem/intune/apps/mam-faq)

## Conclusion

Regardless of where the cloud resource or application resides, Zero Trust principles help ensure that your cloud environments and data are protected. For further information on these processes or help with these implementations, please contact your Customer Success team.


<br/><br/>
[!INCLUDE [navbar, bottom](./includes/navbar-bottom.md)]

