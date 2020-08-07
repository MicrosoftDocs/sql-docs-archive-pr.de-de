---
title: Wiederherstellen von speicheroptimierten Tabellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 294975b7-e7d1-491b-b66a-fdb1100d2acc
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5e702798ea68745a038407fb65af7726a5c5d50e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87620373"
---
# <a name="restore-and-recovery-of-memory-optimized-tables"></a>Wiederherstellen von speicheroptimierten Tabellen
  Der grundlegende Mechanismus zum Wiederherstellen einer Datenbank mit speicheroptimierten Tabellen ist ähnlich wie bei Datenbanken, die nur datenträgerbasierte Tabellen enthalten. Anders als datenträgerbasierte Tabellen müssen speicheroptimierte Tabellen jedoch in den Arbeitsspeicher geladen werden, bevor die Benutzer auf die Datenbank zugreifen können. Hierdurch wird ein neuer Schritt bei der Datenbankwiederherstellung hinzugefügt. Die Schritte bei der Datenbankwiederherstellung werden wie folgt geändert:

 Beim Neustart von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] durchläuft jede Datenbank eine Wiederherstellungsphase, die aus den folgenden drei Phasen besteht:

1.  Die Analysephase. Während dieser Phase werden die aktiven Transaktionsprotokolle durchsucht, um Transaktionen mit ausgeführtem Commit und Transaktionen ohne Commit zu erkennen. Die In-Memory-OLTP-Engine identifiziert den zu ladenden Prüfpunkt und lädt die Protokolleinträge der Systemtabelle vorab. Außerdem werden einige Protokolldatensätze für die Dateizuordnung verarbeitet.

2.  Die Rollforwardphase. Diese Phase wird für datenträgerbasierte und speicheroptimierte Tabellen gleichzeitig ausgeführt.

     Bei datenträgerbasierten Tabellen wird die Datenbank auf den aktuellen Stand verschoben, und es werden Sperren abgerufen, die von Transaktionen ohne Commit aktiviert wurden.

     Bei speicheroptimierten Tabellen werden Daten aus den Daten- und Änderungsdateipaaren in den Arbeitsspeicher geladen, und die Daten werden dann mit dem aktiven Transaktionsprotokoll auf Grundlage des letzten permanenten Prüfpunkts aktualisiert.

     Wenn die oben genannten Vorgänge für datenträgerbasierte und speicheroptimierte Tabellen abgeschlossen wurden, kann auf die Datenbank zugegriffen werden.

3.  Die Rollbackphase. In dieser Phase wird für die Transaktionen ohne Commit ein Rollback ausgeführt.

 Das Laden von speicheroptimierten Tabellen in den Arbeitsspeicher kann die Leistung des Wiederherstellungszeitziels (Recovery Time Objective, RTO) beeinträchtigen. Um die Ladezeit von speicheroptimierten Daten aus Daten- und Änderungsdateien zu verbessern, lädt die In-Memory-OLTP-Engine die Daten-/Änderungsdateien wie folgt parallel:

-   Erstellen eines Änderungszuordnungsfilters. In Änderungsdateien werden Verweise auf die gelöschten Zeilen gespeichert. Ein Thread pro Container liest die Änderungsdateien und erstellt einen Änderungszuordnungsfilter. (Eine speicheroptimierte Datendateigruppe kann mehrere Container enthalten.)

-   Streaming der Datendateien.  Sobald der Änderungszuordnungsfilter erstellt wurde, werden Datendateien mit so vielen Threads gelesen wie logische CPUs vorhanden sind. Jeder Thread, der die Datendatei liest, liest die Datenzeilen, überprüft die zugeordnete Änderungszuordnung und fügt die Zeile nur dann in der Tabelle ein, wenn diese Zeile nicht als gelöscht markiert wurde. Dieser Teil der Wiederherstellung kann in einigen Fällen CPU-gebunden sein, wie unten aufgeführt.

 ![Speicher optimierte Tabellen.](../../database-engine/media/memory-optimized-tables.gif "Speicheroptimierte Tabellen")

 Speicheroptimierte Tabellen können generell mit der Geschwindigkeit des E/A-Vorgangs in den Arbeitsspeicher geladen werden, in einigen Situationen dauert das Laden von Datenzeilen in den Arbeitsspeicher jedoch länger. Dies ist insbesondere in folgenden Situationen der Fall:

-   Eine niedrige Bucketanzahl für den Hashindex kann zu übermäßigen Konflikten führen, wodurch das Einfügen von Datenzeilen langsamer erfolgt. Dies führt normalerweise zu einer sehr hohen allgemeinen CPU-Auslastung, insbesondere gegen Ende der Wiederherstellung. Wenn Sie den Hashindex ordnungsgemäß konfiguriert haben, sollte die Wiederherstellungszeit nicht beeinträchtigt werden.

-   Große speicheroptimierte Tabellen mit einem oder mehreren nicht gruppierten Indizes. Anders als bei einem Hashindex, bei dem die Bucketanzahl beim Erstellen festgelegt wird, wachsen nicht gruppierte Indizes dynamisch, was zu einer hohe CPU-Auslastung führt.

## <a name="restoring-a-database-with-memory-optimized-tables"></a>Wiederherstellen einer Datenbank mit speicheroptimierten Tabellen
 Sie wissen, dass Sie über ausreichend Arbeitsspeicher auf dem Server verfügen, um eine Datenbank wiederherzustellen, allerdings muss der von der Datenbank benötigte Arbeitsspeicher als Teil eines vorhandenen Ressourcenpools berücksichtigt werden.  Sie wissen, dass Sie die Bindung an den Ressourcenpool erst erstellen können, wenn die Datenbank vorhanden ist, daher führen Sie RESTORE WITH NORECOVERY aus.  Dies bewirkt, dass das Datenträgerimage der Datenbank wiederhergestellt und die Datenbank erstellt wird, aber kein In-Memory OLTP-Speicher verbraucht wird, da die Datenbank nicht online geschaltet wird.

 An diesem Punkt können Sie die Datenbank an den Ressourcenpool binden und dann RESTORE WITH RECOVERY verwenden, um die wiederhergestellte Datenbank online zu schalten.  Da die Bindung vorhanden ist, bevor die Datenbank online geschaltet wird, wird der betreffende In-Memory OLTP-Speicherverbrauch ordnungsgemäß berücksichtigt. Dies erfordert nur eine einmalige Wiederherstellung der Datenbank. Der erste RESTORE-Befehl ist ein Informationsbefehl, der lediglich den Sicherungsheader liest, und der letzte Befehl löst einfach die Wiederherstellung aus, ohne tatsächlich Bits wiederherzustellen.

## <a name="see-also"></a>Weitere Informationen
 [Sichern und Wiederherstellen speicheroptimierter Tabellen](memory-optimized-tables.md)


