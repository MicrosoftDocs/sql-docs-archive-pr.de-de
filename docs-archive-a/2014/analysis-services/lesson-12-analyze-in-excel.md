---
title: 'Lektion 13: analysieren in Excel | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ce717071-193b-4c99-9654-c7a613e16327
author: minewiskan
ms.author: owend
ms.openlocfilehash: 129956ddc8e755d1f2b298a7ea36307d50f52344
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608037"
---
# <a name="lesson-13-analyze-in-excel"></a>Lektion 13: In Excel analysieren
  In dieser Lektion verwenden Sie die Funktion In Excel analysieren in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] , um Microsoft Excel zu öffnen, automatisch eine Datenquellenverbindung mit der Datenbank für Modellarbeitsbereiche herzustellen und dem Arbeitsblatt automatisch eine PivotTable hinzuzufügen. Die Funktion „In Excel analysieren“ bietet eine schnelle und einfache Möglichkeit, vor der Bereitstellung ihres Modells die Wirksamkeit Ihres Modelldesigns zu testen. Sie führen in dieser Lektion keine Datenanalyse aus. Der Zweck dieser Lektion ist, Sie als Urheber des Modells mit den Tools vertraut zu machen ,die Sie zum Testen Ihres Modelldesigns verwenden können. Die Funktion In Excel analysieren ist für Modellentwickler vorgesehen, während Endbenutzer zum Herstellen einer Verbindung mit bereitgestellten Modelldaten und zum Durchsuchen dieser Daten Clientberichtsanwendungen, z. B. Excel oder [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] , verwenden.  
  
 Um diese Lektion abzuschließen, muss Excel auf dem gleichen Computer wie [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]installiert sein. Weitere Informationen finden Sie unter [Analysieren in Excel &#40;SSAS – tabellarisch&#41;](tabular-models/analyze-in-excel-ssas-tabular.md).  
  
 Geschätzte Zeit zum Bearbeiten dieser Lektion: **20 Minuten**  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Dieses Thema ist Teil eines Tutorials zur Tabellenmodellierung, das in der richtigen Reihenfolge absolviert werden sollte. Sie sollten vor dem Ausführen der Aufgaben in dieser Lektion die vorherige Lektion abgeschlossen haben: [Lektion 11: Erstellen von Partitionen](lesson-10-create-partitions.md).  
  
## <a name="browse-using-the-default-and-internet-sales-perspectives"></a>Durchsuchen mithilfe der Standard- und Internet Sales-Perspektive  
 In diesen ersten Aufgaben durchsuchen Sie das Modell mit der Standardperspektive, die alle Modellobjekte enthält, und mit der Internet Sales-Perspektive, die Sie in "Lektion 8: Erstellen von Perspektiven" erstellt haben. Die Internet Sales-Perspektive enthält nicht das Customer-Tabellenobjekt.  
  
#### <a name="to-browse-by-using-the-default-perspective"></a>So durchsuchen Sie mit der Standardperspektive  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]auf das Menü **Modell** und dann auf **In Excel analysieren**.  
  
2.  Klicken Sie im Dialogfeld **In Excel analysieren** auf **OK**.  
  
     In Excel wird eine neue Arbeitsmappe geöffnet. Es wird eine Datenquellenverbindung mit dem aktuellen Benutzerkonto erstellt, und zum Definieren von Anzeigefeldern wird die Standardperspektive verwendet. Dem Arbeitsblatt wird automatisch eine PivotTable hinzugefügt.  
  
3.  Beachten Sie, dass in Excel in der **PivotTables-Feldliste**die Measures **Date** und **Internet Sales** sowie die Tabellen **Customer**, **Date**, **geography**, **Product**, **Product Category**, **Product Subcategory**und **Internet Sales** mit allen entsprechenden Spalten angezeigt werden.  
  
4.  Schließen Sie Excel, ohne die Arbeitsmappe zu speichern.  
  
#### <a name="to-browse-by-using-the-internet-sales-perspective"></a>So durchsuchen Sie mit der Internet Sales-Perspektive  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]auf das Menü **Modell** und dann auf **In Excel analysieren**.  
  
2.  Lassen Sie im Dialogfeld **In Excel analysieren** die Option **Aktueller Windows-Benutzer** aktiviert, wählen Sie im Dropdownlistenfeld **Perspektive** den Eintrag **Internet Sales**aus, und klicken Sie anschließend auf **OK**. Excel wird geöffnet.  
  
3.  Beachten Sie, dass in Excel in der **PivotTable-Feldliste**die Tabelle Customer aus der Feldliste ausgeschlossen ist.  
  
## <a name="browse-using-roles"></a>Durchsuchen mit Rollen  
 Rollen sind wesentlicher Bestandteil sämtlicher tabellarischer Modelle. Benutzer können keine Daten mit Ihrem Modell aufrufen und analysieren, wenn sie nicht mindestens einer Rolle als Mitglieder hinzugefügt wurden. Die Funktion In Excel analysieren bietet eine Möglichkeit zum Testen der Rollen, die Sie definiert haben.  
  
#### <a name="to-browse-by-using-the-internet-sales-manager-user-role"></a>So durchsuchen Sie das Modell mit der Internet Sales Manager-Benutzerrolle  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]auf das Menü **Modell** und dann auf **In Excel analysieren**.  
  
2.  Wählen Sie im Dialogfeld **In Excel analysieren** in **Geben Sie den Benutzernamen oder die Benutzerrolle zum Herstellen einer Verbindung mit dem Modell an**die Option **Rolle**aus, wählen Sie im Dropdownlistenfeld **Internet Sales Manager**aus, und klicken Sie anschließend auf **OK**.  
  
     In Excel wird eine neue Arbeitsmappe geöffnet. Es wird automatisch eine PivotTable erstellt. Die PivotTable-Feldliste enthält alle Datenfelder, die im neuen Modell verfügbar sind.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Wenn Sie mit diesem Tutorial fortfahren möchten, wechseln Sie zur nächsten Lektion: [Lektion 14: Bereitstellen](lesson-13-deploy.md).  
  
  
