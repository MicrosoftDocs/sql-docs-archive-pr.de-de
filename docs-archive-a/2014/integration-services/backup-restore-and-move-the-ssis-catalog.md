---
title: Sichern, wiederherstellen und Verschieben des SSIS-Katalogs | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: bf806aef-8556-48ab-aed5-e95de9a2204e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f9de552ddd54168f516f42d9988302561616fd65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87616661"
---
# <a name="backup-restore-and-move-the-ssis-catalog"></a>Sichern, Wiederherstellen und Verschieben des SSIS-Katalogs
  [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] schließt die SSISDB-Datenbank ein. Sie können Sichten in der SSISDB-Datenbank abfragen, um im **SSISDB** -Katalog gespeicherte Objekte, Einstellungen und operative Daten zu überprüfen. Dieses Thema enthält Anweisungen zum Sichern und Wiederherstellen der Datenbank.  
  
 Der **SSISDB**-Katalog speichert die Pakete, die Sie auf dem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Server bereitgestellt haben. Weitere Informationen zum Katalog finden Sie unter [SSIS-Katalog](catalog/ssis-catalog.md).  
  
##  <a name="to-back-up-the-ssis-database"></a><a name="backup"></a> So sichern Sie die SSIS-Datenbank  
  
1.  Öffnen Sie [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] , und stellen Sie eine Verbindung zu einer Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]her.  
  
2.  Sichern Sie den Hauptschlüssel für die SSISDB-Datenbank, indem Sie die Anweisung BACKUP MASTER KEY (Transact-SQL) verwenden. Der Schlüssel wird in einer von Ihnen angegebenen Datei gespeichert. Verwenden Sie ein Kennwort, um den Hauptschlüssel in der Datei zu verschlüsseln.  
  
     Weitere Informationen zur Anweisung finden Sie unter [BACKUP MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-master-key-transact-sql).  
  
     Im folgenden Beispiel wird der Hauptschlüssel in die Datei `c:\temp directory\RCTestInstKey` exportiert. Das `LS2Setup!` -Kennwort wird zum Verschlüsseln des Hauptschlüssels verwendet.  
  
    ```  
    backup master key to file = 'c:\temp\RCTestInstKey'  
           encryption by password = 'LS2Setup!'  
  
    ```  
  
3.  Sichern Sie die SSISDB-Datenbank mit dem Dialogfeld **Datenbank sichern** in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Weitere Informationen finden Sie unter [Vorgehensweise: Sichern einer Datenbank (SQL Server Management Studio)](https://go.microsoft.com/fwlink/?LinkId=231812).  
  
4.  Generieren Sie das CREATE LOGIN-Skript für ##MS_SSISServerCleanupJobLogin ##, indem Sie wie folgt vorgehen. Weitere Informationen finden Sie unter [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql).  
  
    1.  Erweitern Sie in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]im Objekt-Explorer die Knoten **Sicherheit** und **Anmeldungen** .  
  
    2.  Klicken Sie mit der rechten Maustaste auf **##MS_SSISServerCleanupJobLogin##** , und klicken Sie dann auf **Skript für Anmeldenamen als** > **CREATE in** > **Neues Abfrage-Editor-Fenster**.  
  
5.  Wenn Sie die SSISDB-Datenbank auf einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz wiederherstellen, auf der der SSISDB-Katalog nie erstellt wurde, generieren Sie das CREATE PROCEDURE-Skript wie folgt für sp_ssis_startup. Weitere Informationen finden Sie unter [CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql).  
  
    1.  Erweitern Sie in Objekt-Explorer den Knoten **Datenbanken** , und erweitern Sie dann den Knoten **System Datenbanken**  >  **Master**  >  **Programmierbarkeit**  >  **gespeicherte Prozeduren** .  
  
    2.  Klicken Sie mit der rechten Maustaste auf **dbo.sp_ssis_startup**, und klicken Sie dann auf **Skript für gespeicherte Prozeduren als** > **CREATE in** > **Neues Abfrage-Editor-Fenster**.  
  
6.  Bestätigen Sie, dass der SQL Server-Agent gestartet wurde.  
  
