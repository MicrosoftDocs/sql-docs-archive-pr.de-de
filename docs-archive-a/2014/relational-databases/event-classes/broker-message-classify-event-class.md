---
title: Broker:Message Classify-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Broker:Message Classify event class
ms.assetid: e51f3351-1239-4c41-b87c-1dd86968e027
author: stevestein
ms.author: sstein
ms.openlocfilehash: c3a53c34ef42e52b955e22acdeaa9bb77b662cd4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699573"
---
# <a name="brokermessage-classify-event-class"></a><span data-ttu-id="3ac08-102">Broker:Message Classify-Ereignisklasse</span><span class="sxs-lookup"><span data-stu-id="3ac08-102">Broker:Message Classify Event Class</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3ac08-103">generiert ein **Broker:Message Classify** -Ereignis, wenn Service Broker das Routing für eine Nachricht bestimmt.</span><span class="sxs-lookup"><span data-stu-id="3ac08-103">generates a **Broker:Message Classify** event when Service Broker determines the routing for a message.</span></span>  
  
## <a name="brokermessage-classify-event-class-data-columns"></a><span data-ttu-id="3ac08-104">Datenspalten der Broker:Message Classify-Ereignisklasse</span><span class="sxs-lookup"><span data-stu-id="3ac08-104">Broker:Message Classify Event Class Data Columns</span></span>  
  
