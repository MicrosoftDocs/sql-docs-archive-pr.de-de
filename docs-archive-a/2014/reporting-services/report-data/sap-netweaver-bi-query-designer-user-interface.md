---
title: Benutzeroberfläche des Abfrage-Designers für SAP NetWeaver BI | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10014"
- sql12.rtp.rptdesigner.dataview.sapbwquerydesigner.f1
helpviewer_keywords:
- data sources [Reporting Services], SAP NetWeaver Business Intelligence
- SAP NetWeaver Business Intelligence [Reporting Services], query designer
- query designers [Reporting Services]
ms.assetid: 102da66e-ca31-41aa-ab4b-c9b5ab752a72
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2c1bd7293021a1a755c8189f354af7a54f7e4737
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615307"
---
# <a name="sap-netweaver-bi-query-designer-user-interface"></a>Benutzeroberfläche des Abfrage-Designers für SAP NetWeaver BI
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] stellt einen grafischen Abfrage-Designer zum Erstellen von MDX-Abfragen (Multidimensional Expression) für eine SAP NetWeaver® Business Intelligence-Datenquelle bereit. Der grafische MDX-Abfrage-Designer verfügt über zwei Modi: Entwurfsmodus und Abfragemodus. Jeder Modus bietet einen Metadatenbereich, aus dem Sie Elemente aus einem InfoCube, einem MultiProvider oder einer für die Datenquelle definierten, webfähigen Abfrage ziehen können, um eine MDX-Abfrage zu erstellen, die bei der Berichtsverarbeitung Daten abruft.

> [!IMPORTANT]
>  Benutzer greifen auf Datenquellen zu, wenn sie Abfragen erstellen und ausführen. Sie sollten minimale Berechtigungen für die Datenquellen gewähren, z. B. nur Leseberechtigungen.

 Weitere Informationen zum Arbeiten mit einer mehrdimensionalen SAP-Datenquelle finden Sie unter [SAP NetWeaver BI-Verbindungstyp(SSRS)](sap-netweaver-bi-connection-type-ssrs.md).

 In diesem Abschnitt werden die Schaltflächen auf der Symbolleiste und die Bereiche des Abfrage-Designers für jeden Modus des grafischen Abfrage-Designers beschrieben.

## <a name="graphical-query-designer-in-design-mode"></a>Grafischer Abfrage-Designer im Entwurfsmodus
 Wenn Sie in der Datenansicht des Berichts-Designers ein Dataset mit einer [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] -Datenquelle bearbeiten, wird der grafische Abfrage-Designer im Entwurfsmodus geöffnet. In der folgenden Abbildung werden die Bereiche für den Entwurfsmodus bezeichnet.

 ![Abfrage-Designer mithilfe von MDX im Entwurfsmodus](../media/rsqd-dssapbw-mdx-designmode.gif "Verwenden von MDX im Entwurfsmodus des Abfrage-Designers")

 In der folgenden Tabelle sind die Bereiche in diesem Modus aufgeführt.

|Bereich|Funktion|
|----------|--------------|
|Cube auswählen (Schaltfläche)|Zeigt den zurzeit ausgewählten InfoCube, MultiProvider oder die zurzeit ausgewählte webfähige Abfrage an.|
|Metadaten (Bereich)|Zeigt eine hierarchische Liste von InfoCubes, MultiProvidern und Abfragen an. An der Datenquelle erstellte Abfragen werden möglicherweise unter dem entsprechenden Cube angezeigt.|
|Berechnete Elemente (Bereich)|Zeigt die aktuell definierten berechneten Elemente an, die für eine Verwendung in der Abfrage verfügbar sind.|
|Daten (Bereich)|Zeigt die Ergebnisse des Ausführens der Abfrage an.|

 Sie können Dimensionen und Kennzahlen aus dem Metadatenbereich und berechnete Elemente aus dem Bereich Berechnete Elemente in den Datenbereich ziehen. Wenn die Umschaltfläche **AutoExecute** auf der Symbolleiste aktiviert ist, führt der Abfrage-Designer die Abfrage jedes Mal aus, wenn Sie ein Objekt im Datenbereich ablegen. Wenn **AutoExecute** deaktiviert ist, führt der Abfrage-Designer die Abfrage nicht aus, während Sie Änderungen am Datenbereich vornehmen. Sie können die Abfrage mithilfe der Schaltfläche **Ausführen** auf der Symbolleiste manuell ausführen.

