---
ms.date: 03/20/2025
title: "Restrict discovery of SharePoint sites and content"
ms.reviewer: nibandyo
manager: jtremper
recommendations: true 
ms.author: mactra
author: MachelleTranMSFT
audience: Admin
f1.keywords: 
- NOCSH 
ms.topic: article
ms.service: sharepoint-online
ms.localizationpriority: medium
ms.custom:
  - has-azure-ad-ps-ref
ms.collection: 
- M365-collaboration
- M365-SAM
- Tier2
search.appverid:
description: "Learn how to restrict the discovery of SharePoint sites from Microsoft 365 Copilot Business Chat and tenant-wide search."
---

# Restrict discovery of SharePoint sites and content

[!INCLUDE[Advanced Management](includes/advanced-management.md)]

For organizations onboarding to Microsoft 365 Copilot, maintaining strong data governance controls for SharePoint content is critical to deploying Copilot in a safe manner. Sites identified with the highest risk of oversharing can use restricted content discovery to protect content while taking time to ensure that permissions are accurate and well-managed.

## What is restricted content discovery?

With restricted content discovery, organizations can limit the ability of end users to search for files from specific SharePoint sites. Enabling restricted content discovery for each site prevents the sites from surfacing in organization-wide search and Microsoft 365 Copilot Business Chat, unless a user had a recent interaction.  

> [!NOTE]
> Restricted content discovery doesn't affect existing permissions on sites. Users with access can still open files on sites with restricted content discovery toggled on.

While child content is hidden by default, users in your organization can still discover files they own or recently interacted with. End users can still find relevant content they need for their day-to-day tasks, even if restricted content discovery is applied to the parent site.

Restricted content discovery doesn't affect searches originating from a site context or other intelligent features such as Microsoft 365 Feed and Recommendations.

## Use cases for restricted content discovery

Restricted content discovery can be applied to any SharePoint site in your organization. The key use case for this feature is to prevent accidental discovery of high-risk sites.

We recommend using tools such as Data access governance reports and SharePoint admin center's **Active sites** tab to first compile a selective list of targeted sites.

> [!NOTE]
> This feature can't be applied to OneDrive sites.

> [!CAUTION]
> Overuse of restricted content discovery can negatively affect performance across search, SharePoint, and Copilot. Removing sites or files from tenant-wide discovery means that there's less content for search and Copilot to ground on, leading to inaccurate or incomplete results.

Restricted content discovery is a site-level setting that needs to be propagated to the search index, a large number of transactions could lead to a long queue in the ingestion pipeline and higher update latency times.

## Prerequisites

The restricted content discovery policy requires the following prerequisites:

- Have a [Microsoft SharePoint Premium - SharePoint Advanced Management subscription](advanced-management.md).
- Download and install the latest version of SharePoint Online Management Shell.
- Connect to SharePoint Online as a SharePoint Administrator in Microsoft 365.

## Configure restricted content discovery

By default, restricted content discovery is off for all sites. As an IT administrator, you can enable or disable this feature, and check the current state of a given site.

### Enable restricted content discovery for a site

You can enable restricted content discovery from the SharePoint admin center or via PowerShell.

To enable restricted content discovery for a site using SharePoint admin center:

1. In SharePoint admin center, expand **Sites** and select **Active sites**.
2. Select the site you want to restrict the content discovery, and the site details panel appears.
3. In the **Settings** tab, toggle on or off in the **Restrict content from Microsoft 365 Copilot** section.
4. Select **Save**.

:::image type="content" source="./media/restricted-content-discovery/1-rcd-enable-spac.png" alt-text="Screenshot of site details panel showing ability to restrict a site from being discovered in Microsoft 365 Copilot." lightbox="./media/restricted-content-discovery/1-rcd-enable-spac.png":::

> [!NOTE]
> Changes can take time to be effective.

To enable restricted content discovery for a site using PowerShell, run the following command:

```powershell
Set-SPOSite –identity <site-url> -RestrictContentOrgWideSearch $true
```

### Check status of restricted content discovery

To check the status of restricted content discovery, run the following command:

```powershell
Get-SPOSite –identity <site-url> | Select RestrictContentOrgWideSearch
```

