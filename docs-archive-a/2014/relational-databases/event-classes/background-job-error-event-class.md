---
title: Background Job Error-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Background Job Error event class
ms.assetid: 9e6d2a0e-919d-4fe2-a306-b20b8d41c197
author: stevestein
ms.author: sstein
ms.openlocfilehash: 11aeaa058209eebd93b83fc812db2173167bf65a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699579"
---
# <a name="background-job-error-event-class"></a><span data-ttu-id="8ce84-102">Background Job Error-Ereignisklasse</span><span class="sxs-lookup"><span data-stu-id="8ce84-102">Background Job Error Event Class</span></span>
  <span data-ttu-id="8ce84-103">Die **Background Job Error** -Ereignisklasse tritt auf, wenn ein Hintergrundauftrag fehlerbedingt beendet wurde.</span><span class="sxs-lookup"><span data-stu-id="8ce84-103">The **Background Job Error** event class occurs when a background job has terminated abnormally.</span></span> <span data-ttu-id="8ce84-104">Dieser Zustand erfordert möglicherweise ein Eingreifen des Systemadministrators.</span><span class="sxs-lookup"><span data-stu-id="8ce84-104">This condition might require the attention of a system administrator.</span></span>  
  
## <a name="background-job-error-event-class-data-columns"></a><span data-ttu-id="8ce84-105">Datenspalten der Background Job Error-Ereignisklasse</span><span class="sxs-lookup"><span data-stu-id="8ce84-105">Background Job Error Event Class Data Columns</span></span>  
  
