---
title: Scenario 1. Secure Azure storage with Zero Trust
description:   
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

# Scenario 1. Secure Azure storage with Zero Trust

In this article, we apply the principles of zero trust to Azure Storage:
- Verify explicitly
- Use least privileged access
- Assume breach

Zero trust principles for Azure Storage are applied across the logical architecture, from the tenant and directory level down to the storage container at the data layer. 

The following illustration provides a reference of logical architecture components.


:::image type="content" source="media/azure-infrastructure-storage-logical-architecture-1.png" alt-text="Units of work for modernizing identity and access for Zero Trust." lightbox="media/modernize-access-control-deployment-stack-foundation.png":::

In the illustration:
- Tenant = an instance of Azure AD. It's at the "top" of a hierarchy, or Level 1 in the diagram. 
- Services/subscriptions are Level 2 in the diagram. This is the Azure subscription. Many Azure subscriptions can share the same Azure AD directory.
- A given service usually has a "sublevel" boundary, or Level 3 (L3). This boundary is useful to understand for segregation of security, policies, governance, and so on. For Azure Storage, this includes the resource group, storage account, and specific Azure Storage services, such as Blob Storage and Azure Queues. 
- Level 4 is where the actual data lives. For Azure Storage, this is the containers,for example the individual data sets that use the Blob Storage service. Each container is accessed by its unique namespace, for example https://*mystorageaccount*.blob.core.windows.net/*mycontainer*/*myblob*. This is the endpoint namespace used by accounts and applications to access and work with the data. 

This article walks through the steps to apply the principles of Zero Trust across this logical architecture.


|Step     |Task    |Description |
|---------|---------|---------|
|Step 1    |  Protect Data in all three modes: data at rest, data in transit, data in use     | These protections are configured at the Storage account level|
|Step 2    | Verify users and control access to storage data with least Privilege  | Accounts are configured in Azure AD. Use Role-base Access Control with Storage Accounts to configure granular access to components within the storage account. This step also includes recommendations for configuring shared access signatures (SAS) which allow granular control over how a client can access data. |
|Step 3    | Logically separate or segregate critical data with network Controls        | |
|Step 4    | Use Defender for Storage for automated threat detection and protection    |Microsoft Defender for Storage provides an additional layer of security intelligence that detects unusual and potentially harmful attempts to access or exploit storage accounts. |


## Step 1. Protect Data in all three modes: data at rest, data in transit, data in use 
Most of the protections for protecting data at rest, in transit, and in use are configured when you create the storage account. Use the following checklist to be sure these protections are configured.


|Item     |Description |
|---------|---------|
|Use encryption in transit     |Keep your data secure by enabling transport-level security between Azure and the client. Always use HTTPS to secure communication over the public internet. When you call the REST APIs to access objects in storage accounts, you can enforce the use of HTTPS by [requiring Secure Transfer ](/azure/storage/common/storage-require-secure-transfer)for the storage account. Any request originating from an insecure connection is rejected. <br> - This configuration is enabled by default when you deploy a new Azure Storage Account (Secure by Default)<br> - Consider applying a policy to Deny the deployment of insecure connections for Azure Storage (Secure by Design)<br> - This Configuration also requires SMB 3.0 with Encryption         |
|[Prevent anonymous public read access](/azure/storage/blobs/anonymous-read-access-prevent) | By default, public blog access is prohibited but a user with the proper permissions can configure an accessible resource. To prevent data breaches from anonymous access. You should verify explicitly who has access to your data. Preventing this at the Storage account level prevents a user from enabling this access at the container or blog level. |
|[Prevent shared key authorization](/azure/storage/common/shared-key-authorization-prevent?tabs=portal)    | This configuration will force the storage account to drop all requests made with a shared key and require Azure AD authorization instead. Azure AD is superior as you can leverage risk-based access mechanisms to harden access to data tiers.   |
|[Enforce a minimum required version of transport layer security (TLS)](/azure/storage/common/shared-key-authorization-prevent?tabs=portal)  | The highest version Azure Storage currently supports is TLS 1.2. Enforcing a minimum TLS version will reject request from clients using the older version.   |
|Define the scope for copy operations    |  Restrict copy operations from source storage accounts that are within the same Azure AD tenant or that have a [private link](/azure/storage/common/storage-network-security?tabs=azure-portal) to the same virtual network as this storage account.       |
|Understand how encryption at rest works |All data written to Azure Storage is automatically encrypted by [Storage Service Encryption (SSE)](/azure/security/fundamentals/encryption-atrest) with a 256-bit Advanced Encryption Standard (AES) cipher. SSE automatically encrypts data when writing it to Azure Storage. When you read data from Azure Storage, Azure Storage decrypts the data before returning it. This process incurs no additional charges and doesn't degrade performance. Using CMKs provides additional capabilities to control rotation of the key encryption key or cryptographically erase data.         |


