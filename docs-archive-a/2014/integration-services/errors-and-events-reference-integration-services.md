---
title: Fehler- und Ereignisreferenz (Integration Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, events
- events [Integration Services]
- errors [Integration Services]
- Integration Services, errors
ms.assetid: cf4f0f14-8087-42d7-9b67-e4929228abd6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c434e68aa676508d8a50d89bc18b79b6167b48ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87618812"
---
# <a name="errors-and-events-reference-integration-services"></a>Fehler- und Ereignisreferenz (Integration Services)
  Dieser Abschnitt der Dokumentation enthält Informationen zu verschiedenen Fehlern und Ereignissen, die im Zusammenhang mit [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]auftreten können. Für Fehlermeldungen sind Informationen zu Ursache und Lösung enthalten.  
  
 Weitere Informationen zu [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Fehlermeldungen, einschließlich einer Liste der wichtigsten [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Fehler und deren Beschreibungen, finden Sie unter [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md). Zum aktuellen Zeitpunkt enthält diese Liste jedoch noch keine Informationen zur Problembehandlung.  
  
> [!IMPORTANT]  
>  Viele Fehlermeldungen, die Ihnen bei der Verwendung von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] angezeigt werden, stammen von anderen Komponenten wie OLE DB-Anbietern, anderen Datenbankkomponenten wie der [!INCLUDE[ssDE](../includes/ssde-md.md)] und [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] oder von anderen Diensten bzw. Komponenten wie dem Dateisystem, dem SMTP-Server oder Microsoft Message Queueing. Informationen zu diesen externen Fehlermeldungen finden Sie in der Dokumentation der entsprechenden Komponenten.  
  
## <a name="error-messages"></a>Fehlermeldungen  
  
|Symbolischer Name des Fehlers|BESCHREIBUNG|  
|----------------------------|-----------------|  
|DTS_E_CACHELOADEDFROMFILE|Gibt an, dass das Paket nicht ausgeführt werden kann, da von einer Transformation für Cachetransformation versucht wird, Daten in den Cache im Arbeitsspeicher zu schreiben. Ein Cacheverbindungs-Manager hat jedoch bereits eine Cachedatei in den Cache im Arbeitsspeicher geladen.|  
|DTS_E_CANNOTACQUIRECONNECTIONFROMCONNECTIONMANAGER|Gibt an, dass das Paket nicht ausgeführt werden kann, da bei einer angegebenen Verbindung ein Fehler aufgetreten ist.|  
|DTS_E_CANNOTCONVERTBETWEENUNICODEANDNONUNICODESTRINGCOLUMN|Zeigt an, dass eine Datenflusskomponente versucht, Unicode-Zeichenfolgendaten an eine andere Komponente zu übergeben, die jedoch in der entsprechenden Spalte Nicht-Unicode-Zeichenfolgendaten erwartet oder umgekehrt.|  
|DTS_E_CANNOTCONVERTBETWEENUNICODEANDNONUNICODESTRINGCOLUMNS|Zeigt an, dass eine Datenflusskomponente versucht, Unicode-Zeichenfolgendaten an eine andere Komponente zu übergeben, die jedoch in der entsprechenden Spalte Nicht-Unicode-Zeichenfolgendaten erwartet oder umgekehrt.|  
|DTS_E_CANTINSERTCOLUMNTYPE|Gibt an, dass die Spalte der Datenbanktabelle nicht hinzugefügt werden kann, da eine Konvertierung zwischen dem Datentyp der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Spalte und dem Datentyp der Datenbankspalte nicht unterstützt wird.|  
|DTS_E_CONNECTIONNOTFOUND|Gibt an, dass das Paket nicht ausgeführt werden kann, da der angegebene Verbindungs-Manager nicht gefunden werden kann.|  
|DTS_E_CONNECTIONREQUIREDFORMETADATA|Zeigt an, dass [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer eine Verbindung mit einer Datenquelle herstellen muss, um neue oder aktualisierte Metadaten für eine Quelle oder ein Ziel anzurufen, und dass diese Verbindung nicht hergestellt werden kann.|  
|DTS_E_MULTIPLECACHEWRITES|Gibt an, dass das Paket nicht ausgeführt werden kann, da von einer Transformation für Cachetransformation versucht wird, Daten in den Cache im Arbeitsspeicher zu schreiben. Eine andere Transformation für Cachetransformation hat jedoch bereits in den Cache im Arbeitsspeicher geschrieben.|  
|DTS_E_PRODUCTLEVELTOLOW|Zeigt an, dass das Paket nicht ausgeführt werden kann, weil die geeignete Version von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] nicht installiert ist.|  
|DTS_E_READNOTFILLEDCACHE|Gibt an, dass eine Transformation für Suche versucht, Daten aus dem Cache im Arbeitsspeicher zu lesen, während gleichzeitig eine Transformation für Cachetransformation Daten in den Cache schreibt.|  
|DTS_E_UNPROTECTXMLFAILED|Gibt an, dass das System einen geschützten XML-Knoten nicht entschlüsselt hat.|  
|DTS_E_WRITEWHILECACHEINUSE|Gibt an, dass eine Transformation für Cachetransformation versucht, Daten in den Cache im Arbeitsspeicher zu schreiben, während gleichzeitig eine Transformation für Suche Daten aus dem Cache im Arbeitsspeicher liest.|  
|DTS_W_EXTERNALMETADATACOLUMNSOUTOFSYNC|Gibt an, dass die Spaltenmetadaten in der Datenquelle nicht mit den Spaltenmetadaten in der Quell- oder Zielkomponente übereinstimmen, die mit der Datenquelle verbunden ist.|  
  
## <a name="events-sqlispackage"></a>Ereignisse (SQLISPackage)  
 Weitere Informationen finden Sie unter [Von einem Integration Services-Paket protokollierte Ereignisse](performance/events-logged-by-an-integration-services-package.md).  
  
|Ereignis|BESCHREIBUNG|  
|-----------|-----------------|  
|SQLISPackage_12288|Gibt an, dass ein Paket gestartet wurde.|  
|SQLISPackage_12289|Gibt an, dass ein Paket erfolgreich zu Ende ausgeführt wurde.|  
|SQLISPACKAGE_12291|Gibt an, dass die Ausführung eines Pakets nicht abgeschlossen werden konnte und beendet wurde.|  
|SQLISPackage_12546|Gibt an, dass die Ausführung einer Aufgabe oder einer anderen ausführbaren Datei in einem Paket abgeschlossen wurde.|  
|SQLISPackage_12549|Gibt an, dass eine Warnmeldung in einem Paket ausgelöst wurde.|  
|SQLISPackage_12550|Gibt an, dass eine Fehlermeldung in einem Paket ausgelöst wurde.|  
|SQLISPackage_12551|Gibt an, dass die Ausführung eines Pakets nicht abgeschlossen werden konnte und beendet wurde.|  
|SQLISPackage_12557|Gibt an, dass ein Paket zu Ende ausgeführt wurde.|  
  
## <a name="events-sqlisservice"></a>Ereignisse (SQLISService)  
 Weitere Informationen finden Sie unter [Vom Integration Services-Dienst protokollierte Ereignisse](service/events-logged-by-the-integration-services-service.md).  
  
|Ereignis|BESCHREIBUNG|  
|-----------|-----------------|  
|SQLISService_256|Gibt an, dass der Dienst umgehend gestartet wird.|  
|SQLISService_257|Gibt an, dass der Dienst gestartet wurde.|  
|SQLISService_258|Gibt an, dass der Dienst umgehend beendet wird.|  
|SQLISService_259|Gibt an, dass der Dienst beendet wurde.|  
|SQLISService_260|Gibt an, dass erfolglos versucht wurde, den Dienst zu starten.|  
|SQLISService_272|Gibt an, dass die Konfigurationsdatei am angegebenen Speicherort nicht vorhanden ist.|  
|SQLISService_273|Gibt an, dass die Konfigurationsdatei nicht gelesen werden konnte oder nicht gültig ist.|  
|SQLISService_274|Gibt an, dass der Registrierungseintrag, der den Speicherort der Konfigurationsdatei enthält, nicht vorhanden oder leer ist.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
