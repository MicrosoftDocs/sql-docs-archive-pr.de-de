---
title: Common Criteria-Konformität aktiviert (Serverkonfigurationsoption) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- common criteria compliance
helpviewer_keywords:
- CC (common criteria) [Database Engine]
- common criteria compliance [Database Engine]
- Risidual Information Protection [Database Engine]
- RIP (Residual Information Protection)
ms.assetid: 61766eea-c450-408d-af33-fbe7ef8c9ff2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6722d05351b8b9e80240abb4edef0633a97b6da0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608854"
---
# <a name="common-criteria-compliance-enabled-server-configuration-option"></a>Common Criteria-Kompatibilität aktiviert (Serverkonfigurationsoption)
  Mit der Option Common Criteria-Kompatibilität aktiviert werden die folgenden Elemente aktiviert, die für die Common Criteria erforderlich sind.  
  
|Kriterien|BESCHREIBUNG|  
|--------------|-----------------|  
|RIP (Residual Information Protection)|Bei RIP muss eine Speicherbelegung mit einem bekannten Muster von Bits überschrieben werden, bevor der Arbeitsspeicher wieder einer neuen Quelle zugewiesen wird. Durch Einhalten des RIP-Standards kann die Sicherheit erhöht werden. Beim Überschreiben der Speicherbelegung kann jedoch die Leistung beeinträchtigt werden. Das Überschreiben wird erst ausgeführt, nachdem die Option Common Criteria-Kompatibilität aktiviert aktiviert wurde.|  
|Die Möglichkeit zum Anzeigen von Anmeldestatistiken|Die Anmeldungsüberwachung wird erst aktiviert, nachdem die Option Common Criteria-Kompatibilität aktiviert aktiviert wurde. Immer wenn sich ein Benutzer erfolgreich bei [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]anmeldet, werden Informationen zum Zeitpunkt der letzten erfolgreichen Anmeldung, zum Zeitpunkt der letzten erfolglosen Anmeldung sowie zur Anzahl der Versuche zwischen dem Zeitpunkt der letzten erfolgreichen Anmeldung und dem der aktuellen Anmeldung bereitgestellt. Diese Anmeldestatistiken können angezeigt werden, indem die dynamische Verwaltungssicht [sys.dm_exec_sessions](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql) abgefragt wird.|  
|DENY auf Tabellenebene sollte nicht durch GRANT auf Spaltenebene außer Kraft gesetzt werden|Nachdem die Option Common Criteria-Kompatibilität aktiviert aktiviert wurde, hat DENY auf Tabellenebene Vorrang vor GRANT auf Spaltenebene. Wenn die Option nicht aktiviert ist, hat GRANT auf Spaltenebene Vorrang vor DENY auf Tabellenebene.|  
  
 Die Option „Common Criteria-Kompatibilität aktiviert“ ist eine erweiterte Option. Allgemeine Kriterien werden nur für die Enterprise Edition und die Datacenter Edition ausgewertet und zertifiziert. Informationen zum aktuellen Status der Common Criteria-Zertifizierung finden Sie auf der Website [Microsoft SQL Server Common Criteria](https://go.microsoft.com/fwlink/?LinkId=616319) (in Englisch).  
  
> [!IMPORTANT]  
>  Zusätzlich zur Aktivierung der Option Common Criteria-Kompatibilität aktiviert müssen Sie ein Skript herunterladen und ausführen, mit dem die Konfiguration von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für die Kompatibilität mit der Common Criteria-Auswertungssicherungsstufe 4+ (EAL4+) ausgeführt wird. Sie können dieses Skript von der Website [Microsoft SQL Server Common Criteria](https://go.microsoft.com/fwlink/?LinkId=616319) (in Englisch) herunterladen.  
  
 Wenn Sie die Einstellung mithilfe der gespeicherten Systemprozedur sp_configure ändern, können Sie die Option Common Criteria-Kompatibilität aktiviert nur ändern, wenn für Erweiterte Optionen anzeigen der Wert 1 festgelegt ist. Diese Einstellung wird wirksam, nachdem der Server neu gestartet wurde. Die möglichen Werte lauten 0 und 1:  
  
-   Mit 0 wird angegeben, dass die Common Criteria-Kompatibilität nicht aktiviert ist. Dies ist die Standardoption.  
  
-   Mit 1 wird angegeben, dass die Common Criteria-Kompatibilität aktiviert ist.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Common Criteria-Kompatibilität aktiviert.  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'common criteria compliance enabled', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)  
  
  
