---
title: Integrate OT/IoT security into the Infrastructure/Networking discipline
description: Use the Microsoft security adoption model to secure OT/IoT assets and resources across the business, based on Zero Trust principles.
ms.date: 05/24/2026
ms.service: security
ms.subservice: zero-trust
author: rayne-wiselman
ms.author: raynew
ms.topic: conceptual

#customer intent: As a business leader or security adopter, I want to understand how I can use the Microsoft security adoption model to secure OT/IoT assets across the business.
---

# Establish an OT/IoT discipline

This article outlines the OT/IoT Security discipline. It focuses on establishing or modernizing security for specialized Internet of Things (IoT) and Operational Technology (OT) devices, while preserving operational continuity and safety.

[Security disciplines](security-adoption-discipline-overview.md) are groupings of related security work that help organizations consistently deliver security outcomes across the entire technology estate. Within the security adoption model, disciplines help provide a bridge between [business scenarios](security-adoption-business-scenarios-overview.md) and [technical implementation](implement-overview.md), ensuring that security investments translate into real measurable outcomes as part of the [security adoption model](security-adoption-model.md).


## Why OT/IoT security?

OT/IoT security addresses systems with unique safety, availability, and reliability constraints. 

OT and IoT systems increasingly appear in modern attack paths as entry points, lateral movement paths, and high‑impact targets. The key challenge is that most OT environments are composed of legacy (“brownfield”) systems that are fragile, unsupportable, or difficult to modify. Common constraints include:

- Software that can't easily be updated.
- Operating systems or hardware that's no longer supported.
- Vendors ending product support or gone out of business.
- Regulatory or safety requirements that make changes costly or impractical.

Without a modern OT/IoT security discipline, organizations face:

- Increased risk of production outages and safety incidents.
- Targeted attacks, including ransomware, on industrial control systems.
- Regulatory violations (for example, NERC CIP, IEC 62443).
- Physical damage and potential harm to human safety.
- Operational downtime, and long‑term operational and reputational damage.

Because these systems often support critical services, OT/IoT security is essential to operational resilience and public safety.


## Mission and outcomes

The mission is to protect OT systems and IoT devices that control physical processes or collect critical operational data. Outcomes of the mission include:

- Improved visibility into all OT/IoT assets.
- Isolation of OT/IoT environments from IT environments and the internet.
- Keep operations resilient and compliant.
- Secure remote and vendor access without disrupting operations.
- Early detection of OT‑specific threats.
- Reduced likelihood and impact of outages, safety incidents, and physical damage.
- Compliance with industry and regulatory requirements.

The following diagram from the [Microsoft Cybersecurity Reference Architecture (MCRA)](microsoft-reference-architecture.md) illustrates the range of OT and IoT Devices that must be secured.  

:::image type="content" source="./media/internet-of-things-devices.png" alt-text="OT and IoT device types" lightbox="./media/internet-of-things-devices.png":::

## How to apply this discipline

To apply the OT/IoT discipline effectively, focus on establishing a coordinated approach to securing connected devices and operational environments while maintaining safety and availability:

1. **Define an OT/IoT security strategy aligned to operational risk**  
  Establish a clear approach for identifying, prioritizing, and mitigating risks to critical operational processes, industrial systems, and connected devices based on their potential safety and business impact.
1. **Gain comprehensive visibility into OT and IoT assets**  
  Maintain an accurate inventory of devices, networks, and communication flows to understand what exists in the environment and identify unmanaged or vulnerable systems.
1. **Segment and protect OT/IoT environments**  
  Implement network segmentation and access controls to isolate critical systems, limit lateral movement, and reduce exposure to threats across IT and OT boundaries.
1. **Standardize monitoring and threat detection for OT/IoT**  
  Apply consistent monitoring and detection capabilities across connected devices and industrial systems to identify anomalies, unsafe conditions, and potential compromises.
1. **Align OT/IoT security with operational requirements and safety priorities**  
 Ensure that security controls support operational continuity and safety requirements, prioritizing protections for critical processes and minimizing disruptions to industrial operations.
1. **Continuously improve through insights and operational feedba**  
  Use learnings from incidents, device telemetry, and operational metrics to strengthen visibility, improve detection, and refine security controls over time.

## Manage change

OT and IoT Security modernization focuses on improving organizational ability to discover, monitor, and protect specialized OT/IoT devices that often aren't included in IT security efforts, controls, or scope. Unlike IT environments, most OT/IoT systems are long-live, safety-critical, and difficult to change.

Key change principles include:

- **Visibility**: Use passive monitoring to discover and understand OT/IoT assets and communications.
- **Isolation**: Segment and isolate OT environments to reduce exposure before applying other controls.
- **Operational safety**: Ensure security controls don't disrupt real‑time operations or safety systems.
- **Procurement**: Embed security requirements in purchasing decisions.
- **Alignment**: Make security sustainable by aligning people, processes, and technology. For example, train operations, update procedures, and consistently enforce controls. 
- 

## Modernization strategy

The OT/IoT security strategy combines near‑term risk reduction with long‑term structural improvements to reduce the likelihood and impact of cybersecurity incidents that could cause human harm, physical damage, or business disruption.

