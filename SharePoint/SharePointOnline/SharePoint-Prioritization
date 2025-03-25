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
description: "What is SharePoint app prioritization and How to Leverage It"
---

# SharePoint App Prioritization: A Guide to Enhancing Business-Critical Applications in SharePoint

SharePoint app prioritization, is a powerful service designed to prioritize apps within your SharePoint Online tenants, particularly those considered business-critical. By leveraging app prioritization, organizations can ensure optimal performance, scalability, and reliability for key applications without requiring code modifications. Below, we explore what SharePoint App prioritization entails and how to effectively leverage it within your organization.

## What is SharePoint App Prioritization?

SharePoint App prioritization enables businesses to assign a higher priority to their critical applications within a SharePoint environment. This prioritization ensures that these apps are the last to experience throttling in their tenant during periods of high resource usage. It allows the app to scale resource usage limits ([aka.ms/SPO429](https://aka.ms/spo429)) significantly—ranging from a minimum of 2x up to 10x when there are available resources. Additionally, these apps receive dedicated resource units that are separate from the general tenant limits, enhancing their reliability and performance.

### Key Benefits of SharePoint App Prioritization

- **Scalable Resources**: Application resource limits can exceed [normal thresholds](https://aka.ms/spo429), offering up to 10 times more capacity when available.
- **Dedicated Resources**: Resources for prioritized apps are isolated, preventing conflicts with general tenant operations.
- **Financially-Backed SLAs**: SharePoint app prioritization follows Azure’s financially-backed Service Level Agreements, ensuring a reliable and robust service experience.
- **No Code Changes Required**: Any app can be prioritized without requiring development or code modifications as long as they can be registered on Microsoft Graph metered APIs.
- **Last to Get Throttled**: Business-critical apps are prioritized during resource contention, ensuring uninterrupted functionality.
- **Pay-As-You-Go Model**: Organizations only pay for the resources they consume.

## Metered API Classification

SharePoint app prioritization integrates with Azure's standard cost management experience, enabling organizations to monitor and control expenses associated with prioritized apps. For detailed reporting, refer to Microsoft’s Cost Management documentation.

To support prioritization, SharePoint app prioritization operates on a metered API model with defined costs:

- **Graph API Requests**: Most Graph APIs are charged at $0.50 per 1,000 requests.
- **Other API Requests**: SharePoint APIs such as CSOM and REST are charged at $1.00 per 1,000 requests.

## How to Leverage SharePoint App Prioritization

### 1. Onboard on Microsoft Graph Metered APIs

Follow the instructions at [Microsoft Graph metered APIs](https://learn.microsoft.com/en-us/graph/metered-api) to onboard your app.

### 2. Onboard and Manage SharePoint App Prioritization Using PowerShell

Administrators can manage SharePoint app prioritization policies using the [SharePoint Online PowerShell module](https://learn.microsoft.com/en-us/powershell/module/sharepoint-online/?view=sharepoint-ps). Below are some key cmdlets:

- **[Add-SPOAppPrioritizationPolicy](https://learn.microsoft.com/en-us/powershell/module/sharepoint-online/add-spoappprioritizationpolicy)**: Adds a new SharePoint app prioritization policy to your tenancy. Requires details such as App ID, Azure Subscription ID, and Quota Multiplier. The Quota Multiplier is the maximum range you want to allow the app to scale compared to [normal thresholds](https://aka.ms/spo429).
- **[Get-SPOAppPrioritizationPolicies](https://learn.microsoft.com/en-us/powershell/module/sharepoint-online/get-spoappprioritizationpolicies)**: Retrieves all existing SharePoint app prioritization policies in the tenancy.
- **[Set-SPOAppPrioritizationPolicy](https://learn.microsoft.com/en-us/powershell/module/sharepoint-online/set-spoappprioritizationpolicy)**: Edits an existing SharePoint app prioritization policy by enabling/disabling it or modifying the Quota Multiplier.
- **[Remove-SPOAppPrioritizationPolicy](https://learn.microsoft.com/en-us/powershell/module/sharepoint-online/remove-spoappprioritizationpolicy)**: Deletes an existing SharePoint app prioritization policy.

### 3. Best Practices and Considerations

- Prioritize apps that are critical to your business operations to maximize the value of SharePoint app prioritization.
- Take time to understand the limits of the service at [https://aka.ms/spo429](https://aka.ms/spo429).
- Regularly review resource usage and adjust quotas or policies as necessary to balance performance with cost efficiency.

## Related Topics

- [Microsoft Graph Metered APIs](https://learn.microsoft.com/en-us/graph/metered-api)
- [Azure Cost Management Documentation](https://learn.microsoft.com/en-us/azure/cost-management/)
- [Understanding SharePoint Throttling Limits](https://aka.ms/spo429)
- [Add-SPOAppPrioritizationPolicy PowerShell Cmdlet](https://learn.microsoft.com/en-us/powershell/module/sharepoint-online/add-spoappprioritizationpolicy?view=sharepoint-ps)

