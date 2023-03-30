---
title: Zero Trust integration for Applications overview
description: Independent software vendors (ISVs) can integrate their solutions with Microsoft Defender for Cloud Apps to help customers adopt a Zero Trust model and keep their organizations secure.
ms.date: 02/22/2023
ms.service: security
author: janicericketts
ms.author: jricketts
ms.topic: conceptual
ms.collection:
  - zerotrust-partner
---

# Application integrations

:::image type="icon" source="../media/icon-applications-medium.png":::

Applications are core productivity tools for employees. In a modern workplace, adoption of cloud based Software as a Service (SaaS) applications has created new challenges for IT. Lack of visibility and control over applications, the way users interact with them, and the data that is exposed through them creates security and compliance risks.

Zero Trust solutions for the applications pillar are about providing visibility and control over app usage data and analytics that identify and combat cyber threats across cloud apps and services.

This guidance is for software providers and technology partners who want to enhance their applications security solutions by integrating with Microsoft products.

## Zero Trust integration with Applications guide

This integration guide includes instructions for integrating with [Microsoft Defender for Cloud Apps)](/cloud-app-security/). Defender for Cloud Apps is a cloud access security broker (CASB) that operates on multiple clouds. It provides rich visibility, control over data travel, and sophisticated analytics to identify and combat cyberthreats across all your cloud services.

:::image type="content" source="../media/integrate/applications/microsoft-cloud-app-security-architecture.png" alt-text="Architectural diagram showing how an organization uses Defender for Cloud Apps features including app connectors, cloud discovery, and proxy access. App connectors connect to protected cloud apps via APIs. Cloud discovery consumes traffic logs and provides configuration scripts. Proxy access sits in between the organization and its protected apps in the cloud.":::

### Microsoft Defender for Cloud Apps

Independent software vendors (ISVs) can integrate with Defender for Cloud Apps to help organizations discover risky usage or potential exfiltration and protect them from risks surfaced by the use of shadow applications.

The Defender for Cloud Apps API provides programmatic access to Defender for Cloud Apps through [REST API endpoints](/cloud-app-security/api-introduction).  ISVs can use the API to perform read and update operations on Defender for Cloud Apps data and objects at scale. For example:
- Uploading log files for Cloud Discovery
- Generating block scripts
- List activities and alerts
- Dismiss or resolve alerts

This allows ISVs to:
- Use Cloud Discovery to map and identify your cloud environment and the cloud apps your organization is using.
- Sanction and unsanction apps in your cloud.
- Easily deploy app connectors that take advantage of provider APIs, for deeper visibility and granular governance of apps that you connect to.
- Use Conditional Access App Control protection to get real-time visibility and control over access and activities within your cloud apps.

To get started, check out the introduction to the [Defender for Cloud Apps REST API](/cloud-app-security/api-introduction).

### Shadow IT partner integration

Secure Web Gateways (SWG) and Endian Firewall (EFW) solutions can integrate with Defender for Cloud Apps to provide customers with a comprehensive Shadow IT discovery, compliance and security risk assessment of the discovered apps, and integrated Access Control to unsanctioned apps.

The principles of the integration are:

1. Deployment-less: The vendor will stream traffic logs directly to Defender for Cloud Apps to avoid any agent deployment and maintenance.
1. Log enrichment and App correlation: traffic logs will be enriched against the Defender for Cloud Apps catalog to map each log record to a known app (associated with a risk profile)
1. Defender for Cloud Apps analytics and reporting: Defender for Cloud Apps will analyze and process the data to provide an overview Shadow IT report
1. Risk-based access control: Defender for Cloud Apps will sync back to the vendor the signatures of the app to be blocked in to allow the customer with risk-based app management in Defender for Cloud Apps that is enforced by consistent access control mechanism of the vendor

We recommend performing the following steps before starting to develop the integration:

1. Create a trial Defender for Cloud Apps tenant using [this link](https://www.microsoft.com/en-us/security/business/cloud-apps-defender).
1. Upload a sample traffic log using the manual upload feature.
1. Alternatively, you can use the API-based upload. For detailed instructions, use your trial credentials and [Cloud Discovery API documentation](/cloud-app-security/api-discovery)
    1. [Generate API token](/cloud-app-security/api-authentication#generate-a-token)
    1. Log upload –consists of three stages:
        1. [Initiate file upload](/cloud-app-security/api-discovery-initiate)
        1. [Perform file upload](/cloud-app-security/api-discovery-perform)
        1. [Finalize file upload](/cloud-app-security/api-discovery-finalize)
    1. [Generate block script](/cloud-app-security/api-discovery-script) (that is, extract unsanctioned apps info)

When uploading the log, choose one of the following parser options:

1. If your log format is a standard CEF, W3C, LEEF, select it in the dropdown of existing log formats
1. If not, [configure a custom log parser](/cloud-app-security/custom-log-parser)

## Next steps

- [Microsoft Defender for Cloud Apps overview](/cloud-app-security/what-is-cloud-app-security)
- [Defender for Cloud Apps REST API](/cloud-app-security/api-introduction)
