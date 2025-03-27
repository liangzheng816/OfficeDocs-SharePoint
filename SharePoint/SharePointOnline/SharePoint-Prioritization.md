---
ms.date: 03/25/2025
title: "SharePoint App Prioritization"
ms.reviewer: 
ms.author: sibourda
author: killerewok2000
manager: fraga
recommendations: true
audience: Admin
f1.keywords: NOCSH
ms.topic: article
ms.service: sharepoint-online
ms.collection: M365-collaboration
ms.custom: admindeeplinkSPO
ms.localizationpriority: medium
search.appverid:
- SPO160
- MET150
ms.assetid: 
description: "Learn about SharePoint app prioritization and how to use it to enhance business-critical applications."
---

# SharePoint App Prioritization

SharePoint app prioritization is a service that helps prioritize apps in your SharePoint Online tenants, especially business-critical ones. It ensures these apps perform optimally, scale effectively, and remain reliable without requiring code changes. This guide explains what SharePoint app prioritization is and how to use it.

> [!NOTE]
> This feature is still rolling out and may not yet be fully available in your tenant.

## What is SharePoint App Prioritization?

SharePoint app prioritization allows businesses to assign higher priority to critical applications in a SharePoint environment. These apps are the last to face throttling during high resource usage. They can scale resource usage limits ([aka.ms/SPO429](https://aka.ms/spo429)) by minimum 2x to 10x when resources are available. Additionally, prioritized apps receive dedicated resource units separate from general tenant limits, improving reliability and performance.

### Key Benefits

- **Scalable Resources**: Apps can exceed [normal thresholds](https://aka.ms/spo429) by up to 10x when resources are available.
- **Dedicated Resources**: Prioritized apps use isolated resources, avoiding conflicts with general tenant operations. The app utilization no longer counts against user and tenant limits.
- **Financially-Backed SLAs**: The service follows Azure’s financially-backed Service Level Agreements for reliability.
- **No Code Changes**: Apps can be prioritized without development changes if they are registered on [Microsoft Graph metered APIs](/graph/metered-api-overview).
- **Reduced Throttling**: Critical apps are prioritized during resource contention, ensuring uninterrupted functionality.
- **Pay-As-You-Go**: Organizations only pay for the resources they use.

## Metered API Classification

SharePoint app prioritization integrates with Azure's cost management tools, allowing organizations to monitor and control expenses. The service operates on a metered API model with defined costs:

- **Graph API Requests**: Most Graph API requests cost $0.50 per 1,000 requests.
- **Other API Requests**: SharePoint APIs like CSOM and REST cost $1.00 per 1,000 requests.

> [!NOTE]
> As stated above, while this is part of the Microsoft Graph Metered API platform, all API calls to SharePoint and OneDrive will be included. Prices will vary based on the API used per pricing above.

## How to Use SharePoint App Prioritization

### 1. Onboard to Microsoft Graph Metered APIs

Follow the instructions at [Microsoft Graph metered APIs](/graph/metered-api-setup) to onboard your app.

### 2. Manage SharePoint App Prioritization with PowerShell

Administrators can manage prioritization policies using the [SharePoint Online PowerShell module](/powershell/module/sharepoint-online/index). Key cmdlets include:

- **[Add-SPOAppPrioritizationPolicy](/powershell/module/sharepoint-online/add-spoappprioritizationpolicy)**: Adds a new policy. Requires App ID, Azure Subscription ID, and Quota Multiplier (the maximum scaling range compared to [normal thresholds](https://aka.ms/spo429)).
- **[Get-SPOAppPrioritizationPolicies](/powershell/module/sharepoint-online/get-spoappprioritizationpolicies)**: Retrieves all existing policies.
- **[Set-SPOAppPrioritizationPolicy](/powershell/module/sharepoint-online/set-spoappprioritizationpolicy)**: Edits an existing policy by enabling/disabling it or modifying the Quota Multiplier.
- **[Remove-SPOAppPrioritizationPolicy](/powershell/module/sharepoint-online/remove-spoappprioritizationpolicy)**: Deletes an existing policy.

### 3. Best Practices

- Prioritize apps critical to your business to maximize the service's value.
- Understand the service limits at [https://aka.ms/spo429](https://aka.ms/spo429).
- Regularly review resource usage and adjust quotas or policies to balance performance and cost.

## Frequently Asked Questions (FAQ)

### What is the cost of using SharePoint App Prioritization?
The cost depends on the API usage. Graph API requests cost $0.50 per 1,000 requests, while SharePoint APIs like CSOM and REST cost $1.00 per 1,000 requests.

### Can I prioritize apps without making code changes?
Yes, apps can be prioritized without development changes if they are registered on Microsoft Graph metered APIs.

### How do I monitor the cost of prioritized apps?
You can use [Azure's cost management tools](/azure/cost-management-billing/understand/download-azure-invoice) to monitor and control expenses related to SharePoint App Prioritization.

### What happens if my app exceeds the allocated quota?
Depending on the quota multiplier property assigned (2 to 10), when the set limit is reached, the app will see normal throttling responses.

### How are throttling rules applied?
Based on the limits defined at [Aka.ms/SPO429](https://aka.ms/spo429), the following will change. The [user](/sharepoint/dev/general-development/how-to-avoid-getting-throttled-or-blocked-in-sharepoint-online#user-throttling) and [tenant](/sharepoint/dev/general-development/how-to-avoid-getting-throttled-or-blocked-in-sharepoint-online#tenant-throttling) limits won't apply to apps onboarded on SharePoint app prioritization. The [app](/sharepoint/dev/general-development/how-to-avoid-getting-throttled-or-blocked-in-sharepoint-online#application-throttling) category limit will see its base numbers multiplied by the assigned quota multiplier value.

## Related Topics

- [Microsoft Graph Metered APIs](/graph/metered-api-overview)
- [Azure Cost Management Documentation](/azure/cost-management/index)
- [Understanding SharePoint Throttling Limits](https://aka.ms/spo429)
- [Add-SPOAppPrioritizationPolicy PowerShell Cmdlet](/powershell/module/sharepoint-online/add-spoappprioritizationpolicy)



