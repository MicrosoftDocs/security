---
title: Ingest data sources and configure incident detection in Microsoft Sentinel
description: Learn how to configure Sentinel to ingest data sources and incident detection
author: mjcaparas
ms.author: macapara
manager: dansimp
ms.date: 3/16/2023
ms.topic: article
ms.service: microsoft-365-security
ms.localization_priority: Normal
ms.collection: 
  - msftsolution-sentinel-xdr
  - msftsolution-scenario
  - zerotrust-solution
---


# Step 3. Ingest data sources and configure incident detection in Sentinel

After you've completed designing and implementing your Microsoft Sentinel workspaces, you can proceed to ingest data sources and configure incident detection.


Data connectors are configured to enable data ingestion into the workspace. After enabling key data points to be ingested into Sentinel, User and Entity Behavior Analytics (UEBA) and Analytic Rules must also be enabled to capture anomalous and malicious activities. Analytic Rules dictate how Alerts and Incidents are generated in your Sentinel instance. Tailoring Analytic Rules to your environment and organizational needs through entity mapping allows you to produce high-fidelity incidents and reduce alert fatigue.

## Before you begin

Confirm the installation method, roles required, and licenses needed to turn on data connectors. For more information, see [Find your Microsoft Sentinel data connector \| Microsoft Learn](/azure/sentinel/data-connectors-reference).

The following table is a summary of the prerequisites required for key Azure and data connectors:

| Resource Type                              | Installation Method              | Role/Permissions/License Needed                                                                                    |
|--------------------------------------------|----------------------------------|--------------------------------------------------------------------------------------------------------------------|
| Azure Active Directory                     | Native Data connector            | Security Admin/Global Admin<br>Sign-in Logs require Azure AD P1 or P2 license<br>Other logs don't require P1/P2        |
| Azure Active Directory Identity Protection | Native Data Connector            | Security Admin/Global Admin<br>License: Azure AD Premium P2                                                        |
| Azure Activity                             | Azure Policy                     | Owner role required on subscriptions                                                                               |
| Microsoft Defender for Cloud               | Native Data Connector            | Security Reader<br><br>To enable bi-directional sync, Contributor/Security Admin role is required on the subscription. |
| Microsoft Defender for Identity            | Native Data Connector            | Security Admin/Global admin<br><br>License: Microsoft Defender for Identity                                            |
| Microsoft Defender for Office 365          | Native Data Connector            | Security Admin/Global admin<br><br>License: Microsoft Defender for Office 365 Plan 2                                   |
| Office 365                                 | Native Data Connector            | Security Admin/Global admin                                                                                        |
| Microsoft Defender for IoT                 |                                  | Contributor to subscription with IoT hubs                                                                          |
| Microsoft Defender for Cloud Apps          | Native Data Connector            | Security Admin/Global admin<br><br>License: Microsoft Defender for Cloud Apps                                          |
| Microsoft Defender for Endpoint            | Native Data Connector            | Security Admin/Global admin<br><br>License: Microsoft Defender for Endpoint                                            |
| Windows Security Events through Azure Monitor Agent (AMA)            | Native Data Connector with Agent | Read/Write Workspace                                                                                               |
| Syslog                                     | Native Data Connector with Agent | Read/Write Workspace                                                                                               |

## Step 1. Turn on data connectors

Use the following recommendations to get started with configuring data connectors:

