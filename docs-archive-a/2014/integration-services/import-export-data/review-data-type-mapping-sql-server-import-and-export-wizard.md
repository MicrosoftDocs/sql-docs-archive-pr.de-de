---
title: Datentypzuordnung überprüfen (SQL Server-Import/Export-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.reviewissues.f1
ms.assetid: 0625c4f9-b8ff-4593-b884-39398b9d43af
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 693abfdc3bd19b8e39ba6b53d31c86b36944c16c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619922"
---
# <a name="review-data-type-mapping-sql-server-import-and-export-wizard"></a>Datentypzuordnung überprüfen (SQL Server-Import/Export-Assistent)
  Verwenden Sie die Seite **Datentyp Zuordnung überprüfen** , um ausführliche Informationen zu Datentyp Konvertierungen zu überprüfen, die der Assistent ausführen muss, damit die Quelldaten mit dem Ziel kompatibel sind. Diese Informationen enthalten optische Hinweise, um Konvertierungen, die voraussichtlich fehlerfrei ablaufen, von Konvertierungen zu unterscheiden, die zu Fehlern oder Kürzungen führen könnten. Sie können für jede Konvertierung entscheiden, ob Sie die vom Assistenten vorgeschlagene Konvertierung übernehmen möchten. Außerdem können Sie angeben, wie mit Fehlern verfahren werden soll.  
  
 Weitere Informationen zu diesem Assistenten finden Sie unter [SQL Server-Import/Export-Assistenten](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Weitere Informationen zu den Optionen für das Starten des Assistenten sowie zu den Berechtigungen, die zum erfolgreichen Ausführen des Assistenten erforderlich sind, finden Sie unter [Ausführen des SQL Server-Import/Export-Assistenten](start-the-sql-server-import-and-export-wizard.md).  
  
 Mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Import/Export-Assistenten werden Daten aus einer Quelle in ein Ziel kopiert. Mit dem Assistenten können auch eine Zieldatenbank und Zieltabellen erstellt werden. Wenn Sie jedoch mehrere Datenbanken, Tabellen oder andere Datenbankobjekte kopieren müssen, verwenden Sie stattdessen den Assistenten zum Kopieren von Datenbanken. Weitere Informationen finden Sie unter [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="options"></a>Tastatur  
 Die Seite **Datentypzuordnung überprüfen** besteht aus der Liste **Tabelle** , der Liste **Datentypzuordnung** und Optionen zur Fehlerbehandlung.  
  
### <a name="table-list"></a>Liste 'Tabelle'  
 Der obere Teil der Seite **Datentyp Probleme überprüfen** ist eine **Tabellen** Liste, in der die Tabellen aufgelistet sind, die von der Quelle an das Ziel übertragen werden sollen. In der folgenden Tabelle werden die Spalten dieser Liste beschrieben.  
  
|Spalte|BESCHREIBUNG|  
|------------|-----------------|  
|Quellensymbol|Gibt die Wahrscheinlichkeit des Erfolgs für die Datentypkonvertierungen an:<br /><br /> Ein grünes Häkchen gibt an, dass der Assistent erwartet, dass alle Datentypkonvertierungen für diese Tabelle erfolgreich sind.<br /><br /> Ein gelbes Warnsymbol gibt an, dass Sie die einzelnen Konvertierungen überprüfen sollten, die der Assistent ausführt. Um diese Konvertierungen zu prüfen, wählen Sie die Tabelle aus und prüfen dann die Konvertierungen für einzelne Spalten in der Liste **Datentypzuordnung** .<br /><br /> Ein rotes Fehlersymbol gibt an, dass der Assistent einige der Konvertierungen für diese Tabelle nicht zuverlässig ausführen kann.|  
|**Quelle**|Zeigt den Namen der Quelltabelle an.|  
|Zielsymbol|Gibt an, ob das Ziel bereits vorhanden ist oder vom Assistenten erstellt wird:<br /><br /> Ein Tabellensymbol gibt an, dass das Ziel eine vorhandene Tabelle ist.<br /><br /> Ein Tabellensymbol in Form einer Sonne gibt an, dass das Ziel eine neue Tabelle ist, die der Assistent erstellt.|  
|**Ziel**|Zeigt den Namen der Zieltabelle an.|  
  
 Wenn Sie Konvertierungs Informationen zu einer einzelnen Tabelle anzeigen möchten, wählen Sie eine Tabelle in diesem **Tabellen** Raster aus. Die Konvertierungsinformationen für die ausgewählte Tabelle werden in den Spalten im Raster **Datentypzuordnung** unten auf der Seite angezeigt.  
  
### <a name="data-type-mapping-list"></a>Liste 'Datentypzuordnung'  
 Der untere Teil der Seite **Datentyp Probleme überprüfen** ist die Liste **Datentyp Zuordnung** . Dieses Raster enthält detaillierte Konvertierungsinformationen über die Spalten in der Tabelle, die in der Liste **Tabelle** ausgewählt ist. In der folgenden Tabelle werden die Spalten dieser Liste beschrieben.  
  
|Spalte|BESCHREIBUNG|  
|------------|-----------------|  
|Konvertierungssymbol|Gibt die Wahrscheinlichkeit des Erfolgs für die Datentypkonvertierungen an:<br /><br /> Ein grünes Häkchen gibt an, dass der Assistent erwartet, dass die Datentypkonvertierung für diese Spalte erfolgreich ist.<br /><br /> Ein gelbes Warnsymbol gibt an, dass Sie die Konvertierung überprüfen sollten, die der Assistent ausführt. Doppelklicken Sie auf die Spalte, um das Dialogfeld **Spaltenkonvertierungsdetails** anzuzeigen und die Konvertierung zu überprüfen.<br /><br /> Ein rotes Fehlersymbol gibt an, dass der Assistent die Konvertierung nicht zuverlässig ausführen kann.|  
|**Quellspalte**|Zeigt den Namen der Quellspalte an.|  
|**Quelltyp**|Zeigt den Datentyp der Quellspalte an.|  
|**Zielspalte**|Zeigt den Namen der Zielspalte an.|  
|**Zieltyp**|Zeigt den Datentyp der Zielspalte an.|  
|**Konvertieren**|Geben Sie an, ob die geplante Konvertierung fortgesetzt werden soll:<br /><br /> Aktivieren Sie das Kontrollkästchen, damit der Assistent mit der geplanten Konvertierung fortfährt.<br /><br /> Deaktivieren Sie das Kontrollkästchen, um die Datentypkonvertierung abzubrechen.|  
|**Bei Fehler**|Geben Sie an, wie der Assistent Fehler behandelt:<br /><br /> Verwenden Sie die Einstellung **bei Fehler (Global)** .<br /><br /> Import- oder Exportprozess beim Auftreten eines Fehlers beenden.<br /><br /> Fehler ignorieren.|  
|**Bei Kürzung**|Geben Sie an, wie der Assistent Kürzungen behandelt:<br /><br /> Verwenden Sie die Einstellung **bei abkürzen (Global)** .<br /><br /> Mit einem Fehler fehlschlagen und den Import-oder Exportprozess beenden<br /><br /> Kürzung ignorieren.|  
  
 Um detaillierte Informationen über die Konvertierung einer bestimmten Datenspalte anzuzeigen, doppelklicken Sie auf eine beliebige Zeile in der Liste. Das Dialogfeld **Spaltenkonvertierungsdetails** wird geöffnet und zeigt ausführlichere Konvertierungsinformationen für die Spalte an.  
  
### <a name="error-handling-options"></a>Fehlerbehandlungsoptionen  
 **Bei Fehler (global)**  
 Geben Sie an, wie der Assistent Fehler behandelt:  
  
-   Import- oder Exportprozess beim Auftreten eines Fehlers beenden.  
  
-   Fehler ignorieren und den Import- oder Exportprozess fortsetzen.  
  
 Diese Einstellung gilt für alle Konvertierungen, bei denen die Option **Global verwenden** in der Spalte **Bei Fehler** der Liste **Datentypzuordnung** aktiviert ist.  
  
 **Bei Kürzung (global)**  
 Geben Sie an, wie der Assistent Kürzungen behandelt:  
  
-   Import- oder Exportprozess beim Auftreten eines Fehlers beenden.  
  
-   Kürzung ignorieren und den Import- oder Exportprozess fortsetzen.  
  
 Diese Einstellung gilt für alle Konvertierungen, bei denen die Option **Global verwenden** in der Spalte **Bei Kürzung** der Liste **Datentypzuordnung** aktiviert ist.  
  
  
