---
title: Integrate OT/IoT security into the Infrastructure/Networking discipline
description: Use the Microsoft security adoption model to secure OT/IoT assets and resources across the business, based on Zero Trust principles.
ms.date: 01/29/2026
ms.service: security
ms.subservice: zero-trust
author: MicrosoftGuyJFlo
ms.author: joflore
ms.topic: conceptual

#customer intent: As a business leader or security adopter, I want to understand how I can use the Microsoft security adoption model to secure OT/IoT assets across the business.
---

# Integrate OT/IoT security 

[Security disciplines](security-adoption-discipline-overview.md) are groupings of related security work that help teams to consistently deliver security outcomes across the entire technology estate.

Security disciplines are used in our security adoption model. They provide a bridge between [business scenarios](security-adoption-business-scenarios-overview.md) and technical implementation, ensuring that security investments translate into real, measurable outcomes. 

This article helps you to integrate OT/IoT security into the [Infrastructure and Networking Security discipline](security-adoption-discipline-infrastructure.md).

## Why integrate?

OT and IoT security is a specialized subset of the Infrastructure Security discipline, addressing systems with unique safety, availability, and reliability constraints that differ from traditional IT environments. The guidance helps organizations establish or modernize OT/IoT security while preserving operational continuity and safety.

OT and IoT systems increasingly appear in modern attack paths—as entry points, lateral movement paths, and high‑impact targets. Unlike IT systems, many OT environments are fragile, legacy (“brownfield”), and difficult or impossible to patch or modify.
Without a modern OT/IoT security discipline, organizations face:

- Production outages and safety incidents
- Ransomware attacks on industrial control systems
- Regulatory violations (for example, NERC CIP, IEC 62443)
- Physical damage or human harm
- Long‑term operational and reputational damage

Because these systems often support critical services, OT/IoT security is not optional—it is essential to operational resilience and public safety.

## Mission and outcomes

The mission of OT and IoT security is to protect OT systems and IoT devices that control physical processes or collect critical operational data, ensuring safety, availability, and resilience against cyber threats. Mission outcomes focus on:


- Improved visibility into all OT and IoT assets
- Isolation of OT/IoT environments from IT and the internet
- Secure remote and vendor access without disrupting operations
- Early detection of OT‑specific threats and anomalous behavior
- Reduced likelihood and impact of outages, safety incidents, and physical damage
- Compliance with industry and regulatory requirements
Without modern and effective OT/IoT security, organizations face increased risks of production outages, safety incidents, regulatory violations, and targeted attacks on industrial control systems—leading to operational downtime, financial loss, reputational damage, and potential harm to public safety.

