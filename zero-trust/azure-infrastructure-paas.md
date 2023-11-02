---
title: Apply Zero Trust principles to a spoke VNet with Azure PaaS Services
description: Learn how to secure a spoke VNet for PaaS workloads with Zero Trust. 
ms.date: 06/28/2023
ms.service: security
author: brsteph
ms.author: bstephenson
ms.topic: conceptual
ms.collection: 
  - msftsolution-azurepaas
  - msftsolution-scenario
  - zerotrust-solution
  - zerotrust-azure
---

# Apply Zero Trust principles to a spoke virtual network with Azure PaaS Services

This article helps you apply the [principles of the Zero Trust](zero-trust-overview.md#guiding-principles-of-zero-trust) security model to a PaaS workload using Azure virtual networks (VNets) and private endpoints in the following ways:

| Zero Trust principle | Definition | Met by |
| --- | --- | --- |
| Verify explicitly |Always authenticate and authorize based on all available data points. | Use threat detection in Azure Firewall and Azure Application Gateway to validate traffic and to verify if the traffic is acceptable. |
| Use least privileged access | Limit user access with Just-In-Time and Just-Enough-Access (JIT/JEA), risk-based adaptive policies, and data protection. | Reduce ingress to and egress from Azure services to your private networking. Use network security groups to allow only specific ingress from your VNet. Use a central Azure Firewall instance to grant non-VNet traffic access to the Azure service. |
| Assume breach | Minimize blast radius and segment access. Verify end-to-end encryption and use analytics to get visibility, drive threat detection, and improve defenses. | Limit unnecessary communication between resources. Ensure that you are logging from network security groups and that you have proper visibility into anomalous traffic. Track changes to network security groups. |

For more information about how to apply the principles of Zero Trust across an Azure IaaS environment, see the [Apply Zero Trust principles to Azure IaaS overview](azure-infrastructure-overview.md).

## Zero Trust stand alone or spoke network for Azure PaaS services

Many PaaS services contain their own, service-native ingress and egress control functionality. You can use these controls to secure network access to PaaS service resources without the need of infrastructure such as VNets. For example:

- Azure SQL Database has its own firewall that can be used to allow specific client IP addresses that need to access the database server.
- Azure storage accounts have a configuration option allow connections from a specific VNet or to block public network access.
- Azure App Service supports access restrictions to define a priority-ordered allow/deny list that controls network access to your app.

However, for Zero Trust guided implementations, these service-native access controls often fall short of being sufficient. This creates a diffusion of access controls and logging that can increase management and decrease visibility.

In addition, PaaS services can use fully qualified domain names (FQDN) that resolve to a dynamically assigned public IP address that is allocated from a pool of public IP addresses in a specific region for a type of service. Because of this, you won't be able to allow traffic from or to a specific PaaS service by using their public IP address, which can change.

Microsoft recommends that you use [private endpoints](/azure/private-link/private-endpoint-overview). A private endpoint is a VNet interface that uses a private IP address from your VNet. This network interface connects you privately and securely to a service that's powered by Azure Private Link. By enabling a private endpoint, you bring the service into your VNet.

Depending on your solution scenario, you may still need public inbound access to your PaaS services. But unless you do, Microsoft recommends that all traffic remain private to eliminate potential security risks.

This guide provides instructions for a specific reference architecture, but the principles and methods can be applied to other architectures as needed.

## Reference architecture

The following diagram shows a common reference architecture for PaaS-based workloads.

:::image type="content" source="media/spoke-paas/azure-infra-spoke-subscription-paas-architecture-2.png" alt-text="Diagram of the reference architecture for PaaS-based workloads." lightbox="media/spoke-paas/azure-infra-spoke-subscription-paas-architecture-2.png":::

In the diagram:

- A spoke VNet includes components to support a PaaS application.
- The PaaS application is a two-tier application leveraging Azure Application Services for a web app/front end and an Azure SQL Database for relational databases.
- Each tier is contained within a dedicated subnet for ingress with a dedicated network security group.
- The web tier contains a dedicated subnet for egress.
- Access to the application is provided through an Application Gateway contained in its own subnet.

The following diagram shows the logical architecture of these components within an Azure subscription.

:::image type="content" source="media/spoke-paas/azure-infra-spoke-subscription-paas-architecture-3.png" alt-text="Diagram of components within an Azure subscription.":::

In the diagram, all components of the spoke VNet are contained in a dedicated resource group:

- One VNet
- One Azure Application Gateway (App GW), including a Web Application Firewall (WAF)
- Three network security groups (named with "NSG" in the diagram) for the database, application, and front-end tiers
- Two application security groups (named with "ASG" in the diagram)
- Two private endpoints

In addition, resources for the hub VNet are deployed in the appropriate connectivity subscription.

## What's in this article

Zero Trust principles are applied across the architecture, from the tenant and directory level down to the assignment of VMs to application security groups. The following table describes the recommendations for securing this architecture.

| Step | Task |
| --- | --- |
| 1 | Leverage Microsoft Entra RBAC or set up custom roles for networking resources. |
| 2 | Isolate infrastructure into its own resource group. |
| 3 | Create a network security group for each subnet. |
| 4 | Secure traffic and resources within the VNet: <ul><li> Deploy baseline deny rules for network security groups. </li><li> Plan for management traffic into the VNet. </li><li> Deploy network security group flow logging. </li></ul> |
| 5 | Secure ingress and egress for Azure PaaS services. |
| 6 | Secure access to the VNet and application. |
| 7 | Enable advanced threat detection, alerting, and protection. |

This guide assumes that you already have an Azure Application Service and Azure SQL Database deployed in their own resource groups.

<a name='step-1-leverage-azure-ad-rbac-or-set-up-custom-roles-for-networking-resources'></a>

## Step 1: Leverage Microsoft Entra RBAC or set up custom roles for networking resources

You can leverage [Microsoft Entra RBAC built-in roles](/azure/role-based-access-control/built-in-roles#network-contributor) for network contributors. However, another approach is to leverage custom roles. Spoke VNet network managers don't need full access to networking resources granted by the Microsoft Entra RBAC Network Contributor role but need more permissions than other common roles. A custom role can be used to scope access to just what is needed.

One easy way to implement this is to deploy the custom roles found in the [Azure Landing Zone Reference Architecture](https://github.com/Azure/ALZ-Bicep/tree/main/infra-as-code/bicep/modules/customRoleDefinitions).

The specific role that can be used is the **Network Management** custom role, which has the following permissions:

- Read all in the scope
- Any actions with the network provider
- Any actions with the support provider
- Any actions with the resources provider

This role can be created using the scripts in the Azure Landing Zone Reference Architecture GitHub repository or can be created through Microsoft Entra ID with [Azure custom roles](/azure/role-based-access-control/custom-roles).

## Step 2: Isolate infrastructure into its own resource group

By isolating network resources from compute, data, or storage resources, you reduce the likelihood of permissions bleed. In addition, by ensuring that all related resources are in one resource group, you can make one security assignment and better manage logging and monitoring to these resources.

Rather than having the spoke network resources available in multiple contexts in a shared resource group, create a dedicated resource group. The following reference architecture diagram shows this configuration.

:::image type="content" source="media/spoke-paas/azure-infra-spoke-subscription-paas-architecture-3.png" alt-text="Diagram of isolating infrastructure into its own resource group." lightbox="media/spoke-paas/azure-infra-spoke-subscription-paas-architecture-3.png":::

In the diagram, resources and components across the reference architecture are divided into dedicated resource groups for application services, Azure SQL databases, storage accounts, hub VNet resources, and spoke VNet resources.

With a dedicated resource group, you can assign a custom role using the [Grant a user access to Azure resources using the Azure portal](/azure/role-based-access-control/quickstart-assign-role-user-portal) tutorial.

Additional recommendations:

- Reference a security group for the role instead of named individuals.
- Manage access to the security group through your enterprise identity management practices.

If you are not using policies that enforce log forwarding on resource groups, configure this in the activity log for the resource group:

1. Find the resource group in the Azure portal.
2. Navigate to **Activity log -\> Export Activity Logs** and then select **+ Add diagnostic setting**.
3. On the **Diagnostic setting** screen, select all log categories (especially **Security**) and send them to the appropriate logging sources, such as a Log Analytics workspace for observability, or a storage account for long term storage. Here's an example:

:::image type="content" source="media/spoke/diagnostic-setting.png" alt-text="Example of the Diagnostic setting." lightbox="media/spoke/diagnostic-setting.png":::

See [Diagnostic Settings](/azure/azure-monitor/essentials/diagnostic-settings) to understand how to review these logs and alert on them.

### Subscription democratization

While not directly related to networking, you should plan your subscription RBAC in a similar way. In addition to isolating resources logically by resource group, you should also isolate the subscription based on business areas and portfolio owners. The subscription as a management unit should be narrowly scoped.

See the [Azure landing zone design principles](/azure/cloud-adoption-framework/ready/landing-zone/design-principles#subscription-democratization) for more information.

## Step 3: Create a network security group for each subnet

Azure network security groups are used to filter network traffic between Azure resources in an Azure VNet. It is recommended to apply a network security group to each subnet. This is enforced through Azure policy by default when deploying Azure Landing Zones. A network security group contains security rules that allow or deny inbound network traffic to, or outbound network traffic from, several types of Azure resources. For each rule, you can specify source and destination IP addresses, a protocol (such as TCP or UDP), and a port.

For multi-tier applications, the recommendation is to create a dedicated network security group ("NSG" in the following diagram) for each subnet that hosts a networking component.

:::image type="content" source="media/spoke-paas/azure-infra-spoke-subscription-paas-nsg-4.png" alt-text="Diagram of dedicated network security groups for each subnet." lightbox="media/spoke-paas/azure-infra-spoke-subscription-paas-nsg-4.png":::

In the diagram:

- Each tier of the application has a dedicated ingress subnet, such as one for the web tier and another for the data tier.
- Azure Application Services has a dedicated egress subnet for a specific application service.
- A network security group is configured for each of these subnets.

Configuring network security groups in a different way than in the diagram can result in incorrect configuration of some or all of the network security groups and can create issues in troubleshooting. It can also make it difficult to monitor and log.

See [Create, change, or delete an Azure network security group](/azure/virtual-network/manage-network-security-group) to manage the settings of your network security groups.

Read more about [Network security groups](/azure/virtual-network/network-security-groups-overview) to understand how they can be used to secure your environments.

## Step 4: Secure traffic and resources within the VNet

This section describes the following recommendations:

- Deploy baseline deny rules for network security groups
- Deploy application-specific rules
- Plan for management traffic in the VNet
- Deploy network security group flow logging

### Deploy baseline deny rules for network security groups

A key element of Zero Trust is using the least level of access needed. By default, network security groups have **allow** rules. By adding a baseline of **deny** rules, you can enforce the least level of access. Once provisioned, create a **deny all** rule in each of the inbound and outbound rules with a priority of 4096. This is the last custom priority available, which means you still have the remaining scope to configure allow actions.

To do this, in the network security group, go to **Outbound Security Rules** and select **Add**. Fill in the following:

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

Here's an example.

:::image type="content" source="media/spoke/outbound-sec-rules.png" alt-text="Example of outbound security rules." lightbox="media/spoke/outbound-sec-rules.png":::

Repeat this process with inbound rules, adjusting the name and description as appropriate.

The **Inbound security rules** tab displays warning sign on the rule. Here's an example.

:::image type="content" source="media/spoke/outbound-sec-rules-1.png" alt-text="Example of inbound security rules." lightbox="media/spoke/outbound-sec-rules-1.png":::

Click the rule and scroll to the bottom to see more details. Here's an example:

:::image type="content" source="media/spoke/rule-details.png" alt-text="Example of rule details." lightbox="media/spoke/rule-details.png":::

This message gives the following two warnings:

- Azure Load Balancers won't, by default, be able to access resources using this network security group.
- Other resources on this VNet won't, by default, be able to access resources using this network security group.

For our purpose in Zero Trust, this is how it should be. It means that just because something is on this VNet, doesn't mean that it will have immediate access to your resources. For each traffic pattern, create a rule explicitly allowing it and you should do so with the least amount of permissions.

If you have specific outbound connections for management, such as to Active Directory Domain Services (AD DS) domain controllers, private DNS VMs, or to specific external websites, they need to be controlled here.

### Alternative deny rules

> [!NOTE]
> The recommendations in this section only apply to the web-egress subnet.

If you are using Azure Firewall to manage your outbound connections, instead of performing a deny-outbound-all, you can create alternate rules for outbound connections. As a part of the Azure Firewall implementation, you set up a route table that sends default route (0.0.0.0/0) traffic to the firewall. This will handle traffic outside of the VNet.

You can then either create a deny all VNet outbound rule, or an allow all outbound rule but secure items with their inbound rules.

See [Azure Firewall](/azure/firewall/overview) and [Route Tables](/azure/virtual-network/manage-route-table) to understand how they can be used to further increase the security of the environment.

### Deploy application-specific rules

Define traffic patterns with the least amount of permissions and only following explicitly allowed paths. Using subnets as sources, define networking patterns in the network security groups. Here's an example.

:::image type="content" source="media/spoke-paas/azure-infra-spoke-subscription-paas-tiers-6.png" alt-text="Diagram of networking patterns in network security groups." lightbox="media/spoke-paas/azure-infra-spoke-subscription-paas-tiers-6.png":::

Use the [Manage network security groups: Create a security rule](/azure/virtual-network/manage-network-security-group?tabs=network-security-group-portal#create-a-security-rule) process to add rules to your network security groups.

To secure this scenario, add the following rules:

| Network security group for Subnet | Direction | Source | Source Details | Source Port | Destination | Destination Details | Service | Network security group Name | Network security group description |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| App Service Subnet | Inbound | IP Addresses | Your Application Gateway Subnet's Private IP Address Range | 443 | IP Addresses | The explicit IP address of your App Service's private endpoint | MS SQL | AllowGWtoAppInbound | Allows inbound access to the App Service from the Application Gateway. |
| App Service Integration Subnet | Outbound | IP Addresses | Your App Service Integration Subnet's IP Address Range | 1433 | IP Addresses | The explicit IP address of your SQL DB's private endpoint | MS SQL | AllowApptoSQLDBOutbound | Allows outbound access to the SQL private endpoint from App Service Integration subnet.
| Azure SQL Subnet | Inbound | IP Addresses | Your App Service Integration Subnet's IP Address Range | 1433 | IP Addresses | The explicit IP address of your SQL DB's private endpoint | MS SQL | AllowApptoSQLDBInbound | Allows inbound access to the SQL private endpoint from App Service Integration subnet.

>[!NOTE]
>Sometimes source traffic can come from different ports and if this pattern occurs you can add source port ranges to "\*" to allow any source port. The destination port is more significant, and some recommendations are to always use "\*" for the source port.

>[!NOTE]
>For priority, use a value between 100 and 4000. You can start at 105.

This is in addition to the network security group rules on your Application Gateway Subnet.

With these rules, you have defined the Zero Trust connectivity pattern for a single application tier. You can repeat this process as required for additional flows.

### Plan for management traffic in the VNet

In addition to the application-specific traffic, plan for management traffic. However, because management traffic typically originates outside of the spoke VNet, more rules are required. First, understand the specific ports and sources that management traffic will be coming from. Typically, all management traffic should flow from a firewall or other network virtual appliance (NVA) located in the hub network for the spoke.

See [Apply Zero Trust principles to Azure IaaS overview](azure-infrastructure-overview.md#reference-architecture) for the full reference architecture.

Your configuration will vary based on your specific management needs. However, you should use rules on firewall appliances and rules on the network security group to explicitly allow connections on both the platform networking and workload networking sides.

### Planning for deployments

Because your application services and databases are now using private networking, plan for how deployments of code and data to these resources operate. Add rules to allow your private build servers to access these endpoints.

### Deploy network security group flow logging

Even if your network security group is blocking unnecessary traffic it doesn't mean that your goals are met. To detect an attack, you still need to observe the traffic that is occurring outside of your explicit patterns.

The traffic to the private endpoints is **not** logged, but if other services are deployed to the subnets later this log will help detect the activities.

To enable network security group flow Logging, follow the [Tutorial: Log network traffic flow to and from a virtual machine](/azure/network-watcher/network-watcher-nsg-flow-logging-portal#enable-nsg-flow-log) for the existing network security group for the private endpoints.

> [!NOTE]
> Keep these recommendations in mind:
>
> - You should restrict access to the logs as needed.
>
> - Logs should flow into Log Analytics and Azure Sentinel as needed.

## Step 5: Secure ingress and egress for Azure PaaS services

This section contains two steps needed to secure ingress and egress for your PaaS Services:

- Deploy private endpoints for ingress to your services.
- Deploy VNet integration to allow your Application Service to talk to your VNet.

In addition, you should also consider your DNS configuration to allow for the resolution of names.

### Deploy private endpoints for ingress

While many services allow you to create private endpoints from the resource-specific blade in the Azure portal, a more consistent experience is to create a private endpoint from its own resource creation. To do so, resources should already be deployed. Once deployed, you can [create the private endpoint](/azure/private-link/create-private-endpoint-portal?tabs=dynamic-ip#create-a-private-endpoint).

When deploying the private endpoints, configure them as follows:

- Place them in the specific resource group that houses the parent resources to keep resources with a similar lifecycle together and to provide central access.
- Place them in the appropriate subnet in the VNet based on their role.
- For the Azure Application Service, you can configure private endpoints both for its normal frontend and its SCM endpoint, which is used for deployments and management.

Also, as part of this deployment, you should ensure that the service-specific firewall is set to deny inbound traffic. This will deny any attempts at public ingress.

For the Azure SQL database, [manage its server-level IP firewall rules](/azure/azure-sql/database/firewall-configure). Ensure that *Public network access* is set to **Disable** from the networking panel in the Azure portal.

For the Azure Application Service, adding the private endpoint sets its service level firewall to block inbound access by default. For more information, see [Using Private Endpoints for App Service apps](/azure/app-service/networking/private-endpoint).

### Deploy VNet integration for egress

In addition to the private endpoints for ingress, enable VNet integration. Each App Service Plan can have VNet integration enabled and doing so allocates a whole subnet for the App Service. For more information, see [Integrate your app with an Azure VNet](/azure/app-service/overview-VNet-integration).

To configure your App Service, see [Enable VNet integration in Azure App Service](/azure/app-service/configure-VNet-integration-enable). Ensure that you are placing it in your subnet designated for egress.

### DNS considerations

As part of using private endpoints, enable DNS resolution of the resources' FQDNs to their new private IP addresses. For the instructions to implement this in a variety of ways, see [Private Endpoint DNS configuration](/azure/private-link/private-endpoint-dns).

> [!NOTE]
> DNS resolution needs to apply to all traffic. Resources in the same VNet won't be able to resolve unless they are using the correct DNS zones.

## Step 6: Secure access to the VNet and application

Securing access to the VNet and applications include:

- Securing traffic within the Azure environment to the application
- Using multi-factor authentication (MFA) and Conditional Access policies for user access to applications.

The following diagram shows both access modes across the reference architecture.

:::image type="content" source="media/spoke-paas/azure-infra-spoke-subscription-paas-network-7.png" alt-text="Diagram of access modes in the reference architecture." lightbox="media/spoke/azure-infra-spoke-network-7.png":::

### Secure traffic within Azure environment for the VNet and application

Much of the work of security traffic within the Azure environment is already complete. See [Apply Zero Trust principles to Azure storage](azure-infrastructure-storage.md) to configure secure connections between storage resources and the VMs.

See [Apply Zero Trust principles to a hub VNet in Azure](azure-infrastructure-networking.md) to secure access from hub resources to the VNet.

### Using MFA and Conditional Access policies for user access to applications

The [Apply Zero Trust principles to virtual machines](azure-infrastructure-virtual-machines.md) article recommends how to protect access requests directly to VMs with MFA and Conditional Access. These requests are most likely from administrators and developers. The next step is to secure access to applications with MFA and Conditional Access. This applies to all users who access the application.

First, if the application isn't yet integrated with Microsoft Entra ID, see [Application types for the Microsoft identity platform](/azure/active-directory/develop/v2-app-types#daemons-and-server-side-apps).

Next, add the application to the scope of your [identity and device access policies](/microsoft-365/security/office-365-security/microsoft-365-policies-configurations).

When configuring MFA with Conditional Access and related policies, use the recommended policy set for Zero Trust as a guide. This includes **Starting point** policies that don't require managing devices. Ideally, the devices accessing your VMs are managed and you can implement the **Enterprise** level, which is recommended for Zero Trust. For more information, see [Common Zero Trust identity and device access policies](/microsoft-365/security/office-365-security/identity-access-policies).

The following diagram shows the recommended policies for Zero Trust.

:::image type="content" source="media/identity-device-access-policies-byplan.png" alt-text="Diagram of recommended identity and device access policies for Zero Trust." lightbox="media/identity-device-access-policies-byplan.png":::

## Step 7: Enable advanced threat detection and protection

Your spoke VNet built on Azure may be protected by [Microsoft Defender for Cloud](/azure/defender-for-cloud/defender-for-cloud-introduction) as other resources from your IT business environment running on Azure or on-premises may also be protected.

As mentioned in the other articles from this series, Defender for Cloud is a Cloud Security Posture Management (CSPM) and Cloud Workload Protection (CWP) tool that offers security recommendations, alerts, and advanced features such as [adaptive network hardening](/azure/defender-for-cloud/adaptive-network-hardening) to assist you as you progress in your cloud security journey.

This article does not describe Defender for Cloud in detail, but it is important to understand that Defender for Cloud works based on Azure policies and logs ingested in a Log Analytics workspace. Once enabled on the subscriptions with your spoke VNet and associated resources, you can see recommendations to improve their security posture. You can filter these recommendations further by MITRE tactic, Resource Group, and others. Consider prioritizing to resolve recommendations that have a greater impact on your organization's Secure Score. Here's an example.

:::image type="content" source="media/spoke/dfc-recs.png" alt-text="Example of Microsoft Defender for Cloud recommendations." lightbox="media/spoke/dfc-recs.png":::

There are Defender for Cloud plans that offer advanced workload protections that includes adaptive network hardening recommendations to improve your existing network security group rules. Here's an example.

:::image type="content" source="media\spoke\network-hardening.png" alt-text="Example of network hardening recommendations." lightbox="media\spoke\network-hardening.png":::

You can accept the recommendation by selecting **Enforce**, which will either create a new network security group rule or modify an existing one.

## Recommended training

- [Secure your Azure resources with Azure role-based access control (Azure RBAC)](/training/modules/secure-azure-resources-with-rbac/)
- [Configure and manage Azure Monitor](/training/modules/azure-monitor/)
- [Configure network security groups](/training/modules/configure-network-security-groups/)
- [Design and implement network security](/training/modules/design-implement-network-security-monitoring/)
- [Design and implement private access to Azure Services](/training/modules/design-implement-private-access-to-azure-services/)

## Next Steps

See these additional articles for applying Zero Trust principles to Azure:

- For Azure IaaS:
  - [Overview](azure-infrastructure-overview.md)
  - [Azure storage](azure-infrastructure-storage.md)
  - [Virtual machines](azure-infrastructure-virtual-machines.md)
  - [Spoke virtual networks](azure-infrastructure-iaas.md)
  - [Hub virtual networks](azure-infrastructure-networking.md)
- [Azure Virtual Desktop](azure-infrastructure-avd.md)
- [Azure Virtual WAN](azure-virtual-wan.md)
- [IaaS applications in Amazon Web Services](secure-iaas-apps.md)
- [Microsoft Sentinel and Microsoft 365 Defender](/security/operations/siem-xdr-overview)

## References

- [Embrace proactive security with Zero Trust](https://aka.ms/zerotrust)
- [Secure networks with Zero Trust](/security/zero-trust/deploy/networks)
- [Zero-trust network for web applications with Azure Firewall and Application Gateway](/azure/architecture/example-scenario/gateway/application-gateway-before-azure-firewall)
- [Azure Landing Zone Policies](https://github.com/Azure/Enterprise-Scale/wiki/ALZ-Policies)
- [Common Zero Trust identity and device across policies](/microsoft-365/security/office-365-security/identity-access-policies)
- [What is a private endpoint?](/azure/private-link/private-endpoint-overview)
- [Private endpoint DNS configuration](/azure/private-link/private-endpoint-dns)
- [Integrate your app with an Azure VNet](/azure/app-service/overview-VNet-integration)
- [Using private endpoints for App Service apps](/azure/app-service/networking/private-endpoint)
- [Connect to an Azure SQL server using an Azure private endpoint](/azure/private-link/tutorial-private-endpoint-sql-portal)
