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
# <a name="server-level-roles"></a><span data-ttu-id="e09a5-102">Rollen auf Serverebene</span><span class="sxs-lookup"><span data-stu-id="e09a5-102">Server-Level Roles</span></span>
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="e09a5-103">stellt Rollen auf Serverebene bereit, um Sie beim Verwalten der Berechtigungen auf einem Server zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="e09a5-103">provides server-level roles to help you manage the permissions on a server.</span></span> <span data-ttu-id="e09a5-104">Bei diesen Rollen handelt es sich um Sicherheitsprinzipale, in denen andere Prinzipale gruppiert sind.</span><span class="sxs-lookup"><span data-stu-id="e09a5-104">These roles are security principals that group other principals.</span></span> <span data-ttu-id="e09a5-105">Der Geltungsbereich der Berechtigungen von Rollen auf Serverebene erstreckt sich auf den gesamten Server.</span><span class="sxs-lookup"><span data-stu-id="e09a5-105">Server-level roles are server-wide in their permissions scope.</span></span> <span data-ttu-id="e09a5-106">(*Rollen* entsprechen den *Gruppen* im Betriebssystem Windows.)</span><span class="sxs-lookup"><span data-stu-id="e09a5-106">(*Roles* are like *groups* in the Windows operating system.)</span></span>  
  
 <span data-ttu-id="e09a5-107">Feste Serverrollen werden der Einfachheit halber und zur Gewährung der Abwärtskompatibilität bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="e09a5-107">Fixed server roles are provided for convenience and backward compatibility.</span></span> <span data-ttu-id="e09a5-108">Weisen Sie nach Möglichkeit spezifischere Berechtigungen zu.</span><span class="sxs-lookup"><span data-stu-id="e09a5-108">Assign more specific permissions whenever possible.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="e09a5-109">sind neun feste Serverrollen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="e09a5-109">provides nine fixed server roles.</span></span> <span data-ttu-id="e09a5-110">Die den festen Serverrollen erteilten Berechtigungen können nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="e09a5-110">The permissions that are granted to the fixed server roles cannot be changed.</span></span> <span data-ttu-id="e09a5-111">Ab [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] können Sie benutzerdefinierte Serverrollen erstellen und diesen Berechtigungen auf Serverebene hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="e09a5-111">Beginning with [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], you can create user-defined server roles and add server-level permissions to the user-defined server roles.</span></span>  
  
 <span data-ttu-id="e09a5-112">Sie können Prinzipale auf Serverebene ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Anmeldungen, Windows-Konten und Windows-Gruppen) zu Rollen auf Serverebene zusammenfassen.</span><span class="sxs-lookup"><span data-stu-id="e09a5-112">You can add server-level principals ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] logins, Windows accounts, and Windows groups) into server-level roles.</span></span> <span data-ttu-id="e09a5-113">Jedes Mitglied einer festen Serverrolle kann der gleichen Rolle andere Anmeldenamen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="e09a5-113">Each member of a fixed server role can add other logins to that same role.</span></span> <span data-ttu-id="e09a5-114">Mitglieder benutzerdefinierter Serverrollen können der Rolle keine weiteren Serverprinzipale hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="e09a5-114">Members of user-defined server roles cannot add other server principals to the role.</span></span>  
  
## <a name="fixed-server-level-roles"></a><span data-ttu-id="e09a5-115">Feste Rollen auf Serverebene</span><span class="sxs-lookup"><span data-stu-id="e09a5-115">Fixed Server-Level Roles</span></span>  
 <span data-ttu-id="e09a5-116">In der folgenden Tabelle werden die festen Rollen auf Serverebene und deren Möglichkeiten angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e09a5-116">The following table shows the fixed server-level roles and their capabilities.</span></span>  
  