### <a name="toolbar-for-the-graphical-query-designer-in-design-mode-toolbar"></a>Symbolleiste für den grafischen Abfrage-Designer im Entwurfsmodus
 Die Symbolleiste des Abfrage-Designers stellt Schaltflächen bereit, die Ihnen beim Entwurf von MDX-Abfragen mit der grafischen Oberfläche helfen. In der folgenden Tabelle werden die Schaltflächen und ihre Funktionen beschrieben.

|Taste|BESCHREIBUNG|
|------------|-----------------|
|**Als Text bearbeiten**|Wechseln zwischen dem textbasierten Abfrage-Designer und dem grafischen Abfrage-Designer. Nicht verfügbar für diesen Datenquellentyp.|
|**Importieren**|Importieren einer vorhandenen Abfrage aus einer Berichtsdefinitionsdatei (.rdl) im Dateisystem. Weitere Informationen finden Sie unter [Erstellen von Berichten zu eingebetteten und freigegebenen Datasets &#40;Berichts-Generator und SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).|
|![Datasetfelder aktualisieren](../media/rsqdicon-refreshfields.gif "Aktualisieren der Datasetfelder")|Aktualisieren von Metadaten aus der Datenquelle.|
|![Berechnetes Element hinzufügen](../../analysis-services/media/rsqdicon-addcalculatedmember.gif "Berechnetes Element hinzufügen")|Zeigt das Dialogfeld **Generator für berechnete Elemente** an.|
|![Zum Anzeigen von leeren Zellen umschalten](../../analysis-services/media/rsqdicon-showemptycells.gif "Leere Zellen anzeigen/nicht anzeigen")|Umschalten zwischen Einblenden und Ausblenden leerer Zellen im Datenbereich. (Dies entspricht dem Verwenden der NON EMPTY-Klausel in MDX.)|
|![Abfrage automatisch ausführen](../../analysis-services/media/rsqdicon-autoexecute.gif "Abfrage automatisch ausführen")|Automatisches Ausführen der Abfrage und Anzeigen des Ergebnisses, sobald eine Änderung vorgenommen wird, beispielsweise Löschen einer Spalte im Datenbereich. Die Ergebnisse werden im Datenbereich angezeigt.|
|![Löschen](../../analysis-services/media/rsqdicon-delete.gif "Löschen")|Löschen der ausgewählten Spalte im Datenbereich aus der Abfrage.|
|![Symbol für das Dialogfeld „Abfrageparameter“](../../analysis-services/media/iconqueryparameter.gif "Symbol für das Dialogfeld „Abfrageparameter“")|Anzeigen des Dialogfelds **Variablen** . Diese Schaltfläche ist nur aktiviert, wenn es sich bei dem ausgewählten Cube um einen Abfragecube handelt (da nur Abfragecubes Variablen unterstützen). Wenn Sie einer Variablen einen Standardwert zuweisen, wird ein entsprechender Berichtsparameter erstellt.|
|![Abfrage ausführen](../../analysis-services/media/rsqdicon-run.gif "Abfrage ausführen")|Führt die Abfrage aus und zeigt die Ergebnisse im Datenbereich an.|
|![Abfrage abbrechen](../../analysis-services/media/rsqdicon-cancel.gif "Abfrage abbrechen")|Abbrechen der Abfrage.|
|![In Entwurfsmodus wechseln](../../analysis-services/media/rsqdicon-designmode.gif "Wechselt in den Entwurfsmodus")|Umschalten zwischen Entwurfsmodus und Abfragemodus.|

## <a name="graphical-query-designer-in-query-mode"></a>Grafischer Abfrage-Designer im Abfragemodus
 Klicken Sie zum Umschalten des grafischen Abfrage-Designers in den Abfragemodus auf der Symbolleiste auf die Umschaltfläche **Entwurfsmodus** .

 In der folgenden Abbildung werden die Teile des Abfrage-Designers im Abfragemodus angezeigt.

 ![MDX-Abfrage-Designer für SAP BW in der Abfrageansicht](../media/rsqd-dssapbw-mdx-querymode.gif "MDX-Abfrage-Designer für SAP BW in der Abfrageansicht")

 Die folgende Tabelle beschreibt die Funktion jedes Bereichs.

|Bereich|Funktion|
|----------|--------------|
|Cube auswählen (Schaltfläche)|Zeigt den zurzeit ausgewählten InfoCube, MultiProvider oder sonstigen Cube an.|
|Metadaten/Funktionen (Bereich)|Zeigt ein Fenster im Registerformat mit einer Liste verfügbarer Metadaten oder Funktionen an, die zum Erstellen des Abfragetexts verwendet werden können.|
|Variablen (Bereich)|Zeigt die zurzeit definierten Variablen an, die für die Verwendung in der Abfrage verfügbar sind.|
|Abfragebereich|Zeigt den aktuellen Abfragetext an.|
|Ergebnisbereich|Zeigt die Ergebnisse der Abfrage an.|

 Aus dem Metadatenbereich können Sie Kennzahlen und Dimensionen von der Registerkarte **Metadaten** in den MDX-Abfragebereich ziehen. Der technische Name für die Metadaten wird an der Cursorposition eingefügt. Sie können Funktionen von der Registerkarte **Funktionen** in den MDX-Abfragebereich ziehen. Wenn Sie die Abfrage ausführen, zeigt der Ergebnisbereich die Ergebnisse für die aktuelle MDX-Abfrage an.

 Wenn es sich bei dem von Ihnen ausgewählten Cube um eine webfähige Abfrage handelt, werden Sie aufgefordert, statische Standardwerte für die vorhandenen Variablen festzulegen. Sie können dann Variablen in den MDX-Abfragebereich ziehen.

 Im Metadatenbereich und im Variablenbereich werden Anzeigenamen angezeigt. Wenn Sie die Objekte im MDX-Abfragebereich ablegen, sehen Sie, wie die technischen Namen, die von der Datenquelle benötigt werden, in die MDX-Abfrage eingegeben werden.

### <a name="toolbar-for-the-graphical-query-designer-in-query-mode"></a>Symbolleiste für den grafischen Abfrage-Designer im Abfragemodus
 Die Symbolleiste des Abfrage-Designers stellt Schaltflächen bereit, die Ihnen beim Entwurf von MDX-Abfragen mit der grafischen Oberfläche helfen. Die Schaltflächen der Symbolleiste sind im Entwurfs- und Abfragemodus identisch, aber die folgenden Schaltflächen sind für den Abfragemodus nicht aktiviert:

-   **Als Text bearbeiten**

-   **Berechnetes Element hinzufügen** (![Berechnetes Element hinzufügen](../../analysis-services/media/rsqdicon-addcalculatedmember.gif "Berechnetes Element hinzufügen"))

-   **Leere Zellen anzeigen** (![Schaltfläche zum ein-/ausblenden leerer Zellen](../../analysis-services/media/rsqdicon-showemptycells.gif "Leere Zellen anzeigen/nicht anzeigen"))

-   **AutoExecute** (![Abfrage automatisch ausführen](../../analysis-services/media/rsqdicon-autoexecute.gif "Abfrage automatisch ausführen"))

-   **Löschen** (![Löschen](../../analysis-services/media/rsqdicon-delete.gif "Löschen"))

## <a name="see-also"></a>Weitere Informationen
 [Erstellen eines freigegebenen Datasets oder eingebetteten Datasets &#40;Berichts-Generator und SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) [RSReportDesigner-Konfigurationsdatei](../report-server/rsreportdesigner-configuration-file.md)


