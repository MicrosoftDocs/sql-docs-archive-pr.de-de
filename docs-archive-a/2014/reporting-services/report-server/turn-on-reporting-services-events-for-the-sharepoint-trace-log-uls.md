---
title: Aktivieren von Reporting Services-Ereignissen für das SharePoint-Ablaufverfolgungsprotokoll (ULS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 81110ef6-4289-405c-a931-e7e9f49e69ba
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b7d1b0a936c234035baf18ca947661de2663195a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617622"
---
# <a name="turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls"></a>Aktivieren von Reporting Services-Ereignissen für das SharePoint-Ablaufverfolgungsprotokoll (ULS)
  Ab [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]schreiben [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] -Server im SharePoint-Modus [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] -Ereignisse in die Ablaufverfolgung des SharePoint Unified Logging Service (ULS). [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] -spezifische Kategorien sind auf der Seite Überwachung der SharePoint-Zentraladministration verfügbar.

 In diesem Thema:

-   [Allgemeine ULS-Protokollempfehlungen](#bkmk_general)

-   [So aktivieren bzw. deaktivieren Sie Reporting Services-Ereignisse in der Reporting Services-Kategorie](#bkmk_turnon)

-   [Empfohlene Konfiguration](#bkmk_recommended)

-   [Lesen der Protokolleinträge](#bkmk_readentries)

-   [Liste der SQL Server Reporting Services-Ereignisse](#bkmk_list)

-   [Anzeigen einer Protokolldatei mit PowerShell](#bkmk_powershell)

-   [Speicherort des Ablaufverfolgungsprotokolls](#bkmk_trace)

##  <a name="general-uls-log-recommendations"></a><a name="bkmk_general"></a> Allgemeine ULS-Protokollempfehlungen
 In der folgenden Tabelle werden Ereigniskategorien und -ebenen aufgelistet, die für die Überwachung einer [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] -Umgebung empfohlen werden. Wenn ein Ereignis protokolliert wird, enthält jeder Eintrag den Zeitpunkt der Protokollierung, den Prozessnamen und die Thread-ID.

|Category|Ebene|BESCHREIBUNG|
|--------------|-----------|-----------------|
|Datenbank|Ausführlich|Protokolliert Ereignisse, die Datenbankzugriff einschließen.|
|Allgemein|Ausführlich|Protokolliert Ereignisse, die Zugriff auf die folgenden Elemente einschließen:<br /><br /> [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] -Webseiten<br /><br /> Berichts-Viewer-HTTP-Handler<br /><br /> Zugriff auf Bericht (RDL-Dateien)<br /><br /> Datenquellen (RSDS-Dateien)<br /><br /> URLs auf der SharePoint-Website (SMDL-Dateien)|
|Office Server General|Ausnahme|Protokolliert Anmeldefehler.|
|Topologie|Ausführlich|Protokolliert aktuelle Benutzerinformationen.|
|Webparts|Ausführlich|Protokolliert Ereignisse, die Zugriff auf den Berichts-Viewer-Webpart einschließen.|

##  <a name="to-turn-on-and-off-reporting-services-events-in-the-reporting-services-category"></a><a name="bkmk_turnon"></a> So aktivieren bzw. deaktivieren Sie Reporting Services-Ereignisse in der Reporting Services-Kategorie

1.  In der SharePoint 2010-Zentraladministration

2.  Klicken Sie auf **Überwachung**.

3.  Klicken Sie in der Gruppe **Berichterstellung** auf **Diagnoseprotokollierung konfigurieren** .

4.  Suchen Sie **SQL Server Reporting Services** in der Kategorieliste.

5.  Klicken Sie auf das Pluszeichen (+), um die Unterkategorien unter **SQL Server Reporting Services**zu erweitern.

6.  Wählen Sie die Unterkategorien aus, die dem Ablaufverfolgungsprotokoll hinzugefügt werden sollen.

7.  Wählen Sie unten in der Kategorieliste eine Ereignisebene für **Unwichtigstes, im Ablaufverfolgungsprotokoll aufzuzeichnendes Ereignis**aus. Wählen Sie **Keine** aus, um die Ablaufverfolgung zu deaktivieren.

> [!NOTE]
>  Die Option **Unwichtigstes, im Ereignisprotokoll aufzuzeichnendes Ereignis** wird von [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]nicht unterstützt. Die Option wird ignoriert.

##  <a name="recommended-configuration"></a><a name="bkmk_recommended"></a> Empfohlene Konfiguration
 Die folgenden Protokollierungsoptionen werden als Standardkonfiguration empfohlen:

-   **HTTP-Redirector**

-   **SOAP-Clientproxy**

-   Wenn Probleme bei der Konfiguration auftreten, fügen Sie **Konfigurationsseiten**hinzu.

 Sie können alle aktuellen Farm-Diagnoseprotokolleinstellungen mit dem folgenden PowerShell-Cmdlet überprüfen:

```powershell
Get-SPDiagnosticConfig
```

##  <a name="reading-the-logs-entries"></a><a name="bkmk_readentries"></a> Lesen der Protokolleinträge
 Die [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] -Einträge im Protokoll werden wie folgt formatiert.

1.  **Produkt: SQL Server Reporting Services**

2.  **Kategorie** : Auf den Server bezogene Ereignisse weisen am Anfang des Namens die Zeichenfolge „Berichtsserver“ auf. Beispiel: „Laufzeit für Berichtsserverwarnungen“. Diese Ereignisse werden auch in den Protokolldateien des Berichtsservers protokolliert.

3.  **Kategorie**: Auf eine Web-Front-End-Komponente bezogene oder von einer Web-Front-End-Komponente kommunizierte Ereignisse enthalten nicht die Zeichenfolge „Berichtsserver“. Beispiel: „Dienstanwendungsproxy – Laufzeit für Berichtsserverwarnungen“. Die WFE-Einträge enthalten CorrelationID, die Servereinträge jedoch nicht.

##  <a name="list-of-sql-server-reporting-services-events"></a><a name="bkmk_list"></a> Liste der SQL Server Reporting Services-Ereignisse
 Die folgende Tabelle enthält eine Liste der Ereignisse in der SQL Server Reporting Services-Kategorie:

|Bereichsname|Beschreibung oder Beispieleinträge|
|---------------|-----------------------------------|
|Konfigurationsseiten||
|HTTP-Redirector||
|Verarbeitung im lokalen Modus||
|Rendering im lokalen Modus||
|SOAP-Clientproxy||
|Benutzeroberflächenseiten||
|Power View|Protokolleinträge, die in die **LogClientTraceEvents** -API geschrieben wurden. Diese Einträge stammen aus Client Anwendungen, einschließlich [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] , einer Funktion des [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] -Add-Ins für [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] Enterprise Edition.<br /><br /> Alle Protokolleinträge aus der LogClientTraceEvents-API werden unter der **Kategorie** von „SQL Server Reporting Services" und dem **Bereich** von „Power View“ protokolliert.<br /><br /> Der Inhalt der Einträge, der mit dem Bereich „Power View“ protokolliert wurde, wird von der Clientanwendung bestimmt.|
|Laufzeit für Berichtsserverwarnungen||
|Berichtsserver-AppDomain-Manager||
|Gepufferte Berichtsserverantwort||
|Berichtsservercache||
|Berichtsserverkatalog||
|Berichtsserverausschnitt||
|Berichtsservercleanup||
|Berichtsserver-Konfigurations-Manager|Beispieleinträge:<br /><br /> Interne URL http://localhost:80/ReportServer des MediumUsing-Berichtservers<br /><br /> UnexpectedMissing- oder ungültige ExtendedProtectionLevel-Einstellung|
|Berichtsserver-Crypto||
|Berichtsserver-Datenerweiterung||
|Berichtsserver-DB-Abruf||
|Berichtsserverstandard||
|Berichtsserver-E-Mail-Erweiterung||
|Berichtsserver-Excel-Renderer||
|Berichtsserver-Erweiterungsfactory||
|Berichtsserver-HTTP-Laufzeit||
|Berichtsserver-Bildrenderer||
|Berichtsserver-Arbeitsspeicherüberwachung||
|Berichtsserverbenachrichtigung||
|Berichtsserververarbeitung||
|Berichtsserveranbieter||
|Berichtsserverrendering||
|Berichtsserver-Berichtsvorschau||
|Berichtsserver-Ressourcenhilfsprogramm|Beispieleinträge:<br /><br /> Start-SKU für MediumReporting-Dienste: Auswertung<br /><br /> MediumEvaluation-Kopie: noch 180 Tage|
|Laufende Berichtsserveraufträge||
|Laufende Berichtsserveranforderungen||
|Berichtsserverplan||
|Berichtsserversicherheit||
|Berichtsserver-Dienstcontroller||
|Berichtsserversitzung||
|Berichtsserverabonnement||
|Berichtsserver-WCF-Laufzeit||
|Report Server-Webserver||
|Proxy für Dienstanwendung||
|Gemeinsamer Dienst|Beispieleinträge:<br /><br /> MediumUpdating ReportingWebServiceApplication<br /><br /> MediumGranting-Zugriff auf Inhaltsdatenbanken.<br /><br /> MediumProvisioning-Instanzen für ReportingWebServiceApplication<br /><br /> MediumProcessing-Dienstkontoänderung für ReportingWebServiceApplication<br /><br /> MediumSetting-Datenbankberechtigungen.|

##  <a name="view-a-log-file-with-powershell"></a><a name="bkmk_powershell"></a> Anzeigen einer Protokolldatei mit PowerShell
 ![PowerShell-Inhalt](../media/rs-powershellicon.jpg "PowerShell-Inhalt") Sie können PowerShell verwenden, um sich eine Liste der [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-bezogenen Ereignisse aus einer ULS-Protokolldatei zurückgeben zu lassen. Geben Sie über die SharePoint 2010-Verwaltungsshell folgenden Befehl ein, um eine gefilterte Liste mit den Zeilen der ULS-Protokolldatei „UESQL11SPOINT-20110606-1530.log“ zurückzugeben, die „**sql server reporting services**“ enthalten:

```powershell
Get-Content -Path "C:\Program Files\Common Files\Microsoft Shared\Web Server Extensions\14\LOGS\UESQL11SPOINT-20110606-1530.log" | Select-String "sql server reporting services"
```

 Es gibt auch viele für den Download verfügbare Tools, mit denen sich ULS-Protokolle lesen lassen. Beispielsweise der [SharePoint LogViewer](https://sharepointlogviewer.codeplex.com/) oder [SharePoint ULS Log Viewer](http://ulsviewer.codeplex.com/workitem/list/basic). Beide sind über CodePlex verfügbar.

 Weitere Informationen zum Anzeigen von Protokolldaten mithilfe von PowerShell finden Sie unter [Anzeigen von Diagnoseprotokollen (SharePoint Server 2010)](https://technet.microsoft.com/library/ff463595.aspx).

##  <a name="trace-log-location"></a><a name="bkmk_trace"></a>Ablauf Verfolgungs Protokoll
 Die Protokolldateien der Ablaufverfolgung befinden sich normalerweise im Ordner **C:\Programme\Common files\Microsoft Shared\Web Server Extensions\14\logs** . Sie können jedoch den Pfad auf der Seite **Diagnoseprotokollierung** der SharePoint-Zentraladministration überprüfen und ggf. ändern.

