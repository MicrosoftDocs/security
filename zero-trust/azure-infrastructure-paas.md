---
title: Apply Zero Trust Principles to a spoke virtual network with Azure PaaS Services
description: Learn how to secure a spoke virtual network for PaaS workloads with Zero Trust.   
ms.date: 
ms.service: security
author: brsteph
ms.author: bstephenson
ms.topic: conceptual
ms.collection: 
  - msftsolution-azurepaas
  - msftsolution-scenario
  - zerotrust-solution
---

# Apply Zero Trust Principles to a spoke virtual network with Azure PaaS Services

This article will help you apply the principles of Zero Trust security model to a PaaS workload using Azure virtual networks and private endpoints.

| **Zero Trust Principle** | **Met by** |
| --- | --- |
| Verify Explicitly | Use threat detection in Azure Firewall and Azure Application Gateways to validate traffic and to verify if the traffic is acceptable. |
| Use Least Privileged Access | Reduce ingress to and egress from Azure services to your private networking.  Use Network Security Groups to allow only specific ingress from your vnet.  Use a central Azure Firewall instance to grant non-vnet traffic access to the Azure service. |
| Assume Breach | Limit unnecessary communication between resources. Ensure that you are logging from Network Security Groups and that you have proper visibility into anomalous traffic. Track changes to Network Security Groups. |

This article is a part of a series that demonstrates how to apply the Zero Trust principles across an Azure environment with a spoke virtual network (VNet) hosting a VM-based workload. For more information, see [Overview – Apply Zero Trust principles to Azure infrastructure](azure-infrastructure-overview.md).

## Zero Trust Stand Alone or Spoke Network for PaaS Services

Many PaaS services contain their own, service-native ingress and egress functionality.  These services have controls can be used to secure network access to these resources without the need of infrastructure such as virtual networks.

For example:

- Azure SQL Database has its own firewall that can be used allow specific client IPs that need to access the database server.
- Storage Account has the option to configure if you allow connections from a specific VNet or block the public network access.  
- Azure App Service you can set up access restrictions to define a priority-ordered allow/deny list that controls network access to your app.  

However, for Zero Trust guided implementations, these service-native access controls often fall short of being sufficient. This creates a diffusion of access controls and logging that can increase management and decrease visibility.

In addition, the PaaS services use a FQDN that resolved to a dynamically assigned public IP, allocated from a pool of public IPs in a specific region for a type of service. Because of this, you won't be able to allow traffic from/to a specific PaaS service by using their public IP, which can change.

It's recommended for organizations to use [Private Endpoints](https://learn.microsoft.com/azure/private-link/private-endpoint-overview). A Private Endpoint is a virtual network interface that uses a private IP address from your virtual network. This network interface connects you privately and securely to a service that's powered by Azure Private Link. By enabling a private endpoint, you're bringing the service into your virtual network.

Depending on your solution scenario, you may still need public ingress access to your PaaS services, but unless you do, it's recommended that all traffic remain private, to eliminate potential risks.

This guide provides instructions for a specific reference architecture, but the principles and methods can be applied to any other architecture as needed.

## Reference architecture

The following diagram illustrates a common reference architecture for PaaS-based workloads.

:::image type="content" source="media/spoke-PaaS/azure-infra-spoke-subscription-paas-architecture-1.png" alt-text="Diagram of reference architecture for IaaS-based workloads.":::

:::image type="content" source="media/spoke-paas/azure-infra-spoke-subscription-paas-architecture-2.png" alt-text="Diagram of reference architecture for IaaS-based workloads.":::

In the illustration:

- A "spoke" virtual network includes components to support a PaaS application comprised of virtual machines.
- The PaaS application is a two-tier application leveraging Azure Application Services for a web app/front end, and an Azure SQL Database for relational databases.
- Each tier is contained within a dedicated subnet for ingress with a dedicated network security group.
- The web tier contains a dedicated subnet for egress.
- Access to the application is provided through an Application Gateway contained in its own subnet.

