---
title: Secure a hub virtual network with Zero Trust 
description: Learn how to secure a hub virtual network with Zero Trust for access to Azure infrastructure.  
ms.date: 
ms.service: security
author: brendacarter
ms.author: bcarter
ms.topic: conceptual
ms.collection: 
  - msftsolution-accesscontrol
  - msftsolution-scenario
  - zerotrust-solution
---
# Secure a Hub virtual network with Zero Trust for access to Azure infrastructure

Guidance from Azure FastTrack team:

[fta-deliveryhowto/networkingHub.md at zta-brstep-hubnet-patch7 · Azure/fta-deliveryhowto (github.com)](https://github.com/Azure/fta-deliveryhowto/blob/zta-brstep-hubnet-patch7/articles/security/Zero%20Trust/Networking/networkingHub.md)

The best way to deploy a hub network for Zero Trust is to leverage the Azure Landing Zone materials to deploy a feature complete hub network, and then tailor it to your specific configuration expectations.

This article provides steps for how to take an existing hub network and ensure you are ready for a Zero Trust methodology. It assumes that you have used the the ALZ-Bicep [hubNetworking](https://github.com/Azure/ALZ-Bicep/tree/main/infra-as-code/bicep/modules/hubNetworking) module to rapidly deploy a hub network, or have deployed some other hub network with similar resources.

Using a separate connectivity hub connected to isolated workplace spokes is an anchor pattern in Azure secure networking, and helps support the Zero Trust principles in play.

This article is part of a series of article that demonstrate how to apply the principles of Zero Trust across an environment in Azure that includes a hub virtual network to support an IaaS workload. For more information, see Overview--Secure Azure infrastructure with Zero Trust.

This article describes how to deploy a hub network for Zero Trust by mapping the principles of zero trust in the following ways.

| **Zero Trust Principle** | **Met by** |
| --- | --- |
| Verify explicitly | Use Azure Firewall with SSL inspection to verify risk and threats based on all available data. |
| Use least privileged access | Each spoke has no access to other spokes unless the traffic is routed through the Firewall. The Firewall is set to deny by default, allowing only authorized rules to execute. |
| Assume breach | In the event of a compromise or breach of one application/workload, it will have limited ability to spread due to the Azure Firewall performing inspection and only allowing approved rules. Only resources in the same workload would be able to be exposed to the breach in the same application. |

# Reference architecture

The following diagram illustrates the reference architecture. The Hub virtual network is highlighted in red.

![](RackMultipart20221007-1-lq2ecf_html_47e1d4932f1e6b2e.gif)

For this reference architecture, there are a number of ways you can deploy the resources across the Azure subscription. The following illustration shows one recommendation—isolating all resources for the hub virtual network within a dedicated resource group. The resources for the spoke virtual network are also illustrated, for comparison. This model works well if different teams are given responsibility for these different areas.

![](RackMultipart20221007-1-lq2ecf_html_4b84b113acebf811.gif)

The following screen capture of the Azure portal lists the resources that are deployed for the hub virtual network.

![](RackMultipart20221007-1-lq2ecf_html_c88c2ed441f56130.png)

If you selected for Azure DDoS Plan to be deployed as part of the resources, that will be included as well.

Depending on your deployment, you may also note that there was a deployment of an array for Private DNS Zones used for Private Link DNS resolution. These are used to secure PaaS resources with Private Endpoints, which is part of [Securing PaaS workloads in a Virtual Network](https://github.com/Azure/fta-deliveryhowto/blob/zta-brstep-hubnet-patch7/articles/security/Zero%20Trust/Networking/networkingPaaSVnet.md).

Note that it deploys both a VPN Gateway and an ExpressRoute Gateway. You may not need both, so feel free to delete whichever one is not needed for your scenario, or turn off during deployment.

# In this article

This article provides recommendations for the securing the components of the hub virtual network.

| **Step** | **Task** |
| --- | --- |
| 1 | Secure Azure Firewall Premium |
| 2 | Deploy Azure DDoS Protection Standard |
| 3 | Configure network gateway routing to the firewall |
| 4. | Maintenance of the environment? |
| 5. | Threat protection? |

As part of your deployment, you will want to make specific selections. It should be noted that these tend not to be the defaults for automated deployments, due to their additional costs.

PriorPrior to deployment, you should review costs to confirm that you are prepared to make them.

Operating the connectivity hub as deployed still provides significant value for isolation and inspection, so if your organization is not ready for the cost of adopting these advanced features, you can deploy a reduced functionality hub and make these adjustments later.

# Step 1. Secure Azure Firewall Premium

Azure Firewall Premium plays a starring role in helping you secure your Azure infrastructure for Zero Trust, as described in the following table.

| **Zero Trust Principle** | **Met by** |
| --- | --- |
| Verify explicitly | By inspecting both the traffic source and the nature of the traffic, Azure Firewall verifies explicitly that traffic itself is safe (in addition to applying access control rules). |
| Use least privileged access | By providing a firewall between distinct applications, and inspecting all traffic regardless of its source, Azure Firewall can reduce access between network segments. |
| Assume breach | Because of this segmentation, individual network segments become their own blast radii. The firewall can prevent a compromise in one network segment from spreading into others. |

As part of the deployment, select Azure Firewall Premium as the SKU for Azure Firewall. This will require the management policy generated to be deployed as a premium policy as well.

Changing the SKU of the firewall involves recreating the firewall, and often the policy as well. As a result, start with Azure Firewall if possible. Or, be prepared for redeployment activities to replace the existing firewall.

## Why Azure Firewall Premium?

Azure Firewall Premium provides [advanced features](/azure/firewall/premium-features) for inspecting traffic.

Most significant is the TLS inspection options:

- **Outbound TLS Inspection**  which protects against malicious traffic that is sent from an internal client to the Internet. This helps identify when a client has been breached, and if it is trying to ship data outside of your network or establish a connection to a remote controller.
- **East-West TLS Inspection**  which protects against malicious traffic sent from within Azure to other parts of Azure or to your non-Azure networks. This helps identify attempts for a breach to expand and spread from one blast radius to another.
- **Inbound TLS Inspection**  which protects resources in Azure from malicious requests that arrive from outside the Azure network. Azure Application Gateway is needed to make this available.

The Inbound TLS inspection for resources should be used whenever possible. Because Application Gateway provides HTTP and HTTPS traffic only, there may be some scenarios where it is not able to be used - such as SQL or RDP traffic. Other methods should be used to provide _verify explicitly_ controls for those services.

These scenarios have specific certificate considerations. You can read more about them in the article on [Azure Firewall Premium certificates](/azure/firewall/premium-certificates).

Without TLS inspection, Azure Firewall has no visibility into the data that flows in the encrypted TLS tunnel, and so its protection is more limited.

In addition to the customer defined allow/deny rules, the Azure Firewall is still able to apply [threat intelligence-based filtering](/azure/firewall/threat-intel). Threat intelligence-based filtering uses known-bad Ips and domains to identify traffic that poses a risk. This filtering occurs prior to any other rules, meaning that even if the access was allowed by your defined rules, the traffic can be stopped.

Azure Firewall Premium also has enhanced options for URL filtering and web category filtering, allowing for there to be more fine tuned roles.

Threat intelligent can be set to Alert, to notify you of when this traffic occurs but to allow it through. However, for our Zero Trust deployment, it should be set to Deny.

## Configure Azure Firewall Premium for Zero Trust

To configure Azure Firewall Premium to a Zero Trust configuration, make the following changes.

1. Enable Threat Intelligence in Alert and Deny Mode:
      1. Navigate to the Firewall Policy and select  **Threat Intelligence**.
      2. In  **Threat intelligence mode**  select _Alert and deny_
      3. Select  **Save**.

![](RackMultipart20221007-1-lq2ecf_html_c79f1a2d62f73745.png)

2. Enable TLS inspection

    1. Prepare a certificate to be used, stored in a Key Vault, or plan to auto-generate a certificate with a managed identity. You can review these options for [Azure Firewall Premium certificates](/azure/firewall/premium-certificates) to select the option for your scenario.
    2. Navigate to the Firewall Policy and select  **TLS Inspection**.
    3. Select  **Enabled**.
    4. Either select a Managed Identity to be used to generate certificates, or select the Key Vault and Certificate.
    5. Then select  **Save**.

![](RackMultipart20221007-1-lq2ecf_html_447faed360b4054f.png)

3. Enable IDPS:
      1. Navigate to the Firewall Policy and select  **IDPS**.
      2. Select  **Alert and deny**.
      3. Then select  **Apply**.

![](RackMultipart20221007-1-lq2ecf_html_4e92ef979b6bbec8.png)

## Additional configuration

With the Azure Firewall Premium configured, you can now perform the following configurations:

- Configure Application Gateways to route traffic to your Azure Firewall, by assigning the appropriate route tables and [following this guidance](/azure/architecture/example-scenario/gateway/application-gateway-before-azure-firewall#hub-and-spoke-example).
- Create alerts for Firewall events and metrics, [following these instructions](/azure/firewall/firewall-diagnostics)
- Deploy the [Azure Firewall Workbook](/azure/firewall/firewall-workbook) to visualize events.
- Configure URL and [Web category filtering](/azure/firewall/web-categories), if needed. Because Azure Firewall is deny by default, this configuration is only needed if the Azure Firewall needs to grant outbound internet access broadly, but then use additional verifications to determine connections.

# Step 2. Deploy Azure DDoS Protection Standard

As part of the deployment, you will want to deploy an Azure DDoS Protection Standard Policy. This increases the default protection provided on the Azure Platform, as described in the following table.

| **Zero Trust Principle** | **Met by** |
| --- | --- |
| Verify explicitly | Monitors traffic and uses ML-based frameworks to detect traffic floods. |
| Use least privileged access | Prevent traffic flooding without controlled authorization. |
| Assume breach | Can monitor traffic to protect from different attack scenarios |

Because the policy that is created can be deployed out to existing resources, you can add this protection after the initial deployment without requiring the redeployment of resources.

## Why Azure DDoS Protection Standard?

Azure DDoS Protection Standard has [increased benefits](/azure/ddos-protection/ddos-protection-overview) over the default DDoS Protection. Specifically for Zero Trust, we want to:

- Have access to mitigation reports, flow logs, and metrics.
- Have application based mitigation policies.
- Have access to DDoS rapid response support in the event of a DDoS attack.

While automatic detection and automatic mitigation are both baked in to the DDoS Protection Basic that is enabled by default, these features are only available with DDoS Standard.

## Configure Azure DDoS Protection Standard

Because there are not any "Zero Trust Specific" configurations for DDoS Protection Standard, you can follow the resource specific guides for this solution:

- [Create a DDoS Protection Plan](/azure/ddos-protection/manage-ddos-protection)
- [Configure Alerting](/azure/ddos-protection/alerts)
- [Configure Diagnostic Logging](/azure/ddos-protection/diagnostic-logging)
- [Configure Telemetry](/azure/ddos-protection/telemetry)

# Step 3. Configure network gateway routing to the firewall

This configuration contributes to Zero Trust in the following ways.

| **Zero Trust Principle** | **Met by** |
| --- | --- |
| Verify explicitly | By inspecting traffic flowing to and from the VPN, you are ensuring that only verified traffic is able to pass through the boundary. |
| Use least privileged access | Only resources that need connectivity to the on-prem environment will have that access. |
| Assume breach | A breach in one network segment will not be able to cross over to on-prem resources. |

Post deployment, you will need to configure Route Tables on various subnets to ensure that traffic between spoke networks and the on-prem networks are inspected by the Azure Firewall.

This activity can be performed in an existing environment without a requirement of redeployment, but you will have to author the necessary firewall rules to allow for access.

If you configure only one side of this - either just the spoke subnets, or the gateway subnets - then you will have asynchronous routing which will prevent connections from working at all.

## Why Route Network Gateway Traffic to the Firewall?

A key element of Zero Trust is to not assume that just because something is in your environment, that it should have access to other things in your environment. A default configuration will often allow for routing between resources in Azure to the on-prem networks, controlled only by the Network Security Groups.

By routing the traffic to the firewall, you increase the inspection and as a result the security. You are able to be alerted to suspicious activity, and can take action sooner.

## Configure Gateway Routing

There are two main ways to ensure that gateway traffic is being routed to the Azure firewall:

- Deploy the Azure VPN Gateway in a dedicated virtual network (often called a Transit or Gateway virtual network), peer it to the hub network, and then create a broad routing rule that covers your planned Azure networking address spaces routing to the firewall.
- Deploy the Azure VPN Gateway in the hub network, configure routing on the Gateway subnet, and configure routing on the spoke subnets.

This guide details the second option as it is more compatible with the reference architectures discussed above.

**Note:**  [Azure Virtual Network Manager](/azure/virtual-network-manager/overview) is a service that simplifies this process. When this services is Generally Available, it should be used to manage these routing.

## Configure Gateway Subnet Routing

To configure the Gateway Subnet Route table to forward internal traffic to the Azure Firewall, follow this process:

- Create a new Route Table:
  - Navigate to  **Create a Route Table**  in the Azure Portal.
  - Place the Route Table in a Resource Group, select a Region and Name.
  - Select  **Review and Create**  and then  **Create**.

![](RackMultipart20221007-1-lq2ecf_html_c7f3824052a3f3d0.png)

- Once deployed, navigate to the route table, and select  **Routes**.

![](RackMultipart20221007-1-lq2ecf_html_2b804fcebd10e218.png)

- Select  **Add**  and then populate a route to one of the spoke virtual networks:

- Populate the  **Route name**  field.
- Select _IP addressess_ in the  **Address prefix destination**  drop down.
- Provide the spoke virtual network's address space in the  **Destination IP addresses/CIDR ranges**  field.
- Select _Virtual Appliance_ in the  **Next hop type**  drop down box.
- Provide the Azure Firewall's private IP address in the  **Next hop address**  field.
- Select  **Add**

![](RackMultipart20221007-1-lq2ecf_html_d5cdb8cf60889680.png)

1. Associate the Route Table to the Gateway subnet:

- Navigate to  **Subnets** , and select  **Associate**.
- Select the Hub virtual network in the  **Virtual network**  drop down.
- Select the GatewaySubnet in the  **Subnet**  dropdown.
- Select  **OK**.

![](RackMultipart20221007-1-lq2ecf_html_8c2ae3258a0f9a5b.png)

Now your gateway will forward traffic intended to spoke networks to the Azure Firewall.

## Configure spoke subnet routing

This process assumes you already have a route table attached to your spoke network subnets, with a default route to forward traffic to the Azure Firewall. This is most often accomplished by a rule that forwards traffic for CIDR range 0.0.0.0/0, often called a quad-zero route.

![](RackMultipart20221007-1-lq2ecf_html_523cc2818c2dc3b1.png)

This process disables the propagation of routes from the gateway, which will enable the default route to take traffic intended to the on-prem networks.

- Navigate to the Route Table associated with your subnet, and select  **Configuration**  on the left hand menu bar.
- Set  **Propagate gateway routes**  to _No_.
- Select  **Save**.

![](RackMultipart20221007-1-lq2ecf_html_e8e894f2c483ee16.png)

Now your default route will send traffic intended for the Gateway to the Azure Firewall.