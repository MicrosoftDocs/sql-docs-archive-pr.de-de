---
title: Integration Services-Rollen (SSIS-Dienst) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- security [Integration Services], roles
- db_ssisoperator role
- db_ssisadmin role
- fixed database roles [Integration Services]
- packages [Integration Services], security
- roles [Integration Services]
- db_ssisltduser role
ms.assetid: 9702e90c-fada-4978-a473-1b1423017d80
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5bc65a7a3ff30deb429ceeb8458ac477432a758c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615421"
---
# <a name="integration-services-roles-ssis-service"></a><span data-ttu-id="9d4d9-102">Integration Services-Rollen (SSIS-Dienst)</span><span class="sxs-lookup"><span data-stu-id="9d4d9-102">Integration Services Roles (SSIS Service)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="9d4d9-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]umfasst die drei Fixed-Rollen auf Datenbankebene, `db_ssisadmin` **db_ssisltduser**und **db_ssisoperator**zum Steuern des Zugriffs auf Pakete.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes the three fixed database-level roles, `db_ssisadmin`, **db_ssisltduser**, and **db_ssisoperator**, for controlling access to packages.</span></span> <span data-ttu-id="9d4d9-104">Rollen können nur für Pakete implementiert werden, die in der- `msdb` Datenbank in gespeichert werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9d4d9-104">Roles can be implemented only on packages that are saved to the `msdb` database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9d4d9-105">Rollen weisen Sie mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]zu.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-105">You assign roles to a package using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="9d4d9-106">Die Rollenzuweisungen werden in der `msdb` Datenbank gespeichert.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-106">The role assignments are saved to the `msdb` database.</span></span>  
  
## <a name="read-and-write-actions"></a><span data-ttu-id="9d4d9-107">Lese- und Schreibaktionen</span><span class="sxs-lookup"><span data-stu-id="9d4d9-107">Read and Write Actions</span></span>  
 <span data-ttu-id="9d4d9-108">In der folgenden Tabelle werden die Lese- und Schreibaktionen von Windows und der festen Rollen auf Datenbankebene in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]beschrieben.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-108">The following table describes the read and write actions of Windows and fixed database-level roles in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span>  
  
