---
title: Rollen auf Serverebene | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.Security.BUILTIN.administrators
- sql12.Security.NT_AUTHORITY.SYSTEM
helpviewer_keywords:
- roles [SQL Server], server-level
- principals [SQL Server], server-level
- CONTROL SERVER permission
- fixed server roles [SQL Server]
- credentials [SQL Server], roles
- sysadmin fixed server role
- server-level roles [SQL Server]
- authentication [SQL Server], roles
ms.assetid: 7adf2ad7-015d-4cbe-9e29-abaefd779008
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 4e8f2e75eb5272f30153814e923048b4f5c4f8b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700953"
---
# <a name="server-level-roles"></a>Rollen auf Serverebene
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] stellt Rollen auf Serverebene bereit, um Sie beim Verwalten der Berechtigungen auf einem Server zu unterstützen. Bei diesen Rollen handelt es sich um Sicherheitsprinzipale, in denen andere Prinzipale gruppiert sind. Der Geltungsbereich der Berechtigungen von Rollen auf Serverebene erstreckt sich auf den gesamten Server. (*Rollen* entsprechen den *Gruppen* im Betriebssystem Windows.)  
  
 Feste Serverrollen werden der Einfachheit halber und zur Gewährung der Abwärtskompatibilität bereitgestellt. Weisen Sie nach Möglichkeit spezifischere Berechtigungen zu.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sind neun feste Serverrollen verfügbar. Die den festen Serverrollen erteilten Berechtigungen können nicht geändert werden. Ab [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] können Sie benutzerdefinierte Serverrollen erstellen und diesen Berechtigungen auf Serverebene hinzufügen.  
  
 Sie können Prinzipale auf Serverebene ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Anmeldungen, Windows-Konten und Windows-Gruppen) zu Rollen auf Serverebene zusammenfassen. Jedes Mitglied einer festen Serverrolle kann der gleichen Rolle andere Anmeldenamen hinzufügen. Mitglieder benutzerdefinierter Serverrollen können der Rolle keine weiteren Serverprinzipale hinzufügen.  
  
## <a name="fixed-server-level-roles"></a>Feste Rollen auf Serverebene  
 In der folgenden Tabelle werden die festen Rollen auf Serverebene und deren Möglichkeiten angezeigt.  
  
