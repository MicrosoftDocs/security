---
title: Building identity solutions for Zero Trust
description: Building identity solutions for Zero Trust
ms.date: 04/20/2021
ms.service: security
author: knicholasa
ms.author: nichola
ms.topic: conceptual
---

# Building identity solutions for Zero Trust

:::image type="icon" source="../media/icon-identity-medium.png":::

The modern workplace has changed. Applications are moving into the cloud and employees need to work from home on their own devices and collaborate with partners who are outside of their organization. With these changes, companies can no longer rely on traditional network security solutions. Controls need to move to where the data is: on devices, inside apps, and with partners.

Businesses want to support this new reality but creating the proper solutions takes time and technical know-how. This is where ISVs can help. ISVs can create solutions that bridge the gap between traditional on-premise network security and a modern, cloud-based Zero Trust security architecture.

## Azure AD integrations that strengthen identity solutions

Identities represent people, services, and devices and the permissions that they obtain to access your data. Identities are the key control plane for managing access in the modern, interconnected, and increasingly cloud-based modern workplace.

Azure Active Directory is Microsoft’s cloud enterprise identity service. It provides features such as single sign-on, conditional access, passwordless and multi-factor authentication, and many more features that enable companies to protect and automate identity processes at scale. As an ISV, you can integrate many of these features into your own applications by using APIs available via Microsoft Graph. You can also gain access to the risk signals Azure AD calculates based on myriad data sources and policies, and feed your own information back into the system to create a safer environment for all.

:::image type="content" source="../media/diagram-conditional-access-policies-small.png" alt-text="Diagram of conditional access, showing machine learning, policies, and a real time evaluation engine making decisions about how to allow access." lightbox="../media/diagram-conditional-access-policies-white-background.png":::

In addition to the Graph API, there are other ways to provide value on top of Azure AD - such as publishing your app to the Azure AD gallery or becoming an approved passwordless hardware vendor.

## Integration guidance

We have included the following guidance to help you on the journey to integrating your solutions with Azure AD. We have also included examples of existing partnerships that have allowed Microsoft and strategic partners to build strong solutions together.

<br/>
<table border="0">
   <tbody>
      <tr>
         <td>
            <p><strong><a>Cloud security integrations</a href="cloud-security.md"></strong> </p>
            <p>How to get started integrating with Azure AD.</p>
         </td>
      </tr>
      <tr>
         <td>
            <p><strong><a>Secure Hybrid Access</a href="legacy-apps.md"></strong> </p>
            <p>Creating solutions that connect apps using legacy authentication methods with the cloud.</p>
         </td>
      </tr>
      <tr>
         <td>
            <p><strong><a>Becoming a FIDO2 Partner</a href="fido2-hardware-vendor.md"></strong> </p>
            <p>How to partner with Microsoft to offer passwordless hardware devices compatible with Azure AD.</p>
         </td>
      </tr>
      <tr>
         <td>
            <p><strong><a>Privileged Access Management</a href="privileged-access.md"></strong> </p>
            <p>Integration suggestions for providers of Privileged Access Management (PAM) solutions.</p>
         </td>
      </tr>
    </tbody>
</table>