|<span data-ttu-id="9d4d9-109">Role</span><span class="sxs-lookup"><span data-stu-id="9d4d9-109">Role</span></span>|<span data-ttu-id="9d4d9-110">Leseaktion</span><span class="sxs-lookup"><span data-stu-id="9d4d9-110">Read action</span></span>|<span data-ttu-id="9d4d9-111">Schreibaktion</span><span class="sxs-lookup"><span data-stu-id="9d4d9-111">Write action</span></span>|  
|----------|-----------------|------------------|  
|`db_ssisadmin`<br /><br /> <span data-ttu-id="9d4d9-112">oder</span><span class="sxs-lookup"><span data-stu-id="9d4d9-112">or</span></span><br /><br /> `sysadmin`|<span data-ttu-id="9d4d9-113">Eigene Pakete aufzählen.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-113">Enumerate own packages.</span></span><br /><br /> <span data-ttu-id="9d4d9-114">Alle Pakete aufzählen.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-114">Enumerate all packages.</span></span><br /><br /> <span data-ttu-id="9d4d9-115">Eigene Pakete anzeigen.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-115">View own packages.</span></span><br /><br /> <span data-ttu-id="9d4d9-116">Alle Pakete anzeigen.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-116">View all packages.</span></span><br /><br /> <span data-ttu-id="9d4d9-117">Eigene Pakete ausführen.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-117">Execute own packages.</span></span><br /><br /> <span data-ttu-id="9d4d9-118">Alle Pakete ausführen.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-118">Execute all packages.</span></span><br /><br /> <span data-ttu-id="9d4d9-119">Eigene Pakete exportieren.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-119">Export own packages.</span></span><br /><br /> <span data-ttu-id="9d4d9-120">Alle Pakete exportieren.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-120">Export all packages.</span></span><br /><br /> <span data-ttu-id="9d4d9-121">Alle Pakete in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent ausführen.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-121">Execute all packages in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>|<span data-ttu-id="9d4d9-122">Pakete importieren.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-122">Import packages.</span></span><br /><br /> <span data-ttu-id="9d4d9-123">Eigene Pakete löschen.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-123">Delete own packages.</span></span><br /><br /> <span data-ttu-id="9d4d9-124">Alle Pakete löschen.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-124">Delete all packages.</span></span><br /><br /> <span data-ttu-id="9d4d9-125">Eigene Paketrollen ändern.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-125">Change own package roles.</span></span><br /><br /> <span data-ttu-id="9d4d9-126">Alle Paketrollen ändern.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-126">Change all package roles.</span></span><br /><br /> <br /><br /> <span data-ttu-id="9d4d9-127">Wichtige Mitglieder der db_ssisadmin Rolle und der dc_admin-Rolle können Ihre Berechtigungen möglicherweise auf sysadmin erhöhen. \*\* \* \* \* \* \*\*</span><span class="sxs-lookup"><span data-stu-id="9d4d9-127">**\*\* Important \*\*** Members of the db_ssisadmin role and the dc_admin role may be able to elevate their privileges to sysadmin.</span></span> <span data-ttu-id="9d4d9-128">Diese Ausweitung von Berechtigungen ist möglich, da diese Rollen [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Pakete ändern können und [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Pakete von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe des sysadmin-Sicherheitskontexts des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents ausgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-128">This elevation of privilege can occur because these roles can modify [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages can be executed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the sysadmin security context of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="9d4d9-129">Konfigurieren Sie als Schutz vor dieser Ausweitung von Berechtigungen beim Ausführen von Wartungsplänen, Datensammlungssätzen und anderen [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paketen Aufträge des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents, die Pakete ausführen, für die Verwendung eines Proxykontos mit einschränkten Berechtigungen, oder fügen Sie der db_ssisadmin-Rolle und der dc_admin-Rolle nur sysadmin-Mitglieder hinzu.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-129">To guard against this elevation of privilege when running maintenance plans, data collection sets, and other [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs that run packages to use a proxy account with limited privileges or only add sysadmin members to the db_ssisadmin and dc_admin roles.</span></span>|  
|<span data-ttu-id="9d4d9-130">**db_ssisltduser**</span><span class="sxs-lookup"><span data-stu-id="9d4d9-130">**db_ssisltduser**</span></span>|<span data-ttu-id="9d4d9-131">Eigene Pakete aufzählen.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-131">Enumerate own packages.</span></span><br /><br /> <span data-ttu-id="9d4d9-132">Alle Pakete aufzählen.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-132">Enumerate all packages.</span></span><br /><br /> <span data-ttu-id="9d4d9-133">Eigene Pakete anzeigen.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-133">View own packages.</span></span><br /><br /> <span data-ttu-id="9d4d9-134">Eigene Pakete ausführen.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-134">Execute own packages.</span></span><br /><br /> <span data-ttu-id="9d4d9-135">Eigene Pakete exportieren.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-135">Export own packages.</span></span>|<span data-ttu-id="9d4d9-136">Pakete importieren.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-136">Import packages.</span></span><br /><br /> <span data-ttu-id="9d4d9-137">Eigene Pakete löschen.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-137">Delete own packages.</span></span><br /><br /> <span data-ttu-id="9d4d9-138">Eigene Paketrollen ändern.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-138">Change own package roles.</span></span>|  
|<span data-ttu-id="9d4d9-139">**db_ssisoperator**</span><span class="sxs-lookup"><span data-stu-id="9d4d9-139">**db_ssisoperator**</span></span>|<span data-ttu-id="9d4d9-140">Alle Pakete aufzählen.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-140">Enumerate all packages.</span></span><br /><br /> <span data-ttu-id="9d4d9-141">Alle Pakete anzeigen.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-141">View all packages.</span></span><br /><br /> <span data-ttu-id="9d4d9-142">Alle Pakete ausführen.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-142">Execute all packages.</span></span><br /><br /> <span data-ttu-id="9d4d9-143">Alle Pakete exportieren.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-143">Export all packages.</span></span><br /><br /> <span data-ttu-id="9d4d9-144">Alle Pakete in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent ausführen.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-144">Execute all packages in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>|<span data-ttu-id="9d4d9-145">Keine</span><span class="sxs-lookup"><span data-stu-id="9d4d9-145">None</span></span>|  
|<span data-ttu-id="9d4d9-146">**Windows-Administratoren**</span><span class="sxs-lookup"><span data-stu-id="9d4d9-146">**Windows administrators**</span></span>|<span data-ttu-id="9d4d9-147">Ausführungsdetails zu allen ausgeführten Paketen anzeigen.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-147">View execution details of all running packages.</span></span>|<span data-ttu-id="9d4d9-148">Alle derzeit ausgeführten Pakete anhalten.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-148">Stop all currently running packages.</span></span>|  
  
## <a name="sysssispackages-table"></a><span data-ttu-id="9d4d9-149">Sysssispackages-Tabelle</span><span class="sxs-lookup"><span data-stu-id="9d4d9-149">Sysssispackages Table</span></span>  
 <span data-ttu-id="9d4d9-150">Die **sysssispackages** -Tabelle in `msdb` enthält die Pakete, die in gespeichert werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9d4d9-150">The **sysssispackages** table in `msdb` contains the packages that are saved to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9d4d9-151">Weitere Informationen finden Sie unter [sysssispackages &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/sysssispackages-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="9d4d9-151">For more information, see [sysssispackages &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/sysssispackages-transact-sql).</span></span>  
  
 <span data-ttu-id="9d4d9-152">Die **sysssispackages** -Tabelle enthält Spalten, die Informationen über die Rollen enthalten, die Paketen zugewiesen sind.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-152">The **sysssispackages** table includes columns that contain information about the roles that are assigned to packages.</span></span>  
  
-   <span data-ttu-id="9d4d9-153">In der Spalte **readerrole** wird die Rolle angegeben, die über Lesezugriff auf das Paket verfügt.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-153">The **readerrole** column specifies the role that has read access to the package.</span></span>  
  
-   <span data-ttu-id="9d4d9-154">In der Spalte **writerrole** wird die Rolle angegeben, die über Schreibzugriff auf das Paket verfügt.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-154">The **writerrole** column specifies the role that has write access to the package.</span></span>  
  
-   <span data-ttu-id="9d4d9-155">Die **ownersid** -Spalte enthält den eindeutigen Sicherheitsbezeichner des Benutzers, der das Paket erstellte.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-155">The **ownersid** column contains the unique security identifier of the user who created the package.</span></span> <span data-ttu-id="9d4d9-156">In dieser Spalte wird der Besitzer des Pakets definiert.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-156">This column defines the owner of the package.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="9d4d9-157">Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="9d4d9-157">Permissions</span></span>  
 <span data-ttu-id="9d4d9-158">Standardmäßig gelten die Berechtigungen von `db_ssisadmin` und **db_ssisoperator** fixierte Rollen auf Datenbankebene und die eindeutige Sicherheits-ID des Benutzers, der das Paket erstellt hat, für die Rolle "Leser" für Pakete, und die Berechtigungen der `db_ssisadmin` Rolle und die eindeutige Sicherheits-ID des Benutzers, der das Paket erstellt hat, gelten für die Schreib Rolle.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-158">By default, the permissions of the `db_ssisadmin` and **db_ssisoperator** fixed database-level roles and the unique security identifier of the user who created the package apply to the reader role for packages, and the permissions of the `db_ssisadmin` role and the unique security identifier of the user who created the package apply to the writer role.</span></span> <span data-ttu-id="9d4d9-159">Ein Benutzer muss Mitglied der `db_ssisadmin` Rolle, **db_ssisltduser**oder **db_ssisoperator** sein, um Lesezugriff auf das Paket zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-159">A user must be a member of the `db_ssisadmin`, **db_ssisltduser**, or **db_ssisoperator** role to have read access to the package.</span></span> <span data-ttu-id="9d4d9-160">Ein Benutzer muss Mitglied der `db_ssisadmin` Rolle sein, um über Schreibzugriff zu verfügen.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-160">A user must be a member of the `db_ssisadmin` role to have write access.</span></span>  
  
## <a name="access-to-packages"></a><span data-ttu-id="9d4d9-161">Zugriff auf Pakete</span><span class="sxs-lookup"><span data-stu-id="9d4d9-161">Access to Packages</span></span>  
 <span data-ttu-id="9d4d9-162">Die festen Rollen auf Datenbankebene arbeiten mit benutzerdefinierten Rollen zusammen.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-162">The fixed database-level roles work in conjunction with user-defined roles.</span></span> <span data-ttu-id="9d4d9-163">Die benutzerdefinierten Rollen sind die Rollen, die Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] erstellen und dann zum Zuweisen von Berechtigungen zu Paketen verwenden.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-163">The user-defined roles are the roles that you create in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and then use to assign permissions to packages.</span></span> <span data-ttu-id="9d4d9-164">Um auf ein Paket zuzugreifen, muss ein Benutzer Mitglied der benutzerdefinierten Rolle und der entsprechenden festen [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Datenbankrolle sein.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-164">To access a package, a user must be a member of the user-defined role and the pertinent [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] fixed database-level role.</span></span> <span data-ttu-id="9d4d9-165">Wenn Benutzer z. b. Mitglieder der benutzerdefinierten **Audit** users-Rolle sind, die einem Paket zugewiesen ist, müssen Sie auch Mitglieder von `db_ssisadmin` , **db_ssisltduser**oder **db_ssisoperator** Rolle sein, um Lesezugriff auf das Paket zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-165">For example, if users are members of the **AuditUsers** user-defined role that is assigned to a package, they must also be members of `db_ssisadmin`, **db_ssisltduser**, or **db_ssisoperator** role to have read access to the package.</span></span>  
  
 <span data-ttu-id="9d4d9-166">Wenn Sie Paketen keine benutzerdefinierten Rollen zuweisen, wird der Paketzugriff durch die festen Rollen auf Datenbankebene bestimmt.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-166">If you do not assign user-defined roles to packages, access to packages is determined by the fixed database-level roles.</span></span>  
  
 <span data-ttu-id="9d4d9-167">Wenn Sie benutzerdefinierte Rollen verwenden möchten, müssen Sie diese der-Datenbank hinzufügen, bevor Sie Sie `msdb` Paketen zuweisen können.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-167">If you want to use user-defined roles, you must add them to the `msdb` database before you can assign them to packages.</span></span> <span data-ttu-id="9d4d9-168">Neue Datenbankrollen können Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]erstellen.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-168">You can create new database roles in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="9d4d9-169">Die [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Rollen auf Datenbankebene gewähren den [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Systemtabellen in der msdb-Datenbank Rechte.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-169">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] database-level roles grant rights on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] system tables in the msdb database.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="9d4d9-170">(der MSSQLServer-Dienst) muss gestartet werden, bevor Sie eine Verbindung mit dem Datenbank-Engine herstellen und auf die Datenbank zugreifen können `msdb` .</span><span class="sxs-lookup"><span data-stu-id="9d4d9-170">(the MSSQLSERVER service) must be started before you can connect to the Database Engine and access the `msdb` database.</span></span>  
  
 <span data-ttu-id="9d4d9-171">Um Rollen Paketen zuzuweisen, müssen Sie die folgenden Tasks ausführen.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-171">To assign roles to packages, you need to complete the following tasks.</span></span>  
  
-   <span data-ttu-id="9d4d9-172">**Öffnen Sie den Objekt-Explorer und stellen Sie eine Verbindung mit Integration Services her.**</span><span class="sxs-lookup"><span data-stu-id="9d4d9-172">**Open Object Explorer and Connect to Integration Services**</span></span>  
  
     <span data-ttu-id="9d4d9-173">Bevor Sie Paketen Rollen mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]zuweisen können, müssen Sie den Objekt-Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] öffnen und eine Verbindung mit [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]herstellen.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-173">Before you can assign roles to packages by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you must open Object Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and connect to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="9d4d9-174">Der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Dienst muss gestartet werden, bevor Sie eine Verbindung mit [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]herstellen können.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-174">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service must be started before you can connect to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="9d4d9-175">**Paketen Lese- und Schreibrollen zuweisen**</span><span class="sxs-lookup"><span data-stu-id="9d4d9-175">**Assign Reader and Writer Roles to Packages**</span></span>  
  
     <span data-ttu-id="9d4d9-176">Sie können jedem Paket eine Lese- und eine Schreibrolle zuweisen.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-176">You can assign a reader and a writer role to each package.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="9d4d9-177">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="9d4d9-177">Related Tasks</span></span>  
  
-   [<span data-ttu-id="9d4d9-178">Zuweisen einer Lese- und Schreibrolle zu einem Paket</span><span class="sxs-lookup"><span data-stu-id="9d4d9-178">Assign a Reader and Writer Role to a Package</span></span>](../assign-a-reader-and-writer-role-to-a-package.md)  
  
-   [<span data-ttu-id="9d4d9-179">Erstellen einer benutzerdefinierten Rolle</span><span class="sxs-lookup"><span data-stu-id="9d4d9-179">Create a User-Defined Role</span></span>](../create-a-user-defined-role.md)  
  
-   [<span data-ttu-id="9d4d9-180">Herstellen einer Verbindung mit Integration Services</span><span class="sxs-lookup"><span data-stu-id="9d4d9-180">Connect to Integration Services</span></span>](../connect-to-integration-services.md)  
  
  