|Feste Rolle auf Serverebene|BESCHREIBUNG|  
|------------------------------|-----------------|  
|Serverrollen|Mitglieder der festen Serverrolle sysadmin können alle Aktivitäten auf dem Server ausführen.|  
|serveradmin|Mitglieder der festen Serverrolle serveradmin können serverweite Konfigurationsoptionen ändern und den Server herunterfahren.|  
|securityadmin|Mitglieder der festen Serverrolle securityadmin können Anmeldungen und deren Eigenschaften verwalten. Sie verfügen für Berechtigungen auf Serverebene über die Berechtigungen GRANT, DENY und REVOKE. Sie verfügen auf Datenbankebene auch über die Berechtigungen GRANT, DENY und REVOKE, sofern sie Zugriff eine Datenbank haben. Sie können außerdem Kennwörter für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Anmeldungen zurücksetzen.<br /><br /> ** \* \* Sicherheits \* Hinweis \* ** : die Möglichkeit, Zugriff auf zu gewähren [!INCLUDE[ssDE](../../../includes/ssde-md.md)] und Benutzerberechtigungen zu konfigurieren, ermöglicht dem Sicherheitsadministrator die Zuweisung der meisten Server Berechtigungen. Die `securityadmin` Rolle sollte als Äquivalent zur-Rolle behandelt werden `sysadmin` .|  
|processadmin|Mitglieder der festen Serverrolle processadmin können Prozesse beenden, die in einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ausgeführt werden.|  
|setupadmin|Mitglieder der festen Serverrolle „setupadmin“ können Verbindungsserver mithilfe von [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisungen hinzufügen und entfernen. (Die Verwendung von [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]erfordert die Mitgliedschaft in „sysadmin“.)|  
|bulkadmin|Mitglieder der festen Serverrolle bulkadmin können die BULK INSERT-Anweisung ausführen.|  
|diskadmin|Die feste Serverrolle diskadmin wird zum Verwalten von Datenträgerdateien verwendet.|  
|dbcreator|Mitglieder der festen Serverrolle dbcreator können beliebige Datenbanken erstellen, ändern, löschen und wiederherstellen.|  
|public|Jede [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Anmeldung gehört zur Serverrolle public. Wenn einem Serverprinzipal keine bestimmten Berechtigungen für ein sicherungsfähiges Objekt erteilt oder verweigert werden, erbt der Benutzer die Berechtigungen, die der Rolle public für dieses Objekt erteilt wurden. Weisen Sie einem Objekt nur dann public-Berechtigungen zu, wenn das Objekt für alle Benutzer verfügbar sein soll. Sie können keine Mitgliedschaft in „public“ ändern.<br /><br /> Hinweis: „public“ wird anders implementiert als andere Rollen. Berechtigungen können jedoch von „public“ gewährt, verweigert oder widerrufen werden.|  
  
## <a name="permissions-of-fixed-server-roles"></a>Berechtigungen fester Serverrollen  
 Jede feste Serverrolle besitzt bestimmte Berechtigungen. Eine Übersicht der Berechtigungen, die Serverrollen zugewiesen sind, finden Sie unter [Feste Serverrollen und feste Datenbankrollen der Datenbank-Engine](https://social.technet.microsoft.com/wiki/contents/articles/2024.database-engine-fixed-server-and-fixed-database-roles.aspx).  
  
> [!IMPORTANT]  
>  Die Berechtigung `CONTROL SERVER` ist ähnlich, aber nicht identisch mit der festen Serverrolle `sysadmin`. Berechtigungen umfassen keine Rollenmitgliedschaften, und Rollenmitgliedschaften gewähren keine Berechtigungen. (Beispiele: `CONTROL SERVER`impliziert nicht die Mitgliedschaft in der `sysadmin` Server Rolle "Fixed".) Es ist jedoch manchmal möglich, die Identität zwischen Rollen und entsprechenden Berechtigungen anzunehmen. Die meisten `DBCC`-Befehle und viele Systemprozeduren erfordern die Mitgliedschaft in der festen Serverrolle `sysadmin`. Eine Liste mit 171 gespeicherten System Prozeduren, die eine `sysadmin` Mitgliedschaft erfordern, finden Sie im folgenden Blogbeitrag von Andreas Wolter [Control Server im Vergleich zu sysadmin/SA: Berechtigungen, System Prozeduren, DBCC, automatische Schema Erstellung und Berechtigungs Ausweitung](http://www.insidesql.org/blogs/andreaswolter/2013/08/control-server-vs-sysadmin-sa-permissions-privilege-escalation-caveats).  
  
## <a name="server-level-permissions"></a>Berechtigung auf Serverebene  
 Benutzerdefinierten Serverrollen können nur Berechtigungen auf Serverebene hinzugefügt werden. Führen Sie zum Auflisten der Berechtigungen auf Serverebene die folgende Anweisung aus. Folgende Berechtigungen gelten auf Serverebene:  
  
```sql  
SELECT * FROM sys.fn_builtin_permissions('SERVER') ORDER BY permission_name;  
```  
  
 Weitere Informationen zu Berechtigungen finden Sie unter [Berechtigungen &#40;Datenbank-Engine&#41;](../permissions-database-engine.md) und [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql).  
  
## <a name="working-with-server-level-roles"></a>Arbeiten mit Rollen auf Serverebene  
 In der folgenden Tabelle werden die Befehle, Sichten und Funktionen erklärt, die Sie beim Arbeiten mit Rollen auf Serverebene verwenden können.  
  
|Funktion|type|BESCHREIBUNG|  
|-------------|----------|-----------------|  
|[sp_helpsrvrole &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpsrvrole-transact-sql)|Metadaten|Gibt eine Liste von Rollen auf Serverebene zurück.|  
|[sp_helpsrvrolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpsrvrolemember-transact-sql)|Metadaten|Gibt Informationen zu Mitgliedern einer Rolle auf Serverebene zurück.|  
|[sp_srvrolepermission &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-srvrolepermission-transact-sql)|Metadaten|Zeigt die Berechtigungen einer Rolle auf Serverebene an.|  
|[IS_SRVROLEMEMBER &#40;Transact-SQL&#41;](/sql/t-sql/functions/is-srvrolemember-transact-sql)|Metadaten|Gibt an, ob eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Anmeldung Mitglied der angegebenen Rolle auf Serverebene ist.|  
|[sys.server_role_members &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-role-members-transact-sql)|Metadaten|Gibt eine Zeile für jedes Mitglied jeder Rolle auf Serverebene zurück.|  
|[sp_addsrvrolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql)|Get-Help|Fügt einen Benutzernamen als Mitglied einer Rolle auf Serverebene hinzu. Veraltet. Verwenden Sie stattdessen [ALTER SERVER ROLE](/sql/t-sql/statements/alter-server-role-transact-sql) .|  
|[sp_dropsrvrolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsrvrolemember-transact-sql)|Get-Help|Entfernt einen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Anmeldenamen oder einen Windows-Benutzer bzw. eine -Gruppe aus einer Rolle auf Serverebene. Veraltet. Verwenden Sie stattdessen [ALTER SERVER ROLE](/sql/t-sql/statements/alter-server-role-transact-sql) .|  
|[CREATE SERVER ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-role-transact-sql)|Get-Help|Erstellt eine benutzerdefinierte Serverrolle.|  
|[ALTER SERVER ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-server-role-transact-sql)|Get-Help|Ändert die Mitgliedschaft einer Serverrolle oder ändert Namen einer benutzerdefinierten Serverrolle.|  
|[DROP SERVER ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-server-role-transact-sql)|Get-Help|Entfernt eine benutzerdefinierte Serverrolle.|  
|[IS_SRVROLEMEMBER &#40;Transact-SQL&#41;](/sql/t-sql/functions/is-srvrolemember-transact-sql)|Funktion|Bestimmt die Mitgliedschaft einer Serverrolle.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Rollen auf Datenbankebene](../authentication-access/database-level-roles.md)   
 [Sicherheitskatalogsichten &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/security-catalog-views-transact-sql)   
 [Sicherheitsfunktionen &#40;Transact-SQL&#41;](/sql/t-sql/functions/security-functions-transact-sql)   
 [Sichern von SQL Server](../securing-sql-server.md)   
 [GRANT (Berechtigungen für Serverprinzipal) &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-server-principal-permissions-transact-sql)   
 [REVOKE (Berechtigungen für Serverprinzipal) &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-server-principal-permissions-transact-sql)   
 [DENY (Berechtigungen für Serverprinzipal) &#40;Transact-SQL&#41;](/sql/t-sql/statements/deny-server-principal-permissions-transact-sql)   
 [Erstellen einer Serverrolle](../authentication-access/create-a-server-role.md)  
  
  
