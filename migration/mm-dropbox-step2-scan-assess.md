---
ms.date: 01/07/2025
title: "Step 2: Scan and assess Dropbox folders using Migration Manager"
ms.reviewer:
ms.author: heidip
author: MicrosoftHeidi
manager: jtremper
audience: ITPro
f1.keywords:
- NOCSH
ms.topic: how-to
ms.service: microsoft-365-migration
ms.localizationpriority: high
ms.collection:
- m365solution-migratefileshares
- m365solution-migratetom365
- m365solution-scenario
- M365-collaboration
- SPMigration
- highpri
- m365initiative-migratetom365
search.appverid: MET150
description: "Step 2: Scan and assess Dropbox folders using Migration Manager."
---

# Step 2: Scan and assess Dropbox folders

After you connect to Dropbox, add the source paths to scan and assess your Dropbox folders. 

After you connect, scan and assess your Box user accounts.

1. Select **Add folders** from the menu bar to choose how to add folders:</br> - **All new folders** to autodiscover all new users in Box</br>- **Single folder** for only one account,  or </br>- **Multiple specific folders** to bulk upload folders by entering them into a CSV file to upload.
2. Choose to **Automatically start scanning now** or choose to scan later.
3. Select **Add**.
4. Highlight any or all of the accounts and then select **Scan** if you chose not to auto scan earlier.

>[!Important]
> The total number cannot exceed 50,000 tasks.

5. Once the scan is complete, a table summary displays to give you an at-a-glance overview of your folders. The summary includes Folder item counts, migration readiness, and any issues that need attention. 
4. Review the scanned folders. Search for specific text, or select a filter to review the list more easily.


## Download reports

Summary and detailed scan reports are available to assist you in troubleshooting. Download the generated reports and logs to investigate any possible issues that might block your migration.

1. Once the scan is complete, select **Download summary report**.

2. To download a detailed scan report for an individual account, select a single row, then select **Download scan log**.

## Managing Folders that contain large amounts of data

Upon completing your scan, download the scan reports and review/address any large source data owners.

A migration task (Dropbox Team Folder or Member Folder) should not exceed 100,000 items or 1 TB of data. To enable faster transfers, Team Folders or Member Folders in Dropbox with large data sets should be divided into smaller migration tasks based on their root folders.

To split a Team Folder or Member Folder into multiple migration tasks, follow these steps:

1. Delete the Folder.
1. Select **Add folders** from the command bar.
1. In the side panel that appears, select **Multiple specific folders**.
4. Download and edit the provided .csv template file to divide the Folder into multiple tasks. For example:
    - `MemberFolder01@contoso.com/folder01`  
    - `MemberFolder01@contoso.com/folder02`  
    - `MemberFolder01@contoso.com/folder03`  
    - `MemberFolder01@contoso.com/folder04` 
5. Save the updated .csv file and upload it to create the divided migration tasks.

## [**Step 3: Copy to migrations**](mm-dropbox-step3-copy-to-migrations.md)

