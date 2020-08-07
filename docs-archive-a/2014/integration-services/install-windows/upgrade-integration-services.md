---
title: Durchführen eines Upgrades für Integration Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services, upgrading
- SSIS, upgrading
- SQL Server Integration Services, upgrading
- upgrading Integration Services
ms.assetid: 04f9863c-ba0b-47c5-af91-f2d41b078a23
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2229dfceee00d7818e22c909f01d8261542d39cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619908"
---
# <a name="upgrade-integration-services"></a>Upgrade von Integration Services
  Wenn [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] oder [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] derzeit auf Ihrem Computer installiert ist, können Sie auf [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] aktualisieren.  
  
 Wenn Sie einen Computer, auf dem eine dieser früheren Versionen von [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] installiert ist, auf [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] aktualisieren, wird [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] parallel zur früheren Version installiert.  
  
 Durch diese parallele Installation werden mehrere Versionen des Hilfsprogramms dtexec installiert. Um sicherzustellen, dass Sie die korrekte Version des Hilfsprogramms ausführen, führen Sie das Hilfsprogramm an der Eingabeaufforderung aus, indem Sie den vollständigen Pfad (\<drive>:\Programme\Microsoft SQL Server\\<Version\>\DTS\Binn) eingeben. Weitere Informationen zu dtexec finden Sie unter [dtexec (Hilfsprogramm)](../packages/dtexec-utility.md).  
  
> [!NOTE]  
>  In vorherigen Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hatten alle Benutzer in der Gruppe Benutzer standardmäßig Zugriff auf den Dienst [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , wenn Sie [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installiert haben. Wenn Sie [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]installieren, haben Benutzer keinen Zugriff auf den Dienst [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Der Dienst ist standardmäßig sicher. Nach der Installation von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] muss der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Administrator das DCOM-Konfigurationstool (Dcomcnfg.exe) ausführen, um einzelnen Benutzern den Zugriff auf den Dienst [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] zu gewähren. Weitere Informationen finden Sie unter [Grant Permissions to Integration Services Service](../grant-permissions-to-integration-services-service.md).  
  
## <a name="before-upgrading-integration-services"></a>Vor dem Upgrade von Integration Services  
 Es wird empfohlen, Upgrade Advisor auszuführen, bevor Sie auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]aktualisieren. Der Upgrade Advisor meldet Probleme, die auftreten können, wenn Sie vorhandene [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Pakete auf das neue Paketformat migrieren, das von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] verwendet wird. Weitere Informationen finden Sie unter [Use Upgrade Advisor to Prepare for Upgrades](../../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).  
  
> [!NOTE]
>  Die Unterstützung für das Migrieren oder Ausführen von DTS-Paketen (Data Transformation Services) wurde in der aktuellen Version von nicht mehr unterstützt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Folgende DTS-Funktionen werden nicht mehr unterstützt:  
> 
>  -   DTS-Laufzeit  
> -   DTS-API  
> -   Paketmigrations-Assistent zum Migrieren von DTS-Paketen zur nächsten Version von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
> -   Unterstützung der DTS-Paketverwaltung in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
> -   DTS 2000-Paket ausführen (Task)  
> -   Scannen von DTS-Paketen durch den Upgrade Advisor  
> 
>  Informationen zu anderen nicht mehr unterstützten Funktionen finden Sie unter nicht mehr [unterstützte Integration Services Funktionen in SQL Server 2014](../discontinued-integration-services-functionality-in-sql-server-2014.md).  
  
## <a name="upgrading-integration-services"></a>Aktualisieren von Integration Services  
 Verwenden Sie für das Upgrade eine der folgenden Methoden:  
  
-   Führen [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Sie das-Setup aus, und wählen Sie die Option zum **Aktualisieren von SQL Server 2005, SQL Server 2008 oder SQL Server 2008 R2 oder aus** **[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]** .  
  
-   Führen Sie **setup.exe** an der Eingabeaufforderung aus, und geben Sie die `/ACTION=upgrade` Option an. Weitere Informationen finden Sie im Abschnitt "Installations Skripts für [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] " in [Install SQL Server 2014 von der Eingabeaufforderung](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
 Mit der Upgradefunktion können Sie folgende Aktionen nicht ausführen:  
  
-   Neukonfigurieren einer vorhandenen Installation von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
-   Umstellen von einer 32-Bit- auf eine 64-Bit-Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder von einer 64-Bit-Version auf eine 32-Bit-Version.  
  
-   Umstellen von einer lokalisierten Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf eine andere lokalisierte Version.  
  
 Beim Upgrade können Sie sowohl [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] als auch [!INCLUDE[ssDE](../../includes/ssde-md.md)], nur [!INCLUDE[ssDE](../../includes/ssde-md.md)]oder nur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]aktualisieren. Wenn Sie nur [!INCLUDE[ssDE](../../includes/ssde-md.md)] aktualisieren, bleibt [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] bzw. [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] funktionsbereit, Sie verfügen jedoch nicht über die Funktionalität von [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)]. Wenn Sie nur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]aktualisieren, ist [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] voll funktionsbereit, kann jedoch nur Pakete im Dateisystem speichern, es sei denn, auf einem anderen Computer ist eine Instanz von [!INCLUDE[ssDECurrent](../../includes/ssdecurrent-md.md)] verfügbar.  
  