1.  Focus on setting up with free data sources to ingest:

    1.  Azure Activity Logs:
        a.  Ingesting Azure Activity Logs is **critical** in enabling Sentinel to provide a single-pane of glass view across the environment.
    2.  Office 365 Audit Logs, including all SharePoint activity, Exchange admin activity, and Teams.
    3.  Security alerts, including alerts from Microsoft Defender for Cloud, Microsoft 365 Defender, Microsoft Defender for Office 365, Microsoft Defender for Identity, and Microsoft Defender for Endpoint:

        1.  Ingesting security alerts into Sentinel enables it to be the "central pane of incident management" across the environment.

        2.  Incident investigation starts in Sentinel and should continue in the Microsoft 365 Defender or Defender for Cloud, if deeper analysis is required.

    4.  Microsoft Defender for Cloud Apps Alerts.

    For more information, see [Free data sources](/azure/sentinel/billing?tabs=commitment-tier#free-data-sources).

    The following table lists the free data sources you can enable in Microsoft Sentinel:
    
    | **Microsoft Sentinel data connector** | **Free data type**                      |
    |---------------------------------------|-----------------------------------------|
    | Azure Activity Logs                   | AzureActivity                           |
    | Azure AD Identity Protection          | SecurityAlert (IPC)                     |
    | Office 365                            | OfficeActivity (SharePoint)  <br> OfficeActivity (Exchange) <br>  OfficeActivity (Teams)           |
    | Microsoft Defender for Cloud          | SecurityAlert (Defender for Cloud)      |
    | Microsoft Defender for IoT            | SecurityAlert (Defender for IoT)        |
    | Microsoft 365 Defender                | SecurityIncident       <br>       SecurityAlert              |
    | Microsoft Defender for Endpoint       | SecurityAlert (Microsoft Defender Advanced Threat Protection (MDATP))                   |
    | Microsoft Defender for Identity       | SecurityAlert (Azure Advanced Threat Protection (AATP))                    |
    | Microsoft Defender for Cloud Apps     | SecurityAlert (Defender for Cloud Apps) |

2.  To provide broader monitoring and alerting coverage, focus on the following data connectors:

    >[!NOTE]
    >There is a charge for ingesting data from the sources listed in the section

    - Azure Active Directory
    - Microsoft 365 Defender connector
           
        -  Send Microsoft 365 Defender logs to Sentinel, if any of the following are required:
        
            1.  Leverage Fusion Alerts with Sentinel.                 
                - Fusion correlates data sources from multiple products to detect multi-stage attacks across the environment.
            2. Longer retention than what is offered in Microsoft 365 Defender.

            3.  Automation not covered by the built-in remediations offered by Microsoft Defender for Endpoint.  For more information, see [Remediation actions in Microsoft 365 Defender](/microsoft-365/security/defender/m365d-remediation-actions).

3.  If deployed in Azure, use the following connectors to send these resources' Diagnostic Logs to Sentinel: 

    - Azure Firewall
    - Azure Application Gateway
    - Keyvault
    - Azure Kubernetes Service
    - Azure SQL
    - Network Security Groups
    - Azure-Arc Servers


    The recommended method is setting up Azure Policy to require that their logs be forwarded to the underlying Log Analytics workspace. For more on information, see [Create diagnostic settings at scale using Azure Policy](/azure/azure-monitor/essentials/diagnostic-settings-policy).

4.  For virtual machines hosted on-premises or in other clouds that require their logs collected, use:

    - Windows Security Events using AMA
    - Security Events using Legacy Agent
    - Events via Defender for Endpoint (for server)
    - [Syslog connector](/azure/sentinel/connect-log-forwarder)

5.  For Network Virtual Appliances or other on-premises sources that generate Common Event Format (CEF) or SYSLOG logs, use the following connector:

    - Common Event Format (CEF) via AMA
    - Common Event Format (CEF) via Legacy Agent

    For more information, see, [Deploy a log forwarder to ingest Syslog and CEF logs to Microsoft Sentinel](/azure/sentinel/connect-log-forwarder).

6.  Search in content hub for other devices, Software as a service (SaaS) apps that require logs to be sent to Sentinel. For more information, see [Discover and manage Microsoft Sentinel out-of-the-box content ](/azure/sentinel/sentinel-solutions-deploy).

## Step 2. Enable User Entity Behavior Analytics 

After setting up data connectors in Sentinel, make sure to enable [User Entity Behavior Analysis](/azure/sentinel/identify-threats-with-entity-behavior-analytics) to identify suspicious behavior  that could lead to phishing exploits and eventually attacks such as ransomware.

Data Sources required:

-   Active Directory logs (Microsoft Defender for Identity)
-   Azure Active Directory
    -   Audit Logs
    -   Azure Activity
-   Security Events
-   Sign in Logs

Using UEBA allows Microsoft Sentinel to build behavioral profiles of your organization's entities across time and peer group to identify anomalous activity. This added utility aids in an expedition of determining if an asset has been compromised. Since it identifies peer group association this can also aid in determining the blast radius of said compromise.

## Step 3. Enable Analytic Rules

The brains of Sentinel come from the Analytic Rules. These are rules you set to tell Sentinel to alert you to events with a set of conditions that you consider to be important. The out-of-the-box decisions Sentinel makes are based on User Entity Behavioral Analytics (UEBA) and on correlations of data across multiple data sources. 


Microsoft Sentinel enables the Fusion Advanced multistage attack detection analytic rule by default to automatically identify multistage attacks. Leveraging anomalous behavior and suspicious activity events observed across the cyber kill chain, Microsoft Sentinel generates incidents that allow you to see the compromise incidents with two or more alert activities in it with a high degree of confidence.

Fusion alert technology correlates broad points of data signals with extended machine learning (ML) analysis to help determine known, unknown and emerging threats. For example, Fusion detection can take the Anomaly Rule templates and the scheduled queries created for the [Ransomware scenario](/azure/sentinel/fusion#fusion-for-ransomware) and pair them with alerts from Microsoft Security Suite products: 

-   Azure Active Directory Identity Protection
-   Microsoft Defender for Cloud
-   Microsoft Defender for IoT
-   Microsoft 365 Defender
-   Microsoft Defender for Cloud Apps
-   Microsoft Defender for Endpoint
-   Microsoft Defender for Identity
-   Microsoft Defender for Office 365

Another set of out-of-the-box rules enabled by default are Anomaly Rules in Sentinel. These are based on Machine Learning models and  UEBA that train on the data in your workspace to flag anomalous behavior across users, hosts, and others. Often a phishing attack leads to an execution step such as local or cloud account manipulation/control or malicious script execution. Anomaly Rules look exactly for those types of activities: 

-   [Anomalous Account Access Removal](/azure/sentinel/anomalies-reference#anomalous-account-access-removal)
-   [Anomalous Account Creation](/azure/sentinel/anomalies-reference#anomalous-account-creation)
-   [Anomalous Account Deletion](/azure/sentinel/anomalies-reference#anomalous-account-deletion)
-   [Anomalous Account Manipulation](/azure/sentinel/anomalies-reference#anomalous-account-manipulation)
-   [Anomalous Code Execution (UEBA)](/azure/sentinel/anomalies-reference#anomalous-code-execution-ueba)
-   [Anomalous Data Destruction](/azure/sentinel/anomalies-reference#anomalous-data-destruction)
-   [Anomalous Defensive Mechanism Modification](/azure/sentinel/anomalies-reference#anomalous-defensive-mechanism-modification)
-   [Anomalous Failed Sign-in](/azure/sentinel/anomalies-reference#anomalous-failed-sign-in)
-   [Anomalous Password Reset](/azure/sentinel/anomalies-reference#anomalous-password-reset)
-   [Anomalous Privilege Granted](/azure/sentinel/anomalies-reference#anomalous-privilege-granted)
-   [Anomalous Sign-in](/azure/sentinel/anomalies-reference#anomalous-sign-in)

Review the Anomaly Rules and Anomaly Score Threshold for each one. If you're observing false positives for example, consider duplicating the rule and modifying the threshold by following the steps outlined in [Tune anomaly rules](/Azure/sentinel/work-with-anomaly-rules#tune-anomaly-rules).

After reviewing and modifying Fusion and Anomaly rules, enable the out-of-the-box Microsoft Threat Intelligence Analytics Rule. Verify that [this rule matches your log data with Microsoft-generated threat intelligence](/azure/sentinel/understand-threat-intelligence#detect-threats-with-threat-indicator-analytics). Microsoft has a vast repository of threat intelligence data, and this Analytic Rule uses a subset of it to generate high fidelity alerts and incidents for SOC (security operations centers) teams to triage.

With Fusion, Anomaly, and Threat Intelligence Analytic Rules enabled, you should conduct a [MITRE Att&ck crosswalk](/azure/sentinel/mitre-coverage) to help you decide which remaining Analytic Rules to enable and to finish implementing a mature XDR (extended detection and response) process. This will empower you to detect and respond throughout the lifecycle of an attack.

The [MITRE Att&ck research department](https://attack.mitre.org/matrices/enterprise/) created the MITRE method, and it is provided as part of Microsoft Sentinel to ease your implementation. You should ensure you have Analytic rules that stretch the length and breadth of the attack vectors approach. Start by reviewing the MITRE techniques that are covered by your existing 'Active' Analytic Rules, and then select '**Analytic rule templates**' and '**Anomaly Rules**' in the **Simulated** dropdown. Now, it will show you where you have the adversary tactic and/or technique covered and where there are available Analytic Rules you should consider enabling to improve your coverage. For example, to detect potential phishing attacks, review the **Analytic rule templates** for the Phishing technique, and prioritize enabling the rules that specifically query the data sources you have onboarded to Sentinel.

:::image type="content" source="./media/sentinel-dashboard.svg" alt-text="Image of the Sentinel dashboard" lightbox="./media/sentinel-dashboard.svg":::


In summary, when turning on Analytic rules for Sentinel, prioritize enabling by connected data sources, organizational risk, and MITRE tactic.

## Recommended training


### Connect data to Microsoft Sentinel using data connectors

|Training  |[Connect data to Microsoft Sentinel using data connectors](/training/modules/connect-data-to-azure-sentinel-with-data-connectors/)|
|---------|---------|
|:::image type="icon" source="media/connect-data-to-azure-sentinel-with-data-connectors.svg" border="false"::: |The primary approach to connect log data is using the Microsoft Sentinel provided data connectors. This module provides an overview of the available data connectors. |
> [!div class="nextstepaction"]
> [Start >](/training/modules/connect-data-to-azure-sentinel-with-data-connectors/)

### Connect logs to Microsoft Sentinel


|Training  |[Connect logs to Microsoft Sentinel](/training/paths/sc-200-connect-logs-to-azure-sentinel/)|
|---------|---------|
|:::image type="icon" source="media/connect-windows-hosts-to-azure-sentinel.svg" border="false"::: |Connect data at cloud scale across all users, devices, applications, and infrastructure, both on-premises and in multiple clouds to Microsoft Sentinel. |
> [!div class="nextstepaction"]
> [Start >](/training/paths/sc-200-connect-logs-to-azure-sentinel/)



### Identify threats with Behavioral Analytics

|Training  |[Identify threats with Behavioral Analytics| Microsoft Learn](/training/modules/use-entity-behavior-analytics-azure-sentinel/)|
|---------|---------|
|:::image type="icon" source="media/azure-sentinel-behavior-analytics.svg" border="false"::: |The primary approach to connect log data is using the Microsoft Sentinel provided data connectors. This module provides an overview of the available data connectors. |
> [!div class="nextstepaction"]
> [Start >](/training/modules/use-entity-behavior-analytics-azure-sentinel/)



## Next steps

Continue to [Step 4](respond-incident.md) to respond to an incident.


[![Image of Microsoft Sentinel and XDR solution steps with step 4 highlighted](./media/siem-xdr-solution-4.png)](respond-incident.md)
 
