---
title: Einrichten einer verschlüsselten Spiegeldatenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/26/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- cryptography [SQL Server], database mirroring
- encryption [SQL Server], database mirroring
- database master key [SQL Server], database mirroring
- mirror database [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 7329a575-be29-46e0-abc6-1344db37920c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a5148411792f1ea881bba59e599252284575bbdf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701757"
---
# <a name="set-up-an-encrypted-mirror-database"></a>Einrichten einer verschlüsselten Spiegeldatenbank

Geben Sie zum Aktivieren der automatischen Entschlüsselung des Datenbank-Hauptschlüssels einer Spiegeldatenbank das Kennwort an, das zum Verschlüsseln des Hauptschlüssels der Spiegelserverinstanz verwendet wurde. [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höhere Versionen schließen Mechanismen zum Übertragen des Kennworts ein. Erstellen Sie vor Beginn der Datenbankspiegelung eine Berechtigung für den Datenbank-Hauptschlüssel mithilfe von **sp_control_dbmasterkey_password** . Sie müssen diesen Vorgang für jede Datenbank wiederholen, die Sie spiegeln möchten. Weitere Informationen finden Sie unter [sp_control_dbmasterkey_password &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql).
  
> [!CAUTION]  
>  Aktivieren Sie keine Failoverentschlüsselung einer Datenbank, auf die **sa** und andere Serverprinzipale mit hohen Berechtigungen nicht zugreifen dürfen. Sie können eine Datenbank so konfigurieren, dass ihre Schlüsselhierarchie nicht vom Diensthauptschlüssel entschlüsselt werden kann. Diese Option wird als sicherer Schutz für Datenbanken unterstützt, die Informationen enthalten, auf die **Systemadministratoren** oder andere Serverprinzipale mit hohen Berechtigungen nicht zugreifen dürfen sollten. Durch die Aktivierung der Failoverentschlüsselung einer solchen Datenbank wird dieser sichere Schutz entfernt, wodurch **Systemadministratoren** und andere Serverprinzipale mit hohen Berechtigungen die Datenbank entschlüsseln können.  


<!-- Note: We cannot append '?view=sql-server-2016' to these, even tho in theory we might want to. -->

## <a name="see-also"></a>Weitere Informationen

[sp_control_dbmasterkey_password &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql)

[CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql)

[ALTER MASTER KEY (Transact-SQL)](/sql/t-sql/statements/alter-master-key-transact-sql)

[Verschlüsselungshierarchie](../../relational-databases/security/encryption/encryption-hierarchy.md)

[Einrichten der Datenbankspiegelung &#40;SQL Server&#41;](database-mirroring-sql-server.md)

