# Secure Hybrid Access Integrations for ISVs

Modern authentication protocols are designed to keep applications secure in a highly connected, cloud-based world. However, many business-critical applications were built before this move to the cloud. Their methods of authentication and authorization were not built to work outside of a protected corporate network. Companies need solutions that provide modern authentication for these applications with legacy protocols to continue using them securely in the modern workplace.

In this article we show you how you can create a solution that integrates legacy applications with Azure Active Directory, creating a modern authentication solution to help achieve Zero Trust. This will be useful if you are creating a solution for your own company, or to sell to others.

# Solution Overview

There are two key components that help a company integrate legacy applications with a modern identity provider like Azure Active Directory. First, enabling discovery of applications that are using legacy authentication methods. Second, creating an easy workflow for integrating these applications with Azure Active Directory.

When you're creating the solution for integrating applications with Azure Active Directory, you should consider two categories of apps. Apps that use SAML, OpenID Connect, or authentication protocols that work with Azure AD Application Proxy are directly supported by Azure Active Directory. Integrating them simply involves registering them in Azure Active Directory and configuring the application so that it uses Azure Active Directory as its identity provider. Other protocols, like SSH, LDAP, and NTLM require you to implement an additional layer that connects the legacy authentication to Azure Active Directory in a way that it supports. You can create a programmatic solution to connect either or both types of apps with Azure Active Directory.

# Key components

This section outlines the key pieces of the solution and provides guidance on how to implement them.

## Publish your app to the Azure AD app gallery

Whether you are adding the legacy app integration functionality to an existing application or creating a new solution, you should make sure that the resulting application is published to the Azure AD app gallery.

The solution you are creating will require the permission to view potentially all the applications in the user's tenant, so users need to know they can trust your app. When you publish your app in the app gallery this will increase customer trust. Customers know that your application has been validated to be compatible with Azure Active Directory, and you can become a [verified publisher](https://docs.microsoft.com/azure/active-directory/develop/publisher-verification-overview) by certifying yourself as a trusted developer with the Microsoft Partner Network.

In addition, publishing in the app gallery will make it easy for IT admins to integrate the solution into their tenant with automated app registration. Manual registrations are a common cause of support issues with Azure Active Directory. Adding your app to the gallery will help allay these issues with your app.

## Implement application discovery

You can save the customer time and provide valuable insight by providing a tool for them to see the various authentication protocols and identity providers that are currently in use at their company. This allows them to make informed decisions about the applications they want to integrate with Azure AD. You can also use this tool as the jumping off point for single-click integrations of these legacy applications to Azure AD.

An example solution is Microsoft's tool for migrating AD FS apps to Azure Active Directory: [Use the activity report to move AD FS apps to Azure Active Directory | Microsoft Docs](https://docs.microsoft.com/azure/active-directory/manage-apps/migrate-adfs-application-activity). Foo and Bar have also implemented solutions, which you can see in the highlighted partners section below.

## Implement programmatic app integration

The core feature your solution is offering is the programmatic integration of applications to Azure Active Directory. When you are implementing this feature, there are three categories of apps to consider, which are discussed separately below.

### Apps available in the App Gallery

Some of the applications your customer is using will already be available in the [Azure Active Directory Application Gallery](https://azuremarketplace.microsoft.com/marketplace/apps). The gallery includes thousands of SaaS applications that are already integrated with Azure Active Directory. Applications in the gallery can be easily added to a tenant by IT Admins from the Azure Portal. However, you can also create a solution that programmatically adds these applications.

The following tutorial provides an example of how you can use Microsoft Graph APIs to search for and register gallery apps. [Automate SAML-based SSO app configuration using MS Graph API SDK .NET - Code Samples | Microsoft Docs](https://docs.microsoft.com/samples/azure-samples/ms-identity-dotnetcore-galleryapp-management/automate-saml-based-sso-app-configuration-using-ms-graph-api-sdk-net/)

### Apps not in the gallery that use modern or App-Proxy-supported protocols

Another category of application will be applications that are not already available in the application gallery, but make use of either modern authentication protocols, or protocols that are supported by [Azure AD App Proxy](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).

In this case you will use API to register with Azure AD tenant directly. If App Proxy needs to be used, the customer using your application will need a P1 or P2 license.

You can use this for guidance on programmatically setting up App Proxy: [Configure Application Proxy using Microsoft Graph APIs - Microsoft Graph | Microsoft Docs](https://docs.microsoft.com/graph/application-proxy-configure-api)

To create and register an app not in the gallery, you can follow [this tutorial](https://docs.microsoft.com/graph/application-saml-sso-configure-api), but with the following request instead up using the app ID retrieved from the gallery:

```https
POST https://graph.microsoft.com/beta/applicationTemplates/8b1025e4-1dd2-430b-a150-2ef79cd700f5/instantiate
Content-type: application/json

{
    "displayName": "AWS Contoso"
}
```

### Apps that are not directly supported by Azure Active Directory

Your solution can work together with Azure Active Directory to get the benefits of Single-Sign On and other Azure Active Directory features even for applications that are not generally supported. To do so, Azure AD will call your application to authenticate incoming requests from the legacy application. This is sometimes called &quot;preauthentication&quot;.

This section feels light and I wonder if we have anything else we can add or point them to.

# Further recommendations

After discovering and integrating applications, there are some useful next steps your users will want to take.

## Leverage Azure AD App Roles for authorization

Once the user has migrated their applications, they will want to make sure that the permissions to access these applications are set correctly.

## Publish the application to the Azre AD My Apps portal

IT admins that make use of your solution will want the resulting applications to be discoverable for the users in their tenant. To this end, you should encourage customers to publish apps to the My Apps portal, and fill in the app descriptions and icons. You should provide guidance to your customers on how they can add this information to the imported apps. Without it, the applications that use your solutions to connect to Azure AD may use the icon and name of your solution, which could cause confusion with users in their tenant.

## Apply Conditional Access Policies to the application

[Conditional Access](https://docs.microsoft.com/azure/active-directory/conditional-access/overview) is a key offering from Azure Active Directory. Conditional Access policies allow organizations to apply the right access controls when needed to stay secure, for example by blocking risky sign-ins.

You can set up conditional access in the applications you have migrated for your customers programmatically. For more, check out this sample on GitHub [Configure Conditional Access policies using the Microsoft Graph API](https://github.com/Azure-Samples/azure-ad-conditional-access-apis/tree/main/01-configure/graphapi).

# Highlighted partners

Some text explaining how these partners work with us.

List of partners:

- Foo
- Bar
- Baz