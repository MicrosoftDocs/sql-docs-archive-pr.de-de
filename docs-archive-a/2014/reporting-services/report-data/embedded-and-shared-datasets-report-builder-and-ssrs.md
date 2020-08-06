---
title: Eingebettete und freigegebene Datasets (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: adc95cc0-d15a-413d-bc5a-302eab37a069
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 21b6136433d3fca56f3a98825e3d0ab9c0cf42e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87726565"
---
# <a name="embedded-and-shared-datasets-report-builder-and-ssrs"></a>Eingebettete und freigegebene Datasets (Berichts-Generator und SSRS)
  In einem Bericht stellt ein Dataset Berichtsdaten dar, die als Ergebnis der Ausführung einer Abfrage für eine externe Datenquelle zurückgegeben werden. Das Dataset hängt von der Datenverbindung ab, die Informationen zur externen Datenquelle enthält. Die Daten selbst sind nicht in der Berichtsdefinition enthalten. Das Dataset enthält einen Abfragebefehl, eine Feldauflistung, Parameter, Filter und Datenoptionen, mit denen die Groß- und Kleinschreibung berücksichtigt und eine Sortierung vorgenommen werden kann. Die folgenden beiden Datasettypen stehen zur Verfügung:  
  
-   **Freigegebene Datasets.** Ein freigegebenes Dataset wird auf einem Berichtsserver veröffentlicht und kann in mehreren Berichten verwendet werden. Ein freigegebenes Dataset muss auf einer freigegebenen Datenquelle basieren. Ein freigegebenes Dataset kann zwischengespeichert und durch Erstellen eines Cacheaktualisierungsplans geplant werden.  
  
-   **Eingebettete Datasets.** Eingebettete Datasets werden in nur einem Bericht definiert und verwendet.  
  
 Der Unterschied zwischen den beiden Datasettypen ist die Art der Erstellung, Speicherung und Verwaltung.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="shared-datasets"></a>Freigegebene Datasets  
 Verwenden Sie ein freigegebenes Dataset, um eine Abfrage bereitzustellen, die in mehreren Berichten verwendet werden kann. Freigegebene Datasets werden auf dem Berichtsserver gespeichert und separat von Berichten oder freigegebenen Datenquellen verwaltet. Ein Berichtsserveradministrator kann die Abfrage z. B. aktualisieren, damit Benutzer von einer verbesserten Indizierung oder einer anderweitigen Optimierung der Abfrageleistung profitieren können.  
  
 Es wird empfohlen, so oft wie möglich freigegebene Datasets zu verwenden. Sie können eine Abfrage optimieren oder Abfrageergebnisse zwischenspeichern, um die Berichtsleistung zu verbessern. Freigegebene Datasets vereinfachen die Verwaltung des Datenzugriffs und verbessern die Sicherheit und Leistung der Berichte und der darin verwendeten Datasets.  
  
 Im Berichts-Designer können Sie freigegebene Datasets als Teil eines Berichtsprojekts erstellen und steuern, ob sie auf einem Berichtsserver bereitgestellt werden sollen. Sie können nicht zu einem Berichtsserver navigieren und ein freigegebenes Dataset auswählen, das dem Bericht hinzugefügt werden soll.  
  
 In Berichts-Generator können Sie folgende Aufgaben ausführen:  
  
1.  Um ein freigegebenes Dataset zu erstellen, verwenden Sie die Entwurfsansicht für freigegebene Datasets. Sie können es auf einem Berichtsserver oder einer SharePoint-Website speichern, um des für andere Berichte freizugeben. Sie können auch zum Berichtsserver navigieren und das vorhandene freigegebene Dataset bearbeiten. In dieser Ansicht können Sie eine Abfrage erstellen und alle Datasetoptionen festlegen. Weitere Informationen finden Sie unter [Shared Dataset Design View (Report Builder) (Entwurfsansicht für freigegebene Datasets (Berichts-Generator))](../report-builder/shared-dataset-design-view-report-builder.md).  
  
2.  Öffnen Sie den Berichts-Generator in der Berichtsentwurfsansicht, um dem Bericht ein freigegebenes Dataset hinzuzufügen. Wechseln Sie von einem Assistenten oder dem Berichtsdatenbereich zum Berichtsserver, und wählen Sie das freigegebene Dataset aus, das dem Bericht hinzugefügt werden soll. In dieser Ansicht können außer dem Hinzufügen von Feldern keine Änderungen an der Abfrage vorgenommen werden. Sie können andere Datenoptionen überschreiben und Filter hinzufügen. Es ist nicht möglich, Filter zu entfernen.  
  
3.  In der folgenden Tabelle werden die Eigenschaften verglichen, die für die Definition des freigegebenen Datasets auf dem Berichtsserver und die Instanz des freigegebenen Datasets in der Berichtsdefinition konfiguriert werden können.  
  
    |Eigenschaft|Konfigurationshinweise für die Definition|Konfigurationshinweise für die Instanz|  
    |--------------|--------------------------------------------|------------------------------------------|  
    |Abfragetext|Die Abfrage kann konfiguriert werden, einschließlich der Definition als Ausdruck.|Die Abfrage kann nicht geändert werden.|  
    |Abfrageparameter|Auf Berichtsparameter kann nicht verwiesen werden.<br /><br /> Schließt Standardwerte ein.<br /><br /> Schließt eine Markierung für den Schreibschutz ein.|Parameter, die in der Definition nicht als schreibgeschützt markiert sind, können konfiguriert werden.|  
    |Filter|Definieren von Filtern|Datasetfilter, die Teil der Definition sind, können nicht angezeigt oder geändert werden.<br /><br /> Zusätzliche Filter können erstellt werden.|  
    |Data source|Muss eine freigegebene Datenquelle sein.|Die Datenquelle kann nicht geändert werden.|  
    |Felder|Felder im Abfragebefehl<br /><br /> Berechnete Felder sind kein Teil der Datasetdefinition.|Felder anzeigen, aber nicht ändern<br /><br /> Die Feldauflistung ist statisch und basiert auf der Abfrage, die beim Hinzufügen des freigegebenen Datasets zum Berichts vorlag. Klicken Sie im Dialogfeld **Dataseteigenschaften** auf **Felder aktualisieren** , um die Auflistung zu aktualisieren. Die tatsächliche Feldauflistung entspricht dem Rückgabeergebnis der aktuellen Abfrage in der Definition.<br /><br /> Berechnete Felder hinzufügen|  
    |Dataset|Datenoptionen wie z. B. die Berücksichtigung der Groß- und Kleinschreibung|Datenoptionen in der Instanz können überschrieben werden.|  
  
## <a name="embedded-datasets"></a>Eingebettete Datasets  
 Verwenden Sie ein eingebettetes Dataset, wenn Sie Daten aus einer externen Datenquelle abrufen möchten, die nur in einem Bericht verwendet werden sollen. Eingebettete Datasets sind nützlich, wenn Sie eine Abfrage erstellen möchten, die über keine anderen Abhängigkeiten verfügt, und die Sie nicht für mehrere Berichte verwenden müssen.  
  
 Um ein eingebettetes Dataset zu erstellen oder zu bearbeiten, verwenden Sie den Berichtsdatenbereich. Nachdem Sie ein Dataset erstellt haben, können Sie die Eigenschaften im Dialogfeld **Dataseteigenschaften** konfigurieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Eingebettete und freigegebene Datenverbindungen oder Datenquellen &#40;Berichts-Generator und SSRS&#41;](../embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md)   
 [Erstellen eines freigegebenen Datasets oder eingebetteten Datasets &#40;Berichts-Generator und SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)   
 [Hinzufügen von Daten zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](report-datasets-ssrs.md)   
 [Datasetfeld-Sammlung &#40;Berichts-Generator und SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md)   
 [Datenverbindungen, Datenquellen und Verbindungs Zeichenfolgen in Berichts-Generator](../data-connections-data-sources-and-connection-strings-in-report-builder.md)   
 [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)  
  
  
