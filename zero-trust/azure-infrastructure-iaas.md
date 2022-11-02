---
title: Apply Zero Trust principles to spoke virtual network in Azure
description: Learn how to secure a spoke virtual network for IaaS workloads with Zero Trust.   
ms.date: 10/20/2022
ms.service: security
author: brsteph
ms.author: bstephenson
ms.topic: conceptual
ms.collection: 
  - msftsolution-accesscontrol
  - msftsolution-scenario
  - zerotrust-solution
---

# Apply Zero Trust Principles to a spoke virtual network in Azure

This article will help you apply the principles of Zero Trust to a virtual network for IaaS workloads in Azure in the following ways:

| **Zero Trust Principle** | **Met by** |
| --- | --- |
| Verify Explicitly | Use Application Security Groups to verify that individual NICs have permissions to communicate over specific channels. |
| Use Least Privileged Access | Do not enable 3389/RDP access by default on any channel. Use correct role permissions for the spoke context. |
| Assume Breach | Limit unnecessary communication between resources. Ensure that you are able to log in to Network Security Groups and that you have proper visibility into anomalous traffic. Track changes to Network Security Groups. |

This article is a part of a series of articles that demonstrate how to apply the principles of Zero Trust across an environment in Azure that includes a spoke virtual network (VNet) hosting a virtual machine-based workload. For more information, see [Overview – Apply Zero Trust principles to Azure infrastructure](azure-infrastructure-overview.md).

## Reference architecture

The following diagram illustrates a common reference architecture for IaaS-based workloads.

:::image type="content" source="media/spoke/azure-infra-spoke-architecture-1.png" alt-text="Diagram of reference architecture for IaaS-based workloads.":::

In the illustration:

- A "spoke" virtual network includes components to support an IaaS application comprised of virtual machines.
- The IaaS application is a three-tier application comprised of two virtual machines for each tier—front end, application, and data.
- Each tier is contained within a dedicated subnet with a dedicated network security group.
- Each virtual machine role is assigned to an application security group corresponding to its role.
- Access to the application is provided through an Application Gateway contained in its own subnet.
The application illustrated by the reference architecture follows the [N-tier architecture style - Azure Architecture Center | Microsoft Learn](/azure/architecture/guide/architecture-styles/n-tier)

The following diagram illustrates the logical architecture of these components within an Azure subscription.

:::image type="content" source="media/spoke/azure-infra-spoke-subscription-architecture-2.png" alt-text="Diagram of components within an Azure subscription.":::

In the illustration, all components of the spoke virtual network are contained in a dedicated resource group:
- One virtual network
- One Azure Application Gateway (App GW), including a Web Application Firewall (WAF)
- Three network security groups, one for each application tier
- Three application security groups, one for each tier

## What's in this article

Zero Trust principles are applied across the architecture, from the tenant and directory level down to the assignment of virtual machines to application security groups. The following table describes the recommendations for securing this architecture.

| Step | Task |
| --- | --- |
| 1 | Leverage Azure AD RBAC or set up custom roles for networking resources. |
| 2 | Isolate infrastructure into its own resource group. |
| 3 | Create a network security group for each subnet. |
| 4 | Create an application security group for each virtual machine role. |
| 5 | Secure traffic and resources within the virtual network: <li> Deploy baseline deny rules for network security groups <li>Deploy application specific rules for application security groups <li> Plan for management traffic into the virtual network <li> Deploy network security group flow logging |
| 6 | Secure access to the virtual network and application. |
| 7 | Enable advanced threat detection, alerting, and protection. |

## Step 1. Leverage Azure AD RBAC or set up custom roles for networking resources

