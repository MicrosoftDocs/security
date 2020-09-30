---
title: Securing infrastructure with Zero Trust
description: Infrastructure represents a critical threat vector. A Zero Trust strategy makes it easier for you to develop, test, deliver, monitor, control, and support IT services.
ms.date: 09/01/2020
ms.service: security
author: Kellylorenebaker
ms.author: v-kbaker
ms.topic: conceptual
---

# Secure infrastructure with Zero Trust

:::image type="icon" source="./media/icon-data-storage-disks-medium.png":::

Infrastructure represents a critical threat vector. IT Infrastructure, whether on-premises or multi-cloud, is defined as all the hardware (physical, virtual, containerized), software (open source, first- and third-party, PaaS, SaaS), micro-services (functions, APIs), networking infrastructure, facilities, etc. that are required to develop, test,
deliver, monitor, control, or support IT services. It is an area where Microsoft has invested tremendous resources to develop a comprehensive set of capabilities to secure your future cloud and on-premises infrastructure.

Modern security with an end-to-end Zero Trust strategy makes it easier for you to: 

-  Assess for version.
-  Perform configuration management.
-  Employ Just-In-Time and Just-Enough-Access (JIT/JEA) administrative privileges to harden defenses.
-  Use telemetry to detect attacks and anomalies.
-  Automatically block and flag risky behavior and take protective actions.

Just as importantly, Microsoft Azure Blueprints and related capabilities ensure that resources are designed, implemented, and sustained in ways that conform to an organization's policies, standards, and requirements.

Azure Blueprints, Azure Policies, Azure Security Center, Azure Sentinel, and Azure Sphere can greatly contribute to improving the security of your deployed infrastructure and enable a different approach to defining, designing, provisioning, deploying, and monitoring your infrastructure.

:::image type="content" source="./media/diagram-infrastructure-5-elements.png" alt-text="A repeating circular diagram of 5 elements: Assess compliance, Observe gaps, Author, Test, and Deploy." border="false":::


## Infrastructure Zero Trust deployment objectives

> [!TIP]
> Before most organizations start the Zero Trust journey, their approach to infrastructure security is characterized by the following:
> 
> -  Permissions are managed manually across environments.
> -  Configuration management of VMs and servers on which workloads are running.



<table border="0">
   <tr>
      <td colspan="2">
         <p>When implementing an end-to-end Zero Trust framework for managing and monitoring your infrastructure, we recommend you focus first on these <b>initial deployment objectives</b>:</p>
	  </td>
   </tr>
   <tr>
      <td>
		 <p><img src="./media/icon-initial-deployment-small.png" alt="List icon with one checkmark."></p>
      </td>
      <td>
		 <p><b>I.</b> <a href="#i-workloads-are-monitored-and-alerted-to-abnormal-behavior">Workloads are monitored and alerted to abnormal behavior.</a></p>
	     <p><b>II.</b> <a href="#ii-every-workload-is-assigned-an-app-identityand-configured-and-deployed-consistently">Every workload is assigned an app identity—and configured and deployed consistently.</a></p>
		 <p><b>III.</b> <a href="#iii-human-access-to-resources-requires-just-in-time">Human access to resources requires Just-In-Time.</a></p>
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
         <p><b>IV.</b> <a href="#iv-unauthorized-deployments-are-blocked-and-alert-is-triggered">Unauthorized deployments are blocked, and alert is triggered.</a></p>
         <p><b>V.</b> <a href="#v-granular-visibility-and-access-control-are-available-across-workloads">Granular visibility and access control are available across workloads.</a></p>
         <p><b>VI.</b> <a href="#vi-user-and-resource-access-segmented-for-each-workload">User and resource access segmented for each workload.</a></p>
      </td>
   </tr>
</table>

## Infrastructure Zero Trust deployment guide

This guide will walk you through the steps required to secure your infrastructure following the principles of a Zero Trust security framework.

Before you get started, ensure you've met these baseline infrastructure deployment objectives.  
  
