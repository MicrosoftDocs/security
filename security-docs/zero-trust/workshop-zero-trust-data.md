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

In a Zero Trust framework, data is critical. It isn’t enough just to protect the perimeter or infrastructure. You need to know what data you have, where it lives, how sensitive it is, and how it’s used. The Data pillar is about classifying, discovering, protecting, and governing your data to reduce risk, enforce least privilege, and continuously monitor for risky behaviors.

Identity pillar Workshop guidance focuses on understanding your data estate and which data is sensitive, organizing your data policies, deploying data loss prevention (DLP) and insider risk controls, monitoring data sharing, and apply strong controls for critical data. The Data workshop covers these implementation areas:

- **Discover and classify sensitive data**: Use sensitive data discovery to identify where sensitive documents, emails, and other data reside. Leverage classifiers (trainable, fingerprinting, exact data match) to detect data based on content and pattern.
- **Define a data classification taxonomy**: Establish a labeling taxonomy (e.g., internal, confidential, highly confidential) that aligns with your business sensitivity model. Ensure the taxonomy is simple, understandable, and stable over time. 
- **Apply labels and protect data**: Implement sensitivity labels (manual or automatic) to your data assets. Set data protection policies and enforce DLP to prevent data exfiltration or inappropriate access.
- **Monitor data sharing**: Track external sharing of sensitive data with partners and customers.Implement continuous monitoring of sharing channels and enforce restrictions where needed.
- **Manage insider risk**: Define insider risk management policies to detect risky user behavior on data: data exfiltration, over-permission, or unusual access patterns. Identify and protect critical assets (e.g., IP, financial data) with higher-level controls or cryptographic isolation.
- **Control admin access to data**: Apply role-based access control (RBAC) for data/label administrators, ensuring that only appropriate personnel can manage DLP or information protection settings. Use administrative segmentation (e.g., using administrative units) to isolate sensitive data admin roles.

## Assess data posture**

The Zero Trust Assessment tool  can assess your data configuration against a range of security best practices. [Learn more](/security/zero-trust/assessment/overview).