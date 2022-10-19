---
title: Secure Azure storage with Zero Trust
description: Learn how to secure Azure storage with Zero Trust.  
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
# Secure Azure storage with Zero Trust

In this article, we apply the principles of Zero Trust to Azure Storage:

- Verify explicitly
- Use least privileged access
- Assume breach

This article is part of a series of articles that demonstrate how to apply the principles of Zero Trust across an environment in Azure that includes Azure Storage services to support an IaaS workload. For more information, see Overview--Secure Azure infrastructure with Zero Trust.

## Storage architecture in Azure

Zero trust principles for Azure Storage are applied across the architecture, from the tenant and directory level down to the storage container at the data layer.

The following illustration provides a reference of logical architecture components.

Illustration

In the illustration:

- The storage account for the reference architecture is contained in a dedicated resource group. You can isolate each storage account in a different resource group for more granular permission control.
- Azure storage services for the reference architecture are contained within a dedicated storage account. You can have one storage account for each type of storage workload.
- For a broader look at the reference architecture, see [Overview-Secure Azure infrastructure with Zero Trust](azure-infrastructure-overview.md).

The illustration doesn't show Azure Queues and Azure Tables. Use the guidance in this article to secure these resources.

## What's in this article?

This article walks through the steps to apply the principles of Zero Trust across the reference architecture.

|Step| Task |
| --- | --- |
| 1 | Protect Data in all three modes: data at rest, data in transit, data in use |
| 2 | Verify users and control access to storage data with least Privilege |
| 3 | Logically separate or segregate critical data with network Controls |
| 4 | Use Defender for Storage for automated threat detection and protection |

## Step 1. Protect data in all three modes: data at rest, data in transit, data in use

Most of the settings for protecting data at rest, in transit, and in use are configured when you create the storage account. Use the following recommendations to be sure these protections are configured.

### Use encryption in transit

Keep your data secure by enabling transport-level security between Azure and the client. Always use HTTPS to secure communication over the public internet. When you call the REST APIs to access objects in storage accounts, you can enforce the use of HTTPS by setting [Secure Transfer Required](/azure/storage/common/storage-require-secure-transfer) for the Storage Account. Any request originating from an insecure connection is rejected.

- This configuration is enabled by default when you deploy a new Azure Storage Account (Secure by Default).
- Consider applying a policy to deny the deployment of insecure connections for Azure Storage (Secure by Design).
- This configuration also requires SMB 3.0 with Encryption.

### Prevent anonymous public read access

By default, public blob access is prohibited, but a user with proper permissions can configure an accessible resource. To prevent data breaches from anonymous access, you should verify explicitly who has access to your data. Preventing this at the Storage account level prevents a user from enabling this access at the container or blob level. See [Prevent anonymous public read access to containers and blobs](/azure/storage/blobs/anonymous-read-access-prevent).

### Prevent shared key authorization

This configuration will force the storage account to drop all requests made with a shared key and require Azure AD authorization instead. Azure AD is a more secure choice as you can leverage risk-based access mechanisms to harden access to data tiers. See [Prevent Shared Key authorization for an Azure Storage account](/azure/storage/common/shared-key-authorization-prevent?tabs=portal)

Illustration

### Enforce a minimum required version of transport layer security (TLS)

The highest version Azure Storage currently supports is TLS 1.2. Enforcing a minimum TLS version will reject requests from clients using older versions. See [Prevent Shared Key authorization for an Azure Storage account](/azure/storage/common/shared-key-authorization-prevent).

### Define the scope for copy operations

Define the scope for copy operations: Restrict copy operations to only those from source storage accounts that are within the same Azure AD tenant or that have a [Private Link](/azure/storage/common/storage-network-security?tabs=azure-portal) to the same virtual network as the destination storage account.

Limiting copy operations to source storage accounts with private endpoints is the most restrictive option. Source storage account must have private endpoints enabled.

Illustration

### Understand how encryption at rest works

All data written to Azure Storage is automatically encrypted by [Storage Service Encryption (SSE)](/azure/security/fundamentals/encryption-atrest) with a 256-bit Advanced Encryption Standard (AES) cipher. SSE automatically encrypts data when writing it to Azure Storage. When you read data from Azure Storage, Azure Storage decrypts the data before returning it. This process incurs no additional charges and doesn't degrade performance. Using customer-managed keys (CMKs) provides additional capabilities to control rotation of the encryption key or cryptographically erase data.

Illustration

