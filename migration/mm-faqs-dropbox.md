---
ms.date: 03/18/2021
title: "Migration Manager Dropbox FAQs"
ms.reviewer: 
ms.author: heidip
author: MicrosoftHeidi
manager: jtremper
recommendations: true
audience: ITPro
f1.keywords:
- NOCSH
ms.topic: faq
ms.service: microsoft-365-migration
ms.localizationpriority: high
ms.collection: 
- M365-collaboration
- SPMigration
- m365initiative-migratetom365
search.appverid: MET150
description: Migration Manager Dropbox FAQs
---

# Frequently Asked Questions: Migration Manager Dropbox


**Question:**  **Is Migration Manager Dropbox available for GCC, GCCHigh, DoD tenants?**</br>
Answer:  For the latest updates, refer to [specialty environments support](mm-specialty-environments-support.md).
</br>

**Question:**   **What gets transferred?**</br>
Answer: Only owned folders and the root files for each user are copied. If a user isn't the owner of data they can access, we don't copy it. Content may be automatically reshared after migration, ensuring that each user retains access to their content exactly as before.
</br>

**Question:**   **Does Migration Manager sync files from Dropbox after first migration?**</br>
Answer: After completing a migration task for the first time, triggering the **Migrate** button again will initiate a delta sync (incremental migration run). During this process, the destination directory is compared to the source, and only new or modified files are transferred. Here are a few examples of how we deal with changes to files and folders.

- **Content changes**: If a document is edited in the source, it will be copied to the destination during the next incremental run, replacing the previous versions. If new files are added in the source, they'll also be migrated in the next incremental run.

- **Name changes**: If the name of a file or folder changes in Office 365, we treat it as a brand new object. This change can lead to duplicate files being migrated to Office 365, or worse in that entire folders worth of data would be duplicated from the changed folder downwards.

- **Example**: Changing the path `/Sales/Clients` to `/Global Sales/Clients` results in two copies of your `Sales` folder after the `Global Sales` folder is also copied during an incremental pass.
</br>

**Question:**   **Can I rearrange content during a migration?**</br>
Answer:  Not recommended. Any major changes in directory structure should happen before or after your migration. It's also not a good idea to use our app to rearrange content.  The risks that come with rearranging content during the migration are primarily in the form of data duplication; our incremental process sees all changes as new data. So, for example, if you change a folder name at the root, we detect that as a new folder, and all of the contents is retransferred, including all subfolders.  When sharing permissions are transferred, both owners and collaborators receive duplicate data if content has been rearranged or renamed.
</br>

**Question:**   **What happens to external sharing links?**</br>
Answer:  We don't recreate external sharing links. After migration, these have to be set in the destination manually.</br>

**Question:**   **What about external collaborators?**</br>
Answer:  We don't share content with external collaborators. This policy is in place to protect your organization, and industry best practice is to never automatically share sensitive internal data with external users.</br>

**Question:**   **Does Migration Manager preserve file versions?**</br>
Answer:  No. During a migration, only the most recent version of a file is transferred.</br>

**Question:**   **Does Migration Manager automatically notify users?**</br>
Answer:  No.  We automatically suppress all emails to users so they aren't bombarded with excessive notifications about the data they now have access to.</br>

**Question:**   **Why I can’t see some of my SharePoint sites while assigning destinations on the UI?**</br>
Answer: If SharePoint or Teams sites in your tenant aren't visible on the UI while assigning destinations, there could be a few reasons:
- SharePoint admins only see sites where they are at least a member, as sites are searched using a user-scoped delegated token.
- Admins might not see sites for a multi-geo tenant due to limitations in the graph API.
- Recently created sites might take a couple of hours to sync and appear on the UI.
- For some corner cases (e.g., special characters in the destination path), SharePoint site search on the UI might not work.
</br>
