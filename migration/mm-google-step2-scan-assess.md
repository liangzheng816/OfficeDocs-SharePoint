---
ms.date: 03/25/2025
title: "Step 2: Scan and assess Google accounts using Migration Manager"
ms.reviewer:
ms.author: heidip
author: MicrosoftHeidi
manager: jtremper
audience: ITPro
f1.keywords:
- NOCSH
ms.topic: article
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
description: "Step 2:  Scan and assess Google users using Migration Manager."
---

# Step 2: Scan and assess Google Drives

After you connect to Google, add the Drives to scan and assess.

1. Select **Add Drives** and choose a method: to look for new users in Google Drives, target a single source path, or bulk upload the source paths using a CSV file. You can choose to automatically start scanning or do it later. However, all drives must be scanned before you can migrate them.

   :::image type="content" source="media/mm-google-add-drive-choices.png" alt-text="Select how to add google drives.":::

2. After adding the drives, highlight any or all of the drives and then select **Scan** if you haven't already.

>[!Important]
> The total number can't exceed 50,000 tasks.

3. Once the scan is complete, a table summary displays to give you an at-a-glance overview of your users. The summary includes content size, migration readiness, and any issues that need attention. Review the scanned users. Search for specific text, or select a filter to review the list more easily or download summary and detailed reports to troubleshoot further.

## Download reports

Summary and detailed scan reports are available to assist you in troubleshooting. Download the generated reports and logs to investigate any possible issues that might block your migration.

1. Once the scan is complete, select **Download reports**.

   ![download reports for google](media/mm-google-download-reports-button.png)
   
2. To download a detailed scan report for an individual account, select a single row, then select **Download scan log**.

## Managing Drives that own large amounts of data

Upon completing your scan, download the scan reports and review/address any large source data owners.

A migration task (Google Drive) shouldn't exceed 100,000 items or 1 TB of data. To enable faster transfers, Google Drives with large data sets should be divided into smaller migration tasks based on their root folders.

To split a Drive into multiple migration tasks, follow these steps:

1. Delete the Drive.
1. Select **Add Drives** from the command bar.
1. In the side panel that appears, select **Multiple specific Drives**.
4. Download and edit the provided .csv template file to divide the user into multiple tasks. For example:
    - `LargeDrive01@contoso.com/folder01`  
    - `LargeDrive01@contoso.com/folder02`  
    - `LargeDrive01@contoso.com/folder03`  
    - `LargeDrive01@contoso.com/folder04` 
5. Save the updated .csv file and upload it to create the divided migration tasks.

## Go to [**Step 3: Copy to migrations**](mm-Google-step3-copy-to-migrations.md)
