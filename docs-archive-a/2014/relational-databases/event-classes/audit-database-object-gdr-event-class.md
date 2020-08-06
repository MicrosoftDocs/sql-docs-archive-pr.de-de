---
title: Audit Database Object GDR (Ereignisklasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Audit Database Object GDR event class
ms.assetid: 2289aab5-e048-4288-bcae-aaf768ca014a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 804c1c74356e52822cc369e9b4a179433d6c6f92
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701168"
---
# <a name="audit-database-object-gdr-event-class"></a><span data-ttu-id="07e56-102">Audit Database Object GDR (Ereignisklasse)</span><span class="sxs-lookup"><span data-stu-id="07e56-102">Audit Database Object GDR Event Class</span></span>
  <span data-ttu-id="07e56-103">Die **Audit Database Object GDR** -Ereignisklasse tritt auf, wenn für Datenbankobjekte, z. B. Assemblys und Schemas, eine GRANT-, REVOKE- oder DENY-Anweisung ausgegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="07e56-103">The **Audit Database Object GDR** event class occurs when a GRANT, REVOKE, or DENY has been issued for database objects, such as assemblies and schemas.</span></span>  
  
## <a name="audit-database-object-gdr-event-class-data-columns"></a><span data-ttu-id="07e56-104">Audit Database Object GDR-Ereignisklasse (Datenspalten)</span><span class="sxs-lookup"><span data-stu-id="07e56-104">Audit Database Object GDR Event Class Data Columns</span></span>  
  
|<span data-ttu-id="07e56-105">Datenspaltenname</span><span class="sxs-lookup"><span data-stu-id="07e56-105">Data column name</span></span>|<span data-ttu-id="07e56-106">Datentyp</span><span class="sxs-lookup"><span data-stu-id="07e56-106">Data type</span></span>|<span data-ttu-id="07e56-107">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="07e56-107">Description</span></span>|<span data-ttu-id="07e56-108">Column ID</span><span class="sxs-lookup"><span data-stu-id="07e56-108">Column ID</span></span>|<span data-ttu-id="07e56-109">Filterbar</span><span class="sxs-lookup"><span data-stu-id="07e56-109">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="07e56-110">**ApplicationName**</span><span class="sxs-lookup"><span data-stu-id="07e56-110">**ApplicationName**</span></span>|<span data-ttu-id="07e56-111">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="07e56-111">**nvarchar**</span></span>|<span data-ttu-id="07e56-112">Dies ist der Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hergestellt hat.</span><span class="sxs-lookup"><span data-stu-id="07e56-112">Name of the client application that created the connection to an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="07e56-113">Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.</span><span class="sxs-lookup"><span data-stu-id="07e56-113">This column is populated with the values passed by the application rather than the displayed name of the program.</span></span>|<span data-ttu-id="07e56-114">10</span><span class="sxs-lookup"><span data-stu-id="07e56-114">10</span></span>|<span data-ttu-id="07e56-115">Ja</span><span class="sxs-lookup"><span data-stu-id="07e56-115">Yes</span></span>|  
|<span data-ttu-id="07e56-116">**ClientProcessID**</span><span class="sxs-lookup"><span data-stu-id="07e56-116">**ClientProcessID**</span></span>|<span data-ttu-id="07e56-117">**int**</span><span class="sxs-lookup"><span data-stu-id="07e56-117">**int**</span></span>|<span data-ttu-id="07e56-118">Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="07e56-118">ID assigned by the host computer to the process where the client application is running.</span></span> <span data-ttu-id="07e56-119">Diese Datenspalte wird aufgefüllt, wenn die Clientprozess-ID durch den Client bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="07e56-119">This data column is populated if the client process ID is provided by the client.</span></span>|<span data-ttu-id="07e56-120">9</span><span class="sxs-lookup"><span data-stu-id="07e56-120">9</span></span>|<span data-ttu-id="07e56-121">Ja</span><span class="sxs-lookup"><span data-stu-id="07e56-121">Yes</span></span>|  
|<span data-ttu-id="07e56-122">**DatabaseID**</span><span class="sxs-lookup"><span data-stu-id="07e56-122">**DatabaseID**</span></span>|<span data-ttu-id="07e56-123">**int**</span><span class="sxs-lookup"><span data-stu-id="07e56-123">**int**</span></span>|<span data-ttu-id="07e56-124">Die ID der Datenbank, die durch die USE *database* -Anweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine bestimmte Instanz keine USE *database* -Anweisung ausgegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="07e56-124">ID of the database specified by the USE *database* statement or the default database if no USE *database* statement has been issued for a given instance.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="07e56-125">zeigt den Namen der Datenbank an, wenn die **ServerName** -Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="07e56-125">displays the name of the database if the **ServerName** data column is captured in the trace and the server is available.</span></span> <span data-ttu-id="07e56-126">Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="07e56-126">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="07e56-127">3</span><span class="sxs-lookup"><span data-stu-id="07e56-127">3</span></span>|<span data-ttu-id="07e56-128">Ja</span><span class="sxs-lookup"><span data-stu-id="07e56-128">Yes</span></span>|  
|<span data-ttu-id="07e56-129">**DatabaseName**</span><span class="sxs-lookup"><span data-stu-id="07e56-129">**DatabaseName**</span></span>|<span data-ttu-id="07e56-130">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="07e56-130">**nvarchar**</span></span>|<span data-ttu-id="07e56-131">Name der Datenbank, in der die Benutzeranweisung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="07e56-131">Name of the database in which the user statement is running.</span></span>|<span data-ttu-id="07e56-132">35</span><span class="sxs-lookup"><span data-stu-id="07e56-132">35</span></span>|<span data-ttu-id="07e56-133">Ja</span><span class="sxs-lookup"><span data-stu-id="07e56-133">Yes</span></span>|  
|<span data-ttu-id="07e56-134">**DBUserName**</span><span class="sxs-lookup"><span data-stu-id="07e56-134">**DBUserName**</span></span>|<span data-ttu-id="07e56-135">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="07e56-135">**nvarchar**</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="07e56-136">-Benutzername des Clients.</span><span class="sxs-lookup"><span data-stu-id="07e56-136">user name of the client.</span></span>|<span data-ttu-id="07e56-137">40</span><span class="sxs-lookup"><span data-stu-id="07e56-137">40</span></span>|<span data-ttu-id="07e56-138">Ja</span><span class="sxs-lookup"><span data-stu-id="07e56-138">Yes</span></span>|  
|<span data-ttu-id="07e56-139">**EventClass**</span><span class="sxs-lookup"><span data-stu-id="07e56-139">**EventClass**</span></span>|<span data-ttu-id="07e56-140">**int**</span><span class="sxs-lookup"><span data-stu-id="07e56-140">**int**</span></span>|<span data-ttu-id="07e56-141">Ereignistyp = 172.</span><span class="sxs-lookup"><span data-stu-id="07e56-141">Type of event = 172.</span></span>|<span data-ttu-id="07e56-142">27</span><span class="sxs-lookup"><span data-stu-id="07e56-142">27</span></span>|<span data-ttu-id="07e56-143">Nein</span><span class="sxs-lookup"><span data-stu-id="07e56-143">No</span></span>|  
|<span data-ttu-id="07e56-144">**EventSequence**</span><span class="sxs-lookup"><span data-stu-id="07e56-144">**EventSequence**</span></span>|<span data-ttu-id="07e56-145">**int**</span><span class="sxs-lookup"><span data-stu-id="07e56-145">**int**</span></span>|<span data-ttu-id="07e56-146">Sequenz eines bestimmten Ereignisses innerhalb der Anforderung.</span><span class="sxs-lookup"><span data-stu-id="07e56-146">Sequence of a given event within the request.</span></span>|<span data-ttu-id="07e56-147">51</span><span class="sxs-lookup"><span data-stu-id="07e56-147">51</span></span>|<span data-ttu-id="07e56-148">Nein</span><span class="sxs-lookup"><span data-stu-id="07e56-148">No</span></span>|  
|<span data-ttu-id="07e56-149">**EventSubClass**</span><span class="sxs-lookup"><span data-stu-id="07e56-149">**EventSubClass**</span></span>|<span data-ttu-id="07e56-150">**int**</span><span class="sxs-lookup"><span data-stu-id="07e56-150">**int**</span></span>|<span data-ttu-id="07e56-151">Der Typ der Ereignisunterklasse.</span><span class="sxs-lookup"><span data-stu-id="07e56-151">Type of event subclass.</span></span><br /><br /> <span data-ttu-id="07e56-152">1 = Erteilen</span><span class="sxs-lookup"><span data-stu-id="07e56-152">1=Grant</span></span><br /><br /> <span data-ttu-id="07e56-153">2 = Aufheben</span><span class="sxs-lookup"><span data-stu-id="07e56-153">2=Revoke</span></span><br /><br /> <span data-ttu-id="07e56-154">3 = Verweigern</span><span class="sxs-lookup"><span data-stu-id="07e56-154">3=Deny</span></span>|<span data-ttu-id="07e56-155">21</span><span class="sxs-lookup"><span data-stu-id="07e56-155">21</span></span>|<span data-ttu-id="07e56-156">Ja</span><span class="sxs-lookup"><span data-stu-id="07e56-156">Yes</span></span>|  
|<span data-ttu-id="07e56-157">**HostName**</span><span class="sxs-lookup"><span data-stu-id="07e56-157">**HostName**</span></span>|<span data-ttu-id="07e56-158">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="07e56-158">**nvarchar**</span></span>|<span data-ttu-id="07e56-159">Der Name des Computers, auf dem der Client ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="07e56-159">Name of the computer on which the client is running.</span></span> <span data-ttu-id="07e56-160">Diese Datenspalte wird aufgefüllt, wenn der Hostname vom Client bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="07e56-160">This data column is populated if the client provides the host name.</span></span> <span data-ttu-id="07e56-161">Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.</span><span class="sxs-lookup"><span data-stu-id="07e56-161">To determine the host name, use the HOST_NAME function.</span></span>|<span data-ttu-id="07e56-162">8</span><span class="sxs-lookup"><span data-stu-id="07e56-162">8</span></span>|<span data-ttu-id="07e56-163">Ja</span><span class="sxs-lookup"><span data-stu-id="07e56-163">Yes</span></span>|  
|<span data-ttu-id="07e56-164">**IsSystem**</span><span class="sxs-lookup"><span data-stu-id="07e56-164">**IsSystem**</span></span>|<span data-ttu-id="07e56-165">**int**</span><span class="sxs-lookup"><span data-stu-id="07e56-165">**int**</span></span>|<span data-ttu-id="07e56-166">Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="07e56-166">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="07e56-167">1 = System, 0 = Benutzer.</span><span class="sxs-lookup"><span data-stu-id="07e56-167">1 = system, 0 = user.</span></span>|<span data-ttu-id="07e56-168">60</span><span class="sxs-lookup"><span data-stu-id="07e56-168">60</span></span>|<span data-ttu-id="07e56-169">Ja</span><span class="sxs-lookup"><span data-stu-id="07e56-169">Yes</span></span>|  
|<span data-ttu-id="07e56-170">**LoginName**</span><span class="sxs-lookup"><span data-stu-id="07e56-170">**LoginName**</span></span>|<span data-ttu-id="07e56-171">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="07e56-171">**nvarchar**</span></span>|<span data-ttu-id="07e56-172">Anmeldename des Benutzers (Anmeldung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheit oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anmeldeinformationen im Format DOMAIN\username).</span><span class="sxs-lookup"><span data-stu-id="07e56-172">Name of the login of the user (either the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security login or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows login credentials in the form of DOMAIN\username).</span></span>|<span data-ttu-id="07e56-173">11</span><span class="sxs-lookup"><span data-stu-id="07e56-173">11</span></span>|<span data-ttu-id="07e56-174">Ja</span><span class="sxs-lookup"><span data-stu-id="07e56-174">Yes</span></span>|  
|<span data-ttu-id="07e56-175">**LoginSid**</span><span class="sxs-lookup"><span data-stu-id="07e56-175">**LoginSid**</span></span>|<span data-ttu-id="07e56-176">**image**</span><span class="sxs-lookup"><span data-stu-id="07e56-176">**image**</span></span>|<span data-ttu-id="07e56-177">Sicherheits-ID (SID) des angemeldeten Benutzers.</span><span class="sxs-lookup"><span data-stu-id="07e56-177">Security identification number (SID) of the logged-in user.</span></span> <span data-ttu-id="07e56-178">Diese Informationen finden Sie in der **sys.server_principals** -Katalogsicht.</span><span class="sxs-lookup"><span data-stu-id="07e56-178">You can find this information in the **sys.server_principals** catalog view.</span></span> <span data-ttu-id="07e56-179">Die SID ist für jede Anmeldung beim Server eindeutig.</span><span class="sxs-lookup"><span data-stu-id="07e56-179">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="07e56-180">41</span><span class="sxs-lookup"><span data-stu-id="07e56-180">41</span></span>|<span data-ttu-id="07e56-181">Ja</span><span class="sxs-lookup"><span data-stu-id="07e56-181">Yes</span></span>|  
|<span data-ttu-id="07e56-182">**NTDomainName**</span><span class="sxs-lookup"><span data-stu-id="07e56-182">**NTDomainName**</span></span>|<span data-ttu-id="07e56-183">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="07e56-183">**nvarchar**</span></span>|<span data-ttu-id="07e56-184">Windows-Domäne, zu der der Benutzer gehört.</span><span class="sxs-lookup"><span data-stu-id="07e56-184">Windows domain to which the user belongs.</span></span>|<span data-ttu-id="07e56-185">7</span><span class="sxs-lookup"><span data-stu-id="07e56-185">7</span></span>|<span data-ttu-id="07e56-186">Ja</span><span class="sxs-lookup"><span data-stu-id="07e56-186">Yes</span></span>|  
|<span data-ttu-id="07e56-187">**NTUserName**</span><span class="sxs-lookup"><span data-stu-id="07e56-187">**NTUserName**</span></span>|<span data-ttu-id="07e56-188">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="07e56-188">**nvarchar**</span></span>|<span data-ttu-id="07e56-189">Windows-Benutzername.</span><span class="sxs-lookup"><span data-stu-id="07e56-189">Windows user name.</span></span>|<span data-ttu-id="07e56-190">6</span><span class="sxs-lookup"><span data-stu-id="07e56-190">6</span></span>|<span data-ttu-id="07e56-191">Ja</span><span class="sxs-lookup"><span data-stu-id="07e56-191">Yes</span></span>|  
|<span data-ttu-id="07e56-192">**ObjectName**</span><span class="sxs-lookup"><span data-stu-id="07e56-192">**ObjectName**</span></span>|<span data-ttu-id="07e56-193">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="07e56-193">**nvarchar**</span></span>|<span data-ttu-id="07e56-194">Name des Objekts, auf das verwiesen wird</span><span class="sxs-lookup"><span data-stu-id="07e56-194">Name of the object being referenced.</span></span>|<span data-ttu-id="07e56-195">34</span><span class="sxs-lookup"><span data-stu-id="07e56-195">34</span></span>|<span data-ttu-id="07e56-196">Ja</span><span class="sxs-lookup"><span data-stu-id="07e56-196">Yes</span></span>|  
|<span data-ttu-id="07e56-197">**ObjectType**</span><span class="sxs-lookup"><span data-stu-id="07e56-197">**ObjectType**</span></span>|<span data-ttu-id="07e56-198">**int**</span><span class="sxs-lookup"><span data-stu-id="07e56-198">**int**</span></span>|<span data-ttu-id="07e56-199">Der Wert, der den Typ des am Ereignis beteiligten Objekts darstellt.</span><span class="sxs-lookup"><span data-stu-id="07e56-199">Value representing the type of the object involved in the event.</span></span> <span data-ttu-id="07e56-200">Dieser Wert entspricht der type-Spalte in der **sys.objects** -Katalogsicht.</span><span class="sxs-lookup"><span data-stu-id="07e56-200">This value corresponds to the type column in the **sys.objects** catalog view.</span></span> <span data-ttu-id="07e56-201">Weitere Werte finden Sie unter [ObjectType (Spalte für Ablaufverfolgungsereignisse)](objecttype-trace-event-column.md).</span><span class="sxs-lookup"><span data-stu-id="07e56-201">For values, see [ObjectType Trace Event Column](objecttype-trace-event-column.md).</span></span>|<span data-ttu-id="07e56-202">28</span><span class="sxs-lookup"><span data-stu-id="07e56-202">28</span></span>|<span data-ttu-id="07e56-203">Ja</span><span class="sxs-lookup"><span data-stu-id="07e56-203">Yes</span></span>|  
|<span data-ttu-id="07e56-204">**OwnerName**</span><span class="sxs-lookup"><span data-stu-id="07e56-204">**OwnerName**</span></span>|<span data-ttu-id="07e56-205">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="07e56-205">**nvarchar**</span></span>|<span data-ttu-id="07e56-206">Datenbank-Benutzername des Objektbesitzers.</span><span class="sxs-lookup"><span data-stu-id="07e56-206">Database user name of the object owner.</span></span>|<span data-ttu-id="07e56-207">37</span><span class="sxs-lookup"><span data-stu-id="07e56-207">37</span></span>|<span data-ttu-id="07e56-208">Ja</span><span class="sxs-lookup"><span data-stu-id="07e56-208">Yes</span></span>|  
|<span data-ttu-id="07e56-209">**Berechtigungen**</span><span class="sxs-lookup"><span data-stu-id="07e56-209">**Permissions**</span></span>|<span data-ttu-id="07e56-210">**bigint**</span><span class="sxs-lookup"><span data-stu-id="07e56-210">**bigint**</span></span>|<span data-ttu-id="07e56-211">Wert für ganze Zahl, der den Typ der überprüften Berechtigungen darstellt.</span><span class="sxs-lookup"><span data-stu-id="07e56-211">Integer value representing the type of permissions checked.</span></span><br /><br /> <span data-ttu-id="07e56-212">1 = SELECT ALL</span><span class="sxs-lookup"><span data-stu-id="07e56-212">1 = SELECT ALL</span></span><br /><br /> <span data-ttu-id="07e56-213">2 = UPDATE ALL</span><span class="sxs-lookup"><span data-stu-id="07e56-213">2 = UPDATE ALL</span></span><br /><br /> <span data-ttu-id="07e56-214">4 = REFERENCES ALL</span><span class="sxs-lookup"><span data-stu-id="07e56-214">4 = REFERENCES ALL</span></span><br /><br /> <span data-ttu-id="07e56-215">8 = INSERT</span><span class="sxs-lookup"><span data-stu-id="07e56-215">8 = INSERT</span></span><br /><br /> <span data-ttu-id="07e56-216">16 = DELETE</span><span class="sxs-lookup"><span data-stu-id="07e56-216">16 = DELETE</span></span><br /><br /> <span data-ttu-id="07e56-217">32 = EXECUTE (nur Prozeduren)</span><span class="sxs-lookup"><span data-stu-id="07e56-217">32 = EXECUTE (procedures only)</span></span>|<span data-ttu-id="07e56-218">19</span><span class="sxs-lookup"><span data-stu-id="07e56-218">19</span></span>|<span data-ttu-id="07e56-219">Ja</span><span class="sxs-lookup"><span data-stu-id="07e56-219">Yes</span></span>|  
|<span data-ttu-id="07e56-220">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="07e56-220">**RequestID**</span></span>|<span data-ttu-id="07e56-221">**int**</span><span class="sxs-lookup"><span data-stu-id="07e56-221">**int**</span></span>|<span data-ttu-id="07e56-222">Die ID der Anforderung, die die Anweisung enthält.</span><span class="sxs-lookup"><span data-stu-id="07e56-222">ID of the request containing the statement.</span></span>|<span data-ttu-id="07e56-223">49</span><span class="sxs-lookup"><span data-stu-id="07e56-223">49</span></span>|<span data-ttu-id="07e56-224">Ja</span><span class="sxs-lookup"><span data-stu-id="07e56-224">Yes</span></span>|  
|<span data-ttu-id="07e56-225">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="07e56-225">**ServerName**</span></span>|<span data-ttu-id="07e56-226">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="07e56-226">**nvarchar**</span></span>|<span data-ttu-id="07e56-227">Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, für die eine Ablaufverfolgung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="07e56-227">Name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] being traced.</span></span>|<span data-ttu-id="07e56-228">26</span><span class="sxs-lookup"><span data-stu-id="07e56-228">26</span></span>|<span data-ttu-id="07e56-229">Nein</span><span class="sxs-lookup"><span data-stu-id="07e56-229">No</span></span>|  
|<span data-ttu-id="07e56-230">**SessionLoginName**</span><span class="sxs-lookup"><span data-stu-id="07e56-230">**SessionLoginName**</span></span>|<span data-ttu-id="07e56-231">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="07e56-231">**nvarchar**</span></span>|<span data-ttu-id="07e56-232">Der Anmeldename des Benutzers, der die Sitzung gestartet hat.</span><span class="sxs-lookup"><span data-stu-id="07e56-232">Login name of the user who originated the session.</span></span> <span data-ttu-id="07e56-233">Wenn Sie z. B. mit Login1 eine Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und mit Login2 eine Anweisung ausführen, zeigt **SessionLoginName** Login1 an, und **LoginName** zeigt Login2 an.</span><span class="sxs-lookup"><span data-stu-id="07e56-233">For example, if you connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, **SessionLoginName** shows Login1 and **LoginName** shows Login2.</span></span> <span data-ttu-id="07e56-234">Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.</span><span class="sxs-lookup"><span data-stu-id="07e56-234">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows logins.</span></span>|<span data-ttu-id="07e56-235">64</span><span class="sxs-lookup"><span data-stu-id="07e56-235">64</span></span>|<span data-ttu-id="07e56-236">Ja</span><span class="sxs-lookup"><span data-stu-id="07e56-236">Yes</span></span>|  
|<span data-ttu-id="07e56-237">**SPID**</span><span class="sxs-lookup"><span data-stu-id="07e56-237">**SPID**</span></span>|<span data-ttu-id="07e56-238">**int**</span><span class="sxs-lookup"><span data-stu-id="07e56-238">**int**</span></span>|<span data-ttu-id="07e56-239">Die ID der Sitzung, in der das Ereignis aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="07e56-239">ID of the session on which the event occurred.</span></span>|<span data-ttu-id="07e56-240">12</span><span class="sxs-lookup"><span data-stu-id="07e56-240">12</span></span>|<span data-ttu-id="07e56-241">Ja</span><span class="sxs-lookup"><span data-stu-id="07e56-241">Yes</span></span>|  
|<span data-ttu-id="07e56-242">**StartTime**</span><span class="sxs-lookup"><span data-stu-id="07e56-242">**StartTime**</span></span>|<span data-ttu-id="07e56-243">**datetime**</span><span class="sxs-lookup"><span data-stu-id="07e56-243">**datetime**</span></span>|<span data-ttu-id="07e56-244">Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).</span><span class="sxs-lookup"><span data-stu-id="07e56-244">Time at which the event started, if available.</span></span>|<span data-ttu-id="07e56-245">14</span><span class="sxs-lookup"><span data-stu-id="07e56-245">14</span></span>|<span data-ttu-id="07e56-246">Ja</span><span class="sxs-lookup"><span data-stu-id="07e56-246">Yes</span></span>|  
|<span data-ttu-id="07e56-247">**Erfolgreich**</span><span class="sxs-lookup"><span data-stu-id="07e56-247">**Success**</span></span>|<span data-ttu-id="07e56-248">**int**</span><span class="sxs-lookup"><span data-stu-id="07e56-248">**int**</span></span>|<span data-ttu-id="07e56-249">1 = Erfolg</span><span class="sxs-lookup"><span data-stu-id="07e56-249">1 = success.</span></span> <span data-ttu-id="07e56-250">0 = Fehler.</span><span class="sxs-lookup"><span data-stu-id="07e56-250">0 = failure.</span></span> <span data-ttu-id="07e56-251">Der Wert 1 deutet beispielsweise auf eine erfolgreiche Überprüfung der Berechtigungen hin, während die Überprüfung bei dem Wert 0 fehlgeschlagen ist.</span><span class="sxs-lookup"><span data-stu-id="07e56-251">For example, a value of 1 indicates success of a permissions check and a value of 0 indicates failure of that check.</span></span>|<span data-ttu-id="07e56-252">23</span><span class="sxs-lookup"><span data-stu-id="07e56-252">23</span></span>|<span data-ttu-id="07e56-253">Ja</span><span class="sxs-lookup"><span data-stu-id="07e56-253">Yes</span></span>|  
|<span data-ttu-id="07e56-254">**TargetLoginName**</span><span class="sxs-lookup"><span data-stu-id="07e56-254">**TargetLoginName**</span></span>|<span data-ttu-id="07e56-255">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="07e56-255">**nvarchar**</span></span>|<span data-ttu-id="07e56-256">Für Aktionen, die auf einen Anmeldenamen abzielen (z. B. das Hinzufügen eines neuen Anmeldenamens), der Anmeldename, auf den abgezielt wird.</span><span class="sxs-lookup"><span data-stu-id="07e56-256">For actions that target a login (for example, adding a new login), the name of the targeted login.</span></span>|<span data-ttu-id="07e56-257">42</span><span class="sxs-lookup"><span data-stu-id="07e56-257">42</span></span>|<span data-ttu-id="07e56-258">Ja</span><span class="sxs-lookup"><span data-stu-id="07e56-258">Yes</span></span>|  
|<span data-ttu-id="07e56-259">**TargetLoginSid**</span><span class="sxs-lookup"><span data-stu-id="07e56-259">**TargetLoginSid**</span></span>|<span data-ttu-id="07e56-260">**image**</span><span class="sxs-lookup"><span data-stu-id="07e56-260">**image**</span></span>|<span data-ttu-id="07e56-261">Für Aktionen, die auf einen Anmeldenamen abzielen (z. B. das Hinzufügen eines neuen Anmeldenamens), die Sicherheits-ID (SID), auf die abgezielt wird.</span><span class="sxs-lookup"><span data-stu-id="07e56-261">For actions that target a login (for example, adding a new login), the security identification number (SID) of the targeted login.</span></span>|<span data-ttu-id="07e56-262">43</span><span class="sxs-lookup"><span data-stu-id="07e56-262">43</span></span>|<span data-ttu-id="07e56-263">Ja</span><span class="sxs-lookup"><span data-stu-id="07e56-263">Yes</span></span>|  
|<span data-ttu-id="07e56-264">**TargetUserName**</span><span class="sxs-lookup"><span data-stu-id="07e56-264">**TargetUserName**</span></span>|<span data-ttu-id="07e56-265">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="07e56-265">**nvarchar**</span></span>|<span data-ttu-id="07e56-266">Für Aktionen, die auf einen Datenbankbenutzer abzielen (z. B. das Erteilen von Berechtigungen für einen Benutzer), der Name des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="07e56-266">For actions that target a database user (for example, granting permission to a user), the name of that user.</span></span>|<span data-ttu-id="07e56-267">39</span><span class="sxs-lookup"><span data-stu-id="07e56-267">39</span></span>|<span data-ttu-id="07e56-268">Ja</span><span class="sxs-lookup"><span data-stu-id="07e56-268">Yes</span></span>|  
|<span data-ttu-id="07e56-269">**TextData**</span><span class="sxs-lookup"><span data-stu-id="07e56-269">**TextData**</span></span>|<span data-ttu-id="07e56-270">**ntext**</span><span class="sxs-lookup"><span data-stu-id="07e56-270">**ntext**</span></span>|<span data-ttu-id="07e56-271">Textwert, der von der Ereignisklasse abhängt, die in der Ablaufverfolgung aufgezeichnet wurde.</span><span class="sxs-lookup"><span data-stu-id="07e56-271">Text value dependent on the event class captured in the trace.</span></span>|<span data-ttu-id="07e56-272">1</span><span class="sxs-lookup"><span data-stu-id="07e56-272">1</span></span>|<span data-ttu-id="07e56-273">Ja</span><span class="sxs-lookup"><span data-stu-id="07e56-273">Yes</span></span>|  
|<span data-ttu-id="07e56-274">**TransactionID**</span><span class="sxs-lookup"><span data-stu-id="07e56-274">**TransactionID**</span></span>|<span data-ttu-id="07e56-275">**bigint**</span><span class="sxs-lookup"><span data-stu-id="07e56-275">**bigint**</span></span>|<span data-ttu-id="07e56-276">Die vom System zugewiesene ID der Transaktion.</span><span class="sxs-lookup"><span data-stu-id="07e56-276">System-assigned ID of the transaction.</span></span>|<span data-ttu-id="07e56-277">4</span><span class="sxs-lookup"><span data-stu-id="07e56-277">4</span></span>|<span data-ttu-id="07e56-278">Ja</span><span class="sxs-lookup"><span data-stu-id="07e56-278">Yes</span></span>|  
|<span data-ttu-id="07e56-279">**XactSequence**</span><span class="sxs-lookup"><span data-stu-id="07e56-279">**XactSequence**</span></span>|<span data-ttu-id="07e56-280">**bigint**</span><span class="sxs-lookup"><span data-stu-id="07e56-280">**bigint**</span></span>|<span data-ttu-id="07e56-281">Token zur Beschreibung der aktuellen Transaktion.</span><span class="sxs-lookup"><span data-stu-id="07e56-281">Token used to describe the current transaction.</span></span>|<span data-ttu-id="07e56-282">50</span><span class="sxs-lookup"><span data-stu-id="07e56-282">50</span></span>|<span data-ttu-id="07e56-283">Ja</span><span class="sxs-lookup"><span data-stu-id="07e56-283">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="07e56-284">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="07e56-284">See Also</span></span>  
 [<span data-ttu-id="07e56-285">sp_trace_setevent &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="07e56-285">sp_trace_setevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  