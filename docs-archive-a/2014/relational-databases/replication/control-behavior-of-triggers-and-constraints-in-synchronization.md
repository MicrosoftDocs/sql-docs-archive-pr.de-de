---
title: Steuern des Verhaltens von Triggern und Einschränkungen während der Synchronisierung (Replikations Programmierung mit Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- identities [SQL Server replication]
- constraints [SQL Server], replication
- triggers [SQL Server], replication
- triggers [SQL Server replication]
- constraints [SQL Server replication]
- NOT FOR REPLICATION option
- NFR option
ms.assetid: 7c4e0f0e-cadc-4c99-98f4-69799b9b356b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 88176f43295fe2ab1f5f5643a46db1ce6132c5f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608573"
---
# <a name="control-the-behavior-of-triggers-and-constraints-during-synchronization-replication-transact-sql-programming"></a>Kontrollieren des Verhaltens von Triggern und Einschränkungen während der Synchronisierung (Replikationsprogrammierung mit Transact-SQL)
  Während der Synchronisierung führen Replikation-Agents [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql)-Anweisungen und [UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql) sowie [DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql)-Anweisungen für replizierte Tabellen aus, was zur Ausführung von DML (Data Manipulation Language)-Triggern in diesen Tabellen führen kann. Es gibt Fälle, in denen Sie verhindern müssen, dass Trigger während der Synchronisierung ausgelöst werden oder Einschränkungen während der Synchronisierung erzwungen werden. Dieses Verhalten hängt davon ab, wie der Trigger oder die Einschränkung erstellt wird.  
  
### <a name="to-prevent-triggers-from-executing-during-synchronization"></a>So verhindern Sie, dass Trigger während der Synchronisierung ausgeführt werden  
  
1.  Geben Sie bei der Erstellung eines neuen Triggers die Option NOT FOR REPLICATION für [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) an.  
  
2.  Für einen vorhandenen Trigger geben Sie die Option NOT FOR REPLICATION für [ALTER TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql) an.  
  
### <a name="to-prevent-constraints-from-being-enforced-during-synchronization"></a>So verhindern Sie, dass Einschränkungen während der Synchronisierung erzwungen werden  
  
1.  Beim Erstellen einer neuen CHECK- oder FOREIGN KEY-Einschränkung geben Sie in der Einschränkungsdefinition von [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) die Option CHECK NOT FOR REPLICATION an.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von Tabellen &#40;Datenbank-Engine&#41;](../tables/create-tables-database-engine.md)  
  
  
