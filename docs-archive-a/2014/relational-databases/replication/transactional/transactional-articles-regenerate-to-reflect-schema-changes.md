---
title: Erneutes Generieren von Transaktionsprozeduren zur Erfassung von Schemaänderungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- custom procedures [SQL Server replication]
- transactional replication, replicating schema changes
- schemas [SQL Server replication], replicating changes
ms.assetid: ccf68a13-e748-4455-8168-90e6d2868098
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7b41b5309816e037ce3619e880b796e0653c7506
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87722689"
---
# <a name="regenerate-custom-transactional-procedures-to-reflect-schema-changes"></a>Erneutes Generieren von Transaktionsprozeduren zur Erfassung von Schemaänderungen
  Änderungen von Daten auf den Abonnenten werden bei der Transaktionsreplikation standardmäßig mithilfe von gespeicherten Prozeduren vorgenommen, die durch interne Prozeduren für jeden Tabellenartikel in der Veröffentlichung generiert werden. Die drei Prozeduren (eine für Einfügungen, eine für Updates und eine für Löschungen) werden auf den Abonnenten kopiert und ausgeführt, wenn eine Einfügung, ein Update oder eine Löschung auf den Abonnenten repliziert wird. Wenn bei einer Tabelle auf einem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Verleger eine Schemaänderung vorgenommen wird, werden diese Prozeduren bei der Replikation automatisch erneut generiert, indem derselbe Satz interner Skriptprozeduren aufgerufen wird, damit die neuen Prozeduren dem neuen Schema entsprechen (die Replikation von Schemaänderungen wird bei Oracle-Verlegern nicht unterstützt).  
  
 Es ist auch möglich, benutzerdefinierte Prozeduren anzugeben, die an die Stelle einer oder mehrerer Standardprozedur(en) treten. Benutzerdefinierte Prozeduren müssen immer dann geändert werden, wenn sich die Schemaänderung auf die jeweilige Prozedur auswirkt. Wenn eine Prozedur z. B. auf eine Spalte verweist, die in einer Schemaänderung gelöscht wurde, müssen die Verweise auf diese Spalte aus der Prozedur entfernt werden. Für die Weitergabe einer neuen benutzerdefinierten Prozedur an Abonnenten durch Replikation gibt es die folgenden beiden Möglichkeiten:  
  
-   Die erste Möglichkeit besteht in der Verwendung einer benutzerdefinierten Skriptprozedur zum Ersetzen der von der Replikation verwendeten Standardprozeduren:  
  
    1.  Wenn Sie [sp_addarticle &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)ausführen, stellen Sie sicher, dass das **@schema_option** 0x02-Bit den Wert **true**hat.  
  
    2.  Führen Sie [sp_register_custom_scripting &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql) aus, und geben Sie den Wert "Insert", "Update" oder "Delete" für den Parameter **@type** und den Namen der benutzerdefinierten Skript Prozedur für den Parameter an **@value** .  
  
     Wenn das nächste Mal eine Schemaänderung vorgenommen wird, ruft die Replikation diese gespeicherte Prozedur auf, um die Definition für die neue benutzerdefinierte gespeicherte Prozedur auszugeben. Anschließend wird die Prozedur an die einzelnen Abonnenten weitergegeben.  
  
-   Die zweite Möglichkeit besteht darin, ein Skript zu verwenden, das eine neue benutzerdefinierte Prozedurdefinition enthält:  
  
    1.  Wenn Sie [sp_addarticle &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)ausführen, legen **@schema_option** Sie das 0x02-Bit auf **false** fest, damit die Replikation nicht automatisch benutzerdefinierte Prozeduren auf dem Abonnenten generiert.  
  
    2.  Erstellen Sie vor jeder Schemaänderung eine neue Skriptdatei, und registrieren Sie das Skript bei der Replikation, indem Sie [sp_register_custom_scripting &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql) ausführen. Geben Sie für den Parameter den Wert ' custom_script ' **@type** und für den Parameter den Pfad zum Skript auf dem Verleger an **@value** .  
  
     Bei der nächsten relevanten Schemaänderung wird dieses Skript innerhalb derselben Transaktion wie der DDL-Befehl auf allen Abonnenten ausgeführt. Nach Abschluss der Schemaänderung wird die Registrierung des Skripts aufgehoben. Damit das Skript bei einer weiteren Schemaänderung wieder ausgeführt wird, müssen Sie es erneut registrieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Angeben der Weitergabemethode für Änderungen bei Transaktionsartikeln](transactional-articles-specify-how-changes-are-propagated.md)   
 [Vornehmen von Schemaänderungen in Veröffentlichungsdatenbanken](../publish/make-schema-changes-on-publication-databases.md)  
  
  
