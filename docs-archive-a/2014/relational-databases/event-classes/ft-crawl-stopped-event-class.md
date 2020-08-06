---
title: FT:Crawl Stopped-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Crawl Stopped event class
ms.assetid: dbc91bf7-687c-4083-9694-02f3e102c175
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4fe72aa8b6c38a25baf537eb01bac7924d43e290
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615414"
---
# <a name="ftcrawl-stopped-event-class"></a><span data-ttu-id="7d439-102">FT:Crawl Stopped-Ereignisklasse</span><span class="sxs-lookup"><span data-stu-id="7d439-102">FT:Crawl Stopped Event Class</span></span>
  <span data-ttu-id="7d439-103">Die **:Crawl Stopped** -Ereignisklasse zeigt an, dass eine Volltextdurchforstung (Auffüllung) beendet wurde.</span><span class="sxs-lookup"><span data-stu-id="7d439-103">The **:Crawl Stopped** event class indicates that a full-text crawl (population) has stopped.</span></span> <span data-ttu-id="7d439-104">Die Beendigung kann aus einem erfolgreichen Abschließen der Durchforstung oder aus einem schwerwiegenden Fehler erfolgen.</span><span class="sxs-lookup"><span data-stu-id="7d439-104">The stop can be due to a successfully completed crawl or a fatal error.</span></span>  
  
## <a name="ftcrawl-stopped-event-class-data-columns"></a><span data-ttu-id="7d439-105">Datenspalten der FT:Crawl Stopped-Ereignisklasse</span><span class="sxs-lookup"><span data-stu-id="7d439-105">FT:Crawl Stopped Event Class Data Columns</span></span>  
  