## Step 2. Verify users and control access to storage data with least Privilege

First, Use Azure Active Directory to govern access to storage accounts. Using [Role-based Access Control with Storage Accounts](/azure/storage/blobs/authorize-access-azure-active-directory) allows you to granularly allow access based job function leveraging OAuth 2.0. You can align your granular access to your Conditional Access Policy (see Identity Zero Trust).

List of Storage Account Roles for granular access:
- Storage Account Backup Operator -
- Storage Account Contributor -
- Storage Blob Data Contributor - read, write, and delete  - Azure Storage containers and blobs
- Storage Blob Data Owner - full access to Azure Storage blob containers and data
- Storage Blob Data Reader - read and list Azure Storage containers and blobs.
-  Storage Blog Delegator – get a user delegation key, which can then be used to create a shared access signature for a container or blob that is signed with Azure AD credentials.
- Storage File Data SMB Share Contributor - read, write, and delete access on files/directories in Azure file shares. This role has no built-in equivalent on Windows file servers
- Storage File Data SMB Share Elevated Contributor - read, write, delete, and modify ACLs on files/directories in Azure file shares. This role is equivalent to a file share ACL of change on Windows file servers
- Storage File Data SMB Share Reader - read access on files/directories in Azure file shares. This role is equivalent to a file share ACL of read on Windows file servers.

Additionally, these roles are recommended for . . .

- Storage Queue Data Contributor - read, write, and delete Azure Storage queues and queue messages.
- Storage Queue Data Message Processor – peek, retrieve delete a message from Queue
- Storage Queue Data Message Sender – add messages to Queue
- Storage Queue Data Reader – read AND list Azure storage queues and queue messages
- Storage Table Data Contributor -read/write/delete to Azure tables and entities only
- Storage Table Data Read – read but not write to tables and entities

Next, use [best practices](/azure/storage/common/storage-sas-overview) when granting access to Azure Storage resources using shared access signatures (SAS):
- Always use HTTPS
- Have a revocation plan
- Configure SAS expiration policies
- Validate permissions


## Step 3. Logically separate or segregate critical data with network Controls

intro
illustration


|Task |Description  |
|---------|---------|
|Prevent public access, create network segmentation with [Private Endpoint](/azure/private-link/private-endpoint-overview) and Private Link.    |  Private endpoint allows you to connect to services with the use of a single private IP address on the Virtual Network leveraging Azure Private Link. <br> - Enabling private endpoints allows the Azure platform to validate network connections and allow only the connection with explicit access to the private-link resource to gain access to subsequent resource.<br> - You will need a separate private endpoint for each service on the Azure Storage Account.       |
|Use [Azure Private Link](/azure/private-link/private-link-overview)     | Use Azure Private Link to access Azure Storage over a private endpoint in your virtual network. Use the [approval workflow](/azure/private-link/private-endpoint-overview) to automatically approve or manually request, as appropriate.  |
|Prevent public access to your data sources using [Service Endpoints](/azure/virtual-network/virtual-network-service-endpoints-overview)     | Network segmentation can be achieved using Service Endpoints by enabling private IP addresses in a VNET to reach an endpoint without using Public IP addresses.     |


## Step 4. Use Defender for Storage for automated threat detection and protection  

[Microsoft Defender for Storage ](/azure/storage/common/azure-defender-storage-configure?tabs=azure-security-center)provides that additional level of intelligence that detects unusual and potentially harmful attempts to exploit your Storage services. Microsoft Defender for Storage is built into Microsoft Defender for Cloud.

Defender for Storage will detect anomalous access pattern alerts such as:

- Access from unusual location
- Application Anomaly
- Anonymous access
- Anomalous extract/upload alerts
- Data Exfiltration
- Unexpected delete
- Upload Azure Cloud Service package
- Suspicious storage activities alerts
- Access permission change
- Access Inspection
- Data Exploration 