---
title: Zwischenspeichern von freigegebenen Datasets (SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4acb1bbe-1c04-4979-b893-dc1b1c5039b6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5b08149b075ae3fd267baf2dad0ca342457958c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619613"
---
# <a name="cache-shared-datasets-ssrs"></a>Zwischenspeichern von freigegebenen Datasets (SSRS)
  Abfrageergebnisse für ein freigegebenes Dataset können in einen Cache kopiert werden, um konsistente Daten für mehrere Berichte bereitzustellen und die Antwortzeit für die Datasetabfrage zu verbessern. Freigegebene Datasets können ähnlich wie Berichte so konfiguriert werden, dass sie bei der erstmaligen Verwendung oder nach einem angegebenen Zeitplan zwischengespeichert werden.  
  
 Ein freigegebenes Dataset kann in mehreren Berichten enthalten oder Teil einer Komponentendefinition sein. Indem Sie das freigegebene Dataset zwischenspeichern, stellen Sie für alle Berichte, die das Dataset verwenden, konsistente Daten bereit und reduzieren gleichzeitig die Anzahl der in der externen Datenquelle ausgeführten Datasetabfragen.  
  
 Die folgende Liste enthält Beispiele dafür, wann ein freigegebenes Dataset zwischengespeichert werden sollte:  
  
-   Die Ausführung der Abfrage nimmt viel Zeit in Anspruch.  
  
-   Die Abfrage verwendet Parameter, die Anzahl der Parameterkombinationen ist jedoch meist klein. Durch jede Kombination werden zwischengespeicherte Abfrageergebnisse generiert.  
  
-   Die Abfrage wird täglich, wöchentlich oder monatlich zu festen Zeiten ausgeführt.  
  
-   Die Abfrage wird in Reaktion auf einen Verweis auf ein freigegebenes Dataset in einem Bericht ausgeführt, der per E-Mail übermittelt wird, und es wird erwartet, dass eine große Anzahl von Personen in kurzer Zeit auf den Link klicken wird.  
  
-   Die folgende Liste enthält Beispiele dafür, wann ein freigegebenes Dataset nicht zwischengespeichert werden sollte:  
  
-   Die Abfrageergebnisse müssen immer die neuesten Daten enthalten.  
  
-   Die Abfrage wird schnell ausgeführt.  
  
-   Die Abfrage wird selten ausgeführt.  
  
-   Die Abfrage verwendet Parameter, die Anzahl der Parameterkombinationen ist groß, und keine Kombination ist wahrscheinlicher als eine andere.  
  
-   Für die Datenquelle, auf der das freigegebene Dataset basiert, werden Anmeldeinformationen angefordert oder integrierte Windows-Anmeldeinformationen verwendet.  
  
-   Der Filter für das freigegebene Dataset oder die Abfrage enthält einen Ausdruck mit einem Verweis auf die globale User-Auflistung.  
  
 Wenn ein Benutzer Berichtsparameterwerte auswählt, die sich von den Standardwerten unterscheiden, die für das zwischengespeicherte Resultset angegeben wurden, wird die Datasetabfrage aktiv ausgeführt, und die zwischengespeicherten Ergebnisse werden nicht für diese Abfrage verwendet.  
  
## <a name="caching-shared-datasets"></a>Zwischenspeichern freigegebener Datasets  
 Um das Zwischenspeichern für ein freigegebenes Dataset zu aktivieren, müssen Sie die Cacheoption für das freigegebene Dataset auswählen. Nachdem das Zwischenspeichern aktiviert wurde, werden die Abfrageergebnisse für ein freigegebenes Dataset bei der ersten Verwendung in den Cache kopiert. Wenn das freigegebene Dataset über Parameter verfügt, wird durch jede Parameterkombination ein neuer Eintrag im Cache erstellt.  
  
 Während die Abfrageergebnisse für eine bestimmte Parameterkombination im Cache enthalten sind, verwendet jeder Bericht, dessen Verarbeitung gestartet wird und der einen Verweis auf das freigegebene Dataset mit den jeweiligen Parameterwerten enthält, die zwischengespeicherten Daten.  
  
 Sie können angeben, wie lange die Daten im Cache beibehalten werden, bevor sie ungültig werden. Weitere Informationen finden Sie unter [Zwischenspeichern (Seite), Freigegebene Datasets &#40;Berichts-Manager&#41;](../caching-page-shared-datasets-report-manager.md).  
  
## <a name="preloading-the-cache"></a>Vorabladen des Caches  
 Sie können den Cache vorab laden, indem Sie einen Cacheaktualisierungsplan erstellen. Mit einem Aktualisierungsplan können Sie unter Verwendung eines elementspezifischen Zeitplans oder eines freigegebenen Zeitplans angeben, wie oft der Cache aktualisiert werden soll. Damit nicht mehrere Cacheeinträge für das gleiche Element gespeichert werden, sollte der angegebene Zeitplan genügend Zeit zur Abfrageverarbeitung in der externen Datenquelle vorsehen. Wenn die Abfrageausführung z. B. 20 Minuten benötigt, sollte der Aktualisierungszeitplan größer als 20 Minuten sein. Weitere Informationen finden Sie unter [Schedules](../subscriptions/schedules.md).  
  
 Beim Erstellen eines Cacheaktualisierungsplans für ein freigegebenes Dataset gelten die folgenden Bedingungen.  
  
-   Für das freigegebene Dataset muss das Zwischenspeichern aktiviert sein.  
  
-   Von der freigegebenen Datenquelle, von der das freigegebene Dataset abhängig ist, dürfen keine Anmeldeinformationen angefordert bzw. integrierte Windows-Anmeldeinformationen verwendet werden.  
  
-   Wenn das freigegebene Dataset über Parameter verfügt, müssen Sie statische Standardwerte für alle Parameter angeben, die nicht als schreibgeschützt gekennzeichnet sind. Schreibgeschützte Parameter verwenden immer den Standardwert. Um ein freigegebenes Dataset für mehrere Parameterkombinationen zwischenzuspeichern, müssen Sie einen separaten Cacheaktualisierungsplan für jede Kombination von Werten erstellen. Parameter können keine Verweise auf andere Datasets enthalten.  
  
-   Jeder Cacheaktualisierungsplan ist nur einem freigegebenen Dataset oder Bericht zugeordnet.  
  
-   Sie benötigen die ReadPolicy-Berechtigung und UpdatePolicy-Berechtigung für das freigegebene Dataset.  
  
 Cacheaktualisierungspläne können sowohl auf freigegebene Datasets als auch auf Berichte angewendet werden. Weitere Informationen finden Sie unter [Optionen zur Cacheaktualisierung (Berichts-Manager)](../cache-refresh-options-report-manager.md).  
  
## <a name="conditions-that-cause-cache-expiration"></a>Bedingungen, die zum Ablaufen des Caches führen  
 Die folgenden Bedingungen können bewirken, dass ein Cache für ein freigegebenes Dataset ungültig wird.  
  
-   Eine Zeitplanbedingung läuft ab. Das Timeout für den Cache oder die Ablaufzeit wird erreicht.  
  
-   Ein freigegebener Zeitplan wird gelöscht.  
  
-   Änderungen an einem freigegebenen Zeitplan. Freigegebene Zeitpläne können angehalten werden, was sich auch auf die Ablaufzeit eines Caches auswirkt.  
  
-   Die Abfragedefinition für das freigegebene Dataset wird geändert.  
  
-   Die Anmeldeinformationen für die freigegebene Datenquelle, von der das freigegebene Dataset abhängig ist, werden geändert.  
  
-   Die Cacheoptionen für das freigegebene Dataset werden geändert.  
  
-   Die Standardwerte für schreibgeschützte Parameter für das freigegebene Dataset werden geändert.  
  
-   Die Filter, die Teil der Definition für das freigegebene Dataset sind, werden geändert.  
  
-   Das freigegebene Dataset wird vom Berichtsserver gelöscht. Wenn ein freigegebenes Dataset gelöscht wird, werden zugeordnete zwischengespeicherte Kopien und Cacheaktualisierungspläne ebenfalls gelöscht.  
  
 Aktualisierungen an Cacheaktualisierungsplänen für freigegebene Datasets haben keinen Einfluss auf Berichte, die bereits verarbeitet werden. Aktualisierungen an einem Cacheaktualisierungsplan wirken sich nur auf zukünftig gestartete Berichte aus, die auf das freigegebene Dataset verweisen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von freigegebenen Datasets](../report-data/manage-shared-datasets.md)  
  
  
