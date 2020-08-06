---
title: Optimieren der Leistung der Mergereplikation durch nur herunterladbare Artikel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication [SQL Server replication], download-only articles
- articles [SQL Server replication], download-only
- download-only articles
ms.assetid: 8851faa6-e6df-4ea5-a6ea-2a3471680fa3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8414174971792f8a2c256cd564dd1ea224527463
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607685"
---
# <a name="optimize-merge-replication-performance-with-download-only-articles"></a>Optimieren der Leistung der Mergereplikation durch nur herunterladbare Artikel
  Die Mergereplikation bietet zwei Artikeltypen, um die verschiedenen Anwendungsanforderungen zu erfüllen. Veröffentlichungen können der Anwendung entsprechend einen oder mehrere der Artikeltypen enthalten:  
  
-   Standardartikel  
  
-   Nur herunterladbare Artikel  
  
 Nur herunterladbare Artikel bieten eine bessere Leistung im Vergleich zu Standardartikeln und sollten stets verwendet werden, wenn sie sich eignen.  
  
> [!NOTE]  
>  Damit nur herunterladbare Artikel verwendet werden können, muss die Veröffentlichung mindestens einen Kompatibilitätsgrad von 90RTM aufweisen.  
  
## <a name="standard-articles"></a>Standardartikel  
 Standardartikel werden standardmäßig verwendet und bieten den vollen Umfang der Replikationsfunktionen, einschließlich der vielseitigen Konflikterkennung und -lösung. Standardartikel eigenen sich für Tabellen, die von mehreren Abonnenten aktualisiert werden. Andere Objekte als Tabellen, wie z. B. gespeicherte Prozeduren und Sichten, werden immer als Standardartikel veröffentlicht.  
  
## <a name="download-only-articles"></a>Nur herunterladbare Artikel  
 Nur herunterladbare Artikel sind für Anwendungen bestimmt, deren Daten nicht auf den Abonnenten aktualisiert werden, z. B. eine Gruppe von Artikeln, die in einem Produktkatalog enthalten sind. Ein Produktkatalog wird in der Regel auf dem Verleger, nicht auf den Abonnenten aktualisiert. Da nur herunterladbare Artikel nicht auf dem Abonnenten aktualisiert werden können, wird das Nachverfolgen von Metadaten nicht an die Abonnenten gesendet. Das kann den Speicher auf den Abonnenten entlasten und zu einer höheren Leistung führen, besonders bei einer langsamen Netzwerkverbindung.  
  
 Nur herunterladbare Artikel funktionieren in Verbindung mit Clientabonnements: wenn ein Artikel als nur zum Herunterladen angegeben wird, können Zeilen für diesen Artikel nicht auf Abonnenten, die Clientabonnements verwenden, eingefügt, aktualisiert oder gelöscht werden. Verleger und Abonnenten, die den Serverabonnementtyp verwenden (in der Regel Abonnenten, die Daten auf anderen Abonnenten erneut veröffentlichen), können Daten einfügen, aktualisieren und löschen. Weitere Informationen zu Clientabonnements finden Sie unter [Abonnieren von Veröffentlichungen](../subscribe-to-publications.md).  
  
 Informationen zum Angeben eines herunterladbaren Artikels finden Sie unter [Angeben, dass ein neuer Mergetabellenartikel nur herunterladbar ist](../publish/specify-merge-replication-properties.md#download-only).  
  
## <a name="using-different-article-types-in-your-applications"></a>Verwenden unterschiedlicher Artikeltypen in den Anwendungen  
 Wenn Sie die Anforderungen Ihrer Anwendung kennen, können Sie die Vor- und Nachteile zwischen einer maximalen Flexibilität und einer optimalen Leistung abwägen. Wenn z. B. bei einer Anwendung zahlreiche Konflikte und Änderungen auf dem Verleger und den Abonnenten auftreten, wird hier eine aus Standardartikeln bestehende Veröffentlichung verwendet. Einige Anwendungen, z. B. SFA-Anwendungen (Sales Force Automation), enthalten möglicherweise Artikel mit potenziellen Konflikten sowie weitere Artikel, die als Nachschlagetabellen fungieren und nur herunterladbar sind. In Anwendungen zur Dateneingabe, wie Point-of-Sale-Systeme und FFA-Anwendungen (Field Force Automation), werden Daten häufig streng partitioniert, damit keine Konflikte auftreten, und es werden in keinem Fall Daten zwischen Abonnenten ausgetauscht. In diesen Fällen bietet eine Kombination aus nicht überlappenden Partitionen, nur herunterladbare Artikeln und vorausberechneten Partitionen ein Maximum an Leistung und Skalierbarkeit. Weitere Informationen zu nicht überlappenden Partition und vorausberechneten Partitionen finden Sie unter [Parameterized Row Filters](parameterized-filters-parameterized-row-filters.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Artikeloptionen für die Mergereplikation](article-options-for-merge-replication.md)   
 [Optimieren der Mergereplikationsleistung durch bedingtes Nachverfolgen von Löschvorgängen](optimize-merge-replication-performance-with-conditional-delete-tracking.md)  
  
  
