---
title: Quellen-Editor für Excel (Seite Verbindungs-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.excelsourceadapter.connection.f1
helpviewer_keywords:
- Excel Source Editor
ms.assetid: 428e04e0-ad98-45d0-8345-12ec1b67b2eb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3285b5c8b14016b91005af79542e3e2f9b6559b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87618795"
---
# <a name="excel-source-editor-connection-manager-page"></a>Quellen-Editor für Excel (Seite Verbindungs-Manager)
  Mithilfe des Knotens **Verbindungs-Manager** im Dialogfeld **Quellen-Editor für Excel** können Sie eine [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] -Arbeitsmappe für die Quelle auswählen. Die Excel-Quelle liest Daten aus einem Arbeitsblatt oder dem benannten Bereich einer vorhandenen Arbeitsmappe.  
  
> [!NOTE]  
>  Die- `CommandTimeout` Eigenschaft der Excel-Quelle ist nicht im **Quellen-Editor für Excel**verfügbar, kann jedoch mit dem- **Erweiterter Editor**festgelegt werden. Weitere Informationen zu dieser Eigenschaft finden Sie im Abschnitt Excel-Quelle von [Excel Custom Properties](data-flow/excel-custom-properties.md).  
  
 Weitere Informationen zur Excel-Quelle finden Sie unter [Excel Source](data-flow/excel-source.md).  
  
## <a name="static-options"></a>Statische Optionen  
 **Teilcache**  
 Wählen Sie einen vorhandenen Excel-Verbindungs-Manager aus der Liste aus, oder erstellen Sie eine neue Verbindung, indem Sie auf **Neu**klicken.  
  
 **Neu**  
 Erstellen Sie mithilfe des Dialogfelds **Excel-Verbindungs-Manager** eine neue Verbindung.  
  
 **Datenzugriffsmodus**  
 Geben Sie die Methode für die Auswahl von Daten aus der Quelle an.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|Tabelle oder Sicht|Ruft Daten aus einem Arbeitsblatt oder dem benannten Bereich einer Excel-Datei ab.|  
|Variable für Tabellenname oder Sichtname|Geben Sie den Namen des Arbeitsblatts oder Bereichs in einer Variablen an.<br /><br /> **Verwandte Informationen**: [Verwenden von Variablen in Paketen](../../2014/integration-services/use-variables-in-packages.md)|  
|SQL-Befehl|Ruft mithilfe einer SQL-Abfrage Daten aus einer Excel-Datei ab. Informationen zur Abfragesyntax finden Sie unter [Excel Source](data-flow/excel-source.md).|  
|SQL-Befehl aus Variable|Gibt den SQL-Abfragetext in einer Variablen an.|  
  
 **Vorschau**  
 Zeigen Sie mithilfe des Dialogfelds **Datenansicht** eine Vorschau der Ergebnisse an. In der Vorschau können bis zu 200 Zeilen angezeigt werden.  
  
## <a name="data-access-mode-dynamic-options"></a>Dynamische Optionen (Datenzugriffsmodus)  
  
### <a name="data-access-mode--table-or-view"></a>Datenzugriffsmodus = Tabelle oder Sicht  
 **Name der Excel-Tabelle**  
 Wählen Sie in der Liste der in der Excel-Arbeitsmappe verfügbaren Objekte den Namen des Arbeitsblatts oder des benannten Bereichs aus.  
  
### <a name="data-access-mode--table-name-or-view-name-variable"></a>Datenzugriffsmodus = Variable für Tabellenname oder Sichtname  
 **Variablenname**  
 Wählen Sie die Variable aus, die den Namen des Arbeitsblatts oder des benannten Bereichs enthält.  
  
### <a name="data-access-mode--sql-command"></a>Datenzugriffsmodus = SQL-Befehl  
 **SQL-Befehlstext**  
 Geben Sie den Text der SQL-Abfrage ein, und erstellen Sie die Abfrage, indem Sie auf **Abfrage erstellen**klicken. Wahlweise können Sie auch nach der Datei mit dem Abfragetext suchen, indem Sie auf **Durchsuchen**klicken.  
  
 **Parameter**  
 Wenn Sie eine parametrisierte Abfrage eingeben und im Abfragetext ? als Parameterplatzhalter verwenden, können Sie den Paketvariablen mithilfe des Dialogfelds **Abfrageparameter festlegen** Abfrageeingabeparameter zuordnen.  
  
 **Abfrage erstellen**  
 Mithilfe des Dialogfelds **Abfrage-Generator** können Sie die SQL-Abfrage visuell erstellen.  
  
 **Durchsuchen**  
 Mithilfe des Dialogfelds **Öffnen** können Sie nach der Datei suchen, die den Text der SQL-Abfrage enthält.  
  
 **Abfrage analysieren**  
 Überprüft die Syntax des Abfragetexts.  
  
### <a name="data-access-mode--sql-command-from-variable"></a>Datenzugriffsmodus = SQL-Befehl aus Variable  
 **Variablenname**  
 Wählen Sie die Variable aus, die den Text für die SQL-Abfrage enthält.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Der Quellen-Editor für Excel &#40;Spalten&#41;](../../2014/integration-services/excel-source-editor-columns-page.md)   
 [Quellen-Editor für Excel &#40;Seite Fehlerausgabe&#41;](../../2014/integration-services/excel-source-editor-error-output-page.md)   
 [Excel-Verbindungs-Manager](connection-manager/excel-connection-manager.md)   
 [Schleife durch Excel-Dateien und Tabellen mit einem Foreach-Schleifencontainer](control-flow/foreach-loop-container.md)  
  
  