You can leverage [Azure AD RBAC built-in roles](/azure/role-based-access-control/built-in-roles#network-contributor) for network contributors. However, another approach is to leverage custom roles. Spoke network managers don't need full access to networking resources granted by the Azure AD RBAC Network Contributor role, but need more permissions than other common roles. A custom role can be used to scope access to just what is needed.

One easy way to implement this is to deploy the custom roles found in the [Azure Landing Zone Reference Architecture](https://github.com/Azure/ALZ-Bicep/tree/main/infra-as-code/bicep/modules/customRoleDefinitions).

The specific role that can be used is the **Network Management** custom role has the following permissions:

- Read all in the scope
- Any actions with the network provider
- Any actions with the support provider
- Any actions with the Resources provider

This role can be created using the scripts in the above repository or can be created through Azure Active Directory by the following process with the above scopes: [Azure custom roles - Azure RBAC | Microsoft Docs](/azure/role-based-access-control/custom-roles).

## Step 2. Isolate infrastructure into its own resource group

By isolating network resources from compute, data, or storage resources, you reduce the likelihood of permissions bleed. In addition, by ensuring that all related resources are in one resource group, you can make one security assignment and better manage logging and monitoring to these resources.

Rather than having the spoke network resources available in multiple contexts in a shared resource group, create a dedicated resource group for it. The reference architecture that this article supports illustrates this concept.

:::image type="content" source="media/spoke/azure-infra-spoke-dedicated-resource-group-3.png" alt-text="Diagram of isolate infrastructure into its own resource group." lightbox="media/spoke/azure-infra-spoke-dedicated-resource-group-3.png":::

In the illustration, resources and components across the reference architecture are divided into dedicated resource groups for virtual machines, storage accounts, hub virtual network resources, and spoke virtual network resources.

With a dedicated resource group, you can assign a custom role using the following process: [Tutorial: Grant a user access to Azure resources using the Azure portal - Azure RBAC | Microsoft Docs](/azure/role-based-access-control/quickstart-assign-role-user-portal).

Additional recommendations:

- Reference a security group for the role instead of named individuals.
- Manage access to the security group through your enterprise identity management patterns.

If you are not using policies that enforce log forwarding on resource groups, configure this in the Activity log for the resource group: 
Navigate to **Activity log -\> Export Activity Logs** and then select **+ Add diagnostic setting**.<br>
On the Diagnostic setting screen, select all log categories (especially Security) and send them to the appropriate logging sources, such as a Log Analytics workspace for observability, or a storage account for long term storage.

### Subscription Democratization

While not directly related to networking, you should plan your subscription RBAC in a similar way. In addition to isolating resources logically by resource group, you should also isolate the subscription based on business areas and portfolio owners. The subscription as a management unit should be narrowly scoped.<br>You can read more about subscription democratization here: [Azure landing zone design principles - Cloud Adoption Framework | Microsoft Learn](/azure/cloud-adoption-framework/ready/landing-zone/design-principles#subscription-democratization)

:::image type="content" source="media/spoke/diagnostic-setting.png" alt-text="Screenshot of Diagnostic setting." lightbox="media/spoke/diagnostic-setting.png":::

Read more about [Diagnostic Settings](/azure/azure-monitor/essentials/diagnostic-settings) to understand how to review these logs and alert on them.

## Step 3. Create a network security group for each subnet

Azure network security groups (NSGs) are used to filter network traffic between Azure resources in an Azure virtual network. It is recommended to apply a NSG to each subnet. This is enforced through Azure policy by default when deploying Azure Landing Zones. A network security group contains security rules that allow or deny inbound network traffic to, or outbound network traffic from, several types of Azure resources. For each rule, you can specify source and destination, port, and protocol.

For a multi-tier virtual-machine based application, the recommendation is to create a dedicated network security group (NSG in the illustration below) for each subnet that hosts a virtual machine role.

:::image type="content" source="media/spoke/azure-infra-spoke-nsg-4.png" alt-text="Diagram of dedicated NSG.":::

In the illustration:
- Each tier of the application is hosted in a dedicated subnet such as, web tier, app tier, and data tier.
- A network security group (NSG) is configured for each of these subnets.

Configuring network security groups in a different way than illustrated above can result in incorrect configuration of some or all of the network security groups and can create issues in troubleshooting. It can also make it difficult to monitor and log.

Create a network security group using this process: [Create, change, or delete an Azure network security group](/azure/virtual-network/manage-network-security-group)

Read more about [Network security groups](/azure/virtual-network/network-security-groups-overview) to understand how they can be used to secure the environment.

## Step 4. Create an application security group for each virtual machine role

Application security groups enable you to configure network security as a natural extension of an application's structure, allowing you to group virtual machines and define network security policies based on those groups. You can reuse your security policy at scale without manual maintenance of explicit IP addresses. The platform handles the complexity of explicit IP addresses and multiple rule sets, allowing you to focus on your business logic.

Inside your workload, identify the specific virtual machine roles. Then, build an application security group for each role. In the reference architecture, three application security groups (ASGs) are represented.

:::image type="content" source="media/spoke/azure-infra-spoke-asg-5.png" alt-text="Diagram of application security groups.":::

In the illustration:
- Three application security groups are created to support this app, one for each tier web, app, and data.
- Each virtual machine is assigned to the corresponding application security group for its role (red text in the illustration).

For more information about application security groups and how to assign these to virtual machines, see [Azure application security groups overview | Microsoft Learn](/azure/virtual-network/application-security-groups).

> [!NOTE]
> If you are using load balancers, using IP address of the load balancer in the NSGs is required as ASGs cannot scope a load balancer.

## Step 5. Secure traffic and resources within the virtual network

This section covers the following recommendations:

- Deploy baseline deny rules for network security groups
- Deploy application specific rules for application security groups
- Plan for management traffic into the virtual network
- Deploy network security group flow logging

### Deploy baseline deny rules for network security groups

A key element of Zero Trust is using the least level of access needed. By default, network security groups have allowed rules. By adding a baseline of deny rules, you can enforce the least level of access.

Once provisioned, create a deny all rule in each of the inbound and outbound rules, with a priority of 4096. This is the last custom priority available, which means you still have the remaining scope to configure allow actions.

To do this, in the Network Security Group go to **Outbound Security Rules** and select **Add**. Fill in the following:
- Source: Any
- Source port ranges: \*
- Destination: Any
- Service: Custom
- Destination Port Ranges: \*
- Protocol: Any
- Action: Deny
- Priority: 4096
- Name: DenyAllOutbound
- Description: Denies all outbound traffic unless specifically allowed.

The following screen capture provides an example.

:::image type="content" source="media/spoke/outbound-sec-rules.png" alt-text="Screenshot of Outbound security rules." lightbox="media/spoke/outbound-sec-rules.png":::

Repeat this process with inbound rules, adjusting the name and description as appropriate.<br>
You will notice that on the Inbound security rules tab, you will see a warning sign on the rule.

:::image type="content" source="media/spoke/outbound-sec-rules-1.png" alt-text="Screenshot of inbound security rules." lightbox="media/spoke/outbound-sec-rules-1.png":::

If you click on the rule and scroll to the bottom, you will see more details:

:::image type="content" source="media/spoke/rule-details.png" alt-text="Screenshot of rule details.":::

This message gives the following two warnings:

- Azure Load Balancers will not, by default, be able to access resources using this NSG.
- Other resources on this virtual network will not, by default, be able to access resources using this NSG.

For our purpose in Zero Trust, this is _excellent_. It means that just because something is on this virtual network, doesn't mean that it will have immediate access to your resources! For each traffic pattern, you will need to create a rule explicitly allowing it, and you should do so with the least amount of permissions.<br>
Thus if you have specific outbound connections for management, such as to Active Directory Domain Controllers, private DNS VMs, or to specific external websites, they need to be controlled here.

### Alternative Deny Rules

If you are using Azure Firewall to manage your outbound connections, then instead of performing a deny outbound all, you can leave all outbound open. As a part of the Azure Firewall implementation, you will set up a route table that will send the default route (0.0.0.0/0) to the firewall. This will handle traffic outside of the virtual network.

You can then either create a deny all vnet outbound, or instead allow all outbound (but secure items with their inbound rules).

Read more about [Azure Firewall](/azure/firewall/overview) and [Route Tables](/azure/virtual-network/manage-route-table) to understand how they can be used to further increase the security of the environment.

### VM Management Rules

To configure VMs with Azure AD Login, Anti-Malware, and automatic updates enabled, you will need to allow the following outbound connections. Many of these are by FQDN, meaning that either Azure Firewall is needed for FQDN rules, or you will make a more complex plan.<br>
Azure Firewall is recommended.<br>
The outbound connections are:
- On port 443:
  - enterpriseregistration.windows.net
  - settings-win.data.microsoft.com
  - sls.update.microsoft.com
  - v10.events.data.microsoft.com
  - login.microsoftonline.com
  - pas.windows.net
  - 169.254.169.254
- On port 80:
  - ctldl.windowsupdate.com
  - www.msftconnecttest.com
- On port 123:
  - 40.119.6.228
- On port 1688:
  - 40.83.235.53

### Deploy application specific rules for application security groups

Define traffic patterns with the least amount of permissions and only following explicitly allowed paths. Using the application security groups in this example, define networking patterns in the network security groups.

:::image type="content" source="media/spoke/azure-infra-spoke-tiers-6.png" alt-text="Diagram of networking patters in NSG." lightbox="media/spoke/azure-infra-spoke-tiers-6.png":::

This results in the following rules:
- Allowing internet traffic into the DMZ Load Balancer (HTTPS 443)
- Allowing traffic from the DMZ NVAs to the Web tier Load Balancer (HTTPS 433)
- Allowing traffic from the Web tier VMs to the Business tier Load Balancer (HTTPS 443)
- Allowing traffic from the Business tier VMs to the Data tier Load Balancer (SQL 1433)
- Allowing traffic from the Data tier Load Balancer to the Data tier VMs (SQL 1433)

Presumably, the SQL servers need to communicate with each other over SQL 1433.

Configure the SQL pattern first, and then repeat this process with the remaining tiers.

#### Rule 1 - Allow traffic from Business tier VMs to Data tier Load Balancer (SQL 1433)

In the NSG, navigate to **Inbound Security Rules**, and select **Add**. Populate the list with the following:
- Source: Application Security Group
- Source application security groups: Select your business tier ASG
- Source port ranges: 1433 (Sometimes source traffic can come from different ports and if this pattern occurs you can add source port ranges to \* to allow any source port. Destination port is more significant and some recommendations are to always use \* for source port)
- Destination: IP addresses
- Destination IP addresses/CIDR ranges: the explicit IP of the load balancer
  - You need to use the explicit IP here because you cannot associate a load balancer with an ASG.
  - You can plan for this in your IP schema or deploy the load balancer and refer to the IP it is assigned.
- Service: MS SQL
- Destination Port Ranges: This will be automatically filled in for port 1433
- Protocol: This will be automatically selected for TCP
- Action: Allow
- Priority: A value between 100 and 4096. You can start with 105.
- Name: AllowBusinesstoSQLLBInbound
- Description: Allows inbound access to the SQL Load Balancer from Business Tier Virtual Machines

You will notice after completion that there will be a blue icon for informational alerts on the rule. <br>Clicking the rule will give the following message: <br> "Rules using application security groups may only be applied when the ASGs are associated with network interfaces on the same virtual network."

:::image type="content" source="media/spoke/informational-alert.png" alt-text="Screenshot of informational alert.":::

Thus, the rule will only be applied when this ASG is used in this network.

Finally, in the NSG, navigate to **Outbound Security Rules** and select **Add**. Populate the list similar to the above, changing Inbound to Outbound.

#### Rule 2 - Allow traffic from Data tier Load Balancer to Data tier VMs (SQL 1433)

In the NSG, navigate to **Inbound Security Rules** and select **Add**. Populate the list with the following:

- Source: IP Address
- Source IP Address: The IP address of the load balancer
- Source port ranges: 1433
- Destination: Application security group
- Destination application security groups: Select your data tier ASG
- Service: MS SQL
- Destination Port Ranges: This will be automatically filled in for port 1433.
- Protocol: This will be automatically selected for TCP.
- Action: Allow
- Priority: A value between 100 and 4096. You can start with 105.
- Name: AllowSQLLBtoSQLVMInbound
- Description: Allows inbound access to the SQL Tier Virtual Machines from the SQL Load Balancer.

In the NSG, navigate to **Outbound Security Rules** and select **Add**. Populate the list as done above, changing Inbound to Outbound.

#### Rule 3 — Allow traffic from Data tier VMs to Data tier VMs (SQL 1433)

In the NSG, navigate to **Inbound Security Rules** and select **Add**. Populate the list with the following:

- Source: Application security group
- Destination application security groups: Select your data tier ASG
- Source port ranges: 1433
- Destination: Application security groups
- Destination application security groups: Select your data tier ASG
- Service: MS SQL
- Destination Port Ranges: This will be automatically filled in for port 1433.
- Protocol: This will be automatically selected for TCP.
- Action: Allow
- Priority: A value between 100 and 4096. You can start with 105.
- Name: AllowSQLVMtoSQLVMInbound
- Description: Allows inbound access between SQL Tier VMs.

In the NSG, navigate to **Outbound Security Rules** and select **Add**. Populate the list as done above, changing Inbound to Outbound.

With these three rules, you have defined the Zero Trust connectivity pattern for a single application tier. You can repeat this process as required for additional flows.

### Plan for management traffic in the virtual network

In addition to the application specific traffic, you need to plan for management traffic. However, management traffic generally originates outside of the spoke virtual network. Additional rules are required. First, you will need to understand the specific ports and sources that management traffic will be coming from. Generally, all management traffic should flow from a firewall or other NVA located in the hub network for the spoke.<br> See the full reference architecture in the [Overview – Apply Zero Trust principles to Azure infrastructure](azure-infrastructure-overview.md) article.

This will vary based on your specific management needs. However, rules on the firewall appliances and rules on the NSG should be used to explicitly allow connections on both the platform networking side and the workload networking side.

### Deploy network security group flow logging

Even if your network security group is blocking unnecessary traffic doesn't mean that your goals are met. You still need to observe the traffic occurring outside your explicit patterns, so that you know if an attack is occurring.

To enable Network Security Group Flow Logging, you can follow the [Tutorial: Log network traffic flow to and from a virtual machine](/azure/network-watcher/network-watcher-nsg-flow-logging-portal#enable-nsg-flow-log) against the existing network security group that is created.

> [!NOTE]
> - The storage account should follow the Zero Trust storage account guidance.
> - Access to the logs should be restricted as needed.
> - They should also flow in to Log Analytics and Sentinel as needed.

## Step 6. Secure access to the virtual network and application

Securing access to the virtual network and application includes:
- Securing traffic within the Azure environment to the application
- Using multi-factor authentication and conditional access policies for user access to the application.

The following diagram illustrates both these access modes across the reference architecture.

:::image type="content" source="media/spoke/azure-infra-spoke-network-7.png" alt-text="Diagram of access modes in reference architecture.":::

### Secure traffic within Azure environment for the virtual network and application

Much of the work of security traffic within the Azure environment is already complete. Secure connections between storage resources and the virtual machines are configured in [Apply Zero Trust principles to Azure storage](azure-infrastructure-storage.md).

Securing access from Hub resources to the virtual network is configured in [Apply Zero Trust principles to a hub virtual network in Azure](azure-infrastructure-networking.md).

### Using multi-factor authentication and conditional access policies for user access to the application

The article, [Apply Zero Trust principles to virtual machines(VM)](azure-infrastructure-virtual-machines.md) recommends how to protect access requests directly to virtual machines with multi-factor authentication and conditional access. These requests are most likely from administrators and developers. The next step is to secure access to the application with multi-factor authentication and conditional access. This applies to all users who access the app.

First, if the application is not yet integrated with Azure AD, see [Application types for the Microsoft identity platform](/azure/active-directory/develop/v2-app-types#daemons-and-server-side-apps).

Next, add the application to the scope of your identity and device access policies.

When configuring multi-factor authentication with conditional access and related policies, use the recommended policy set for Zero Trust as a guide. This includes "Starting point" policies that don't require managing devices. Ideally, the devices accessing your virtual machines are managed and you can implement the "Enterprise" level, which is recommended for Zero Trust. For more information, see [Common Zero Trust identity and device access policies](/microsoft-365/security/office-365-security/identity-access-policies).

The following diagram illustrates the recommended policies for Zero Trust.

:::image type="content" source="media/vm/identity-device-access-policies-byplan.png" alt-text="Diagram of authentication with conditional access." lightbox="media/vm/identity-device-access-policies-byplan.png":::

## Step 7. Enable advanced threat detection and protection

Your Spoke virtual network built on Azure may be protected by Microsoft Defender for Cloud (MDC) as other resources from your IT business environment running on Azure or on-premises may also be protected.

As mentioned in the other articles from this series, Microsoft Defender for Cloud is a Cloud Security Posture Management (CSPM) and Cloud Workload Protection (CWP) tool that offers Security Recommendations, Alerts, and advanced features such as [Adaptive Network Hardening](/azure/defender-for-cloud/adaptive-network-hardening) to assist you as you progress in your Cloud Security journey. To better visualize where Defender for Cloud fits into the greater Microsoft security landscape, see [Microsoft Cybersecurity Reference Architectures](/security/cybersecurity-reference-architecture/mcra).

This article is not going to cover Microsoft Defender for Cloud in detail, but it is important to understand that Microsoft Defender for Cloud works based on Azure Policies and logs ingested in a Log Analytics workspace. Once enabled on the subscription(s) with your spoke virtual network and associated resources, you will be able to see Recommendations to improve their Security Posture. You can filter these Recommendations further by MITRE tactic, Resource Group, etc. Consider prioritizing to resolve Recommendations that have a greater impact on your organization's Secure score.

:::image type="content" source="media/spoke/dfc-recs.png" alt-text="Screenshot of MDC recommendations." lightbox="media/spoke/dfc-recs.png"::: 

If you choose to onboard one of the Defender for Cloud plans that offer Advanced Workload Protections, it will include Adaptive Network Hardening Recommendations to improve your existing Network Security Group rules.

:::image type="content" source="media\spoke\network-hardening.png" alt-text="Screenshot of network hardening recommendations." lightbox="media\spoke\network-hardening.png"::: 

You can accept the recommendation by selecting **Enforce** which will either create a new NSG rule or modify an existing one.

## Recommended Training Based on content in this article

- [Secure your Azure resources with Azure role-based access control (Azure RBAC)](/training/modules/secure-azure-resources-with-rbac/)
- [Configure and manage Azure Monitor](/training/modules/azure-monitor/)
- [Configure network security groups](/training/modules/configure-network-security-groups/)
- [Design and implement network security](/training/modules/design-implement-network-security-monitoring/)
- [Secure access to your applications by using Azure identity services](/training/modules/secure-access-azure-identity-services/)

## Next Steps

This article is part of a series of articles. Given below are the links to the rest of the articles in this series:

- [Overview – Apply Zero Trust principles to Azure infrastructure](azure-infrastructure-overview.md)
- [Apply Zero Trust principles to Azure storage](azure-infrastructure-storage.md)
- [Apply Zero Trust principles to virtual machines(VM)](azure-infrastructure-virtual-machines.md)
- [Apply Zero Trust principles to a hub virtual network in Azure](azure-infrastructure-networking.md)

## References

- [Embrace proactive security with Zero Trust](https://aka.ms/zerotrust)
- [Secure networks with Zero Trust | Microsoft Learn](/security/zero-trust/deploy/networks)
- [Zero-trust network for web applications with Azure Firewall and Application Gateway - Azure Architecture Center | Microsoft Learn](/azure/architecture/example-scenario/gateway/application-gateway-before-azure-firewall)
- [Azure Landing Zone Policies](https://github.com/Azure/Enterprise-Scale/blob/main/docs/ESLZ-Policies.md)
- [Common Zero Trust identity and device across policies](/microsoft-365/security/office-365-security/identity-access-policies)