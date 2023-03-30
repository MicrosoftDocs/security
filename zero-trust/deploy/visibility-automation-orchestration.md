---
title: Visibility, automation, and orchestration with Zero Trust
description: Since Zero Trust does not assume that requests are trustworthy, establishing a means to attest to the trustworthiness of the request is critical to proving its point-in-time trustworthiness. This attestation requires the ability to gain visibility into the activities on and around the request.
ms.date: 09/30/2020
ms.service: security
author: Kellylorenebaker
ms.author: v-kbaker
ms.topic: conceptual
ms.collection:
  - zerotrust-pillar
---

# Visibility, automation, and orchestration with Zero Trust

:::image type="icon" source="../media/icon-visibility-automation-orchestration-medium.png":::

One of the significant changes in perspectives that is a hallmark of a Zero Trust security frameworks is moving away from trust-by-default toward trust-by-exception. However, you need some reliable way to establish trust once trust is needed. Since you no longer assume that requests are trustworthy, establishing a means to attest to the trustworthiness of the request is critical to proving its point-in-time trustworthiness. This attestation requires the ability to gain visibility into the activities on and around the request.

In our other Zero Trust guides, we defined the approach to implementing an end-to-end Zero Trust approach across [identities](https://aka.ms/ZTIdentity), [endpoints](https://aka.ms/ZTEndpoints) and devices, [data](https://aka.ms/ZTData), [apps](https://aka.ms/ZTApplications), [infrastructure](https://aka.ms/ZTInfrastructure), and [network](https://aka.ms/ZTNetwork). All these investments increase your visibility, which gives you better data for making trust decisions. However, by adopting a Zero Trust approach in these six areas, you necessarily increase the number of incidents Security Operation Centers (SOC) analysts need to mitigate. Your analysts become busier than ever, at a time when there is already a talent shortage. This can lead to chronic alert fatigue and analysts missing critical alerts.

:::image type="content" source="../media/diagram-provide-integrated-capabilities-manage-threats.png" alt-text="Diagram of integrated capabilities to manage threats." border="true":::

With each of these individual areas generating their own relevant alerts, we need an integrated capability to manage the resulting influx of data to better defend against threats and validate trust in a transaction.

You want the ability to: 

-  Detect threats and vulnerabilities.
-  Investigate.
-  Respond.
-  Hunt.
-  Provide additional context through threat analytics.
-  Assess vulnerabilities.
-  Get help from world class experts
-  Prevent or block events from happening across the pillars.

Managing threats includes reactive as well as proactive detection and requires tools that support both.

**Reactive detection** is when incidents are triggered from one of the six pillars that can be investigated. Additionally, a management product like a SIEM will likely support another layer of analytics that will enrich and correlate data, resulting in flagging an incident as bad. The next step would then be to investigate to get the full narrative of the attack.

**Proactive detection** is when you apply hunting to the data to prove a compromised hypothesis. Threat hunting starts with the assumption you have been breached--you hunt for proof that there is indeed a breach.

Threat hunting starts with a hypothesis based on current threats, such as COVID-19 phishing attacks. Analysts start with this hypothetical threat, identify the key indicators of compromise, and hunt through the data to see if there is proof that the environment has been compromised. If indicators exist, hunting scenarios may result in analytics that would notify the organizations if the certain indicators occurs again.

Either way, once an incident is detected, you need to investigate it to build out the complete story of the attack. What else did the user do? What other systems were involved? What executables were run?

If an investigation results in actionable learnings, you can take remediation steps. For example, if an investigation uncovers gaps in a zero trust deployment, policies can be modified to address these gaps and prevent future unwanted incidents. Whenever possible it is desirable to automate remediation steps, because it reduces the time it takes for a SOC analyst to address the threat and move onto the next incident.

Another key component in the assessment of threats is incorporating known threat intelligence against the ingested data. If an IP, hash, URL, file, executable, etc. are known to be bad, they can be identified, investigated, and remediated.

In the [infrastructure](https://aka.ms/ZTInfrastructure) pillar, time was spent on addressing vulnerabilities. If a system is known to be vulnerable and a threat took advantage of that vulnerability, this is something that could be detected, investigated, and remediated.

In order to use these tactics to manage threats, you should have a central console to allow SOC administrators to detect, investigate, remediate, hunt, utilize threat intelligence, understand known vulnerabilities, lean on threat experts and block threats across any of the six pillars. The tools needed to support these phases work best if converged into a single workflow, providing a seamless experience that increases the effectiveness of the SOC analyst.

Security Operation Centers often deploy a combination of SIEM and SOAR technologies to collect, detect, investigate, and respond to threats. Microsoft offers Microsoft Sentinel as its SIEM-as-a-service offering. Microsoft Sentinel ingests all Microsoft Defender for Identity and third-party data.

Microsoft Threat Protection (MTP), a key feed into Microsoft Sentinel, provides a unified enterprise defense suite that brings context-aware protection, detection, and response across all Microsoft 365 components. By being context- aware and coordinated, customers using Microsoft 365 can gain visibility and protection across endpoints, collaboration tools, identities, and applications.

It is through this hierarchy that we enable our customers to maximize their focus. Though context-awareness and automated remediation, MTP can detect and stop many threats without adding additional alert-fatigue to already overloaded SOC personnel. Advanced hunting inside of MTP brings that context to the hunt to focus on many key attack points. And hunting and orchestration across the entire ecosystem through Microsoft Sentinel provides the ability to gain the right visibility into all aspects of a heterogeneous environment, all while minimizing the cognitive overload of the operator.

## Visibility, automation, and orchestration Zero Trust deployment objectives


<table border="0">
   <tr>
      <td colspan="2">
         <p>When implementing an end-to-end Zero Trust framework for visibility, automation, and orchestration, we recommend you focus first on these <b>initial deployment objectives</b>:</p>
	  </td>
   </tr>
   <tr>
      <td>
		 <p><img src="../media/icon-initial-deployment-small.png" alt="List icon with one checkmark."></p>
      </td>
      <td>
		 <p><b>I.</b> <a href="#i-establish-visibility">Establish visibility.</a></p>
	     <p><b>II.</b> <a href="#ii-enable-automation">Enable automation.</a></p>
      </td>
   </tr>
   <tr>
      <td colspan="2">
         <p>After these are completed, focus on these <b>additional deployment objectives</b>:</p>
      </td>
   </tr>
   <tr>
      <td>
		 <p><img src="../media/icon-additional-deployment-small.png" alt="List icon with two checkmarks."></p>
      </td>
      <td>
         <p><b>III.</b> <a href="#iii-enable-additional-protection-and-detection-controls">Enable additional protection and detection controls.</a></p>
      </td>
   </tr>
</table>

## Visibility, automation, and orchestration Zero Trust deployment guide

This guide will walk you through the steps required to manage visibility, automation, and orchestration following the principles of a Zero Trust security framework.


<br/><br/>
<!-- H2 heading, "Initial deployment objectives" -->
[!INCLUDE [H2 heading, Initial deployment objectives](../includes/deployment-objectives-initial.md)]



### I. Establish visibility

The first step is to establish visibility by enabling [Microsoft Threat Protection](https://www.microsoft.com/security/business/threat-protection/integrated-threat-protection) (MTP).

Follow these steps:

1.  Sign up for one of the Microsoft Threat Protection workloads.
2.  Enable the workloads and establish connectivity.
3.  Configure detection on your devices and infrastructure to bring immediate visibility into activities going on in the environment.
    This gives you the all-important "dial tone" to start the flow of critical data.
4.  Enable Microsoft Threat Protection to gain cross-workload visibility and incident detection.


### II. Enable automation

The next key step, once you have established visibility, is to enable automation.


#### Automated investigations and remediation

With Microsoft Threat Protection, we have automated both investigations and remediation, which essentially provides an extra Tier 1 SOC analysis.

[Automated Investigation and Remediation](/microsoft-365/security/mtp/mtp-autoir) (AIR) can be enabled gradually, so that you can develop a comfort level with the actions that are taken.

Follow these steps:

1.  Enable AIR for a test group.
2.  Analyze the investigation steps and response actions.
3.  Gradually transition to automatic approval for all devices to reduce the time to detection and response.


#### Link Microsoft data connectors and relevant third-party products to Microsoft Sentinel

In order to gain visibility into the incidents that result from deploying a Zero Trust model, it is important to connect MTP, other Microsoft data connectors, and relevant third party products to [Microsoft Sentinel](https://azure.microsoft.com/services/azure-sentinel/) in order to provide a centralized platform for incident investigation and response.  
  
As part of the data connection process, relevant analytics can be enabled to trigger incidents and workbooks can be created for a graphical representation of the data over time.


#### Link threat intelligence data to Microsoft Sentinel

Although machine learning and fusion analytics are provided out of the box, it is also beneficial to ingest threat intelligence data into Microsoft Sentinel to help identify events that relate to known bad entities.


<br/><br/>
<!-- H2 heading, "Additional deployment objectives" -->
[!INCLUDE [H2 heading, Additional deployment objectives](../includes/deployment-objectives-additional.md)]



### III. Enable additional protection and detection controls

Enabling additional controls improves the signal coming in to MTP and Sentinel to improve your visibility and ability to orchestrate responses.

[Attack surface reduction](/windows/security/threat-protection/microsoft-defender-atp/overview-attack-surface-reduction) controls represent one such opportunity. These protective controls not only block certain activities that are most associated with malware, but also give into attempts to use specific approaches, which can help to detect adversaries leveraging these techniques earlier in the process.

## Products covered in this guide

**Microsoft Azure**

[Microsoft Defender for Identity](https://www.microsoft.com/security/business/threat-protection/identity-defender)

[Microsoft Sentinel](https://azure.microsoft.com/services/azure-sentinel/)

**Microsoft 365**

[Microsoft Threat Protection](https://www.microsoft.com/security/business/threat-protection/microsoft-365-defender)


<br/><br/>
<!-- Include the nav bar. -->
[!INCLUDE [navbar, bottom](../includes/navbar-bottom.md)]
