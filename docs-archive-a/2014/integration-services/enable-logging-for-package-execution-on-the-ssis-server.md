---
title: Aktivieren der Protokollierung für die Paket Ausführung auf dem SSIS-Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 8930c63c-bc6f-46c2-b428-b3c29ee89a7d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bb0ca1e03466e6cad277905093262b9aec048c71
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87618814"
---
# <a name="enable-logging-for-package-execution-on-the-ssis-server"></a>Aktivieren der Protokollierung für die Paketausführung auf dem SSIS-Server
  In diesem Verfahren wird beschrieben, wie Sie den Protokolliergrad für ein Paket festlegen oder ändern, wenn Sie ein auf dem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Server bereitgestelltes Paket ausführen. Der Protokolliergrad, den Sie beim Ausführen des Pakets festgelegt haben, überschreibt die Paketprotokollierung, die Sie mit [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] konfigurieren. Weitere Informationen finden Sie unter [Aktivieren der Paketprotokollierung in SQL Server Data Tools](../../2014/integration-services/enable-package-logging-in-sql-server-data-tools.md) .  
  
 Sie können den Protokolliergrad mit einer der folgenden Methoden angeben. In diesem Thema wird die erste Methode behandelt.  
  
-   Konfigurieren einer Instanz einer Paketausführung mithilfe des Dialogfelds "Paket ausführen"  
  
-   Das Festlegen von Parametern für eine Instanz mithilfe von [catalog.set_execution_parameter_value &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database)  
  
-   Das Konfigurieren eines Auftrags des SQL Server-Agents für eine Paketausführung mit dem Dialogfeld "Neuer Auftragsschritt".  
  
### <a name="to-set-the-logging-level-for-a-package-by-using-the-execute-package-dialog-box"></a>So legen Sie den Protokolliergrad für ein Paket mithilfe des Dialogfelds "Paket ausführen" fest  
  
1.  Navigieren Sie in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]zum Paket im Objekt-Explorer.  
  
2.  Klicken Sie mit der rechten Maustaste auf das Paket, und wählen Sie **Ausführen**aus.  
  
3.  Wählen Sie im Dialogfeld **Paket ausführen** die Registerkarte **Erweitert** aus.  
  
4.  Wählen Sie unter **Protokolliergrad**den Protokolliergrad aus. Eine Beschreibung der verfügbaren Werte finden Sie in der unten stehenden Tabelle.  
  
5.  Nehmen Sie ggf. weitere Einstellungen für die Paketkonfiguration vor, und klicken Sie anschließend auf **OK** , um das Paket auszuführen.  
  
 Die folgenden Protokolliergrade sind verfügbar.  
  
|Protokolliergrad|BESCHREIBUNG|  
|-------------------|-----------------|  
|Keine|Die Protokollierung ist deaktiviert. Nur der Status der Ausführung von Paketen wird protokolliert.|  
|Basic|Alle Ereignisse werden protokolliert, außer benutzerdefinierten und Diagnose-Ereignissen. Dies ist der Standardwert.|  
|Leistung|Nur Leistungsstatistiken sowie OnError- und OnWarning-Ereignisse werden protokolliert.<br /><br /> In dem Bericht **Ausführungsleistung** wird die aktive Zeit und die Gesamtzeit für Datenflusskomponenten des Pakets angezeigt. Diese Informationen sind verfügbar, wenn der Protokolliergrad der letzten Paketausführung auf **Leistung** oder **Ausführlich**festgelegt wurde. Weitere Informationen finden Sie unter [Berichte für den Integration Services-Server](../../2014/integration-services/reports-for-the-integration-services-server.md).<br /><br /> In der [catalog.execution_component_phases](/sql/integration-services/system-views/catalog-execution-component-phases) -Sicht werden die Start- und Beendigungszeiten der Datenflusskomponenten für jede Ausführungsphase angezeigt. In dieser Sicht werden die Informationen für diese Komponenten nur angezeigt, wenn der Protokolliergrad der Paketausführung auf **Leistung** oder **Ausführlich**festgelegt ist.|  
|Ausführlich|Alle Ereignisse werden protokolliert, einschließlich benutzerdefinierter Ereignisse und Diagnose-Ereignissen.<br /><br /> Ein Beispiel für ein Diagnoseereignis ist das DiagnosticEx-Ereignis. Jedes Mal, wenn der Task "Paket ausführen" ein untergeordnetes Paket ausführt, wird dieses Ereignis protokolliert. Die Ereignismeldung besteht aus den Parameterwerten, die an untergeordnete Pakete übergeben wurden<br /><br /> Der Wert der Meldungsspalte für DiagnosticEx ist XML-Text. . Fragen Sie zum Anzeigen des Meldungstexts für eine Paketausführung die Sicht [catalog.operation_messages &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-views/catalog-operation-messages-ssisdb-database) ab.<br /><br /> Hinweis: benutzerdefinierte Ereignisse schließen die Ereignisse ein, die von Tasks protokolliert werden [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Weitere Informationen finden Sie unter [Custom Messages for Logging](../../2014/integration-services/custom-messages-for-logging.md).<br /><br /> In der [catalog.execution_data_statistics](../relational-databases/statistics/statistics.md) -Sicht wird eine Zeile angezeigt, sobald eine Datenflusskomponente Daten zur Paketausführung an eine Downstreamkomponente sendet. Der Protokolliergrad muss auf **Ausführlich** festgelegt werden, um diese Informationen in der Sicht zu erfassen.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Integration Services &#40;SSIS-&#41; Protokollierung](performance/integration-services-ssis-logging.md)   
 [Aktivieren der Paket Protokollierung in SQL Server Data Tools](../../2014/integration-services/enable-package-logging-in-sql-server-data-tools.md)  
  
  
