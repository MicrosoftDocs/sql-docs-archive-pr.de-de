---
title: Dialog Feld "Datenquellen Eigenschaften", "Allgemein" | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.datasourceproperties.general.f1
- "10120"
ms.assetid: 44b5edd3-5c11-4d3d-91b8-5871aa0572ed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c79ad70cdd4dcb10e1abce1102fa39eef4c67461
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608403"
---
# <a name="data-source-properties-dialog-box-general"></a>Datenquelleneigenschaften (Dialogfeld), Allgemein
  Mithilfe der Registerkarte **Allgemein** im Dialogfeld **Datenquelleneigenschaften** können Sie die Verbindungsinformationen für eine Datenquelle im Bericht anzeigen und ändern.  
  
## <a name="options"></a>Tastatur  
 **Name**  
 Geben Sie den Namen der Datenquelle ein. Der Datenquellenname muss innerhalb des Berichts eindeutig sein. Standardmäßig wird der Datenquelle ein allgemeiner Name, wie DataSource1 oder DataSource2, zugewiesen.  
  
 **Eingebettete Verbindung**  
 Aktivieren Sie diese Option, wenn Sie keine freigegebene Datenquelle verwenden möchten.  
  
 **Type**  
 Wählen Sie eine Datenverarbeitungserweiterung aus. In der Liste werden alle registrierten Erweiterungen aufgeführt.  
  
 **Verbindungszeichenfolge**  
 Geben Sie eine Verbindungszeichenfolge für die Datenquelle ein. Klicken Sie auf **Bearbeiten** , um die Verbindungszeichenfolge mithilfe des Dialogfeldes **Verbindungseigenschaften** zu erstellen. Klicken Sie auf die Schaltfläche **Ausdruck** (*fx*), um den Ausdruck zu bearbeiten.  
  
 **Freigegebenen Datenquellenverweis verwenden**  
 Wählen Sie diese Option aus, um einen Link zu einer freigegebenen Datenquelle herzustellen. Wählen Sie in der Dropdownliste eine freigegebene Datenquelle aus. Um die ausgewählte Datenquelle zu bearbeiten, klicken Sie auf **Bearbeiten**. Falls die Option **Freigegebenen Datenquellenverweis verwenden** aktiviert ist, sind die Optionen **Typ** und **Verbindungszeichenfolge** deaktiviert.  
  
 **Einzelne Transaktion bei der Verarbeitung der Abfragen verwenden**  
 Wählen Sie diese Option, um anzugeben, dass Datasets, die diese Datenquelle verwenden, in einer einzelnen Transaktion für die Datenbank ausgeführt werden. Um Transaktionen für Unterberichte, die die gleiche Datenquelle verwenden, einzuschließen, setzen Sie die Option **MergeTransactions** im Eigenschaftenabschnitt **Sonstige** des Unterberichts im Bereich **Eigenschaften** auf **True** .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Hinzufügen von Daten zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](report-data/report-datasets-ssrs.md)   
 [Erstellen einer eingebetteten oder freigegebenen Datenquelle &#40;SSRS-&#41;](../../2014/reporting-services/create-an-embedded-or-shared-data-source-ssrs.md)   
 [Datenverbindungen, Datenquellen und Verbindungs Zeichenfolgen in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Datenquelleneigenschaften (Dialogfeld), Anmeldeinformationen](../../2014/reporting-services/data-source-properties-dialog-box-credentials.md)  
  
  
