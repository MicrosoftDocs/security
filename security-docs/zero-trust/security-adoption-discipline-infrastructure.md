---
title: Establish an Infrastructure and Networking discipline
description: Use the Microsoft security adoption model to secure cloud infrastructure, including networks, based on Zero Trust principles.
ms.date: 01/29/2026
ms.service: security
ms.subservice: zero-trust
author: MicrosoftGuyJFlo
ms.author: joflore
ms.topic: conceptual

#customer intent: As a business leader or security adopter, I want to understand how I can use the Microsoft security adoption model to effectively secure cloud infrastructure and networking across the business.
---

# Establish an Infrastructure Security discipline

This article helps security and technology teams establish and modernize an Infrastructure Security discipline across the company.  This discipline focuses on protecting the foundational systems and platforms that underpin the security of systems and data across the organization. 

[Security disciplines](security-adoption-discipline-overview.md) are groupings of related security work that help organizations consistently deliver security outcomes across the entire technology estate. Within the security adoption model, disciplines help provide a bridge between [business scenarios](security-adoption-business-scenarios-overview.md) and [technical implementation](implement-overview.md), ensuring that security investments translate into real measurable outcomes as part of the [security adoption model](security-adoption-model.md).


## Why this discipline?

The Infrastructure Security discipline helps organizations reduce risk from large‑scale compromise by preventing and limiting damage to datacenters, servers, containers, networks, storage, cloud services, and other resources that store and process sensitive data and workloads. 

It's a key strategic priority frequently targeted by threat actors because compromise allows them access to many systems at once. A modern, disciplined approach to infrastructure security limits blast radius, improves resilience, and enables secure operations at scale.

Infrastructure underpins every security outcome. If the cloud, containers, virtualization or other infrastructure platforms are compromised, attackers can rapidly access workloads, data, and identities across the organization.
Without effective infrastructure and networking security, organizations might experience:

- Ransomware and extortion attacks
- Large‑scale data breaches
- Regulatory non‑compliance
- Operational outages and service disruption

These impacts translate directly into financial loss, reputational damage, and harm to customers and critical services. Infrastructure security is therefore a strategic priority, not just a technical concern.

## Mission and outcomes

The mission of the Infrastructure Security discipline is to safeguard the foundational systems that support workloads and data across on‑premises, hybrid, and multi‑cloud environments. Outcomes of the mission include:

- Reduced blast radius from infrastructure compromise
- Consistent security controls across environments
- Improved resilience against ransomware and service outages
- Stronger protection for sensitive workloads and data
- Alignment of infrastructure security with business risk

Infrastructure security reduces risk by preventing, detecting, and limiting damage to datacenters, servers, containers, networks, storage, and cloud services throughout their lifecycle.


## How to apply this discipline

To apply the Infrastructure and Networking Security discipline effectively, focus on establishing a consistent approach to securing the platforms and connectivity that support your organization:

- **Define an infrastructure security strategy aligned to business risk**  
  Establish a clear approach for securing platforms, workloads, and network environments in a way that protects critical systems and reduces the most significant risks.

1. **Ensure consistent protection across hybrid and multicloud environments**  
  Apply a unified approach to securing infrastructure across on-premises, cloud, and edge environments to reduce gaps and inconsistencies.
1. **Establish standardized security configurations and practices**  
  Provide clear guidance to ensure that infrastructure and network controls are implemented consistently across environments and workloads.
1. **Align infrastructure security with business-critical services and scenarios**  
  Prioritize protections for the systems and services that support critical business operations and key scenarios such as secure remote work and protection of critical assets.
1. **Continuously monitor and improve infrastructure security posture**  
  Use insights from vulnerabilities, misconfigurations, and operational signals to strengthen protections and reduce risk over time.



## Manage change

The Infrastructure Security Technology Strategy defines how an organization leverages modern tools and architectures to protect its foundational systems where critical data resides. 

- Strategy focuses on implementing zero trust principles, advanced threat protection, automated patching, and continuous monitoring to ensure confidentiality, integrity, and availability of data across hybrid environments. 
- Strategy aligns technology investments with risk reduction goals, enabling secure connectivity, resilience against cyberattacks, and compliance with regulatory standards.
- Without a clear strategy, organizations face fragmented security controls, increased vulnerabilities, and higher risks of data breaches, service outages, and regulatory penalties.

Modernization of this discipline is focused on:

- Continuously improving infrastructure security throughout the lifecycle of govern, identify, protect, detect, respond, and recover. 
- Implementing security controls such as Zero Trust architecture, automated patching, and continuous monitoring to enhance visibility and address evolving threats/compliance requirements. 

These efforts ensure confidentiality, integrity, and availability of data by reducing attack surfaces, preventing unauthorized access, and maintaining resilience against disruptions.

Technology infrastructure is highly complex, has many moving parts, is constantly evolving, and must stay secure against persistent and evolving threats. This means that effective infrastructure security must be:

