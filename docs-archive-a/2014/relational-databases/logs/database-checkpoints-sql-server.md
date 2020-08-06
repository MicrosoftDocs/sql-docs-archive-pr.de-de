---
title: Datenbankprüfpunkte (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/13/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- automatic checkpoints
- transaction logs [SQL Server], checkpoints
- logs [SQL Server], active
- pages [SQL Server], dirty
- MinLSN
- checkpoints [SQL Server]
- pages [SQL Server], flushing
- dirty pages
- transaction logs [SQL Server], active logs
- recovery interval option [SQL Server]
- buffer cache [SQL Server]
- logs [SQL Server], checkpoints
- Minimum Recovery LSN
- flushing pages
- active logs
ms.assetid: 98a80238-7409-4708-8a7d-5defd9957185
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5776d4a23223637c50ac40098fa44342d5cd94a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87616542"
---
# <a name="database-checkpoints-sql-server"></a>Datenbankprüfpunkte (SQL Server)
  Dieses Thema bietet eine Übersicht über [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbankprüfpunkte. Ein *Prüfpunkt* erstellt einen bekannten fehlerfreien Punkt, von dem aus [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] Änderungen übernehmen kann, die im Protokoll während der Wiederherstellung nach einem unerwarteten Herunterfahren oder einem Absturz enthalten sind.  
  
  
##  <a name="overview-of-checkpoints"></a><a name="Overview"></a>Übersicht über Prüfpunkte  
 Aus Leistungsgründen führt [!INCLUDE[ssDE](../../includes/ssde-md.md)] Änderungen an Datenbankseiten im Arbeitsspeicher aus (im Puffercache) und schreibt diese Seiten nicht nach jeder Änderung auf den Datenträger. Vielmehr gibt [!INCLUDE[ssDE](../../includes/ssde-md.md)] in regelmäßigen Abständen einen Prüfpunkt auf jeder Datenbank aus. Ein *Prüfpunkt* schreibt die aktuellen, speicherintern geänderten Seiten (auch bekannt als *modifizierte Seiten*) sowie Transaktionsprotokollinformationen vom Arbeitsspeicher auf den Datenträger und erfasst auch Informationen zum Transaktionsprotokoll.  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] unterstützt mehrere Typen von Prüfpunkten. Dazu gehören "automatisch", "indirekt", "manuell" und "intern". In der folgenden Tabelle werden die Prüfpunkttypen zusammengefasst.  
  
|Name|[!INCLUDE[tsql](../../includes/tsql-md.md)] -Schnittstelle|BESCHREIBUNG|  
|----------|----------------------------------|-----------------|  
|Automatic|Exec sp_configure **' `recovery interval` ', ' *`seconds`* '**|Wird automatisch im Hintergrund ausgegeben, um das obere Zeit Limit zu erreichen, das von der `recovery interval` Server Konfigurationsoption vorgeschlagen wird. Automatische Prüfpunkte werden vollständig ausgeführt.  Automatische Prüfpunkte werden auf Basis der Anzahl an ausstehenden Schreibvorgängen gedrosselt. Zudem hängt die Drosselung auch davon ab, ob [!INCLUDE[ssDE](../../includes/ssde-md.md)] eine Erhöhung der Schreiblatenz auf über 20 Millisekunden erkennt.<br /><br /> Weitere Informationen finden Sie unter [Configure the recovery interval Server Configuration Option](../../database-engine/configure-windows/configure-the-recovery-interval-server-configuration-option.md).|  
|Indirekt|Datenbank ändern... Festlegen TARGET_RECOVERY_TIME **=** _target_recovery_time_ {Sekunden &#124; Minuten}|Wird im Hintergrund ausgegeben, um eine benutzerdefinierte Zielwiederherstellungszeit für eine bestimmte Datenbank zu erfüllen. Die standardmäßige Zielwiederherstellungszeit ist 0. Sie löst die Verwendung der Heuristik für automatische Prüfpunkte auf der Datenbank aus. Wenn Sie ALTER DATABASE verwendet haben, um TARGET_RECOVERY_TIME auf >0 festzulegen, wird dieser Wert anstelle des Wiederherstellungsintervalls verwendet, das für die Serverinstanz angegeben wurde.<br /><br /> Weitere Informationen finden Sie unter [Ändern der Zielwiederherstellungszeit einer Datenbank &#40;SQL Server&#41;](change-the-target-recovery-time-of-a-database-sql-server.md)konfiguriert wird.|  
|Manuell|CHECKPOINT [ *checkpoint_duration* ]|Wird ausgegeben, wenn Sie einen [!INCLUDE[tsql](../../includes/tsql-md.md)] -CHECKPOINT-Befehl ausführen. Der manuelle Prüfpunkt tritt in der aktuellen Datenbank für die Verbindung auf. Standardmäßig werden manuelle Prüfpunkte vollständig ausgeführt. Das Drosseln erfolgt auf die gleiche Weise wie für automatische Prüfpunkte.  Optional gibt der *checkpoint_duration* -Parameter die Anforderung an, welchen Zeitraum in Sekunden ein Prüfpunkt benötigen darf, bis er abgeschlossen ist.<br /><br /> Weitere Informationen finden Sie unter [CHECKPOINT &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/checkpoint-transact-sql).|  
|Intern|Keine.|Wird von verschiedenen Servervorgängen wie Sicherung und Erstellung einer Datenbank-Momentaufnahme ausgegeben. So wird gewährleistet, dass Datenträgerabbilder dem aktuellen Protokollstatus entsprechen.|  
  
> [!NOTE]  
>  Die erweiterte Einrichtungsoption `-k`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ermöglicht Datenbankadministratoren, das Prüfpunkt-E/A-Verhalten auf Basis des Durchsatzes des E/A-Teilsystems für einige Typen von Prüfpunkten zu drosseln. Die `-k` Setup Option gilt für automatische Prüfpunkte sowie für andere, nicht gedrosselt manuelle und interne Prüfpunkte.  
  
 Für automatische, manuelle und interne Prüfpunkte muss nur für Änderungen, die nach dem letzten Prüfpunkt erfolgt sind, während der Datenbankwiederherstellung ein Rollforward ausgeführt werden. Dadurch verringert sich die Zeit, die zur Wiederherstellung einer Datenbank erforderlich ist.  
  
> [!IMPORTANT]  
>  Lang andauernde Transaktionen ohne Commit erhöhen die Wiederherstellungszeit für alle Typen von Prüfpunkten.  
  
  
  
###  <a name="interaction-of-the-target_recovery_time-and-recovery-interval-options"></a><a name="InteractionBwnSettings"></a> Interaktion der Optionen "TTARGET_RECOVERY_TIME" und "Wiederherstellungsintervall"  
 In der folgenden Tabelle wird die Interaktion zwischen der serverweiten **sp_configure- `recovery interval` ** Einstellung und der datenbankspezifischen Alter Database... TARGET_RECOVERY_TIME Einstellung.  
  
|Zielwiederherstellungszeit|'Wiederherstellungsintervall'|Verwendeter Prüfpunkttyp|  
|----------------------------|-------------------------|-----------------------------|  
|0|0|Automatische Prüfpunkte, deren Zielwiederherstellungsintervall 1 Minute beträgt.|  
|0|>0|Automatische Prüfpunkte, deren Zielwiederherstellungsintervall anhand der benutzerdefinierten Einstellung der Option **sp_configure recovery interval** angegeben wurde.|  
|>0|Nicht zutreffend|Indirekte Prüfpunkte, deren Zielwiederherstellungszeit anhand der TARGET_RECOVERY_TIME-Einstellung definiert ist (in Sekunden ausgedrückt).|  
  
###  <a name="automatic-checkpoints"></a><a name="AutomaticChkpt"></a>Automatische Prüfpunkte  
 Ein automatischer Prüfpunkt tritt jedes Mal auf, wenn die Anzahl der Protokolldaten Sätze die Anzahl der [!INCLUDE[ssDE](../../includes/ssde-md.md)] in der `recovery interval` Server Konfigurationsoption angegebenen Zeit erreicht. In jeder Datenbank ohne benutzerdefinierte Zielwiederherstellungszeit generiert [!INCLUDE[ssDE](../../includes/ssde-md.md)] automatische Prüfpunkte. Die Häufigkeit automatischer Prüfpunkte hängt von der `recovery interval` erweiterten Server Konfigurationsoption ab, die die maximale Zeit angibt, die eine bestimmte Serverinstanz zum Wiederherstellen einer Datenbank während eines Systemneustarts verwenden soll. [!INCLUDE[ssDE](../../includes/ssde-md.md)] schätzt die maximale Anzahl an Protokolldatensätzen, die innerhalb des Wiederherstellungsintervalls verarbeitet werden können. Erreicht eine Datenbank, die automatische Prüfpunkte verwendet, diese maximale Anzahl an Protokolldatensätzen, gibt [!INCLUDE[ssDE](../../includes/ssde-md.md)] einen Prüfpunkt auf der Datenbank aus. Das Zeitintervall zwischen automatischen Prüfpunkten kann stark variieren. Bei einer Datenbank mit einer beträchtlichen Transaktionsarbeitsauslastung treten häufiger Prüfpunkte auf als bei einer Datenbank für hauptsächlich schreibgeschützte Vorgänge.  
  
 Im Fall des einfachen Wiederherstellungsmodells wird ein automatischer Prüfpunkt auch in die Warteschlange aufgenommen, wenn das Protokoll zu 70 Prozent gefüllt ist.  
  
 Unter dem einfachen Wiederherstellungsmodell wird der ungenutzte Abschnitt des Transaktionsprotokolls durch einen automatischen Prüfpunkt abgeschnitten, sofern nicht gewisse Faktoren die Protokollkürzung verzögern. Im Gegensatz dazu lösen automatische Prüfpunkte im Fall des vollständigen und massenprotokollierten Wiederherstellungsmodells keine Protokollkürzung aus, sobald eine Protokollsicherungskette eingerichtet wurde. Weitere Informationen finden Sie unter [Das Transaktionsprotokoll &#40;SQL Server&#41;](the-transaction-log-sql-server.md).  
  
 Nach einem Systemabsturz hängt die Zeitdauer, die für die Wiederherstellung einer bestimmten Datenbank erforderlich ist, stark vom zufälligen E/A-Volumen zur Wiederherstellung der zum Zeitpunkt des Absturzes modifizierten Seiten ab. Dies bedeutet, dass die `recovery interval` Einstellung unzuverlässig ist. Sie ermöglicht keine genaue Bestimmung der Wiederherstellungsdauer. Zudem erhöht sich die allgemeine E/A-Aktivität für Daten erheblich und eher unvorhersehbar, wenn ein automatischer Prüfpunkt ausgeführt wird.  
  
  
####  <a name="impact-of-recovery-interval-on-recovery-performance"></a><a name="PerformanceImpact"></a>Auswirkung des Wiederherstellungs Intervalls auf die Wiederherstellungs Leistung  
 Bei einem OLTP-System (Online Transaction Processing, Online Transaktionsverarbeitung), das kurze Transaktionen verwendet, `recovery interval` ist der primäre Faktor zum Bestimmen der Wiederherstellungs Die Option wirkt sich jedoch `recovery interval` nicht auf die Zeit aus, die zum rückgängig einer Transaktion mit langer Laufzeit erforderlich ist. Die Wiederherstellung einer Datenbank mit einer Transaktion mit langer Laufzeit kann deutlich länger dauern als die in der `recovery interval` Option angegebene. Wenn z. b. eine lang ausgeführte Transaktion zwei Stunden dauert, um Updates durchzuführen, bevor die Serverinstanz deaktiviert wurde, dauert die tatsächliche Wiederherstellung erheblich länger als der `recovery interval` Wert für die Wiederherstellung der langen Transaktion. Weitere Informationen zu den Auswirkungen einer Transaktion mit langer Ausführungszeit auf die Wiederherstellungsdauer finden Sie unter [Das Transaktionsprotokoll &#40;SQL Server&#41;](the-transaction-log-sql-server.md).  
  
 In der Regel gewährleisten die Standardwerte eine optimale Wiederherstellungsleistung. Durch Ändern des Wiederherstellungsintervalls kann sich jedoch die Leistung in folgenden Fällen verbessern:  
  
-   Die Wiederherstellung dauert routinemäßig bedeutend länger als 1 Minute, wenn kein Rollback für Transaktionen mit langer Laufzeit ausgeführt wird.  
  
-   Sie stellen fest, dass häufige Prüfpunkte die Datenbankleistung beeinträchtigen.  
  
 Wenn Sie die Einstellung `recovery interval` erhöhen möchten, empfehlen wir eine schrittweise Erhöhung des entsprechenden Werts. Werten Sie zudem die Auswirkungen der jeweiligen stufenweisen Erhöhung auf die Wiederherstellungsleistung aus. Diese Vorgehensweise ist wichtig, da die `recovery interval` Einstellung für die Daten Bank Wiederherstellung so oft wie länger dauert. Wenn Sie z `recovery interval` . b. 10 ändern, dauert die Wiederherstellung ungefähr zehnmal länger, als wenn `recovery interval` auf 0 (null) festgelegt ist.  
  
  
###  <a name="indirect-checkpoints"></a><a name="IndirectChkpt"></a>Indirekte Prüfpunkte  
 Indirekte Prüfpunkte (neu in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) stellen auf Datenbankebene eine konfigurierbare Alternative zu automatischen Prüfpunkten dar. Im Fall eines Systemabsturzes ermöglichen indirekte Prüfpunkte eine potenziell schnellere und besser vorhersehbare Wiederherstellungszeit als automatische Prüfpunkte. Indirekte Prüfpunkte bieten folgende Vorteile:  
  
-   Im Fall einer Arbeitsauslastung für Onlinetransaktionen bei einer Datenbank, die für indirekte Prüfpunkte konfiguriert ist, kann eine Verringerung der Leistung auftreten. Indirekte Prüfpunkte stellen sicher, dass die Anzahl der modifizierten Seiten unter einem bestimmten Schwellenwert liegt, sodass die Datenbankwiederherstellung innerhalb der Zielwiederherstellungszeit abgeschlossen wird. Die Konfigurationsoption „Wiederherstellungsintervall“ ermittelt die Wiederherstellungszeit über die Anzahl der Transaktionen. Im Gegensatz dazu greifen indirekte Prüfpunkte auf die Anzahl der modifizierten Seiten zurück. Wenn für eine Datenbank, die eine große Anzahl von DML-Vorgängen empfängt, indirekte Prüfpunkte aktiviert sind, können beim Schreiben im Hintergrund leere modifizierte Puffer aggressiv auf den Datenträger geleert werden. Dadurch wird sichergestellt, dass der Zeitaufwand für die Wiederherstellung innerhalb der Zielwiederherstellungszeit der Datenbank liegt. Dies kann auf bestimmten Systemen zusätzliche E/A-Aktivitäten verursachen, die zu einem Leistungsengpass beitragen können, wenn das Datenträgersubsystem über oder nahe dem E/A-Schwellenwert arbeitet.  
  
-   Indirekte Prüfpunkte ermöglichen Ihnen eine zuverlässige Kontrolle der Datenbankwiederherstellungszeit, indem die Kosten für das zufällige E/A-Volumen während des REDO-Vorgangs berücksichtigt werden. Dadurch überschreitet eine Serverinstanz nicht den Obergrenzwert der Wiederherstellungszeiten für eine bestimmte Datenbank, sofern eine Transaktion mit langer Laufzeit keine übermäßig langen UNDO-Vorgänge verursacht.  
  
-   Indirekte Prüfpunkte reduzieren prüfpunktbezogene E/A-Spitzen, indem modifizierte Seiten im Hintergrund kontinuierlich auf den Datenträger geschrieben werden.  
  
 Im Fall einer Arbeitsauslastung für Onlinetransaktionen bei einer Datenbank, die für indirekte Prüfpunkte konfiguriert ist, kann jedoch eine Verringerung der Leistung auftreten. Dies ist darauf zurückzuführen, dass der Hintergrundschreiber, der von indirekten Prüfpunkten verwendet wird, manchmal die Gesamtarbeitsauslastung zum Schreiben für eine Serverinstanz erhöht.  
  
  
###  <a name="internal-checkpoints"></a><a name="EventsCausingChkpt"></a>Interne Prüfpunkte  
 Interne Prüfpunkte werden von verschiedenen Serverkomponenten generiert, um so gewährleisten zu können, dass Datenträgerabbilder dem aktuellen Protokollstatus entsprechen. Interne Prüfpunkte werden als Antwort auf die folgenden Ereignisse erstellt:  
  
-   Datenbankdateien wurden mit ALTER DATABASE hinzugefügt oder entfernt.  
  
-   Eine vollständige Datenbanksicherung wird ausgeführt.  
  
-   Eine Datenbank-Momentaufnahme wird erstellt, entweder explizit oder intern für DBCC CHECK.  
  
-   Eine Aktivität wird ausgeführt, für die das Herunterfahren einer Datenbank erforderlich ist. Beispielsweise besitzt AUTO_CLOSE den Status ON, und die letzte Benutzerverbindung mit der Datenbank wird geschlossen, oder eine Änderung einer Datenbankoption wird vorgenommen, für die ein Neustart der Datenbank erforderlich ist.  
  
-   Eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz wird beendet, indem der Dienst [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER) beendet wird. Durch jede der Aktionen wird ein Prüfpunkt in jeder Datenbank der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ausgelöst.  
  
-   Aktivieren des Offlinemodus einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Failoverclusterinstanz (FCI).  
  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben  
 **So ändern Sie das Wiederherstellungsintervall auf einer Serverinstanz**  
  
-   [Konfigurieren des Wiederherstellungsintervalls (Serverkonfigurationsoption)](../../database-engine/configure-windows/configure-the-recovery-interval-server-configuration-option.md)  
  
 **So konfigurieren Sie indirekte Prüfpunkte auf einer Datenbank**  
  
-   [Ändern der Zielwiederherstellungszeit einer Datenbank &#40;SQL Server&#41;](change-the-target-recovery-time-of-a-database-sql-server.md)  
  
 **So geben Sie einen manuellen Prüfpunkt auf einer Datenbank aus**  
  
-   [CHECKPOINT &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/checkpoint-transact-sql)  
  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> Verwandte Inhalte  
  
-   [Physische Architektur des Transaktionsprotokolls](https://technet.microsoft.com/library/ms179355.aspx) (in der [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] -Onlinedokumentation)  
  
  
## <a name="see-also"></a>Weitere Informationen  
 [Das Transaktionsprotokoll &#40;SQL Server&#41;](the-transaction-log-sql-server.md)  
  
  
