---
title: Nicht-SQL Server-Abonnenten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [SQL Server replication], non-SQL Server Subscribers
- heterogeneous data sources, non-SQL Server Subscribers
- heterogeneous data sources
- heterogeneous database replication, non-SQL Server Subscribers
- non-SQL Server Subscribers, about non-SQL Server Subscribers
- heterogeneous Subscribers
- heterogeneous Subscribers, about heterogeneous Subscribers
- Subscribers [SQL Server replication], non-SQL Server Subscribers
- non-SQL Server Subscribers
ms.assetid: 831e7586-2949-4b9b-a2f3-7b0b699b23ff
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3a42ba5aedff4f23c6fb6be4155b1c6d4bf20471
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717917"
---
# <a name="non-sql-server-subscribers"></a>Nicht-SQL Server-Abonnenten
  Die folgenden Nicht-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Abonnenten können Momentaufnahme- und Transaktionsveröffentlichungen mithilfe von Pushabonnements abonnieren. Abonnements werden für die beiden neuesten Versionen jeder aufgeführten Datenbank mithilfe der neuesten Version des aufgeführten OLE DB-Anbieters unterstützt.  
  
 Die heterogene Replikation an Nicht-SQL Server-Abonnenten ist veraltet. Das Veröffentlichen mit Oracle ist veraltet. Um Daten zu verschieben, erstellen Sie Lösungen mit Change Data Capture und [!INCLUDE[ssIS](../../../includes/ssis-md.md)].  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
|Datenbank|Betriebssystem|Anbieter|  
|--------------|----------------------|--------------|  
|Oracle|Alle von Oracle unterstützten Plattformen|Oracle OLE DB-Anbieter (von Oracle bereitgestellt)|  
|IBM DB2|MVS, AS400, Unix, Linux, Windows ausgenommen Version 9.x|Microsoft Host Integration Server (HIS) OLE DB-Anbieter|  
  
 Weitere Informationen zum Erstellen von Abonnements für Oracle und IBM DB2, finden Sie unter [Oracle-Abonnenten](oracle-subscribers.md) und [IBM DB2 Subscribers](ibm-db2-subscribers.md).  
  
## <a name="considerations-for-non-sql-server-subscribers"></a>Überlegungen zu Nicht-SQL Server-Abonnenten  
 Beachten Sie beim Replizieren auf Nicht-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Abonnenten Folgendes:  
  
### <a name="general-considerations"></a>Allgemeine Überlegungen  
  
-   Die Replikation unterstützt veröffentlichende Tabellen und indizierte Sichten als Tabellen für Nicht-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Abonnenten (indizierte Sichten können nicht als indizierte Sichten repliziert werden).  
  