- **Comprehensive** - Controls must address the various technical elements of infrastructure including networks, endpoints (servers, containers, and more), data, apps, and more to avoid providing threat actors an unguarded access path they can exploit. This requires using a combination of well-know security techniques and the integration of advanced automation and technology as it becomes available. 
- **Consistent and Rigorous** - Security controls must be applied consistently and rigorously across all instances of each technology to avoid providing threat actors an opportunity to exploit vulnerabilities in overlooked or undiscovered resources.
- **Continuously Improved** - Both the infrastructure itself and the threat actors are constantly evolving, so all aspects of security must continuously evolve as well including threat models, security architectures and controls, how security is integrated into infrastructure management and automation, and more. 

Change management is critical. Infrastructure operators must be involved early and consistently—security controls that ignore operational reality will fail or be bypassed.

## Discipline roles and collaborators

The Infrastructure Security discipline typically requires close collaboration between technical and security teams. These roles must:

- Work together to ensure that security controls are embedded across infrastructure layers to maintain confidentiality, integrity, and availability of data.
- Are responsible for planning, designing, and operating secure foundational systems (networks, compute, storage, and cloud platforms) where critical data resides.

In larger organizations, infrastructure security responsibilities are typically owned by dedicated specialists. In smaller organizations, roles might be combined with other technical roles.

Primary Roles:

- **Security Architect** – Designs secure architectures for on-premises and cloud infrastructure, applying zero trust principles and integrating identity, network, and platform security.
- **Infrastructure Engineering and Operations** – Implements and manages secure configurations, patching, monitoring, and compliance for servers, networks, and cloud workloads. Maintain secure configurations and enforce compliance across infrastructure components.
- **Network Engineer** – Focuses on secure connectivity, segmentation, and protection of data in transit across hybrid environments.


Key internal collaborators include:

- **Enterprise and Solution Architects** – Ensure security requirements are integrated into infrastructure designs and modernization initiatives.
- **Security Strategy, Integration, and Governance** – Provides governance and oversight for security controls, aligning infrastructure security with organizational risk management. Helps prioritize projects and vulnerabilities based on organizational risk and impact. 
- Developers and Application Teams – Collaborate to ensure infrastructure supports secure application deployment and data protection.
- CISO and Security Leadership – Define strategic priorities, risk tolerance, and compliance objectives for infrastructure security.

Infrastructure architects must understand how identity, network, and platform security intersect to protect workloads effectively.

## Alignment with other disciplines

Infrastructure and Networking security works in concert with other SAF disciplines:

- Access and Identities – Secures privileged and service access to infrastructure
- Security Operations (SecOps) – Detects and responds to infrastructure‑based attacks
- Data Security – Protects sensitive data hosted and processed on infrastructure
- Security Architecture and Governance – Aligns controls with risk and business priorities

This alignment ensures infrastructure security supports end‑to‑end security outcomes rather than operating as an isolated silo.

## Alignment with technology pillars

## Infrastructure security and technology pillars 

Executing the strategy of the infrastructure security discipline requires security controls across multiple technology pillars:

:::image type="content" source="./media/security-adoption-discipline-infrastructure.png" alt-text="Infrastructure Security - mapping to technology pillars" lightbox="./media/security-adoption-discipline-infrastructure.png":::


**Pillar** | **Role of Infrastructure Security**
--- | ---
**Identities** | Identity controls form the foundation of all access control - just as you can't form a sentence without a subject and object, you cannot establish reliable access policies that determine who can access what if you don't have accounts and identities assigned to employees, partners, customers, AI agents, computers, applications, microservices, and more. Attackers regularly try to compromise and abuse accounts, credentials, tokens, and other identity artifacts to gain access to business assets in the organization (often prioritizing privileged accounts like IT admins to get access to many or all digital assets in the organization).
**Endpoints** | Access control assurances rely on endpoint security to be effective. Attackers who compromise an endpoint can impersonate accounts that sign onto the endpoint and can steal credentials, tokens, and other identity artifacts for later attacks. Retiring legacy authentication protocols and cryptography often requires updating and reconfiguring endpoints.
**Infrastructure**| The organization's infrastructure hosts identity systems (such as Active Directory Domain Controllers, LDAP servers, federation servers, and more), so any compromise of these assets can result in a compromise of many or all accounts and identities in the organization. Additionally, IT administrators must follow identity and access best practices for privileged accounts used to manage infrastructure assets (including infrastructure as code (IAC) and other automation). Retiring legacy authentication protocols and cryptography often requires updating and reconfiguring infrastructure.
**Apps** | Applications are a key store of value for the organization and are commonly used as entry points by threat actors to gain access to other assets. All apps must follow access and identity security best practices including commercial Software as a Service (SaaS) and mobile apps, custom developed apps, CI/CD processes for development, and more.
**Data** | Data is a key store of value for the organization and often targeted by attackers for intellectual property theft, encryption to gain leverage for extortion or ransomware, planning future attacks, and other purposes. Security best practices must be followed rigorously because access and identity is the primary means of protecting data.
**Network**|  Network controls are foundational to access control. While network was once the dominant access control technology and skill, the utility and importance of network controls has diminished as assets are increasingly on cloud providers, mobile devices, and other environments outside of the organization's network. Access and Identity can no longer primarily focus only network controls, but must maintain basic controls to block older attacks and integrate network enforcement into modern controls like security service edge (SSE).
**AI** | AI Apps and Agents must have identities to govern what they can access and these must be carefully designed to enforce the least privilege principle and monitor for anomalous activity. AI also increases the volume and quality of all attacks, further amplifying the need to follow security best practices like phishing resistant authentication and more. Access and Identity can also take advantage of AI to automate discovery of policy misconfigurations and other issues.

