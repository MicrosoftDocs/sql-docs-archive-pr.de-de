---
title: SQL Server-Verschlüsselung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- encryption [SQL Server], about encryption
- security [SQL Server], encryption
- cryptography [SQL Server], about cryptography
ms.assetid: ead0150e-4943-4ad5-84c8-36f85c7278f4
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 6fc68e6f3280a8e23d6a1bf4f364aadfffd69f85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87726830"
---
# <a name="sql-server-encryption"></a>SQL Server-Verschlüsselung
  Als Verschlüsselung wird der Vorgang bezeichnet, Daten mithilfe eines Schlüssels oder eines Kennworts unlesbar zu machen. Die Daten werden dadurch ohne den entsprechenden Entschlüsselungsschlüssel oder das Kennwort unbrauchbar. Durch Verschlüsselung werden keine Probleme der Zugriffssteuerung gelöst. Sie erhöht jedoch die Sicherheit, indem sie den Datenverlust auch dann einschränkt, wenn die Zugriffssteuerung umgangen wird. Wenn der Hostcomputer einer Datenbank beispielsweise falsch konfiguriert wurde und ein Hacker Zugriff auf vertrauliche Daten erlangt, sind diese gestohlenen Daten sehr wahrscheinlich nutzlos, wenn sie verschlüsselt wurden.  
  
 Sie können in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Verbindungen, Daten und gespeicherte Prozeduren verschlüsseln. Die folgende Tabelle enthält weitere Informationen zur Verschlüsselung in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  Zwar ist die Verschlüsselung ein wertvolles Mittel, Sicherheit zu gewährleisten, sollte jedoch nicht für alle Daten oder Verbindungen verwendet werden. Bevor Sie sich dafür entscheiden, Verschlüsselung zu verwenden, prüfen Sie, wie Benutzer auf die Daten zugreifen. Wenn Benutzer über ein öffentliches Netzwerk auf Daten zugreifen, könnte die Datenverschlüsselung die Sicherheit erhöhen. Wenn sich aber der gesamte Zugriff innerhalb einer sicheren Intranetkonfiguration abspielt, ist eine Verschlüsselung möglicherweise nicht erforderlich. Jede Verwendung der Verschlüsselung sollte auch eine Wartungsstrategie für Kennwörter, Schlüssel und Zertifikate einschließen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Verschlüsselungshierarchie](encryption-hierarchy.md)  
 Informationen zur Verschlüsselungshierarchie in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Auswählen eines Verschlüsselungsalgorithmus](choose-an-encryption-algorithm.md)  
 Informationen zur Auswahl eines wirksamen Verschlüsselungsalgorithmus.  
  
 [Transparente Datenverschlüsselung &#40;TDE&#41;](transparent-data-encryption.md)  
 Allgemeine Informationen über das transparente Verschlüsseln von Daten.  
  
 [Verschlüsselungsschlüssel für SQL Server und Datenbank &#40;Datenbank-Engine&#41;](sql-server-and-database-encryption-keys-database-engine.md)  
 Die Verschlüsselungsschlüssel in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]bestehen aus einer Kombination von öffentlichen, privaten und symmetrischen Schlüsseln, die zum Schutz sensibler Daten verwendet werden. Dieser Abschnitt erklärt, wie Verschlüsselungsschlüssel implementiert und verwaltet werden.  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [Sichern von SQL Server](../securing-sql-server.md)  
 Überblick über die Absicherung der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Plattform und die Arbeit mit Benutzern und sicherungsfähigen Objekten.  
  
 [Kryptografiefunktionen &#40;Transact-SQL&#41;](/sql/t-sql/functions/cryptographic-functions-transact-sql)  
 Informationen dazu, wie Kryptografiefunktionen implementiert werden.  
  
 [ENCRYPTBYPASSPHRASE &#40;Transact-SQL&#41;](/sql/t-sql/functions/encryptbypassphrase-transact-sql)  
 Informationen dazu, wie ein Kennwort zur Verschlüsselung von Daten verwendet wird.  
  
 [ENCRYPTBYKEY &#40;Transact-SQL&#41;](/sql/t-sql/functions/encryptbykey-transact-sql)  
 Informationen dazu, wie ein symmetrischer Schlüssel zur Verschlüsselung von Daten verwendet wird.  
  
 [ENCRYPTBYASYMKEY &#40;Transact-SQL&#41;](/sql/t-sql/functions/encryptbyasymkey-transact-sql)  
 Informationen dazu, wie ein asymmetrischer Schlüssel zur Verschlüsselung von Daten verwendet wird.  
  
 [ENCRYPTBYCERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/encryptbycert-transact-sql)  
 Informationen dazu, wie ein Zertifikat zur Verschlüsselung von Daten verwendet wird.  
  
## <a name="external-resources"></a>Externe Ressourcen  
 [10 Schritte zum SQL Server 2005-Sicherheit](https://www.itprotoday.com/sql-server/10-steps-sql-server-2005-security)  
 Aktuelle Informationen über die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Sicherheit.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys.key_encryptions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-key-encryptions-transact-sql)   
 [Verschlüsselungsschlüssel für SQL Server und Datenbank &#40;Datenbank-Engine&#41;](sql-server-and-database-encryption-keys-database-engine.md)   
 [Sichern und Wiederherstellen von Reporting Services-Verschlüsselungsschlüsseln](../../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)  
  
  
