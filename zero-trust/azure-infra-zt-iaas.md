---
title: Secure network components for an Azure IaaS app with Zero Trust
description: Learn how to secure a spoke virtual network for IaaS workloads with Zero Trust.   
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
# Secure a spoke virtual network for IaaS workloads with Zero Trust

Guidance from Azure FastTrack team:

[fta-deliveryhowto/networkingSpokeVM.md at master · Azure/fta-deliveryhowto (github.com)](https://github.com/Azure/fta-deliveryhowto/blob/master/articles/security/Zero%20Trust/Networking/networkingSpokeVM.md)

In this article, we apply the principles of zero trust to a virtual network for IaaS workloads in Azure:

- Verify explicitly
- Use least privileged access
- Assume breach

This article is part of a series of article that demonstrate how to apply the principles of Zero Trust across an environment in Azure that includes a spoke Vnet hosting a virtual machine-based workload. For more information, see Overview--Secure Azure infrastructure with Zero Trust.

## Reference architecture

The following diagram illustrates a common reference architecture for IaaS-based workloads.

![](RackMultipart20221007-1-rca6re_html_fd629ce417d977ee.gif)

In the illustration:

- A "spoke" virtual network includes components to support an IaaS application comprised of virtual machines.
- The IaaS application is a three-tier application comprised of two virtual machines for each tier—front end, application, data.
- Each tier is contained within a dedicated subnet with a dedicated network security group.
- Each virtual machine role is assigned to an application security group corresponding to its role.
- Access to the application is provided through an Application Gateway contained in its own subnet.

The application illustrated by the reference architecture follows the [N-tier architecture style - Azure Architecture Center | Microsoft Learn](/azure/architecture/guide/architecture-styles/n-tier)

The following diagram illustrates the logical architecture of these components within an Azure subscription.

![](RackMultipart20221007-1-rca6re_html_c39c6f316b33d893.gif)

In the illustration — All components of the spoke virtual network are contained in a dedicated resource group:

- One virtual network
- One Azure Application Gateway (App GW), including a Web Application Firewall (WAF)
- Three network security groups, one for each application tier
- Three application security groups, one for each tier

## In this article

Zero trust principles are applied across the architecture, from the tenant and directory level down to the assignment of virtual machines to application security groups. The following table describes the recommendations for securing this architecture.

| **Step** | **Task** |
| --- | --- |
| 1 | Leverage Azure AD RBAC or set up custom roles for networking resources |
| 2 | Isolate infrastructure into its own resource group |
| 3 | Create a network security group for each subnet |
| 4 | Create an application security group for each virtual machine role |
| 5 | Secure traffic and resources within the virtual network:
- Deploy baseline deny rules for network security groups
- Deploy application specific rules for application security groups
- Plan for management traffic into the virtual network (might be covered in subsequent section)
- Deploy network security group flow logging
 |
| 6 | Secure access to the virtual network and application |
| 7 | Set up secure maintenance of the virtual network and application? |
| 8 | Enable advanced threat detection and protection |

## Step 1. Leverage Azure AD RBAC or set up custom roles for networking resources

You can leverage [Azure AD RBAC built-in roles](/azure/role-based-access-control/built-in-roles#network-contributor) for network contributors. However, another approach is to leverage custom roles. Spoke network managers do not need the full access to networking resources granted by the Azure AD RBAC Network Contributor role, but need more permissions than other common roles. A custom role can be used to scope access to just what is needed.

One easy way to implement this is to deploy the custom roles found in the Azure Landing Zone Reference Architecture: [ALZ-Bicep/infra-as-code/bicep/modules/customRoleDefinitions at main · Azure/ALZ-Bicep (github.com)](https://github.com/Azure/ALZ-Bicep/tree/main/infra-as-code/bicep/modules/customRoleDefinitions).

The specific role that can be used is the **Network Management** custom role, that has the following permissions:

- Read all in the scope
- Any actions with the network provider
- Any actions with the support provider
- Any actions with the Resources provider

This role can be created using the scripts in the above repository, or can be created through Azure Active Directory by the following process with the above scopes: [Azure custom roles - Azure RBAC | Microsoft Docs](/azure/role-based-access-control/custom-roles).

## Step 2. Isolate infrastructure into its own resource group

By isolating network resources from compute, data, or storage resources, you reduce the likelihood of permissions bleed. In addition, by ensuring that all related resources are in one resource group, you can make one security assignment and better manage logging and monitoring to these resources.

Rather than have the spoke network resources be available in multiple contexts in a shared resource group, create a resource group just for it. The reference architecture that this article supports illustrates this concept.

![](RackMultipart20221007-1-rca6re_html_715c81dd6f1dfb23.gif)

In the illustration — Resources and components across the reference architecture are divided into dedicated resource groups for virtual machines, storage accounts, hub virtual network resources, and spoke virtual network resources.

With a dedicated resource group, you can assign a custom role using the following process: [Tutorial: Grant a user access to Azure resources using the Azure portal - Azure RBAC | Microsoft Docs](/azure/role-based-access-control/quickstart-assign-role-user-portal).

Additional recommendations:

- Reference a Security Group for the role instead of named individuals.
- Manage access to the security group through your enterprise identity management patterns.

If you are not already using policies that enforce log forwarding on resource groups, configure this in the Activity log for the resource group (navigate to  **Activity log -\> Export Activity Logs**  and then select **+ Add diagnostic setting)**.

On the Diagnostic setting screen, select all log categories (but especially Security!) and send them to the appropriate logging sources, such as a Log Analytics workspace for observability, or a storage account for long term storage.

![](RackMultipart20221007-1-rca6re_html_55b03949e8d6d276.png)

Read more about [Diagnostic Settings](/azure/azure-monitor/essentials/diagnostic-settings) to understand how to review these logs and alert on them.

## Step 3. Create a network security group for each subnet

Azure network security groups are used to filter network traffic between Azure resources in an Azure virtual network. A network security group contains security rules that allow or deny inbound network traffic to, or outbound network traffic from, several types of Azure resources. For each rule, you can specify source and destination, port, and protocol.

For a multi-tier virtual-machine based application, the recommendation is to create a dedicated network security group (NSG in the illustration below) for each subnet that hosts a virtual machine role.

![](RackMultipart20221007-1-rca6re_html_41be6b6ae806a72c.gif)

In the illustration:

- Each tier of the application is hosted in a dedicated subnet – web tier, app tier, data tier.
- A network security group (NSG) is configured for each of these subnets.

Configuring network security groups in a different way than illustrated above can result in incorrect configuration of some or all of the network security groups and can create issues in troubleshooting. It can also make it difficult to monitor and log.

Create a network security group using this process: [Create, change, or delete an Azure network security group](/azure/virtual-network/manage-network-security-group)

Read more about [Network security groups](/azure/virtual-network/network-security-groups-overview) to understand how they can be used to secure the environment.

## Step 4. Create an application security group for each virtual machine role

Application security groups enable you to configure network security as a natural extension of an application's structure, allowing you to group virtual machines and define network security policies based on those groups. You can reuse your security policy at scale without manual maintenance of explicit IP addresses. The platform handles the complexity of explicit IP addresses and multiple rule sets, allowing you to focus on your business logic.

Inside of your workload, identify the specific virtual machine roles. Then, build an application security group for each role. In our reference architecture, three application security groups are represented.

![](RackMultipart20221007-1-rca6re_html_d4083e8b3a6baa0e.gif)

In the illustration:

- Three application security groups are created to support this app, one for each tier – web, app, data.
- Each virtual machine is assigned to the corresponding application security group for its role (red text in the illustration).

For more information about application security groups and how to assign these to virtual machines, see [Azure application security groups overview | Microsoft Learn](/azure/virtual-network/application-security-groups).

**Note:**  If you are using load balancers, using the IP address of the load balancer in the NSGs are needed as ASGs cannot scope a Load Balancer.

## Step 5. Secure traffic and resources within the virtual network

In this section we cover the following recommendations:

- Deploy baseline deny rules for network security groups
- Deploy application specific rules for application security groups
- Plan for management traffic into the virtual network
- Deploy network security group flow logging

## Deploy baseline deny rules for network security groups

A key element of zero trust is using the least level of access needed. By default, network security groups have allowed rules. By adding a baseline of deny rules, we can enforce the least level of access.

Once provisioned, create a deny all Rule in each of the inbound and outbound rules, with a priority of 4096. This is the last custom priority available, so it means you still have the remaining scope to configure allow actions.

To do this, in the Network Security Group go to **Outbound Security Rules** , select **Add**. Fill in the following:

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

![](RackMultipart20221007-1-rca6re_html_bb1f1df734d73940.png)

Repeat this process with Inbound rules, adjusting the name and description as appropriate.

You will notice that, on the Inbound security rules tab, you will see a warning sign on the rule.

![](RackMultipart20221007-1-rca6re_html_9ea6360f1095dcac.png)

If you click on the rule, and scroll to the bottom, you will see more details:

![](RackMultipart20221007-1-rca6re_html_d91193330ba727c5.png)

This message is warning us of two things:

- Azure Load Balancers will not, by default, be able to access resources using this NSG.
- Other resources on this virtual network will not, by default, be able to access resources using this NSG.

For our purposes in Zero Trust, this is _excellent_. It means that just because something is on this virtual network, does not mean that it will have immediate access to our resources! For each traffic pattern, we will need to create a rule explicitly allowing it, and we should do so with the least amount of permissions.

This will mean that if we have specific outbound connections for management, such as to Active Directory Domain Controllers, private DNS VMs, or to specific external websites, they will need to be controlled here.

### **Alternative Deny Rules**

If you are using Azure Firewall to manage your outbound connections, then instead of performing a deny outbound all, you can leave all outbound open. As part of the Azure Firewall implementation, you will set up a route table that will send the default route (0.0.0.0/0) to the Firewall. This will handle traffic outside of the virtual network.

You can then either create a deny all vnet outbound, or instead allow all outbound (but secure items with their inbound rules).

Read more about [Azure Firewall](/azure/firewall/overview) and [Route Tables](/azure/virtual-network/manage-route-table) to understand how they can be used to further increase the security of the environment.

### **VM Management Rules**

To configure VMs with Azure AD Login, Anti-Malware, and automatic updates enabled, you will need to allow the following outbound connections. Many of these are by FQDN, meaning that either Azure Firewall is needed for FQDN rules, or you will make a more complex plan.

Azure firewall is recommended.

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

## Deploy application specific rules for application security groups

Define traffic patterns with the least amount of permissions, and only following explicitly allowed paths. Using the application security groups in this example, define networking patterns in the network security groups.

![](RackMultipart20221007-1-rca6re_html_6741f07733a9ade7.png)

This results in the following rules:

- Allowing internet traffic into the DMZ Load Balancer (HTTPS 443)
- Allowing traffic from the DMZ NVAs to the Web tier Load Balancer (HTTPS 433)
- Allowing traffic from the Web tier VMs to the Business tier Load Balancer (HTTPS 443)
- Allowing traffic from the Business tier VMs to the Data tier Load Balancer (SQL 1433)
- Allowing traffic from the Data tier Load Balancer to the Data tier VMs. (SQL 1433)

Presumably, we also need the SQL servers to communicate with each other over SQL 1433.

Configure the SQL pattern first, and then repeat this process with the remaining tiers.

### Rule 1-- Allow traffic from the Business tier VMs to the Data tier Load Balancer (SQL 1433)

Inside of the NSG, Navigate to Inbound Security Rules, and select Add. Populate the list with the following:

- Source: Application Security Group
- Source application security groups: Select your business tier ASG
- Source port ranges: 1433 (Sometimes source traffic can come from different ports, and if this pattern occurs you can add source port ranges to \* to allow any source port. Destination port is more significant, and some recommendations are to always use \* for source port)
- Destination: IP addresses
- Destination IP addresses/CIDR ranges: the explicit IP of the load balancer
  - We need to use the explicit IP here because we cannot associate a Load Balancer with an ASG.
  - You can plan for this in your IP schema, or deploy the load balancer and refer to the IP it is assigned.
- Service: MS SQL
- Destination Port Ranges: This will be automatically filled in for port 1433
- Protocol: This will be automatically selected for TCP
- Action: Allow
- Priority: A value between 100 and 4096. We can start with 105.
- Name: AllowBusinesstoSQLLBInbound
- Description: Allows inbound access to the SQL Load Balancer from Business Tier Virtual Machines

You will notice after completion that there will be a blue icon for informational alerts on the rule. Clicking into the rule will reveal the following message—"Rules using application security groups may only be3 applied when the ASGs are associated with network interfaces on the same virtual network."

![](RackMultipart20221007-1-rca6re_html_1147d9069c17755e.png)

For our purposes this is excellent. The rule will only be applied when this ASG is used in this network.

Finally, inside of the NSG, Navigate to Outbound Security Rules, and select Add. Populate the list similar to the above, changing the Inbound to Outbound.

### Rule 2 — Allow traffic from the Data tier Load Balancer to the Data tier VMs. (SQL 1433)

Inside of the NSG, Navigate to Inbound Security Rules, and select Add. Populate the list with the following:

- Source: IP Address
- Source IP Address: The IP address of the load balancer
- Source port ranges: 1433
- Destination: Application security group
- Destination application security groups: Select your data tier ASG
- Service: MS SQL
- Destination Port Ranges: This will be automatically filled in for port 1433
- Protocol: This will be automatically selected for TCP
- Action: Allow
- Priority: A value between 100 and 4096. We can start with 105.
- Name: AllowSQLLBtoSQLVMInbound
- Description: Allows inbound access to the SQL Tier Virtual Machines from the SQL Load Balancer.

Inside of the NSG, Navigate to Outbound Security Rules, and select Add. Populate the list similar to the above, changing the Inbound to Outbound.

### Rule 3 — Allow traffic from the Data tier VMs to the Data tier VMs. (SQL 1433)

Inside of the NSG, Navigate to Inbound Security Rules, and select Add. Populate the list with the following:

- Source: Application security group
- Destination application security groups: Select your data tier ASG
- Source port ranges: 1433
- Destination: Application security groups
- Destination application security groups: Select your data tier ASG
- Service: MS SQL
- Destination Port Ranges: This will be automatically filled in for port 1433
- Protocol: This will be automatically selected for TCP
- Action: Allow
- Priority: A value between 100 and 4096. We can start with 105.
- Name: AllowSQLVMtoSQLVMInbound
- Description: Allows inbound access between SQL Tier VMs.

Inside of the NSG, Navigate to Outbound Security Rules, and select Add. Populate the list similar to the above, changing the Inbound to Outbound.

With these three rules, you have defined the Zero Trust connectivity pattern for a single application tier. You can repeat this process as needed for additional flows.

## Plan for management traffic into the virtual network

In addition to the application specific traffic, management traffic may be needed. However, management traffic generally originates outside of our spoke virtual network. Additional rules will be needed. First, you will need to understand the specific ports and sources that management traffic will be coming from. Generally, all management traffic should flow from a firewall or other NVA located in the hub network for the spoke (see the full reference architecture in the overview article).

This will vary based on your specific management needs, but both rules on the firewall appliances and rules on the NSG should be used to explicitly allow connections on both the platform networking side, and the workload networking side.

There may be specific management rules for Azure virtual machines that we would advocate whitelisting, but those would be a future increment of this.

## Deploy network security group flow logging

Just because we have a network security group that is blocking unneeded traffic doesn't mean that our goals are met. We still need to observe where traffic is occurring outside of our explicit patterns, so that we understand if an attack is occurring.

To enable Network Security Group Flow Logging, you can follow the [Tutorial: Log network traffic flow to and from a virtual machine](/azure/network-watcher/network-watcher-nsg-flow-logging-portal#enable-nsg-flow-log) against the existing network security group we created.

There are a few notes to this process:

- The storage account should follow the Zero Trust storage account guidance.
- Access to the logs should be restricted as needed.
- They should also flow in to Log Analytics and Sentinel as needed.

# Step 6. Secure access to the virtual network and application

Securing access to the virtual network and application includes:

- Securing traffic within the Azure environment to the application
- Using multi-factor authentication and conditional access policies for user access to the application.

The following diagram illustrates both of these access modes across the reference architecture.

![](RackMultipart20221007-1-rca6re_html_e6dd26d5a5300e92.gif)

## Secure traffic within the Azure environment to the virtual network and application

Much of the work of security traffic within the Azure environment is already complete. Secure connections between storage resources and the virtual machines are configured in Secure storage with Zero Trust.

Securing access from Hub resources to the virtual network is configured in Secure a Hub virtual network with Zero Trust.

Anything else?

## Using multi-factor authentication and conditional access policies for user access to the application

The article, Secure virtual machines with Zero Trust, recommends how to protect access requests directly to virtual machines with multi-factor authentication and conditional access. These requests are most likely from administrators and developers. The next step is to secure access to the application with multi-factor authentication and conditional access. This applies to all users who access the app.

First, if the application is not yet integrated with Azure AD, see [Application types for the Microsoft identity platform](/azure/active-directory/develop/v2-app-types#daemons-and-server-side-apps).

Next, add the application to the scope of your identity and device access policies.

When configuring multi-factor authentication with conditional access and related policies, use the recommended policy set for Zero Trust as a guide. This includes "Starting point" policies that don't require managing devices. Ideally, the devices accessing your virtual machines are managed and you can implement the "Enterprise" level, which is recommended for Zero Trust. For more information, see [Common Zero Trust identity and device access policies](/microsoft-365/security/office-365-security/identity-access-policies).

The following diagram illustrates the recommended policies for Zero Trust.

![](RackMultipart20221007-1-rca6re_html_e25aeacb4e0ece1f.png)

# Step 7. Set up secure maintenance of the virtual network and application?

# Step 8. Enable advanced threat detection and protection