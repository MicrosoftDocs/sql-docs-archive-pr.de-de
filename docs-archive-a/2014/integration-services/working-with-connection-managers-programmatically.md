---
title: Programmgesteuertes Arbeiten mit Verbindungs-Managern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- connection managers [Integration Services], programming
ms.assetid: 2686fe84-1ecc-48b8-9160-e7122274bd84
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 01fc61a4a5c85366c7af8c5c68a73777049d3cba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619895"
---
# <a name="working-with-connection-managers-programmatically"></a>Programmgesteuertes Arbeiten mit Verbindungs-Managern
  In [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ist die AcquireConnection-Methode der zugehörigen Verbindungs-Manager-Klasse die Methode, die Sie am häufigsten aufrufen, wenn Sie mit Verbindungs-Managern in verwaltetem Code arbeiten. Wenn Sie verwaltete Codes schreiben, müssen Sie zur Verwendung der Funktionalität eines Verbindungs-Managers die AcquireConnection-Methode aufrufen. Sie müssen diese Methode unabhängig davon, ob Sie einen verwalteten Code in einem Skripttask, einer Skriptkomponente, einem benutzerdefinierten Objekt oder einer benutzerdefinierten Anwendung schreiben, aufrufen.  
  
 Um die Methode AcquireConnection erfolgreich aufrufen zu können, müssen folgende Fragen geklärt sein:  
  
-   **Welche Verbindungs-Manager geben ein verwaltetes Objekt über die AcquireConnection-Methode zurück?**  
  
     Viele Verbindungs-Manager geben nicht verwaltete COM-Objekte (System.__ComObject) zurück, und diese Objekte können nicht ohne Weiteres aus verwalteten Codes verwendet werden. Zu diesen Verbindungs-Managern gehört der häufig verwendete OLE DB-Verbindungs-Manager.  
  
-   **Welche Objekte geben Verbindungs-Manager, die ein verwaltetes Objekt zurückgeben, über die AcquireConnection-Methoden zurück?**  
  
     Um den Rückgabewert in den entsprechenden Typ umzuwandeln, müssen Sie wissen, welcher Objekttyp die AcquireConnection-Methode zurückgibt. Die AcquireConnection-Methode für den Verbindungs-Manager [!INCLUDE[vstecado](../includes/vstecado-md.md)] gibt beispielsweise ein offenes SqlConnection-Objekt zurück, wenn Sie den SqlClient-Provider verwenden. Die AcquireConnection-Methode für den Dateiverbindungs-Manager gibt jedoch nur eine Zeichenfolge zurück.  
  
 In diesem Thema werden diese Fragen für die in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] enthaltenen Verbindungs-Manager beantwortet.  
  
## <a name="connection-managers-that-do-not-return-a-managed-object"></a>Verbindungs-Manager, die kein verwaltetes Objekt zurückgeben  
 In der folgenden Tabelle werden die Verbindungs-Manager aufgelistet, die ein natives COM-Objekt (System.__ComObject) über die AcquireConnection-Methode zurückgeben. Diese nicht verwalteten Objekte können nicht ohne Weiteres in verwaltetem Code verwendet werden.  
  
|Typ des Verbindungs-Managers|Name des Verbindungs-Managers|  
|-----------------------------|-----------------------------|  
|ADO|ADO-Verbindungs-Manager|  
|MSOLAP90|[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Verbindungs-Manager|  
|EXCEL|Excel-Verbindungs-Manager|  
|FTP|FTP-Verbindungs-Manager|  
|HTTP|HTTP-Verbindungs-Manager|  
|ODBC|ODBC-Verbindungs-Manager|  
|OLEDB|OLE DB-Verbindungs-Manager|  
  
 Normalerweise können Sie einen [!INCLUDE[vstecado](../includes/vstecado-md.md)]-Verbindungs-Manager aus verwalteten Codes verwenden, um eine Verbindung mit einer ADO-, Excel-, ODBC- oder OLE DB-Datenquelle herzustellen.  
  
## <a name="return-values-from-the-acquireconnection-method"></a>Rückgabewerte von der AcquireConnection-Methode  
 In der folgenden Tabelle werden die Verbindungs-Manager aufgelistet, die ein verwaltetes Objekt über die AcquireConnection-Methode zurückgeben. Diese verwalteten Objekte können einfach in verwaltetem Code verwendet werden.  
  
|Typ des Verbindungs-Managers|Name des Verbindungs-Managers|Typ des Rückgabewerts|Zusätzliche Informationen|  
|-----------------------------|-----------------------------|--------------------------|----------------------------|  
|[!INCLUDE[vstecado](../includes/vstecado-md.md)]|[!INCLUDE[vstecado](../includes/vstecado-md.md)]-Verbindungs-Manager|`System.Data.SqlClient.SqlConnection`||  
|FILE|Dateiverbindungs-Manager|`System.String`|Pfad zur Datei.|  
|FLATFILE|Verbindungs-Manager für Flatfiles|`System.String`|Pfad zur Datei.|  
|MSMQ|MSMQ-Verbindungs-Manager|`System.Messaging.MessageQueue`||  
|MULTIFILE|Verbindungs-Manager für mehrere Dateien|`System.String`|Pfad zu einer der Dateien.|  
|MULTIFLATFILE|Verbindungs-Manager für mehrere Flatfiles|`System.String`|Pfad zu einer der Dateien.|  
|SMOServer|SMO-Verbindungs-Manager|`Microsoft.SqlServer.Management.Smo.Server`||  
|SMTP|SMTP-Verbindungs-Manager|`System.String`|Beispiel: `SmtpServer=<server name>;UseWindowsAuthentication=True;EnableSsl=False;`|  
|WMI|WMI-Verbindungs-Manager|`System.Management.ManagementScope`||  
|SQLMOBILE|SQL Server Compact Verbindungs-Manager|`System.Data.SqlServerCe.SqlCeConnection`||  
  
![Integration Services Symbol (klein)](media/dts-16.gif "Integration Services (kleines Symbol)")immer auf**dem neuesten Stand bleiben mit Integration Services**  <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Herstellen einer Verbindung mit Datenquellen im Skript Task](extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md)   
 [Herstellen einer Verbindung mit Datenquellen in der Skript Komponente](extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md)   
 [Herstellen einer Verbindung mit Datenquellen in einem benutzerdefinierten Task](extending-packages-custom-objects/task/connecting-to-data-sources-in-a-custom-task.md)  
  
  
