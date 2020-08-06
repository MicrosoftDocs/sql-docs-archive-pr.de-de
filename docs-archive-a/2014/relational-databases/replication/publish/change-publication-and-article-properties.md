---
title: Ändern von Veröffentlichungs- und Artikeleigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- modifying article properties
- modifying publication properties
- administering replication, properties
- publications [SQL Server replication], changing properties
- articles [SQL Server replication], properties
ms.assetid: f7df51ef-c088-4efc-b247-f91fb2c6ff32
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 185e5d0beb9df2ec8a3dcf263632c1d260a3bcd7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87622563"
---
# <a name="change-publication-and-article-properties"></a>Ändern von Veröffentlichungs- und Artikeleigenschaften
  Nach dem Erstellen einer Veröffentlichung können die meisten Veröffentlichungs- und Artikeleigenschaften geändert werden. Bei Änderungen bestimmter Eigenschaften muss jedoch die Momentaufnahme erneut generiert und/oder die Abonnements müssen erneut initialisiert werden. Dieses Thema enthält Informationen zu allen Eigenschaften, bei deren Änderung eine oder beide der genannten Aktionen erforderlich werden.  
  
## <a name="publication-properties-for-snapshot-and-transactional-replication"></a>Veröffentlichungseigenschaften für die Momentaufnahme- und Transaktionsreplikation  
  
