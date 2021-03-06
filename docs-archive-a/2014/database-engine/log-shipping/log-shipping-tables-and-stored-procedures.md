---
title: Protokollversandtabellen und gespeicherte Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- secondary servers [SQL Server]
- monitor servers [SQL Server]
- log shipping [SQL Server], system tables
- log shipping [SQL Server], stored procedures
- primary servers [SQL Server]
ms.assetid: 03420810-4c38-4c0c-adf0-913eb044c50a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f10a6555ed3a0c27a72c3d097cc200f21d901274
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697105"
---
# <a name="log-shipping-tables-and-stored-procedures"></a>Log Shipping Tables and Stored Procedures
  In diesem Thema werden alle mit der Protokollversandkonfiguration verknüpften Tabellen und gespeicherten Prozeduren beschrieben. Die Protokollversandtabellen sind auf allen Servern in **msdb** gespeichert. Die unten stehenden Tabellen beschreiben, welche Tabellen und gespeicherten Prozeduren auf welchen Servern in Protokollversandkonfigurationen verwendet werden.  
  
## <a name="primary-server-tables"></a>Tabellen des primären Servers  
  
|Tabelle|BESCHREIBUNG|  
|-----------|-----------------|  
|[log_shipping_monitor_alert](/sql/relational-databases/system-tables/log-shipping-monitor-alert-transact-sql)|Speichert die Warnungsauftrags-ID. Diese Tabelle wird auf dem primären Server nur dann verwendet, wenn kein Remoteüberwachungsserver konfiguriert wurde.|  
|[log_shipping_monitor_error_detail](/sql/relational-databases/system-tables/log-shipping-monitor-error-detail-transact-sql)|Speichert Fehlerdetails für Protokollversandaufträge, die dem primären Server zugeordnet sind.|  
|[log_shipping_monitor_history_detail](/sql/relational-databases/system-tables/log-shipping-monitor-history-detail-transact-sql)|Speichert Verlaufsdetails für Protokollversandaufträge, die dem primären Server zugeordnet sind.|  
|[log_shipping_monitor_primary](/sql/relational-databases/system-tables/log-shipping-monitor-primary-transact-sql)|Speichert einen Überwachungseintrag für die primäre Datenbank.|  
|[log_shipping_primary_databases](/sql/relational-databases/system-tables/log-shipping-primary-databases-transact-sql)|Enthält Konfigurationsinformationen für die primären Datenbanken eines bestimmten Servers. Speichert eine Zeile pro primäre Datenbank.|  
|[log_shipping_primary_secondaries](/sql/relational-databases/system-tables/log-shipping-primary-secondaries-transact-sql)|Ordnet primäre Datenbanken sekundären Datenbanken zu.|  
  
## <a name="primary-server-stored-procedures"></a>Gespeicherte Prozeduren des primären Servers  
  
|Gespeicherte Prozedur|BESCHREIBUNG|  
|----------------------|-----------------|  
|[sp_add_log_shipping_primary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql)|Richtet die primäre Datenbank, einschließlich des Sicherungsauftrags sowie des lokalen und Remoteüberwachungseintrags, für eine Protokollversandkonfiguration ein.|  
|[sp_add_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-secondary-transact-sql)|Fügt zu einer vorhandenen primären Datenbank den Namen einer sekundären Datenbank hinzu.|  
|[sp_change_log_shipping_primary_database](/sql/relational-databases/system-stored-procedures/sp-change-log-shipping-primary-database-transact-sql)|Ändert die Einstellungen der primären Datenbank, einschließlich des lokalen und Remoteüberwachungseintrags.|  
|[sp_cleanup_log_shipping_history](/sql/relational-databases/system-stored-procedures/sp-cleanup-log-shipping-history-transact-sql)|Löscht Verlaufsinformationen je nach Aufbewahrungsdauer lokal und auf dem Monitor.|  
|[sp_delete_log_shipping_primary_database](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-database-transact-sql)|Löscht den Protokollversand der primären Datenbank, einschließlich des Sicherungsauftrags, des lokalen und Remoteverlaufs.|  
|[sp_delete_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-secondary-transact-sql)|Entfernt den Namen einer sekundären Datenbank aus einer primären Datenbank.|  
|[sp_help_log_shipping_primary_database](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-primary-database-transact-sql)|Ruft Einstellungen der primären Datenbank ab und zeigt die Werte aus den Tabellen **log_shipping_primary_databases** und **log_shipping_monitor_primary** an.|  
|[sp_help_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-primary-secondary-transact-sql)|Ruft die Namen sekundärer Datenbanken für eine primäre Datenbank ab.|  
|[sp_refresh_log_shipping_monitor](/sql/relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql)|Aktualisiert die Anzeige auf die neuesten Informationen für den angegebenen Protokollversand-Agent.|  
  
