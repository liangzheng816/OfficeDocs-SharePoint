---
title: "Transport Layer Security (TLS) 1.3 Support"
ms.reviewer: 
ms.author: serdars
author: serdars
manager: serdars
ms.date: 03/11/2025
audience: ITPro
f1.keywords:
- NOCSH
ms.topic: article
ms.service: sharepoint-server-itpro
ms.localizationpriority: medium
ms.collection:
- IT_Sharepoint_Server
- IT_Sharepoint_Server_Top
- IT_Sharepoint16
ms.assetid: 
description: "This article describes the supported and unsupported components on Transport Layer Security (TLS) protocol version 1.3."
---

# Transport Layer Security (TLS) 1.3 Support

[!INCLUDE[appliesto-xxx-xxx-xxx-SUB-xxx-md](../includes/appliesto-xxx-xxx-xxx-SUB-xxx-md.md)]

SharePoint Server 2019 supports TLS protocol version 1.3 by default. However, to enable end-to-end support for TLS protocol version 1.3 in your SharePoint 2019 environment, you might need to install updates or change configuration settings in the following locations:
  
1. SharePoint servers in your SharePoint farm
    
2. Microsoft SQL Servers in your SharePoint farm
    
3. Client computers used to access your SharePoint sites

TLS 1.3 is the latest version of the TLS encryption protocol. SharePoint Server Subscription Edition by default supports TLS 1.3 when deployed with Windows Server 2022 and 2021-06 Cumulative Update for .NET Framework 3.5, and 4.8 for Microsoft server operating system x64 (KB5003529).

> [!NOTE]
> TLS 1.3 doesn't require any additional configuration and might not support all softwares and systems. Microsoft recommends you to contact your software and hardware administrator to check compatibility of TLS 1.3.
>
> TLS 1.3 isn't available and isn't supported when SharePoint Server Subscription Edition is deployed with earlier versions of Windows Server. Microsoft recommends deploying SharePoint Server Subscription Edition with Windows Server 2022 or higher.

SharePoint Server Subscription Edition adds support for connecting to SQL databases using TLS 1.3 connection encryption, while also remaining backward compatible with previous versions of SQL Server that don't support TLS 1.3 connection encryption. TLS 1.3 is currently supported by SQL Server 2022. SQL Server 2022 and Windows-based applications connecting to it must be running on Windows 11 or Windows Server 2022 (or higher) to be able to use TLS 1.3. 

SharePoint Server Subscription Edition uses [Microsoft.Data.SqlClient version 5.1.4](https://github.com/dotnet/SqlClient/tree/main/release-notes/5.1) for its database connectivity layer.

## Support for Tabular Data Stream (TDS) Version 8.0

SharePoint Server Subscription Edition supports TDS 8.0 while also remaining backward compatible with previous versions of SQL Server that don't support TDS 8.0. TDS 8.0 is currently supported by SQL Server 2022, Azure SQL Database, and Azure SQL Managed Instance.
 
TDS 8.0 supports newer encryption protocols such as TLS 1.3 that older versions of TDS can't support, while maintaining compatibility with older versions of TLS. 

## Database settings

The database connectivity layer has the following properties for each SharePoint database (Microsoft.SharePoint.Administration.SPDatabase). 
1. Encrypt ([Microsoft.Data.SqlClient.SqlConnectionEncryptOption](/dotnet/api/microsoft.data.sqlclient.sqlconnectionencryptoption)) 

    1. Optional: Connection encryption can be used if required by the SQL Server. However, if encryption isn't required by the SQL Server, then no connection encryption is used. The connection is limited to using TDS 7.4. 

    2. Mandatory: Connection encryption must be established with the SQL Server. If connection encryption can't be established, then the connection is blocked. The connection is limited to using TDS 7.4. 

    3. Strict: Connection encryption must be established with the SQL Server and the connection must use TDS 8.0 or higher. If connection encryption using TDS 8.0 or higher can't be established, then the connection is blocked. 

1. HostnameInCert (String): Specifies the hostname in the SSL/TLS server certificate of the SQL Server. SharePoint farm administrators should specify this property if the hostname in the certificate doesn't match the hostname that SharePoint connects to. 

## Behaviors when upgrading a farm with existing databases

Databases that were part of a SharePoint farm will be configured to use **Optional** encryption by default. This is to ensure the SharePoint farm remains compatible with the existing SQL Servers in its farm in case they don't support the newer TDS 8.0 and TLS 1.3 protocols. This means SharePoint will continue to use TDS 7.4 when connecting to those databases. If connection encryption is used to connect to those databases, it will be based on TLS 1.2 or lower. 

## Behaviors when adding a database to a farm 

Databases added to a farm are configured to use **Strict** encryption by default. This is to ensure that SharePoint is in a *secure by default* configuration going forward. This means that SharePoint will only use TDS 8.0 when connecting to these databases. The SQL Servers hosting these databases must support TDS 8.0 and must support connection encryption (including having an appropriate SSL/TLS server certificate configured on the SQL Server). If both the SharePoint server and SQL server support TLS 1.3, then it's used for that connection. Otherwise, a previous TLS version is used. 

New SharePoint farms that are created are configured to use **Strict** encryption by default for all their databases, including the configuration database and Central Administration content database. The same requirements described above apply for these databases. 

## Specifying non-default settings when adding a new database

SharePoint farm administrators have the option to override the default settings when creating a new configuration database. These settings can be specified in both our command line and GUI tools.

### Creating a new configuration database with non-default settings 

- In PowerShell, add the following optional parameters to the `New-SPConfigurationDatabase` cmdlet: 
    ``` 
    -DatabaseConnectionEncryption {Mandatory | Optional | Strict} 
    -DatabaseServerCertificateHostName <String> 
    ```
    For example: 

    ```powershell 
    New-SPConfigurationDatabase -DatabaseName "SharePointConfigDB1" -DatabaseServer "SQL-01" -DatabaseConnectionEncryption "Mandatory" -DatabaseServerCertificateHostName "SQL-01.internal.contoso.com" -Passphrase (ConvertTo-SecureString "MyPassword" -AsPlainText -force) -FarmCredentials (Get-Credential) -LocalServerRole "Application" 
    ``` 

- In PSConfig.exe, add the following optional parameters to the configdb operation: 

    ``` 
    -dbencryption {Mandatory | Optional | Strict} 
    -dbcerthostname <String> 
    ``` 

    For example: 
    ```powershell 
    psconfig.exe -cmd configdb -create -database "SharePointConfigDB1" -server "SQL-01" -dbencryption "Mandatory" -dbcerthostname "SQL01.internal.contoso.com" -passphrase "the_passphrase" -user "DOMAIN\username" -password "the_password" -localserverrole "Application" 
    ```

- In the SharePoint Products Configuration Wizard (PSConfigUI.exe), specify the settings in the **Database connection encryption** and **Database server certificate host name** fields in the configuration database form.
:::image type="content" source="media/config-db-settings.png" alt-text="Screenshot of Configuration Wizard.":::