<div class="alert">
   <p><b>Setting the Microsoft Tenant Baseline</b></p>
   <p>A prioritized baseline should be set for how your Infrastructure is managed. Leveraging industry guidance such as NIST 800-53, you can derive a set of requirements for managing your infrastructure. At Microsoft, we have set a minimal baseline to the following list of requirements:</p>
   <ul>
      <li>
         <p>Access to data, networks, services, utilities, tools, and applications must be controlled by authentication and authorization mechanisms.</p>
      </li>
      <li>
         <p>Data must be encrypted in transit and at rest.</p>
      </li>
      <li>
         <p>Restrict network traffic flows.</p>
      </li>
      <li>
         <p>Security team visibility into all assets.</p>
      </li>
      <li>
         <p>Monitoring and auditing must be enabled and correctly configured according to prescribed organizational guidance.</p>
      </li>
      <li>
         <p>Anti-malware must be up to date and running.</p>
      </li>
      <li>
         <p>Vulnerability scans must be performed, and vulnerabilities remediated, according to prescribed organizational guidance.</p>
      </li>
   </ul>
   <p>In order to measure and drive compliance to this minimal—or our expanded—baseline, we start with getting visibility at the Tenant level, and across your on-prem environments, by applying a Security Reader role across the Azure Tenant. With the Security Reader role in place, it can gain additional visibility through Azure Security Center and Azure Policies that can be used to apply industry baselines (e.g., Azure CIS, PCI, ISO 27001) or a custom baseline that your organization has defined.</p>
</div>


### Permissions are managed manually across environments

From the tenant level down to the individual resources within each resource group ad subscription, appropriate role-based access controls must be applied.

