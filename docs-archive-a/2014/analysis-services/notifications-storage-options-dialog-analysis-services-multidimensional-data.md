---
title: Benachrichtigungen (Dialog Feld ' Speicheroptionen ') (Analysis Services-Mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitiondesigner.partitionstoragesettings.setstorageoptions.notifications.f1
ms.assetid: 5675cdbf-bfaa-4b6e-b716-31b8e9da72b4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 62e2a00c2b8dd5d2b0a5f3faae71f477de436e69
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615645"
---
# <a name="notifications-storage-options-dialog-box-analysis-services---multidimensional-data"></a>Benachrichtigungen (Dialogfeld 'Speicheroptionen') (Analysis Services – Mehrdimensionale Daten)
  Mithilfe des Dialogfelds **Benachrichtigungen** des Dialogfelds **Speicheroptionen** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] können Sie die Benachrichtigungsmethode und die damit verbundenen Einstellungen für eine Dimension, einen Cube, eine Measuregruppe oder eine Partition festlegen.  
  
> [!NOTE]  
>  Sie sollten mit den Funktionen für den Speichermodus und das proaktive Zwischenspeichern vertraut sein, bevor Sie Änderungen an diesen Einstellungen vornehmen. Weitere Informationen finden Sie unter [Proaktives Zwischenspeichern &#40;Partitionen&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).  
  
## <a name="options"></a>Tastatur  
  
|Begriff|Definition|  
|----------|----------------|  
|**Speichermodus**|Wählt den für das Objekt zu verwendenden Speichermodus aus.<br /><br /> **MOLAP**<br /> Für das Objekt wird die mehrdimensionale OLAP (MOLAP)-Speicherung verwendet.<br /><br /> **HOLAP**<br /> Für das Objekt wird die hybride OLAP (HOLAP)-Speicherung verwendet.<br /><br /> **ROLAP**<br /> Für das Objekt wird die relationale OLAP (ROLAP)-Speicherung verwendet.|  
|**Aktiviert die proaktive Zwischenspeicherung.**|Aktiviert die proaktive Zwischenspeicherung.<br /><br /> Hinweis: Wenn diese Option nicht ausgewählt ist, sind alle Optionen mit Ausnahme von **Speichermodus** deaktiviert.|  
|**SQL Server**|Verwendet einen spezialisierten Ablauf Verfolgungs Mechanismus für [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , um Änderungen an zugrunde liegenden Tabellen für das Objekt zu identifizieren.|  
|**Nachverfolgungstabellen angeben**|Geben Sie die zugrunde liegenden Tabellen an, in denen das Objekt nachverfolgt werden soll. Geben Sie anschließend eine durch Semikolons (;) unterteilte Liste der Tabellen ein, oder klicken Sie auf die Schaltfläche mit den Auslassungspunkten **(…)**, um das Dialogfeld **Relationale Objekte** aufzurufen und die Tabellen auszuwählen, die nachverfolgt werden sollen. Weitere Informationen finden Sie unter [Dialogfeld „Relationale Objekte“ &#40;Analysis Services – Mehrdimensionale Daten&#41;](relational-objects-dialog-box-analysis-services-multidimensional-data.md).<br /><br /> Wenn diese Option nicht ausgewählt ist, versucht [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] die Liste der zugrunde liegenden Tabellen zu bestimmen, für die eine Nachverfolgung für das Objekt durchgeführt werden soll, wenn bestimmte Anforderungen erfüllt sind. Weitere Informationen zu diesen Anforderungen finden Sie unter [Proaktives Zwischenspeichern &#40;Partitionen&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).|  
|**Vom Client initiiert**|Wählen Sie diese Option aus, um den XMLA-Befehl (XML for Analysis) `NotifyTableChange` zu verwenden, mit dem Sie Änderungen an den zugrunde liegenden Tabellen für das Objekt identifizieren können. Diese Option ist normalerweise ausgewählt, wenn Sie die Verwendung eines Client-basierten Benachrichtigungsprozesses planen.|  
|**Nachverfolgungstabellen angeben**|Wählen Sie diese Option aus, um die zugrunde liegenden Tabellen anzugeben, in denen das Objekt nachverfolgt werden soll. Geben Sie anschließend eine durch Semikolons (;) unterteilte Liste der Tabellen ein, oder klicken Sie auf die Schaltfläche mit den Auslassungspunkten (**...**), um das Dialogfeld **Relationale Objekte** aufzurufen, und wählen Sie die Tabellen aus, die nachverfolgt werden sollen. Weitere Informationen finden Sie unter [Dialogfeld „Relationale Objekte“ &#40;Analysis Services – Mehrdimensionale Daten&#41;](relational-objects-dialog-box-analysis-services-multidimensional-data.md).<br /><br /> Wenn diese Option nicht ausgewählt ist, versucht [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] die Liste der zugrunde liegenden Tabellen zu bestimmen, für die eine Nachverfolgung für das Objekt durchgeführt werden soll, wenn bestimmte Anforderungen erfüllt sind. Weitere Informationen zu diesen Anforderungen finden Sie unter [Proaktives Zwischenspeichern &#40;Partitionen&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).|  
|**Geplantes Abrufen**|Verwendet einen Abrufmechanismus zum Identifizieren von Änderungen, indem eine Reihe von Abfragen der zugrunde liegenden Tabellen für das Objekt ausgeführt werden.|  
|**Abrufintervall**|Gibt das Intervall und die Zeiteinheiten für den Zeitraum an, nach dessen Ablauf [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] die im Abrufraster definierten Abrufabfragen und Verarbeitungsabfragen ausführt.|  
|**Inkrementelle Updates aktivieren**|Aktualisiert den MOLAP-Cache inkrementell für ein Objekt, das auf einem Satz von Abruf- und Verarbeitungsabfragen basiert, mit denen nur zusätzliche Daten identifiziert werden können. Wenn diese Option ausgewählt ist, wird die Abrufabfrage mit einer Tabellen in der Datenquellensicht verknüpft. Mithilfe der Verarbeitungsabfrage wird dann der aktuelle Wert der Abrufabfrage mit dem gespeicherten Wert der zuvor ausgeführten Abrufabfrage verglichen, um so Änderungen zu identifizieren.<br /><br /> Wenn diese Option nicht ausgewählt ist, wird der MOLAP-Cache vollständig aktualisiert. Mithilfe der Abrufabfrage können erfolgte Änderungen identifiziert werden. Verarbeitungsabfragen oder Tabellenbezeichner sind nicht erforderlich.|  
|**Abrufraster**|Enthält die Abrufabfragen, die Verarbeitungsabfragen und die Tabellenbezeichner, die von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] verwendet werden, um die Datenquelle abzurufen und Änderungen zu identifizieren, die an den zugrunde liegenden Tabellen für das Objekt vorgenommen wurden. Das Raster enthält die folgenden Spalten:<br /><br /> Abruf **Abfrage**: Geben Sie die im Abruf Intervall ausgeführte SINGLETON-Abfrage ein, um die Änderungen für das Objekt zu identifizieren, oder klicken Sie auf die Schaltfläche mit den Auslassungs Punkten (**...**), um das Dialogfeld Abruf **Abfrage erstellen** zu öffnen und die SINGLETON-Abfrage Weitere Informationen finden Sie unter [Dialogfeld „Abrufabfrage erstellen“ &#40;Analysis Services – Mehrdimensionale Daten&#41;](create-polling-query-dialog-box-analysis-services-multidimensional-data.md). Wenn **Inkrementelle Updates aktivieren** ausgewählt ist, gibt die Abrufabfrage einen Wert zurück, durch den der letzte Datensatz identifiziert wird, der der unter **Tabelle**angegebenen Tabelle hinzugefügt wurde. Wenn **Inkrementelle Updates aktivieren** nicht ausgewählt ist, gibt die Abrufabfrage einen Wert zurück, durch den die aktuell in der Tabelle enthalten Anzahl von Datensätzen identifiziert wird.<br /><br /> **Verarbeitungs Abfrage**: Geben Sie die im Abruf Intervall ausgeführte Abfrage ein, um neue Datensätze aus der in **Tabelle**identifizierten Tabelle abzurufen, oder klicken Sie auf die Schaltfläche mit den Auslassungs Punkten (**...**), um das Dialogfeld **Verarbeitungs Abfrage erstellen** zu öffnen und die Abfrage zu definieren. Weitere Informationen finden Sie unter [Dialogfeld „Verarbeitungsabfrage erstellen“ &#40;Analysis Services – Mehrdimensionale Daten&#41;](create-processing-query-dialog-box-analysis-services-multidimensional-data.md). Die Abfrage sollte parametrisiert werden, um zwei Parameter zu akzeptieren: der vorherige Wert, der von der Abfrage in der Abruf **Abfrage** zurückgegeben wird, und der aktuelle Wert, der von der Abfrage in der Abruf **Abfrage**zurückgegeben wird. diese kann zum Identifizieren und Extrahieren von Datensätzen verwendet werden, die während des Abruf Zeitraums hinzugefügt wurden Beachten Sie, dass diese Option nur aktiviert ist, wenn **Inkrementelle Updates aktivieren** ausgewählt wird.<br /><br /> **Tabelle**: Geben Sie den Bezeichner der Tabelle ein, in der die Abfrage in der Abruf **Abfrage** den letzten Datensatz nachverfolgt, oder klicken Sie auf die Schaltfläche mit den Auslassungs Punkten (**...**), um das Dialogfeld **Tabelle suchen** zu öffnen und die Tabelle auszuwählen. Weitere Informationen finden Sie unter [Dialogfeld „Tabelle suchen“ &#40;Analysis Services – Mehrdimensionale Daten&#41;](find-table-dialog-box-analysis-services-multidimensional-data.md).|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dialog Feld "Speicheroptionen" &#40;Analysis Services Mehrdimensionale Daten&#41;](storage-options-dialog-box-analysis-services-multidimensional-data.md)  
  
  