### Remove restricted content discovery from a site

To remove restricted content discovery on a SharePoint site, run the following command:

```powershell
Set-SPOSite –identity <site-url> -RestrictContentOrgWideSearch $false
```

### Delegate restricted content discovery management to site owners and site admins

Restricted content discovery is disabled by default for site owners and site admins. You can enable this feature for site owners and site admins by running the following commands in SharePoint Online Management Shell as an administrator:

To enable delegation control, run the following command:

```powershell
Set-SPOTenant -DelegateRestrictedContentDiscoverabilityManagement $true
```

To fetch delegation status, run the following command:

```powershell
Get-SPOTenant | Select-Object DelegateRestrictedContentDiscoverabilityManagement
```

### Allow site admins to edit restricted content discovery

> [!NOTE]
> Once the restricted content discovery policy is enabled for a site and the delegation control is configured, the site admin can view this setting in the **Site information** panel.

:::image type="content" source="./media/restricted-content-discovery/0-rcd-site-info-panel.png" alt-text="Screenshot of site information panel showing site owners and site admins the ability to restrict a site from being discovered in Microsoft 365 Copilot." lightbox="./media/restricted-content-discovery/0-rcd-site-info-panel.png":::

## Restricted content discovery policy insights

You can view the following reports to gain insights on the SharePoint sites protected with restricted content discovery:

### Generate insights report

To generate a list of sites with restricted content discovery enabled, run the following command:

```powershell
Start-SPORestrictedContentDiscoverabilityReport
```

### View insights report

To view a report displaying the Report GUID, created DateTime stamp, and status of the report generation, run the following command:

```powershell
Get-SPORestrictedContentDiscoverabilityReport
```

### Download insights report

To download a restricted content discovery insights report, you must run the following command as an administrator:

```powershell
Get-SPORestrictedContentDiscoverabilityReport –Action Download –ReportId <Report GUID>
```

The downloaded report is located on the path where the command was run.

## Next steps

Restricted content discovery gives organizations time to review and/or audit permissions and deploy access controls while onboarding Copilot in a safe manner.

Ultimately for sites that are overshared, the goal is to ensure that proper controls are in place to manage access. SharePoint Advanced Management has a suite of features, such as advanced site content lifecycle management, to help site owners and admins create a robust SharePoint governance framework.

## Frequently Asked Questions

**Is my organization eligible to use restricted content discovery?**

Customers who are licensed for Copilot and have SharePoint Advanced Management available to them can configure restricted content discovery.

**What search scenarios enforce restricted content discovery?**

Restricted content discovery only affects tenant-wide search (SharePoint home, Office.com, Bing) and Microsoft 365 Copilot. Only Copilot Discovery scenarios are in scope; Copilot experiences that use data-in-use, such as "summarize the current document" in Word aren't impacted.  

**Does restricted content discovery impact other features with dependencies on the search index, such as the Microsoft Purview product suite?**

No, restricted content discovery doesn't remove content from the tenant search index, which means Microsoft Purview features such as eDiscovery and autolabeling aren't impacted.

**How soon can I expect Search and Copilot to reflect an update made to the restricted content discovery configuration of a site?**

Restricted content discovery is a site-level property. Index update latency is highly dependent on the number of items in the site and the number of sites getting updated at the same time. For sites with more than 500,000 items, the restricted content discovery update could take more than a week to fully process and reflect in search and Copilot.

**How does restricted content discovery affect the end user experience in Copilot?**

Based on usage of this feature, Copilot has less information available to reference, which could negatively affect its ability to provide accurate and comprehensive responses.

**How does restricted content discovery fit into an overall approach to prepare SharePoint data for Microsoft 365 Copilot?**

Restricted content discovery is designed to limit the ability of end users to search for content from specific SharePoint sites. For a more comprehensive guidance on preparing your data for Copilot, check out this [blueprint](https://aka.ms/Copilot/OversharingBlueprintLearn).

## Related topics

[Overview of SharePoint Advanced Management](advanced-management.md)

[Manage access agents in SharePoint](manage-access-agents-in-sharepoint.md)
