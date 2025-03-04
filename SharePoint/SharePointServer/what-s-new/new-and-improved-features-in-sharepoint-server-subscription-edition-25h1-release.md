---
ms.date: 04/02/2025
title: "New and improved features in SharePoint Server Subscription Edition Version 25H1"
ms.reviewer: 
ms.author: 
author: 
manager:
audience: ITPro
f1.keywords:
- NOCSH
ms.topic: overview
ms.service: sharepoint-server-itpro
ms.localizationpriority: high
ms.collection:
- IT_Sharepoint_Server
- IT_Sharepoint_Server_Top
- Strat_SP_server
ms.custom: 
description: "Learn about the new features and updates to existing features in SharePoint Server Subscription Edition Version 25H1."
---

# New and improved features in SharePoint Server Subscription Edition Version 25H1

[!INCLUDE[appliesto-xxx-xxx-xxx-SUB-xxx-md](../includes/appliesto-xxx-xxx-xxx-SUB-xxx-md.md)]

Learn about the new features and updates introduced in the SharePoint Server Subscription Edition Version 25H1 feature update. 

## Summary of the features

The following table provides a summary of the new features introduced in the SharePoint Server Subscription Edition Version 25H1 feature update.

|**Feature**|**Release ring**|**More information**|
|:-----|:-----|:-----|
| **Support RSA public key in OIDC authentication configuration**   |Standard release   |For more information, see [Set up OIDC authentication in SharePoint Server using RSA public keys](../security-for-sharepoint-server/set-up-oidc-auth-in-sharepoint-server-using-rsa.md).<p> This was part of Early release in the Version 24H2 feature update.|
|  **Support for automatic machine key rotation**  |  Early release   | For more information, see xxx.|
|  **Dynamic customer survey by One Customer Voice**  | Early release  | For more information, see xxx |
| **Create new Office files in client apps**   |Early release   |For more information, see xxx.|
| **Support for request body scan in AMSI**   |Early release   |For more information, see xxx.|
| **Cloud Hybrid Search upgrade**   |Early release   |For more information, see xxx.|
| **New database connectivity layer with TLS 1.3 and TDS 8.0 support**   |Standard release   |For more information, see xxx.|

## Detailed description of features

This section provides detailed descriptions of the new and updated features in SharePoint Server Subscription Edition Version 25H1.

> [!NOTE]
> Features previously introduced in the Version 24H2 feature update will not be described here. For more information on Version 24H1, see [New and improved features in SharePoint Server Subscription Edition Version 24H2](new-and-improved-features-in-sharepoint-server-subscription-edition-24h2-release.md). 

### Support RSA public key in OIDC authentication configuration

OIDC is an authentication protocol that uses JSON Web Tokens (JWTs) to verify the identity of users, and grant them access to protected resources. JWTs are digitally signed using either symmetric keys (shared between the issuer and the consumer) or asymmetric keys (public/private key pairs).

Some OIDC providers use RSA public keys that are directly represented with RSA modulus and RSA public exponent. To support these providers, SharePoint Server Subscription Edition Version 24H2 now gives the ability to parse and validate RSA public keys in JWTs. 

For more information, see [Set up OIDC authentication in SharePoint Server using RSA public keys](../security-for-sharepoint-server/set-up-oidc-auth-in-sharepoint-server-using-rsa.md) .

### Support for automatic machine key rotation

The objective of Automatic machine key rotation is to enhance security by regularly updating machine keys without manual intervention, thereby reducing the risk of key compromise. This feature ensures seamless and automatic rotation of machine keys while maintaining high availability and reliability of SharePoint services during key rotation.

The feature incorporates a Key Management Service that handles storage, retrieval and distribution of machine keys using a timer job called Machine Key Rotation Job.

### Dynamic customer survey by One Customer Voice

One Customer Voice (OCV) was introduced in Version 24H1 of SharePoint Server introduced for gathering feedback from farm administrators. When enabled, it prompts administrators with an NPS survey via a dialog box on the Central Administration page, collecting data like NPS score, reason for the score, contact email, farm ID, and SharePoint Server version. The initial prompt appears two weeks after the administrator first opens Central Administration and every six months. If dismissed, the dialog box reappears after two weeks. Administrators can disable or enable this feature via PowerShell.

