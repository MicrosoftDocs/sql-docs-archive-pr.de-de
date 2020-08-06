---
title: Verwalten von DQS-Datenbanken | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 655a67aa-d662-42f2-b982-c6217125ada8
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 7228021dd3fe0af61312eeb891081cc24e1aa95d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621687"
---
# <a name="manage-dqs-databases"></a>Manage DQS Databases
  Dieser Abschnitt enthält Informationen zu Datenbankverwaltungsaktionen, z. B. zum Sichern/Wiederherstellen oder Trennen/Anfügen, die für DQS-Datenbanken ausgeführt werden können.  
  
##  <a name="backup-and-restore-the-dqs-databases"></a><a name="BackupRestore"></a> Sichern und Wiederherstellen der DQS-Datenbanken  
 Die Sicherung und Wiederherstellung von SQL Server-Datenbanken sind allgemeine Vorgänge, die Datenbankadministratoren ausführen, damit sie in einem Notfall Datenverlust verhindern können, indem sie die Daten aus den Sicherungsdatenbanken wiederherstellen. [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] wird hauptsächlich von zwei SQL Server-Datenbanken implementiert: DQS_MAIN und DQS_PROJECTS. Die Sicherungs- und Wiederherstellungsverfahren für [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS)-Datenbanken sind vergleichbar mit denen für beliebige andere SQL Server-Datenbanken. Bei der Sicherung und Wiederherstellung von DQS-Datenbanken sind jedoch drei Besonderheiten zu beachten:  
  
-   Die Sicherungs- und Wiederherstellungsvorgänge der DQS-Datenbanken müssen synchronisiert werden. Andernfalls ist der wiederhergestellte [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] nicht funktionsfähig.  
  
-   Die beiden DQS-Datenbanken, DQS_MAIN und DQS_PROJECTS, enthalten außer den einfachen Datenbankobjekten (z. B. Tabellen und gespeicherte Prozeduren) Assemblys und andere komplexe Objekte.  
  
-   Einige Entitäten außerhalb der DQS-Datenbank müssen vorhanden sein, damit die DQS-Datenbank als [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]funktionsfähig ist. Das gilt insbesondere für die beiden SQL Server-Anmeldenamen (##MS_dqs_db_owner_login## und ##MS_dqs_service_login##) und eine gespeicherte Initialisierungsprozedur (DQInitDQS_MAIN) in der Masterdatenbank.  
  
 Ausführliche Informationen zur Sicherung und Wiederherstellung in SQL Server finden Sie unter [Sichern und Wiederherstellen von SQL Server-Datenbanken](../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).  
  
### <a name="default-autogrowth-size-and-recovery-model-for-the-dqs-databases"></a>Standardmäßige automatische Vergrößerung und Wiederherstellungsmodell für DQS-Datenbanken  
 So verhindern Sie, dass DQS-Datenbanken und Transaktionsprotokolle immer größer werden und sich die Kapazität der Festplatte erschöpft:  
  
-   Der Standardwert von **Automatische Vergrößerung** ist für DQS-Datenbanken auf 10% festgelegt.  
  
-   Das Standardwiederherstellungsmodell der DQS-Datenbanken ist auf **Einfach**festgelegt. Im einfachen Wiederherstellungsmodell findet eine minimale Protokollierung der Transaktionen statt. Die Protokollkürzung erfolgt automatisch nach Ende der Transaktion, um Speicherplatz im Transaktionsprotokoll (LDF-Datei) freizugeben. Ausführliche Informationen zum einfachen Wiederherstellungsmodell finden Sie unter [Vollständige Datenbanksicherungen &#40;SQL Server&#41;](../relational-databases/backup-restore/full-database-backups-sql-server.md).  
  
> [!IMPORTANT]
>  -   Die Protokollkürzung im einfachen Wiederherstellungsmodell kann sich verzögern, wenn die Protokolleinträge über eine längere Zeit aktiv bleiben (z. B. bei einer langen und zeitintensiven Transaktion). Dies kann dann dazu führen, dass das Transaktionsprotokoll schnell an Größe zunimmt. Außerdem wird die Größe der physischen Protokolldatei (LDF-Datei) bei der Protokollkürzung nicht verringert. Um die Größe einer physischen Protokolldatei zu verringern, müssen Sie die Protokolldatei verkleinern. Informationen zum Beheben von Problemen bei Transaktionsprotokollen finden Sie unter [Das Transaktionsprotokoll &#40;SQL Server&#41;](../relational-databases/logs/the-transaction-log-sql-server.md) oder im Microsoft Support-Artikel unter [https://go.microsoft.com/fwlink/?LinkId=237446](https://go.microsoft.com/fwlink/?LinkId=237446).  
> -   Sie müssen regelmäßig eine vollständige oder differenzielle Sicherung der DQS-Datenbanken ausführen und das Transaktionsprotokoll sichern, um eine Zeitpunktwiederherstellung der Daten auszuführen. Weitere Informationen finden Sie unter [Vollständige Datenbanksicherungen &#40;SQL Server&#41;](../relational-databases/backup-restore/full-database-backups-sql-server.md) und [Sichern eines Transaktionsprotokolls &#40;SQL Server&#41;](../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md).  
  
##  <a name="detachattach-the-dqs-databases"></a><a name="DetachAttach"></a>Trennen/Anfügen der DQS-Datenbanken  
 Sie können die Daten- und Transaktionsprotokolldateien der DQS-Datenbanken trennen und die Datenbanken dann wieder an dieselbe oder eine andere Instanz von SQL Server anfügen, wenn Sie die DQS-Datenbanken in eine andere Instanz von SQL Server auf demselben Computer ändern oder die Datenbank verschieben möchten.  
  
 Ausführliche Informationen zu den Aspekten, die berücksichtigt werden sollten, bevor oder während Datenbanken in SQL Server getrennt und angefügt werden, finden Sie unter [Anfügen und Trennen von Datenbanken &#40;SQL Server&#41;](../relational-databases/databases/database-detach-and-attach-sql-server.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Beschreibt das Sichern und Wiederherstellen von DQS-Datenbanken.|[Sichern und Wiederherstellen von DQS-Datenbanken](../../2014/data-quality-services/backing-up-and-restoring-dqs-databases.md)|  
|Beschreibt das Trennen und Anfügen der DQS-Datenbanken.|[Trennen und Anfügen von DQS-Datenbanken](../../2014/data-quality-services/detaching-and-attaching-dqs-databases.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [DQS-Administration](../../2014/data-quality-services/dqs-administration.md)  
  
  
