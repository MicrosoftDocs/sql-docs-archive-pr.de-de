---
title: CDC-Quelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdcsource.f1
ms.assetid: 99775608-e177-44ed-bb44-aaccb0f4f327
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 064c25b129364dfcd813d71a462586303dd4ff60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621622"
---
# <a name="cdc-source"></a>CDC-Quelle
  Die CDC-Quelle liest einen Bereich mit Änderungsdaten aus [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Änderungstabellen und übermittelt die Änderungen an die anderen SSIS-Downstreamkomponenten.  
  
 Der Bereich mit Änderungsdaten, der von CDC-Quelle gelesen wird, wird als CDC-Verarbeitungsbereich bezeichnet und mithilfe des CDC-Steuerungstasks bestimmt, der vor Beginn des aktuellen Datenflusses ausgeführt wird. Der CDC-Verarbeitungsbereich wird aus dem Wert einer Paketvariablen abgeleitet, die den Status der CDC-Verarbeitung für eine Gruppe von Tabellen verwaltet.  
  
 Die CDC-Quelle extrahiert Daten mithilfe einer Datenbanktabelle, Sicht oder SQL-Anweisung aus einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank.  
  
 Die CDC-Quelle verwendet die folgenden Konfigurationen:  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -ADO.NET-Verbindungs-Manager, um auf die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -CDC-Datenbank zuzugreifen. Weitere Informationen zum Konfigurieren der CDC-Quellverbindung finden Sie unter [Quellen-Editor für CDC &#40;Seite „Verbindungs-Manager“&#41;](../cdc-source-editor-connection-manager-page.md).  
  
-   Für CDC aktivierte Tabelle.  
  
-   Name der Aufzeichnungsinstanz der ausgewählten Tabelle (falls mehr als eine vorhanden ist).  
  
-   Änderungsverarbeitungsmodus  
  
-   Name der CDC-Statuspaketvariablen, auf deren Grundlage der CDC-Verarbeitungsbereich bestimmt wird. Die CDC-Quelle ändert diese Variable nicht.  
  
 Die von der CDC-Quelle zurückgegebenen Daten entsprechen den Daten, die von den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-CDC-Funktionen **cdc.fn_cdc_get_all_changes_\<capture-instance-name>** oder **cdc.fn_cdc_get_net_changes_\<capture-instance-name>** (falls verfügbar) zurückgegeben werden. Die einzige optionale Hinzufügung ist die Spalte **__$initial_processing** , in der angegeben wird, ob sich der aktuelle Verarbeitungsbereich mit einem erstmaligen Ladevorgang der Tabelle überschneiden kann. Weitere Informationen zur erstmaligen Verarbeitung finden Sie unter [CDC Control Task](../control-flow/cdc-control-task.md).  
  
 Die CDC-Quelle weist eine reguläre Ausgabe und eine Fehlerausgabe auf.  
  
## <a name="error-handling"></a>Fehlerbehandlung  
 Die CDC-Quelle verfügt über eine Fehlerausgabe. Die Komponentenfehlerausgabe enthält die folgenden Ausgabespalten:  
  
-   **Fehlercode**: Der Wert beträgt immer -1.  
  
-   **Fehlerspalte**: Die Quellspalte, die den Fehler verursacht (für Konvertierungsfehler).  
  
-   **Fehlerzeilenspalten**: Die Datensatzdaten, die den Fehler verursachen.  
  
 Je nach Einstellung des Fehlerverhaltens unterstützt die CDC-Quelle das Zurückgeben von Fehlern (Datenkonvertierung, Abschneiden), die während des Extraktionsprozesses in der Fehlerausgabe auftreten. Weitere Informationen finden Sie unter [Quellen-Editor für CDC &#40;Seite „Fehlerausgabe“&#41;](../cdc-source-editor-error-output-page.md).  
  
## <a name="data-type-support"></a>Datentypunterstützung  
 Die CDC-Quellkomponente für Microsoft unterstützt alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentypen, die den richtigen SSIS-Datentypen zugeordnet sind.  
  
## <a name="troubleshooting-the-cdc-source"></a>Problembehandlung der CDC-Quelle  
 Unten sind Informationen zum Durchführen einer Problembehandlung für die CDC-Quelle aufgeführt.  
  
### <a name="use-this-script-to-isolate-problems-and-reproduce-them-in-sql-server-management-studio"></a>Verwenden dieses Skripts zum Isolieren von Problemen und zum Reproduzieren in SQL Server Management Studio  
 Der CDC-Quellvorgang wird vom Vorgang des CDC-Steuerungstasks gesteuert, der vor dem Aufrufen der CDC-Quelle ausgeführt wurde. Der CDC-Steuerungstask bereitet den Wert der CDC-Statuspaketvariablen vor, damit die Start- und End-LSN darin enthalten sein kann. Es wird eine Funktion ausgeführt, die dem folgenden Skript entspricht:  
  
```  
use <cdc-enabled-database-name>  
               declare @start_lsn binary(10), @end_lsn binary(10)  
               set @start_lsn = sys.fn_cdc_increment_lsn(  
                       convert(binary(10),'0x' + '<value-from-state-cs>', 1))  
               set @end_lsn =   
                       convert(binary(10),'0x' + '<value-from-state-ce>', 1)  
               select * from cdc.fn_cdc_get_net_changes_dbo_Table1(@start_lsn,  
@end_lsn, '<mode>')  
```  
  
 Dabei gilt:  
  
-   \<cdc-enabled-database-name> ist der Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank, die die Änderungstabellen enthält.  
  
-   \<value-from-state-cs> ist der Wert, der in der CDC-Statusvariablen als CS/\<value-from-state-cs>/ (CS steht für Current-processing-range-Start) angegeben wird.  
  
-   \<value-from-state-ce> ist der Wert, der in der CDC-Statusvariablen als CE/\<value-from-state-cs>/ (CE steht für Current-processing-range-End) angegeben wird.  
  
-   \<mode> steht für die CDC-Verarbeitungsmodi. Die Verarbeitungsmodi haben einen der folgenden Werte: **All**, **All with Old Values**, **Net**, **Net with Update Mask**, **Net with Merge**.  
  
 Dieses Skript trägt zur Isolierung von Problemen bei, indem sie im [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]reproduziert werden, wo sie leicht reproduziert und identifiziert werden können.  
  
#### <a name="sql-server-error-message"></a>SQL Server-Fehlermeldung  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]gibt möglicherweise die folgende Meldung zurück:  
  
 **Für die Prozedur oder Funktion „cdc.fn_cdc_get_net_changes_\<..>“ wurden zu wenig Argumente bereitgestellt.**  
  
 Dieser Fehler gibt nicht an, dass ein Argument fehlt. Die Bedeutung ist, dass die Start- bzw. End-LSN-Werte in der CDC-Statusvariablen ungültig sind.  
  
## <a name="configuring-the-cdc-source"></a>Konfigurieren der CDC-Quelle  
 Sie können die CDC-Quelle programmgesteuert oder mit dem SSIS-Designer konfigurieren.  
  
 Weitere Informationen finden Sie in einem der folgenden Themen:  
  
-   [Quellen-Editor für CDC &#40;Seite „Verbindungs-Manager“&#41;](../cdc-source-editor-connection-manager-page.md)  
  
-   [Quellen-Editor für CDC &#40;Seite „Spalten“&#41;](../cdc-source-editor-columns-page.md)  
  
-   [Quellen-Editor für CDC &#40;Seite „Fehlerausgabe“&#41;](../cdc-source-editor-error-output-page.md)  
  
 Das Dialogfeld **Erweiterter Editor** enthält die Eigenschaften, die programmgesteuert festgelegt werden können.  
  
 So öffnen Sie das Dialogfeld **Erweiterter Editor** :  
  
-   Klicken Sie auf dem Bildschirm **Datenfluss** des [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] -Projekts mit der rechten Maustaste auf die CDC-Quelle, und wählen Sie **Erweiterten Editor anzeigen**.  
  
 Weitere Informationen zu den Eigenschaften, die Sie im Dialogfeld **Erweiterter Editor** festlegen können, finden Sie unter [CDC Source Custom Properties](cdc-source-custom-properties.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Quellen-Editor für CDC &#40;Seite „Verbindungs-Manager“&#41;](../cdc-source-editor-connection-manager-page.md)  
  
-   [Quellen-Editor für CDC &#40;Seite „Spalten“&#41;](../cdc-source-editor-columns-page.md)  
  
-   [Quellen-Editor für CDC &#40;Seite „Fehlerausgabe“&#41;](../cdc-source-editor-error-output-page.md)  
  
-   [Benutzerdefinierte Eigenschaften der CDC-Quelle](cdc-source-custom-properties.md)  
  
-   [Extrahieren von Änderungsdaten mithilfe der CDC-Quelle](cdc-source.md)  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   Blogeintrag, [Processing Modes for the CDC Source](https://www.mattmasson.com/2012/01/processing-modes-for-the-cdc-source/), auf mattmasson.com.  
  
  