Unlike IT security, OT/IoT security has few viable security controls. Security strategy must acknowledge constraints, focus on consistently and effectively executing available on practical, sustainable controls without disrupting safety or availability.


## Strategic priorities

The unique OT/IoT security constraints require focusing on a small number of short-term and long-term strategic priorities:

- **Short Term - Monitor** - Use ***passive*** monitoring of network data to inventory devices and identify anomalous activities that may represent an attack. Note that *Actively* scanning for software vulnerabilities can cause some remote systems to crash, sometimes requiring a site visit to a distant or uninhabited remote location to physically restart the system. 
- **Short Term - Isolate** - Isolate OT and IoT devices from direct internet access and from other internet connected devices, including standard user IT devices and networks. 
- **Short Term - Other Controls _(as applicable)_** - Design and implement other controls that are available to secure the systems which may include physical isolation of highly sensitive systems, application of IT best practices such as software updates (if available), and more. 
- **Long Term - Purchase or Replace** - Procurement policy requires ability to secure devices for their full operational lifetime

The specific mix of controls will vary based on device types, operational constraints, and procurement cycles.

This diagram shows key priorities.

:::image type="content" source="./media/internet-of-things-challenges.png" alt-text="Shows strategic security strategies for OT/IoT security" lightbox="./media/internet-of-things-challenges.png":::

### Short-term - Isolate OT/IoT environments

Effective isolation requires more than just simple network segmentation with firewall rules to block traffic. Achieving effective isolation against threats that doesn't disrupt operations requires a comprehensive and thoughtful approach implemented consistently over time. 

The approach should include:

 - **Modeling business processes, technology, and threats**: Discover and document OT/IoT systems. How they're used in business workflows, how the technology is configured, and how threats actors might gain access. 
 - **Accounting for people, process, and technology** - Take a holistic approach. For example:

    - **For technology**, block unauthorized communications, detect threats, and establish rigorous security controls for all bridging/transit devices.
    - **For processes**, establish, monitor, and update organizational policy, business and technical procedures, and governance to sustain assurances over time.
    - **For people**, train all stakeholders on what, why, and how to execute procedures.

 - **Apply to all layers** - Don't restrict analysis, design, and implementation to only one control such as networking. Consider the whole system, including identities and access, network connectivity, physical access, operating systems, and apps.
 - **Secure transient devices** - Device access to isolated OT/IoT environments must be strongly secured to ensure the safety of fragile environments. Apply rigorous people, process, and technology controls to:
    - All devices that are permanently connected to the environment, such as monitoring workstations.
    - Devices that transit in or out, such as vendor maintenance laptops. Ensure you follow [privileged device principles](security-adoption-scenario-privileged-access.md). 

This diagram shows key points for isolating high value assets.

:::image type="content" source="./media/internet-of-things-isolation.png" alt-text="Key aspects of isolating high value assets" lightbox="./media/internet-of-things-isolation.png":::

### Long-term - purchase or replace

Ensure OT/IoT security and productivity increase over time by including their requirements in procurement policy. Without this step, OT/IoT operations costs and risks will grow over time.


The diagram compares the outcome with and without the inclusion of security requirements. 

:::image type="content" source="./media/internet-of-things-outcomes.png" alt-text="Compares security outcomes" lightbox="./media/internet-of-things-outcomes.png":::

- In **A**, the organization makes a large purchase without security requirements. The example shows a  support contract ending early, and a vendor closing down. This might incur unbudgeted support expenses, and elevated risk.  
- In **B** the organization includes security requirements during the procurement. Negotiation considers key factors that include:

    - The vendor provides lifetime updates, or provides more modern operating systems for equipment in order to close a deal.
    - The vendor provides lifetime support. Or at least are willing to extend regular support or provide a discount to close a deal.
    - The vendor must follow sound software development practices to reduce design flaws and risk early.
    - The vendor is subject to checks that estimate the ability of the vendor to provide continuity and stay in business.
    - Plans are in place in case the vendor goes out of business.


### Get value

Early evaluation of requirements helps you to maximize value from equipment and mitigate future risk. When you have this information early, it guards against:

- Vendor motivation to address security requirements post-purchase. 
- The need to negotiate updates and support at a later date, which might be more difficult or costly. 

Obviously, security requirements must be balanced with other business priorities and tradeoffs.

### Replacement

Be proactive in asking for updates, upgrades, and replacement systems and equipment.

- Don't assume that the cost of replacing a legacy system is always too expensive.
- Consider the business and security benefits or upgrade or replacement.
- Productivity gains from newer equipment might offset upgrade costs.
- Consider the hidden cost of legacy systems in terms of maintenance, business agility, and security risk and operational disruption. 
- Perform a full analysis of lifetime cost for legacy maintenance versus upgrade.


## Discipline roles and collaborators

OT and IoT security roles protect OT/IoT devices and systems. They ensure that security controls are implemented while maintaining operations and safety. In smaller organizations, these responsibilities might be combined into infrastructure or SecOps roles. Larger enterprises might have dedicated OT/IoT specialists.

