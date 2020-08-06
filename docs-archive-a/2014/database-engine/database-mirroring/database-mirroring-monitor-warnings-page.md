---
title: Datenbankspiegelungs-Monitor (Seite Warnungen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dbmmonitor.warningsandalerts.f1
ms.assetid: 01936122-961d-436b-ba3c-5f79fefe5469
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e7afc4ff0e6b69c70535ef39677f3d834edbee15
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87726258"
---
# <a name="database-mirroring-monitor-warnings-page"></a>Datenbankspiegelungs-Monitor (Seite Warnungen)
  Zeigt eine schreibgeschützte Liste mit Warnungen an, die für Datenbank-Spiegelungsereignisse unterstützt werden, sowie (falls verfügbar) die angegebenen Warnungsschwellenwerte.  
  
 **So verwenden Sie SQL Server Management Studio zum Überwachen der Datenbankspiegelung**  
  
-   [Starten des Datenbankspiegelungs-Monitors &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
## <a name="columns"></a>Spalten  
 **Warning**  
 Für folgende Warnungen können Sie einen Schwellenwert definieren:  
  
|Warnung|Schwellenwert|  
|-------------|---------------|  
|**Warnhinweis anzeigen, wenn das nicht gesendete Protokoll den Schwellenwert überschreitet.**|Gibt an, wie viele Kilobyte (KB) nicht gesendeten Protokolls eine Warnung auf der Prinzipalserverinstanz generieren werden. Diese Warnung hilft, das Datenverlustrisiko in KB zu messen, und ist besonders für den Modus für hohe Leistung relevant. Die Warnung ist aber auch für den Modus für hohe Sicherheit relevant, wenn die Spiegelung angehalten oder unterbrochen wird, weil die Verbindung zwischen den Partnern getrennt wurde.|  
|**Warnhinweis anzeigen, wenn das nicht wiederhergestellte Protokoll den Schwellenwert überschreitet.**|Gibt an, wie viele KB nicht wiederhergestellten Protokolls eine Warnung auf der Spiegelserverinstanz generieren werden. Diese Warnung ist hilfreich beim Messen der Failoverzeit in Kilobyte. Die*Failoverzeit* besteht hauptsächlich aus der Zeit, die der frühere Spiegelserver benötigt, um ein Rollforward für die Protokolldaten auszuführen, die sich noch in seiner Wiederholungswarteschlange befinden, sowie einer zusätzlichen kurzen Zeitspanne.<br /><br /> Hinweis: Bei einem automatischen Failover hängt die Zeitspanne, die es dauert, bis das System den Fehler bemerkt, nicht von der Failoverzeit ab.<br /><br /> Weitere Informationen finden Sie unter [Einschätzen der Unterbrechung des Diensts während des Rollenwechsels &#40;Datenbankspiegelung&#41;](estimate-the-interruption-of-service-during-role-switching-database-mirroring.md)ausgetauscht werden.|  
|**Warnhinweis anzeigen, wenn das Alter der ältesten, nicht gesendeten Transaktion den Schwellenwert überschreitet.**|Gibt die Menge an Transaktionen (in Anzahl Minuten) an, die sich in der Sendewarteschlange ansammeln dürfen, bevor auf der Prinzipalserverinstanz eine Warnung generiert wird. Diese Warnung hilft, das Datenverlustrisiko in Bezug auf die Zeit zu messen, und ist besonders für den Modus für hohe Leistung relevant. Die Warnung ist aber auch für den Modus für hohe Sicherheit relevant, wenn die Spiegelung angehalten oder unterbrochen wird, weil die Verbindung zwischen den Partnern getrennt wurde.|  
|**Warnhinweis anzeigen, wenn der Spiegelungscommitaufwand den Schwellenwert überschreitet.**|Gibt an, wie viele Millisekunden durchschnittlicher Verzögerung pro Transaktion toleriert werden, bevor eine Warnung auf dem Prinzipalserver generiert wird. Hierbei handelt es sich um die Verzögerung, die entsteht, während die Prinzipalserverinstanz darauf wartet, dass die Spiegelserverinstanz den Transaktionsprotokolldatensatz in die Wiederholungswarteschlange schreibt. Dieser Wert ist nur im Modus für hohe Sicherheit relevant.|  
  
 **Schwellenwert auf '** _<Serverinstanz>_ **'**  
 Zeigt für jede der Warnungen gegebenenfalls den aktuellen vom Benutzer angegebenen Schwellenwert für eine der Serverinstanzen an. Der vollständige Instanzname der Serverinstanz wird in der entsprechenden Spaltenüberschrift angegeben.  
  
 Weitere Informationen finden Sie unter "Hinweise" weiter unten in diesem Thema.  
  
 **Schwellenwerte festlegen**  
 Klicken Sie auf diese Schaltfläche, um einen Schwellenwert für eine Warnung auf jedem der Failoverpartner festzulegen.  
  
 Weitere Informationen finden Sie unter "Hinweise" weiter unten in diesem Thema.  
  
## <a name="remarks"></a>Bemerkungen  
 Falls Informationen zum jetzigen Zeitpunkt für eine Serverinstanz nicht verfügbar sind, zeigen die Zellen der entsprechenden Spalte **Schwellenwert auf** einen grauen Hintergrund und Wasserzeichentext an. Wenn der Monitor nicht mit der Serverinstanz verbunden ist, wird in jeder Zelle des Rasters entweder **Nicht verbunden mit** _„<SYSTEMNAME>“_ oder **Nicht verbunden mit** _„<SYSTEMNAME>_ **\\** _<Instanzname>“_ angezeigt. Ausschlaggebend für die Statusmeldung ist, ob es sich bei der Instanz um die Standardinstanz oder eine benannte Instanz handelt. Wenn der Monitor auf die Rückgabe einer Abfrage wartet, zeigt das Raster in jeder Zelle **Auf Daten wird gewartet...** an.  
  
 Wenn Informationen verfügbar sind, zeigt die Zelle für jede Warnung entweder einen angegebenen Schwellenwert (und eine Maßeinheit) oder **Nicht aktiviert**an.  
  
 Wenn ein Schwellenwert zum Zeitpunkt des Updates der Statustabelle überschritten wird, wird ein Ereignis im Windows-Ereignisprotokoll protokolliert, sobald die Statuszeile aufgezeichnet wird. Standardmäßig wird die Statuszeile einmal pro Minute aufgezeichnet, wenn der Monitor nicht ausgeführt wird. Sie können eine Warnung für jeden protokollierten Ereignistyp konfigurieren, indem Sie den SQL Server-Agent oder ein anderes Programm verwenden, wie z. B. Microsoft Management Operations Manager (MOM).  
  
 Welche Ereignisse auf einen bestimmten Partner protokolliert werden, ist abhängig von dessen aktueller Rolle (Prinzipal oder Spiegel). Es ist jedoch empfehlenswert, einen Warnungsschwellenwert für ein bestimmtes Ereignis auf beiden Partnern festzulegen, um sicherzustellen, dass die Warnung weiterhin angezeigt wird, sobald ein Failover der Datenbank erfolgt. Der geeignete Schwellenwert für jeden Partner ist abhängig von der Leistungsfähigkeit des Systems des betreffenden Partners.  
  
> [!NOTE]  
>  Sie können auch die gespeicherte Systemprozedur **sp_dbmmonitorchangealert** verwenden, um Schwellenwerte für die entsprechenden Ereignisse (Nicht gesendetes Protokoll, Nicht wiederhergestelltes Protokoll, Älteste, nicht gesendete Transaktion und Spiegelungscommitaufwand) zu konfigurieren. Weitere Informationen finden Sie unter [sp_dbmmonitorchangealert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorchangealert-transact-sql).  
  
 Die folgende Tabelle zeigt die jeder Warnung zugeordnete Ereignis-ID.  
  
|Warnung des Datenbankspiegelungs-Monitors|Ereignisname|Ereignis-ID|  
|----------------------------------------|----------------|--------------|  
|**Warnhinweis anzeigen, wenn das nicht gesendete Protokoll den Schwellenwert überschreitet.**|Nicht gesendetes Protokoll|32042|  
|**Warnhinweis anzeigen, wenn das nicht wiederhergestellte Protokoll den Schwellenwert überschreitet.**|Nicht wiederhergestelltes Protokoll|32043|  
|**Warnhinweis anzeigen, wenn das Alter der ältesten, nicht gesendeten Transaktion den Schwellenwert überschreitet.**|Älteste, nicht gesendete Transaktion|32044|  
|**Warnhinweis anzeigen, wenn der Spiegelungscommitaufwand den Schwellenwert überschreitet.**|Spiegelungscommitaufwand|32045|  
  
## <a name="permissions"></a>Berechtigungen  
 Für vollständigen Zugriff wird die Mitgliedschaft in der festen Serverrolle **sysadmin** erfordert. Nur Mitglieder von **sysadmin** können auch Warnungsschwellenwerte für wichtige Leistungsmetriken konfigurieren und anzeigen.  
  
 Die Mitgliedschaft in der **dbm_monitor** -Rolle ermöglicht Ihnen lediglich das Anzeigen der neuesten Statuszeile auf der Seite **Warnungen** .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten des Datenbankspiegelungs-Monitors &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)   
 [Überwachen der Datenbankspiegelung &#40;SQL Server&#41;](database-mirroring-sql-server.md)   
 [Starten des Assistenten zum Konfigurieren der Sicherheit für die Datenbankspiegelung &#40;SQL Server Management Studio&#41;](start-the-configuring-database-mirroring-security-wizard.md)  
  
  