|BESCHREIBUNG|Gespeicherte Prozedur|Eigenschaften|Requirements (Anforderungen)|  
|-----------------|----------------------|----------------|------------------|  
|Ändern des Momentaufnahmeformats|**sp_changepublication**|**sync_method**|Neue Momentaufnahme|  
|Ändern des Momentaufnahmespeicherorts|**sp_changepublication**|**alt_snapshot_folder**<br /><br /> **snapshot_in_defaultfolder**|Neue Momentaufnahme|  
|Ändern des Momentaufnahmespeicherorts|**sp_changedistpublisher**|**working_directory**|Neue Momentaufnahme|  
|Ändern der Momentaufnahmekomprimierung|**sp_changepublication**|**compress_snapshot**|Neue Momentaufnahme|  
|Ändern der FTP-Momentaufnahmeoptionen|**sp_changepublication**|**enabled_for_internet**<br /><br /> **ftp_address**<br /><br /> **ftp_login**<br /><br /> **ftp_password**<br /><br /> **ftp_port**<br /><br /> **ftp_subdirectory**|Neue Momentaufnahme|  
|Ändern des Skriptspeicherorts vor und nach der Momentaufnahme|**sp_changepublication**|**pre_snapshot_script**<br /><br /> **post_snapshot_script**|Neue Momentaufnahme (auch bei Änderung des Skriptinhalts notwendig)<br /><br /> Zum Anwenden des neuen Skripts auf den Abonnenten ist eine erneute Initialisierung erforderlich.|  
|Aktivieren oder Deaktivieren der Unterstützung für [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Benutzer ohne Abonnement|**sp_changepublication**|**is_enabled_for_het_sub**|Neue Momentaufnahme|  
|Ändern der Konfliktberichterstellung bei Abonnements mit verzögertem Update über eine Warteschlange|**sp_changepublication**|**centralized_conflicts**|Änderung nur möglich, wenn keine aktiven Abonnements vorhanden sind.|  
|Ändern der Richtlinie zur Konfliktlösung bei Abonnements mit verzögertem Update über eine Warteschlange|**sp_changepublication**|**conflict_policy**|Änderung nur möglich, wenn keine aktiven Abonnements vorhanden sind.|  
  
## <a name="article-properties-for-snapshot-and-transactional-replication"></a>Artikeleigenschaften für die Momentaufnahme- und Transaktionsreplikation  
  
|BESCHREIBUNG|Gespeicherte Prozedur|Eigenschaften|Requirements (Anforderungen)|  
|-----------------|----------------------|----------------|------------------|  
|Löschen eines Artikels|**sp_droparticle**|Alle Parameter|Artikel können vor dem Erstellen von Abonnements gelöscht werden. Bei Verwendung von gespeicherten Prozeduren kann ein Abonnement eines Artikels gelöscht werden; wird dagegen [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]verwendet, muss das gesamte Abonnement gelöscht, neu erstellt und synchronisiert werden. Weitere Informationen finden Sie unter [Hinzufügen und Löschen von Artikeln aus vorhandenen Veröffentlichungen](add-articles-to-and-drop-articles-from-existing-publications.md).|  
|Ändern eines Spaltenfilters|**sp_articlecolumn**|**\@Kolumne**<br /><br /> **\@Betriebs**|Neue Momentaufnahme<br /><br /> Erneutes Initialisieren von Abonnements|  
|Hinzufügen eines Zeilenfilters|**sp_articlefilter**|Alle Parameter|Neue Momentaufnahme<br /><br /> Erneutes Initialisieren von Abonnements|  
|Löschen eines Zeilenfilters|**sp_articlefilter**|**\@Artikel**|Neue Momentaufnahme<br /><br /> Erneutes Initialisieren von Abonnements|  
|Ändern eines Zeilenfilters|**sp_articlefilter**|**\@filter_clause**|Neue Momentaufnahme<br /><br /> Erneutes Initialisieren von Abonnements|  
|Ändern eines Zeilenfilters|**sp_changearticle**|**filter**|Neue Momentaufnahme<br /><br /> Erneutes Initialisieren von Abonnements|  
|Ändern von Schemaoptionen|**sp_changearticle**|**schema_option**|Neue Momentaufnahme|  
|Ändern der Art und Weise, wie vor dem Anwenden der Momentaufnahme mit Tabellen auf dem Abonnenten umgegangen wird|**sp_changearticle**|**pre_creation_cmd**|Neue Momentaufnahme|  
|Ändern des Artikelstatus|**sp_changearticle**|**status**|Neue Momentaufnahme|  
|Ändern des INSERT-, UPDATE- oder DELETE-Befehls|**sp_changearticle**|**ins_cmd**<br /><br /> **upd_cmd**<br /><br /> **del_cmd**|Neue Momentaufnahme<br /><br /> Erneutes Initialisieren von Abonnements|  
|Ändern des Zieltabellennamens|**sp_changearticle**|**dest_table**|Neue Momentaufnahme<br /><br /> Erneutes Initialisieren von Abonnements|  
|Ändern des Besitzers der Zieltabelle (Schema)|**sp_changearticle**|**destination_owner**|Neue Momentaufnahme<br /><br /> Erneutes Initialisieren von Abonnements|  
|Ändern der Datentypzuordnungen (gilt nur für Oracle-Veröffentlichungen)|**sp_changearticlecolumndatatype**|**\@Sorte**<br /><br /> **\@Füll**<br /><br /> **\@präziser**<br /><br /> **\@migen**|Neue Momentaufnahme<br /><br /> Erneutes Initialisieren von Abonnements|  
  
## <a name="publication-properties-for-merge-replication"></a>Veröffentlichungseigenschaften für die Mergereplikation  
  
|BESCHREIBUNG|Gespeicherte Prozedur|Eigenschaften|Requirements (Anforderungen)|  
|-----------------|----------------------|----------------|------------------|  
|Ändern des Momentaufnahmeformats|**sp_changemergepublication**|**sync_mode**|Neue Momentaufnahme|  
|Ändern des Momentaufnahmespeicherorts|**sp_changemergepublication**|**alt_snapshot_folder**<br /><br /> **snapshot_in_defaultfolder**|Neue Momentaufnahme|  
|Ändern des Momentaufnahmespeicherorts|**sp_changedistpublisher**|**working_directory**|Neue Momentaufnahme|  
|Ändern der Momentaufnahmekomprimierung|**sp_changemergepublication**|**compress_snapshot**|Neue Momentaufnahme|  
|Ändern der FTP-Momentaufnahmeoptionen|**sp_changemergepublication**|**enabled_for_internet**<br /><br /> **ftp_address**<br /><br /> **ftp_login**<br /><br /> **ftp_password**<br /><br /> **ftp_port**<br /><br /> **ftp_subdirectory**|Neue Momentaufnahme|  
|Ändern der Skripts vor und nach der Momentaufnahme|**sp_changemergepublication**|**pre_snapshot_script**<br /><br /> **post_snapshot_script**|Neue Momentaufnahme (auch bei Änderung des Skriptinhalts notwendig)<br /><br /> Zum Anwenden des neuen Skripts auf den Abonnenten ist eine erneute Initialisierung erforderlich.|  
|Hinzufügen eines Joinfilters oder logischen Datensatzes|**sp_addmergefilter**|Alle Parameter|Neue Momentaufnahme<br /><br /> Erneutes Initialisieren von Abonnements|  
|Löschen eines Joinfilters oder logischen Datensatzes|**sp_dropmergefilter**|Alle Parameter|Neue Momentaufnahme<br /><br /> Erneutes Initialisieren von Abonnements|  
|Ändern eines Joinfilters oder logischen Datensatzes|**sp_changemergefilter**|**\@Property**<br /><br /> **\@Wert**|Neue Momentaufnahme<br /><br /> Erneutes Initialisieren von Abonnements|  
|Deaktivieren der Verwendung parametrisierter Filter (das Aktivieren parametrisierter Filter erfordert keine besonderen Aktionen)|**sp_changemergepublication**|Wert **false** für **dynamic_filters**|Neue Momentaufnahme<br /><br /> Erneutes Initialisieren von Abonnements|  
|Aktivieren oder Deaktivieren der Verwendung von vorausberechneten Partitionen|**sp_changemergepublication**|**use_partition_groups**|Neue Momentaufnahme|  
|Aktivieren oder Deaktivieren der [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] Partitions Optimierung.|**sp_changemergepublication**|**keep_partition_changes**|Erneutes Initialisieren von Abonnements|  
|Aktivieren bzw. Deaktivieren der Abonnementpartitionsüberprüfung|**sp_changemergepublication**|**validate_subscriber_info**|Erneutes Initialisieren von Abonnements|  
|Ändern des Veröffentlichungskompatibilitätsgrades auf 80sp3 oder niedriger|**sp_changemergepublication**|**publication_compatibility_level**|Neue Momentaufnahme|  
  
## <a name="article-properties-for-merge-replication"></a>Artikeleigenschaften für die Mergereplikation  
  
|BESCHREIBUNG|Gespeicherte Prozedur|Eigenschaften|Requirements (Anforderungen)|  
|-----------------|----------------------|----------------|------------------|  
|Löschen eines Artikels, der den zuletzt parametrisierten Filter in der Veröffentlichung enthält|**sp_dropmergearticle**|Alle Parameter|Neue Momentaufnahme<br /><br /> Erneutes Initialisieren von Abonnements|  
|Löschen eines Artikels, der einem Joinfilter oder einem logischen Datensatz übergeordnet ist (mit der Nebenwirkung, dass der Join gelöscht wird).|**sp_dropmergearticle**|Alle Parameter|Neue Momentaufnahme<br /><br /> Erneutes Initialisieren von Abonnements|  
|Löschen eines Artikels in allen anderen Fällen|**sp_dropmergearticle**|Alle Parameter|Neue Momentaufnahme|  
|Einbinden eines Spaltenfilters, der zuvor nicht veröffentlicht wurde|**sp_mergearticlecolumn**|**\@Kolumne**<br /><br /> **\@Betriebs**|Neue Momentaufnahme<br /><br /> Erneutes Initialisieren von Abonnements|  
|Hinzufügen, Löschen oder Ändern eines Zeilenfilters|**sp_changemergearticle**|**subset_filterclause**|Neue Momentaufnahme<br /><br /> Erneutes Initialisieren von Abonnements<br /><br /> Wenn Sie einen parametrisierten Filter hinzufügen, löschen oder ändern, können ausstehende Änderungen auf dem Abonnenten während der erneuten Initialisierung nicht auf den Verleger hochgeladen werden. Wenn Sie ausstehende Änderungen hochladen möchten, sollten Sie vor dem Ändern des Filters alle Abonnements synchronisieren.<br /><br /> Wenn ein Artikel in keinem Joinfilter enthalten ist, können Sie den Artikel löschen und mit einem anderen Zeilenfilter wieder hinzufügen. Das erneute Initialisieren des gesamten Abonnements ist nicht notwendig. Informationen zum Hinzufügen und Löschen von Artikeln finden Sie unter [Hinzufügen und Löschen von Artikeln aus vorhandenen Veröffentlichungen](add-articles-to-and-drop-articles-from-existing-publications.md).|  
|Ändern von Schemaoptionen|**sp_changemergearticle**|**schema_option**|Neue Momentaufnahme|  
|Ändern der Nachverfolgung auf Spaltenebene in die Nachverfolgung auf Zeilenebene (beim Ändern der Nachverfolgung auf Zeilenebene in die Nachverfolgung auf Spaltenebene sind keine gesonderten Aktionen notwendig)|**sp_changemergearticle**|Wert **false** für **column_tracking**|Neue Momentaufnahme<br /><br /> Erneutes Initialisieren von Abonnements|  
|Ändern, ob Berechtigungen geprüft werden, bevor auf dem Abonnenten vorgenommene Anweisungen auf den Verleger angewendet werden|**sp_changemergearticle**|**check_permissions**|Neue Momentaufnahme<br /><br /> Erneutes Initialisieren von Abonnements|  
|Aktivieren bzw. Deaktivieren von nur zum Herunterladen berechtigten Abonnements (beim Ändern in oder aus andere(n) Uploadoptionen sind keine gesonderten Aktionen erforderlich)|**sp_changemergearticle**|Ändern in den oder aus dem Wert **2** für **subscriber_upload_options**|Erneutes Initialisieren von Abonnements|  
|Ändern des Besitzers der Zieltabelle|**sp_changemergearticle**|**destination_owner**|Neue Momentaufnahme<br /><br /> Erneutes Initialisieren von Abonnements|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Häufig gestellte Fragen für Replikationsadministratoren](../administration/frequently-asked-questions-for-replication-administrators.md)   
 [Erstellen und Anwenden der Momentaufnahme](../create-and-apply-the-snapshot.md)   
 [Erneutes Initialisieren von Abonnements](../reinitialize-subscriptions.md)   
 [sp_addmergefilter &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql)   
 [sp_articlecolumn &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql)   
 [sp_articlefilter &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql)   
 [sp_changearticle &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql)   
 [sp_changearticlecolumndatatype &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-changearticlecolumndatatype-transact-sql)   
 [sp_changedistpublisher &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql)   
 [sp_changemergearticle &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)   
 [sp_changemergefilter &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergefilter-transact-sql)   
 [sp_changemergepublication &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)   
 [sp_changepublication &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)   
 [sp_droparticle &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-droparticle-transact-sql)   
 [sp_dropmergearticle &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergearticle-transact-sql)   
 [sp_dropmergefilter &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql)   
 [sp_mergearticlecolumn &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql)  
  
  