|<span data-ttu-id="8ce84-106">Datenspaltenname</span><span class="sxs-lookup"><span data-stu-id="8ce84-106">Data column name</span></span>|<span data-ttu-id="8ce84-107">Datentyp</span><span class="sxs-lookup"><span data-stu-id="8ce84-107">Data type</span></span>|<span data-ttu-id="8ce84-108">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="8ce84-108">Description</span></span>|<span data-ttu-id="8ce84-109">Column ID</span><span class="sxs-lookup"><span data-stu-id="8ce84-109">Column ID</span></span>|<span data-ttu-id="8ce84-110">Filterbar</span><span class="sxs-lookup"><span data-stu-id="8ce84-110">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="8ce84-111">**DatabaseID**</span><span class="sxs-lookup"><span data-stu-id="8ce84-111">**DatabaseID**</span></span>|<span data-ttu-id="8ce84-112">**int**</span><span class="sxs-lookup"><span data-stu-id="8ce84-112">**int**</span></span>|<span data-ttu-id="8ce84-113">ID der durch den Auftrag angegebenen Datenbank.</span><span class="sxs-lookup"><span data-stu-id="8ce84-113">ID of the database specified by job.</span></span> <span data-ttu-id="8ce84-114">Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="8ce84-114">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="8ce84-115">3</span><span class="sxs-lookup"><span data-stu-id="8ce84-115">3</span></span>|<span data-ttu-id="8ce84-116">Ja</span><span class="sxs-lookup"><span data-stu-id="8ce84-116">Yes</span></span>|  
|<span data-ttu-id="8ce84-117">**DatabaseName**</span><span class="sxs-lookup"><span data-stu-id="8ce84-117">**DatabaseName**</span></span>|<span data-ttu-id="8ce84-118">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="8ce84-118">**nvarchar**</span></span>|<span data-ttu-id="8ce84-119">Name der Datenbank, in der die Benutzeranweisung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="8ce84-119">Name of the database in which the user statement is running.</span></span>|<span data-ttu-id="8ce84-120">35</span><span class="sxs-lookup"><span data-stu-id="8ce84-120">35</span></span>|<span data-ttu-id="8ce84-121">Ja</span><span class="sxs-lookup"><span data-stu-id="8ce84-121">Yes</span></span>|  
|<span data-ttu-id="8ce84-122">**Fehler**</span><span class="sxs-lookup"><span data-stu-id="8ce84-122">**Error**</span></span>|<span data-ttu-id="8ce84-123">**int**</span><span class="sxs-lookup"><span data-stu-id="8ce84-123">**int**</span></span>|<span data-ttu-id="8ce84-124">Fehlernummer des letzten Versuchs (nur bei**EventSubClass** 1).</span><span class="sxs-lookup"><span data-stu-id="8ce84-124">Error number of the last attempt (**EventSubClass** 1 only).</span></span>|<span data-ttu-id="8ce84-125">31</span><span class="sxs-lookup"><span data-stu-id="8ce84-125">31</span></span>|<span data-ttu-id="8ce84-126">Ja</span><span class="sxs-lookup"><span data-stu-id="8ce84-126">Yes</span></span>|  
|<span data-ttu-id="8ce84-127">**EventClass**</span><span class="sxs-lookup"><span data-stu-id="8ce84-127">**EventClass**</span></span>|<span data-ttu-id="8ce84-128">**int**</span><span class="sxs-lookup"><span data-stu-id="8ce84-128">**int**</span></span>|<span data-ttu-id="8ce84-129">Ereignistyp = 193.</span><span class="sxs-lookup"><span data-stu-id="8ce84-129">Type of event = 193.</span></span>|<span data-ttu-id="8ce84-130">27</span><span class="sxs-lookup"><span data-stu-id="8ce84-130">27</span></span>|<span data-ttu-id="8ce84-131">Nein</span><span class="sxs-lookup"><span data-stu-id="8ce84-131">No</span></span>|  
|<span data-ttu-id="8ce84-132">**EventSequence**</span><span class="sxs-lookup"><span data-stu-id="8ce84-132">**EventSequence**</span></span>|<span data-ttu-id="8ce84-133">**int**</span><span class="sxs-lookup"><span data-stu-id="8ce84-133">**int**</span></span>|<span data-ttu-id="8ce84-134">Die Sequenz eines bestimmten Ereignisses innerhalb der Anforderung.</span><span class="sxs-lookup"><span data-stu-id="8ce84-134">The sequence of a given event within the request.</span></span>|<span data-ttu-id="8ce84-135">51</span><span class="sxs-lookup"><span data-stu-id="8ce84-135">51</span></span>|<span data-ttu-id="8ce84-136">Nein</span><span class="sxs-lookup"><span data-stu-id="8ce84-136">No</span></span>|  
|<span data-ttu-id="8ce84-137">**EventSubClass**</span><span class="sxs-lookup"><span data-stu-id="8ce84-137">**EventSubClass**</span></span>|<span data-ttu-id="8ce84-138">**int**</span><span class="sxs-lookup"><span data-stu-id="8ce84-138">**int**</span></span>|<span data-ttu-id="8ce84-139">Der Typ der Ereignisunterklasse.</span><span class="sxs-lookup"><span data-stu-id="8ce84-139">Type of event subclass.</span></span><br /><br /> <span data-ttu-id="8ce84-140">1 = Hintergrundauftrag nach Fehler vorzeitig beendet.</span><span class="sxs-lookup"><span data-stu-id="8ce84-140">1 = Background job giving up after failure.</span></span><br /><br /> <span data-ttu-id="8ce84-141">2 = Hintergrundauftrag gelöscht - Warteschlange voll.</span><span class="sxs-lookup"><span data-stu-id="8ce84-141">2 = Background job dropped - queue is full.</span></span><br /><br /> <span data-ttu-id="8ce84-142">3 = Hintergrundauftrag hat einen Fehler zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="8ce84-142">3 = Background job returned an error.</span></span>|<span data-ttu-id="8ce84-143">21</span><span class="sxs-lookup"><span data-stu-id="8ce84-143">21</span></span>|<span data-ttu-id="8ce84-144">Ja</span><span class="sxs-lookup"><span data-stu-id="8ce84-144">Yes</span></span>|  
|<span data-ttu-id="8ce84-145">**IndexID**</span><span class="sxs-lookup"><span data-stu-id="8ce84-145">**IndexID**</span></span>|<span data-ttu-id="8ce84-146">**int**</span><span class="sxs-lookup"><span data-stu-id="8ce84-146">**int**</span></span>|<span data-ttu-id="8ce84-147">ID für den Index des Objekts, das von dem Ereignis betroffen ist.</span><span class="sxs-lookup"><span data-stu-id="8ce84-147">ID for the index on the object affected by the event.</span></span> <span data-ttu-id="8ce84-148">Sie können die Index-ID für ein Objekt mithilfe der **indid** -Spalte der **sysindexes** -Systemtabelle ermitteln.</span><span class="sxs-lookup"><span data-stu-id="8ce84-148">To determine the index ID for an object, use the **indid** column of the **sysindexes** system table.</span></span>|<span data-ttu-id="8ce84-149">24</span><span class="sxs-lookup"><span data-stu-id="8ce84-149">24</span></span>|<span data-ttu-id="8ce84-150">Ja</span><span class="sxs-lookup"><span data-stu-id="8ce84-150">Yes</span></span>|  
|<span data-ttu-id="8ce84-151">**IntegerData**</span><span class="sxs-lookup"><span data-stu-id="8ce84-151">**IntegerData**</span></span>|<span data-ttu-id="8ce84-152">**int**</span><span class="sxs-lookup"><span data-stu-id="8ce84-152">**int**</span></span>|<span data-ttu-id="8ce84-153">Anzahl der Versuche des Auftrags (nur bei**EventSubClass** 1).</span><span class="sxs-lookup"><span data-stu-id="8ce84-153">Number of tries attempted by the job (**EventSubClass** 1 only).</span></span>|<span data-ttu-id="8ce84-154">25</span><span class="sxs-lookup"><span data-stu-id="8ce84-154">25</span></span>|<span data-ttu-id="8ce84-155">Ja</span><span class="sxs-lookup"><span data-stu-id="8ce84-155">Yes</span></span>|  
|<span data-ttu-id="8ce84-156">**IntegerData2**</span><span class="sxs-lookup"><span data-stu-id="8ce84-156">**IntegerData2**</span></span>|<span data-ttu-id="8ce84-157">**int**</span><span class="sxs-lookup"><span data-stu-id="8ce84-157">**int**</span></span>|<span data-ttu-id="8ce84-158">Auftragssequenznummer.</span><span class="sxs-lookup"><span data-stu-id="8ce84-158">Job sequence number.</span></span>|<span data-ttu-id="8ce84-159">55</span><span class="sxs-lookup"><span data-stu-id="8ce84-159">55</span></span>|<span data-ttu-id="8ce84-160">Ja</span><span class="sxs-lookup"><span data-stu-id="8ce84-160">Yes</span></span>|  
|<span data-ttu-id="8ce84-161">**ObjectID**</span><span class="sxs-lookup"><span data-stu-id="8ce84-161">**ObjectID**</span></span>|<span data-ttu-id="8ce84-162">**int**</span><span class="sxs-lookup"><span data-stu-id="8ce84-162">**int**</span></span>|<span data-ttu-id="8ce84-163">Vom System zugewiesene ID des Objekts.</span><span class="sxs-lookup"><span data-stu-id="8ce84-163">System-assigned ID of the object.</span></span>|<span data-ttu-id="8ce84-164">22</span><span class="sxs-lookup"><span data-stu-id="8ce84-164">22</span></span>|<span data-ttu-id="8ce84-165">Ja</span><span class="sxs-lookup"><span data-stu-id="8ce84-165">Yes</span></span>|  
|<span data-ttu-id="8ce84-166">**SessionLoginName**</span><span class="sxs-lookup"><span data-stu-id="8ce84-166">**SessionLoginName**</span></span>|<span data-ttu-id="8ce84-167">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="8ce84-167">**nvarchar**</span></span>|<span data-ttu-id="8ce84-168">Der Anmeldename des Benutzers, der die Sitzung geöffnet hat.</span><span class="sxs-lookup"><span data-stu-id="8ce84-168">Login name of the user that originated the session.</span></span> <span data-ttu-id="8ce84-169">Wenn Sie z. B. mit Login1 eine Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und mit Login2 eine Anweisung ausführen, zeigt **SessionLoginName** Login1 an, und **LoginName** zeigt Login2 an.</span><span class="sxs-lookup"><span data-stu-id="8ce84-169">For example, if you connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, **SessionLoginName** shows Login1 and **LoginName** shows Login2.</span></span> <span data-ttu-id="8ce84-170">Diese Spalte zeigt die Windows-Anmeldenamen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und [!INCLUDE[msCoName](../../includes/msconame-md.md)] an.</span><span class="sxs-lookup"><span data-stu-id="8ce84-170">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows logins.</span></span>|<span data-ttu-id="8ce84-171">64</span><span class="sxs-lookup"><span data-stu-id="8ce84-171">64</span></span>|<span data-ttu-id="8ce84-172">Ja</span><span class="sxs-lookup"><span data-stu-id="8ce84-172">Yes</span></span>|  
|<span data-ttu-id="8ce84-173">**Severity**</span><span class="sxs-lookup"><span data-stu-id="8ce84-173">**Severity**</span></span>|<span data-ttu-id="8ce84-174">**int**</span><span class="sxs-lookup"><span data-stu-id="8ce84-174">**int**</span></span>|<span data-ttu-id="8ce84-175">Der Schweregrad des Fehlers beim letzten Versuch (nur bei**EventSubClass** 1).</span><span class="sxs-lookup"><span data-stu-id="8ce84-175">Severity level of the error on the last attempt (**EventSubClass** 1 only).</span></span>|<span data-ttu-id="8ce84-176">20</span><span class="sxs-lookup"><span data-stu-id="8ce84-176">20</span></span>|<span data-ttu-id="8ce84-177">Ja</span><span class="sxs-lookup"><span data-stu-id="8ce84-177">Yes</span></span>|  
|<span data-ttu-id="8ce84-178">**StartTime**</span><span class="sxs-lookup"><span data-stu-id="8ce84-178">**StartTime**</span></span>|<span data-ttu-id="8ce84-179">**datetime**</span><span class="sxs-lookup"><span data-stu-id="8ce84-179">**datetime**</span></span>|<span data-ttu-id="8ce84-180">Der Zeitpunkt, zu dem der Auftrag erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="8ce84-180">Time at which the job was created.</span></span>|<span data-ttu-id="8ce84-181">14</span><span class="sxs-lookup"><span data-stu-id="8ce84-181">14</span></span>|<span data-ttu-id="8ce84-182">Ja</span><span class="sxs-lookup"><span data-stu-id="8ce84-182">Yes</span></span>|  
|<span data-ttu-id="8ce84-183">**State**</span><span class="sxs-lookup"><span data-stu-id="8ce84-183">**State**</span></span>|<span data-ttu-id="8ce84-184">**int**</span><span class="sxs-lookup"><span data-stu-id="8ce84-184">**int**</span></span>|<span data-ttu-id="8ce84-185">Der Status des Fehlers beim letzten Versuch (nur bei**EventSubClass** 1).</span><span class="sxs-lookup"><span data-stu-id="8ce84-185">State of the error on the last attempt (**EventSubClass** 1 only).</span></span>|<span data-ttu-id="8ce84-186">30</span><span class="sxs-lookup"><span data-stu-id="8ce84-186">30</span></span>|<span data-ttu-id="8ce84-187">Ja</span><span class="sxs-lookup"><span data-stu-id="8ce84-187">Yes</span></span>|  
|<span data-ttu-id="8ce84-188">**TextData**</span><span class="sxs-lookup"><span data-stu-id="8ce84-188">**TextData**</span></span>|<span data-ttu-id="8ce84-189">**ntext**</span><span class="sxs-lookup"><span data-stu-id="8ce84-189">**ntext**</span></span>|<span data-ttu-id="8ce84-190">Die Textbeschreibung des Wertes der Ereignisunterklasse.</span><span class="sxs-lookup"><span data-stu-id="8ce84-190">Text description of the event subclass value.</span></span>|<span data-ttu-id="8ce84-191">1</span><span class="sxs-lookup"><span data-stu-id="8ce84-191">1</span></span>|<span data-ttu-id="8ce84-192">Ja</span><span class="sxs-lookup"><span data-stu-id="8ce84-192">Yes</span></span>|  
|<span data-ttu-id="8ce84-193">**Typ**</span><span class="sxs-lookup"><span data-stu-id="8ce84-193">**Type**</span></span>|<span data-ttu-id="8ce84-194">**int**</span><span class="sxs-lookup"><span data-stu-id="8ce84-194">**int**</span></span>|<span data-ttu-id="8ce84-195">Typ des Auftrags.</span><span class="sxs-lookup"><span data-stu-id="8ce84-195">Type of job.</span></span>|<span data-ttu-id="8ce84-196">57</span><span class="sxs-lookup"><span data-stu-id="8ce84-196">57</span></span>|<span data-ttu-id="8ce84-197">Ja</span><span class="sxs-lookup"><span data-stu-id="8ce84-197">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8ce84-198">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="8ce84-198">See Also</span></span>  
 <span data-ttu-id="8ce84-199">[Erweiterte Ereignisse](../extended-events/extended-events.md) </span><span class="sxs-lookup"><span data-stu-id="8ce84-199">[Extended Events](../extended-events/extended-events.md) </span></span>  
 <span data-ttu-id="8ce84-200">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8ce84-200">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span></span>  
 [<span data-ttu-id="8ce84-201">Auto Stats-Ereignisklasse</span><span class="sxs-lookup"><span data-stu-id="8ce84-201">Auto Stats Event Class</span></span>](auto-stats-event-class.md)  
  
  