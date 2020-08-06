---
title: Konfigurieren der Verteilung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], distribution
- distribution configuration [SQL Server replication]
- remote Distributors [SQL Server replication]
- transactional replication, configuring distribution
- distribution databases [SQL Server replication], sizing
- Distributors [SQL Server replication], configuring
- distribution databases [SQL Server replication], about distribution databases
- distribution databases [SQL Server replication]
- merge replication [SQL Server replication], configuring distribution
ms.assetid: 94d52169-384e-4885-84eb-2304e967d9f7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b0378fe285ba57e1420b7e6bebf5e2e6fe13d29e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615943"
---
# <a name="configure-distribution"></a>Konfigurieren der Verteilung
  Bei dem Verteiler handelt es sich um einen Server, der die Verteilungsdatenbank enthält. In der Datenbank sind Metadaten und Verlaufsdaten für alle Replikations- und Transaktionstypen der Transaktionsreplikation gespeichert. Zum Einrichten der Replikation müssen Sie einen Verteiler konfigurieren. Jeder Verleger kann nur einer einzigen Verteilerinstanz zugewiesen werden, es kann jedoch für mehrere ein Verteiler freigegeben werden. Der Verteiler verwendet die folgenden zusätzlichen Ressourcen auf dem Server, auf dem er sich befindet:  
  
-   Zusätzlichen Speicherplatz, falls die Momentaufnahmedateien für die Veröffentlichung auf dem Verteiler gespeichert werden (was in der Regel der Fall ist).  
  
-   Zusätzlichen Speicherplatz zum Speichern der Verteilungsdatenbank.  
  
-   Zusätzliche Prozessornutzung durch Replikations-Agents für auf dem Verteiler ausgeführte Pushabonnements.  
  
 Der Server, den Sie als Verteiler auswählen, sollte ausreichend Speicherplatz und Prozessorleistung für die Replikation und sonstige Aktivitäten, die auf diesem Server basieren, aufweisen. Beim Konfigurieren des Verteilers geben Sie Folgendes an:  
  
-   Einen Momentaufnahmeordner, der standardmäßig für alle Verleger verwendet wird, die diesen Verteiler verwenden. Stellen Sie sicher, dass dieser Ordner bereits freigegeben ist und die richtigen Berechtigungen festgelegt sind. Weitere Informationen finden Sie unter [Schützen des Momentaufnahmeordners](security/secure-the-snapshot-folder.md).  
  
-   Einen Namen und Dateispeicherorte für die Verteilungsdatenbank. Die Verteilungsdatenbank kann nach dem Erstellen nicht mehr umbenannt werden. Wenn Sie einen anderen Namen für die Datenbank verwenden möchten, müssen Sie die Verteilung deaktivieren und neu konfigurieren.  
  
-   Alle Verleger, die den Verteiler verwenden dürfen. Wenn Sie andere Verleger angeben als die Instanz, auf der der Verteiler ausgeführt wird, müssen Sie auch ein Kennwort für die Verbindungen angeben, die die Verleger mit dem Remoteverteiler herstellen.  
  
 Führen Sie bei der Transaktionsreplikation nach dem Konfigurieren der Verteilung folgende Aktionen aus:  
  
-   Richten Sie eine angemessene Größe für die Verteilungsdatenbank ein. Testen Sie die Replikation unter der typischen Auslastung des Systems, um den Speicherbedarf für Befehle zu ermitteln. Stellen Sie sicher, dass die Datenbank ausreichend Speicherkapazität für Befehle aufweist, um die häufige automatische Vergrößerung zu verhindern. Weitere Informationen zum Ändern der Größe einer Datenbank finden Sie unter [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).  
  
-   Legen Sie die Option **sync with backup** für die Verteilungsdatenbank fest. Weitere Informationen finden Sie unter [Strategien zum Sichern und Wiederherstellen einer Momentaufnahme- und Transaktionsreplikation](administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md) und [Aktivieren koordinierter Sicherungen für die Transaktionsreplikation &#40;Replication Transact-SQL Programming&#41;](administration/enable-coordinated-backups-for-transactional-replication.md).  
  
## <a name="local-and-remote-distributors"></a>Lokale und Remoteverteiler  
 Standardmäßig handelt es sich beim Verteiler um den gleichen Server wie beim Verleger (ein lokaler Verteiler), der Verteiler kann jedoch auch ein anderer Server sein als der Verleger (ein Remoteverteiler). In der Regel verwenden Sie in den folgenden Fällen einen Remoteverteiler:  
  
-   Zum Auslagern der Verarbeitung auf einen anderen Computer, wenn sich die Replikation so wenig wie möglich auf den Verleger auswirken soll (z. B. wenn der Verleger ein OLTP-Server ist).  
  
-   Zum Konfigurieren eines zentralen Verteilers für mehrere Verleger.  
  
 Remoteverteiler treten bei der Transaktionsreplikation häufiger auf als bei der Mergereplikation. Dafür gibt es zwei Gründe:  
  
-   Der Verteiler spielt bei der Transaktionsreplikation eine größere Rolle, da alle replizierten Transaktionen in die Verteilungsdatenbank geschrieben werden oder daraus gelesen werden.  
  
-   Mergereplikationstoplogien verwenden im Allgemeinen Pullabonnements. Deshalb werden Agents jeweils auf einzelnen Abonnenten und nicht alle auf dem Verteiler ausgeführt. Weitere Informationen finden Sie unter [Abonnieren von Veröffentlichungen](subscribe-to-publications.md). In den meisten Fällen sollten Sie einen lokalen Verteiler für die Mergereplikation verwenden.  
  
 Informationen zum Konfigurieren Sie der Veröffentlichung und Verteilung finden Sie unter [Configure Publishing and Distribution](configure-publishing-and-distribution.md).  
  
 Informationen zum Ändern der Verleger- und Verteilereigenschaften finden Sie unter [View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Veröffentlichen von Daten und Datenbankobjekten](publish/publish-data-and-database-objects.md)   
 [Schützen des Verteilers](security/secure-the-distributor.md)  
  
  