> [!TIP]
> [Learn about implementing an end-to-end identity Zero Trust strategy](https://aka.ms/ZTIdentity).


#### Configuration management of VMS and servers on which workloads are running

Just as we have managed our on-prem data center environment, we must also ensure that we are effectively managing our cloud resources. The benefit of leveraging Azure is the ability to manage all your VMs from one platform using [Azure Arc](https://azure.microsoft.com/services/azure-arc/) (preview). Using Azure Arc, you can extend your Security Baselines from [Azure Policy](https://docs.microsoft.com/azure/governance/policy/overview), your [Azure Security Center](https://azure.microsoft.com/services/security-center)
(ASC) policies, and Secure Score evaluations, as well as logging and monitoring all your resources in one place. Below are some actions for getting started.


##### Implement [Azure Arc (preview)](https://azure.microsoft.com/services/azure-arc/)

[Azure Arc](https://azure.microsoft.com/services/azure-arc/) allows organizations to extend the familiar security controls of Azure to on-premises and the edge of the organization's infrastructure. Administrators have several options for connecting on-premises resources to Azure Arc. These include Azure Portal, PowerShell, and Windows Installation with Service Principal scripting. 

[Learn more about these techniques](https://docs.microsoft.com/azure/azure-arc/).


##### Apply security baselines through Azure Policy, including application of in-guest policies

Enabling [ASC Standard](https://docs.microsoft.com/azure/security-center/security-center-get-started) will let you incorporate a set of baseline controls through Azure
Policy by incorporating the [Azure Policy built-in policy definitions for Azure Security Center](https://docs.microsoft.com/azure/security-center/policy-samples).
The set of baseline policies will be reflected in the [ASC secure score](https://docs.microsoft.com/azure/security-center/security-center-secure-score), where you can measure your compliance to those policies.

You can extend your coverage of policies beyond the ASC set and create custom policies if a built-in is not available. You and can also incorporate [Guest Configuration policies](https://docs.microsoft.com/azure/governance/policy/how-to/guest-configuration-create) which will measure compliance inside your guest VMs within your subscriptions.


##### Apply ASC Endpoint Protection and Vulnerability Management controls

Endpoint protection is essential to ensuring infrastructure remains secure and available. As part of any endpoint protection and vulnerability management strategy, you will be able to measure compliance centrally to ensure malware protection is enabled and configured through the [Endpoint protection assessment and recommendations in Azure Security Center](https://docs.microsoft.com/azure/security-center/security-center-endpoint-protection). 


<div class="alert">
   <p><b>Centralized visibility of your baseline across multiple subscriptions</b></p>
   <p>By applying the tenant reader roll, you can get visibility across your tenant of the status of each of the policies that are being evaluated as part of the ASC secure score, Azure Policy, and Guest Config policies. You funnel that to your organizational compliance dashboard for central reporting of the state of your tenant.</p>
</div>


Additionally, as part of ASC Standard, you can use the policy [Enable
the built-in vulnerability assessment solution on virtual machines (powered by Qualys)](https://docs.microsoft.com/azure/security-center/built-in-vulnerability-assessment)
to scan your VMs for vulnerabilities, and have those reflected directly in ASC. If you already have a Vulnerability scanning solution deployed in your enterprise, you can use the alternate policy Vulnerability assessment solution, which should be installed on your virtual machines for [Deploying a partner vulnerability scanning solution](https://docs.microsoft.com/azure/security-center/partner-vulnerability-assessment).

> [!TIP]
> [Learn about implementing an end-to-end Zero Trust strategy for endpoints](https://aka.ms/ZTEndpoints).


<br/><br/>
<!-- H2 heading, "Initial deployment objectives" -->
<!-- [v-gmoor, 2020-09-30] The following include worked fine in the release branch, but for some reason, the build considered the included icon image to be out of scope when we built this for the live branch. So, I am copying in the code from the include here to take the place of the include file until we can figure out that problem.
[!INCLUDE [H2 heading, Initial deployment objectives](./includes/deployment-objectives-initial.md)]
-->
<table border="0">
   <tr>
      <td>
	     <br/>
         <p><img src="media/icon-initial-deployment.png" alt="Checklist icon with one checkmark."></p>
      </td>
      <td>
         <h2>Initial deployment objectives</h2>
      </td>
   </tr>
</table>

Once you've met the baseline infrastructure objectives, you can focus on implementing a modern infrastructure with an end-to-end Zero Trust strategy.


### I. Workloads are monitored and alerted to abnormal behavior

When you create new infrastructure, you need to ensure that you also establish rules for monitoring and raising alerts. This is key for identifying when a resource is displaying unexpected behavior. 

**Enabling [Azure Security Center with Standard Tier](https://docs.microsoft.com/azure/security-center/security-center-get-started) (ASC)**, including the relevant bundles to cover your various resources (e.g., Container Registry, Kubernetes, IoT, Virtual Machines, etc.) is highly recommended.

For monitoring identities, we recommend **enabling [Azure Advanced Threat Protection](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp)
(A-ATP) and [Advanced Threat Analytics](https://docs.microsoft.com/advanced-threat-analytics/what-is-ata) (ATA)** in order to enable signal collection to identify, detect, and investigate advanced threats, compromised identities, and malicious insider actions directed at your organization.

Integrating these signals from ASC, A-ATP, ATA, and other monitoring and auditing systems with [Azure Sentinel](https://docs.microsoft.com/azure/sentinel/overview), a
cloud-native, security information event management (SIEM) and security orchestration automated response (SOAR) solution, will allow your Security Operations Center (SOC) to work from a single pane of glass to monitor security events across your enterprise.

> [!TIP]
> [Learn about implementing an end-to-end identity Zero Trust strategy](https://aka.ms/ZTIdentity).


### II. Every workload is assigned an app identity—and configured and deployed consistently

Microsoft recommends customers use a [policy](https://docs.microsoft.com/azure/governance/policy/tutorials/create-and-manage) that is assigned and enforced when creating resources/workloads. Policies can require tags be to applied to a resource upon creation, mandate resource group assignment, as well as restrict/direct technical characteristics, such as regions allowed, VM specifications (e.g., VM type, disks, network policies applied).

> [!TIP]
> [Learn about implementing an end-to-end Zero Trust strategy for applications](https://aka.ms/ZTApplications).


### III. Human access to resources requires Just-In-Time

Personnel should use administrative access sparingly. When administrative functions are required, users should receive temporary
administrative access.

Organizations should establish a [Protect the Administrator](https://www.microsoft.com/itshowcase/protecting-high-risk-environments-with-secure-admin-workstations)
program. Characteristics of these programs include:

-  Targeted reduction in the number of users with administrative permissions.
-  Auditing elevated permission accounts and roles.
-  Creating special High-Value Asset (HVA) infrastructure zones to reduce surface area.
-  Giving administrators special Secure Admin Workstations (SAWs) to reduce the likelihood of credential theft.

All of these items help an organization become more aware of how administrative permissions are being used, where these permissions are still necessary, and provide a roadmap for how to operate more securely.


<br/><br/>
<!-- H2 heading, "Additional deployment objectives" -->
<!-- [v-gmoor, 2020-09-30] The following include worked fine in the release branch, but for some reason, the build considered the included icon image to be out of scope when we built this for the live branch. So, I am copying in the code from the include here to take the place of the include file until we can figure out that problem.
[!INCLUDE [H2 heading, Additional deployment objectives](./includes/deployment-objectives-additional.md)]
-->
<table border="0">
   <tr>
      <td>
         <br/>
		 <p><img src="./media/icon-additional-deployment.png" alt="Checklist icon with two checkmarks."></p>
      </td>
      <td>
         <h2>Additional deployment objectives</h2>
      </td>
   </tr>
</table>


Once you've accomplished your initial three objectives, you can focus on additional objectives such as blocking unauthorized deployments.


### IV. Unauthorized deployments are blocked, and alert is triggered

When organizations move to the cloud, the possibilities are limitless. That's not always a good thing. For a variety of reasons, organizations need to be able to block unauthorized deployments and trigger alerts to make leaders and managers aware of the issues.

Microsoft Azure offers [Azure Blueprints](https://docs.microsoft.com/azure/governance/blueprints/overview) to govern how resources are deployed, ensuring that only approved
resources (e.g., ARM templates) can be deployed. Blueprints can ensure that resources which do not meet the Blueprint's policies or other rules are blocked from deployment. Actual or attempted Blueprint violation can raise alerts as needed and make notifications, activate webhooks or automation runbooks, or even create service management tickets.


### V. Granular visibility and access control are available across workloads

Microsoft Azure offers a variety of methods to achieve resource [visibility](https://aka.ms/ZTCrossPillars). From the Azure Portal, resource owners can set up many metric and log collection and analysis capabilities. This visibility can be used not only to feed security operations but can also to support computing efficiency and organizational objectives. These include capabilities like [VM Scale Sets](https://docs.microsoft.com/azure/virtual-machine-scale-sets/overview), which allow for the secure and efficient scaling out and scaling in of resources based on metrics.

On the access control side, [Role-Based Access Control (RBAC)](https://docs.microsoft.com/azure/role-based-access-control/overview) can be employed to assign permissions to resources. This allows permissions to be assigned and revoked uniformly at the individual and group levels by using a variety of built-in or custom roles.


### VI. User and resource access segmented for each workload

Microsoft Azure offers many ways to segment workloads to manage user and resource access. [Network segmentation](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/network-level-segmentation) is the overall approach, and, within Azure, resources can be isolated at the subscription level with Virtual networks (VNets), VNet peering rules, Network Security Groups (NSGs), Application Security Groups (ASGs), and Azure Firewalls. There are several design patterns to determine the best approach to segmenting workloads.

> [!TIP]
> [Learn about implementing an end-to-end Zero Trust strategy for your network](https://aka.ms/ZTNetwork).

## Products covered in this guide  
  
**Microsoft Azure**

[Azure Blueprints](https://azure.microsoft.com/services/blueprints/)

[Azure Policy](https://docs.microsoft.com/azure/governance/policy/overview)

[Azure Arc](https://azure.microsoft.com/services/azure-arc)

[Azure Security Center (ASC)](https://azure.microsoft.com/services/security-center)

[Azure Sentinel](https://azure.microsoft.com/services/azure-sentinel/)

[Azure Resource Manager (ARM) templates](https://docs.microsoft.com/azure/azure-resource-manager/templates/overview)

## Conclusion

Infrastructure is central to a successful Zero Trust strategy. For further information or help with implementation, please contact your Customer Success team, or continue to read through the other chapters of this guide, which spans all Zero Trust pillars.

<br/><br/>
<!-- [v-gmoor, 2020-09-30]: The following include is constructed correctly, but it displays only a couple of the icons. The build claims that the others are outside of the build scope, even though they are located in the same path. So, I've copied the code for the navbar into each article, which I hope is a temporary fix.
[!INCLUDE [navbar, bottom](./includes/navbar-bottom.md)]
-->
**The Zero Trust deployment guide series**

:::row:::
   :::column:::
[![Icon for the introduction](./media/icon-introduction-navbar.png)](https://aka.ms/ZTDeploymentGuideIntroduction)
   :::column-end:::
   :::column:::
[![Icon for identity](./media/icon-identity-navbar.png)](https://aka.ms/ZTIdentity)
   :::column-end:::
   :::column:::
[![Icon for endpoints](./media/icon-endpoints-navbar.png)](https://aka.ms/ZTDevices)
   :::column-end:::
   :::column:::
[![Icon for applications](./media/icon-applications-navbar.png)](https://aka.ms/ZTApplications)
   :::column-end:::
   :::column:::
[![Icon for data](./media/icon-data-navbar.png)](https://aka.ms/ZTData)
   :::column-end:::
   :::column:::
[![Icon for infrastructure](./media/icon-infrastructure-navbar.png)](https://aka.ms/ZTInfrastructure)
   :::column-end:::
   :::column:::
[![Icon for networks](./media/icon-networks-navbar.png)](https://aka.ms/ZTNetwork)
   :::column-end:::
   :::column:::
[![Icon for visibility, automation, orchestration](./media/icon-visibility-automation-orchestration-navbar.png)](https://aka.ms/ZTCrossPillars)
   :::column-end:::
:::row-end:::

