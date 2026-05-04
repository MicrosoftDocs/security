---
title: Microsoft Zero Trust Workshop - Data
description: Learn about the Data pillar in the Microsoft Zero Trust Workshop
ms.date: 04/18/2024
ms.service: security
author: rayne-wiselman
ms.author: raynew
ms.subservice: zero-trust
ms.topic: conceptual
---

# Data security in the Microsoft Zero Trust Workshop

In a Zero Trust framework, data is a critical security boundary. Protecting infrastructure or identities alone is not sufficient—organizations must understand what data they have, where it resides, how sensitive it is, and how it is accessed and used. The Data pillar focuses on discovering, classifying, protecting, and governing data to reduce risk, enforce least privilege, and monitor for inappropriate use.

Data pillar workshop guidance focuses on understanding the data estate, defining classification and protection policies, enforcing controls on data usage and sharing, and monitoring for data risks across users, endpoints, and applications.

The Data workshop covers the following implementation areas:

- **Discover and classify sensitive data**  
  Identify and inventory sensitive data across locations such as Microsoft 365, endpoints, and other connected data sources. Use built-in and trainable classifiers (including exact data match and fingerprinting) to detect sensitive information based on content and patterns.
- **Define and standardize a data classification taxonomy**  
  Establish a sensitivity labeling taxonomy (for example, internal, confidential, and highly confidential) aligned with business requirements. Ensure labeling definitions are clear, enforceable, and consistently applied across workloads.
- **Gain visibility into data usage and activity**  
  Understand how data is accessed, used, and shared across the organization. Use activity monitoring and data exploration tools to assess current behaviors and identify risks before enforcing policies.
- **Apply labels and enforce data protection policies**  
  Implement sensitivity labels (manual and automatic) to protect data through encryption, access restrictions, and usage controls. Apply protection consistently across data at rest, in motion, and in use.
- **Enforce data access and usage controls**  
  Apply policy-based controls that govern how protected data can be accessed and used based on identity, device, location, and session context. Use conditional access for apps, session controls, and app-based protections to enforce Zero Trust access decisions for data.
- **Monitor and control data sharing and collaboration**  
  Track and control external and internal sharing of sensitive data. Implement policies to govern collaboration with partners and external users, and enforce restrictions on risky sharing behaviors across services such as SharePoint, OneDrive, and Teams.
- **Protect data across endpoints and devices**  
  Extend data protection policies to endpoints by integrating labeling and DLP with device and application controls. Ensure sensitive data remains protected when accessed, copied, or moved across managed and unmanaged devices.
- **Manage insider risk and sensitive data exposure**  
  Detect and respond to risky user activities involving data, such as exfiltration, misuse, or unusual access patterns. Correlate signals across data, identity, and endpoints, and apply enhanced protections to high-value data assets.
- **Manage data governance and administrative control**  
  Apply role-based access control (RBAC) and administrative segmentation for data protection, labeling, and compliance roles. Ensure separation of duties so that only authorized personnel can define, manage, and operate data security policies.
- **Integrate data signals into security operations (SecOps)**  
  Use data-related alerts, DLP events, and insider risk signals as part of broader security monitoring and incident response. Correlate data activity with identity and device signals to detect, investigate, and respond to threats.

## Assess data posture

The Zero Trust Assessment tool  can assess your data configuration against a range of security best practices. [Learn more](/security/zero-trust/assessment/overview).


## What's next?

[Run an assessment](assessment/get-started.md), and begin the [Data workshop](https://zerotrust.microsoft.com/).