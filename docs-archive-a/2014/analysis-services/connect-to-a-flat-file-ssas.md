---
title: Herstellen einer Verbindung mit einer Flatfile (SSAS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connflatfile.f1
ms.assetid: a365991e-eded-4cd8-89c0-0daf6d658d15
author: minewiskan
ms.author: owend
ms.openlocfilehash: e6bee3c8f7f4b255e6985e8d783365bc8a47599e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87610226"
---
# <a name="connect-to-a-flat-file-ssas"></a>Mit einer Flatfile verbinden (SSAS)
  Auf dieser Seite des **Tabellenimport-Assistenten** können Sie eine Verbindung mit einer Flatfile (.txt), einer durch Tabstopps getrennten Datei (.tab) oder einer durch Trennzeichen getrennten Datei (.csv) herstellen. Um im [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]auf den Assistenten zuzugreifen, klicken Sie im Menü **Modell** auf **Aus Datenquelle importieren**.  
  
 Der ACE-Anbieter muss auf dem Computer installiert sein, um eine Verbindung mit einer Flatfile herzustellen. Weitere Informationen finden Sie unter [Unterstützte Datenquellen &#40;SSAS – tabellarisch&#41;](tabular-models/data-sources-supported-ssas-tabular.md).  
  
> [!NOTE]  
>  Beim Auswählen einer Datei auf dieser Seite werden die Anmeldeinformationen des aktuellen Benutzers verwendet. Der Import ist jedoch nicht erfolgreich, wenn der auf der Seite Identitätswechselinformationen angegebene Benutzer nicht über ausreichend Berechtigungen zum Lesen aus der ausgewählten Datei verfügt.  
  
## <a name="ui-element-list"></a>Liste der Benutzeroberflächenelemente  
 **Anzeigename der Verbindung**  
 Geben Sie einen eindeutigen Namen für diese Datenquellenverbindung ein. Dies ist ein Pflichtfeld.  
  
 **Dateipfad**  
 Geben Sie den vollständigen Pfad der Datei an.  
  
 **Durchsuchen**  
 Navigieren Sie zu einem Speicherort, an dem eine Datei verfügbar ist.  
  
 **Spalten Trennzeichen**  
 Wählen Sie eine Option aus der Liste der verfügbaren Spaltentrennzeichen aus. Dabei sollten Sie ein Spaltentrennzeichen auswählen, dessen Auftreten als Zeichen im Text unwahrscheinlich ist.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|Tabulator (t)|Als Trennzeichen für Spalten dient ein Tabulator (t).|  
|Komma (,)|Als Trennzeichen für Spalten dient ein Komma (,).|  
|Semikolon (;)|Als Trennzeichen für Spalten dient ein Semikolon (;).|  
|Leerzeichen ( )|Als Trennzeichen für Spalten dient ein Leerzeichen ( ).|  
|Doppelpunkt (:)|Als Trennzeichen für Spalten dient ein Doppelpunkt (:).|  
|Senkrechter Strich (&#124;)|Als Trennzeichen für Spalten dient ein senkrechter Strich (&#124;).|  
  
 **Erweitert**  
 Geben Sie die Codierung und die Gebietsschemaoptionen für die Flatfile an.  
  
 **Erste Zeile als Spaltenüberschriften verwenden**  
 Geben Sie an, ob die erste Datenzeile für die Spaltenüberschriften der Zieltabelle verwendet werden soll.  
  
 **Datenvorschau**  
 Zeigen Sie die Daten in der ausgewählten Datei in einer Vorschau an, und verwenden Sie die folgenden Optionen zum Ändern des Datenimports.  
  
> [!NOTE]  
>  Nur die ersten 50 Zeilen in der Datei werden in dieser Vorschau angezeigt.  
  
|Option|BESCHREIBUNG|  
|------------|-----------------|  
|**Kontrollkästchen in der Spaltenüberschrift**|Aktivieren Sie das Kontrollkästchen, um die Spalte in den Datenimport einzuschließen. Deaktivieren Sie das Kontrollkästchen, um die Spalte aus dem Datenimport zu entfernen.|  
|**Schaltfläche mit Abwärtspfeil in der Spaltenüberschrift**|Sortieren und filtern Sie die Daten in der Spalte.|  
  
 **Zeilenfilter löschen**  
 Entfernen Sie alle Filter, die auf die Daten in den Spalten angewendet wurden.  
  
  
