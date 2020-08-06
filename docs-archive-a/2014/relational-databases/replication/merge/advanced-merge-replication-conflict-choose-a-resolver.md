---
title: Wählen eines Konfliktlösers | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- default conflict resolver
- articles [SQL Server replication], conflict resolution
- conflict resolution [SQL Server replication], merge replication
ms.assetid: b7dec3fa-d9d9-409d-b946-f9b9a3202829
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0db289e923cab72bf175b172f039ea228c991110
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609829"
---
# <a name="choose-a-resolver"></a>Auswählen von Resolvern
  Beim Auswählen eines Konfliktlösers sollten Sie die Bedeutung der Konfliktlösung in Ihrer Anwendung und die Frage berücksichtigen, ob der standardmäßige prioritätsbasierte Konfliktlöser verwendet werden kann oder ob ein Artikelkonfliktlöser verwendet werden muss.  
  
 Wenn die Daten partitioniert werden, ohne dass mehrere Benutzer in dieselben Partitionen schreiben, und die Replikationstopologie relativ einfach ist (ein Verleger und wenige Abonnenten) sollten Konflikte selten oder nie vorkommen. In diesen Umgebungen ist eine komplexe Konfliktauflösungsstrategie eher nicht notwendig. Es wird eine Strategie empfohlen, die die Standardeinstellungen für die Konfliktlösung, Clientabonnements und eine Richtlinie verwendet, bei der die erste Änderung gewinnt. Wenn die Topologie komplexer ist (z. B. weil Wiederveröffentlichungsabonnenten verwendet werden), sind Serverabonnements mit spezifischen Prioritäten möglicherweise geeigneter.  
  
 Die Verwendung eines Artikelkonfliktlösers wird empfohlen, wenn die Anforderungen in Ihrem Unternehmen eine genauer abgestimmte Lösung als die mit dem Standardkonfliktlöser verfügbare Lösung nötig machen. Wenn Sie sich für die Verwendung eines Artikelkonfliktlösers entscheiden, empfiehlt sich die Verwendung eines Geschäftslogikhandlers. Weitere Informationen finden Sie unter [Ausführen von Geschäftslogik während der Mergesynchronisierung](execute-business-logic-during-merge-synchronization.md).  
  
 Letztendlich sollte sich die Entscheidung, ob der Standardkonfliktlöser oder ein Artikelkonfliktlöser verwendet wird, nach den Daten und den Geschäftslogikanforderungen der Anwendung richten. Nehmen wir z. B. eine Firma, in der Mitarbeiter in eine Gruppe von nicht partitionierten Tabellen auf unterschiedlichen Abonnenten Kundeneinstufungsdaten eingeben. Die Mitarbeiter gehören unterschiedlichen Funktionskategorien (Filialleiter, Abteilungsleiter, Vertriebsmitarbeiter) an. Für die Entscheidung, welche Daten Priorität erhalten, soll die jeweilige Funktionskategorie herangezogen werden. In diesem Fall kann ein Artikelkonfliktlöser erstellt werden, der beim Auftreten eines Konflikts anhand der Funktionskategorie aus dem Artikel den Prioritätsgewinner bestimmt.  
  
 Wenn die Wahrscheinlichkeit von häufigen Konflikten relativ hoch ist, sollten Sie bei der Implementierung einer Konfliktauflösungsstrategie u. a. die folgenden Punkte berücksichtigen:  
  
|Konfliktlösungsproblem|Empfehlung|  
|-------------------------------|--------------------|  
|Verschiedene Kategorien von Benutzern erfordern verschiedene Prioritätswerte.|Verwenden Sie den Standardkonfliktlöser, und erstellen Sie Serverabonnements mit unterschiedlichen Prioritätswerten.<br /><br /> -Oder-<br /><br /> Verwenden Sie einen Artikelkonfliktlöser, der eine Spalte mit Autoritätswerten im Artikel erkennt und damit die Konfliktlösung vereinfacht.|  
|Lösung wird gewünscht, bei der die erste Änderung den Konflikt gewinnt.|Verwenden Sie den Standardkonfliktlöser, und erstellen Sie Clientabonnements.|  
|Mehrere Benutzer, die dieselbe Datenzeile ändern, sollen zulässig sein, sofern keine konfliktverursachenden Änderungen an derselben Spalte vorgenommen werden.|Verwenden Sie entweder den Standardkonfliktlöser oder einen Artikelkonfliktlöser mit aktivierter Nachverfolgung auf Spaltenebene.|  
|Mehrere Änderungen an einem Wert in einer Zeile sollen als Konflikt markiert werden.|Verwenden Sie entweder den Standardkonfliktlöser oder einen Artikelkonfliktlöser mit Nachverfolgung auf Zeilenebene.|  
|Mehrere Änderungen an einem Wert in einem logischen Datensatz sollen als Konflikt markiert werden.|Verwenden Sie den Standardkonfliktlöser mit Nachverfolgung auf der Ebene des logischen Datensatzes (bei Verwendung logischer Datensätze werden weder benutzerdefinierte Konfliktlöser noch Geschäftslogikhandler unterstützt).|  
|Die resultierenden Konfliktdaten müssen sich von den ursprünglichen Konfliktdaten unterscheiden.|Verwenden Sie einen Artikelkonfliktlöser, der neue Werte berechnet.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Detecting and Resolving Conflicts in Logical Records](advanced-merge-replication-conflict-resolving-in-logical-record.md)   
 [Erweiterte Konflikterkennung und -lösung der Mergereplikation](advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Erneutes Veröffentlichen von Daten](../republish-data.md)  
  
  