The following diagram illustrates the logical architecture of these components within an Azure subscription.

:::image type="content" source="media/spoke-paas/azure-infra-spoke-subscription-paas-architecture-3.png" alt-text="Diagram of components within an Azure subscription.":::

In the illustration, all components of the spoke virtual network are contained in a dedicated resource group:

- One virtual network
- One Azure Application Gateway (App GW), including a Web Application Firewall (WAF)
- Three network security groups, one for the database tier and two for the application tier
- Two private endpoints

In addition, resources for the hub virtual network are deployed in the appropriate connectivity subscription.

## What's in this article

Zero Trust principles are applied across the architecture, from the tenant and directory level down to the assignment of virtual machines to application security groups. The following table describes the recommendations for securing this architecture.

| Step | Task |
| --- | --- |
| 1 | Leverage Azure AD RBAC or set up custom roles for networking resources. |
| 2 | Isolate infrastructure into its own resource group. |
| 3 | Create a network security group for each subnet. |
| 4 | Secure traffic and resources within the virtual network: <li> Deploy baseline deny rules for network security groups <li> Plan for management traffic into the virtual network <li> Deploy network security group flow logging |
| 5 | Secure Ingress and Egress for Azure PaaS Services  |
| 6 | Secure access to the virtual network and application. |
| 7 | Enable advanced threat detection, alerting, and protection. |

This guide assumes that you already have an Azure Application Service and Azure SQL Database deployed in their own resource groups.

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

:::image type="content" source="media/spoke-paas/azure-infra-spoke-subscription-paas-architecture-3.png" alt-text="Diagram of isolate infrastructure into its own resource group." lightbox="media/spoke-paas/azure-infra-spoke-subscription-paas-architecture-3.png":::

In the illustration, resources and components across the reference architecture are divided into dedicated resource groups for application services, Azure SQL databases, storage accounts, hub virtual network resources, and spoke virtual network resources.

With a dedicated resource group, you can assign a custom role using the following process: [Tutorial: Grant a user access to Azure resources using the Azure portal - Azure RBAC | Microsoft Docs](/azure/role-based-access-control/quickstart-assign-role-user-portal).

Additional recommendations:

- Reference a security group for the role instead of named individuals.
- Manage access to the security group through your enterprise identity management patterns.

If you are not using policies that enforce log forwarding on resource groups, configure this in the Activity log for the resource group:

Navigate to **Activity log -\> Export Activity Logs** and then select **+ Add diagnostic setting**.

On the Diagnostic setting screen, select all log categories (especially Security) and send them to the appropriate logging sources, such as a Log Analytics workspace for observability, or a storage account for long term storage.

### Subscription Democratization

While not directly related to networking, you should plan your subscription RBAC in a similar way. In addition to isolating resources logically by resource group, you should also isolate the subscription based on business areas and portfolio owners. The subscription as a management unit should be narrowly scoped.

