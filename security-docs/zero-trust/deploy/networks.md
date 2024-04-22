---
title: Secure networks with Zero Trust
description: Due to the cloud, mobile devices, and other endpoints that expand boundaries and change paradigms, there isn't necessarily a contained/defined network to secure. Instead, there is a vast portfolio of devices and networks, all linked by the cloud.
ms.date: 09/30/2020
ms.service: security
author: TerryLanfear
manager: rKarlin
ms.author: terrylan
ms.topic: conceptual
ms.collection:
  - zerotrust-pillar
---

# Secure networks with Zero Trust

:::image type="icon" source="../media/icon-networks-medium.png":::

Big data presents new opportunities to derive new insights and gain a competitive edge. We are moving away from an era where networks were clearly defined and usually specific to a certain location. The cloud, mobile devices, and other [endpoints](https://aka.ms/ZTEndpoints) expand the boundaries and change the paradigm. Now there isn't necessarily a contained/defined network to secure. Instead, there is a vast portfolio of devices and networks, all linked by the cloud.

Instead of believing everything behind the corporate firewall is safe, an end-to-end Zero Trust strategy assumes breaches are inevitable. That means you must verify each request as if it originates from an uncontrolled network—[identity](https://aka.ms/ZTIdentity) management plays a crucial role in this.

In the Zero Trust model, there are three key objectives when it comes to securing your networks:

- Be ready to handle attacks before they happen. 

- Minimize the extent of the damage and how fast it spreads.

- Increase the difficulty of compromising your cloud footprint.

To make this happen, we follow three Zero Trust principles:

- **Verify explicitly.** Always authenticate and authorize based on all available data points, including user identity, location, device health, service or workload, data classification, and anomalies.

- **Use least-privileged access.** Limit user access with Just-In-Time and Just-Enough-Access (JIT/JEA), risk-based adaptive polices, and data protection to protect both data and productivity.

- **Assume breach.** Minimize blast radius for breaches and prevent lateral movement by segmenting access by network, user, devices, and application awareness. Verify all sessions are encrypted end to end. Use analytics to get [visibility](https://aka.ms/ZTCrossPillars), drive threat detection, and improve defenses.


## Network Zero Trust deployment objectives

<div class="alert">
   <p><b>Before</b> most organizations <b>start their Zero Trust journey</b>, they have network security that is characterized by the following:</p>
   <ul>
      <li>
         <p>Few network security perimeters and open, flat networks.</p>
      </li>
      <li>
         <p>Minimal threat protection and static traffic filtering.</p>
      </li>
      <li>
         <p>Unencrypted internal traffic.</p>
      </li>
   </ul>
</div>




<table border="0">
   <tr>
      <td colspan="2">
         <p>When implementing an end-to-end Zero Trust framework for securing networks, we recommend you focus first on these <b>initial deployment objectives</b>:</p>
	  </td>
   </tr>
   <tr>
      <td>
		 <p><img src="../media/icon-initial-deployment-small.png" alt="List icon with one checkmark."></p>
      </td>
      <td>
		 <p><b>I.</b> <a href="#i-network-segmentation-many-ingressegress-cloud-micro-perimeters-with-some-micro-segmentation">Network segmentation: Many ingress/egress cloud micro-perimeters with some micro-segmentation.</a></p>
	     <p><b>II.</b> <a href="#ii-threat-protection-cloud-native-filtering-and-protection-for-known-threats">Threat protection: Cloud native filtering and protection for known threats.</a></p>
		 <p><b>III.</b> <a href="#iii-encryption-user-to-app-internal-traffic-is-encrypted">Encryption: User-to-app internal traffic is encrypted.</a></p>
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
         <p><b>IV.</b> <a href="#iv-network-segmentation-fully-distributed-ingressegress-cloud-micro-perimeters-and-deeper-micro-segmentation">Network segmentation: Fully distributed ingress/egress cloud micro-perimeters and deeper micro-segmentation.</a></p>
         <p><b>V.</b> <a href="#v-threat-protection-machine-learning-based-threat-protection-and-filtering-with-context-based-signals">Threat protection: Machine learning-based threat protection and filtering with context-based signals.</a></p>
         <p><b>VI.</b> <a href="#vi-encryption-all-traffic-is-encrypted">Encryption: All traffic is encrypted.</a></p>
        <p><b>VII.</b> <a href="#vii-discontinue-legacy-network-security-technology">Discontinue legacy network security technology.</a></p>
      </td>
   </tr>
</table>

## Networking Zero Trust deployment guide

This guide will walk you through the steps required to secure your networks following the principles of a Zero Trust security framework.


<br/><br/>
<!-- H2 heading, "Initial deployment objectives" -->
[!INCLUDE [H2 heading, Initial deployment objectives](../includes/deployment-objectives-initial.md)]



### I. Network segmentation: Many ingress/egress cloud micro-perimeters with some micro-segmentation

Organizations should not just have one single, big pipe in and out of their network. In a Zero Trust approach, networks are instead segmented into smaller islands where specific workloads are contained. Each segment has its own ingress and egress controls to minimize the "blast radius" of unauthorized access to data. By implementing software-defined perimeters with granular controls, you increase the difficulty for unauthorized actors to propagate throughout your network, and so reduce the lateral movement of threats.

There is no architecture design that fits the needs of all organizations. You have the option between a few [common design patterns](https://www.microsoft.com/security/blog/2020/06/15/zero-trust-part-1-networking/) for segmenting your network according to the Zero Trust model.

In this deployment guide, we'll walk you through the steps to achieve one of those designs: Micro-segmentation.

With micro-segmentation, organizations can move beyond simple centralized network-based perimeters to comprehensive and distributed segmentation using software-defined micro-perimeters.  


#### Applications are partitioned to different Azure Virtual Networks (VNets) and connected using a hub-spoke model

:::image type="content" source="../media/diagram-network-hub-spoke-two-regions.png" alt-text="Diagram of two virtual networks connected in a hub-and-spoke model." border="false":::

Follow these steps:

1.  [Create dedicated virtual networks](/azure/virtual-network/quick-create-portal) for different applications and/or application components.

2.  Create a central VNet to set up the security posture for inter-app connectivity and connect the app VNets in [a hub-and-spoke architecture](/azure/architecture/reference-architectures/hybrid-networking/hub-spoke).

3.  [Deploy Azure Firewall](/azure/firewall/deploy-ps) in the hub VNet to inspect and govern traffic between the VNets.


### II. Threat protection: Cloud native filtering and protection for known threats

Cloud applications that have opened up endpoints to external environments, such as the internet or your on-premises footprint, are at risk of attacks coming in from those environments. It is therefore imperative that you scan the traffic for malicious payloads or logic.

These types of threats fall into two broad categories:

- **Known attacks**. Threats that have been discovered by your software provider or the larger community. In such cases, the attack signature is available and you need to ensure that each request is checked against those signatures. The key is to be able to quickly update your detection engine with any newly identified attacks.

- **Unknown attacks.** These are threats that don't quite match against any known signature. These types of threats include zero-day vulnerabilities and unusual patterns in request traffic. The ability to detect such attacks depends on how well your defenses know what's normal and what is not. Your defenses should be constantly learning and updating such patterns as your business (and associated traffic) evolves.

Take these steps to protect against known threats:

1.  **For endpoints with HTTP/S traffic**, protect using [Azure Web Application Firewall (WAF)](/azure/web-application-firewall/overview) by:

    1.  Turning on the default ruleset or [OWASP top 10](https://owasp.org/www-project-top-ten/) protection ruleset to protect against known web-layer attacks

    1.  Turning on the bot protection ruleset to prevent malicious bots from scraping information, conducting credential stuffing, etc.

    1.  Adding custom rules to protect against threats specific to your business.

    You can use one of two options:

    - [Azure Front Door](/azure/frontdoor/front-door-overview)

        1. [Create a Web Application Firewall policy on Azure Front Door](/azure/web-application-firewall/afds/waf-front-door-create-portal).

        1. [Configure bot protection for Web Application Firewall](/azure/web-application-firewall/afds/waf-front-door-policy-configure-bot-protection).

        1. [Custom rules for Web Application Firewall](/azure/web-application-firewall/afds/waf-front-door-custom-rules-powershell).

    - [Azure Application Gateway](/azure/application-gateway/overview)

       1. [Create an application gateway with a Web Application Firewall](/azure/web-application-firewall/ag/application-gateway-web-application-firewall-portal).

       1. [Configure bot protection for Web Application Firewall](/azure/web-application-firewall/ag/bot-protection).

       1. [Create and use Web Application Firewall v2 custom rules.](/azure/web-application-firewall/ag/create-custom-waf-rules).


2.  **For all endpoints (HTTP or not)**, front with [Azure Firewall](/azure/firewall/overview) for threat intelligence-based filtering at Layer 4:

    1.  [Deploy and configure Azure Firewall](/azure/firewall/tutorial-firewall-deploy-portal) using the Azure portal.

    1.  [Enable threat intelligence-based filtering](/azure/firewall/threat-intel) for your traffic.

    > [!TIP]
    > [Learn about implementing an end-to-end Zero Trust strategy for endpoints](https://aka.ms/ZTEndpoints).


### III. Encryption: User-to-app internal traffic is encrypted

The third initial objective to focus on is adding encryption to ensure user-to-app internal traffic is encrypted.

Follow these steps:

1.  Enforce HTTPS-only communication for your internet facing web applications by [redirecting HTTP traffic to HTTPS using Azure Front Door](/azure/frontdoor/front-door-how-to-redirect-https).

2.  Connect remote employees/partners to Microsoft Azure using the [Azure VPN Gateway](/azure/vpn-gateway/vpn-gateway-about-vpngateways).

    1.  [Turn on encryption](/azure/vpn-gateway/vpn-gateway-security-controls#data-protection) for any point-to-site traffic in Azure VPN Gateway service.

3.  Access your Azure virtual machines securely using encrypted communication via [Azure Bastion](/azure/bastion/bastion-overview).

    1.  [Connect using SSH to a Linux virtual machine](/azure/bastion/bastion-connect-vm-ssh).

    1.  [Connect using RDP to a Windows virtual machine](/azure/bastion/bastion-connect-vm-rdp).

> [!TIP]
> [Learn about implementing an end-to-end Zero Trust strategy for applications](https://aka.ms/ZTApplications).


<br/><br/>
<!-- H2 heading, "Additional deployment objectives" -->
[!INCLUDE [H2 heading, Additional deployment objectives](../includes/deployment-objectives-additional.md)]



### IV. Network segmentation: Fully distributed ingress/egress cloud micro-perimeters and deeper micro-segmentation

Once you've accomplished your initial three objectives, the next step is to further segment your network.


#### Partition app components to different subnets

:::image type="content" source="../media/diagram-azure-region-virtual-network-servers.png" alt-text="Diagram of a virtual network of servers in the Azure region." border="true":::


Follow these steps:

1.  Within the VNet, [add virtual network subnets](/azure/virtual-network/virtual-network-manage-subnet) so that discrete components of an application can have their own perimeters.

2.  [Apply network security group rules](/azure/virtual-network/tutorial-filter-network-traffic#create-security-rules) to allow traffic only from the subnets that have an app subcomponent identified as a legitimate communications counterpart.


#### Segment and enforce the external boundaries

:::image type="content" source="../media/diagram-servers-devices-boundaries-azure-vpn.png" alt-text="Diagram of a servers and devices with connections across boundaries." border="true":::

Follow these steps, depending on the type of boundary:

##### Internet boundary

1.  If internet connectivity is required for your application that needs to be routed via the hub VNet, [update the network security group rules](/azure/virtual-network/tutorial-filter-network-traffic) in hub VNet to allow internet connectivity.

2.  [Turn on Azure DDoS Protection Standard](/azure/virtual-network/manage-ddos-protection#enable-ddos-for-an-existing-virtual-network)
    to protect the hub VNet from volumetric network layer attacks.

3.  If your application uses HTTP/S protocols, [turn on Azure Web Application Firewall](/azure/web-application-firewall/afds/waf-front-door-custom-rules-powershell) to protect against Layer 7 threats.


##### On-premises boundary

1.  If your app needs connectivity to your on-premise data center, [use Azure ExpressRoute](/azure/expressroute/expressroute-howto-circuit-portal-resource-manager) of Azure VPN [for connectivity to your hub VNet](/azure/vpn-gateway/vpn-gateway-howto-site-to-site-resource-manager-portal).

2.  [Configure the Azure Firewall](/azure/firewall/tutorial-hybrid-ps) in the hub VNet to inspect and govern traffic.


##### PaaS services boundary

 - When using Azure-provided PaaS services (e.g., Azure Storage, [Azure Cosmos DB](/azure/private-link/create-private-endpoint-cosmosdb-portal),
    or [Azure Web App](/azure/private-link/create-private-endpoint-webapp-portal), use the [PrivateLink](/azure/private-link/create-private-link-service-portal) connectivity option to ensure all data exchanges are over the private IP space and the traffic never leaves the Microsoft network.

> [!TIP]
> [Learn about implementing an end-to-end Zero Trust strategy for data](https://aka.ms/ZTData).


### V. Threat protection: Machine learning-based threat protection and filtering with context-based signals

For further threat protection, turn on [Azure DDoS Protection Standard](/azure/virtual-network/ddos-protection-overview) to constantly monitor your Azure-hosted application traffic, use ML-based frameworks to baseline and detect volumetric traffic floods, and apply automatic mitigations.

Follow these steps:

1.  [Configure and manage](/azure/virtual-network/manage-ddos-protection) Azure DDoS Protection Standard.

1.  [Configure alerts](/azure/virtual-network/manage-ddos-protection#configure-alerts-for-ddos-protection-metrics) for DDoS protection metrics.


### VI. Encryption: All traffic is encrypted

Finally, complete your network protection by ensuring that all traffic is encrypted.

Follow these steps:

1.  [Encrypt application backend traffic](/azure/vpn-gateway/vpn-gateway-ipsecikepolicy-rm-powershell) between virtual networks.

1.  Encrypt traffic between on-premises and cloud:

    1.  [Configure a site-to-site VPN](/azure/expressroute/site-to-site-vpn-over-microsoft-peering) over ExpressRoute Microsoft peering.

    1.  [Configure IPsec transport mode](/azure/expressroute/expressroute-howto-ipsec-transport-private-windows) for ExpressRoute private peering.

<a name='discontinue-legacy-network'></a>
### VII. Discontinue legacy network security technology

Discontinue the use of signature-based Network Intrusion Detection/Network Intrusion Prevention (NIDS/NIPS) Systems and Network Data Leakage/Loss Prevention (DLP).

The major cloud service providers already filter for malformed packets and common network layer attacks, so there's no need for a NIDS/NIPS solution to detect those. In addition, traditional NIDS/NIPS solutions are typically driven by signature-based approaches (which are considered outdated) and are easily evaded by attackers and typically produce a high rate of false positives.

Network-based DLP is decreasingly effective at identifying both inadvertent and deliberate data loss. The reason for this is that most modern protocols and attackers use network-level encryption for inbound and outbound communications. The only viable workaround for this is "SSL-bridging" which provides an "authorized man-in-the-middle" that terminates and then reestablishes encrypted network connections. The SSL-bridging approach has fallen out of favor because of the level of trust required for the partner running the solution and the technologies that are being used.

Based on this rationale, we offer an all-up recommendation that you discontinue use of these legacy network security technologies. However, if your organizational experience is that these technologies have had a palpable impact on preventing and detecting real attacks, you can consider porting them to your cloud environment.

## Products covered in this guide

**Microsoft Azure**

[Azure Networking](/azure/networking/)

[Virtual Networks and Subnets](/azure/virtual-network/virtual-networks-overview)

[Network Security Groups](/azure/virtual-network/security-overview)
and [Application Security Groups](/azure/virtual-network/application-security-groups)

[Azure Firewall](/azure/firewall/overview)

[Azure DDoS Protection](/azure/virtual-network/ddos-protection-overview)

[Azure Web Application Firewall](/azure/web-application-firewall/ag/ag-overview)

[Azure VPN Gateway](/azure/vpn-gateway/vpn-gateway-about-vpngateways)

[Azure ExpressRoute](/azure/expressroute/expressroute-introduction)

[Azure Network Watcher](/azure/network-watcher/network-watcher-monitoring-overview)

## Conclusion

Securing networks is central to a successful Zero Trust strategy. For further information or help with implementation, please contact your Customer Success team or continue to read through the other chapters of this guide, which spans all Zero Trust pillars.


<br/><br/>
<!-- Include the nav bar. -->
[!INCLUDE [navbar, bottom](../includes/navbar-bottom.md)]
