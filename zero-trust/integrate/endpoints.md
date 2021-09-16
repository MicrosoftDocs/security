---
title: Endpoint Zero Trust integration overview
description: Independent software vendors (ISVs) can integrate their solutions with Microsoft Defender for Endpoint and Microsoft Endpoint Manager to help customers adopt a Zero Trust model and keep their organizations secure.
ms.date: 09/17/2021
ms.service: security
author: knicholasa
ms.author: nichola
ms.topic: conceptual
---

# Endpoint integrations

:::image type="icon" source="../media/icon-endpoints-medium.png":::

Endpoints are devices that access an organization's resources and applications. Modern workplaces include a variety of devices that request access from both inside and outside the corporate network.

Endpoint Zero Trust solutions are about verifying the security of the devices that access work data, including the applications that are running on the devices. Partners can integrate with Microsoft's endpoint solutions to verify device and app security, enforce least privileged policies, and prepare in advance for breaches.

This guidance is for software providers and technology partners who want to enhance their endpoint security solutions by integrating with Microsoft products.

## Endpoint Zero Trust integration guide

This integration guide includes instructions for integrating with the following products:

- [Microsoft Defender for Endpoint](#microsoft-defender-for-endpoint), which helps enterprise networks prevent, detect, investigate, and respond to advanced threats.
- [Microsoft Endpoint Manager](#microsoft-endpoint-manager), which provides protection and security for the devices that employees use and the applications that run on those devices.

### Microsoft Defender for Endpoint

[Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint) is an enterprise endpoint security platform designed to help enterprise networks prevent, detect, investigate, and respond to advanced threats. It uses a combination of endpoint behavioral sensors, cloud security analytics, and threat intelligence.

Defender for Endpoint [supports third-party applications](/microsoft-365/security/defender-endpoint/partner-applications) to help enhance the detection, investigation, and threat intelligence capabilities of the platform. In addition, partners can [extend their existing security offerings](/microsoft-365/security/defender-endpoint/partner-integration) on top of the open framework and a rich and complete set of APIs to build extensions and integrations with Defender for Endpoint.

The [Microsoft Defender for Endpoint partner opportunities and scenarios](/microsoft-365/security/defender-endpoint/partner-integration) page describes several categories of integrations that are supported. In addition, other ideas for integration scenarios can include:

- Streamlining threat remediation: Microsoft Defender for Endpoint can take immediate or operator-assisted responses to address alerts. Partners can leverage the endpoint response actions such as machine isolation, file quarantine to block IoC across the managed endpoint.
- Combine network access control with device security: Risk or exposure scores can be used  to implement and enforce policies for network and application access.

To become a Defender for Endpoint solution partner, you'll need to follow and complete the  steps found at Become a [Microsoft Defender for Endpoint partner](/microsoft-365/security/defender-endpoint/get-started-partner-integration).

### Microsoft Endpoint Manager

Microsoft Endpoint Manager, which includes Microsoft Intune and Microsoft Configuration Manager, provides protection and security for the devices that employees use and the applications that run on those devices. Endpoint Manager includes device compliance policies that ensure employees are accessing applications and data from devices that meet company security policies. It also includes application protection policies which provide application based security controls for both fully managed and employee-owned devices.

To integrate with Microsoft Endpoint Manager, ISVs will use Microsoft Graph and the Microsoft Endpoint Manager application management SDK. Endpoint Manager’s integration with the Graph API allows any of the same functionality offered by the administrator console for Endpoint Manager (Intune). Information such as device compliance state, compliance policy configuration, application protection policy settings and more can be found through the Graph API. Additionally, you can automate tasks in Endpoint Manager that further enhance your customer’s Zero Trust story. General guidance for [Working with Intune in Microsoft Graph](/graph/api/resources/intune-graph-overview) is available in the Microsoft Graph documentation repo. Here, we focus on scenarios related to Zero Trust.

:::image type="content" source="../media/integrate/endpoints/microsoft-365-platform.png" alt-text="Microsoft Graph, Microsoft Graph data connect, and Microsoft Graph connectors enable extending Microsoft 365 experiences and building intelligent apps.":::

#### Verify devices follow security and compliance standards

ISV solutions can leverage Endpoint Manager’s device compliance and policy information to support the Zero Trust principle of Verify Explicitly. The compliance data about users and devices from Endpoint Manager allows the ISV's application to determine a device's risk posture as it relates to use of the application. By doing these verifications, the ISV ensures that devices using the service are compliant with the customers’ security and compliance standards and policies.

The Microsoft Graph API allows ISVs to integrate with Endpoint Manager (Intune) through a set of RESTful APIs. These APIs are the same ones used by the Endpoint Manager console to view, create, manage, deploy, and report on all actions, data and activity in Intune. Items of specific interest for ISVs supporting Zero Trust initiatives are the ability to view device compliance state and configure compliance rules and policies. See Microsoft’s Zero Trust recommendations for using Azure AD and Endpoint Manager for Zero Trust configuration and compliance: [Secure endpoints with Zero Trust](/security/zero-trust/endpoints). Endpoint Manager’s compliance rules are foundational for device based Conditional Access support through Azure Active Directory. ISVs should also view the Conditional Access feature and APIs to understand how to complete scenarios for user and device compliance and Conditional Access.

Ideally as an ISV, your application connects to the Microsoft Graph APIs as a cloud application and establishes a service-to-service connection. Multi-tenant applications provide ISVs with centralized application definition and control and enable customers to individually consent to the ISV application operating against their tenant data. Review the information on [Tenancy in Azure Active Directory](/azure/active-directory/develop/single-and-multi-tenant-apps) for registering and creating single or multi-tenant Azure AD Applications. Your application’s authentication can leverage Azure AD for single sign on.

After creating your application, you will need to access the device and compliance information using the Microsoft Graph API. Documentation for using Microsoft Graph can be found at the [Microsoft Graph dev center](https://developer.microsoft.com/graph/). The Graph API is a RESTful set of APIs that follow ODATA standards for data access and querying.

#### Getting Device compliance state

:::image type="content" source="../media/integrate/endpoints/device-compliance-data-flow.png" alt-text="Visualization of the data flow checking if a device is compliant. End user devices feed threat info to a mobile threat defense partner. The devices also provide compliance policy state to Intune and an mobile device management partners. Next, the mobile threat defence partner supplies a risk assessment to the Intune cloud service. Intune and the mobile device management partner provide compliance status to the same service. Finally, the Intune cloud service provides a calculated compliance state to Azure Active Directory, which then supplies a device compliance status via the Microsoft Graph API to the ISV's solution.":::

This diagram shows how device compliance information flows from the device to your ISV solution. End user devices receive policies from Intune, a mobile threat defense (MTD) partner, or an mobile device management (MDM) compliance partner. Once the compliance information is gathered from the devices, Intune calculates the overall compliance state of each device and stores that in Azure AD. By using the Microsoft Graph API, your solution can read and respond to the device compliance state, applying the principles of Zero Trust.

When enrolled with Intune, a device record is created in Intune with additional device details, including the device compliance state. Intune forwards the device compliance state to Azure AD, where Azure AD also stores the compliance state with each device. By making a GET on https://graph.microsoft.com/v1.0/deviceManagement/managedDevices you can see all the enrolled devices for a tenant and their compliance state. Or you can query https://graph.microsoft.com/v1.0/devices to get a list of the Azure AD registered and enrolled devices and their compliance state.

For example, this request:

```http
GET https://graph.microsoft.com/v1.0/users/{usersId}/managedDevices/{managedDeviceId} 
```

Will return:

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 5095

{
 "value": {
  "@odata.type": "#microsoft.graph.managedDevice",
  "id": "705c034c-034c-705c-4c03-5c704c035c70",
  "userId": "User Id value",
  "deviceName": "Device Name value",
  "managedDeviceOwnerType": "company",
  "enrolledDateTime": "2016-12-31T23:59:43.797191-08:00",
  "lastSyncDateTime": "2017-01-01T00:02:49.3205976-08:00",
  "complianceState": "compliant",
…
}
```

You can also retrieve a list of compliance policies, their deployments, and status of users and devices for those compliance policies. Information for calling Graph to get compliance policy information starts here: [Get deviceCompliancePolicy - Microsoft Graph v1.0](/graph/api/intune-deviceconfig-devicecompliancepolicy-get). A good background on device compliance policies and how they are used is here: [Device compliance policies in Microsoft Intune - Azure](/mem/intune/protect/device-compliance-get-started).

Once you have identified a specific policy, you can query to get the state of a device for a particular compliance policy setting. For example, assuming a compliance policy was deployed to require a passcode on lock, query [Get deviceComplianceSettingState](/graph/api/intune-deviceconfig-devicecompliancesettingstate-get) for the specific state of that setting. This indicates whether the device is compliant or non-compliant with the passcode lock setting. This same approach can be used for other device compliance policies that customers have deployed.

Compliance information is foundational to Azure AD’s Conditional Access feature. Intune determines the device compliance based on compliance policies and writes the compliance state to Azure AD. Then, customers use Conditional Access policies to determine whether any actions are taken for non-compliance, including blocking the users from accessing corporate data from a non-compliant device.

See [Device compliance policies in Microsoft Intune](/mem/intune/protect/device-compliance-get-started#integrate-with-conditional-access) for additional information about integrating device compliance with conditional access.

#### Follow the least privilege access principle

An ISV integrating with Endpoint Manager will also want to ensure their application supports the Zero Trust principle to Apply Least Privileged Access. Endpoint Manager integration supports two important methods of access control – delegated permissions or application permissions. The ISV's application must use one of the permission models. Delegated permissions give you fine grained control over the specific objects in Endpoint Manager the application has access to but requires that an administrator log in with their credentials.  By comparison, application permissions allow the ISV's app to access or control classes of data and objects, rather than specific individual objects, but does not require a user to log in.

In addition to creating your application as a single-tenant or multi-tenant (preferred) application, you must declare the delegated or application permissions required by your application to access Endpoint Manager information and perform actions against Endpoint Manager. View information about getting started with permissions here: [Quickstart: Configure an app to access a web API](/azure/active-directory/develop/quickstart-configure-app-access-web-apis).

## Next steps

- [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint)
- [Microsoft Endpoint Manager](/mem/)