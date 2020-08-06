---
title: Ausführung von Abfrage Optionen (Seite erweitert) | Microsoft-Dokumentation
ms.prod: sql-server-2014
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.advanced.f1
ms.assetid: 661595ce-99b9-4316-ad80-ed04002d04d5
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: ''
ms.date: 09/03/2019
ms.openlocfilehash: 5b6ab8cc3c788e27946ddb68a3c926e8f926ebd7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721722"
---
# <a name="query-options-execution-advanced-page"></a>Abfrageausführung (Seite Erweitert)

  Bei Verwendung der **SET** -Anweisung ist eine Vielzahl von Optionen verfügbar. Verwenden Sie diese Seite, um eine **Set** -Option zum Ausführen von Microsoft SQL Server Abfragen anzugeben. Detaillierte Informationen zu jeder dieser Optionen finden Sie in der SQL Server-Onlinedokumentation.
  
**NOCOUNT festlegen** Gibt nicht die Anzahl der Zeilen als Meldung mit dem Resultset zurück. Diese Option ist standardmäßig deaktiviert.

**noexec festlegen** Führt die Abfrage nicht aus. Diese Option ist standardmäßig deaktiviert.

**Festlegen von "parameseonly** " Überprüft die Syntax der einzelnen Abfragen, führt die Abfragen jedoch nicht aus. Diese Option ist standardmäßig deaktiviert.  

**CONCAT_NULL_YIELDS_NULL festlegen** Wenn dieses Kontrollkästchen aktiviert ist, geben Abfragen, von denen ein vorhandener Wert mit einer verkettet wird `NULL` , immer `NULL` als Ergebnis zurück. Wenn dieses Kontrollkästchen deaktiviert ist, gibt ein vorhandener, mit einer `NULL` verketteter Wert, den vorhandenen Wert zurück. Diese Option ist standardmäßig aktiviert.

**ARITHABORT festlegen** Wenn dieses Kontrollkästchen aktiviert ist, wird `INSERT` `DELETE` die Abfrage oder der Batch beendet, wenn eine-,-oder `UPDATE` -Anweisung einen arithmetischen Fehler (Überlauf, Division durch Null oder Domänen Fehler) während der Auswertung des Ausdrucks trifft. Wenn dieses Kontrollkästchen deaktiviert ist, wird für diesen Wert nach Möglichkeit eine `NULL` bereitgestellt, die Abfrage fortgesetzt und in das Ergebnis eine Meldung eingeschlossen. Eine ausführlichere Beschreibung dieses Verhaltens finden Sie in der Onlinedokumentation. Diese Option ist standardmäßig aktiviert.
  
**SHOWPLAN_TEXT festlegen** Wenn dieses Kontrollkästchen aktiviert ist, wird der Abfrageplan in Textform mit jeder Abfrage zurückgegeben. Diese Option ist standardmäßig deaktiviert.
  
**SET STATISTICS TIME** Wenn dieses Kontrollkästchen aktiviert ist, wird bei jeder Abfrage die Zeitstatistik zurückgegeben. Diese Option ist standardmäßig deaktiviert.
  
**SET STATISTICS IO** Wenn dieses Kontrollkästchen aktiviert ist, wird bei jeder Abfrage die Statistik zur Eingabe/Ausgabe (e/a) zurückgegeben. Diese Option ist standardmäßig deaktiviert.
  
**SET TRANSACTION ISOLATION LEVEL** Die Transaktionsisolationsstufe READ COMMITTED wird standardmäßig festgelegt. Weitere Informationen finden Sie unter [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql). Die Momentaufnahme-Transaktions Isolationsstufe ist nicht verfügbar. Fügen Sie zum Verwenden der MOMENTAUFNAHME-Isolation die folgende [!INCLUDE[tsql](../includes/tsql-md.md)]-Anweisung hinzu:
  
  ```sql
  SET TRANSACTION ISOLATION LEVEL SNAPSHOT;
  GO
  ```

**SET DEADLOCK PRIORITY** Beim Standardwert **Normal** kann jede Abfrage bei Auftreten eines Deadlock dieselbe Priorität haben. Wählen Sie in der Dropdownliste die Priorität Niedrig aus, wenn diese Abfrage bei eventuellen Deadlockkonflikten verlieren und als die zu beendende Abfrage ausgewählt werden soll.

**Sperr Timeout festlegen** Der Standardwert-1 gibt an, dass Sperren aufrechterhalten werden, bis Transaktionen abgeschlossen sind. Der Wert 0 gibt an, dass nicht gewartet und eine Meldung zurückgegeben wird, sobald eine Sperre auftritt. Geben Sie einen Wert von mehr als 0 Millisekunden für die Beendigung einer Transaktion an, wenn die Transaktionssperren länger als diese Zeit aktiv bleiben sollen.

**QUERY_GOVERNOR_COST_LIMIT festlegen** Verwenden Sie die Option **Kostenbeschränkung der Abfrage** Kontrolle, um eine Obergrenze für den Zeitraum anzugeben, in dem eine Abfrage ausgeführt werden kann. Die Abfragekosten beziehen sich auf eine geschätzte Zeit in Sekunden, die für das Ausführen einer Abfrage bei einer bestimmten Hardwarekonfiguration benötigt wird. Die Standardeinstellung von 0 gibt an, dass die Zeit für die Ausführung einer Abfrage nicht begrenzt ist.

**Anbieter Nachrichten Header unterdrücken** Wenn dieses Kontrollkästchen aktiviert ist, werden keine Statusmeldungen vom Anbieter (z. b. der OLE DB Anbieter) angezeigt. Dieses Kontrollkästchen ist standardmäßig aktiviert. Deaktivieren Sie dieses Kontrollkästchen, wenn bei der Problembehandlung für Abfragen, bei denen auf Anbieterebene ein Fehler auftritt, Anbieternachrichten angezeigt werden sollen.

**Verbindung nach Ausführung der Abfrage trennen** Wenn dieses Kontrollkästchen aktiviert ist, wird die Verbindung mit SQL Server nach Ausführung der Abfrage getrennt. Diese Option ist standardmäßig deaktiviert.

**Abschlusszeit anzeigen** Ermöglicht es Ihnen, die Zeit, zu der die Abfrage Ausführung abgeschlossen wurde, nach den Abfrage Ergebnissen oder auf der Registerkarte Nachrichten zu drucken.

Nachweis **Protokoll für VB-Enklaven für Always Encrypted** Ermöglicht das Festlegen eines Nachweis Protokolls für die virtualisierungsbasierte Sicherheit (VB)-Enklaven, die von Always verschlüsselt mit sicheren Enklaven verwendet werden.

Die derzeit unterstützten Nachweis Protokolle lauten:

* Host-Überwachungsdienst: ein Nachweis Protokoll, das den Windows-Host-Überwachungsdienst (HGS) verwendet.

Weitere Informationen finden Sie unter [Always Encrypted mit sicheren Enklaven](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-enclaves?view=sqlallproducts-allversions) und [sicherem Enclave](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-enclaves?view=sqlallproducts-allversions#secure-enclave-attestation)-Nachweis.

**Standard wiederherstellen** Setzt alle auf dieser Seite verfügbaren Werte auf die ursprünglichen Standardwerte zurück.