7.  Wenn Sie die SSISDB-Datenbank auf einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz wiederherstellen, auf der der SSISDB-Katalog nie erstellt wurde, generieren Sie wie folgt ein Skript für den SSIS-Server-Wartungsauftrag. Das Skript wird bei Erstellung des SSISDB-Katalogs automatisch im [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent erstellt. Der Auftrag hilft beim Bereinigen von Bereinigungsvorgangsprotokollen außerhalb der Beibehaltungsdauer und entfernt ältere Projektversionen.  
  
    1.  Erweitern Sie im Objekt-Explorer den Knoten **SQL Server-Agent** und dann den Knoten **Aufträge** .  
  
    2.  Klicken Sie mit der rechten Maustaste auf SSIS-Server Wartungsauftrag, und klicken Sie dann auf **Skript für Auftrag als**  >  **Create to**  >  **New Query Editor Window**  
  
### <a name="to-restore-the-ssis-database"></a>So stellen Sie die SSIS-Datenbank wieder her  
  
1.  Wenn Sie die SSISDB-Datenbank auf einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz wiederherstellen, auf der der SSISDB-Katalog nie erstellt wurde, aktivieren Sie Common Language Runtime (clr), indem Sie die gespeicherte Prozedur sp_configure ausführen. Weitere Informationen finden Sie unter [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) und [CLR-fähig (Option)](https://go.microsoft.com/fwlink/?LinkId=231855).  
  
    ```  
    use master   
           sp_configure 'clr enabled', 1  
           reconfigure  
  
    ```  
  
2.  Wenn Sie die SSISDB-Datenbank auf einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz wiederherstellen, auf der der SSISDB-Katalog nie erstellt wurde, erstellen Sie den asymmetrischen Schlüssel und den Anmeldenamen aus dem asymmetrischen Schlüssel, und gewähren Sie dem Anmeldenamen die UNSAFE-Berechtigung.  
  
    ```  
    Create Asymmetric key MS_SQLEnableSystemAssemblyLoadingKey  
           FROM Executable File = 'C:\Program Files\Microsoft SQL Server\110\DTS\Binn\Microsoft.SqlServer.IntegrationServices.Server.dll'  
  
    ```  
  
     [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -CLR-gespeicherte Prozeduren erfordern UNSAFE-Berechtigungen, die der Anmeldung gewährt werden müssen, da die Anmeldung einen zusätzlichen Zugriff auf eingeschränkte Ressourcen (z. B. die Microsoft Win32-API) benötigt. Weitere Informationen zur UNSAFE-Codeberechtigung finden Sie unter [Creating an Assembly](../relational-databases/clr-integration/assemblies/creating-an-assembly.md).  
  
    ```  
    Create Login MS_SQLEnableSystemAssemblyLoadingUser  
           FROM Asymmetric key MS_SQLEnableSystemAssemblyLoadingKey   
  
           Grant unsafe Assembly to MS_SQLEnableSystemAssemblyLoadingUser  
  
    ```  
  
3.  Stellen Sie die SSISDB-Datenbank über die Sicherung wieder her. Verwenden Sie dazu das Dialogfeld **Datenbank wiederherstellen** in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Weitere Informationen finden Sie in den nachfolgenden Themen.  
  
    -   [Datenbank wiederherstellen &#40;Seite „Allgemein“&#41;](general-page-of-integration-services-designers-options.md)  
  
    -   [Datenbank wiederherstellen &#40;Seite Dateien&#41;](../relational-databases/backup-restore/restore-database-files-page.md)  
  
    -   [Datenbank wiederherstellen &#40;Seite Optionen&#41;](../relational-databases/backup-restore/restore-database-options-page.md)  
  
4.  Führen Sie die Skripts aus, die Sie in [So sichern Sie die SSIS-Datenbank](#backup) für ##MS_SSISServerCleanupJobLogin##, sp_ssis_startup und den SSIS-Serverwartungsauftrag erstellt haben. Bestätigen Sie, dass der SQL Server-Agent gestartet wurde.  
  
5.  Führen Sie die folgende Anweisung aus, um die Prozedur "sp_ssis_startup" für die automatische Ausführung festzulegen. Weitere Informationen finden Sie unter [sp_procoption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql).  
  
    ```  
    EXEC sp_procoption N'sp_ssis_startup','startup','on'  
    ```  
  
6.  Ordnen Sie den SSISDB-Benutzer ##MS_SSISServerCleanupJobUser## (SSISDB-Datenbank) ##MS_SSISServerCleanupJobLogin## zu, indem Sie das Dialogfeld **Anmeldungseigenschaften** in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]verwenden.  
  
7.  Verwenden Sie zum Sichern des Hauptschlüssels eine der folgenden Methoden. Weitere Informationen zur Verschlüsselung finden Sie unter [Encryption Hierarchy](../relational-databases/security/encryption/encryption-hierarchy.md).  
  
    -   **Methode 1:**  
  
         Verwenden Sie diese Methode, wenn Sie bereits eine Sicherung des Datenbank-Hauptschlüssels ausgeführt haben und Sie über das Kennwort verfügen, das verwendet wurde, um den Hauptschlüssel zu verschlüsseln.  
  
        ```  
               Restore master key from file = 'c:\temp\RCTestInstKey'  
               Decryption by password = 'LS2Setup!' -- 'Password used to encrypt the master key during SSISDB backup'  
               Encryption by password = 'LS3Setup!' -- 'New Password'  
               Force  
  
        ```  
  
        > [!NOTE]  
        >  Bestätigen Sie, dass das [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Dienstkonto über Berechtigungen verfügt, die Sicherungsschlüsseldatei zu lesen.  
  
        > [!NOTE]  
        >  Es wird die folgende Warnmeldung in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] angezeigt, wenn der Datenbank-Hauptschlüssel noch nicht vom Diensthauptschlüssel verschlüsselt wurde. Ignorieren Sie die Warnmeldung.  
        >   
        >  **Der aktuelle Hauptschlüssel kann nicht entschlüsselt werden. Dieser Fehler wurde ignoriert, weil die Option FORCE angegeben war.**  
        >   
        >  Das FORCE-Argument gibt an, dass der Wiederherstellungsprozess fortfahren sollte, auch wenn der aktuelle Datenbank-Hauptschlüssel nicht geöffnet ist. Diese Meldung wird für den SSISDB-Katalog angezeigt, da der Datenbank-Hauptschlüssel noch nicht auf der Instanz geöffnet wurde, auf der Sie die Datenbank wiederherstellen.  
  
    -   **Methode 2:**  
  
         Verwenden Sie diese Methode, wenn Sie über das ursprüngliche Kennwort verfügen, das verwendet wurde, um SSISDB zu erstellen.  
  
        ```  
        open master key decryption by password = 'LS1Setup!' --'Password used when creating SSISDB'  
               Alter Master Key Add encryption by Service Master Key  
        ```  
  
8.  Bestimmen Sie, ob das SSISDB-Katalogschema und die [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Binärdateien (ISServerExec-Assembly und SQLCLR-Assembly) kompatibel sind, indem Sie [catalog.check_schema_version](/sql/integration-services/system-stored-procedures/catalog-check-schema-version)ausführen.  
  
9. Um zu bestätigen, dass die SSISDB-Datenbank erfolgreich wiederhergestellt wurde, führen Sie Vorgänge für den SSISDB-Katalog aus, beispielsweise das Ausführen von Paketen, die auf dem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Server bereitgestellt wurden. Weitere Informationen finden Sie unter [Ausführen eines Pakets auf dem SSIS-Server mit SQL Server Management Studio](run-a-package-on-the-ssis-server-using-sql-server-management-studio.md).  
  
### <a name="to-move-the-ssis-database"></a>So verschieben Sie die SSIS-Datenbank  
  
-   Folgen Sie den Anweisungen zum Verschieben von Benutzerdatenbanken. Weitere Informationen finden Sie unter [Move User Databases](../relational-databases/databases/move-user-databases.md).  
  
     Stellen Sie sicher, dass Sie den Hauptschlüssel für die SSISDB-Datenbank sichern und die Sicherungsdatei schützen. Weitere Informationen finden Sie unter [So sichern Sie die SSIS-Datenbank](#backup).  
  
     Stellen Sie sicher, dass die für Integration Services (SSIS) relevanten Objekte in der neuen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz erstellt werden, auf der der SSISDB-Katalog noch nicht erstellt wurde.  
  
  