Primary roles include:

- **Security architects** – Design secure architectures for OT environments, applying Zero Trust principles while respecting air-gap requirements and operational constraints.
- **OT engineering and operations** - Secure the industrial control systems (ICS), supervisory control and data acquisition (SCADA) environments, and the programmable logic controllers (PLCs) used to control and monitor physical processes. 

    These roles implement and manage security monitoring, network segmentation, and threat detection without disrupting business operations.

- **IoT professionals** - Integrate IoT devices and data into  business workflows, services, and custom applications. 

Key internal collaborators include:

- **Front line workers (Business operations and engineering teams)** – Maintain production systems and ensure that operational processes run smoothly. They integrate logging and telemetry into security incident and event management (SIEM) and security systems.
- **Front line workers (vendor management)** – Oversee third-party access to OT systems.
- **Infrastructure, platform, networking engineering/ops teams** – Coordinate network segmentation and connectivity between IT/OT environments.
- **SecOps** – Monitor OT/IoT threats and respond to incidents.
- **Security compliance management, compliance and audit team** – Ensure compliance with industry-specific regulations (NERC CIP, IEC 62443, NIST CSF).
- **CISO, security directors/managers** – Define strategic priorities, risk tolerance, and compliance objectives for OT/IoT security.

No role operates in isolation. Security professionals must understand cybersecurity principles ***and*** OT/IoT operational requirements.

Safety and availability often take precedence over traditional security controls in OT environments, requiring the balance of security with operational needs.

## Integration with other disciplines

OT and IoT security must integrate tightly with other disciplines:

- **Infrastructure security** – OT/IoT security is a specialized subset focused on industrial systems.
- **SecOps** – The SecOps team needs training, defined processes, and technology to detect and respond to OT/IoT attacks, avoiding blind spots.
- **Security posture management** - These teams must include IoT/OT devices into discovery and posture prioritization/mitigation efforts. This helps identify OT/IoT risk, including attack surfaces and potential access paths.

## Integration with technology pillars

Executing the strategy of the OT and IoT security discipline requires security controls across multiple technology pillars.

- **Identities**: Identity controls for OT/IoT environments must account for machine identities, service accounts used by automation systems, and human operators who require access to industrial controls.
- **Endpoints**: OT endpoints including industrial workstations, engineering stations, and operator terminals require specialized security to protect these specialized systems without impeding real-time operations.
- **Infrastructure**: OT infrastructure including industrial control systems, SCADA servers, industrial data historians, and PLCs require visibility and protection while maintaining operational requirements and air-gap architectures where appropriate.
- **Apps**: Applications that interface with OT/IoT devices must be secured to prevent unauthorized control of physical systems. This includes human-machine interfaces (HMI), SCADA applications, and industrial software.
- **Data**: Operational data from sensors, control systems, and industrial processes must be protected both at rest and in transit, while maintaining the integrity critical for safe operations.
- **Networks**: Network segmentation between IT and OT environments is critical, along with monitoring of industrial protocols (Modbus, OPC, DNP3) and secure remote access for vendors and operators.
- **AI**: AI and machine learning can enhance OT security through anomaly detection in industrial processes, predictive maintenance, and automated threat identification while respecting operational constraints.


## Microsoft resources


### Technologies

Microsoft offers technology solutions that enable and accelerate modernization of OT and IoT security.

This includes both primary enablement technology and key enabling technologies. 

**Technology** | **Details**
--- | ---
[**Microsoft Defender for Endpoint**](/defender-for-iot/enterprise-iot) | Enterprise IoT in the Microsoft Defender portal provides support for Enterprise IoT security. [Review license information for Defender for Endpoint and Defender XDR](/defender-xdr/protect-against-iot-ot-threats#enterprise-iot-device-protection-in-defender-for-endpoint-and-defender-xdr).
[**Microsoft Entra**](/entra/fundamentals/whatis) | Provides identity management for OT operators, engineers, and service accounts accessing industrial systems.
[**Microsoft Intune**](/intune/intune-service/fundamentals/what-is-intune) | Secures OT workstations and engineering stations used to manage industrial systems.
[**Microsoft Defender XDR**](/defender-xdr/microsoft-365-defender) | Provides detection and response capabilities for OT workstations and IT systems connected to operational environments (via Microsoft Defender for IoT).
[**Microsoft Sentinel**](/azure/sentinel/overview) | A SIEM solution that correlates OT security alerts with IT security events for comprehensive threat detection.
**Microsoft Azure** | Provides secure cloud infrastructure for OT data analytics, remote monitoring, and secure connectivity including [Azure IoT Hub](/azure/iot-hub/about-iot-hub), [Azure Firewall](/azure/firewall/overview), and [Azure Private Link](/azure/private-link/private-link-overview),
[**Microsoft Azure Sphere**](/azure-sphere/product-overview/what-is-azure-sphere) | Provides a comprehensive IoT solution that provides a secured, connected microcontroller unit (MCU), a custom Linux-based OS, and a cloud-based security service.

## Next steps

[Learn about the infrastructure and networking discipline](security-adoption-discipline-infrastructure.md).