---
title: Common security antipatterns
description: 

ms.service: security

ms.topic: overview
ms.date: 04/26/2024

ms.author: joflore
author: MicrosoftGuyJFlo
manager: amycolannino
ms.reviewer: mas
---
# Common security antipatterns

Antipatterns are a common response to a recurring problem that is usually ineffective or counterproductive. These antipatterns (common mistakes) often impede security effectiveness and increase organizational risk. 

These are some of the common ones we see regularly.

:::image type="content" source="media/antipatterns/antipatterns.png" alt-text="Diagram showing common antipatterns in security along with best practices." lightbox="media/antipatterns/antipatterns.png":::

Use this list as a way to perform a (look back at yourself Mirror? Retrospective?) **blameless postmortem** analysis to help avoid common mistakes in security architecture and technical strategy in your own organization.

The SAF and our technical documentation help you overcome these antipatterns. We understand that many orgs have security debt becuase of a Good/fast/cheap? You pick two. Our guidance helps both new and existing organizations overcome this debt 

## Commonly seen mistakes include:

### Skipping basic maintenance

Organizations often designed and deployed most technical systems and processes long before security was a priority. This led to a habit of skipping security in favor of other requirements (availability, speed, cost, etc.), leading to neglect of basic security requirements like backups and disaster recovery planning/exercises, software updates/patching on assets, security configuration baselines.

Good/fast/cheap? You pick two.

This happens across resource types from PCs and servers to network devices (and even security appliances!)

This might take the form of skipping it entirely or only partially applying basic maintenance. For example, systems may be isolated with a firewall, but little or no action is taken to apply available patches/updates, monitor systems for attacks, update acquisition processes to ensure new systems are more secure, and so on. 

### Securing cloud like on premises

The first instinct of many security teams is to attempt to force on-premises controls and practices directly onto cloud resources. This doesn’t work well because the underlying architecture and operating model of cloud services is fundamentally different (virtual storage and compute resources instead of physical servers, shared responsibility model, and so on). 

Many of the same principles and types of controls are required for cloud, but they must be applied differently for an effective security approach. 

It’s critical for security and technology teams to **work together to update processes and technology** to secure cloud using effective and efficient approaches (described throughout the security adoption framework)

### Wasting resources on legacy

Organizations often waste resources attempting to secure legacy systems that are fundamentally indefensible. While these save money in the short term by avoiding the cost of change, they come with large negative impacts to both security and organizational productivity resulting from system downtime after security attacks and lack of organizational agility to meet changing business needs.

#### Increased incidents on Indefensible/Unsecurable systems

Many legacy systems have limited processing/storage/memory and/or run outdated software that can’t be secured with modern effective approaches. 

Many of these systems rely on outdated standards/technologies (cryptography, protocols, etc.) that are not considered safe today because attackers can quickly compromise them with freely available tooling. This often leaves security teams with zero good options for protecting them often requiring security to fall back on network isolation or archaic defensive approaches that force ugly choices between security vs. business processes and which are expensive/difficult to implement and maintain consistently over time, resulting in higher volume and impact of damaging security incidents. 

#### Increased security cost / decreased security resources 

- The hidden costs of maintaining and securing these systems often drain the ability of the organization to support and secure other systems, leaving the organization exposed to increase risk of more incidents with greater negative business impact. 

#### Missed business opportunities

Legacy systems often lack the modern features organizations need to support an agile digital business that can keep up with continuously changing customer and market demands, hurting the business’ ability to grow or protect revenue streams.

These impacts increase over time as attackers become more effective and efficient at compromising these legacy systems.

- Make decisions intentionally - It’s critical analyze whether its better to maintain and secure those systems (at a higher operational expense level) or to invest in updating them to more productive, agile, and secure modern systems. 
- While keeping an old system running appears financially sound at first glance, the reality is that hidden costs of outdated systems can often be a black hole that eats money, time, and business opportunities slowly (or in big increments with large security incidents like ransomware attacks)

### Disconnected security approach

Security and IT teams often operate independently with fragmented strategies, technology, and processes. 

This independence often leads to confusion and conflict when trying to accomplish security goals. Attackers freely traverse between network, identity, devices, and other resources while defenders struggle to protect, detect, and respond across these independent systems. 

Examples include:

- A successful Windows Hello for Business (WHFB) deployment needs the Identity and Access team to work closely with the Devices/Endpoint team. 
- A successful Microsoft 365 deployment requires the Identity and Access team to work closely with the Collaboration team. 
- Detecting and responding to attacks require integrating logs and other signals from all technical assets (devices, networks, servers, etc.) and team cooperation across all those teams to rapidly clean those up before ransomware actors can extort the organization

**Security is a team sport** across security, technology, and business teams / Integration of organizational Functions and Teams (including use cases and scenarios)

### Artisan Security

Security teams often favor building and customizing tools rather than taking a practical approach of **configure before customize**.

This is because many security professionals started their careers when security tools maturity was very low and custom tools were the only option for solving many challenges. Recent years have seen massively improved maturity for vendor provided capabilities, so it’s critical to shift to a preference of using *off the shelf* tooling when available. Security problems have outgrown the ability of people to manually handle them, so it’s critical to embrace security automation for and integrate security into IT and developer/DevOps automation. 

### Lack of commitment to lifecycle

Organizations often treat security controls and processes as a single point in time, instead of part of an ongoing lifecycle. Like anything else in business or technology, security investments must be operationalized, maintained, and supported to sustain effects over time. 

Some examples of common mistakes include: 

- Acquiring tools without a clear understanding of how they will integrate with existing capabilities and processes.
- Implementing controls with an (implicit) belief that they will permanently block attacks effectively without testing or monitoring them to ensure they are effective.
- Considering how attackers may work around them or what attackers will try next
- Granting security permissions once without evaluating or monitoring what permissions are granted, when people leave roles (or the organization), etc. 
- Focusing data protection solely on the moment data leaves the network (with DLP technology) instead of identifying and protecting sensitive data throughout its lifecycle

It’s critical to assume failure and to take a full lifecycle view of security controls and a full lifecycle view of the data and technical systems they are protecting. 

## Best practices

Develop and implement an end to end technical security strategy focused on durable capabilities and Zero Trust Principles

1. **Asset-centric security** aligned to business priorities & technical estate (beyond network perimeter)
1. **Consistent principle-driven approach** throughout security lifecycle
1. **Pragmatic prioritization** based on attacker motivations, behavior, and return on investment 
1. **Balance investments** between innovation and rigorous application of security maintenance/hygiene
1. **Configure before customize** approach that embraces automation, innovation, and continuous improvement
1. **Security is a team sport** across security, technology, and business teams

The [Security Adoption Framework (SAF)](adoption.md) illustrates how to apply these best practices in design and daily operations. 

## Related content

- [Microsoft Cybersecurity Reference Architectures](mcra.md)
- [The immutable laws of security](../zero-trust/ten-laws-of-security.md)