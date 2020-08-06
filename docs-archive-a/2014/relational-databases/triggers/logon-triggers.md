---
title: Logon-Trigger | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- logon triggers
- login triggers
helpviewer_keywords:
- triggers [SQL Server], logon
ms.assetid: 2f0ebb2f-de10-482d-9806-1a5de5b312b8
author: rothja
ms.author: jroth
ms.openlocfilehash: cda0be25f07ed2ee283b9707884041e7c6e4692f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621918"
---
# <a name="logon-triggers"></a>Logon-Trigger
  Logon-Trigger lösen gespeicherte Prozeduren als Antwort auf ein LOGON-Ereignis aus. Dieses Ereignis wird ausgelöst, wenn eine Benutzersitzung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]erstellt wird. Logon-Trigger werden ausgelöst, nachdem die Authentifizierungsphase der Anmeldung abgeschlossen ist und bevor die Benutzersitzung erstellt wird. Aus diesem Grund werden alle Meldungen, die aus dem Trigger stammen und normalerweise den Benutzer erreichen (z. B. Fehlermeldungen und Meldungen aus der PRINT-Anweisung) zum [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehlerprotokoll umgeleitet. Logon-Trigger werden nicht ausgelöst, wenn die Authentifizierung nicht ausgeführt werden kann.  
  
 Sie können Logon-Trigger zum Überwachen und Steuern von Serversitzungen verwenden, beispielsweise durch Nachverfolgung der Anmeldeaktivität, Einschränkung von Anmeldungen auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]oder durch Einschränkung der Anzahl der Sitzungen für einen bestimmten Anmeldenamen. Beispielsweise werden im folgenden Code durch den Logon-Trigger Anmeldeversuche für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] abgelehnt, die mit dem Anmeldenamen *login_test* initiiert werden, wenn mit diesem Anmeldenamen bereits drei Benutzersitzungen erstellt wurden.  
  
 [!code-sql[TriggerDDL#LogonTrigger1](../../snippets/tsql/SQL14/tsql/triggerddl/transact-sql/snippet_create_alter_drop_trigger.sql#logontrigger1)]  
  
 Beachten Sie, dass das LOGON-Ereignis dem AUDIT_LOGIN SQL-Ablaufverfolgungsereignis entspricht, das in [Ereignisbenachrichtigungen](../service-broker/event-notifications.md)verwendet werden kann. Der Hauptunterschied zwischen Triggern und Ereignisbenachrichtigungen besteht darin, dass Trigger synchron mit Ereignissen ausgelöst werden und Ereignisbenachrichtigungen sich asynchron verhalten. Dies bedeutet beispielsweise, dass Sie einen Logon-Trigger verwenden müssen, wenn Sie das Erstellen einer Sitzung abbrechen möchten. Eine Ereignisbenachrichtigung für ein AUDIT_LOGIN-Ereignis kann nicht für diesen Zweck verwendet werden.  
  
## <a name="specifying-first-and-last-trigger"></a>Angeben des ersten und des letzten Triggers  
 Für das LOGON-Ereignis können mehrere Trigger definiert werden. Jeder dieser Trigger kann als zuerst oder zuletzt für ein Ereignis ausgelöster Trigger festgelegt werden. Hierfür wird die gespeicherte Systemprozedur [sp_settriggerorder](/sql/relational-databases/system-stored-procedures/sp-settriggerorder-transact-sql) verwendet. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt es keine Garantie für die Ausführungsreihenfolge der restlichen Trigger.  
  
## <a name="managing-transactions"></a>Verwalten von Transaktionen  
 Bevor in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ein Logon-Trigger ausgelöst wird, wird in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine implizite Transaktion erstellt, die von keiner Benutzertransaktion abhängig ist. Aus diesem Grund lautet die Transaktionsanzahl 1, wenn der erste Logon-Trigger ausgelöst wird. Nachdem alle Logon-Trigger ausgeführt wurden, wird ein Commit für die Transaktion ausgeführt. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird wie bei anderen Arten von Triggern auch ein Fehler zurückgegeben, wenn die Ausführung eines Logon-Triggers mit der Transaktionsanzahl 0 abgeschlossen wird. Mit der ROLLBACK TRANSACTION-Anweisung wird die Transaktionsanzahl auch dann auf 0 zurückgesetzt, wenn die Anweisung in einer geschachtelten Transaktion ausgegeben wird. Mit COMMIT TRANSACTION kann die Transaktionsanzahl auf 0 verringert werden. Aus diesem Grund empfiehlt es sich nicht, COMMIT TRANSACTION-Anweisungen in Logon-Triggern auszugeben.  
  
 Bedenken Sie folgende Punkte, wenn Sie eine ROLLBACK TRANSACTION-Anweisung in Logon-Triggern verwenden:  
  
-   Für alle Datenänderungen, die bis zum Zeitpunkt von ROLLBACK TRANSACTION vorgenommen werden, wird ein Rollback ausgeführt. Zu diesen Änderungen zählen die durch den aktuellen Trigger vorgenommenen Änderungen sowie die durch vorherige Trigger erfolgten Änderungen, die für das gleiche Ereignis ausgeführt wurden. Die restlichen Trigger für dieses bestimmte Ereignis werden nicht ausgeführt.  
  
-   Durch den aktuellen Trigger werden weiterhin alle restlichen Anweisungen ausgeführt, die nach der ROLLBACK-Anweisung auftreten. Wenn durch eine dieser Anweisungen Daten geändert werden, wird für die Änderungen kein Rollback ausgeführt.  
  
 Es wird keine Benutzersitzung erstellt, wenn eine der folgenden Bedingungen während der Ausführung eines Triggers für ein LOGON-Ereignis auftritt:  
  
-   Für die ursprüngliche implizite Transaktion treten Rollbacks oder Fehler auf.  
  
-   Ein Fehler mit einem Schweregrad über 20 wird im Triggertext ausgelöst.  
  
## <a name="disabling-a-logon-trigger"></a>Deaktivieren eines Logon-Triggers  
 Ein Logon-Trigger kann effektiv erfolgreiche Verbindungen zu [!INCLUDE[ssDE](../../../includes/ssde-md.md)] für alle Benutzer verhindern, einschließlich Elementen der festen Serverrolle `sysadmin`. Wenn ein LOGON-Trigger Verbindungen verhindert, können die Mitglieder der festen Serverrolle `sysadmin` über die dedizierte Administratorverbindung eine Verbindung herstellen oder durch Starten des [!INCLUDE[ssDE](../../../includes/ssde-md.md)]s im minimalen Konfigurationsmodus (-f). Weitere Informationen finden Sie unter [Startoptionen für den Datenbank-Engine-Dienst](../../database-engine/configure-windows/database-engine-service-startup-options.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Aufgabe|Thema|  
|----------|-----------|  
|Beschreibt, wie Logon-Trigger erstellt werden. Logon-Trigger können anhand einer beliebigen Datenbank erstellt werden, sie werden jedoch auf der Serverebene registriert und befinden sich in der **master** -Datenbank.|[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql)|  
|Beschreibt, wie Logon-Trigger geändert werden.|[ALTER TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql)|  
|Beschreibt, wie Logon-Trigger gelöscht werden.|[DROP TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-trigger-transact-sql)|  
|Beschreibt, wie Informationen zu Logon-Triggern zurückgegeben werden.|[sys.server_triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql)<br /><br /> [sys.server_trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql)|  
|Beschreibt, wie Ereignisdaten zu Logon-Triggern aufgezeichnet werden.||  
  
## <a name="see-also"></a>Weitere Informationen  
 [DDL-Trigger](../triggers/ddl-triggers.md)  
  
  