## Microsoft resources

### Workshop

Microsoft Unified offers expert-led workshops to help organizations modernize their Infrastructure Security strategy, architecture, and technology. These workshops include:

- **Architecture and strategy workshops** - The *Security Adoption Framework (SAF) - Architecture Design Session: Infrastructure and Development Security* workshop focuses on accelerating development security modernization and integration with infrastructure security.. This workshop is available as a less than four-hour topic summary/discussion focused on key learnings and best practices.
- **Technology adoption workshops** - Microsoft Unified has workshops to help organizations learn about, plan, implement, and optimize the use of Microsoft infrastructure and networking technologies including Microsoft Entra and Microsoft Intune.


### Technology

Microsoft offers technology solutions that enable and accelerate modernization of infrastructure security.

**Technology** | **Details**
--- | ---
**Microsoft Defender for Cloud** | Provides extended detection and response (XDR) and posture management capabilities to monitor and secure your 'hybrid of everything' infrastructure across Azure, AWS, GCP, and on-premises resources (including VMs, Networks, Kubernetes/Containers, SQL, Storage, IoT/OT, & more). Key capabilities within Microsoft Defender for Cloud include:<br/><br/> - [*Defender for Servers*](/azure/defender-for-cloud/defender-for-servers-overview) - provides recommendations to improve and remediate security posture, protects machines against real-time security threats and attacks with Defender for Endpoint integration, and offers agentless scanning for vulnerabilities.<br/>   - [*Defender For Containers*](/azure/defender-for-cloud/defender-for-containers-introduction) - cloud-native solution to enhance, monitor, and maintain the security of your containerized assets (Kubernetes clusters, nodes, workloads, registries, images, and more) and their applications across multicloud and on-premises environments.<br/>- [*Defender for SQL*](/azure/defender-for-cloud/defender-for-sql-introduction) - helps discover and mitigate potential database vulnerabilities with vulnerability assessment and alerts on anomalous activities that might indicate threats to your databases.<br/>- [*Defender for Storage*](/azure/defender-for-cloud/defender-for-storage-introduction) - detects potential threats to storage accounts with malware scanning and sensitive data threat detection across Azure Blob Storage, Azure Files, and Azure Data Lake Storage.<br/>- [*Defender for Databases*](/azure/defender-for-cloud/defender-for-databases-overview) - helps protect database estates from threats and vulnerabilities with threat protection and security management for Azure SQL, open-source databases, and Cosmos DB.<br/>- [*AI Security Posture Management*](/azure/defender-for-cloud/ai-security-posture) - discovers generative AI applications, identifies vulnerabilities, and reduces risks with built-in recommendations and attack path analysis for AI workloads.
[**Microsoft Sentinel**](/azure/sentinel/overview) | Cloud native SIEM + SOAR + Data Lake solution that includes detection and response for infrastructure components.
[**Azure Arc**](/azure/azure-arc/overview) | Enables unified governance and management across on-premises data centers, multiple clouds, and edge components by projecting your existing non-Azure and/or on-premises resources into Azure Resource Manager.
[**Microsoft Entra**](/entra/fundamentals/whatis) | Supports strong identities for developers as well as identities for the application and avoiding roll your own identities and crypto
[**Microsoft Intune**](/intune/intune-service/fundamentals/what-is-intune) | Supports with cloud-based endpoint management solution for securing developer workstations with mobile device management (MDM) and mobile application management (MAM) 
[**Microsoft Defender XDR**](/defender-xdr/microsoft-365-defender) | Supports with detection and response capabilities for developer workstations, CI/CD systems, servers, containers, and more that are required for a secure development environment.  
**Microsoft Azure** | Supports with security capabilities in the cloud infrastructure that should be leveraged for software design and implementation including [Azure Firewall](/azure/firewall/overview), [Azure WAF](/azure/web-application-firewall/overview), [DDoS Protection](/azure/ddos-protection/ddos-protection-overview), [Azure Key Vault](/azure/key-vault/general/overview), [Azure Bastion](/azure/bastion/bastion-overview), [Azure Lighthouse](/azure/lighthouse/overview), and [Azure Backup](/azure/backup/backup-overview). 

What's next?

[Learn how](security-adoption-discipline-iot.md) OT/IoT security integrates into the Infrastructure and Networking discipline.