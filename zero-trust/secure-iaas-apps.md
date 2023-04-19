---
title: Overview - Apply Zero Trust principles to IaaS applications in Amazon Web Services (AWS)
description: This article gives an overview of how to apply Zero Trust principles to IaaS applications in AWS.
ms.date: 04/17/2023
ms.service: security
author: simona
ms.author: terrylan
ms.topic: conceptual
ms.collection: 
  - zerotrust-solution
---

# Apply Zero Trust principles to IaaS applications in Amazon Web Services

This article provides steps to apply the principles of Zero Trust to IaaS applications in Amazon Web Services (AWS):

| Zero Trust Principle | Definition | Met by |
| --- | --- | --- |
| Verify explicitly | Always authenticate and authorize based on all available data points. | Security in DevOps (DevSecOps), using GitHub advanced security and DevOps, scans and secures your infrastructure as code. |
| Use least privileged access | Limit user access with Just-In-Time and Just-Enough-Access (JIT/JEA), risk-based adaptive policies, and data protection. | <ul><li> Microsoft Entra Permissions Management detects, right-sizes, and monitors unused and excessive permissions. </li><li> Privileged Identity Management (PIM), a service in Azure Active Directory (Azure AD) Premium P2, allows you to manage, control, and monitor access to important resources in your organization. </li><li> Assign users role-based access control (RBAC) to resources at the repository level, team level, or organization level. </li></ul> |
| Assume breach | Minimize blast radius and segment access. Verify end-to-end encryption and use analytics to get visibility, drive threat detection, and improve defenses. | <ul><li> Microsoft Defender for Cloud and Microsoft Defender for Endpoint (Microsoft 365) continuously scan the environment for threats and vulnerabilities. </li><li> Microsoft Sentinel analyzes collected data, behavioral trend of entities, anomalies, and multi-stage threats across enterprises to detect suspicious activity, and can respond with automation. </li></ul> |

For more information about how to apply the principles of Zero Trust across an Azure IaaS environment, see the [Apply Zero Trust principles to Azure IaaS overview](azure-infrastructure-overview.md).

## AWS
AWS is one of the public cloud providers available in the market, along with Microsoft Azure, Google Cloud Platform, and others. It's common for companies to have a multi-cloud architecture that consists of more than one cloud provider. In this article, we'll focus on multi-cloud architecture where Azure and AWS are integrated to run workloads and IT business solutions.

This article shows you how to secure an AWS IaaS workload using Microsoft products, including Microsoft Defender for Cloud, Microsoft Sentinel, Microsoft 365 Defender, GitHub Advanced Security, Azure Arc, Microsoft Entra, and others.

### AWS components
AWS virtual machines, called Amazon Elastic Compute Cloud (Amazon EC2), usually run on top of an AWS virtual network, called Amazon Virtual Private Cloud (Amazon VPC). Users and cloud administrators set up an Amazon VPC in their AWS environment and add Amazon EC2 virtual machines.

AWS CloudTrail logs AWS account activity in the AWS environment. Amazon EC2, Amazon VPC, and AWS CloudTrail are very common in AWS environments. Collecting logs from these services is essential to understanding what is going on in your AWS environment and the actions to take to avoid or mitigate attacks.

Amazon GuardDuty is a threat detection service that helps to protect AWS workloads by monitoring the AWS environment for malicious activities and unauthorized behavior.

In this article, you'll learn how to integrate monitoring and logging of these AWS resources and services with Azure's monitoring solutions and the Microsoft security stack.

## Reference Architecture
The following architecture diagram shows the common services and resources needed to run an IaaS workload in an AWS environment. The diagram also shows the Azure services needed to ingest logs and data from the AWS environment into Azure.

Need final diagram

The diagram demonstrates ingestion of logs into Azure for the following AWS and Amazon resources and services:

- Amazon Elastic Compute Cloud (Amazon EC2)
- Amazon Virtual Private Cloud (Amazon VPC)
- AWS CloudTrail
- Amazon GuardDuty

