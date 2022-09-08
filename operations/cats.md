---
title: Enable Azure Key Vault logging
description: How to enable logging for Azure Key Vault, which saves information in an Azure storage account that you provide.
services: key-vault
author: msmbaldwin
tags: azure-resource-manager

ms.service: key-vault
ms.subservice: general
ms.topic: how-to
ms.date: 10/01/2020
ms.author: mbaldwin 
ms.custom: devx-track-azurepowershell, devx-track-azurecli 
ms.devlang: azurecli
#Customer intent: As an Azure Key Vault administrator, I want to enable logging so I can monitor how my key vaults are accessed.
---
# Enable Key Vault logging

After you create one or more key vaults, you'll likely want to monitor how and when your key vaults are accessed, and by whom. For full details on the feature, see [Azure Key Vault logging](logging.md).

What is logged:

* All authenticated REST API requests, including failed requests as a result of access permissions, system errors, or bad requests.
* Operations on the key vault itself, including creation, deletion, setting key vault access policies, and updating key vault attributes such as tags.
* Operations on keys and secrets in the key vault, including:
  * Creating, modifying, or deleting these keys or secrets.
  * Signing, verifying, encrypting, decrypting, wrapping and unwrapping keys, getting secrets, and listing keys and secrets (and their versions).
* Unauthenticated requests that result in a 401 response. Examples are requests that don't have a bearer token, that are malformed or expired, or that have an invalid token.  
* Azure Event Grid notification events for the following conditions: expired, near expiration, and changed vault access policy (the new version event isn't logged). Events are logged even if there's an event subscription created on the key vault. For more information, see [Azure Key Vault as Event Grid source](../../event-grid/event-schema-key-vault.md).
