---
ms.date: 03/24/2025
title: "Step 6: Migrate and monitor Box migration"
ms.reviewer: 
ms.author: heidip
author: MicrosoftHeidi
manager: jtremper
audience: ITPro
f1.keywords:
- NOCSH
ms.topic: upgrade-and-migration-article
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
description: "Step 6: Migrate and monitor Box migration"
---

# Step 6:  Migrate and monitor your Box migration

Once you review the accounts, confirm the destinations, and correctly map identities, you're ready to migrate.

>[!Important]
>We strongly recommend that you don't rename or move migrated files before the final migration has been completed. Doing so results in files being overwritten.

1. Select the accounts to migrate.

![Select accounts to migrate](media/mm-box-select-to-migrate.png)

2. Select **Migrate**.
3. A confirmation step displays. Click **Migrate**.

>[!Note]
> Starting your migration only copies content from your Box account to the location you specified in Microsoft 365. Make sure the destinations are correct, as once the migration starts, they can't be modified.

4. Once the migration begins, monitor the migration status, and the table summary at the top. Depending on how large your migration, this step may take hours or days.

## How many task rows can I run at once?

At a maximum, only 50 task rows can run simultaneously. This total includes both scanning and migrating. If you select more than that total combined number and start scanning or migrating, only 50 randomly chosen rows are going to run. The rest of the tasks are going to be queued.

As a task row completes, another from the queue starts migrating or scanning automatically. While the maximum number of task rows allowed is set to 50, if a migration experiences any slowdowns or back-off requests, it may drop lower than this number to keep the migration stable.