## <a name="upgrading-both-integration-services-and-the-database-engine-to-sscurrent"></a>Aktualisieren von Integration Services und Datenbank-Engine auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 In diesem Abschnitt werden die Auswirkungen eines Upgrades mit folgenden Kriterien beschrieben:  
  
-   Sie aktualisieren sowohl [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] als auch eine Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] und die Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] befinden sich auf dem gleichen Computer.  
  
### <a name="what-the-upgrade-process-does"></a>Umfang des Upgradevorgangs  
 Der Upgradevorgang führt folgende Aufgaben aus:  
  
-   Installiert die Dateien, den Dienst und die Tools von [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] ([!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] und [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]). Wenn es mehrere Instanzen von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] auf demselben Computer gibt, werden beim ersten Upgrade der Instanzen auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] die Dateien, der Dienst und die Tools von [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] installiert.  
  
-   Aktualisiert die Instanz von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] auf die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Version.  
  
-   Verschiebt Daten aus den- [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] oder- [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] Systemtabellen in die- [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] Systemtabellen wie folgt:  
  
    -   Verschiebt Pakete ohne Änderung von der Systemtabelle msdb.dbo.sysdtspackages90 in die Systemtabelle msdb.dbo.sysssispackages.  
  
        > [!NOTE]  
        >  Obwohl die Daten in eine andere Systemtabelle verschoben werden, werden die Pakete durch den Upgradevorgang nicht auf das neue Format migriert.  
  
    -   Verschiebt Ordnermetadaten von der Systemtabelle msdb.sysdtsfolders90 in die Systemtabelle msdb.sysssisfolders.  
  
    -   Verschiebt Protokolldaten von der Systemtabelle msdb.sysdtslog90 in die Systemtabelle msdb.sysssislog.  
  
-   Entfernt die Systemtabellen msdb.sysdts*90 und die gespeicherten Prozeduren, die für den Zugriff verwendet werden, nachdem die Daten in die neuen Tabellen msdb.sysssis\* verschoben wurden. Das Upgrade ersetzt jedoch die sysdtslog90-Tabelle durch eine Sicht, die auch sysdtslog90 genannt wird. Diese neue sysdtslog90-Sicht macht die neue Systemtabelle msdb.sysssislog verfügbar. So kann sichergestellt werden, dass auf der Protokolltabelle basierende Berichte weiterhin ohne Unterbrechung ausgeführt werden.  
  