|<span data-ttu-id="e09a5-117">Feste Rolle auf Serverebene</span><span class="sxs-lookup"><span data-stu-id="e09a5-117">Fixed server-level role</span></span>|<span data-ttu-id="e09a5-118">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="e09a5-118">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="e09a5-119">Serverrollen</span><span class="sxs-lookup"><span data-stu-id="e09a5-119">sysadmin</span></span>|<span data-ttu-id="e09a5-120">Mitglieder der festen Serverrolle sysadmin können alle Aktivitäten auf dem Server ausführen.</span><span class="sxs-lookup"><span data-stu-id="e09a5-120">Members of the sysadmin fixed server role can perform any activity in the server.</span></span>|  
|<span data-ttu-id="e09a5-121">serveradmin</span><span class="sxs-lookup"><span data-stu-id="e09a5-121">serveradmin</span></span>|<span data-ttu-id="e09a5-122">Mitglieder der festen Serverrolle serveradmin können serverweite Konfigurationsoptionen ändern und den Server herunterfahren.</span><span class="sxs-lookup"><span data-stu-id="e09a5-122">Members of the serveradmin fixed server role can change server-wide configuration options and shut down the server.</span></span>|  
|<span data-ttu-id="e09a5-123">securityadmin</span><span class="sxs-lookup"><span data-stu-id="e09a5-123">securityadmin</span></span>|<span data-ttu-id="e09a5-124">Mitglieder der festen Serverrolle securityadmin können Anmeldungen und deren Eigenschaften verwalten.</span><span class="sxs-lookup"><span data-stu-id="e09a5-124">Members of the securityadmin fixed server role manage logins and their properties.</span></span> <span data-ttu-id="e09a5-125">Sie verfügen für Berechtigungen auf Serverebene über die Berechtigungen GRANT, DENY und REVOKE.</span><span class="sxs-lookup"><span data-stu-id="e09a5-125">They can GRANT, DENY, and REVOKE server-level permissions.</span></span> <span data-ttu-id="e09a5-126">Sie verfügen auf Datenbankebene auch über die Berechtigungen GRANT, DENY und REVOKE, sofern sie Zugriff eine Datenbank haben.</span><span class="sxs-lookup"><span data-stu-id="e09a5-126">They can also GRANT, DENY, and REVOKE database-level permissions if they have access to a database.</span></span> <span data-ttu-id="e09a5-127">Sie können außerdem Kennwörter für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Anmeldungen zurücksetzen.</span><span class="sxs-lookup"><span data-stu-id="e09a5-127">Additionally, they can reset passwords for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] logins.</span></span><br /><br /> <span data-ttu-id="e09a5-128">\*\* \* \* Sicherheits \* Hinweis \* \*\* : die Möglichkeit, Zugriff auf zu gewähren [!INCLUDE[ssDE](../../../includes/ssde-md.md)] und Benutzerberechtigungen zu konfigurieren, ermöglicht dem Sicherheitsadministrator die Zuweisung der meisten Server Berechtigungen.</span><span class="sxs-lookup"><span data-stu-id="e09a5-128">**\*\* Security Note \*\*** The ability to grant access to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] and to configure user permissions allows the security admin to assign most server permissions.</span></span> <span data-ttu-id="e09a5-129">Die `securityadmin` Rolle sollte als Äquivalent zur-Rolle behandelt werden `sysadmin` .</span><span class="sxs-lookup"><span data-stu-id="e09a5-129">The `securityadmin` role should be treated as equivalent to the `sysadmin` role.</span></span>|  
|<span data-ttu-id="e09a5-130">processadmin</span><span class="sxs-lookup"><span data-stu-id="e09a5-130">processadmin</span></span>|<span data-ttu-id="e09a5-131">Mitglieder der festen Serverrolle processadmin können Prozesse beenden, die in einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="e09a5-131">Members of the processadmin fixed server role can end processes that are running in an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>|  
|<span data-ttu-id="e09a5-132">setupadmin</span><span class="sxs-lookup"><span data-stu-id="e09a5-132">setupadmin</span></span>|<span data-ttu-id="e09a5-133">Mitglieder der festen Serverrolle „setupadmin“ können Verbindungsserver mithilfe von [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisungen hinzufügen und entfernen.</span><span class="sxs-lookup"><span data-stu-id="e09a5-133">Members of the setupadmin fixed server role can add and remove linked servers by using [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="e09a5-134">(Die Verwendung von [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]erfordert die Mitgliedschaft in „sysadmin“.)</span><span class="sxs-lookup"><span data-stu-id="e09a5-134">(sysadmin membership is needed when using [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)].)</span></span>|  
|<span data-ttu-id="e09a5-135">bulkadmin</span><span class="sxs-lookup"><span data-stu-id="e09a5-135">bulkadmin</span></span>|<span data-ttu-id="e09a5-136">Mitglieder der festen Serverrolle bulkadmin können die BULK INSERT-Anweisung ausführen.</span><span class="sxs-lookup"><span data-stu-id="e09a5-136">Members of the bulkadmin fixed server role can run the BULK INSERT statement.</span></span>|  
|<span data-ttu-id="e09a5-137">diskadmin</span><span class="sxs-lookup"><span data-stu-id="e09a5-137">diskadmin</span></span>|<span data-ttu-id="e09a5-138">Die feste Serverrolle diskadmin wird zum Verwalten von Datenträgerdateien verwendet.</span><span class="sxs-lookup"><span data-stu-id="e09a5-138">The diskadmin fixed server role is used for managing disk files.</span></span>|  
|<span data-ttu-id="e09a5-139">dbcreator</span><span class="sxs-lookup"><span data-stu-id="e09a5-139">dbcreator</span></span>|<span data-ttu-id="e09a5-140">Mitglieder der festen Serverrolle dbcreator können beliebige Datenbanken erstellen, ändern, löschen und wiederherstellen.</span><span class="sxs-lookup"><span data-stu-id="e09a5-140">Members of the dbcreator fixed server role can create, alter, drop, and restore any database.</span></span>|  
|<span data-ttu-id="e09a5-141">public</span><span class="sxs-lookup"><span data-stu-id="e09a5-141">public</span></span>|<span data-ttu-id="e09a5-142">Jede [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Anmeldung gehört zur Serverrolle public.</span><span class="sxs-lookup"><span data-stu-id="e09a5-142">Every [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login belongs to the public server role.</span></span> <span data-ttu-id="e09a5-143">Wenn einem Serverprinzipal keine bestimmten Berechtigungen für ein sicherungsfähiges Objekt erteilt oder verweigert werden, erbt der Benutzer die Berechtigungen, die der Rolle public für dieses Objekt erteilt wurden.</span><span class="sxs-lookup"><span data-stu-id="e09a5-143">When a server principal has not been granted or denied specific permissions on a securable object, the user inherits the permissions granted to public on that object.</span></span> <span data-ttu-id="e09a5-144">Weisen Sie einem Objekt nur dann public-Berechtigungen zu, wenn das Objekt für alle Benutzer verfügbar sein soll.</span><span class="sxs-lookup"><span data-stu-id="e09a5-144">Only assign public permissions on any object when you want the object to be available to all users.</span></span> <span data-ttu-id="e09a5-145">Sie können keine Mitgliedschaft in „public“ ändern.</span><span class="sxs-lookup"><span data-stu-id="e09a5-145">You cannot change membership in public.</span></span><br /><br /> <span data-ttu-id="e09a5-146">Hinweis: „public“ wird anders implementiert als andere Rollen.</span><span class="sxs-lookup"><span data-stu-id="e09a5-146">Note: public is implemented differently than other roles.</span></span> <span data-ttu-id="e09a5-147">Berechtigungen können jedoch von „public“ gewährt, verweigert oder widerrufen werden.</span><span class="sxs-lookup"><span data-stu-id="e09a5-147">However, permissions can be granted, denied, or revoked from public.</span></span>|  
  
## <a name="permissions-of-fixed-server-roles"></a><span data-ttu-id="e09a5-148">Berechtigungen fester Serverrollen</span><span class="sxs-lookup"><span data-stu-id="e09a5-148">Permissions of Fixed Server Roles</span></span>  
 <span data-ttu-id="e09a5-149">Jede feste Serverrolle besitzt bestimmte Berechtigungen.</span><span class="sxs-lookup"><span data-stu-id="e09a5-149">Each fixed server role has certain permissions assigned to it.</span></span> <span data-ttu-id="e09a5-150">Eine Übersicht der Berechtigungen, die Serverrollen zugewiesen sind, finden Sie unter [Feste Serverrollen und feste Datenbankrollen der Datenbank-Engine](https://social.technet.microsoft.com/wiki/contents/articles/2024.database-engine-fixed-server-and-fixed-database-roles.aspx).</span><span class="sxs-lookup"><span data-stu-id="e09a5-150">For a chart of the permissions assigned to the server roles, see [Database Engine Fixed Server and Fixed Database Roles](https://social.technet.microsoft.com/wiki/contents/articles/2024.database-engine-fixed-server-and-fixed-database-roles.aspx).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e09a5-151">Die Berechtigung `CONTROL SERVER` ist ähnlich, aber nicht identisch mit der festen Serverrolle `sysadmin`.</span><span class="sxs-lookup"><span data-stu-id="e09a5-151">The `CONTROL SERVER` permission is similar but not identical to the `sysadmin` fixed server role.</span></span> <span data-ttu-id="e09a5-152">Berechtigungen umfassen keine Rollenmitgliedschaften, und Rollenmitgliedschaften gewähren keine Berechtigungen.</span><span class="sxs-lookup"><span data-stu-id="e09a5-152">Permissions do not imply role memberships and role memberships do not grant permissions.</span></span> <span data-ttu-id="e09a5-153">(Beispiele:</span><span class="sxs-lookup"><span data-stu-id="e09a5-153">(E.g.</span></span> <span data-ttu-id="e09a5-154">`CONTROL SERVER`impliziert nicht die Mitgliedschaft in der `sysadmin` Server Rolle "Fixed".) Es ist jedoch manchmal möglich, die Identität zwischen Rollen und entsprechenden Berechtigungen anzunehmen.</span><span class="sxs-lookup"><span data-stu-id="e09a5-154">`CONTROL SERVER` does not imply membership in the `sysadmin` fixed server role.) However, it is sometimes possible to impersonate between roles and equivalent permissions.</span></span> <span data-ttu-id="e09a5-155">Die meisten `DBCC`-Befehle und viele Systemprozeduren erfordern die Mitgliedschaft in der festen Serverrolle `sysadmin`.</span><span class="sxs-lookup"><span data-stu-id="e09a5-155">Most `DBCC` commands and many system procedures require membership in the `sysadmin` fixed server role.</span></span> <span data-ttu-id="e09a5-156">Eine Liste mit 171 gespeicherten System Prozeduren, die eine `sysadmin` Mitgliedschaft erfordern, finden Sie im folgenden Blogbeitrag von Andreas Wolter [Control Server im Vergleich zu sysadmin/SA: Berechtigungen, System Prozeduren, DBCC, automatische Schema Erstellung und Berechtigungs Ausweitung](http://www.insidesql.org/blogs/andreaswolter/2013/08/control-server-vs-sysadmin-sa-permissions-privilege-escalation-caveats).</span><span class="sxs-lookup"><span data-stu-id="e09a5-156">For a list of 171 system stored procedures that require `sysadmin` membership, see the following blog post by Andreas Wolter [CONTROL SERVER vs. sysadmin/sa: permissions, system procedures, DBCC, automatic schema creation and privilege escalation - caveats](http://www.insidesql.org/blogs/andreaswolter/2013/08/control-server-vs-sysadmin-sa-permissions-privilege-escalation-caveats).</span></span>  
  
## <a name="server-level-permissions"></a><span data-ttu-id="e09a5-157">Berechtigung auf Serverebene</span><span class="sxs-lookup"><span data-stu-id="e09a5-157">Server-Level Permissions</span></span>  
 <span data-ttu-id="e09a5-158">Benutzerdefinierten Serverrollen können nur Berechtigungen auf Serverebene hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="e09a5-158">Only server-level permissions can be added to user-defined server roles.</span></span> <span data-ttu-id="e09a5-159">Führen Sie zum Auflisten der Berechtigungen auf Serverebene die folgende Anweisung aus.</span><span class="sxs-lookup"><span data-stu-id="e09a5-159">To list the server-level permissions, execute the following statement.</span></span> <span data-ttu-id="e09a5-160">Folgende Berechtigungen gelten auf Serverebene:</span><span class="sxs-lookup"><span data-stu-id="e09a5-160">The server-level permissions are:</span></span>  
  
```sql  
SELECT * FROM sys.fn_builtin_permissions('SERVER') ORDER BY permission_name;  
```  
  
 <span data-ttu-id="e09a5-161">Weitere Informationen zu Berechtigungen finden Sie unter [Berechtigungen &#40;Datenbank-Engine&#41;](../permissions-database-engine.md) und [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="e09a5-161">For more information about permissions, see [Permissions &#40;Database Engine&#41;](../permissions-database-engine.md) and [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql).</span></span>  
  
## <a name="working-with-server-level-roles"></a><span data-ttu-id="e09a5-162">Arbeiten mit Rollen auf Serverebene</span><span class="sxs-lookup"><span data-stu-id="e09a5-162">Working with Server-Level Roles</span></span>  
 <span data-ttu-id="e09a5-163">In der folgenden Tabelle werden die Befehle, Sichten und Funktionen erklärt, die Sie beim Arbeiten mit Rollen auf Serverebene verwenden können.</span><span class="sxs-lookup"><span data-stu-id="e09a5-163">The following table explains the commands, views, and functions that you can use to work with server-level roles.</span></span>  
  
|<span data-ttu-id="e09a5-164">Funktion</span><span class="sxs-lookup"><span data-stu-id="e09a5-164">Feature</span></span>|<span data-ttu-id="e09a5-165">type</span><span class="sxs-lookup"><span data-stu-id="e09a5-165">Type</span></span>|<span data-ttu-id="e09a5-166">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="e09a5-166">Description</span></span>|  
|-------------|----------|-----------------|  
|[<span data-ttu-id="e09a5-167">sp_helpsrvrole &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e09a5-167">sp_helpsrvrole &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-helpsrvrole-transact-sql)|<span data-ttu-id="e09a5-168">Metadaten</span><span class="sxs-lookup"><span data-stu-id="e09a5-168">Metadata</span></span>|<span data-ttu-id="e09a5-169">Gibt eine Liste von Rollen auf Serverebene zurück.</span><span class="sxs-lookup"><span data-stu-id="e09a5-169">Returns a list of server-level roles.</span></span>|  
|[<span data-ttu-id="e09a5-170">sp_helpsrvrolemember &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e09a5-170">sp_helpsrvrolemember &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-helpsrvrolemember-transact-sql)|<span data-ttu-id="e09a5-171">Metadaten</span><span class="sxs-lookup"><span data-stu-id="e09a5-171">Metadata</span></span>|<span data-ttu-id="e09a5-172">Gibt Informationen zu Mitgliedern einer Rolle auf Serverebene zurück.</span><span class="sxs-lookup"><span data-stu-id="e09a5-172">Returns information about the members of a server-level role.</span></span>|  
|[<span data-ttu-id="e09a5-173">sp_srvrolepermission &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e09a5-173">sp_srvrolepermission &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-srvrolepermission-transact-sql)|<span data-ttu-id="e09a5-174">Metadaten</span><span class="sxs-lookup"><span data-stu-id="e09a5-174">Metadata</span></span>|<span data-ttu-id="e09a5-175">Zeigt die Berechtigungen einer Rolle auf Serverebene an.</span><span class="sxs-lookup"><span data-stu-id="e09a5-175">Displays the permissions of a server-level role.</span></span>|  
|[<span data-ttu-id="e09a5-176">IS_SRVROLEMEMBER &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e09a5-176">IS_SRVROLEMEMBER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/is-srvrolemember-transact-sql)|<span data-ttu-id="e09a5-177">Metadaten</span><span class="sxs-lookup"><span data-stu-id="e09a5-177">Metadata</span></span>|<span data-ttu-id="e09a5-178">Gibt an, ob eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Anmeldung Mitglied der angegebenen Rolle auf Serverebene ist.</span><span class="sxs-lookup"><span data-stu-id="e09a5-178">Indicates whether a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login is a member of the specified server-level role.</span></span>|  
|[<span data-ttu-id="e09a5-179">sys.server_role_members &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e09a5-179">sys.server_role_members &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-role-members-transact-sql)|<span data-ttu-id="e09a5-180">Metadaten</span><span class="sxs-lookup"><span data-stu-id="e09a5-180">Metadata</span></span>|<span data-ttu-id="e09a5-181">Gibt eine Zeile für jedes Mitglied jeder Rolle auf Serverebene zurück.</span><span class="sxs-lookup"><span data-stu-id="e09a5-181">Returns one row for each member of each server-level role.</span></span>|  
|[<span data-ttu-id="e09a5-182">sp_addsrvrolemember &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e09a5-182">sp_addsrvrolemember &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql)|<span data-ttu-id="e09a5-183">Get-Help</span><span class="sxs-lookup"><span data-stu-id="e09a5-183">Command</span></span>|<span data-ttu-id="e09a5-184">Fügt einen Benutzernamen als Mitglied einer Rolle auf Serverebene hinzu.</span><span class="sxs-lookup"><span data-stu-id="e09a5-184">Adds a login as a member of a server-level role.</span></span> <span data-ttu-id="e09a5-185">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="e09a5-185">Deprecated.</span></span> <span data-ttu-id="e09a5-186">Verwenden Sie stattdessen [ALTER SERVER ROLE](/sql/t-sql/statements/alter-server-role-transact-sql) .</span><span class="sxs-lookup"><span data-stu-id="e09a5-186">Use [ALTER SERVER ROLE](/sql/t-sql/statements/alter-server-role-transact-sql) instead.</span></span>|  
|[<span data-ttu-id="e09a5-187">sp_dropsrvrolemember &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e09a5-187">sp_dropsrvrolemember &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dropsrvrolemember-transact-sql)|<span data-ttu-id="e09a5-188">Get-Help</span><span class="sxs-lookup"><span data-stu-id="e09a5-188">Command</span></span>|<span data-ttu-id="e09a5-189">Entfernt einen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Anmeldenamen oder einen Windows-Benutzer bzw. eine -Gruppe aus einer Rolle auf Serverebene.</span><span class="sxs-lookup"><span data-stu-id="e09a5-189">Removes a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login or a Windows user or group from a server-level role.</span></span> <span data-ttu-id="e09a5-190">Veraltet.</span><span class="sxs-lookup"><span data-stu-id="e09a5-190">Deprecated.</span></span> <span data-ttu-id="e09a5-191">Verwenden Sie stattdessen [ALTER SERVER ROLE](/sql/t-sql/statements/alter-server-role-transact-sql) .</span><span class="sxs-lookup"><span data-stu-id="e09a5-191">Use [ALTER SERVER ROLE](/sql/t-sql/statements/alter-server-role-transact-sql) instead.</span></span>|  
|[<span data-ttu-id="e09a5-192">CREATE SERVER ROLE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e09a5-192">CREATE SERVER ROLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-server-role-transact-sql)|<span data-ttu-id="e09a5-193">Get-Help</span><span class="sxs-lookup"><span data-stu-id="e09a5-193">Command</span></span>|<span data-ttu-id="e09a5-194">Erstellt eine benutzerdefinierte Serverrolle.</span><span class="sxs-lookup"><span data-stu-id="e09a5-194">Creates a user-defined server role.</span></span>|  
|[<span data-ttu-id="e09a5-195">ALTER SERVER ROLE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e09a5-195">ALTER SERVER ROLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-server-role-transact-sql)|<span data-ttu-id="e09a5-196">Get-Help</span><span class="sxs-lookup"><span data-stu-id="e09a5-196">Command</span></span>|<span data-ttu-id="e09a5-197">Ändert die Mitgliedschaft einer Serverrolle oder ändert Namen einer benutzerdefinierten Serverrolle.</span><span class="sxs-lookup"><span data-stu-id="e09a5-197">Changes the membership of a server role or changes name of a user-defined server role.</span></span>|  
|[<span data-ttu-id="e09a5-198">DROP SERVER ROLE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e09a5-198">DROP SERVER ROLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-server-role-transact-sql)|<span data-ttu-id="e09a5-199">Get-Help</span><span class="sxs-lookup"><span data-stu-id="e09a5-199">Command</span></span>|<span data-ttu-id="e09a5-200">Entfernt eine benutzerdefinierte Serverrolle.</span><span class="sxs-lookup"><span data-stu-id="e09a5-200">Removes a user-defined server role.</span></span>|  
|[<span data-ttu-id="e09a5-201">IS_SRVROLEMEMBER &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e09a5-201">IS_SRVROLEMEMBER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/is-srvrolemember-transact-sql)|<span data-ttu-id="e09a5-202">Funktion</span><span class="sxs-lookup"><span data-stu-id="e09a5-202">Function</span></span>|<span data-ttu-id="e09a5-203">Bestimmt die Mitgliedschaft einer Serverrolle.</span><span class="sxs-lookup"><span data-stu-id="e09a5-203">Determines membership of server role.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e09a5-204">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e09a5-204">See Also</span></span>  
 <span data-ttu-id="e09a5-205">[Rollen auf Datenbankebene](../authentication-access/database-level-roles.md) </span><span class="sxs-lookup"><span data-stu-id="e09a5-205">[Database-Level Roles](../authentication-access/database-level-roles.md) </span></span>  
 <span data-ttu-id="e09a5-206">[Sicherheitskatalogsichten &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/security-catalog-views-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e09a5-206">[Security Catalog Views &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/security-catalog-views-transact-sql) </span></span>  
 <span data-ttu-id="e09a5-207">[Sicherheitsfunktionen &#40;Transact-SQL&#41;](/sql/t-sql/functions/security-functions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e09a5-207">[Security Functions &#40;Transact-SQL&#41;](/sql/t-sql/functions/security-functions-transact-sql) </span></span>  
 <span data-ttu-id="e09a5-208">[Sichern von SQL Server](../securing-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e09a5-208">[Securing SQL Server](../securing-sql-server.md) </span></span>  
 <span data-ttu-id="e09a5-209">[GRANT (Berechtigungen für Serverprinzipal) &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-server-principal-permissions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e09a5-209">[GRANT Server Principal Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-server-principal-permissions-transact-sql) </span></span>  
 <span data-ttu-id="e09a5-210">[REVOKE (Berechtigungen für Serverprinzipal) &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-server-principal-permissions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e09a5-210">[REVOKE Server Principal Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-server-principal-permissions-transact-sql) </span></span>  
 <span data-ttu-id="e09a5-211">[DENY (Berechtigungen für Serverprinzipal) &#40;Transact-SQL&#41;](/sql/t-sql/statements/deny-server-principal-permissions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e09a5-211">[DENY Server Principal Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/deny-server-principal-permissions-transact-sql) </span></span>  
 [<span data-ttu-id="e09a5-212">Erstellen einer Serverrolle</span><span class="sxs-lookup"><span data-stu-id="e09a5-212">Create a Server Role</span></span>](../authentication-access/create-a-server-role.md)  
  
  