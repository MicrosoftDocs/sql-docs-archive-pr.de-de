---
title: Zusammenführen von Partitionen in Analysis Services (SSAS-Multidimensional) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- partitions [Analysis Services], merging
- merging partitions [Analysis Services]
ms.assetid: b3857b9b-de43-4911-989d-d14da0196f89
author: minewiskan
ms.author: owend
ms.openlocfilehash: 42820a202c4da58e21dfd55756b7bb03522ea879
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87724274"
---
# <a name="merge-partitions-in-analysis-services-ssas---multidimensional"></a>Zusammenführen von Partitionen in Analysis Services (SSAS – Mehrdimensional)
  Sie können Partitionen in einer bestehenden [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank zusammenführen, um Faktendaten aus mehreren Partitionen derselben Measuregruppe zu konsolidieren.  
  
 [Gängige Szenarios](#bkmk_Scenario)  
  
 [Anforderungen](#bkmk_prereq)  
  
 [Aktualisieren der Partitionsquelle nach dem Zusammenführen von Partitionen](#bkmk_Where)  
  
 [Besondere Überlegungen für Partitionen, die nach Faktentabelle oder benannter Abfrage segmentiert sind](#bkmk_fact)  
  
 [Zusammenführen von Partitionen mithilfe von SSMS](#bkmk_partitionSSMS)  
  
 [Zusammenführen von Partitionen mithilfe von XMLA](#bkmk_partitionsXMLA)  
  
##  <a name="common-scenarios"></a><a name="bkmk_Scenario"></a>Häufige Szenarien  
 Die am häufigsten vorkommende Konfiguration für die Verwendung von Partitionen umfasst die Trennung von Daten über die Dimension der Zeit. Die den einzelnen Partitionen zugeordnete Zeitgranularität richtet sich nach den für das Projekt geltenden Geschäftsanforderungen. Die Segmentierung kann z. B. nach Jahr erfolgen, wobei das aktuelle Jahr nach Monaten unterteilt und eine separate Partition für den aktiven Monat vorhanden ist. Der Partition für den aktiven Monat werden regelmäßig neue Daten hinzugefügt.  
  
 Wenn der aktive Monat abgeschlossen ist, wird diese Partition wieder mit den Monaten in der Partition für das laufende Jahr zusammengeführt, und der Prozess wird fortgesetzt. Bis zum Ende des Jahres entsteht auf diese Weise eine vollständige neue Jahrespartition.  
  
 Wie dieses Szenario veranschaulicht, kann das Zusammenführen von Partitionen zu einer regelmäßig ausgeführten Routineaufgabe werden. Somit stellt es einen fortschrittlichen Ansatz für das Konsolidieren und Organisieren von Verlaufsdaten dar.  
  
##  <a name="requirements"></a><a name="bkmk_prereq"></a> Anforderungen  
 Partitionen können nur zusammengeführt werden, wenn sie sämtliche der folgenden Kriterien erfüllen:  
  
-   Sie verfügen über dieselbe Measuregruppe.  
  
-   Sie verfügen über die gleiche Struktur.  
  
-   Sie müssen sich im Status Verarbeitet befinden.  
  
-   Sie verfügen über dieselben Speichermodi.  
  
-   Sie enthalten einen identischen Aggregationsentwurf.  
  
-   Sie verfügen über denselben Kompatibilitätsgrad der Zeichenfolgenspeicher (gilt nur für partitionierte Distinct Count Measure-Gruppen).  
  
 Wenn die Zielpartition leer ist (d. h., sie verfügt über einen Aggregationsentwurf, aber keine Aggregationen), werden die Aggregationen für die Quellpartitionen beim Zusammenführen gelöscht. Sie müssen Index verarbeiten, Vollständig verarbeiten oder Standard verarbeiten für die Partition ausführen, um die Aggregationen zu erstellen.  
  
 Remotepartitionen können nur mit anderen Remotepartitionen zusammengeführt werden, die mithilfe derselben [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Remoteinstanz definiert wurden.  
  
> [!NOTE]  
>  Wenn Sie lokale Partitionen mit Remotepartitionen kombinieren, besteht ein alternativer Ansatz in der Erstellung neuer Partitionen, die die kombinierten Daten enthalten. Die nicht mehr benötigten Partitionen werden gelöscht.  
  
 Wenn Sie eine Partition erstellen, die später zusammengeführt werden soll, können Sie beim Erstellen der Partition im Partitions-Assistenten den Aggregationsaufbau einer anderen Partition des Cubes kopieren. Dadurch wird sichergestellt, dass diese Partitionen über den gleichen Aggregationsentwurf verfügen. Beim Zusammenführen werden die Aggregationen der Quellpartition mit den Aggregationen der Zielpartition kombiniert.  
  
##  <a name="update-the-partition-source-after-merging-partitions"></a><a name="bkmk_Where"></a>Aktualisieren der Partitions Quelle nach dem Zusammenführen von Partitionen  
 Partitionen werden nach Abfrage segmentiert, etwa so wie die WHERE-Klausel einer SQL-Abfrage zur Verarbeitung der Daten verwendet wird, oder nach einer Tabelle oder benannten Abfrage, die Daten für die Partition bereitstellt. Die `Source`-Eigenschaft der Partition gibt an, ob die Partition an eine Abfrage oder eine Tabelle gebunden ist.  
  
 Beim Zusammenführen von Partitionen wird der Inhalt der Partitionen konsolidiert, die `Source`-Eigenschaft wird jedoch nicht aktualisiert, um den erweiterten Partitionsbereich widerzuspiegeln. Wenn Sie eine Partition, die ihre ursprüngliche `Source` beibehält, also später erneut verarbeiten, rufen Sie falsche Daten aus dieser Partition ab. Die Partition aggregiert die Daten fälschlicherweise auf der übergeordneten Ebene. Im folgenden Beispiel wird dieses Verhalten veranschaulicht.  
  
 **Das Problem**  
  
 Angenommen, Sie verfügen über einen Cube, der Informationen zu drei nicht alkoholischen Getränken enthält. Er verfügt über drei Partitionen, die dieselbe Faktentabelle verwenden. Diese Partitionen sind nach Produkt segmentiert. Partition 1 enthält Daten über [ColaFull], Partition 2 enthält Daten über [ColaDecaf] und Partition 3 enthält Daten über [ColaDiet]. Wenn Partition 3 in Partition 2 zusammengeführt wird, sind die Daten in der sich ergebenden Partition (Partition 2) richtig und die Cubedaten sind richtig. Wenn Partition 2 verarbeitet wird, kann ihr Inhalt jedoch vom übergeordneten Element auf der Produktebene bestimmt werden. Dieses übergeordnete Element, [SoftDrinks], enthält auch [ColaFull], das Produkt in Partition 1. Durch das Verarbeiten von Partition 2 wird die Partition mit Daten für alle Softdrinks geladen, einschließlich [ColaFull]. Der Cube enthält dann doppelte Daten für [ColaFull] und gibt falsche Daten an Endbenutzer zurück.  
  
 **Die Lösung**  
  
 Die Lösung liegt in der Aktualisierung der `Source`-Eigenschaft. Dabei wird entweder die WHERE-Klausel oder benannte Abfrage angepasst, oder Daten aus den zugrunde liegenden Faktentabellen werden manuell zusammengeführt. So kann sichergestellt werden, dass die nachfolgende Verarbeitung unter Berücksichtigung des erweiterten Partitionsbereichs präzise abläuft.  
  
 In diesem Beispiel können Sie nach dem Zusammenführen von Partition 3 in Partition 2 einen Filter bereitstellen, z.B. ("Product" = 'ColaDecaf' OR "Product" = 'ColaDiet'), um die Daten in der sich ergebenden Partition 2 anzugeben, damit nur Daten über [ColaDecaf] und [ColaDiet] aus der Faktentabelle extrahiert und die zu [ColaFull] gehörenden Daten ausgeschlossen werden. Alternativ können Sie bereits beim Erstellen Filter für Partition 2 und Partition 3 angeben. Diese Filter werden beim Zusammenführen dann kombiniert. In beiden Fällen enthält der Cube nach der Verarbeitung der Partition keine doppelten Daten.  
  
 **Schlussfolgerung**  
  
 Nach dem Zusammenführen von Partitionen sollten Sie `Source` immer daraufhin überprüfen, ob der richtige Filter für die zusammengeführten Daten verwendet wird. Wenn Sie anfänglich eine Partition mit den Verlaufsdaten für Q1, Q2 und Q3 verwendet haben und diese jetzt mit Q4 zusammenführen möchten, müssen Sie Q4 einbeziehen, indem Sie den Filter anpassen. Andernfalls werden bei der nachfolgenden Verarbeitung der Partition fehlerhafte Ergebnisse zurückgegeben, bei denen Q4 nicht berücksichtigt wird.  
  
##  <a name="special-considerations-for-partitions-segmented-by-fact-table-or-named-query"></a><a name="bkmk_fact"></a>Besonderheiten bei Partitionen, die nach Fakten Tabelle oder benannter Abfrage segmentiert sind  
 Zusätzlich zu Abfragen können auch Partitionen nach Tabelle oder benannter Abfrage segmentiert werden. Wenn Quell- und Zielpartition dieselbe Faktentabelle in einer Datenquelle oder Datenquellensicht verwenden, behält die `Source`-Eigenschaft nach dem Zusammenführen von Partitionen Gültigkeit. Sie gibt die Faktentabellendaten für die resultierende Partition an. Da die für die resultierende Partition erforderlichen Fakten in der Faktentabelle vorhanden sind, muss die `Source`-Eigenschaft nicht geändert werden.  
  
 Partitionen, die Daten aus mehreren Faktentabellen oder benannten Abfragen verwenden, erfordern zusätzlichen Arbeitsaufwand. Sie müssen die Fakten aus der Faktentabelle der Quellpartition manuell mit der Faktentabelle der Zielpartition zusammenführen.  
  
 Sie können auch die Quelle einer zusammengeführten Partition in eine benannte Abfrage ändern, die den Inhalt der beiden getrennten Faktentabellen zurückgibt. Wird dieser manuelle Schritt nicht ausgeführt, enthält die Faktentabelle nicht die vollständigen Informationen.  
  
 Aus diesem Grund müssen Partitionen, die segmentierte Daten aus benannten Abfragen abrufen, ebenfalls aktualisiert werden. Die kombinierte Partition muss jetzt über eine benannte Abfrage verfügen, die das kombinierte Resultset zurückgibt, das zuvor aus separaten benannten Abfragen abgerufen wurde.  
  
## <a name="partition-storage-considerations-molap"></a>Überlegungen zum Partitionsspeicher: MOLAP  
 Beim Zusammenführen von MOLAP-Partitionen werden die in den mehrdimensionalen Strukturen der Partitionen gespeicherten Fakten ebenfalls zusammengeführt. Dies führt zu einer in sich vollständigen und konsistenten Partition. Die in MOLAP-Partitionen gespeicherten Fakten sind Kopien der Fakten in der Faktentabelle. Bei einem späteren Verarbeiten der Partition werden die Fakten in der mehrdimensionalen Struktur gelöscht (nur bei einer vollständigen Verarbeitung oder Aktualisierung) und Daten, wie durch die Datenquelle und den Filter der Partition angegeben, aus der Faktentabelle kopiert. Wenn die Quellpartition eine andere Faktentabelle aus der Zielpartition verwendet, muss die Faktentabelle der Quellpartition manuell mit der Faktentabelle der Zielpartition zusammengeführt werden, um sicherzustellen, dass eine vollständige Datenmenge verfügbar ist, wenn die sich ergebende Partition verarbeitet wird. Dies trifft auch zu, wenn die beiden Partitionen auf zwei unterschiedlichen benannten Abfragen basieren.  
  
> [!IMPORTANT]  
>  Eine zusammengeführte MOLAP-Partition mit einer unvollständigen Faktentabelle enthält eine intern zusammengeführte Kopie der Faktentabellendaten und wird bis zu ihrer Verarbeitung einwandfrei ausgeführt.  
  
## <a name="partition-storage-considerations-holap-and-rolap-partitions"></a>Überlegungen zum Partitionsspeicher: HOLAP- und ROLAP-Partitionen  
 Beim Zusammenführen von HOLAP- oder ROLAP-Partitionen, die über verschiedene Faktentabellen verfügen, werden die Faktentabellen nicht automatisch zusammengeführt. Werden die Faktentabellen nicht manuell zusammengeführt, ist nur die mit der Zielpartition verknüpfte Faktentabelle für die sich ergebende Partition verfügbar. Mit der Quellpartition verknüpfte Fakten sind nicht für Drilldowns in der sich ergebenden Partition verfügbar, und beim Verarbeiten der Partition fassen die Aggregationen keine Daten aus der nicht verfügbaren Tabelle zusammen.  
  
> [!IMPORTANT]  
>  Eine zusammengeführte HOLAP- oder ROLAP-Partition mit einer unvollständigen Faktentabelle enthält richtige Aggregationen, jedoch unvollständige Fakten. Abfragen, die auf fehlende Fakten verweisen, geben falsche Daten zurück. Beim Verarbeiten der Partition werden Aggregationen nur aus verfügbaren Fakten berechnet.  
  
 Das Fehlen nicht verfügbarer Fakten wird möglicherweise nicht bemerkt, bis ein Benutzer versucht, einen Drilldown zu Fakten in der nicht verfügbaren Tabelle durchzuführen oder eine Abfrage auszuführen, die Fakten aus der nicht verfügbaren Tabelle erfordert. Da Aggregationen während des Zusammenführens kombiniert werden, geben Abfragen, deren Ergebnisse nur auf Aggregationen basieren, genaue Daten zurück, während andere Abfragen möglicherweise ungenaue Daten zurückgeben. Selbst nach dem Verarbeiten der sich ergebenden Partition ist es möglicherweise nicht erkennbar, dass Daten aus der nicht verfügbaren Faktentabelle fehlen; insbesondere dann, wenn diese nur einen kleinen Anteil der kombinierten Daten darstellen.  
  
 Faktentabellen können vor oder nach dem Zusammenführen von Partitionen zusammengeführt werden. Die Aggregationen zeigen jedoch die zugrundeliegenden Fakten nicht einwandfrei an, bis beide Vorgänge abgeschlossen wurden. Es wird empfohlen, dass Sie HOLAP- oder ROLAP-Partitionen, die auf verschiedene Faktentabellen zugreifen, dann zusammenführen, wenn Benutzer nicht mit dem Cube verbunden sind, der diese Partitionen enthält.  
  
##  <a name="how-to-merge-partitions-using-ssms"></a><a name="bkmk_partitionSSMS"></a>Zusammenführen von Partitionen mithilfe von SSMS  
  
> [!IMPORTANT]  
>  Vor dem Zusammenführen von Partitionen kopieren Sie zunächst die Datenfilterinformationen (häufig die WHERE-Klausel für Filter basierend auf SQL-Abfragen). Nachdem die Zusammenführung abgeschlossen ist, sollten Sie später die Eigenschaft für die Partitionsquelle der Partition aktualisieren, in der die akkumulierten Faktendaten enthalten sind.  
  
1.  Erweitern Sie im Objekt-Explorer den Knoten **Measuregruppen** des Cubes, in dem die zusammenzuführenden Partitionen enthalten sind. Anschließend erweitern Sie **Partitionen**und klicken mit der rechten Maustaste auf die Partition, die das Ziel des Zusammenführungsvorgangs ist. Wenn Sie z. B. vierteljährliche Faktendaten zu einer Partition verschieben, in der jährliche Faktendaten gespeichert sind, wählen Sie die Partition aus, in der die jährlichen Faktendaten enthalten sind.  
  
2.  Klicken Sie auf **Partitionen zusammenführen** , um das Dialogfeld zusammen ** \<partition name> führen** zu öffnen.  
  
3.  Aktivieren Sie unter **Quellpartitionen**das Kontrollkästchen neben jeder Quellpartition, die Sie mit der Zielpartition zusammenführen möchten, und klicken Sie auf **OK**.  
  
    > [!NOTE]  
    >  Quellpartitionen werden sofort gelöscht, nachdem die Quelle mit der Zielpartition zusammengeführt wurde. Aktualisieren Sie den Ordner Partitionen, um den Inhalt nach Ende der Zusammenführung zu aktualisieren.  
  
4.  Klicken Sie mit der rechten Maustaste auf die Partition mit den akkumulierten Daten, und wählen Sie **Eigenschaften**aus.  
  
5.  Öffnen Sie die `Source` -Eigenschaft, und ändern Sie die WHERE-Klausel so, dass Sie die soeben zusammengeführten Partitions Daten enthält. Beachten Sie, dass die- `Source` Eigenschaft nicht automatisch aktualisiert wird. Wenn Sie erneut verarbeiten, ohne zuerst das `Source` zu aktualisieren, erhalten Sie möglicherweise nicht alle erwarteten Daten.  
  
##  <a name="how-to-merge-partitions-using-xmla"></a><a name="bkmk_partitionsXMLA"></a> Zusammenführen von Partitionen mithilfe von XMLA  
 Weitere Informationen zu diesem Thema finden Sie unter [Zusammenführen von Partitionen &#40;XMLA&#41;](../multidimensional-models-scripting-language-assl-xmla/merging-partitions-xmla.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verarbeiten von Analysis Services Objekten](processing-analysis-services-objects.md)   
 [Partitionen &#40;Analysis Services Mehrdimensionale Daten&#41;](../multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)   
 [Erstellen und Verwalten einer lokalen Partition &#40;Analysis Services&#41;](create-and-manage-a-local-partition-analysis-services.md)   
 [Erstellen und Verwalten einer Remote Partition &#40;Analysis Services&#41;](create-and-manage-a-remote-partition-analysis-services.md)   
 [Festlegen des Rück Schreibens von Partitionen](set-partition-writeback.md)   
 [Partitionen mit aktiviertem Schreibzugriff](../multidimensional-models-olap-logical-cube-objects/partitions-write-enabled-partitions.md)   
 [Konfigurieren des Zeichenfolgenspeichers für Dimensionen und Partitionen](configure-string-storage-for-dimensions-and-partitions.md)  
  
  