## <a name="secondary-server-tables"></a>Tabellen des sekundären Servers  
  
|Tabelle|BESCHREIBUNG|  
|-----------|-----------------|  
|[log_shipping_monitor_alert](/sql/relational-databases/system-tables/log-shipping-monitor-alert-transact-sql)|Speichert die Warnungsauftrags-ID. Diese Tabelle wird auf dem sekundären Server nur dann verwendet, wenn kein Remoteüberwachungsserver konfiguriert wurde.|  
|[log_shipping_monitor_error_detail](/sql/relational-databases/system-tables/log-shipping-monitor-error-detail-transact-sql)|Speichert Fehlerdetails für Protokollversandaufträge, die dem sekundären Server zugeordnet sind.|  
|[log_shipping_monitor_history_detail](/sql/relational-databases/system-tables/log-shipping-monitor-history-detail-transact-sql)|Speichert Verlaufsdetails für Protokollversandaufträge, die dem sekundären Server zugeordnet sind.|  
|[log_shipping_monitor_secondary](/sql/relational-databases/system-tables/log-shipping-monitor-secondary-transact-sql)|Speichert einen Überwachungseintrag für jede sekundäre Datenbank, die dem sekundären Server zugeordnet ist.|  
|[log_shipping_secondary](/sql/relational-databases/system-tables/log-shipping-secondary-transact-sql)|Enthält Konfigurationsinformationen für die sekundären Datenbanken eines bestimmten Servers. Speichert eine Zeile pro sekundäre ID.|  
|[log_shipping_secondary_databases](/sql/relational-databases/system-tables/log-shipping-secondary-databases-transact-sql)|Speichert die Konfigurationsinformationen für eine bestimmte sekundäre Datenbank. Speichert eine Zeile pro sekundäre Datenbank.|  
  
> [!NOTE]  
>  Sekundäre Datenbanken, die zu einer primären Datenbank gehören und auf demselben sekundären Server verwaltet werden, nutzen die Einstellungen der **log_shipping_secondary** -Tabelle gemeinsam. Wenn eine freigegebene Eigenschaft für eine einzelne sekundäre Datenbank geändert wird, wird die geänderte Einstellung auch für alle übrigen Datenbanken wirksam.  
  
## <a name="secondary-server-stored-procedures"></a>Gespeicherte Prozeduren des sekundären Servers  
  