|<span data-ttu-id="7d439-106">Datenspaltenname</span><span class="sxs-lookup"><span data-stu-id="7d439-106">Data column name</span></span>|<span data-ttu-id="7d439-107">Datentyp</span><span class="sxs-lookup"><span data-stu-id="7d439-107">Data type</span></span>|<span data-ttu-id="7d439-108">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="7d439-108">Description</span></span>|<span data-ttu-id="7d439-109">Column ID</span><span class="sxs-lookup"><span data-stu-id="7d439-109">Column ID</span></span>|<span data-ttu-id="7d439-110">Filterbar</span><span class="sxs-lookup"><span data-stu-id="7d439-110">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="7d439-111">**DatabaseID**</span><span class="sxs-lookup"><span data-stu-id="7d439-111">**DatabaseID**</span></span>|<span data-ttu-id="7d439-112">**int**</span><span class="sxs-lookup"><span data-stu-id="7d439-112">**int**</span></span>|<span data-ttu-id="7d439-113">Die ID der Datenbank, in der die Volltextdurchforstung beendet wurde.</span><span class="sxs-lookup"><span data-stu-id="7d439-113">ID of the database in which the full-text crawl has stopped.</span></span> <span data-ttu-id="7d439-114">Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="7d439-114">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="7d439-115">3</span><span class="sxs-lookup"><span data-stu-id="7d439-115">3</span></span>|<span data-ttu-id="7d439-116">Ja</span><span class="sxs-lookup"><span data-stu-id="7d439-116">Yes</span></span>|  
|<span data-ttu-id="7d439-117">**EventClass**</span><span class="sxs-lookup"><span data-stu-id="7d439-117">**EventClass**</span></span>|<span data-ttu-id="7d439-118">**int**</span><span class="sxs-lookup"><span data-stu-id="7d439-118">**int**</span></span>|<span data-ttu-id="7d439-119">Ereignistyp = 156.</span><span class="sxs-lookup"><span data-stu-id="7d439-119">Type of event = 156.</span></span>|<span data-ttu-id="7d439-120">27</span><span class="sxs-lookup"><span data-stu-id="7d439-120">27</span></span>|<span data-ttu-id="7d439-121">Nein</span><span class="sxs-lookup"><span data-stu-id="7d439-121">No</span></span>|  
|<span data-ttu-id="7d439-122">**EventSequence**</span><span class="sxs-lookup"><span data-stu-id="7d439-122">**EventSequence**</span></span>|<span data-ttu-id="7d439-123">**int**</span><span class="sxs-lookup"><span data-stu-id="7d439-123">**int**</span></span>|<span data-ttu-id="7d439-124">Sequenz eines bestimmten Ereignisses innerhalb der Anforderung.</span><span class="sxs-lookup"><span data-stu-id="7d439-124">Sequence of a given event within the request.</span></span>|<span data-ttu-id="7d439-125">51</span><span class="sxs-lookup"><span data-stu-id="7d439-125">51</span></span>|<span data-ttu-id="7d439-126">Nein</span><span class="sxs-lookup"><span data-stu-id="7d439-126">No</span></span>|  
|<span data-ttu-id="7d439-127">**IsSystem**</span><span class="sxs-lookup"><span data-stu-id="7d439-127">**IsSystem**</span></span>|<span data-ttu-id="7d439-128">**int**</span><span class="sxs-lookup"><span data-stu-id="7d439-128">**int**</span></span>|<span data-ttu-id="7d439-129">Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="7d439-129">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="7d439-130">1 = System, 0 = Benutzer.</span><span class="sxs-lookup"><span data-stu-id="7d439-130">1 = system, 0 = user.</span></span>|<span data-ttu-id="7d439-131">60</span><span class="sxs-lookup"><span data-stu-id="7d439-131">60</span></span>|<span data-ttu-id="7d439-132">Ja</span><span class="sxs-lookup"><span data-stu-id="7d439-132">Yes</span></span>|  
|<span data-ttu-id="7d439-133">**ObjectID**</span><span class="sxs-lookup"><span data-stu-id="7d439-133">**ObjectID**</span></span>|<span data-ttu-id="7d439-134">**int**</span><span class="sxs-lookup"><span data-stu-id="7d439-134">**int**</span></span>|<span data-ttu-id="7d439-135">Vom System zugewiesene ID des Objekts.</span><span class="sxs-lookup"><span data-stu-id="7d439-135">System-assigned ID of the object.</span></span> <span data-ttu-id="7d439-136">Die Volltextdurchforstung wurde für den Volltextindex in diesem Objekt beendet.</span><span class="sxs-lookup"><span data-stu-id="7d439-136">The full-text crawl has stopped for the full-text index on this object.</span></span>|<span data-ttu-id="7d439-137">22</span><span class="sxs-lookup"><span data-stu-id="7d439-137">22</span></span>|<span data-ttu-id="7d439-138">Ja</span><span class="sxs-lookup"><span data-stu-id="7d439-138">Yes</span></span>|  
|<span data-ttu-id="7d439-139">**SessionLoginName**</span><span class="sxs-lookup"><span data-stu-id="7d439-139">**SessionLoginName**</span></span>|<span data-ttu-id="7d439-140">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="7d439-140">**nvarchar**</span></span>|<span data-ttu-id="7d439-141">Der Anmeldename des Benutzers, der die Sitzung gestartet hat.</span><span class="sxs-lookup"><span data-stu-id="7d439-141">Login name of the user who originated the session.</span></span> <span data-ttu-id="7d439-142">Wenn Sie z. B. mit Login1 eine Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und mit Login2 eine Anweisung ausführen, zeigt **SessionLoginName** Login1 an, und **LoginName** zeigt Login2 an.</span><span class="sxs-lookup"><span data-stu-id="7d439-142">For example, if you connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, **SessionLoginName** shows Login1 and **LoginName** shows Login2.</span></span> <span data-ttu-id="7d439-143">Diese Spalte zeigt die Windows-Anmeldenamen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und [!INCLUDE[msCoName](../../includes/msconame-md.md)] an.</span><span class="sxs-lookup"><span data-stu-id="7d439-143">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows logins.</span></span>|<span data-ttu-id="7d439-144">64</span><span class="sxs-lookup"><span data-stu-id="7d439-144">64</span></span>|<span data-ttu-id="7d439-145">Ja</span><span class="sxs-lookup"><span data-stu-id="7d439-145">Yes</span></span>|  
|<span data-ttu-id="7d439-146">**SPID**</span><span class="sxs-lookup"><span data-stu-id="7d439-146">**SPID**</span></span>|<span data-ttu-id="7d439-147">**int**</span><span class="sxs-lookup"><span data-stu-id="7d439-147">**int**</span></span>|<span data-ttu-id="7d439-148">Die ID der Sitzung, in der das Ereignis aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="7d439-148">ID of the session on which the event occurred.</span></span>|<span data-ttu-id="7d439-149">12</span><span class="sxs-lookup"><span data-stu-id="7d439-149">12</span></span>|<span data-ttu-id="7d439-150">Ja</span><span class="sxs-lookup"><span data-stu-id="7d439-150">Yes</span></span>|  
|<span data-ttu-id="7d439-151">**StartTime**</span><span class="sxs-lookup"><span data-stu-id="7d439-151">**StartTime**</span></span>|<span data-ttu-id="7d439-152">**datetime**</span><span class="sxs-lookup"><span data-stu-id="7d439-152">**datetime**</span></span>|<span data-ttu-id="7d439-153">Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).</span><span class="sxs-lookup"><span data-stu-id="7d439-153">Time at which the event started, if available.</span></span>|<span data-ttu-id="7d439-154">14</span><span class="sxs-lookup"><span data-stu-id="7d439-154">14</span></span>|<span data-ttu-id="7d439-155">Ja</span><span class="sxs-lookup"><span data-stu-id="7d439-155">Yes</span></span>|  
|<span data-ttu-id="7d439-156">**TransactionID**</span><span class="sxs-lookup"><span data-stu-id="7d439-156">**TransactionID**</span></span>|<span data-ttu-id="7d439-157">**bigint**</span><span class="sxs-lookup"><span data-stu-id="7d439-157">**bigint**</span></span>|<span data-ttu-id="7d439-158">Die vom System zugewiesene ID der Transaktion.</span><span class="sxs-lookup"><span data-stu-id="7d439-158">System-assigned ID of the transaction.</span></span>|<span data-ttu-id="7d439-159">4</span><span class="sxs-lookup"><span data-stu-id="7d439-159">4</span></span>|<span data-ttu-id="7d439-160">Ja</span><span class="sxs-lookup"><span data-stu-id="7d439-160">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7d439-161">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="7d439-161">See Also</span></span>  
 [<span data-ttu-id="7d439-162">sp_trace_setevent &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7d439-162">sp_trace_setevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  