You can read more about subscription democratization here: [Azure landing zone design principles - Cloud Adoption Framework | Microsoft Learn](/azure/cloud-adoption-framework/ready/landing-zone/design-principles#subscription-democratization)

:::image type="content" source="media/spoke/diagnostic-setting.png" alt-text="Screenshot of Diagnostic setting." lightbox="media/spoke/diagnostic-setting.png":::

Read more about [Diagnostic Settings](/azure/azure-monitor/essentials/diagnostic-settings) to understand how to review these logs and alert on them.

## Step 3. Create a network security group for each subnet

Azure network security groups (NSGs) are used to filter network traffic between Azure resources in an Azure virtual network. It is recommended to apply a NSG to each subnet. This is enforced through Azure policy by default when deploying Azure Landing Zones. A network security group contains security rules that allow or deny inbound network traffic to, or outbound network traffic from, several types of Azure resources. For each rule, you can specify source and destination, port, and protocol.

For a multi-tier applications, the recommendation is to create a dedicated network security group (NSG in the illustration below) for each subnet that hosts a a networking component.

:::image type="content" source="media/spoke-paas/azure-infra-spoke-subscription-paas-nsg-4.png" alt-text="Diagram of dedicated NSG.":::

In the illustration:

- Each tier of the application has a dedicated ingress subnet such as one for web tier and data tier.
- Azure Application Services has a dedicated egress subnet for a specific application service.
- A network security group (NSG) is configured for each of these subnets.

Configuring network security groups in a different way than illustrated above can result in incorrect configuration of some or all of the network security groups and can create issues in troubleshooting. It can also make it difficult to monitor and log.

Create a network security group using this process: [Create, change, or delete an Azure network security group](/azure/virtual-network/manage-network-security-group)

Read more about [Network security groups](/azure/virtual-network/network-security-groups-overview) to understand how they can be used to secure the environment.

## Step 4. Secure traffic and resources within the virtual network

This section covers the following recommendations:

- Deploy baseline deny rules for network security groups
- Deploy application specific rules
- Plan for management traffic in the virtual network
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

Repeat this process with inbound rules, adjusting the name and description as appropriate.

You will notice that on the Inbound security rules tab, you will see a warning sign on the rule.

:::image type="content" source="media/spoke/outbound-sec-rules-1.png" alt-text="Screenshot of inbound security rules." lightbox="media/spoke/outbound-sec-rules-1.png":::

If you click the rule and scroll to the bottom, you will see more details:

:::image type="content" source="media/spoke/rule-details.png" alt-text="Screenshot of rule details.":::

This message gives the following two warnings:

- Azure Load Balancers will not, by default, be able to access resources using this NSG.
- Other resources on this virtual network will not, by default, be able to access resources using this NSG.

For our purpose in Zero Trust, this is how it should be. It means that just because something is on this virtual network, doesn't mean that it will have immediate access to your resources! For each traffic pattern, you will need to create a rule explicitly allowing it and you should do so with the least amount of permissions.

Thus if you have specific outbound connections for management, such as to Active Directory Domain Controllers, private DNS VMs, or to specific external websites, they need to be controlled here.

### Alternative Deny Rules

The following applies only to the web-egress subnet.

If you are using Azure Firewall to manage your outbound connections, then instead of performing a deny outbound all, you can create alternate rules for outbound connections. As a part of the Azure Firewall implementation, you will set up a route table that will send the default route (0.0.0.0/0) to the firewall. This will handle traffic outside of the virtual network.

You can then either create a deny all vnet outbound, or instead allow all outbound (but secure items with their inbound rules).

Read more about [Azure Firewall](/azure/firewall/overview) and [Route Tables](/azure/virtual-network/manage-route-table) to understand how they can be used to further increase the security of the environment.

### Deploy application specific rules

Define traffic patterns with the least amount of permissions and only following explicitly allowed paths. Using subnets as sources, define networking patterns in the network security groups.

:::image type="content" source="media/spoke-paas/azure-infra-spoke-subscription-paas-tiers-6.png" alt-text="Diagram of networking patters in NSG." lightbox="media/spoke-paas/azure-infra-spoke-subscription-paas-tiers-6.png":::

Use the following process to add rules to your Network Security Groups: [Manage network security groups: Create a security rule](https://learn.microsoft.com/azure/virtual-network/manage-network-security-group?tabs=network-security-group-portal#create-a-security-rule)

To secure this scenario, you will need to add the following rules:

| NSG for Subnet | Direction | Source | Source Details | Source Port | Destination | Destination Details | Service | NSG Name | NSG Description
| - | - | - | - | - | - | - | - | - |- |
| App Service Subnet | Inbound | IP Addresses | Your Application Gateway Subnet's Private IP Range | 443 | IP Addresses | The explicit IP of your App Service's Private Endpoint | MS SQL | AllowGWtoAppInbound | Allows inbound access to the App Service from the Application Gateway. |
| App Service Integration Subnet | Outbound | IP Addresses | Your App Service Integration Subnet's IP Range | 1433 | IP Addresses | The explicit IP of your SQL DB's Private Endpoint | MS SQL | AllowApptoSQLDBOutbound | Allows outbound access to the SQL Private Endpoint from App Service Integration subnet.
| Azure SQL Subnet | Inbound | IP Addresses | Your App Service Integration Subnet's IP Range | 1433 | IP Addresses | The explicit IP of your SQL DB's Private Endpoint | MS SQL | AllowApptoSQLDBInbound | Allows inbound access to the SQL Private Endpoint from App Service Integration subnet.

>[!NOTE] Sometimes source traffic can come from different ports and if this pattern occurs you can add source port ranges to \* to allow any source port. Destination port is more significant and some recommendations are to always use \* for source port.

>[!NOTE]For priority, use a value between 100 and 4000. You can start with 105.

This is in addition to the NSG rules on your Application Gateway Subnet.

With these rules, you have defined the Zero Trust connectivity pattern for a single application tier. You can repeat this process as required for additional flows.

### Plan for management traffic in the virtual network

In addition to the application specific traffic, you need to plan for management traffic. However, management traffic generally originates outside of the spoke virtual network. Additional rules are required. First, you will need to understand the specific ports and sources that management traffic will be coming from. Generally, all management traffic should flow from a firewall or other NVA located in the hub network for the spoke.

See the full reference architecture in the [Overview – Apply Zero Trust principles to Azure infrastructure](azure-infrastructure-overview.md) article.

This will vary based on your specific management needs. However, rules on the firewall appliances and rules on the NSG should be used to explicitly allow connections on both the platform networking side and the workload networking side.

### Planning for deployments

Because your Application Services and Databases are now using private networking, you will need to plan for how deployments of code and data to these resources will operate.  You will need to add additional rules to allow your private build servers to access these endpoints.

### Deploy network security group flow logging

Even if your network security group is blocking unnecessary traffic doesn't mean that your goals are met. You still need to observe the traffic occurring outside your explicit patterns, so that you know if an attack is occurring.

The traffic to the Private Endpoints will *not* be logged, but if other services are deployed to the subnets later this log will help detect the activities.

To enable Network Security Group Flow Logging, you can follow the [Tutorial: Log network traffic flow to and from a virtual machine](/azure/network-watcher/network-watcher-nsg-flow-logging-portal#enable-nsg-flow-log) against the existing network security group that is created.

> [!NOTE]
> - Access to the logs should be restricted as needed.
> - They should also flow in to Log Analytics and Sentinel as needed.

## Step 5. Secure Ingress and Egress for Azure PaaS Services

This section contains two steps needed to secure ingress and egress for your PaaS Services:

- Deploy Private Endpoints for Ingress to your services.
- Deploy Vnet Integration to allow your Application Service to talk to your virtual network.

In addition, you should also consider your DNS configuration to allow for the resolution of names.

### Deploy Private Endpoints for Ingress

While many services allow you to create Private Endpoints from the resource specific blade, a more consistent experience is to create a Private Endpoint from its own resource creation.  To do so, you will need the resources already deployed.  Once done, you can [create the private endpoint](https://learn.microsoft.com/azure/private-link/create-private-endpoint-portal?tabs=dynamic-ip#create-a-private-endpoint).

When deploying the Private Endpoints, configure them as follows:

- Place them in the specific resource group that houses the parent resources, to keep resources with a similar lifecycle together and to provide central access.
- Place them in the appropriate subnet in the virtual network based on their role.
- For the Azure Application Service, you can configure private endpoints both for its normal frontend and its SCM endpoint, which is used for deployments and management.

Also as part of this deployment, you should ensure that the service specific firewall is set to deny inbound traffic.  This will deny any attempts at public ingress.

For the Azure SQL Database, you will need to [manage its server-level IP firewall rules](https://learn.microsoft.com/azure/azure-sql/database/firewall-configure?view=azuresql#use-the-azure-portal-to-manage-server-level-ip-firewall-rules).  Ensure that *Public network access* is set to **Disable** from the networking panel.

For the Azure Application Service, adding the Private Endpoint will set its service level firewall to block inbound access by default.  You can read more about this at [Using Private Endpoints for Azure Web Apps](https://learn.microsoft.com/azure/app-service/networking/private-endpoint)

### Deploy Vnet Integration for Egress

In addition to the Private Endpoints for ingress, you will also need to enable Vnet Integration.  Each App Service Plan can have Vnet Integration enabled, and doing so allocates a whole subnet to be used for the App Service.  You can read more about this service and how it operates in the article [Integrate your app with an Azure virtual network](https://learn.microsoft.com/azure/app-service/overview-vnet-integration).

You can follow the instructions to [Enable virtual network integration in Azure App Service](https://learn.microsoft.com/azure/app-service/configure-vnet-integration-enable) to configure your Application Service.  Ensure that you are placing it in your subnet designated for egress.

### DNS Considerations

As part of using Private Endpoints, you will need to enable DNS resolution of the resources' fully qualified domain names to their new private IPs.  You can find instructions for implementing this in a variety of ways in the article for [Private Endpoint DNS configuration](https://learn.microsoft.com/azure/private-link/private-endpoint-dns).

Note that this needs to apply to all traffic; resources in the same virtual network won't be able to resolve unless they are using the correct zones.

## Step 6. Secure access to the virtual network and application

Securing access to the virtual network and application includes:

- Securing traffic within the Azure environment to the application
- Using multi-factor authentication and conditional access policies for user access to the application.

The following diagram illustrates both these access modes across the reference architecture.

:::image type="content" source="media/spoke-paas/azure-infra-spoke-subscription-paas-network-7.png" alt-text="Diagram of access modes in reference architecture." lightbox="media/spoke/azure-infra-spoke-network-7.png":::

### Secure traffic within Azure environment for the virtual network and application

Much of the work of security traffic within the Azure environment is already complete. Secure connections between storage resources and the virtual machines are configured in [Apply Zero Trust principles to Azure storage](azure-infrastructure-storage.md).

Securing access from Hub resources to the virtual network is configured in [Apply Zero Trust principles to a hub virtual network in Azure](azure-infrastructure-networking.md).

### Using multi-factor authentication and conditional access policies for user access to the application

The article, [Apply Zero Trust principles to virtual machines(VM)](azure-infrastructure-virtual-machines.md) recommends how to protect access requests directly to virtual machines with multi-factor authentication and conditional access. These requests are most likely from administrators and developers. The next step is to secure access to the application with multi-factor authentication and conditional access. This applies to all users who access the app.

First, if the application is not yet integrated with Azure AD, see [Application types for the Microsoft identity platform](/azure/active-directory/develop/v2-app-types#daemons-and-server-side-apps).

Next, add the application to the scope of your identity and device access policies.

When configuring multi-factor authentication with conditional access and related policies, use the recommended policy set for Zero Trust as a guide. This includes "Starting point" policies that don't require managing devices. Ideally, the devices accessing your virtual machines are managed and you can implement the "Enterprise" level, which is recommended for Zero Trust. For more information, see [Common Zero Trust identity and device access policies](/microsoft-365/security/office-365-security/identity-access-policies).

The following diagram illustrates the recommended policies for Zero Trust.

:::image type="content" source="media/identity-device-access-policies-byplan.png" alt-text="Diagram of authentication with conditional access." lightbox="media/vm/identity-device-access-policies-byplan.png":::

## Step 7. Enable advanced threat detection and protection

Your Spoke virtual network built on Azure may be protected by Microsoft Defender for Cloud (MDC) as other resources from your IT business environment running on Azure or on-premises may also be protected.

As mentioned in the other articles from this series, Microsoft Defender for Cloud is a Cloud Security Posture Management (CSPM) and Cloud Workload Protection (CWP) tool that offers Security Recommendations, Alerts, and advanced features such as [Adaptive Network Hardening](/azure/defender-for-cloud/adaptive-network-hardening) to assist you as you progress in your Cloud Security journey. To better visualize where Defender for Cloud fits into the greater Microsoft security landscape, see [Microsoft Cybersecurity Reference Architectures](/security/cybersecurity-reference-architecture/mcra).

This article is not going to cover Microsoft Defender for Cloud in detail, but it is important to understand that Microsoft Defender for Cloud works based on Azure Policies and logs ingested in a Log Analytics workspace. Once enabled on the subscription(s) with your spoke virtual network and associated resources, you will be able to see Recommendations to improve their Security Posture. You can filter these Recommendations further by MITRE tactic, Resource Group, etc. Consider prioritizing to resolve Recommendations that have a greater impact on your organization's Secure score.

:::image type="content" source="media/spoke/dfc-recs.png" alt-text="Screenshot of MDC recommendations." lightbox="media/spoke/dfc-recs.png":::

If you choose to onboard one of the Defender for Cloud plans that offer Advanced Workload Protections, it will include Adaptive Network Hardening Recommendations to improve your existing Network Security Group rules.

:::image type="content" source="media\spoke\network-hardening.png" alt-text="Screenshot of network hardening recommendations." lightbox="media\spoke\network-hardening.png":::

You can accept the recommendation by selecting **Enforce** which will either create a new NSG rule or modify an existing one.

## Recommended training

- [Secure your Azure resources with Azure role-based access control (Azure RBAC)](/training/modules/secure-azure-resources-with-rbac/)
- [Configure and manage Azure Monitor](/training/modules/azure-monitor/)
- [Configure network security groups](/training/modules/configure-network-security-groups/)
- [Design and implement network security](/training/modules/design-implement-network-security-monitoring/)
- [Secure access to your applications by using Azure identity services](/training/modules/secure-access-azure-identity-services/)
- [Design and implement private access to Azure Services](/training/modules/design-implement-private-access-to-azure-services/)

## Next Steps

This article is part of a series of articles. Given below are the links to the rest of the articles in this series:

- [Overview – Apply Zero Trust principles to Azure infrastructure](azure-infrastructure-overview.md)
- [Apply Zero Trust principles to Azure storage](azure-infrastructure-storage.md)
- [Apply Zero Trust principles to a hub virtual network in Azure](azure-infrastructure-networking.md)

## References

- [Embrace proactive security with Zero Trust](https://aka.ms/zerotrust)
- [Secure networks with Zero Trust | Microsoft Learn](/security/zero-trust/deploy/networks)
- [Zero-trust network for web applications with Azure Firewall and Application Gateway - Azure Architecture Center | Microsoft Learn](/azure/architecture/example-scenario/gateway/application-gateway-before-azure-firewall)
- [Azure Landing Zone Policies](https://github.com/Azure/Enterprise-Scale/blob/main/docs/ESLZ-Policies.md)
- [Common Zero Trust identity and device across policies](/microsoft-365/security/office-365-security/identity-access-policies)
- [What are private endpoints?](https://learn.microsoft.com/azure/private-link/private-endpoint-overview)
- [Private Endpoint DNS configuration](https://learn.microsoft.com/azure/private-link/private-endpoint-dns)
- [Integrate your app with an Azure virtual network](https://learn.microsoft.com/azure/app-service/overview-vnet-integration)
- [Using Private Endpoints for Azure Web App](https://learn.microsoft.com/azure/app-service/networking/private-endpoint)
- [Connect to an Azure SQL server using an Azure Private Endpoint](https://learn.microsoft.com/azure/private-link/tutorial-private-endpoint-sql-portal)
- 