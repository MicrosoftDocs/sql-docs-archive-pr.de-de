---
title: Warnungs Eigenschaften-neue Warnung (Seite "Allgemein") | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.alert.general.f1
ms.assetid: f5c11610-62e3-44df-9800-a5dc35be4a09
author: stevestein
ms.author: sstein
ms.openlocfilehash: 471b0062ecc805e83020495e422f8914baec5f71
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87722229"
---
# <a name="alert-properties-new-alert-general-page"></a>Warnungs Eigenschaften-neue Warnung (Seite "Allgemein")
  Mithilfe dieser Seite können Sie die allgemeinen Eigenschaften von-Agent-Warnungen anzeigen und ändern [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="options"></a>Tastatur  
 **Name**  
 Ändern Sie den Namen der Warnung.  
  
 **Aktivieren**  
 Aktivieren Sie die Warnung. Wenn die Warnung nicht aktiviert ist, werden die in der Warnung angegebenen Aktionen nicht ausgeführt.  
  
 **Type**  
 Wählen Sie den Typ der Warnung aus:  
  
-   **SQL Server-Ereigniswarnung** reagiert auf Meldungen im [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Ereignisprotokoll.  
  
-   **SQL Server-Leistungsstatuswarnung** reagiert auf eine bestimmte Bedingung in einem Leistungsindikator.  
  
-   **WMI-Ereigniswarnung** reagiert auf ein WMI-Ereignis (Windows Management Instrumentation).  
  
## <a name="sql-server-event-alert-options"></a>Optionen für die SQL Server-Ereigniswarnung  
 **Datenbankname**  
 Geben Sie eine Datenbank für das Ereignis an, oder geben Sie **Alle Datenbanken** an, damit auf eine Meldung unabhängig von der Datenbank reagiert wird, in der das Ereignis auftritt.  
  
 **Fehlernummer**  
 Geben Sie an, dass dieses Ereignis auf einen Fehler reagiert, und geben Sie die Fehlernummer an.  
  
 **Severity**  
 Geben Sie an, dass dieses Ereignis auf alle Meldungen innerhalb eines bestimmten Schweregrads reagiert, und geben Sie den Schweregrad an.  
  
 **Warnung auslösen, wenn eine Meldung Folgendes enthält**  
 Filtert Ereignisse nach einer bestimmten Zeichenfolge. Wenn diese Option ausgewählt ist, reagiert die Warnung nur auf Ereignisse, die eine bestimmte Zeichenfolge enthalten.  
  
 **Meldungs Text**  
 Geben Sie die Zeichenfolge ein, die zum Filtern von Ereignissen verwendet werden soll.  
  
## <a name="sql-server-performance-condition-alerts"></a>SQL Server-Leistungsstatuswarnungen  
 **Object**  
 Geben Sie das zu überwachende Leistungsobjekt an.  
  
 **Leistungsindikator**  
 Geben Sie den Leistungsindikator innerhalb des Leistungsobjekts an, der überwacht werden soll.  
  
 **Instanz**  
 Geben Sie die Instanz des Leistungsindikators an, die überwacht werden soll.  
  
 **Warnung, falls Leistungsindikator**  
 Geben Sie das Verhalten des Leistungsindikators an, auf das die Warnung reagiert. Die Warnung könnte beispielsweise auf eine Bedingung reagieren, bei der der Wert des Leistungsindikators **Freier Speicherplatz in 'tempdb' (KB)** unter eine bestimmte Grenze fällt, oder auf eine Bedingung, bei der der Wert für **SQL-Kompilierungen/Sekunde** einen bestimmten Wert übersteigt.  
  
 **Wert**  
 Geben Sie einen Wert für den Leistungsindikator an.  
  
## <a name="wmi-event-alert-options"></a>WMI-Ereigniswarnungsoptionen  
 **Namespace**  
 Geben Sie den Namespace an, der für die WQL-Anweisung (WMI Query Language) verwendet werden soll. Es werden nur Namespaces auf dem Computer unterstützt, auf dem der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent ausgeführt wird.  
  
 **Abfrage**  
 Geben Sie die WQL-Anweisung an, die das Ereignis identifiziert, auf das die Warnung reagiert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Warnungen](alerts.md)   
 [Verwenden von WQL mit dem WMI-Anbieter für Server Ereignisse](../../relational-databases/wmi-provider-server-events/using-wql-with-the-wmi-provider-for-server-events.md)   
 [Erstellen einer Warnung mithilfe einer Fehlernummer](create-an-alert-using-an-error-number.md)   
 [Create an Alert Using Severity Level](create-an-alert-using-severity-level.md)  
  
  
