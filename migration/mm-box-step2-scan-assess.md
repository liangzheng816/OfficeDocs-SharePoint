---
ms.date: 08/03/2023
title: "Step 2: Scan and assess Box accounts using Migration Manager"
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
description: "Step 2:  Scan and assess Box users using Migration Manager."
---

# Step 2: Scan and assess Box users

> [!NOTE]
> "Step 2: Scan and access Box users" can now be skipped to alleviate Box throttling. Once the users (tasks) are added to the Scan list, they can be copied to the Migrations tab instantly for migration operations. Please note that Migration Manager will not discover any possible errors and warnings before migration if the scan process is skipped.

After you connect, scan and assess your Box user accounts.
1. Select **Add users** from the menu bar to choose how to add users:</br> - **All new users** to auto-discover all new users in Box</br>- **Single user** for only one account,  or </br>- **Multiple specific users** to bulk upload users by entering them into a CSV file to upload.
2. Choose to **Automatically start scanning now** or choose to scan later.
3. Select **Add**.
4. Highlight any or all of the accounts and then select **Scan** if you chose not to auto scan earlier.

>[!Important]
> The total number cannot exceed 50,000 tasks.

5. Once the scan is complete, a table summary displays to give you an at-a-glance overview of your users. The summary includes User item counts, migration readiness, and any issues that need attention. 
4. Review the scanned users. Search for specific text, or select a filter to review the list more easily.


## Download reports

Summary and detailed scan reports are available to assist you in troubleshooting. Download the generated reports and logs to investigate any possible issues that might block your migration.

1. Once the scan is complete, select **Download reports** from the menu bar for *summary* reports.

   ![add source paths manually in Box](media/mm-add-source-path.png)
   
2. Highlight a selected Box user, and select **Download scan log**  to download a *detailed* scan report of that user account. </br>

## Managing users who own large amounts of data

Upon completing your scan, download the Scan reports and review/address any large source data owners.

A migration task (Box user) should not exceed 100,000 items or 1 TB of data. To enable faster transfers, users with large data sets should be divided into smaller migration tasks based on their root folders.

To split a user into multiple migration tasks, follow these steps:

1. Delete the user.
1. Select **Add users** from the command bar.
1. In the side panel that appears, select **Multiple specific users**.
4. Download and edit the provided .csv template file to divide the user into multiple tasks. For example:
    - `LargeUser@contoso.com/folder01`  
    - `LargeUser@contoso.com/folder02`  
    - `LargeUser@contoso.com/folder03`  
    - `LargeUser@contoso.com/folder04` 
5. Save the updated .csv file and upload it to create the divided migration tasks.





## [**Step 3: Copy to migrations**](mm-box-step3-copy-to-migrations.md)