To further enhance the flexibility and effectiveness of the OCV feature, SharePoint Server now introduces the new Dynamic Survey functionality. This feature allows us to configure and display surveys dynamically to gather administrator feedback based on current needs. It offers the flexibility to configure the survey type, rating questions, survey rating scale and options, comment question, and whether to collect user emails. Additionally, the frequency of survey prompts can be configured at both the user and survey levels.

Note : This feature overwrites the OCV feature released in 24H1, Thereby, the popup rule from the first iteration of this feature will no longer be triggered.

For more information, see .

### Create new Office files in client apps

This feature enhances the user experience by allowing the creation of new Office documents in an SPSE farm, even when Office Online Server (OOS), also known as Web Access Components (WAC) or Office Web Apps, is not configured or unavailable.

Previously, if OOS was not available, new Office documents could not be created from the document library in the browser. Now, new Office document creation can be initiated in the browser and completed in the client-side application. The "New" button launches the new document within the client-side office application. For example, selecting "Word document" under the "New" menu creates a new docx file in the library and opens it in the Word client application.



Previously, without OOS, users could not create new Office documents from the document library in the browser. Now, users can initiate the new Office document creation in the browser by clicking the "New" button, which will then open in the client-side application. For instance, selecting "Word document" under the "New" menu creates a new docx file in the library and then opens it in the Word client application.

For more information, see 

### Support for request body scan in AMSI

The Antimalware Scanning Interface (AMSI) feature now has the ability to scan the body of web requests. The AMSI Body Scan feature is an expansion of the existing antimalware scan capabilities in SharePoint Server Subscription Edition (SPSE), extending its reach to include the bodies of HTTP requests.

The new AMSI Body Scan feature enhances the existing AMSI functionality in SPSE by scanning the bodies of HTTP requests. This is particularly useful for detecting and mitigating threats that may be embedded in request payloads, providing a more comprehensive security solution. Users can also choose from the available modes such as Balanced and Full mode for scanning request body. 

For more information, see

### Cloud Hybrid Search upgrade

Search Content Service (SCS), an internal component of Cloud Hybrid Search in SharePoint in Microsoft 365 will be retired starting June 30, 2025. To continue using Cloud Hybrid Search, it is necessary to upgrade your SharePoint Server farm to SharePoint Server Subscription Edition (SPSE) Version 25H1 for improved security. Without this upgrade, previous versions of SharePoint Server can only search on-premises and Microsoft 365 content separately using Hybrid Federated Search. 

This update will require patching for SharePoint Server and re-onboarding the Hybrid Search Service Application (Cloud SSA) in the on-premises farm using a PowerShell script. 

For more information on upgrading an existing Cloud SSA, see 

### New database connectivity layer with TLS 1.3 and TDS 8.0 support

Starting with SPSE Version 25H1 build, SharePoint Server Subscription Edition will use [Microsoft.Data.SqlClient version 5.1.4](https://github.com/dotnet/SqlClient/tree/main/release-notes/5.1) for its database connectivity layer. This change enables advanced security capabilities such as TLS 1.3 that couldn’t be
supported in our previous database connectivity layer, while positioning SharePoint Server to leverage other new SQL capabilities. This update addresses the limitation of previous library, i.e., System.Data.SqlClient library by supporting all new SQL Server and Azure SQL features.

The following functionalities can be enabled by switching from the System.Data.SqlClient library to the Microsoft.Data.SqlClient library:

- **Support for Tabular Data Stream (TDS) Version 8.0**: The new TDS version 8.0 is secure by default, requiring encrypted connections and supporting newer encryption protocols like TLS 1.3. This ensures compatibility with older TLS versions while enhancing security.
- **Support for Transport Layer Security (TLS) Version 1.3**: SharePoint Server Subscription Edition adds support for connecting to SQL databases using TLS 1.3 connection encryption, addressing design concerns of previous versions. This enables better database connections, ensuring backward compatibility with older SQL Server versions.