To ingest logs into Azure for the AWS and Amazon resources and services, you must have Amazon Simple Storage Service (Amazon S3) and Amazon Simple Queue Service (SQS) defined.

Logs and data are ingested into Log Analytics in Azure Monitor.

The following Microsoft products use the ingested data to monitor:

- Microsoft Defender for Cloud
- Microsoft Sentinel
- Microsoft Defender for Endpoint

>[!Note]
>You don't have to ingest logs into all of the Microsoft products listed above to monitor your AWS resources and services. Using all of the Microsoft products together, though, provides greater benefit from AWS log and data ingestion into Azure.
>

This article follows the architecture diagram and describes how to:

- Install and configure the Microsoft products to ingest logs from your AWS resources.
- Configure metrics for the security data that you want to monitor.
- Improve your overall security posture and secure the AWS workload.
- Secure Infrastructure as code.

## Step 1: Install and connect Microsoft products to ingest logs and data

This section walks you through how to install and connect the Microsoft products in the referenced architecture to ingest logs from your AWS and Amazon services and resources. To adhere to the Zero Trust **verify explicitly** principle, you need to install Microsoft products and connect to your AWS environment to take proactive actions before an attack.

| Steps | Task |
| --- | --- |
| A | Install Azure Connected Machine agent on to your Amazon Elastic Compute Cloud (Amazon EC2) virtual machines to ingest operating system data and logs into Azure. |
| B | Install Azure Monitor Agent on to Amazon EC2 virtual machines to send logs to your Log Analytics workspace. |
| C | Connect an AWS account to Microsoft Defender for Cloud. |
| D | Connect Microsoft Sentinel to AWS to ingest AWS log data. |
| E | Use the AWS connectors to pull AWS service logs into Microsoft Sentinel. |

### A. Install Azure Connected Machine agent on to your Amazon EC2 virtual machines to ingest operating system data and logs into Azure

[Azure Arc-enabled servers](/azure/azure-arc/servers/overview) let you manage Windows and Linux physical servers and virtual machines hosted outside of Azure, on your corporate network, or other cloud provider. For the purposes of Azure Arc, machines hosted outside of Azure are considered hybrid machines. To connect your Amazon EC2 virtual machines (also known as hybrid machines) to Azure, you install the [Azure Connected Machine agent](/azure/azure-arc/servers/agent-overview) on each machine.

For more information, see [Connect hybrid machines to Azure](/azure/azure-arc/servers/onboard-portal).

### B. Install Azure Monitor Agent on to Amazon EC2 virtual machines to send logs to your Log Analytics workspace

[Azure Monitor](/azure-monitor/best-practices-multicloud) provides complete monitoring for your resources and applications running in Azure and other clouds, including AWS. Azure Monitor collects, analyzes, and acts on telemetry from your cloud and on-premises environments. [VM insights](/azure/azure-monitor/vm/vminsights-overview) in Azure Monitor uses Azure Arc-enabled servers to provide a consistent experience between both Azure virtual machines and your Amazon EC2 virtual machines. You can view your Amazon EC2 virtual machines right alongside your Azure virtual machines. You can onboard your Amazon EC2 virtual machines using identical methods. This includes using standard Azure constructs such as Azure Policy and applying tags.

When you enable VM insights for a machine, the [Azure Monitor Agent](/azure/azure-monitor/agents/agents-overview) (AMA) is installed. AMA collects monitoring data from the Amazon EC2 virtual machines and delivers it to Azure Monitor for use by features, insights, and other services, such as Microsoft Sentinel and Microsoft Defender for Cloud.

>[!Important]
>Log Analytics is a tool in the Azure portal that you use to edit and run log queries against data in the Azure Monitor Logs store. Log Analytics is automatically installed.

Amazon EC2 virtual machines may have the legacy Log Analytics agent installed. This agent will be deprecated in September 2024. Microsoft recommends installing the new Azure Monitor Agent.