|<span data-ttu-id="3ac08-105">Datenspalte</span><span class="sxs-lookup"><span data-stu-id="3ac08-105">Data column</span></span>|<span data-ttu-id="3ac08-106">Datentyp</span><span class="sxs-lookup"><span data-stu-id="3ac08-106">Data type</span></span>|<span data-ttu-id="3ac08-107">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="3ac08-107">Description</span></span>|<span data-ttu-id="3ac08-108">Spaltennummer</span><span class="sxs-lookup"><span data-stu-id="3ac08-108">Column number</span></span>|<span data-ttu-id="3ac08-109">Filterbar</span><span class="sxs-lookup"><span data-stu-id="3ac08-109">Filterable</span></span>|  
|-----------------|---------------|-----------------|-------------------|----------------|  
|<span data-ttu-id="3ac08-110">**ApplicationName**</span><span class="sxs-lookup"><span data-stu-id="3ac08-110">**ApplicationName**</span></span>|<span data-ttu-id="3ac08-111">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="3ac08-111">**nvarchar**</span></span>|<span data-ttu-id="3ac08-112">Der Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat.</span><span class="sxs-lookup"><span data-stu-id="3ac08-112">The name of the client application that created the connection to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3ac08-113">Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.</span><span class="sxs-lookup"><span data-stu-id="3ac08-113">This column is populated with the values passed by the application rather than the displayed name of the program.</span></span>|<span data-ttu-id="3ac08-114">10</span><span class="sxs-lookup"><span data-stu-id="3ac08-114">10</span></span>|<span data-ttu-id="3ac08-115">Ja</span><span class="sxs-lookup"><span data-stu-id="3ac08-115">Yes</span></span>|  
|<span data-ttu-id="3ac08-116">**ClientProcessID**</span><span class="sxs-lookup"><span data-stu-id="3ac08-116">**ClientProcessID**</span></span>|<span data-ttu-id="3ac08-117">**int**</span><span class="sxs-lookup"><span data-stu-id="3ac08-117">**int**</span></span>|<span data-ttu-id="3ac08-118">Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="3ac08-118">The ID assigned by the host computer to the process where the client application is running.</span></span> <span data-ttu-id="3ac08-119">Diese Datenspalte wird aufgefüllt, wenn die Clientprozess-ID durch den Client bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="3ac08-119">This data column is populated if the client process ID is provided by the client.</span></span>|<span data-ttu-id="3ac08-120">9</span><span class="sxs-lookup"><span data-stu-id="3ac08-120">9</span></span>|<span data-ttu-id="3ac08-121">Ja</span><span class="sxs-lookup"><span data-stu-id="3ac08-121">Yes</span></span>|  
|<span data-ttu-id="3ac08-122">**DatabaseID**</span><span class="sxs-lookup"><span data-stu-id="3ac08-122">**DatabaseID**</span></span>|<span data-ttu-id="3ac08-123">**int**</span><span class="sxs-lookup"><span data-stu-id="3ac08-123">**int**</span></span>|<span data-ttu-id="3ac08-124">Die ID der Datenbank, die durch die USE *database* -Anweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine bestimmte Instanz keine USE *database* -Anweisung ausgegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="3ac08-124">The ID of the database specified by the USE *database* statement, or the ID of the default database if no USE *database* statement has been issued for a given instance.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="3ac08-125">zeigt den Namen der Datenbank an, wenn die **ServerName** -Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="3ac08-125">displays the name of the database if the **ServerName** data column is captured in the trace and the server is available.</span></span> <span data-ttu-id="3ac08-126">Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="3ac08-126">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="3ac08-127">3</span><span class="sxs-lookup"><span data-stu-id="3ac08-127">3</span></span>|<span data-ttu-id="3ac08-128">Ja</span><span class="sxs-lookup"><span data-stu-id="3ac08-128">Yes</span></span>|  
|<span data-ttu-id="3ac08-129">**EventClass**</span><span class="sxs-lookup"><span data-stu-id="3ac08-129">**EventClass**</span></span>|<span data-ttu-id="3ac08-130">**int**</span><span class="sxs-lookup"><span data-stu-id="3ac08-130">**int**</span></span>|<span data-ttu-id="3ac08-131">Der Typ der aufgezeichneten Ereignisklasse.</span><span class="sxs-lookup"><span data-stu-id="3ac08-131">The type of event class captured.</span></span> <span data-ttu-id="3ac08-132">Für **Broker:Message Classify** lautet der Typ immer **141**.</span><span class="sxs-lookup"><span data-stu-id="3ac08-132">Always **141** for **Broker:Message Classify**.</span></span>|<span data-ttu-id="3ac08-133">27</span><span class="sxs-lookup"><span data-stu-id="3ac08-133">27</span></span>|<span data-ttu-id="3ac08-134">Nein</span><span class="sxs-lookup"><span data-stu-id="3ac08-134">No</span></span>|  
|<span data-ttu-id="3ac08-135">**EventSequence**</span><span class="sxs-lookup"><span data-stu-id="3ac08-135">**EventSequence**</span></span>|<span data-ttu-id="3ac08-136">**int**</span><span class="sxs-lookup"><span data-stu-id="3ac08-136">**int**</span></span>|<span data-ttu-id="3ac08-137">Die Sequenznummer für dieses Ereignis.</span><span class="sxs-lookup"><span data-stu-id="3ac08-137">Sequence number for this event.</span></span>|<span data-ttu-id="3ac08-138">51</span><span class="sxs-lookup"><span data-stu-id="3ac08-138">51</span></span>|<span data-ttu-id="3ac08-139">Nein</span><span class="sxs-lookup"><span data-stu-id="3ac08-139">No</span></span>|  
|<span data-ttu-id="3ac08-140">**EventSubClass**</span><span class="sxs-lookup"><span data-stu-id="3ac08-140">**EventSubClass**</span></span>|<span data-ttu-id="3ac08-141">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="3ac08-141">**nvarchar**</span></span>|<span data-ttu-id="3ac08-142">Der Typ der Ereignisunterklasse, der weitere Informationen zu jeder Ereignisklasse liefert.</span><span class="sxs-lookup"><span data-stu-id="3ac08-142">The type of event subclass, providing further information about each event class.</span></span> <span data-ttu-id="3ac08-143">Diese Spalte kann die folgenden Werte enthalten:</span><span class="sxs-lookup"><span data-stu-id="3ac08-143">This column may contain the following values:</span></span><br /><br /> <span data-ttu-id="3ac08-144">**Lokal**: Die ausgewählte Route hat die Adresse LOCAL.</span><span class="sxs-lookup"><span data-stu-id="3ac08-144">**Local**: The route chosen has the address LOCAL.</span></span><br /><br /> <span data-ttu-id="3ac08-145">**Remote**: die ausgewählte Route hat eine andere Adresse als local.</span><span class="sxs-lookup"><span data-stu-id="3ac08-145">**Remote**: The route chosen has an address other than LOCAL.</span></span><br /><br /> <span data-ttu-id="3ac08-146">**Verzögert**: die Nachricht wird verzögert, weil die Weiterleitung deaktiviert ist oder weil keine übereinstimmende Route vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="3ac08-146">**Delayed**: The message is delayed, either because forwarding is disabled or because there is no matching route present.</span></span>|<span data-ttu-id="3ac08-147">21</span><span class="sxs-lookup"><span data-stu-id="3ac08-147">21</span></span>|<span data-ttu-id="3ac08-148">Ja</span><span class="sxs-lookup"><span data-stu-id="3ac08-148">Yes</span></span>|  
|<span data-ttu-id="3ac08-149">**FileName**</span><span class="sxs-lookup"><span data-stu-id="3ac08-149">**FileName**</span></span>|<span data-ttu-id="3ac08-150">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="3ac08-150">**nvarchar**</span></span>|<span data-ttu-id="3ac08-151">Der Dienstname, an den die Nachricht weitergeleitet wird.</span><span class="sxs-lookup"><span data-stu-id="3ac08-151">The service name that the message is directed to.</span></span>|<span data-ttu-id="3ac08-152">36</span><span class="sxs-lookup"><span data-stu-id="3ac08-152">36</span></span>|<span data-ttu-id="3ac08-153">Nein</span><span class="sxs-lookup"><span data-stu-id="3ac08-153">No</span></span>|  
|<span data-ttu-id="3ac08-154">**GUID**</span><span class="sxs-lookup"><span data-stu-id="3ac08-154">**GUID**</span></span>|<span data-ttu-id="3ac08-155">**uniqueidentifier**</span><span class="sxs-lookup"><span data-stu-id="3ac08-155">**uniqueidentifier**</span></span>|<span data-ttu-id="3ac08-156">Die Konversations-ID des Dialogs.</span><span class="sxs-lookup"><span data-stu-id="3ac08-156">The conversation id of the dialog.</span></span> <span data-ttu-id="3ac08-157">Dieser Bezeichner wird als Teil der Nachricht übertragen und von beiden Seiten der Konversation gemeinsam verwendet.</span><span class="sxs-lookup"><span data-stu-id="3ac08-157">This identifier is transmitted as part of the message, and is shared between both sides of the conversation.</span></span>|<span data-ttu-id="3ac08-158">54</span><span class="sxs-lookup"><span data-stu-id="3ac08-158">54</span></span>|<span data-ttu-id="3ac08-159">Nein</span><span class="sxs-lookup"><span data-stu-id="3ac08-159">No</span></span>|  
|<span data-ttu-id="3ac08-160">**HostName**</span><span class="sxs-lookup"><span data-stu-id="3ac08-160">**HostName**</span></span>|<span data-ttu-id="3ac08-161">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="3ac08-161">**nvarchar**</span></span>|<span data-ttu-id="3ac08-162">Der Name des Computers, auf dem der Client ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="3ac08-162">The name of the computer on which the client is running.</span></span> <span data-ttu-id="3ac08-163">Diese Datenspalte wird aufgefüllt, wenn der Hostname durch den Client bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="3ac08-163">This data column is populated if the host name is provided by the client.</span></span> <span data-ttu-id="3ac08-164">Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.</span><span class="sxs-lookup"><span data-stu-id="3ac08-164">To determine the host name, use the HOST_NAME function.</span></span>|<span data-ttu-id="3ac08-165">8</span><span class="sxs-lookup"><span data-stu-id="3ac08-165">8</span></span>|<span data-ttu-id="3ac08-166">Ja</span><span class="sxs-lookup"><span data-stu-id="3ac08-166">Yes</span></span>|  
|<span data-ttu-id="3ac08-167">**IsSystem**</span><span class="sxs-lookup"><span data-stu-id="3ac08-167">**IsSystem**</span></span>|<span data-ttu-id="3ac08-168">**int**</span><span class="sxs-lookup"><span data-stu-id="3ac08-168">**int**</span></span>|<span data-ttu-id="3ac08-169">Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="3ac08-169">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="3ac08-170">1 = System, 0 = Benutzer.</span><span class="sxs-lookup"><span data-stu-id="3ac08-170">1 = system, 0 = user.</span></span>|<span data-ttu-id="3ac08-171">60</span><span class="sxs-lookup"><span data-stu-id="3ac08-171">60</span></span>|<span data-ttu-id="3ac08-172">Nein</span><span class="sxs-lookup"><span data-stu-id="3ac08-172">No</span></span>|  
|<span data-ttu-id="3ac08-173">**LoginSid**</span><span class="sxs-lookup"><span data-stu-id="3ac08-173">**LoginSid**</span></span>|<span data-ttu-id="3ac08-174">**image**</span><span class="sxs-lookup"><span data-stu-id="3ac08-174">**image**</span></span>|<span data-ttu-id="3ac08-175">Die Sicherheits-ID (SID, Security Identification Number) des angemeldeten Benutzers.</span><span class="sxs-lookup"><span data-stu-id="3ac08-175">The security identification number (SID) of the logged-in user.</span></span> <span data-ttu-id="3ac08-176">Die SID ist für jede Anmeldung beim Server eindeutig.</span><span class="sxs-lookup"><span data-stu-id="3ac08-176">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="3ac08-177">41</span><span class="sxs-lookup"><span data-stu-id="3ac08-177">41</span></span>|<span data-ttu-id="3ac08-178">Ja</span><span class="sxs-lookup"><span data-stu-id="3ac08-178">Yes</span></span>|  
|<span data-ttu-id="3ac08-179">**NTDomainName**</span><span class="sxs-lookup"><span data-stu-id="3ac08-179">**NTDomainName**</span></span>|<span data-ttu-id="3ac08-180">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="3ac08-180">**nvarchar**</span></span>|<span data-ttu-id="3ac08-181">Die Windows-Domäne, der der Benutzer angehört.</span><span class="sxs-lookup"><span data-stu-id="3ac08-181">The Windows domain to which the user belongs.</span></span>|<span data-ttu-id="3ac08-182">7</span><span class="sxs-lookup"><span data-stu-id="3ac08-182">7</span></span>|<span data-ttu-id="3ac08-183">Ja</span><span class="sxs-lookup"><span data-stu-id="3ac08-183">Yes</span></span>|  
|<span data-ttu-id="3ac08-184">**NTUserName**</span><span class="sxs-lookup"><span data-stu-id="3ac08-184">**NTUserName**</span></span>|<span data-ttu-id="3ac08-185">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="3ac08-185">**nvarchar**</span></span>|<span data-ttu-id="3ac08-186">Der Name des Benutzers, der Besitzer der Verbindung ist, die dieses Ereignis generiert hat.</span><span class="sxs-lookup"><span data-stu-id="3ac08-186">The name of the user that owns the connection that generated this event.</span></span>|<span data-ttu-id="3ac08-187">6</span><span class="sxs-lookup"><span data-stu-id="3ac08-187">6</span></span>|<span data-ttu-id="3ac08-188">Ja</span><span class="sxs-lookup"><span data-stu-id="3ac08-188">Yes</span></span>|  
|<span data-ttu-id="3ac08-189">**OwnerName**</span><span class="sxs-lookup"><span data-stu-id="3ac08-189">**OwnerName**</span></span>|<span data-ttu-id="3ac08-190">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="3ac08-190">**nvarchar**</span></span>|<span data-ttu-id="3ac08-191">Der Brokerbezeichner, an den die Nachricht weitergeleitet wird.</span><span class="sxs-lookup"><span data-stu-id="3ac08-191">The broker identifier that the message is directed to.</span></span>|<span data-ttu-id="3ac08-192">37</span><span class="sxs-lookup"><span data-stu-id="3ac08-192">37</span></span>|<span data-ttu-id="3ac08-193">Nein</span><span class="sxs-lookup"><span data-stu-id="3ac08-193">No</span></span>|  
|<span data-ttu-id="3ac08-194">**RoleName**</span><span class="sxs-lookup"><span data-stu-id="3ac08-194">**RoleName**</span></span>|<span data-ttu-id="3ac08-195">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="3ac08-195">**nvarchar**</span></span>|<span data-ttu-id="3ac08-196">Gibt an, ob die Nachricht aus dem Netzwerk empfangen wurde oder ob sie aus dieser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz stammt.</span><span class="sxs-lookup"><span data-stu-id="3ac08-196">Indicates whether the message was received from the network, or originated in this [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>|<span data-ttu-id="3ac08-197">38</span><span class="sxs-lookup"><span data-stu-id="3ac08-197">38</span></span>|<span data-ttu-id="3ac08-198">Nein</span><span class="sxs-lookup"><span data-stu-id="3ac08-198">No</span></span>|  
|<span data-ttu-id="3ac08-199">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="3ac08-199">**ServerName**</span></span>|<span data-ttu-id="3ac08-200">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="3ac08-200">**nvarchar**</span></span>|<span data-ttu-id="3ac08-201">Der Name der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , für die eine Ablaufverfolgung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="3ac08-201">The name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] being traced.</span></span>|<span data-ttu-id="3ac08-202">26</span><span class="sxs-lookup"><span data-stu-id="3ac08-202">26</span></span>|<span data-ttu-id="3ac08-203">Nein</span><span class="sxs-lookup"><span data-stu-id="3ac08-203">No</span></span>|  
|<span data-ttu-id="3ac08-204">**SPID**</span><span class="sxs-lookup"><span data-stu-id="3ac08-204">**SPID**</span></span>|<span data-ttu-id="3ac08-205">**int**</span><span class="sxs-lookup"><span data-stu-id="3ac08-205">**int**</span></span>|<span data-ttu-id="3ac08-206">Die Serverprozess-ID, die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dem Prozess zugewiesen wurde, der diesem Client zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="3ac08-206">The server process ID assigned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to the process associated with the client.</span></span>|<span data-ttu-id="3ac08-207">12</span><span class="sxs-lookup"><span data-stu-id="3ac08-207">12</span></span>|<span data-ttu-id="3ac08-208">Ja</span><span class="sxs-lookup"><span data-stu-id="3ac08-208">Yes</span></span>|  
|<span data-ttu-id="3ac08-209">**Startzeit**</span><span class="sxs-lookup"><span data-stu-id="3ac08-209">**Start Time**</span></span>|<span data-ttu-id="3ac08-210">**datetime**</span><span class="sxs-lookup"><span data-stu-id="3ac08-210">**datetime**</span></span>|<span data-ttu-id="3ac08-211">Der Zeitpunkt, zu dem das Ereignis begonnen hat, falls verfügbar.</span><span class="sxs-lookup"><span data-stu-id="3ac08-211">The time at which the event started, when available.</span></span>|<span data-ttu-id="3ac08-212">14</span><span class="sxs-lookup"><span data-stu-id="3ac08-212">14</span></span>|<span data-ttu-id="3ac08-213">Ja</span><span class="sxs-lookup"><span data-stu-id="3ac08-213">Yes</span></span>|  
|<span data-ttu-id="3ac08-214">**TargetUserName**</span><span class="sxs-lookup"><span data-stu-id="3ac08-214">**TargetUserName**</span></span>|<span data-ttu-id="3ac08-215">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="3ac08-215">**nvarchar**</span></span>|<span data-ttu-id="3ac08-216">Die Netzwerkadresse des nächsten Hopbrokers.</span><span class="sxs-lookup"><span data-stu-id="3ac08-216">The network address of the next hop broker.</span></span>|<span data-ttu-id="3ac08-217">39</span><span class="sxs-lookup"><span data-stu-id="3ac08-217">39</span></span>|<span data-ttu-id="3ac08-218">Nein</span><span class="sxs-lookup"><span data-stu-id="3ac08-218">No</span></span>|  
|<span data-ttu-id="3ac08-219">**TransactionID**</span><span class="sxs-lookup"><span data-stu-id="3ac08-219">**TransactionID**</span></span>|<span data-ttu-id="3ac08-220">**bigint**</span><span class="sxs-lookup"><span data-stu-id="3ac08-220">**bigint**</span></span>|<span data-ttu-id="3ac08-221">Die vom System zugewiesene ID der Transaktion.</span><span class="sxs-lookup"><span data-stu-id="3ac08-221">The system-assigned ID of the transaction.</span></span>|<span data-ttu-id="3ac08-222">4</span><span class="sxs-lookup"><span data-stu-id="3ac08-222">4</span></span>|<span data-ttu-id="3ac08-223">Nein</span><span class="sxs-lookup"><span data-stu-id="3ac08-223">No</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3ac08-224">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="3ac08-224">See Also</span></span>  
 [<span data-ttu-id="3ac08-225">SQL Server Service Broker</span><span class="sxs-lookup"><span data-stu-id="3ac08-225">SQL Server Service Broker</span></span>](../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  