|Gespeicherte Prozedur|BESCHREIBUNG|  
|----------------------|-----------------|  
|[sp_add_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql)|Richtet eine sekundäre Datenbank für den Protokollversand ein.|  
|[sp_add_log_shipping_secondary_primary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-primary-transact-sql)|Richtet die primären Informationen ein, fügt Links zur lokalen und Remoteüberwachung hinzu und erstellt auf dem sekundären Server Kopier- und Wiederherstellungsaufträge für die angegebene primäre Datenbank.|  
|[sp_change_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-change-log-shipping-secondary-database-transact-sql)|Ändert die Einstellungen der sekundären Datenbank, einschließlich lokaler und Remoteüberwachungseinträge.|  
|[sp_change_log_shipping_secondary_primary](/sql/relational-databases/system-stored-procedures/sp-change-log-shipping-secondary-primary-transact-sql)|Ändert die Einstellungen der sekundären Datenbank, z. B. Quell- und Zielverzeichnis, sowie die Aufbewahrungsdauer von Dateien.|  
|[sp_cleanup_log_shipping_history](/sql/relational-databases/system-stored-procedures/sp-cleanup-log-shipping-history-transact-sql)|Löscht Verlaufsinformationen je nach Aufbewahrungsdauer lokal und auf dem Monitor.|  
|[sp_delete_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql)|Löscht eine sekundäre Datenbank sowie den lokalen und den Remoteverlauf.|  
|[sp_delete_log_shipping_secondary_primary](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-primary-transact-sql)|Entfernt die Informationen zu dem angegebenen primären Server vom sekundären Server.|  
|[sp_help_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-secondary-database-transact-sql)|Ruft Einstellungen der sekundären Datenbank aus den Tabellen **log_shipping_secondary**, **log_shipping_secondary_databases**, und **log_shipping_monitor_secondary** ab.|  
|[sp_help_log_shipping_secondary_primary](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-secondary-primary-transact-sql)|Diese gespeicherte Prozedur ruft die Einstellungen einer angegebenen primären Datenbank auf dem sekundären Server ab.|  
|[sp_refresh_log_shipping_monitor](/sql/relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql)|Aktualisiert die Anzeige auf die neuesten Informationen für den angegebenen Protokollversand-Agent.|  
  
## <a name="monitor-server-tables"></a>Tabellen des Überwachungsservers  
  
|Tabelle|BESCHREIBUNG|  
|-----------|-----------------|  
|[log_shipping_monitor_alert](/sql/relational-databases/system-tables/log-shipping-monitor-alert-transact-sql)|Speichert die Warnungsauftrags-ID.|  
|[log_shipping_monitor_error_detail](/sql/relational-databases/system-tables/log-shipping-monitor-error-detail-transact-sql)|Speichert Fehlerdetails für Protokollversandaufträge.|  
|[log_shipping_monitor_history_detail](/sql/relational-databases/system-tables/log-shipping-monitor-history-detail-transact-sql)|Speichert Verlaufsdetails für Protokollversandaufträge.|  
|[log_shipping_monitor_primary](/sql/relational-databases/system-tables/log-shipping-monitor-primary-transact-sql)|Speichert einen Überwachungseintrag für jede primäre Datenbank, die diesem Überwachungsserver zugeordnet ist.|  
|[log_shipping_monitor_secondary](/sql/relational-databases/system-tables/log-shipping-monitor-secondary-transact-sql)|Speichert einen Überwachungseintrag für jede sekundäre Datenbank, die diesem Überwachungsserver zugeordnet ist.|  
  
## <a name="monitor-server-stored-procedures"></a>Gespeicherte Prozeduren des Überwachungsservers  
  
|Gespeicherte Prozedur|BESCHREIBUNG|  
|----------------------|-----------------|  
|[sp_add_log_shipping_alert_job](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-alert-job-transact-sql)|Erstellt einen Warnungsauftrag des Protokollversands, falls dieser noch nicht erstellt wurde.|  
|[sp_delete_log_shipping_alert_job](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-alert-job-transact-sql)|Entfernt den Warnungsauftrag des Protokollversands, falls keine zugeordneten primären Datenbanken vorhanden sind.|  
|[sp_help_log_shipping_alert_job](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-alert-job-transact-sql)|Gibt die Auftrags-ID des Warnungsauftrags zurück.|  
|[sp_help_log_shipping_monitor_primary](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-primary-transact-sql)|Gibt Überwachungsdatensätze für die angegebene primäre Datenbank aus der **log_shipping_monitor_primary** -Tabelle zurück.|  
|[sp_help_log_shipping_monitor_secondary](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-secondary-transact-sql)|Gibt Überwachungsdatensätze für die angegebene sekundäre Datenbank aus der **log_shipping_monitor_secondary** -Tabelle zurück.|  
  
  
