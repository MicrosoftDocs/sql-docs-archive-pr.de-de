---
title: Löschen von Arbeitsauslastungsgruppen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- workload groups [SQL Server], delete
- Resource Governor, workload group delete
ms.assetid: d5902c46-5c28-4ac1-8b56-cb4ca2b072d0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 801a731db6c5b31bc479d1a3f6079c45ad9a7c04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699417"
---
# <a name="delete-a-workload-group"></a>Löschen von Arbeitsauslastungsgruppen
  Eine Arbeitsauslastungsgruppe oder einen Ressourcenpool können Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder mit Transact-SQL löschen.  
  
-   **Vorbereitungen:**  [Begrenzungen und Einschränkungen](#LimitationsRestrictions), [Berechtigungen](#Permissions)  
  
-   **So löschen Sie eine Arbeitsauslastungsgruppe mit:**  [dem Objekt-Explorer](#DelWGObjEx), [Resource Governor-Eigenschaften](#DelWGRGProp), [Transact-SQL](#DelWGTSQL)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
 Sie können keine Arbeitsauslastungsgruppe löschen, die aktive Sitzungen enthält.  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> Einschränkungen  
 Falls eine Arbeitsauslastungsgruppe aktive Sitzungen enthält, tritt beim Löschen bzw. Verschieben der Arbeitsauslastungsgruppe in einen anderen Ressourcenpool ein Fehler auf, wenn Sie die ALTER RESOURCE GOVERNOR RECONFIGURE-Anweisung aufrufen, um die Änderung zu übernehmen. Führen Sie eine der folgenden Aktionen aus, um dieses Problem zu umgehen:  
  
-   Warten Sie, bis die Verbindungen für alle Sitzungen der entsprechenden Gruppe geschlossen wurden, und führen Sie dann die ALTER RESOURCE GOVERNOR RECONFIGURE-Anweisung noch einmal aus.  
  
-   Stoppen Sie die Sitzungen in der betreffenden Gruppe explizit mit dem KILL-Befehl, und führen Sie die ALTER RESOURCE GOVERNOR RECONFIGURE-Anweisung noch einmal aus. Falls Sie beschließen, die aktiven Sitzungen nicht explizit zu beenden, nachdem Sie **Löschen** verwendet, die Sitzungen jedoch noch nicht gestoppt haben, erstellen Sie die Gruppe noch einmal mit dem ursprünglichen Namen und verschieben sie in den ursprünglichen Ressourcenpool.  
  
-   Starten Sie den Server neu. Nach Abschluss des Neustarts wird die gelöschte Gruppe nicht erstellt und die neue Ressourcenpoolzuordnung wird von einer verschobenen Gruppe verwendet.  
  
###  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Zum Löschen einer Arbeitsauslastungsgruppe ist die CONTROL SERVER-Berechtigung erforderlich.  
  
##  <a name="delete-a-workload-group-using-object-explorer"></a><a name="DelWGObjEx"></a> Löschen einer Arbeitsauslastungsgruppe im Objekt-Explorer  
 **So löschen Sie eine Arbeitsauslastungsgruppe im Objekt-Explorer**  
  
1.  Öffnen Sie in[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]den Objekt-Explorer und erweitern Sie rekursiv den Knoten **Verwaltung** bis einschließlich zum Eintrag **Ressourcenpools**.  
  
2.  Erweitern Sie im Ressourcenpool rekursiv den Knoten **Ressourcenpools** bis einschließlich zum Knoten **Arbeitsauslastungsgruppen** , der die zu löschende Arbeitsauslastungsgruppe enthält.  
  
3.  Klicken Sie mit der rechten Maustaste auf die Arbeitsauslastungsgruppe, und klicken Sie dann auf **Löschen**.  
  
4.  Im Fenster **Objekt löschen** wird die Arbeitsauslastungsgruppe in der Liste **Zu löschendes Objekt** aufgeführt. Um die Arbeitsauslastungsgruppe zu löschen, klicken Sie auf **OK**.  
  
##  <a name="delete-a-workload-group-using-resource-governor-properties"></a><a name="DelWGRGProp"></a> Löschen einer Arbeitsauslastungsgruppe über die Eigenschaften der Ressourcenkontrolle  
 **So löschen Sie eine Arbeitsauslastungsgruppe auf der Seite "Eigenschaften der Ressourcenkontrolle"**  
  
1.  Erweitern Sie im Objekt-Explorer den Knoten **Verwaltung** so lange, bis der Eintrag **Ressourcenpools**angezeigt wird.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Ressourcenpool, der die zu löschende Arbeitsauslastungsgruppe enthält, und klicken Sie dann auf **Eigenschaften**. Die Seite **Eigenschaften der Ressourcenkontrolle** wird angezeigt.  
  
3.  Klicken Sie im Fenster **Arbeitsauslastungsgruppen für Ressourcenpool** auf die Zeile für die zu löschende Arbeitsauslastungsgruppe, klicken Sie dann links neben der Zeile mit der rechten Maustaste auf den Pfeil nach rechts, und klicken Sie dann auf **Löschen**.  
  
4.  Um die Arbeitsauslastungsgruppe zu löschen, klicken Sie auf **OK**.  
  
##  <a name="delete-a-workload-group-using-transact-sql"></a><a name="DelWGTSQL"></a> Löschen einer Arbeitsauslastungsgruppe mit Transact-SQL  
 **So löschen Sie eine Arbeitsauslastungsgruppe mit Transact-SQL**  
  
1.  Führen Sie die `DROP WORKLOAD GROUP`-Anweisung aus, die den Namen der zu löschenden Arbeitsauslastungsgruppe angeben.  
  
2.  Stellen Sie sicher, dass in der zu löschenden Arbeitsauslastungsgruppe keine Anforderungen mehr aktiv sind, bevor Sie die `ALTER RESOURCE GOVERNOR RECONFIGURE`-Anweisung ausgeben. Wenn aktive Anforderungen vorhanden sind, tritt bei `ALTER RESOURCE GOVERNOR` ein Fehler auf. Führen Sie eine der folgenden Aktionen aus, um dieses Problem zu vermeiden:  
  
    -   Warten Sie, bis alle Sitzungen der Arbeitsauslastungsgruppe die Verbindung geschlossen haben.  
  
    -   Beenden Sie Sitzungen in der Arbeitsauslastungsgruppe explizit mit dem `KILL`-Befehl.  
  
    -   Starten Sie den Server neu. Die Arbeitsauslastungsgruppe wird nicht neu erstellt.  
  
    -   Falls Sie nach Ausgabe der `DROP WORKLOAD GROUP`-Anweisung beschließen, dass Sie keine Sitzungen explizit stoppen möchten, um die Änderung zu übernehmen, können Sie die Gruppe mit dem gleichen Namen, den sie vor Ausgabe der DROP-Anweisung hatte, neu erstellen und dann in den ursprünglichen Ressourcenpool verschieben.  
  
3.  Führen Sie die- `ALTER RESOURCE GOVERNOR RECONFIGURE` Anweisung aus.  
  
### <a name="example-transact-sql"></a>Beispiel (Transact-SQL)  
 Das folgende Beispiel löscht die Arbeitsauslastungsgruppe `groupAdhoc`.  
  
```  
DROP WORKLOAD GROUP groupAdhoc;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Resource Governor](resource-governor.md)   
 [Erstellen eines Ressourcenpools](create-a-resource-pool.md)   
 [Erstellen einer Arbeitsauslastungsgruppe](create-a-workload-group.md)   
 [Löschen eines Ressourcenpools](delete-a-resource-pool.md)   
 [DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-workload-group-transact-sql)   
 [DROP RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-resource-pool-transact-sql)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
