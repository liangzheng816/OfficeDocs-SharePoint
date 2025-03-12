---
ms.date: 03/11/2025
title: "Migration Manager Google FAQs"
ms.reviewer: 
ms.author: heidip
author: MicrosoftHeidi
manager: jtremper
recommendations: true
audience: ITPro
f1.keywords:
- NOCSH
ms.topic: article
ms.service: microsoft-365-migration
ms.localizationpriority: high
ms.collection: 
- M365-collaboration
- SPMigration
- m365initiative-migratetom365
search.appverid: MET150
description: Migration Manager Google FAQs
---

# Frequently Asked Questions: Migration Manager Google

**Question:**   **Are there any other tools available to migrate my Google accounts?**</br>
Answer. Currently, Migration Manager is the tool to use to for migrating Google content.

**Question:**   **What gets transferred?**</br>
Answer: Only owned folders and the root files for each user are copied. If a user isn't the owner of data they can access, we don't copy it. Content may be automatically reshared after migration, ensuring that each user retains access to their content exactly as before.
</br>

**Question:**   **Does Migration Manager sync files from Google after first migration?**</br>
Answer: After completing a migration task for the first time, triggering the **Migrate** button again will initiate a delta sync (incremental migration run). During this process, the destination directory is compared to the source, and only new or modified files are transferred. Here are a few examples of how we deal with changes to files and folders.

- **Content changes**: If a document is edited in the source, it will be copied to the destination during the next incremental run, replacing the previous versions. If new files are added in the source, they'll also be migrated in the next incremental run.

- **Name changes**: If the name of a file or folder changes in Office 365, we treat it as a brand new object. This change can lead to duplicate files being migrated to Office 365, or worse in that entire folders worth of data would be duplicated from the changed folder downwards.

- **Example**: Changing the path `/Sales/Clients` to `/Global Sales/Clients` results in two copies of your `Sales` folder after the `Global Sales` folder is also copied during an incremental pass.
</br>

**Question:**   **Does Migration Manager delete my files?**</br>
Answer: No. We never delete your data from any source. We take your data from one place and copy it to another; akin to *copy and paste* rather than *cut and paste.* We also don't retain any of your cloud storage data for any reasons. 

</br>

**Question:**   **Can I rearrange content during a migration?**</br>
Answer:  Not recommended. Any major changes in directory structure should happen before or after your migration. It's also not a good idea to use our app to rearrange content. The risks that come with rearranging content during the migration are primarily in the form of data duplication; our incremental process sees all changes as new data. So, for example, if you change a folder name at the root, we detect that as a new folder, and all of the contents is retransferred, including all subfolders. When sharing permissions are transferred, both owners and collaborators receive duplicate data if content is rearranged or renamed.
</br>

**Question:**   **What happens to external sharing links?**</br>
Answer:  We don't recreate external sharing links. After migration, the links have to be set in the destination manually.</br>

**Question:**   **What about external collaborators?**</br>
Answer:  We don't share content with external collaborators. This policy is in place to protect your organization, and industry best practice is to never automatically share sensitive internal data with guests.</br>

**Question:**   **Does Migration Manager preserve file versions?**</br>
Answer: File version migration for Google is partially available and is on its way to GA </br>

**Question:**   **Does Migration Manager automatically notify users?**</br>
Answer:  No.  We automatically suppress all emails to users so they aren't bombarded with excessive notifications about the data they now have access to.</br>

**Question: Does Migration Manager transfer permissions for shared drives?** </br>
Answer: No. During a migration, we only transfer permissions for user drives. Permissions for shared drives aren't migrated. [Learn how to migrate Google Shared Drives](/sharepointmigration/mm-google-overview#google-shared-drives)

**Question: What can't Migration Manager migrate from Google?** </br>
Answer: Google doesn't allow us to export sites and maps from Google Drive. [Learn more about what isn't migrated](/sharepointmigration/mm-unsupported-files)

**Question: Does Migration Manager migrate Google Forms?** </br>
Answer:  Yes. Migration Manager now migrates Google Forms. Forms destinations are required to make it work. [Learn more about Forms destination editing](/sharepointmigration/mm-google-step4-review-destinations)

**Question: Does Google calculate the size of their proprietary files?** </br>
Answer:  Google only started calculating the size of its proprietary files, including Google Docs, Sheets, Forms, and Slides, on May 2, 2022. Any Google proprietary files created and modified **before** May 2, 2022 don't include file size in the metadata info we get from the API calls. As a result, all Google proprietary files created before May 2, 2022 default to a scanned size of 1 byte and are reported as such in our *ScanSummary report*.

**Question: What happens to the files with the same name in the same folder after they are migrated to Microsoft 365?** </br>
Answer:  Files with the same name are renamed with suffixes (1), (2), etc.

**Question: Does Migration Manager support migrating two Google Drives with the same name?** </br>
Answer:  No, it doesn't. Only the first discovered Drive is migrated.


**Question: Can I migrate Drives with "/" in their names?** </br>
Answer:  No, Google Drive with "/" in its name isn't supported. The **Source location** field in either the scan list or migration list shouldn't include "/", even if you configured invalid character replacement in the Project settings.

**Question:**   **Why I can’t see some of my SharePoint sites while assigning destinations on the UI?**</br>
Answer: If SP or Teams sites in your tenant aren't visible on the UI while assigning destinations, there could be a few reasons:
- SP admins only see sites where they are at least a member, as sites are searched using a user-scoped delegated token.
- Admins might not see sites for a multi-geo tenant due to limitations in the graph API.
- Recently created sites might take a couple of hours to sync and appear on the UI.
- For some corner cases (e.g., special characters in the destination path), SP site search on the UI might not work.
</br>