The following diagram from the Microsoft Cybersecurity Reference Architectures (MCRA)](..\..\workshops\mcra.md) illustrates the range of OT and IoT Devices that must be secured.  The MCRAs are [available as a download](https://download.microsoft.com/download/956f9359-e6d5-4e77-a36c-117f94620eb3/MCRA-April-2025.pptx).

:::image type="content" source="./media/security-adoption-discipline-iot.png" alt-text="OT and IoT device types" lightbox="./media/security-adoption-discipline-iot.png":::


## Manage change

OT and IoT Security modernization is focused on continuously improving the ability of the organization to discover, monitor, and protect specialized operational technology and IoT devices that are often not included in IT cybersecurity efforts, controls, or scope. Modernizing OT and IoT security requires incremental, risk‑based change, not wholesale replacement.

Key change principles include:

- **Visibility**: Use passive monitoring to discover and understand OT/IoT assets and communications.
- **Isolation**: Segment and isolate OT environments to reduce exposure before applying other controls.
- **Operational safety**:  Security controls must not disrupt real‑time operations or safety systems.
- **Procurement**: Long‑term security improves when security requirements are embedded in purchasing decisions.
- **Alignment**: Sustainable security depends on alignment between people, process, and technology. For example, training operators, updating procedures, and consistently enforcing controls.
- 
Modernization ensures operational resilience, compliance with industry regulations, and protection against both direct OT and IoT threats as well as indirect threats via the IT environment. Without these efforts, organizations face increased vulnerability to ransomware targeting industrial systems, supply chain attacks, insider threats, and nation-state actors, leading to production disruptions, safety hazards, regulatory penalties, and potential catastrophic failures.

## Modernization strategy

The OT and IoT security technology strategy combines near‑term risk reduction with long‑term structural improvements to reduce the likelihood and impact of cybersecurity incidents that could cause human harm, physical damage, or business disruption.

Unlike IT environments, most OT and IoT systems are long‑lived, safety‑critical, and difficult to change. This strategy acknowledges those constraints and focuses on practical, sustainable controls that protect operations without disrupting safety or availability.

This diagram illustrates the key strategic priorities for OT and IoT security:

:::image type="content" source="./media/security-adoption-discipline-iot-strategy.png" alt-text="Shows strategic security strategies for OT/IoT security" lightbox="./media/security-adoption-discipline-iot-strategy.png":::

The key challenge is that most OT environments are composed of legacy (“brownfield”) systems that are fragile, unsupportable, or difficult to modify. Common constraints include:

- Software that cannot be easily updated or patched
- Operating systems or hardware no longer supported by vendors
- Vendors that are out of business or have ended product support
- Regulatory or safety requirements that make changes costly or impractical

As a result, many standard IT security practices—such as active vulnerability scanning, frequent patching, or installing endpoint agents—are difficult or unsafe to apply in OT and IoT environments.
These constraints require a focused set of short‑term and long‑term strategic priorities.

### Strategic priorities

These constraints require focusing on a small number of short-term and long-term strategic priorities:

- **Short Term - Monitor** - Use ***passive*** monitoring of network data to inventory devices and identify anomalous activities that may represent an attack. Note that *Actively* scanning for software vulnerabilities can cause some remote systems to crash, sometimes requiring a site visit to a distant or uninhabited remote location to physically restart the system. 
- **Short Term - Isolate** - Isolate OT and IoT devices from direct internet access and from other internet connected devices, including standard user IT devices and networks. 
- **Short Term - Other Controls _(as applicable)_** - Design and implement other controls that are available to secure the systems which may include physical isolation of highly sensitive systems, application of IT best practices such as software updates (if available), and more. 
- **Long Term - Purchase or Replace** - Procurement policy requires ability to secure devices for their full operational lifetime

The specific mix of controls will vary based on device types, operational constraints, and procurement cycles.

#### Short Term - Isolate OT and IoT environments

Effective isolation requires more than just simple network segmentation with firewall rules to block traffic. Achieving effective security isolation that resists real world threat actors and doesn't disrupt business processes requires a comprehensive and thoughtful process that is executed consistently over time. 

The process of isolation should include:

 - **Modelling business processes, technology, and threats** - Discover and document the systems and how they are used within business workflows, how the technology is configured, and how threat actors may gain access to and abuse those systems. 
 - **People, process, and technology considerations** - During modelling, security design, and implementation, you must take a holistic approach that considers people, processes, and technology. Some examples to illustrate include:

    - *Technology* - Block unauthorized communications, detect threats, and rigorous security controls for all bridging/transit devices.
    - - *Process* - Establish, monitor, and update organizational policy, business process, technical procedures, and governance to sustain assurances over time.
    - - *People* - Train all stakeholders (employees, vendors, etc.) on isolation strategy including *what* they are supposed to do, *why* it is important, and *how* to execute those procedures.

 - **Apply to all layers** - Ensure that your analysis, design, and implementation isn't restricted to just networking or another control type - evaluate and consider all aspects of the system including identities and accounts used for access, network connectivity paths, physical access, operating system and applications, and more. 
 - **Secure border/transient devices and entities** - The devices that are able to access the isolated OT and IoT environments must be secured rigorously as the security of those environment depends on them. This is simlar to how a sealed system such as a water tank relies on the integrity of the few pipes and valves that allow access to it. You must apply rigorous people, process, and techology controls to all devices that are allowed to be permanently connected to the environment (such as monitoring workstations) and that transit in or out (such as vendor laptops used to maintain the equipment). See the [privileged access guidance](security-adoption-identity-access-privileged-model.md) for more information on establishing highly secured devices.

This diagram visually illustrates key points for isolating high value assets like OT and IoT environments: 

:::image type="content" source="./media/security-adoption-discipline-iot-isolation.png" alt-text="Key aspects of isolating high value assets" lightbox="./media/security-adoption-discipline-iot-isolation.png":::

### Long Term - Purchase or Replace

Include security requirements in procurement policy to ensure that the organization's security, productivity, and agility increase over time rather than degrading with the passage of time. 

Without including these requirements in the procurement process, business operations will incur greater cost and risk over the lifetime of the equipment. 

This is illustrated by this diagram comparing the typical outcomes of purchasing of business critical equipment when security requirements are included vs. not:

:::image type="content" source="./media/security-adoption-discipline-iot-system.png" alt-text="Compares security outcomes" lightbox="./media/security-adoption-discipline-iot-system..png":::

In the top example (A), the organization makes a large purchase with incomplete requirements that don't include security requirements. This results in the support contract ending earlier (which often requires paying extra for security support that may not be included in the budget) and the bankruptcy of the vendor and/or product end of life. This results in elevated risk of business operations being disrupted by threat actors or the need to isolate these systems to protect them. 

In the second example (B), the organization includes security requirements during the procurement process. This allows the negotiation process to include evaluation of key factors. This should include considerations that impact the ability to keep the system secure over its expected operating lifetime including:
- *Vendor provides security updates for operational lifetime* - Does the contract require the vendor to provide software security updates (patches) for the lifetime of the equipment? (which is required to keep any system with software secure against known vulnerabilities)
- *Vendor follows security development lifecycle* - Does the vendor apply sound security practices to software development? This reduces the number and severity of software security vulnerabilities that will have to be implemented later (which creates security risk and operational downtime for maintenance). This also reduces permanent design flaws that cannot be fixed with a software upate that your organization will have to develop workarounds for. 
- *Vendor business strategy change* - Is the vendor likely to change business strategies that would interrupt security assurances? (discontinue product line, divest or sell business unit, be acquired by another organization, etc.) 
- *Vendor solvency* - Is the vendor likely to avoid bankruptcy so that they can fulfill their contractual obligations for security? 

Evaluating these factors and others that can impact the security of business critical equipment allows the organization to ensure they get what they need from the equipment or to develop workarounds to compensate for the risk. 

> [!TIP]
> The motivation for a vendor to address your security requirements often dramatically drops after the purchase contract is signed. Prior to the deal being closed, the vendor sales and management team is focused on meeting your needs so that they can close the deal to meet their sales goals, but this motivation disappears after the contract is signed.
>
> This makes it critical to ensure that your security requirements are included early to ensure that you have security updates and support for the expected operational lifetime of any new equipment purchases or it will be difficult, expensive, or impossible to get later. 

Organizations must consider security requirements along with other business requirements and perform the appropriate analysis, due diligence, and tradeoffs required to balance all requirements. 

Some examples of organizations proactive managing this risk include:
- A vendor may not offer support for the full operating lifecycle, but may be willing to extend that support or offer a discount to close the deal.
- A vendor may not be using current operating software for their equipment, but may be willing to update their system to close a deal and get your business.
- An organization may need cutting edge specialized equipment from a smaller startup vendor that has a higher risk to develop a new business line. In this case, the organization can develop a contingency plan to access the source code for the equipment and have their own developers take over maintainence to keep the business line running.
- An organization may choose to favor a vendor that provides long term assurances to avoid this risk entirely. 

> [!TIP]
> **Be Proactive and don’t blindly assume early replacement is automatically ‘too expensive’** - Organizations should also consider the potential business and security beenfits of upgrading or replacing equipment early (rather than 'sweating the assets' for maximum lifetime). 
>
> Sometimes people assume that the cost of replacing a legacy system is always too expensive. Organizations should perform full analysis of the lifetime total cost of maintaining legacy equipment vs. upgrading it or replacing it. Organizations often face many hidden costs from older systems including loss of business agility, maintenance costs, and security risks. The cost of a disruption from a cyberattack (which could be weeks or months of lost revenue and other impact) may be greater than the cost of upgrading or retrofitting security to the equipment. Organizations may also find that the productivity gains from newer equipment may offset the cost of the upgrade. 

## Discipline roles and collaborators

OT and IoT Security roles are responsible for protecting operational technology systems, industrial control systems (ICS), and Internet of Things devices that monitor and control physical processes. These roles ensure security controls are implemented while maintaining operational requirements and safety standards. In smaller organizations, these responsibilities may be combined with infrastructure or security operations roles, while larger enterprises typically assign dedicated OT/IoT security specialists.

Primary roles include:

- **Security Architect** – Designs secure architectures for operational technology environments, applying zero trust principles while respecting air-gap requirements and operational constraints unique to industrial systems.
- **Operational Technology (OT) Engineering and Operations** - Focuses on securing Industrial Control Systems (ICS), Supervisory Control and Data Acquisition (SCADA) environments, and programmable logic controllers (PLCs) used to control and monitor physical processes. These role(s) implement and manages security monitoring, network segmentation, threat detection for OT and Industrial IoT devices, and other security controls without disrupting business operations.
- **Internet of Things (IoT) Professionals** - Focuses on integration of IoT Devices and data into the organization's business workflows, services, and custom applications. 

Key internal collaborators include:

- **Front Line Workers (Business Operations and Engineering Teams)** – Maintain production systems and ensure security controls don't interfere with operational processes. Ensure that appropriate logging and telemetry is integrated with SIEM and other security systems. 
- **Front Line Workers (Vendor Management)** – Oversee third-party access to OT systems and industrial equipment maintenance.
- **Infrastructure/Platform and Network Engineering and Operations Teams** – Coordinate network segmentation and secure connectivity between IT and OT environments.
- **Security Operations (SecOps/SOC)** – Monitor OT/IoT-specific threats and respond to incidents affecting operational systems.
- **Security Compliance Management / Compliance and Audit team** – Ensure adherence to industry-specific regulations (NERC CIP, IEC 62443, NIST CSF).
- **CISO and Security Directors/Managers** – Define strategic priorities, risk tolerance, and compliance objectives for OT/IoT security.

No role operates in isolation. Security professionals must understand both cybersecurity principles ***and*** operational requirements for OT and IoT systems. Safety and availability often take precedence over traditional security controls in OT environments, requiring specialized approaches that balance security with operational needs.

## Integration with other disciplines

OT and IoT security must integrate tightly with other disciplines:

- **Infrastructure Security** – OT/IoT security is a specialized subset focused on industrial systems.
Security Operations (SecOps/SOC) – Enables detection and response for OT/IoT‑specific threats.
- **Security Posture Management** - These teams must include IoT and OT devices and environments into their discovery, prioritization, and mitigation efforts. This helps the organization understand and manage their attack surface, access paths, and resulting risk. 
- **Security Operations (SecOps/SOC)** - SecOps teams must have training, processes, and technology to detect and respond to attacks on these assets so that the organization doesn't experience increased damage and risk from OT and IoT blind spots. 

## Integration with technology pillars

Executing the strategy of the OT and IoT security discipline requires security controls across multiple technology pillars.

**Pillar** | **Role of Infrastructure Security**
--- | ---
**Identities** |  Identity controls for OT/IoT environments must account for machine identities, service accounts used by automation systems, and human operators who require access to industrial controls.
**Endpoints**| OT endpoints including industrial workstations, engineering stations, and operator terminals require specialized security to protect these specialized systems without impeding real-time operations.
**Infrastructure**| OT infrastructure including industrial control systems, SCADA servers, historians, and PLCs requires visibility and protection while maintaining operational requirements and air-gap architectures where appropriate.
**Apps** | Applications that interface with OT/IoT devices must be secured to prevent unauthorized control of physical systems. This includes human-machine interfaces (HMI), SCADA applications, and industrial software.
**Data** |  Operational data from sensors, control systems, and industrial processes must be protected both at rest and in transit, while maintaining the integrity critical for safe operations.
**Network**|  Network segmentation between IT and OT environments is critical, along with monitoring of industrial protocols (Modbus, OPC, DNP3) and secure remote access for vendors and operators.
**AI** | AI and machine learning can enhance OT security through anomaly detection in industrial processes, predictive maintenance, and automated threat identification while respecting operational constraints.

## Microsoft resources 


### Workshops

Microsoft Unified offers expert-led workshops to help organizations modernize their IOT/IoT security strategy. These workshops include:

- **Architecture and strategy workshops** - The *Security Adoption Framework (SAF) - Architecture Design Session: Infrastructure and Development Security* workshop focuses on accelerating development security modernization and integration with infrastructure security.. This workshop is available as a less than four-hour topic summary/discussion focused on key learnings and best practices.
- **Technology adoption workshops** - Microsoft Unified has workshops to help organizations learn about, plan, implement, and optimize the use of Microsoft infrastructure and networking technologies.

### Technologies

Microsoft offers technology solutions that enable and accelerate modernization of OT and IoT security.

This includes both primary enablement technology and key enabling technologies. 

**Technology** | **Details**
--- | ---
[**Microsoft Defender for Endpoint**](/defender-for-iot/enterprise-iot) | Enterprise IoT in the Microsoft Defender portal provides support for Enterprise IoT security. [Review license information for Defender for Endpoint and Defender XDR](/defender-xdr/protect-against-iot-ot-threats#enterprise-iot-device-protection-in-defender-for-endpoint-and-defender-xdr).
[**Microsoft Entra**](/entra/fundamentals/whatis) | Provides identity management for OT operators, engineers, and service accounts accessing industrial systems.
[**Microsoft Intune**](/intune/intune-service/fundamentals/what-is-intune) | Secures OT workstations and engineering stations used to manage industrial systems.
[**Microsoft Defender XDR**](/defender-xdr/microsoft-365-defender) | Provides detection and response capabilities for OT workstations and IT systems connected to operational environments (via Microsoft Defender for IoT).
[**Microsoft Sentinel**](/azure/sentinel/overview) | SIEM solution that correlates OT security alerts with IT security events for comprehensive threat detection.
**Microsoft Azure** | Provides secure cloud infrastructure for OT data analytics, remote monitoring, and secure connectivity including [Azure IoT Hub](/azure/iot-hub/about-iot-hub), [Azure Firewall](/azure/firewall/overview), and [Azure Private Link](/azure/private-link/private-link-overview),
[**Microsoft Azure Sphere**](/azure-sphere/product-overview/what-is-azure-sphere) | Provides a comprehensive IoT solution that provides a secured, connected microcontroller unit (MCU), a custom Linux-based OS, and a cloud-based security service.

