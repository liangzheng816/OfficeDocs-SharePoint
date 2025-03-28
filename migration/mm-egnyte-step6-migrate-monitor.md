---
ms.date: 03/27/2025
title: "Step 6: Migrate and monitor Egnyte migration"
ms.reviewer: 
ms.author: heidip
author: MicrosoftHeidi
manager: jtremper
audience: ITPro
f1.keywords:
- NOCSH
ms.topic: article
ms.service: microsoft-365-migration
ms.localizationpriority: medium
ms.collection: 
- m365solution-migratefileshares
- m365solution-migratetom365
- m365solution-scenario
- M365-collaboration
- SPMigration
- highpri
- m365initiative-migratetom365
search.appverid: MET150
ROBOTS: NOINDEX
description: "Step 6: Migrate and monitor Egnyte migration"
---
# Step 6:  Migrate and monitor your Egnyte migration

Once you review the accounts, confirm the destinations, and correctly map identities, you're ready to migrate.

>[!Important]
>We strongly recommend you don't rename or move migrated files before the final migration has been completed. Doing so results in files being overwritten.

1. Select the accounts to migrate.
2. Select **Migrate**.

![Select migrate button.](media/mm-box-migrate-button.png) 

3. A confirmation step displays. Select **Migrate**.

>[!Note]
> Starting your migration only copies content from your Egnyte account to the location you have specified in Microsoft 365. Make sure the destinations are correct. Once migration starts, they can't be modified.

4. Once the migration starts, monitor the migration status, and the table summary at the top. Depending on how large your migration, this step can take hours or days.

## How many task rows can I run at once?

At a maximum, only 50 task rows can run simultaneously. This total includes both scanning and migrating.

If you select more than that total combined number and start scanning or migrating, only 50 randomly chosen rows run. The remaining rows are queued.

As a task row completes, another from the queue starts migrating or scanning automatically. The maximum allowed is 50 task rows. However, if a migration experiences any slowdowns or back-off requests, it can drop lower than this number to keep the migration stable.