-   Wenn Sie im Assistenten für neue Veröffentlichung eine Veröffentlichung erstellen und diese dann für nicht SQL Server Abonnenten mithilfe des Dialog Felds Veröffentlichungs Eigenschaften aktivieren, wird der Besitzer aller Objekte in der Abonnement Datenbank nicht für nicht-- [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Abonnenten angegeben, während für- [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Abonnenten der Besitzer des entsprechenden Objekts in der Veröffentlichungs Datenbank festgelegt ist.  
  
-   Weist eine Veröffentlichung [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Abonnenten und Nicht-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Abonnenten auf, muss sie für Nicht-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Abonnenten aktiviert werden, damit Abonnements für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Abonnenten erstellt werden können.  
  
-   Standardmäßig verwenden vom Momentaufnahme-Agent für Nicht-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Abonnenten generierte Skripts Bezeichner ohne Anführungszeichen in der CREATE TABLE-Syntax. Deshalb wird eine veröffentlichte Tabelle mit dem Namen 'test' als 'TEST' repliziert. Wenn die Groß- und Kleinschreibung der Schreibweise in der Veröffentlichungsdatenbank entsprechen soll, verwenden Sie den **-QuotedIdentifier** -Parameter für den Verteilungs-Agent. Der **-QuotedIdentifier** -Parameter muss auch verwendet werden, wenn veröffentlichte Objektnamen (wie Tabellen, Spalten und Einschränkungen) Leerzeichen und Wörter enthalten, bei denen es sich in der Version der Datenbank auf dem Nicht-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Abonnenten um reservierte Wörter handelt. Weitere Informationen zu diesem Parameter finden Sie unter [Replikationsverteilungs-Agent](../agents/replication-distribution-agent.md).  
  
-   Das Konto, unter dem der Verteilungs-Agent ausgeführt wird, muss über Lesezugriff für das Installationsverzeichnis des OLE DB-Anbieters verfügen.  
  
-   Der Verteilungs-Agent verwendet bei Nicht-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Abonnenten standardmäßig einen Wert [(default destination)] für die Abonnementdatenbank (der **-SubscriberDB** -Parameter für den Verteilungs-Agent):  
  
    -   Bei Oracle weist ein Server höchstens eine Datenbank auf, deshalb ist die Angabe der Datenbank nicht erforderlich.  
  
    -   Bei IBM DB2 wird die Datenbank in der DM2-Verbindungszeichenfolge angegeben. Weitere Informationen finden Sie unter [Erstellen eines Abonnements für einen Nicht-SQL Server-Abonnenten](../create-a-subscription-for-a-non-sql-server-subscriber.md).  
  
-   Wenn der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Verteiler auf einer 64-Bit-Plattform ausgeführt wird, müssen Sie die 64-Bit-Version des entsprechenden OLE DB-Anbieters verwenden.  
  
-   Die Replikation verschiebt Daten im Unicode-Format, unabhängig von der auf dem Verleger und dem Abonnenten verwendeten Sortierung (bzw. den verwendeten Codeseiten). Es wird empfohlen, für die Replikation zwischen Verlegern und Abonnenten eine kompatible Sortierung/Codeseite auszuwählen.  
  
-   Wenn ein Artikel einer Veröffentlichung hinzugefügt oder aus einer Veröffentlichung gelöscht wird, müssen Abonnements für Nicht-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Abonnenten erneut initialisiert werden.  
  
-   Bei allen Nicht-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Abonnenten werden nur zwei Einschränkungen unterstützt: NULL und NOT NULL. PRIMARY KEY-Einschränkungen werden als eindeutige Indizes repliziert.  
  
-   Der Wert NULL wird von den verschiedenen Datenbanken unterschiedlich behandelt. Das wirkt sich darauf aus, wie ein leerer Wert, eine leere Zeichenfolge oder NULL dargestellt werden. Dies wiederum wirkt sich auf das Verhalten von Werten aus, die in Spalten mit definierten UNIQUE-Einschränkungen eingefügt werden. Oracle lässt z. B. mehrere NULL-Werte in einer eindeutigen Spalte zu, während [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nur einen einzigen NULL-Wert in einer eindeutigen Spalte zulässt.  
  
     Ein weiterer Faktor ist, wie NULL-Werte, leere Zeichenfolgen und leere Werte behandelt werden, wenn eine Spalte als NOT NULL definiert ist. Informationen zum Umgang mit Oracle-Abonnenten finden Sie unter [Oracle-Abonnenten](oracle-subscribers.md).  
  
-   Replikationsbezogene Metadaten (Transaktionssequenztabelle) werden bei Nicht-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Abonnenten nicht gelöscht, wenn das Abonnement entfernt wird.  
  
### <a name="conforming-to-the-requirements-of-the-subscriber-database"></a>Erfüllen der Anforderungen der Abonnentendatenbank  
  
-   Veröffentlichte Schemas und Daten müssen den Anforderungen der Datenbank auf dem Abonnenten entsprechen. Wenn beispielsweise die maximale Zeilengröße einer Nicht-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datenbank geringer ist als die von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], müssen Sie sicherstellen, dass das veröffentlichte Schema und die Daten diese Größe nicht überschreiten.  
  
-   Auf Nicht-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Abonnenten replizierte Tabellen übernehmen die Benennungskonventionen für Tabellen, die für die Datenbank auf dem Abonnenten gelten.  
  
-   Die Datendefinitionssprache (DDL) wird für Nicht-SQL Server-Abonnenten nicht unterstützt. Weitere Informationen zu Schemaänderungen finden Sie unter [Vornehmen von Schemaänderungen in Veröffentlichungsdatenbanken](../publish/make-schema-changes-on-publication-databases.md).  
  
### <a name="replication-feature-support"></a>Unterstützte Funktionen der Replikation  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] stellt zwei Arten von Abonnements bereit: Push und Pull. Nicht-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Abonnenten müssen Pushabonnements verwenden, wobei der Verteilungs-Agent auf dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Verteiler ausgeführt wird.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] stellt zwei Momentaufnahmeformate bereit: systemeigener BCP-Modus und Zeichenmodus. Nicht-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Abonnenten erfordern Momentaufnahmen im Zeichenmodus.  
  
-   Nicht-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Abonnenten können keine Abonnements mit sofortigem Update oder mit verzögertem Update über eine Warteschlange verwenden und keine Knoten in einer Peer-zu-Peer-Topologie sein.  
  
-   Nicht-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Abonnenten können nicht automatisch von einer Sicherung initialisiert werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Heterogene Datenbankreplikation](heterogeneous-database-replication.md)   
 [Abonnieren von Veröffentlichungen](../subscribe-to-publications.md)  
  
  
