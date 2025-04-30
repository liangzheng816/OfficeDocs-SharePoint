---
ms.date: 04/30/2025
title: Manage trial access to SharePoint agents with PowerShell
ms.reviewer: 
ms.author: ruihu
author: maggierui
manager: jtremper
recommendations: true
audience: Admin
f1.keywords:
- NOCSH
ms.topic: how-to
ms.service: sharepoint-online
ms.collection: 
- M365-collaboration
- m365copilot
- magic-ai-copilot
- Tier2
ms.localizationpriority: medium
search.appverid:
- MET150
description: "Learn how to manage trial access to SharePoint agents with PowerShell and how the trial access affects your organization."
---

# Manage trial access to SharePoint agents with PowerShell

## What is the trial access to SharePoint agents

During a promotional trial period starting from January 6, 2025, through June 30, 2025, organizations with 50 or more Microsoft 365 Copilot licenses automatically receive 10,000 queries per month for SharePoint agents. This trial gives users without Copilot licenses access to create and use agents. As a SharePoint admin, you can disable this trial access using the [SharePoint Online Management Shell](/powershell/sharepoint/sharepoint-online/introduction-sharepoint-online-management-shell). View the [Trial Agreement details](/legal/microsoft-365/in-app-trials-terms-of-service).

## When is the trial access available

The promotion trial goes into effect January 6, 2025, and remains active until June 30, 2025. As SharePoint agents roll out, tenants will be eligible for this promotion. As a [SharePoint Administrator](/sharepoint/sharepoint-admin-role), you can disable trial access at any point during the promotional period. Tenants that are eligible for the promotion see a message bar on the Copilot Admin page in the Admin Center.

![Screenshot of the Copilot Admin page in the Admin Center.](media/agents-sharepoint/admin-center-promo-message.png)

## What you need to prepare for the trial access

Beginning in December 2024, you, as a SharePoint admin, can use the [SharePoint Online Management Shell](/powershell/sharepoint/sharepoint-online/introduction-sharepoint-online-management-shell) to manage access to the trial for users without Copilot licenses.

You can manage the trial access to SharePoint agents by following these steps:

1. If you haven’t, update to the latest version of the SharePoint Online Management Shell
1. Run the following commands:

   | Action                                      | Command                              |
   |---------------------------------------------|--------------------------------------|
   | [Opt out and disable access to the trial](/powershell/module/sharepoint-online/set-spocopilotpromooptinstatus)  | `Set-SPOCopilotPromoOptInStatus -IsCopilotPromoStatusEnabled $false`     |
   | [Confirm trial settings to the trial](/powershell/module/sharepoint-online/get-spocopilotpromooptinstatus) | `Get-SPOCopilotPromoOptInStatus`     |
   | [Re-enable access](/powershell/module/sharepoint-online/set-spocopilotpromooptinstatus)  | `Set-SPOCopilotPromoOptInStatus -IsCopilotPromoStatusEnabled $true`     |

   > [!IMPORTANT]
   > Ensure that you have the latest version of SharePoint PowerShell installed to run these cmdlets effectively.

## How the trial access affects your organization

<div>
  <div>
Once the trial promotion is available, your unlicensed users are able to view and interact directly with SharePoint agents. They receive a notification about their promotional access and be encouraged to start exploring the feature. If the user doesn't immediately see the Copilot button in the suite navigation bar, ask them to refresh the page.  
    </div>
      <div>

![Screenshot of the trial access message in chat pane.](media/agents-sharepoint/promo-message-to-users.png)
        </div>
    <div >
      <br>Anytime these users interact with agents, their usage counts toward your organization’s monthly trial use of 10,000 queries. Once the maximum number of queries is reached, users are notified that the service is temporarily unavailable and prompted to try again next month.</br>
        <br>
        Unused queries don't roll over to the following month. If you need more queries, you can get them by adding more Microsoft 365 Copilot licenses. After the trial ends on June 30, 2025, users without a Microsoft 365 Copilot License will no longer be able to create or use the agents. However, agents created and used during the trial promotion remain available, and no historical data are lost.</br>
        </div>
    <div >
      ![Screenshot of reaching query limit message.](media/agents-sharepoint/reached-limit-message.png)
    </div>
</div>

## View SharePoint agent trial usage in Microsoft 365 Admin Center

Tenants that qualify for the trial and have opted in can view organization-wide usage data on the Copilot Admin page in the Microsoft 365 Admin Center. Admins can track usage trends month over month.

![Screenshot of the Copilot Admin page in the Microsoft 365 Admin Center.](media/agents-sharepoint/trial-usage-report-mac.png)

## Additional information

- Learn more about [SharePoint agents](https://support.microsoft.com/office/get-started-with-sharepoint-agents-69e2faf9-2c1e-4baa-8305-23e625021bcf)