> [!NOTE]
> In order to utilize a Customer Managed Key for Storage Account Encryption, you must enable it during account creation. You should also have a Key Vault with Key and Managed Identity with appropriate permissions already provisioned. Optionally, 256-bit AES encryption at the Azure Storage infrastructure level can also be enabled.

## Step 2. Verify users and control access to storage data with least Privilege

First, uUse Azure Active Directory to govern access to storage accounts. Using [Role-based Access Control with Storage Accounts](/azure/storage/blobs/authorize-access-azure-active-directory) allows you to granularly allow access based job function leveraging OAuth 2.0. You can align your granular access to your Conditional Access Policy.

It is important to note that roles for Storage Accounts must be assigned at either the management or data level. Thus, if you are using Azure Active Directory as the authentication and authorization method, a user should be assigned the appropriate combination of roles to give them the least amount of privilege necessary to complete their job function.

List of Storage Account Roles for granular access:

- **Storage Account Backup Operator**  - backup and restore operations using [Azure Backup](/azure/backup/blob-backup-configure-manage) on the Storage Account.
- **Storage Account Contributor**  - read, write, delete Azure Storage Accounts. Provision SAS to Azure Storage.
- **Storage Blob Data Contributor**  - read, write, and delete Azure Storage containers and blobs.
- **Storage Blob Data Owner**  - full access to Azure Storage blob containers and data.
- **Storage Blob Data Reader**  - read and list Azure Storage containers and blobs.
- **Storage Blog Delegator**  – get a user delegation key, which can then be used to create a Shared Access Signature for a container or blob that is signed with Azure AD credentials.
- **Storage File Data SMB Share Contributor**  - read, write, and delete permissions on files/directories in Azure file shares. This role has no built-in equivalent for Windows file servers.
- **Storage File Data SMB Share Elevated Contributor**  - read, write, delete, and modify ACLs on files/directories in Azure file shares. This role is equivalent to a file share ACL of change on Windows file servers.
- **Storage File Data SMB Share Reader**  - read access on files/directories in Azure file shares. This role is equivalent to a file share ACL of read on Windows file servers.
- **Storage Queue Data Contributor**  - read, write, and delete Azure Storage queues and queue messages.
- **Storage Queue Data Message Processor**  – peek, retrieve delete a message from queue.
- **Storage Queue Data Message Sender**  – add messages to queue.
- **Storage Queue Data Reader**  – read AND list Azure Storage queues and queue messages.
- **Storage Table Data Contributor**  -read/write/delete to Azure tables and entities only.
- **Storage Table Data Reader**  – read, but not write to tables and entities.

RBAC assignments can be done through the Access Control option on the Storage Account and can be assigned at various scopes.

Illustration

Another way to provide permissions that can be time-bound is through Shared Access Signatures. [Best Practices when using SAS](/azure/storage/common/storage-sas-overview#best-practices-when-using-sas) at a high level are:

- Always use HTTPS
- Have a revocation plan
- Configure SAS expiration policies
- Validate permissions
- Use a user delegation SAS where possible. This SAS is signed with Azure AD credentials.

## Step 3. Logically separate or segregate critical data with network Controls

In this step, use the recommended controls to protect the network connections to and from Azure Storage services.

The following illustration highlights the network connections to the Azure Storage services in the reference architecture.

Illustration

| Task | Description |
| --- | --- |
| Prevent public access, create network segmentation with [Private Endpoint](/azure/private-link/private-endpoint-overview) and Private Link. | Private endpoint allows you to connect to services with the use of a single private IP address on the Virtual Network leveraging Azure Private Link. <li>Enabling private endpoints allows the Azure platform to validate network connections and allow only the connection with explicit access to the private-link resource to gain access to subsequent resource. <li>You will need a separate private endpoint for each service on the Azure Storage Account. |
|Use [Azure Private Link](/azure/private-link/private-link-overview) | Use Azure Private Link to access Azure Storage over a private endpoint in your virtual network. Use the [approval workflow](/azure/private-link/private-endpoint-overview) to automatically approve or manually request, as appropriate. |
| Prevent public access to your data sources using [Service Endpoints](/azure/virtual-network/virtual-network-service-endpoints-overview) | Network segmentation can be achieved using Service Endpoints by enabling private IP addresses in a VNET to reach an endpoint without using Public IP addresses. |

Illustration

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

For more information on the architecture for threat protection across the reference architecture, see Overview--Secure Azure infrastructure with Zero Trust.

Once enabled, Storage Advanced Threat Protection will notify you of security alerts and recommendations for improving the security posture of your Azure Storage Accounts.

Illustration