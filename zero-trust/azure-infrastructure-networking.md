---
title: Apply Zero Trust principles to a hub virtual network in Azure 
description: Learn how to secure a hub virtual network with Zero Trust for access to Azure infrastructure.  
ms.date: 10/27/2022
ms.service: security
author: brendacarter
ms.author: bcarter
ms.topic: conceptual
ms.collection: 
  - msftsolution-accesscontrol
  - msftsolution-scenario
  - zerotrust-solution
---

# Apply Zero Trust principles to a hub virtual network in Azure 

The best way to deploy a hub network for Zero Trust is to leverage the Azure Landing Zone materials to deploy a feature complete hub network, and then tailor it to your specific configuration expectations.

This article provides steps for how to take an existing hub network and ensure you are ready for a Zero Trust methodology. It assumes that you have used the the ALZ-Bicep [hubNetworking](https://github.com/Azure/ALZ-Bicep/tree/main/infra-as-code/bicep/modules/hubNetworking) module to rapidly deploy a hub network, or have deployed some other hub network with similar resources.

Using a separate connectivity hub connected to isolated workplace spokes is an anchor pattern in Azure secure networking, and helps support the Zero Trust principles in play.<br>
This article is a part of a series of articles that demonstrate how to apply the principles of Zero Trust across an environment in Azure that includes a hub virtual network to support an IaaS workload. For more information, see [Overview – Apply Zero Trust principles to Azure infrastructure](azure-infrastructure-overview.md).

This article describes how to deploy a hub network for Zero Trust by mapping the principles of Zero Trust in the following ways.

|Zero Trust Principle | Met by |
| --- | --- |
| Verify explicitly  | Use Azure Firewall with SSL inspection to verify risk and threats based on all available data.  |
| Use least privileged access  | Each spoke has no access to other spokes unless the traffic is routed through the Firewall. The Firewall is set to deny by default, allowing only authorized rules to execute.  |
| Assume breach  | In the event of a compromise or breach of one application/workload, it will have limited ability to spread due to the Azure Firewall performing inspection and only allowing approved rules. Only resources in the same workload would be exposed to the breach in the same application.  |

## Reference architecture
The following diagram illustrates the reference architecture. The Hub virtual network is highlighted in red. For more information about this architecture, see [Overview – Apply Zero Trust principles to Azure infrastructure](azure-infrastructure-overview.md).

:::image type="content" source="media/hub/azure-infra-hub-architecture-1.png" alt-text="Screenshot of hub vnet reference architecture." lightbox="media/hub/azure-infra-hub-architecture-1.png":::

For this reference architecture, there are a number of ways you can deploy the resources across the Azure subscription. The reference architecture shows one recommendation—isolating all resources for the hub virtual network within a dedicated resource group. The resources for the spoke virtual network are also illustrated, for comparison. This model works well if different teams are given responsibility for these different areas.

In the illustration:

- A 'hub' virtual network includes components to support access to other apps and services within the Azure environment. These resources include:
  - Azure Firewall Premium 
  - Azure Bastion 
  - VPN Gateway
  - DDOS Protection 
- The hub virtual network, as illustrated in the reference architecture, provides access from these components to the IaaS app hosted in the spoke virtual network.

The Cloud Adoption Framework gives guidance on organizing for cloud adoption, see: [Manage organization alignment - Cloud Adoption Framework | Microsoft Learn](/azure/cloud-adoption-framework/organize/)

The following table lists the resources that are deployed for the hub virtual network.

|Resource  |Comment  |
|---------|---------|
|Azure Virtual Network     | Part of the illustration        |
|Azure firewall     | Part of the illustration        |
|Azure firewall policy     |Part of Azure firewall (implicit in the illustration)        |
|Public IP address for Azure firewall     | Part of Azure firewall (implicit in the illustration        |
|Bastion     | Part of the illustration        |
|Virtual Network gateway     | Part of the illustration        |
|Public IP address for VPN gateway     | Part of the VPN gateway (implicit in the illustration)        |
|Route table (also called UDR)    | Part of the VNET (implicit in the illustration    )         |

The following diagram illustrates the logical architecture of these components within an Azure subscription. This is one way of organizing these elements within the subscription. Your organization might choose to organize these in a different way.

:::image type="content" source="media/hub/azure-infra-hub-subscription-architecture-2.png" alt-text="Illustration of (hub vnet) Azure Subscription.":::

In the illustration:
- The resources for the hub virtual network are contained within a dedicated resource group. If you selected Azure DDoS Plan to be deployed as a part of the resources, that will be included as well.
- The resources within the spoke virtual network are contained within a dedicated resource group.

Depending on your deployment, you may also note that there can be a deployment of an array for Private DNS Zones used for Private Link DNS resolution. These are used to secure PaaS resources with Private Endpoints, which will be detailed in a future section.<br>
Note that it deploys both a VPN Gateway and an ExpressRoute Gateway. You may not need both, so feel free to delete whichever one is not needed for your scenario, or turn off during deployment.

## In this article

This article provides recommendations for securing the components of a hub virtual network.

| **Step**   | **Task**   |
| --- | --- |
| 1  | Secure Azure Firewall Premium  |
| 2  | Deploy Azure DDoS Protection Standard  |
| 3  | Configure network gateway routing to the firewall  |
| 4.   | Threat protection   |

As a part of your deployment, you will want to make specific selections. It should be noted that these are not the defaults for automated deployments, due to their additional costs.<br>
Prior to the deployment, you should review the costs.<br>
Operating the connectivity hub as deployed still provides significant value for isolation and inspection. So, if your organization is not ready to spend for these advanced features, you can deploy a reduced functionality hub and make these adjustments later.

## Step 1. Secure Azure Firewall Premium

Azure Firewall Premium plays a starring role in helping you secure your Azure infrastructure for Zero Trust, as described in the following table.

| Zero Trust Principle   | Met by   |
| --- | --- |
| Verify explicitly  | By inspecting both the traffic source and the nature of the traffic, Azure Firewall verifies explicitly that traffic itself is safe (in addition to applying access control rules).  |
| Use least privileged access  | By providing a firewall between distinct applications, and inspecting all traffic regardless of its source, Azure Firewall can reduce access between network segments.  |
| Assume breach  | Because of this segmentation, individual network segments become their own blast radius. The firewall can prevent a compromise in one network segment from spreading into others.  |

As a part of the deployment, select Azure Firewall Premium as the SKU for Azure Firewall. This will require the management policy generated to be deployed as a premium policy as well.<br>
Changing the SKU of the firewall involves recreating the firewall, and often the policy as well. As a result, start with Azure Firewall if possible. Or, be prepared for redeployment activities to replace the existing firewall.

### Why Azure Firewall Premium?

Azure Firewall Premium provides [advanced features](/azure/firewall/premium-features) for inspecting traffic.

Most significant are the following TLS inspection options:

- **Outbound TLS Inspection** which protects against malicious traffic that is sent from an internal client to the internet. This helps identify when a client has been breached, and if it is trying to ship data outside of your network or establish a connection to a remote controller.
- **East-West TLS Inspection** which protects against malicious traffic sent from within Azure to other parts of Azure or to your non-Azure networks. This helps identify attempts for a breach to expand and spread from one blast radius to another.
- **Inbound TLS Inspection**  which protects resources in Azure from malicious requests that arrive from outside the Azure network. Azure Application Gateway is needed to make this available.

The Inbound TLS inspection for resources should be used whenever possible. As Application Gateway provides HTTP and HTTPS traffic only, for some scenarios it can't be used - such as SQL or RDP traffic. Other services often have their own threat protection options that should be used to provide _verify explicitly_ controls for those services. You can review [Security baselines for Azure overview | Microsoft Learn](/security/benchmark/azure/security-baselines-overview) to understand the threat protection options for these services.

These scenarios have specific certificate considerations. You can read more about them in the article on [Azure Firewall Premium certificates](/azure/firewall/premium-certificates).<br>
Without TLS inspection, Azure Firewall has no visibility into the data that flows in the encrypted TLS tunnel, and so its protection is more limited.

In addition to the customer defined allow/deny rules, the Azure Firewall is still able to apply [threat intelligence-based filtering](/azure/firewall/threat-intel). Threat intelligence-based filtering uses known-bad Ips and domains to identify traffic that poses a risk. This filtering occurs prior to any other rules, which means even if the access was allowed by your defined rules, the traffic can be stopped.

Azure Firewall Premium also has enhanced options for URL filtering and web category filtering, allowing for more fine tuned roles.

Threat intelligence can be set to Alert, to notify you when this traffic occurs, but to allow it through. However, for this Zero Trust deployment, it should be set to Deny.

### Configure Azure Firewall Premium for Zero Trust

To configure Azure Firewall Premium to a Zero Trust configuration, make the following changes.

1. Enable Threat Intelligence in Alert and Deny Mode:

    1. Navigate to the Firewall Policy and select **Threat Intelligence**.
    1. In **Threat intelligence mode**, select **Alert and deny**.
    1. Select **Save**.

:::image type="content" source="media/hub/hub-threat-intelligence.png" alt-text="Screenshot of enable threat intelligence." lightbox="media/hub/hub-threat-intelligence.png":::

2. Enable TLS inspection:

    1. Prepare a certificate to be used, stored in a Key Vault, or plan to auto-generate a certificate with a managed identity. You can review these options for [Azure Firewall Premium certificates](/azure/firewall/premium-certificates) to select the option for your scenario.
    1. Navigate to the Firewall Policy and select **TLS Inspection**.
    1. Select **Enabled**.
    1. Either select a Managed Identity to be used to generate certificates, or select the Key Vault and Certificate.
    1. Then select **Save**.

:::image type="content" source="media/hub/hub-tls-inspection.png" alt-text="Screenshot of enable TLS inspection." lightbox="media/hub/hub-tls-inspection.png":::

3. Enable IDPS:

    1. Navigate to the Firewall Policy and select **IDPS**.
    1. Select **Alert and deny**.
    1. Then select **Apply**.

:::image type="content" source="media/hub/hub-idps.png" alt-text="Screenshot of enable IDPS." lightbox="media/hub/hub-idps.png":::

### Additional configuration

With the Azure Firewall Premium configured, you can now perform the following configurations:

- Configure Application Gateways to route traffic to your Azure Firewall, by assigning the appropriate route tables and [following this guidance](/azure/architecture/example-scenario/gateway/application-gateway-before-azure-firewall#hub-and-spoke-example).
- Create alerts for firewall events and metrics, [following these instructions](/azure/firewall/firewall-diagnostics).
- Deploy the [Azure Firewall Workbook](/azure/firewall/firewall-workbook) to visualize events.
- Configure URL and [Web category filtering](/azure/firewall/web-categories), if needed. As Azure Firewall is deny by default, this configuration is needed only if the Azure Firewall needs to grant outbound internet access broadly. However, use additional verifications to determine connections.

## Step 2. Deploy Azure DDoS Protection Standard

As a part of the deployment, you will want to deploy an Azure DDoS Protection Standard Policy. This increases the default protection provided on the Azure Platform, as described in the following table.

| Zero Trust Principle  | Met by   |
| --- | --- |
| Verify explicitly  | Monitors traffic and uses ML-based frameworks to detect traffic floods.  |
| Use least privileged access  | Prevent traffic flooding without controlled authorization.  |
| Assume breach  | Can monitor traffic to protect from different attack scenarios  |

As the policy that is created can be deployed to existing resources, you can add this protection after the initial deployment without requiring the redeployment of resources.

### Why Azure DDoS Protection Standard?

Azure DDoS Protection Standard has [increased benefits](/azure/ddos-protection/ddos-protection-overview) over the default DDoS Protection. Specifically for Zero Trust, you can:

- Have access to mitigation reports, flow logs, and metrics.
- Have application based mitigation policies.
- Have access to DDoS rapid response support in the event of a DDoS attack.

While automatic detection and automatic mitigation are both a part of the DDoS Protection Basic that is enabled by default, these features are only available with DDoS Standard.

### Configure Azure DDoS Protection Standard

As there are no "Zero Trust Specific" configurations for DDoS Protection Standard, you can follow the resource specific guides for this solution:

- [Create a DDoS Protection Plan](/azure/ddos-protection/manage-ddos-protection)
- [Configure Alerting](/azure/ddos-protection/alerts)
- [Configure Diagnostic Logging](/azure/ddos-protection/diagnostic-logging)
- [Configure Telemetry](/azure/ddos-protection/telemetry)

## Step 3. Configure network gateway routing to the firewall

This configuration contributes to Zero Trust in the following ways.

|Zero Trust Principle | Met by |
| --- | --- |
| Verify explicitly  | By inspecting traffic flowing to and from the VPN, you are ensuring that only verified traffic is able to pass through the boundary.  |
| Use least privileged access  | Only resources that need connectivity to the on-prem environment will have that access.  |
| Assume breach  | A breach in one network segment will not be able to cross over to on-prem resources.  |

Post deployment, you will need to configure Route Tables on various subnets to ensure that traffic between spoke networks and the on-prem networks are inspected by the Azure Firewall.

This activity can be performed in an existing environment without a requirement of redeployment, but you will have to author the necessary firewall rules to allow access.

If you configure only one side of this - either just the spoke subnets, or the gateway subnets - then you will have asynchronous routing which will prevent connections from working at all.

### Why Route Network Gateway Traffic to the Firewall?

A key element of Zero Trust is to not assume that just because something is in your environment, that it should have access to other things in your environment. A default configuration will often allow for routing between resources in Azure to the on-prem networks, controlled only by the Network Security Groups.

By routing the traffic to the firewall, you increase the inspection and as a result the security. You are alerted to suspicious activity and can take action sooner.

### Configure Gateway Routing

There are two main ways to ensure that gateway traffic is being routed to the Azure firewall:

- Deploy the Azure VPN Gateway in a dedicated virtual network (often called a Transit or Gateway virtual network), peer it to the hub network, and then create a broad routing rule that covers your planned Azure networking address spaces routing to the firewall.

- Deploy the Azure VPN Gateway in the hub network, configure routing on the Gateway subnet, and configure routing on the spoke subnets.

This guide details the second option as it is more compatible with the reference architectures discussed above.

> [!NOTE]
> [Azure Virtual Network Manager](/azure/virtual-network-manager/overview) is a service that simplifies this process. When this services is Generally Available, it should be used to manage the routing.

### Configure Gateway Subnet Routing

To configure the Gateway Subnet Route table to forward internal traffic to the Azure Firewall, follow this process:
1. Create a new Route Table:
1. Navigate to **Create a Route Table** in the Azure Portal.
1. Place the Route Table in a Resource Group, select a Region and Name.
1. Select **Review and Create** and then **Create**.

:::image type="content" source="media/hub/hub-create-route-table.png" alt-text="Screenshot of create a route table." lightbox="media/hub/hub-create-route-table.png":::

5. Once deployed, navigate to the route table, and select **Routes**.

:::image type="content" source="media/hub/hub-routes.png" alt-text="Screenshot of Routes." lightbox="media/hub/hub-routes.png":::

6. Select **Add** and then populate a route to one of the spoke virtual networks:
7. Populate the **Route name** field.
8. Select **IP Addresses** in the **Address prefix destination** drop-down.
9. Provide the spoke virtual network's address space in the **Destination IP addresses/CIDR ranges** field.
10. Select **Virtual appliance** in the **Next hop type** drop-down box.
11. Provide the Azure Firewall's private IP address in the **Next hop address** field.
12. Select **Add**.

:::image type="content" source="media/hub/hub-add-route.png" alt-text="Screenshot of add route." lightbox="media/hub/hub-add-route.png":::

### Associate the Route Table to the Gateway subnet:

1. Navigate to **Subnets**, and select **Associate**.
1. Select the Hub virtual network in the **Virtual network** drop-down list.
1. Select the GatewaySubnet in the **Subnet** drop-down.
1. Select **OK**.

:::image type="content" source="media/hub/hub-associate-subnet.png" alt-text="Screenshot of associate Subnets." lightbox="media/hub/hub-associate-subnet.png":::

Now your gateway will forward traffic intended to spoke networks to the Azure Firewall.

### Configure spoke subnet routing

This process assumes that you already have a route table attached to your spoke network subnets, with a default route to forward traffic to the Azure Firewall. This is most often accomplished by a rule that forwards traffic for CIDR range 0.0.0.0/0, often called a quad-zero route.

:::image type="content" source="media/hub/hub-spoke-routing.png" alt-text="Screenshot of configure spoke subnet routing." lightbox="media/hub/hub-spoke-routing.png":::

This process disables the propagation of routes from the gateway, which will enable the default route to take traffic intended to the on-prem networks.

Note that resources (such as Application Gateways) that require internet access to function should not receive this route table. They should have their own route table to allow their necessary functions, such as what is outlined in the article [Zero-trust network for web applications with Azure Firewall and Application Gateway - Azure Architecture Center | Microsoft Learn](/azure/architecture/example-scenario/gateway/application-gateway-before-azure-firewall).

To configure spoke subnet routing:
1. Navigate to the Route Table associated with your subnet, and select **Configuration** on the left hand menu bar.
1. Set **Propagate gateway routes** to **No**.
1. Select **Save**.

:::image type="content" source="media/hub/hub-gateway-routes.png" alt-text="Screenshot of propagate gateway routes to No." lightbox="media/hub/hub-gateway-routes.png":::

Now your default route will send traffic intended for the Gateway to the Azure Firewall.

## Step 4. Threat protection

Your hub virtual network built on Azure may be protected by Microsoft Defender for Cloud, as other resources from your IT business environment running on Azure or on-premises may also be protected.

As mentioned in the other articles from this series, Microsoft Defender for Cloud is a Cloud Security Posture Management (CSPM) and Cloud Workload Protection (CWP) that offers a secure score system to help your company build an IT environment with a better secure posture. It also includes some features to protect your network environment against threats. You will learn about it in this section.

This article is not going to cover Microsoft Defender for Cloud in detail, but it is important to understand that Microsoft Defender for Cloud works based on Azure Policies and logs ingested on a Log Analytics workspace.

Azure Policies are rules written in JavaScript Object Notation (JSON) that hold different analysis of Azure resource properties, including network services and resources. That said, it is easy for Microsoft Defender for Cloud to check a property under a network resource and provide a recommendation to your subscription if you are protected or exposed to a threat.

### How to check all network recommendations available through Microsoft Defender for Cloud

To view all the Azure policies used by Microsoft Defender for Cloud, the ones that provide network recommendations, follow the steps below:

Screenshot

1. Open **Microsoft Defender for Cloud**, by selecting the Microsoft Defender for Cloud icon in the left menu.

1. Go to **Environment settings**.

1. Select **Security policy**.

1. If you click in the ASC Default, you will be able to review all the policies available, including the policies that evaluate network resources

1. Additionally, there will be network resources evaluated by other regulatory compliances including PCI, ISO and, Microsoft cloud security benchmark. You can enable any of them and track for network recommendations.

### Network recommendations

Follow the steps below to view some of the network recommendations, based on the Microsoft cloud security benchmark:

Screenshot


1. Open **Microsoft Defender for Cloud**.

1. Go to **Regulatory compliance**.

1. Select **Microsoft cloud security benchmark**.

1. Expand **NS. Network Security**.

1. Then, you will be able to review the recommended network control.

It is important to understand that Microsoft Defender for Cloud provides other network recommendations for different Azure resources such as Virtual Machine and Storage. You may review those recommendations in the left menu, under **Recommendations**.

On the left menu, select **Security Alerts** to review alerts based on network resources so you may avoid some types of threats. Those alerts are generated automatically by Microsoft Defender for Cloud based on logs ingested in the **Log Analytics** workspace and monitored by Microsoft Defender for Cloud.

### Mapping and hardening your Azure network environment through Microsoft Defender for Cloud

In the next screenshot, you may check options to get a better secure posture for your network environment by hardening your network environment in an effortless way by mapping your network environment for a better understanding of your network topology. Those recommendations are done through **Workload protection** option in the left menu.

Screenshot

### Managing Azure Firewall policies through Microsoft Defender for Cloud

Azure Firewall is recommended to be set up under a hub virtual network, as demonstrated in this article. Microsoft Defender for Cloud can manage multiple Azure Firewall policies centrally. In addition to "Azure Firewall policies", you will be able to manage other features related to Azure Firewall, as shown in the screenshot below.

:::image type="content" source="media/hub/hub-firewall-manager.png" alt-text="Screenshot of Azure Firewall Manager.":::

For more information about Microsoft Defender for Cloud and how you can use it to get your network environment better protected against threats, see:
[What is Microsoft Defender for Cloud? - Microsoft Defender for Cloud | Microsoft Learn](/azure/defender-for-cloud/defender-for-cloud-introduction)

## Recommended training based on the content in this article

The following Microsoft training is recommended to you in your journey with Zero Trust for Network.

- [Configure Azure Policy - Training | Microsoft Learn](/training/modules/configure-azure-policy/)

- [Design and implement network security - Training | Microsoft Learn](/training/modules/design-implement-network-security-monitoring/)

- [Configure Azure Firewall - Training | Microsoft Learn](/training/modules/configure-azure-firewall/)

- [Configure VPN Gateway - Training | Microsoft Learn](/training/modules/configure-vpn-gateway/)

- [Introduction to Azure DDoS Protection - Training | Microsoft Learn](/training/modules/introduction-azure-ddos-protection/)

- [Resolve security threats with Microsoft Defender for Cloud - Training | Microsoft Learn](/training/modules/resolve-threats-with-azure-security-center/)

For more training regarding Security on Azure, please see the entire Microsoft catalog:
[Browse all - Training | Microsoft Learn](/training/browse/)

## Next Steps

This article is part of a series of articles. Given below are the links to the rest of the articles in this series:

- [Overview – Apply Zero Trust principles to Azure infrastructure](azure-infrastructure-overview.md)
- [Apply Zero Trust principles to Azure storage](azure-infrastructure-storage.md)
- [Apply Zero Trust principles to virtual machines(VM)](azure-infrastructure-virtual-machines.md)
- [Apply Zero Trust principles to spoke virtual network in Azure](azure-infrastructure-iaas.md)

## References

The following are links to the several services and technologies mentioned in this article. 

- [Azure Virtual Network | Microsoft Learn](/azure/virtual-network/virtual-networks-overview)

- [What is Azure Firewall? | Microsoft Learn](/azure/firewall/overview)

- [About Azure VPN Gateway | Microsoft Learn](/azure/vpn-gateway/vpn-gateway-about-vpngateways)

- [Azure DDoS Protection Overview | Microsoft Learn](/azure/ddos-protection/ddos-protection-overview)

- [Introduction to Azure security | Microsoft Learn](/azure/security/fundamentals/overview)

- [Zero Trust implementation guidance | Microsoft Learn](/security/zero-trust/zero-trust-overview)

- [Overview of the Microsoft cloud security benchmark | Microsoft Learn](/security/benchmark/azure/overview)

- [Security baselines for Azure overview | Microsoft Learn](/security/benchmark/azure/security-baselines-overview)

- [Building the first layer of defense with Azure security services - Azure Architecture Center | Microsoft Learn](/azure/architecture/solution-ideas/articles/azure-security-build-first-layer-defense)

- [Microsoft Cybersecurity Reference Architectures - Security documentation | Microsoft Learn](/security/cybersecurity-reference-architecture/mcra)