The Log Analytics agent or Azure Monitor Agent for Windows and Linux is required to:

- Proactively monitor the operating system and workloads running on the machine.
- Manage the machine using Automation runbooks or solutions like Update Management.
- Use other Azure services like Microsoft Defender for Cloud.
>

When you collect logs and data, the information is stored in a Log Analytics workspace. You need a Log Analytics workspace if you collect data from Azure resources in your subscription.

Azure Monitor workbooks are a visualization tool available in the Azure portal. Workbooks combine text, log queries, metrics, and parameters into rich interactive reports. Setting up workbooks helps you use analytics to adhere to the Zero Trust **assume breach** principle.

Workbooks are discussed in the next article under Monitor in Microsoft Sentinel logs from Amazon Virtual Private Cloud (Amazon VPC), AWS CloudTrail, and Amazon GuardDuty.

For more information, see:

- [Install AMA through data collection rules](/azure/azure-monitor/essentials/data-collection-rule-overview) in Azure Monitor
- [Create a Log Analytics workspace](/azure/azure-monitor/logs/quick-create-workspace)
- [Get started with Azure workbooks](/azure/azure-monitor/visualize/workbooks-getting-started)

### C. Connect an AWS account to Microsoft Defender for Cloud

Microsoft Defender for Cloud is a Cloud Security Posture Management (CSPM) and Cloud Workload Protection Platform (CWPP) for all your Azure, on-premises, and multi-cloud resources, including AWS. Defender for Cloud fills three vital needs as you manage the security of your resources and workloads in the cloud and on-premises:

- Continuously assess - Know your security posture. Identify and track vulnerabilities.
- Secure - Harden resources and services with the [Microsoft cloud security benchmark](/security/benchmark/azure/introduction) (MCSB) and [AWS Foundational Security Best Practices standard](https://aws.amazon.com/security-hub/getting-started/security-hub-fsbp/).
- Defend - Detect and resolve threats to resources and services.

Microsoft Defender for Servers is one of the paid plans provided by Microsoft Defender for Cloud. Defender for Servers extends protection to your Windows and Linux machines that run in Azure, AWS, Google Cloud Platform (GCP), and on-premises. Defender for Servers integrates with Microsoft Defender for Endpoint to provide endpoint detection and response (EDR) and other threat protection features.

For more information, see:

- [Connect an AWS account to Microsoft Defender for Cloud](/azure/defender-for-cloud/quickstart-onboard-aws) to protect your AWS-based resources.
- [Select a Defender for Servers plan in Microsoft Defender for Cloud](/azure/defender-for-cloud/plan-defender-for-servers-select-plan#review-plans) to compare different plans offered by Defender for Servers. Defender for Servers automatically provisions the Defender for Endpoint sensor on every supported machine that's connected to Defender for Cloud.

>[!Note]
>If you haven't deployed AMA on your servers yet, you can [deploy the Azure Monitor Agent](/azure/defender-for-cloud/auto-deploy-azure-monitoring-agent) on your servers when you enable Defender for Servers.
>

### D. Connect Microsoft Sentinel to AWS to ingest AWS log data

Microsoft Sentinel is a scalable, cloud-native solution that provides the following services:

- Security information and event management (SIEM)
- Security orchestration, automation, and response (SOAR)

Microsoft Sentinel delivers security analytics and threat intelligence across the enterprise. With Microsoft Sentinel, you get a single solution for attack detection, threat visibility, proactive hunting, and threat response.

For setup instructions, see [Onboard Microsoft Sentinel](/azure/sentinel/quickstart-onboard).

### E. Use the AWS connectors to pull AWS service logs into Microsoft Sentinel

To pull the AWS service logs into Microsoft Sentinel, you need to use a Microsoft Sentinel AWS connector. The connector works by granting Microsoft Sentinel access to your AWS resource logs. Setting up the connector establishes a trust relationship between AWS and Microsoft Sentinel. This is accomplished on AWS by creating a role that gives permission to Microsoft Sentinel to access your AWS logs.

The AWS connector is available in two versions: the new Amazon Simple Storage Service (Amazon S3) connector that ingests logs by pulling them from an Amazon S3 bucket and the legacy connector for CloudTrail management and data logs. The Amazon S3 connector can ingest logs from Amazon Virtual Private Cloud (Amazon VPC), AWS CloudTrail, and Amazon GuardDuty. The Amazon S3 connector is in preview. We recommend using the Amazon S3 connector.

To ingest logs from Amazon VPC, AWS CloudTrail, and Amazon GuardDuty using the Amazon S3 connector, see [Connect Microsoft Sentinel to AWS](/azure/sentinel/connect-aws).

>[!Note]
>Microsoft recommends using the automatic setup script to deploy the Amazon S3 connector. If you prefer to perform each step manually, then follow the [manual setup](/azure/sentinel/connect-aws.md#manual-setup) to connect Microsoft Sentinel to AWS.

## Step 2: Configure metrics for your security data

Now that Azure is ingesting logs from your Amazon Web Services (AWS) resources, you can create threat detection rules in your environment and monitor alerts. This article walks you through the steps to collect logs and data and monitor for suspicious activity. The Zero Trust **assume breach** principle is achieved by monitoring your environment for threats and vulnerabilities.

| Steps | Task |
| --- | --- |
| A | Collect Amazon Elastic Compute Cloud (Amazon EC2) logs in Azure Monitor. |
| B | View and manage Microsoft Defender for Cloud security alerts and recommendations for Amazon EC2. |
| C | Integrate Microsoft Defender for Endpoint with Defender for Cloud. |
| D | Monitor Amazon EC2 data in Microsoft Sentinel. |
| E | Monitor in Microsoft Sentinel logs from Amazon Virtual Private Cloud (Amazon VPC), AWS CloudTrail, and Amazon GuardDuty. |
| F | Use Microsoft Sentinel built in detection rules to create and investigate threat detection rules in your environment. |

### A. Collect Amazon Elastic Compute Cloud (Amazon EC2) logs in Azure Monitor

The Azure Connected Machine agent installed on your Amazon EC2 VMs enables you to monitor your AWS resources as if they are Azure resources. For example, you can use Azure policies to govern and manage updates to your Amazon EC2 VMs.

The [Azure Monitor Agent](/azure/azure-monitor/agents/agents-overview) (AMA) installed on your Amazon EC2 VMs collects monitoring data and delivers it to Azure Monitor. These logs become input for Microsoft Sentinel and Defender for Cloud.

To collect logs from your Amazon EC2 VMs, see [create data collection rules](/azure/azure-monitor/essentials/data-collection-rule-overview.md#create-a-data-collection-rule).

### B. View and manage Microsoft Defender for Cloud security alerts and recommendations for Amazon EC2

Microsoft Defender for Cloud uses resource logs to generate security alerts and recommendations. Defender for Cloud can provide alerts to warn you about possible threats on your Amazon EC2 VMs. Alerts are prioritized by severity. Each alert provides details of affected resources, issues, and remediation recommendations.

There are two ways to view recommendations in the Azure portal. In the Defender for Cloud overview page, you view recommendations for the environment you want to improve. On the Defender for Cloud asset inventory page, recommendations are shown according to the affected resource.

To view and manage Amazon EC2 alerts and recommendations:

- Learn about the different types of [alerts available in Defender for Cloud](/azure/defender-for-cloud/alerts-overview) and how to respond to alerts.
- [Improve your security posture by implementing recommendations](/azure/defender-for-cloud/review-security-recommendations) from Defender for Cloud.
- Learn how to [access the asset inventory page](/azure/defender-for-cloud/asset-inventory) of Defender for Cloud.

>[!Note]
>[Microsoft cloud security Benchmark](/security/benchmark/azure/introduction) (MCSB) includes a collection of high-impact security recommendations you can use to help secure your cloud services in a single or multi-cloud environment. Microsoft recommends using security benchmarks to help you quickly secure cloud deployments. Learn more about the MCSB.
>

### C. Integrate Microsoft Defender for Endpoint with Defender for Cloud

Protect your endpoints with Defender for Cloud's integrated endpoint detection and response solution, Microsoft Defender for Endpoint. Microsoft Defender for Endpoint protects your Windows and Linux machines whether they're hosted in Azure, on-premises, or a multi-cloud environment. Microsoft Defender for Endpoint is a holistic, cloud-delivered, endpoint security solution. The main features include:

- Risk-based vulnerability management and assessment
- Attack surface reduction
- Behavioral based and cloud-powered protection
- Endpoint detection and response (EDR)
- Automatic investigation and remediation
- Managed hunting services

For more information, see [Enable the Microsoft Defender for Endpoint integration](/azure/defender-for-cloud/integration-defender-for-endpoint.md#enable-the-microsoft-defender-for-endpoint-integration).

### D. Monitor Amazon EC2 data in Microsoft Sentinel

Once you install Azure Connected Machine agent and AMA, Amazon EC2 operating systems start sending logs into Azure Log Analytics tables that are automatically available to Microsoft Sentinel.

The image below demonstrates how Amazon EC2 operating system logs are ingested by Microsoft Sentinel. The Azure Connected Machine agent makes your Amazon EC2 VMs part of Azure. The Windows Security Events via AMA data connector collects data from your Amazon EC2 VMs.

Insert image

>[!Note]
>You don't need Microsoft Sentinel to ingest logs from Amazon EC2 but you do need to have a Log Analytics workspace previously set up.
>

For more information, see [Amazon EC2 Sentinel Ingestion using Arc and AMA](https://github.com/rudneir2/AWS_EC2_Sentinel-Ingestion_using_ARC_AMA), which is a GitHub document, for step-by-step guidance. The GitHub document addresses installing AMA, which you can skip because you installed AMA earlier in this solution guide.

### E. Monitor in Microsoft Sentinel logs from Amazon Virtual Private Cloud (Amazon VPC), AWS CloudTrail, and Amazon GuardDuty

Earlier you connected Microsoft Sentinel to AWS using the Amazon Simple Storage Service (Amazon S3) connector. The Amazon S3 bucket sends logs to your Log Analytics workspace, the underlying tool used to query them. The following tables are created in the workspace:

- **AWSCloudTrail** - AWS CloudTrail logs hold all your data and management events of your AWS account.
- **AWSGuardDuty** - Amazon GuardDuty Findings represent a potential security issue detected within your network. Amazon GuardDuty generates a finding whenever it detects unexpected and potentially malicious activity in your AWS environment.
- **AWSVPCFlow** - Amazon Virtual Private Cloud (Amazon VPC) Flow Logs enable you to capture IP traffic going to and from your Amazon VPC network interfaces.

You can query Amazon VPC Flow Logs, AWS CloudTrail and Amazon GuardDuty in Microsoft Sentinel. The following are query examples for each service and corresponding table in Log Analytics:

**For Amazon GuardDuty logs:**

AWSGuardDuty
| where Severity > 7
| summarize count() by ActivityType

**For Amazon VPC Flow logs:**

AWSVPCFlow
| where Action == "REJECT"
| where Type == "Ipv4"
| take 10

**For AWS CloudTrail logs:**

AWSCloudTrail
| where EventName == "CreateUser"
| summarize count() by AWSRegion
 
In Microsoft Sentinel, you utilize the Amazon S3 workbook to analyze additional details.

For AWS CloudTrail you can analyze:

- Data flow over time
- Account IDs
- Event Source list  

For Amazon GuardDuty, you can analyze:

- Amazon GuardDuty by map
- Amazon GuardDuty by region
- Amazon GuardDuty by IP

### F. Use Microsoft Sentinel built in detection rules to create and investigate threat detection rules in your environment

Now that you've connected your data sources to Microsoft Sentinel, use Microsoft Sentinels built-in detection rule templates to help you create and investigate threat detection rules in your environment. Microso'ft Sentinel provides out-of-the-box, built-in templates to help you create threat detection rules.

Rule templates were designed by Microsoft's team of security experts and analysts based on known threats, common attack vectors, and suspicious activity escalation chains. Rules created from these templates will automatically search across your environment for any activity that looks suspicious. Many of the templates can be customized to search for activities, or filter them out, according to your needs. The alerts generated by these rules will create incidents that you can assign and investigate in your environment.

For more information, see [detecting threats with built-in analytics rules in Microsoft Sentinel](/azure/sentinel/detect-threats-built-in).

## Step 3: Improve your overall security posture

In this section you'll learn how Microsoft Entra Permissions Management can help you monitor unused and excessive permissions. You'll step through how to configure, onboard, and view key data. The Zero Trust **use least privileged access** principle is achieved by managing, controlling, and monitoring access to your resources.

| Steps | Task |
| --- | --- |
| A | Configure Permissions Management and Privileged Identity Management. |
| B | Onboard an Amazon Web Services (AWS) account. |
| C | View key statistics and data. |

### Configure Permissions Management

Permissions Management is a cloud infrastructure entitlement management (CIEM) solution that detects, automatically right-sizes, and continuously monitors unused and excessive permissions across your multi-cloud infrastructure.

Permissions Management deepens Zero Trust security strategies by augmenting the **use least privileged access** principle, allowing customers to:

- Get comprehensive visibility: Discover which identity is doing what, where, and when.
- Automate least privilege access: Use access analytics to ensure identities have the right permissions, at the right time.
- Unify access policies across IaaS platforms: Implement consistent security policies across your cloud infrastructure.

Permissions Management provides a summary of key statistics and data for AWS and Azure. The data includes metrics related to avoidable risk. These metrics allow the Permissions Management administrator to identify areas where risks related to the Zero Trust **use least privileged access** principle can be reduced.

Data can be fed into Microsoft Sentinel for further analysis and automation.

To implement tasks, see:

A. [Enable Permissions Management in your organization](/azure/active-directory/cloud-infrastructure-entitlement-management/onboard-enable-tenant)
B. [Onboard an AWS account on Permissions Management](/azure/active-directory/cloud-infrastructure-entitlement-management/onboard-aws)
C. [View key statistics and data](/azure/active-directory/cloud-infrastructure-entitlement-management/ui-dashboard)

## Step 4: Secure infrastructure as code

This section covers a key pillar of DevSecOps, scanning and securing your infrastructure as code.
For infrastructure as code, security and DevOps teams should monitor for misconfigurations that can lead to vulnerabilities in your infrastructure deployments.

By implementing continuous checks on Azure Resource Manager (ARM), Bicep, or Terraform templates, you prevent breaches and exploits early in development, when they are less costly to fix. You will also want to maintain tight control of administrators and service account groups across Azure Active Directory (Azure AD) and your DevOps tool.  

You'll implement the Zero Trust **use least privileged access** principle by:

- Conducting robust reviews of your infrastructure configurations with least privilege identity access and networking set up.
- Assigning users role-based access control (RBAC) to resources at the repository level, team level, or organization level.

**Prerequisites:**

- Code repositories are in Azure DevOps or GitHub
- Pipelines are hosted in Azure DevOps or GitHub

| Steps | Task |
| --- | --- |
| A | Enable DevSecOps for infrastructure as code (IaC). |
| B | Implement RBAC for DevOps tools. |
| C | Enable GitHub Advanced Security. |
| D | View code and secret scanning results. |

### A. Enable DevSecOps for IaC

Defender for DevOps provides visibility into the security posture of your multi-pipeline environment, regardless of whether your code and pipelines are in Azure DevOps or GitHub.  It has the additional benefit of implementing a single pane of glass where security and DevOps teams can see scan results of all their repositories in one dashboard, as well as set up a pull request process to remediate any issues.

For more information, see:

- [DevSecOps for IaC](/azure/architecture/solution-ideas/articles/devsecops-infrastructure-as-code)
- [DevSecOps with GitHub security](/azure/architecture/solution-ideas/articles/devsecops-in-github)

### B. Implement RBAC for DevOps tools

You need to manage and implement sound [governance](/azure/cloud-adoption-framework/secure/best-practices/end-to-end-governance) practices for your team, such as role-based access control permissions. If this model isn't mirrored for DevOps automation, your organization might leave a security back-door open. Consider an example where a developer doesn't have access via ARM templates, but still has sufficient permissions to change application code or infrastructure as code and trigger an automation workflow. The developer, indirectly via DevOps, can access and make destructive changes to your ARM templates.

When you deploy cloud-based solutions for your infrastructure deployments, security should always be your most important concern. Microsoft keeps the underlying cloud infrastructure secure. You configure security in Azure DevOps or GitHub.

To configure security:

- In [Azure DevOps](/azure/cloud-adoption-framework/ready/considerations/security-considerations-tools#azure-devops-role-based-access-considerations), you can use security groups, policies, and settings at the organization/collection, project, or object level.
- In [GitHub](/azure/cloud-adoption-framework/ready/considerations/security-considerations-tools.md#github-role-based-access-considerations), you can assign users access to resources by granting them roles at the repository level, team level, or organization level.

### C. Enable GitHub Advanced Security

To proactively secure environments, it's important to continuously monitor and strengthen DevOps security. GitHub Advanced Security automates checks in your pipeline to look for exposed secrets, dependency vulnerabilities, and more. GitHub makes extra security features available to customers under an Advanced Security license.

By default, GitHub Advanced Security is enabled for public repositories. For your private repositories, you need to leverage the GitHub Advanced Security licensing. Once enabled, you can start leveraging the many features that come with the GitHub Advanced Security suite. This includes:

- Code scanning
- Dependency scanning
- Secret scanning
- Access control
- Vulnerability alerts
- Audit log
- Branch protection rules
- Pull request reviews

With these features, you can ensure that your code is secure and compliant with industry standards. You can also create automated workflows to help you quickly detect and address any security issues in your code. Additionally, you can use branch protection rules to prevent unauthorized changes to your codebase.

For more information, see [Enable GitHub Advanced Security](https://docs.github.com/en/enterprise-cloud@latest/get-started/learning-about-github/about-github-advanced-security#enabling-advanced-security-features).

### D. View code and secret scanning results

[Defender for DevOps](/azure/defender-for-cloud/defender-for-devops-introduction), a service available in Defender for Cloud, enables security teams to manage DevOps security across multi-pipeline environments. Defender for DevOps uses a central console to empower security teams with the ability to protect applications and resources from code to cloud across multi-pipeline environments, such as GitHub and Azure DevOps.

Defender for DevOps exposes security findings as annotations in Pull Requests (PR). Security operators can enable PR annotations in Microsoft Defender for Cloud. Any exposed issues can then be remedied by developers. This process can prevent and fix potential security vulnerabilities and misconfigurations before they enter the production stage. You can configure PR annotations in Azure DevOps. You can get PR annotations in GitHub if you're a GitHub Advanced Security customer.

For more information, see:

- [Configure the Microsoft Security DevOps GitHub action](/azure/defender-for-cloud/github-action)
- [Configure the Microsoft Security DevOps Azure DevOps extension](/azure/defender-for-cloud/azure-devops-extension)
- [Enable pull request annotations in GitHub and Azure DevOps](/azure/defender-for-cloud/enable-pull-request-annotations)

## Next steps
