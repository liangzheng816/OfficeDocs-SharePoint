---
ms.date: 01/21/2025
title: "Manage unlicensed OneDrive user accounts"
ms.author: mactra
author: MachelleTranMSFT
ms.reviewer: trgreen
manager: jtremper
recommendations: true
audience: Admin
f1.keywords:
- NOCSH
ms.topic: article
ms.service: one-drive
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- Highpri
- Tier2
description: "Learn how to manage unlicensed OneDrive user accounts."
---

# Manage unlicensed OneDrive user accounts

As an [IT administrator](/microsoft-365/admin/add-users/about-admin-roles), you might encounter situations where some of your users have unmanaged and unlicensed OneDrive accounts within your organization. Unlicensed OneDrive accounts can pose security and compliance risks, as well as create confusion and duplication of files.

In this article, you learn how to identify, monitor, and manage unlicensed OneDrive accounts in your organization.

## Enforcement of policy changes for unlicensed OneDrive accounts

> [!IMPORTANT]
>
> Enforcement will begin on January 27, 2025, and the process will roll out gradually over a few months. Admins should anticipate that it takes time for all unlicensed accounts to complete the enforcement process.
>
> - Unlicensed OneDrive accounts subject to a retention policy, retention period, or legal hold will be automatically archived after 93 days of license removal. While these accounts remain visible to admins through administrative tools, neither admins nor end users have access to their content. Access stays restricted until administrators take specific actions. (Note these changes don't apply to EDU, GCC, or DoD customers.)
> - Unlicensed accounts not covered by any retention policy or legal hold will be moved to the recycle bin after 93 days of license removal.

### Timeline for accounts unlicensed before February 17, 2025

- April 25, 2025: By this date, all unlicensed accounts transition to read-only mode. Admins are advised to check after this date. Checking earlier can result in an incomplete status snapshot.
- May 16, 2025: By this date, all unlicensed accounts are archived. Admins are advised to check after this date. Checking earlier can result in an incomplete status snapshot.

### Timeline for accounts unlicensed after February 17, 2025

For accounts unlicensed after February 17, 2025, the account will be put into read-only mode on the 60th unlicensed day, and will be archived or moved to the recycle bin on the 93rd unlicensed day.

**Example:**

- Unlicensed Date: March 1, 2025
- Day 60: April 30, 2025. The account is placed in read-only mode.
- Day 93: June 2, 2025: The account is either archived (if a retention policy is in place) or moved to the recycle bin (if no retention policy applies).

Admins are encouraged to monitor account statuses based on these timelines to ensure compliance and take any necessary actions.

## Unlicensed OneDrive account management options

After you identify the unlicensed OneDrive account, you can choose to license or delete the account.

### Assign license to unlicensed OneDrive account

**Prior to the unlicensed OneDrive account archival** - To assign a license to an unlicensed OneDrive account, you need to assign a Microsoft 365 or Office 365 subscription to the user that includes OneDrive. Assigning a license allows the user to access their OneDrive files with their work or school account, and lets you manage their settings and policies.

You can also bulk assign licenses using either of the following methods:

- [Assign licenses to user accounts in the Microsoft 365 admin center](/microsoft-365/admin/manage/assign-licenses-to-users)
- [Assign licenses to user accounts with PowerShell](/microsoft-365/enterprise/assign-licenses-to-user-accounts-with-microsoft-365-powershell)

**After the unlicensed OneDrive account archival** - The account must be reactivated from the archived state before a license can be assigned. If the archived account has an associated user, the IT admin can give the user a valid license and the account is automatically reactivated within 24 hours. If the archived account doesn't have an associated user (for example, if the identity was deleted), then we recommend admins move any actively needed content to a SharePoint site or an active and licensed OneDrive account. For more information on licensing and active users in Microsoft 365, see [Assign or unassign licenses for users in the Microsoft 365 admin center](/microsoft-365/admin/manage/assign-licenses-to-users).

### Delete unlicensed OneDrive account

**Prior to the unlicensed OneDrive account archival** - To delete an unlicensed OneDrive account, you need to [remove the user from your organization and delete their data](/microsoft-365/admin/add-users/delete-a-user). You can use the Microsoft 365 admin center, PowerShell, or the Microsoft Graph API to permanently delete the user.  

Once you delete the unlicensed account, both the OneDrive account and its files are moved to the recycle bin. After 93 days, it will be permanently deleted, and the user is no longer able to sign in to their work or school account.

**After the unlicensed OneDrive account archival** - An account can be deleted from the archived state without reactivation. However, if the account is subject to a retention policy, the unlicensed account can't be deleted, and the administrator receives an error message.

### Archive unlicensed OneDrive account

If no action is taken, the account remains archived through [Microsoft 365 Archive](/microsoft-365/syntex/archive/archive-overview). Archiving the account lets you keep the OneDrive account and its data for long periods of time in case you need to retrieve it later.

For newly unlicensed OneDrive accounts, it will be after 93 days of the license removal or user deletion. For example, a OneDrive account that became unlicensed on August 1, 2025, will be inaccessible to users as of November 2, 2025. For unlicensed OneDrive accounts with license removal before October 26, 2024, the accounts will be archived sometime between late January 2025 to late March 2025.

### Access unlicensed OneDrive account

**Accessing an Archived OneDrive Account:**

- To access data from an archived OneDrive account, reactivation is required. Follow these prerequisites to set up [Microsoft 365 Archive:](/microsoft-365/syntex/archive/archive-setup)

  1. Set up and link an [Azure subscription in Syntex pay-as-you-go](/microsoft-365/syntex/syntex-azure-billing).
  
  1. Ensure you have Global admin or SharePoint admin permissions.
  
  1. [Enable Microsoft 365 Archive ](/microsoft-365/syntex/syntex-azure-billing)Unlicensed Account billing (available starting December 2024).
  
     After completing the setup and triggering reactivation, it may take up to 24 hours for the account to become accessible. Once reactivated, the account remains active for 30 days before being automatically archived again.
  
**Accessing a Read-Only OneDrive Account:**

- If the OneDrive account has been set to read-only, administrators have multiple options to access the content:

  - [Add a license](/SharePoint/unlicensed-onedrive-accounts#assign-license-to-unlicensed-onedrive-account)
    
  - [Use PowerShell to unlock the site](/sharepoint/manage-lock-status) 
  
> [!NOTE]
> These changes don't apply to EDU, GCC, or DoD customers.

## Reporting

Unlicensed OneDrive accounts aren't associated with a Microsoft 365 or Office 365 subscription in your organization. A OneDrive account can become unlicensed when the licensing isn't activated or is expired.

You can also encounter unlicensed OneDrive accounts when accounts are created, but aren't assigned a license. Monitoring unlicensed accounts can help you determine the risk of these accounts, and plan for migration or [deletion of user accounts](/microsoft-365/admin/add-users/delete-a-user).

### Get unlicensed OneDrive users report

You can identify unlicensed OneDrive accounts using the SharePoint admin center. The following steps show how to use the SharePoint admin center to generate a report of unlicensed OneDrive accounts:

1. Sign in to the SharePoint admin center with your work or school account.
2. Go to **Reports** and select **User reports**.
3. Under **OneDrive usage**, select **Unlicensed users**.
4. You can download the report as a CSV file.
5. Starting January 2025, an interactive UI is available. You can select a username to view the details.

   The report shows the username, email address, account type, and last activity date of each unlicensed OneDrive account.

   The following table provides more information on data shown in the unlicensed OneDrive accounts report:

   |Column|Description|
   |---|---|
   | Unlicensed accounts | Total number of OneDrive accounts that aren't licensed as of the date the report is generated.|
   | Storage used | Total storage consumed by these unlicensed OneDrive accounts as of the report's date.|
   | Retention period | Unlicensed accounts with a [set retention period](set-retention.md) during the process of license removal or user account deletion. The retention period is honored, and the content remains in an archived state until the period expires.|
   | Retention policy | Unlicensed accounts subject to a [retention policy](/purview/retention) set up in Microsoft Purview. The retention policy is honored, and the content remains in an archived state until the policy expires.|
   | Active user with no license | Accounts where the user's license was removed, but the account wasn't deleted as part of the [user deletion process](/microsoft-365/admin/add-users/delete-a-user). Starting in January 2025, users who aren't assigned a license, but are still considered active in the system, are archived on the 93rd unlicensed day. If unlicensed billing is enabled, then these archived accounts remain in the Archive state indefinitely, otherwise they're deleted. |
   | Duplicate account | Unlicensed accounts created when an employee transfers to a different country/region, or firm within the organization. If these duplicate accounts are unnecessary, we recommend using the downloadable CSV from the SharePoint admin center to identify and delete them. If no action is taken, the accounts are automatically archived starting in January 2025 and incurs archive charges.|
   | Unlicensed reason | 'No owner' – There's no owner assigned to the OneDrive account, meaning that no license can be associated with this account.|
   ||'Owner deleted from Entra ID' – The assigned owner was deleted, thus there's no license associated with this account.|
   ||'License removed by admin' – The owner is present in Entra ID, but the owner’s license has been removed from the account.|
   ||'Duplicate account' – The owner has multiple OneDrive accounts associated with their identity. The duplicate account isn't the primary OneDrive account associated with the owner’s identity. All nonprimary accounts associated with the owner are considered unlicensed.|
   |Deletion blocked by|'Retention period' – The OneDrive account has been market for deletion but is within the global OneDrive account retention period, as defined by the [OneDrive retention period setting](set-retention.md). Shortening the retention period helps reduce unlicensed OneDrive accounts being retained for this reason.|
||'Retention policy' – A retention policy, a legal hold, or a compliance hold defined in Purview is stopping this account’s contents from being deleted. The retention policy might be applied to only a subset of the account’s contents, which would prevent the entire OneDrive account from being deleted. Modify your Purview retention or hold requirements to reduce OneDrive accounts held for this reason.|
||'Owner active in Entra ID' – The OneDrive account’s owner is still active in Entra ID, causing the account to not be deleted. When unlicensed OneDrive account enforcement begins, these accounts will be deleted after the 93rd unlicensed day and will follow the usual deprovisioning flow including honoring the retention period and any Purview retention or hold requirements.|
|| 'Restored site' – This account was restored from the site recycle bin by an IT administrator. Since the account was intentionally restored, it will no longer be deleted automatically.|

### View more details on unlicensed OneDrive accounts

You can view details on all unlicensed OneDrive accounts, even ones that aren’t passed their 93rd unlicensed day yet, in the SharePoint admin center.

1. In the SharePoint admin center, select **Reports**.
1. Select **OneDrive accounts** and then select **View more details**.

   :::image type="content" alt-text="GIF showing how to access view more details section for unlicensed OneDrive accounts in SharePoint admin center." source="media/unlicensed-onedrive/access-detailed-report-unlicensed-accounts.gif" lightbox="media/unlicensed-onedrive/access-detailed-report-unlicensed-accounts.gif":::

   From this page, you can do the following actions:

   - Enumerate individual unlicensed accounts
   - See account details such as URL, Title, Storage used, Unlicensed date, unlicensed reason, and Archive status
   - Delete accounts (some caveats exist such as delete failing because the account is on hold)
   - Reactivate accounts

> [!NOTE]
> Admins can reactivate accounts from the detailed report.  Accounts selected in the detailed report will display a 'Reactivate' button if the account is archived and billing for Unlicensed OneDrive accounts has been enabled.

## Charges from archived accounts

Once billing for unlicensed OneDrive accounts has been enabled, archived unlicensed OneDrive accounts which aren't deleted will begin to incur charges for both monthly storage and ad-hoc account reactivation.

> [!NOTE]
> Billing enablement refers to turning on the Unlicensed OneDrive accounts billing toggle, which can only be enabled once a general pay-as-you-go billing method has been set up. Billing starts when the billing enablement for unlicensed OneDrive accounts is activated, not when an account is reactivated. Reactivation requires billing enablement, and once it is activated, storage charges begin.

:::image type="content" source="media/unlicensed-onedrive/0-unlicensed-accounts-enablement.png" alt-text="screenshot of billing enablement for unlicensed accounts." lightbox="media/unlicensed-onedrive/0-unlicensed-accounts-enablement.png":::

If the billing is put down to reactivate one particular unlicensed account, the reactivation fee is applied for $0.60/GB for that account, and from that month onward, the storage fee of $0.05/GB/Month is applicable for all unlicensed accounts within the organization for longer than 93 days.

For example, if an organization has 100 unlicensed OneDrive accounts, each consuming 1 TB for a total of 100 TB, and enforcement occurs between January and March 2025, the 100 unlicensed accounts are automatically archived. If the organization needs to reactivate a specific account in October 2025 and set up billing, they incur the following costs:

- A one-time reactivation fee of $0.60/GB for 1TB, totaling $614.40.
- A monthly storage fee of $0.05/GB for 100TB, amounting to $5,120/month starting from October 2025.

> [!NOTE]
> Unlicensed OneDrive accounts can't utilize unused SharePoint storage quota, even if Microsoft 365 Archive is configured within the tenant. Archived unlicensed OneDrive accounts are billed for the full amount of consumed storage.

## Use Microsoft Purview in Archived State

Archived OneDrive accounts fully honor retention policies, settings, and litigation hold and eDiscovery hold. For example, if your company has a five-year retention policy, it remains unchanged whether the OneDrive account is active or archived. Archiving doesn't reset the timeline of the retention policy or holds.

Microsoft Purview eDiscovery and Content Search are still discoverable in archived content. Exporting the content that's supporting the search results doesn't require manual reactivation of the archived account, and it takes up to 24 hours to complete.

Changes made to retention policies apply to archived accounts. For example, if the company reduces the retention policy from five years to three years, this update syncs with all archived accounts, for any accounts that fulfill the updated retention period, those accounts are moved to recycle bin, and the recycle bin process begins.

## Unlicensed OneDrive accounts and education tenants

An education tenant is any tenant with more than 50% education licenses. Any tenant with fewer than 50% education licenses is considered commercial. However, for any education tenant, unlicensed OneDrive accounts consume pooled storage and can pose security and compliance risks. IT admins can view the unlicensed accounts on the OneDrive accounts page to identify unlicensed accounts and take action.

## Frequently Asked Questions

**1. What is an unlicensed OneDrive account?**

**Answer:** When an employee leaves an organization or a license is removed, their OneDrive account becomes unlicensed after the admin takes one of two steps:

**License Removal:**

- Go to the Microsoft 365 admin center.

- Expand Billing and select **Your Products**.
- Select the subscription and select **Remove licenses**.

**User Deletion:**

- In the Microsoft 365 admin center, expand **Users** and select **Active users**.
- Delete the user.

For more information on deleting users, see [Delete a user from your organization](/microsoft-365/admin/add-users/delete-a-user).

**2. Can unlicensed ODB leverage unused SPO storage quota?**

**Answer:** No. They're independent. Unlicensed OneDrive accounts can't use unused SharePoint storage quota, even though there's Microsoft 365 Archive set up in the SharePoint tenant.

**3. What is the outcome if an Unlicensed OneDrive account is restored from the Recycle Bin, 90 days after its license removal? Does the account get automatically archived?**

**Answer:** Yes. If 93 days have past since the license removal, bringing back an unlicensed OneDrive account from the recycle bin can lead to automatic archival.

**4. When will an unlicensed account get archived?**

**Answer:** For newly unlicensed OneDrive accounts, it will be after 93 days of the license removal or user deletion. For example, a OneDrive account that became unlicensed on August 1, 2025, will be inaccessible to users as of November 2, 2025. For unlicensed OneDrive accounts with license removal before October 26, 2024, the accounts will be archived sometime between late January 2025 to late March 2025.

**5. How does it impact eDiscovery in Microsoft Purview?**

**Answer:** Microsoft Purview eDiscovery and Content Search are still discoverable in archived content. Exporting the content that's supporting the search results doesn't require manual reactivation of the archived account, and it takes up to 24 hours to complete.

**6. How does it impact Retention Policy, Retention Setting, or Litigation Hold?**

**Answer:** Archived OneDrive accounts fully honor retention policies, settings, and litigation holds. For example, if your company has a five-year retention policy, it remains unchanged whether the OneDrive account is active or archived. Archiving doesn't reset the timeline of the retention policy or holds.

> [!Note]
> If a OneDrive account is retained due to a Retention Policy, Retention Setting, or Litigation Hold and has been archived due to being unlicensed for 93 days or longer, then you will still pay for the monthly archive storage costs when billing is enabled.

**7. Can I delete an unlicensed account without Archive reactivation?**

**Answer:** Yes. An archived unlicensed account can be deleted from the archive state. However, if the account is under retention policy, the unlicensed account can't be deleted, and the administrator receives an error message.

**8. When will I get charged?**

**Answer:** Once a payment method is provided, billing follows the routine cycle for archived content. If there's no retention policy and billing stops, your content is deleted within a 93-day period. If a retention policy is still active, the policy is honored regardless of billing status. If the account has no retention and billing, the 93-day content deletion lifecycle begins.

As an example, if the billing is put down to reactivate one particular unlicensed account, the reactivation fee is applied for $0.60/GB for that account, and from that month onward, the storing fee of $0.05/GB/Month is applied for all unlicensed accounts within the organization that's longer than 90 days.

**9. What's the guidance on 'duplicate accounts'?**

**Answer:** A duplicate account is created when an employee switches to a different country/region or a different firm within the organization. If the duplicate accounts aren't desired, we recommend using the downloadable CSV in the SharePoint Admin Center to identify the accounts and delete them. For already-archived unlicensed OneDrive accounts, it can be deleted from the archived state without the need of reactivation.

**10. Once I initiate the reactivation of an account from Microsoft 365 Archive, how long do I have to wait until the data is available?**

**Answer:** It takes up to 24 hours for the account to be accessible. Once the account is reactivated, it remains active for a total of 30 days before it gets automatically archived again.

**11. Is there any charge to use the eDiscovery Hold feature?**
**Answer:** We honor eDiscovery hold and charge accordingly. eDiscovery Hold works the same way as retention policy and legal hold.

**12. What's the process to relicense an account once it's archived?**

**Answer:** If the archived account has an associated user, the IT admin can give the user a valid license and the account automatically reactivates within 24 hours. If the archived account doesn't have an associated user (for example, if the identity was deleted), then we recommend admins move any actively needed content to a SharePoint site or an active and licensed OneDrive account.

**13. If a change is made to retention policies, will that change sync down to the archived sites?**

**Answer:** Yes. As an example, if the company retention policy is shortened from five years to three years, this change is synced with all archived accounts, and the recycle bin process begins for accounts that completed the retention policy.

**14. Why are there two different report pages with different numbers about unlicensed accounts?**

**Answer:** The [top-level report page](http://spo.ms/admin#/oneDriveAccounts) shows you insights and lets you download the list of accounts which are at least 93 days unlicensed.  This page directly indicates the amount of storage that will be billed if you have enabled billing.  The [detailed report page](http://spo.ms/admin#/oneDriveAccounts/management) is linked from the top-level report page, and indicates all accounts that are currently unlicensed, even if they have been unlicensed for fewer than 93 days.  

## Related topics

- [OneDrive retention and deletion](retention-and-deletion.md)

- [Pricing model for Microsoft 365 Archive](/microsoft-365/archive/archive-pricing)

- [Learn about retention for SharePoint and OneDrive](/purview/retention-policies-sharepoint#how-retention-works-with-microsoft-365-archive)

- [Set the OneDrive retention for deleted users](set-retention.md)

- [Create retention labels for exceptions](/purview/create-retention-labels-data-lifecycle-management)

- [Delete a user from your organization](/microsoft-365/admin/add-users/delete-a-user)

- [Assign or unassign licenses for users in the Microsoft 365 admin center](/microsoft-365/admin/manage/assign-licenses-to-users)