-   Zum Steuern des Paketzugriffs werden drei neue feste Rollen auf Datenbankebene erstellt: db_ssisadmin, db_ssisltduser und db_ssisoperator. Die [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Rollen von db_dtsadmin, db_dtsltduser und db_dtsoperator werden nicht entfernt, sondern werden Member der entsprechenden neuen Rollen.  
  
-   Wenn der-Paket Speicher (d. h. [!INCLUDE[ssIS](../../includes/ssis-md.md)] der vom-Dienst verwaltete Dateisystem-Speicherort [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ) der Standard Speicherort unter **\SQL Server\90**, **\SQL Server\100**oder **\SQL server\110** ist, werden diese Pakete an den neuen Standard Speicherort unter **\SQL server\120**verschoben.  
  
-   Aktualisiert die [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Dienstkonfigurationsdatei so, dass sie auf die aktualisierte [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz verweist.  
  
### <a name="what-the-upgrade-process-does-not-do"></a>Nicht im Umfang des Upgradevorgangs enthaltene Aufgaben  
 Der Upgradevorgang führt folgende Aufgaben nicht aus:  
  
-   Der-Dienst oder der-Dienst **wird nicht** von entfernt [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] .  
  
-   Vorhandene [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Pakete werden nicht auf das neue Paketformat migriert, das von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] verwendet wird. Informationen zum Migrieren von Paketen finden Sie unter [Aktualisieren von Integration Services-Paketen](upgrade-integration-services-packages.md).  
  
-   Außer vom Standardspeicherort werden Pakete nicht von Speicherorten im Dateisystem verschoben, die zur Dienstkonfigurationsdatei hinzugefügt wurden. Falls Sie zuvor die Dienstkonfigurationsdatei bearbeitet haben, um weitere Dateisystemordner hinzuzufügen, werden in diesen Ordnern gespeicherte Pakete nicht an einen neuen Speicherort verschoben.  
  
-   In Auftragsschritten des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents, die das Hilfsprogramm **dtexec** (dtexec.exe) direkt aufrufen, wird der Dateisystempfad für das Hilfsprogramm **dtexec** nicht aktualisiert. Sie müssen diese Auftragsschritte manuell bearbeiten, um den Dateisystempfad zu aktualisieren, um den [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Speicherort für das Hilfsprogramm **dtexec** anzugeben.  
  
### <a name="what-you-can-do-after-upgrading"></a>Optionen nach dem Upgrade  
 Nach Beendigung des Upgradevorgangs können Sie die folgenden Aufgaben ausführen:  
  
-   Führen Sie Aufträge des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents aus, die Pakete ausführen.  
  
-   Verwenden [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] Sie, um Pakete zu verwalten [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , die in einer Instanz von oder gespeichert sind [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Sie müssen jedoch die Dienstkonfigurationsdatei ändern, um die Instanz von [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] der Liste der von dem Dienst verwalteten Speicherorte hinzuzufügen.  
  
    > [!NOTE]  
    >  Frühere Versionen von [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] können keine Verbindung mit dem [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] -Dienst herstellen.  
  
-   Stellen Sie anhand des Werts in der Spalte „PackageFormat“ fest, welche Version die Pakete der Systemtabelle msdb.dbo.sysssispackages haben. Mit der in der Tabelle enthaltenen PackageFormat-Spalte wird die Version der einzelnen Pakete identifiziert. Der Wert 2 in der Spalte PackageFormat kennzeichnet ein [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)]-Paket, der Wert 3 ein [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)]-Paket. Der Wert in der Spalte PackageFormat ändert sich erst, wenn Sie Pakete auf das neue Paketformat migrieren.  
  
-   Sie können- [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder- [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Tools nicht zum Entwerfen, ausführen oder Verwalten von- [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Paketen verwenden. Die Tools von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] schließen die entsprechenden Versionen von [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Import/Export-Assistenten und das Paketausführungsprogramm (dtexecui.exe) ein. Beim Upgradevorgang werden die [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Tools oder nicht entfernt [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] . Sie können diese Tools jedoch nicht verwenden, um mit [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] oder [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)]-Paketen auf einem Server weiter zu arbeiten, der aktualisiert wurde.  
  
-   Bei einer Upgradeinstallation wird [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] standardmäßig so konfiguriert, dass Ereignisse im Zusammenhang mit der Ausführung von Paketen im Anwendungsereignisprotokoll protokolliert werden. Diese Einstellung generiert möglicherweise zu viele Ereignisprotokolleinträge, wenn Sie die Datensammler-Funktion von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]verwenden. Zu den protokollierten Ereignissen gehören EventID 12288 "Paket wurde gestartet" und EventID 12289 "Paket wurde erfolgreich beendet". Um diese beiden Ereignisse nicht mehr im Anwendungsereignisprotokoll zu protokollieren, öffnen Sie die Registrierung zum Bearbeiten. Suchen Sie anschließend in der Registrierung den Knoten HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\SSIS, und ändern Sie den Wert DWORD der Einstellung LogPackageExecutionToEventLog von 1 auf 0.  
  
## <a name="upgrading-only-the-database-engine-to-sscurrent"></a>Upgrade ausschließlich der Datenbank-Engine auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 In diesem Abschnitt werden die Auswirkungen eines Upgrades mit folgenden Kriterien beschrieben:  
  
-   Sie aktualisieren nur eine Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Das heißt, die [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz ist nun eine Instanz von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], doch die Instanz von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] und die Clienttools stammen aus [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] bzw. [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
-   Die [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz befindet sich auf einem Computer und [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] und die Clienttools befinden sich auf einem anderen Computer.  
  
### <a name="what-you-can-do-after-upgrading"></a>Optionen nach dem Upgrade  
 Die Systemtabellen, in denen Pakete in der aktualisierten [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz gespeichert werden, sind nicht mit den in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] verwendeten Systemtabellen identisch. Daher können die [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] -oder-Versionen von [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] und [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] die Pakete in den Systemtabellen der aktualisierten Instanz von nicht ermitteln [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Da diese Pakete nicht ermittelt werden können, bestehen Einschränkungen hinsichtlich der Verwendung dieser Pakete:  
  
-   Sie können die [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]- bzw. [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]-Tools, [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] und [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] nicht auf anderen Computern zum Laden oder Verwalten von Paketen aus der aktualisierten [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz verwenden.  
  
    > [!NOTE]  
    >  Obwohl die Pakete in der aktualisierten [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz noch nicht auf das neue Paketformat migriert wurden, können sie von den [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]- bzw. [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]-Tools nicht ermittelt werden. Daher können die Pakete von den [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]- bzw. [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]-Tools nicht verwendet werden.  
  
-   Sie können [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] oder nicht [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] auf anderen Computern verwenden, um Pakete auszuführen, die in der aktualisierten Instanz von in der msdb-Datenbank gespeichert sind [!INCLUDE[ssDE](../../includes/ssde-md.md)] .  
  
-   Sie können Aufträge des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agents nicht auf [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]- oder [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]-Computern verwenden, um [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)]- oder [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)]-Pakete auszuführen, die in der aktualisierten [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz gespeichert werden.  
  
## <a name="external-resources"></a>Externe Ressourcen  
 Blogeintrag [Weiterverwenden benutzerdefinierter SSIS-Erweiterungen und -Anwendungen in Denali](https://go.microsoft.com/fwlink/?LinkId=238157) auf blogs.msdn.com.  
  
  
