---
title: Applications Zero Trust integration overview
description: Independent software vendors (ISVs) can integrate their solutions with Microsoft Cloud App Security to help customers adopt a Zero Trust model and keep their organizations secure.
ms.date: 09/17/2021
ms.service: security
author: knicholasa
ms.author: nichola
ms.topic: conceptual
---

# Application integrations

:::image type="icon" source="../media/icon-applications-medium.png":::

Applications are core productivity tools for employees. In a modern workplace, adoption of cloud based Software as a Service (SaaS) applications has created new challenges for IT. Lack of visibility and control over applications, the way users interact with them, and the data that is exposed through them creates security and compliance risks.

Applications Zero Trust solutions are about providing visibility and control over data, and analytics that identify and combat cyber threats across cloud apps and services.

This guidance is for software providers and technology partners who want to enhance their applications security solutions by integrating with Microsoft products.

## Applications Zero Trust integration guide

This integration guide includes instructions for integrating with [Microsoft Cloud App Security (MCAS)](/cloud-app-security/). Microsoft Cloud App Security is a Cloud Access Security Broker (CASB) that operates on multiple clouds. It provides rich visibility, control over data travel, and sophisticated analytics to identify and combat cyberthreats across all your cloud services.

:::image type="content" source="../media/integrate/applications/microsoft-cloud-app-security-architecture.png" alt-text="Architectural diagram showing both protected and unprotected apps in a cloud. The cloud has a bi-directional connection to an organization. The protected apps are connected via an API to Cloud App Security App connectors. The organization sends cloud traffic logs to the Cloud App Security's Cloud Discovery tool, and receives configuration scripts. Both the organization and the app cloud are connected to the Proxy Access and Sessions part of Cloud App Security.":::

### Microsoft Cloud App Security

Independent software vendors (ISVs) can integrate with Microsoft Cloud App Security to help organizations discover risky usage or potential exfiltration and protect them from risks surfaced by the use of shadow applications.

The Microsoft Cloud App Security API provides programmatic access to Cloud App Security through [REST API endpoints](/cloud-app-security/api-introduction).  ISVs can use the API to perform read and update operations on Cloud App Security data and objects at scale. For example:
- Uploading log files for Cloud Discovery
- Generating block scripts
- List activities and alerts
- Dismiss or resolve alerts

This allows ISVs to:
- Use Cloud Discovery to map and identify your cloud environment and the cloud apps your organization is using.
- Sanction and unsanction apps in your cloud.
- Easily deploy app connectors that take advantage of provider APIs, for deeper visibility and granular governance of apps that you connect to.
- Use Conditional Access App Control protection to get real-time visibility and control over access and activities within your cloud apps.

To get started, check out the inctroduction to the [Cloud App Security REST API](/cloud-app-security/api-introduction).

### Shadow IT partner integration

Secure Web Gateways (SWG) and Endian Firewall (EFW) solutions can integrate with MCAS to provide customers with a comprehensive Shadow IT discovery, compliance and security risk assessment of the discovered apps, and integrated Access Control to unsanctioned apps.

The principles of the integration are:

1. Deployment-less: The vendor will stream traffic logs directly to MCAS to avoid any agent deployment and maintenance.
1. Log enrichment and App correlation: traffic logs will be enriched against MCAS catalog to map each log record to a known app (associated with a risk profile)
1. MCAS analytics and reporting: MCAS will analyze and process the data to provide an overview Shadow IT report
1. Risk-based access control: MCAS will sync back to the vendor the signatures of the app to be blocked in to allow the customer with risk-based app management in MCAS that is enforced by consistent access control mechanism of the vendor

We recommend performing the following steps before starting to develop the integration:

1. Create a trial MCAS tenant using [this link](https://www.microsoft.com/cloud-platform/cloud-app-security-trial).
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

## Next Steps
- [Microsoft Cloud App Security overview](/cloud-app-security/what-is-cloud-app-security)
- [Cloud App Security REST API](/cloud-app-security/api-introduction)