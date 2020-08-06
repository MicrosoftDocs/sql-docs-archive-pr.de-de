---
title: Konfigurieren der erweiterten Einstellungen für DQS-Protokolldateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
helpviewer_keywords:
- log files,advanced settings
- dqs log files,advanced settings
ms.assetid: 1d565748-9759-425c-ae38-4d2032a86868
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ad41b0cac95f9bfe5565ccbac16b0fda3e28ddf6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696097"
---
# <a name="configure-advanced-settings-for-dqs-log-files"></a>Konfigurieren der erweiterten Einstellungen für DQS-Protokolldateien
  In diesem Thema wird beschrieben, wie erweiterte Einstellungen für [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] - und [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Protokolldateien konfiguriert werden, z. B. das Festlegen der maximalen Rolldateigröße für Protokolldateien, das Festlegen des Zeitstempelschemas von Ereignissen usw.  
  
> [!NOTE]  
>  Diese Aktivitäten können nicht mit [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]ausgeführt werden und sind nur für erfahrene Benutzer vorgesehen.  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
  
-   Das Windows-Benutzerkonto muss ein Mitglied der festen Serverrolle "sysadmin" in der SQL Server-Instanz sein, damit Konfigurationseinstellungen in der A_CONFIGURATION-Tabelle in der DQS_MAIN-Datenbank geändert werden können.  
  
-   Sie müssen als Mitglied der Gruppe "Administratoren" auf dem Computer angemeldet sein, auf dem Sie die Datei "DQLog.Client.xml" ändern, um die [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Protokollierungseinstellungen konfigurieren zu können.  
  
##  <a name="configure-data-quality-server-log-settings"></a><a name="DQSServer"></a> Konfigurieren von Data Quality Server-Protokolleinstellungen  
 Die [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] -Protokolleinstellungen sind in einem XML-Format in der Spalte **VALUE** der Zeile **ServerLogging** in der A_CONFIGURATION-Tabelle in der DQS_MAIN-Datenbank vorhanden. Sie können die folgende SQL-Abfrage ausführen, um die Konfigurationsinformationen anzuzeigen:  
  
```sql  
select * from DQS_MAIN.dbo.A_CONFIGURATION where NAME='ServerLogging'; 
```  
  
 Sie müssen die entsprechenden Informationen in der Spalte **VALUE** der Zeile **ServerLogging** aktualisieren, um die Konfigurationseinstellungen für die [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] -Protokollierung zu ändern. In diesem Beispiel aktualisieren wir die [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] -Protokolleinstellungen, um die maximale Rolldateigröße auf 25.000 KB festzulegen (der Standard beträgt 20.000 KB).  
  
1.  Starten Sie Microsoft SQL Server Management Studio, und stellen Sie eine Verbindung mit der entsprechenden SQL Server-Instanz her.  
  
2.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf den Server, und klicken Sie dann auf **Neue Abfrage**.  
  
3.  Geben Sie im Fenster Abfrage-Editor die folgenden SQL-Anweisungen ein:  
  
    ```sql  
    -- Begin the transaction.  
    BEGIN TRAN  
    GO  
    -- set the XML value field for the row with name=ServerLogging  
    update DQS_MAIN.dbo.A_CONFIGURATION   
    set VALUE='<configuration>  
      <configSections>  
        <section name="loggingConfiguration" type="Microsoft.Practices.EnterpriseLibrary.Logging.Configuration.LoggingSettings, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" />  
      </configSections>  
      <loggingConfiguration name="Logging Application Block" tracingEnabled="true" defaultCategory="" logWarningsWhenNoCategoriesMatch="true">  
        <listeners>  
          <add fileName="###REPLACE_THIS_WITH_SQL_SERVER_INSTANCE_LOG_FOLDER_NAME###DQServerLog.###REPLACE_THIS_WITH_SQL_CATALOG_NAME###.log" footer="" formatter="Custom Text Formatter" header="" rollFileExistsBehavior="Increment" rollInterval="None" rollSizeKB="25000" timeStampPattern="yyyy-MM-dd" listenerDataType="Microsoft.Practices.EnterpriseLibrary.Logging.Configuration.RollingFlatFileTraceListenerData, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" traceOutputOptions="None" filter="All" type="Microsoft.Practices.EnterpriseLibrary.Logging.TraceListeners.RollingFlatFileTraceListener, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" name="Rolling Flat File Trace Listener" />  
        </listeners>  
        <formatters>  
          <add template="{timestamp(local)}|[{threadName}]|{dictionary({value}|)}{message}" type="Microsoft.Practices.EnterpriseLibrary.Logging.Formatters.TextFormatter, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" name="Custom Text Formatter" />  
        </formatters>  
        <logFilters>  
          <add enabled="true" type="Microsoft.Practices.EnterpriseLibrary.Logging.Filters.LogEnabledFilter, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" name="LogEnabled Filter" />  
        </logFilters>  
        <categorySources />  
        <specialSources>  
          <allEvents switchValue="All" name="All Events" />  
          <notProcessed switchValue="All" name="Unprocessed Category" />  
          <errors switchValue="All" name="Logging Errors & Warnings">  
            <listeners>  
              <add name="Rolling Flat File Trace Listener" />  
            </listeners>  
          </errors>  
        </specialSources>  
      </loggingConfiguration>  
    </configuration>'  
    WHERE NAME='ServerLogging'  
    GO  
    -- check the result  
    select * from DQS_MAIN.dbo.A_CONFIGURATION where NAME='ServerLogging'  
  
    -- Commit the transaction.  
    COMMIT TRAN  
  
    ```  
  
4.  Drücken Sie F5, um die Anweisungen auszuführen. Überprüfen Sie im **Ergebnis** Bereich, ob die Anweisungen erfolgreich ausgeführt wurden.  
  
5.  Um Änderungen an der Konfiguration der [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] -Protokollierung zu übernehmen, müssen Sie die folgenden Transact-SQL-Anweisungen ausführen. Öffnen Sie ein neues Abfrage-Editor-Fenster, und fügen Sie die folgenden Transact-SQL-Anweisungen ein:  
  
    ```sql  
    USE [DQS_MAIN]  
    GO  
    DECLARE @return_value int  
    EXEC @return_value = [internal_core].[RefreshLogSettings]  
    SELECT 'Return Value' = @return_value  
    GO  
    ```  
  
6.  Drücken Sie F5, um die Anweisungen auszuführen. Überprüfen Sie im **Ergebnis** Bereich, ob die Anweisungen erfolgreich ausgeführt wurden.  
  
> [!NOTE]  
>  Die Konfiguration der [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]-Protokolleinstellungen wird dynamisch generiert und in der DQS_MAIN.Log-Datei gespeichert, die in der Regel unter "C:\Programme\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Log" vorhanden ist, wenn Sie die Standardinstanz von SQL Server installiert haben. In dieser Datei direkt ausgeführte Änderungen sind jedoch nicht dauerhaft und werden von den Konfigurationseinstellungen in der A_CONFIGURATION-Tabelle in der DQS_MAIN-Datenbank überschrieben.  
  
##  <a name="configure-data-quality-client-log-settings"></a><a name="DQSClient"></a>Konfigurieren Data Quality-Client Protokoll Einstellungen  
 Die [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] Konfigurationsdatei für die Protokoll Einstellungen (DQLog.Client.xml) ist in der Regel unter c:\Programme\Microsoft SQL server\120\tools\binn\dq\config. Der Inhalt der XML-Datei ähnelt der XML-Datei, die Sie zuvor für die [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] Protokoll Konfigurationseinstellungen geändert haben. So konfigurieren Sie die [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Protokolleinstellungen:  
  
1.  Führen Sie ein beliebiges XML-Bearbeitungstool oder den Editor als Administrator aus.  
  
2.  Öffnen Sie die Datei "DQLog.Client.xml" im Tool oder Editor.  
  
3.  Nehmen Sie die erforderlichen Änderungen vor, und speichern Sie die Datei, um die geänderten Protokollierungseinstellungen zu übernehmen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Schweregraden für DQS-Protokolldateien](../../2014/data-quality-services/configure-severity-levels-for-dqs-log-files.md)  
  
  
