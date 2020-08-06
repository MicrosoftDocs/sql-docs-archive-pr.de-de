---
title: Dialogfeld „Verlegereinstellungen“ für die SQL Server-Replikation | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publishersettings.f1
helpviewer_keywords:
- Publisher Settings dialog box
ms.assetid: 4fb70427-082d-4179-82a1-34b235accc43
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3a9a5ca5b0d7bfae895287708af159f3316e4474
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87724490"
---
# <a name="sql-server-replication-publisher-settings-dialog-box"></a><span data-ttu-id="f57c0-102">Dialogfeld „Verlegereinstellungen“ für die SQL Server-Replikation</span><span class="sxs-lookup"><span data-stu-id="f57c0-102">SQL Server Replication 'Publisher Settings' dialog box</span></span>
  <span data-ttu-id="f57c0-103">Im Dialogfeld **Verlegereinstellungen** können Sie die Einstellungen für Verleger ändern, die dem linken Bereich des Replikationsmonitors hinzugefügt wurden.</span><span class="sxs-lookup"><span data-stu-id="f57c0-103">The **Publisher Settings** dialog box allows you to change settings for Publishers that have been added to the left pane in Replication Monitor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f57c0-104">Tastatur</span><span class="sxs-lookup"><span data-stu-id="f57c0-104">Options</span></span>  
 <span data-ttu-id="f57c0-105">**Verlegerverbindung**</span><span class="sxs-lookup"><span data-stu-id="f57c0-105">**Publisher Connection**</span></span>  
 <span data-ttu-id="f57c0-106">Klicken Sie auf diese Option, um das Dialogfeld **Verbindung mit dem Server herstellen** zu starten. In diesem Dialogfeld können Sie die Verbindungseigenschaften und Anmeldeinformationen anzeigen und ändern, die vom Replikationsmonitor für die Verbindung mit einem Verleger verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="f57c0-106">Click to launch the **Connect to Server** dialog box, which allows you to view and change the connection properties and credentials Replication Monitor uses to connect to a Publisher.</span></span>  
  
 <span data-ttu-id="f57c0-107">**Verteilerverbindung**</span><span class="sxs-lookup"><span data-stu-id="f57c0-107">**Distributor Connection**</span></span>  
 <span data-ttu-id="f57c0-108">Wird nur angezeigt, wenn vom Verleger ein Remoteverteiler verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="f57c0-108">Displayed only if the Publisher uses a remote Distributor.</span></span> <span data-ttu-id="f57c0-109">Klicken Sie auf diese Option, um das Dialogfeld **Verbindung mit dem Server herstellen** zu starten. In diesem Dialogfeld können Sie die Verbindungseigenschaften und Anmeldeinformationen anzeigen und ändern, die vom Replikationsmonitor für die Verbindung mit dem Remoteverteiler verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="f57c0-109">Click to launch the **Connect to Server** dialog box, which allows you to view and change the connection properties and credentials Replication Monitor uses to connect to the remote Distributor.</span></span>  
  
 <span data-ttu-id="f57c0-110">**Beim Starten des Replikationsmonitors automatisch Verbindung herstellen**</span><span class="sxs-lookup"><span data-stu-id="f57c0-110">**Connect automatically when Replication Monitor starts**</span></span>  
 <span data-ttu-id="f57c0-111">Wählen Sie diese Option aus, damit der Replikationsmonitor automatisch eine Verbindung mit dem Verteiler herstellt und Statusinformationen für den Verleger abruft, der im Raster im oberen Bereich des Dialogfelds ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="f57c0-111">Select to allow Replication Monitor to automatically connect to the Distributor and retrieve status information for the Publisher selected in the grid at the top of the dialog box.</span></span> <span data-ttu-id="f57c0-112">Wenn dieses Kontrollkästchen deaktiviert ist, müssen Sie nach dem Starten des Replikationsmonitors manuell eine Verbindung herstellen: Klicken Sie dazu mit der rechten Maustaste auf den Verleger im linken Bereich des Replikationsmonitors, und klicken Sie dann auf **Verbinden**.</span><span class="sxs-lookup"><span data-stu-id="f57c0-112">If this checkbox is cleared, you must manually connect after launching Replication Monitor: right-click the Publisher in the left pane of Replication Monitor, and click **Connect**.</span></span>  
  
 <span data-ttu-id="f57c0-113">**Status dieses Verlegers und seiner Veröffentlichungen automatisch aktualisieren**</span><span class="sxs-lookup"><span data-stu-id="f57c0-113">**Automatically refresh the status of this Publisher and its publications**</span></span>  
 <span data-ttu-id="f57c0-114">Wählen Sie diese Option aus, damit der Replikationsmonitor automatisch den Status für den Verleger aktualisiert, der im Raster im oberen Bereich des Dialogfelds ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="f57c0-114">Select to allow Replication Monitor to automatically refresh status for the Publisher selected in the grid at the top of the dialog box.</span></span> <span data-ttu-id="f57c0-115">Wenn diese Option ausgewählt ist, ruft der Replikationsmonitor die Statusinformationen für den Verleger und seine Veröffentlichungen über den Verteiler ab.</span><span class="sxs-lookup"><span data-stu-id="f57c0-115">If this option is selected, Replication Monitor polls the Distributor for status information on the Publisher and its publications.</span></span> <span data-ttu-id="f57c0-116">Das Abrufintervall wird durch die Option **Aktualisierungsrate** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="f57c0-116">The polling interval is set by the **Refresh rate** option.</span></span> <span data-ttu-id="f57c0-117">Weitere Informationen zum Aktualisieren im Replikationsmonitor finden Sie unter [Zwischenspeichern, Aktualisieren und Leistung des Replikationsmonitors](monitor/caching-refresh-and-replication-monitor-performance.md).</span><span class="sxs-lookup"><span data-stu-id="f57c0-117">For more information on refresh in Replication Monitor, see [Caching, Refresh, and Replication Monitor Performance](monitor/caching-refresh-and-replication-monitor-performance.md).</span></span>  
  
 <span data-ttu-id="f57c0-118">**Aktualisierungsrate**</span><span class="sxs-lookup"><span data-stu-id="f57c0-118">**Refresh rate**</span></span>  
 <span data-ttu-id="f57c0-119">Geben Sie einen Wert (in Sekunden) ein, um anzugeben, wie oft der Replikationsmonitor Statusinformationen über den Verteiler abrufen soll.</span><span class="sxs-lookup"><span data-stu-id="f57c0-119">Enter a value (in seconds) to specify how frequently Replication Monitor should poll the Distributor for status.</span></span> <span data-ttu-id="f57c0-120">Geringere Werte führen zu einem häufigeren Abruf, was die Leistung des Verteilers beeinträchtigen kann, wenn eine große Anzahl von Verlegern überwacht wird.</span><span class="sxs-lookup"><span data-stu-id="f57c0-120">Lower values result in more frequent polling, which can affect performance at the Distributor if you are monitoring a large number of Publishers.</span></span> <span data-ttu-id="f57c0-121">Es wird empfohlen, das eigene System zu testen, um einen angemessenen Wert zu bestimmen.</span><span class="sxs-lookup"><span data-stu-id="f57c0-121">It is recommended that you test your system to determine an appropriate value.</span></span> <span data-ttu-id="f57c0-122">Die Einstellung **Aktualisierungsrate** wird ebenfalls verwendet, wenn Sie in einem der Detailfenster des Replikationsmonitors die Option **Automatisch aktualisieren** ausgewählt haben.</span><span class="sxs-lookup"><span data-stu-id="f57c0-122">The **Refresh rate** setting is also used if you select **Auto Refresh** in any of the detail windows in Replication Monitor.</span></span>  
  
 <span data-ttu-id="f57c0-123">**Diese(n) Verleger in der folgenden Gruppe anzeigen**</span><span class="sxs-lookup"><span data-stu-id="f57c0-123">**Show this Publisher in the following group**</span></span>  
 <span data-ttu-id="f57c0-124">Wählen Sie eine Verlegergruppe aus der Liste aus.</span><span class="sxs-lookup"><span data-stu-id="f57c0-124">Select a Publisher group from the list.</span></span> <span data-ttu-id="f57c0-125">Der Verleger wird unter dieser Gruppe im linken Bereich angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f57c0-125">The Publisher is displayed under this group in the left pane.</span></span> <span data-ttu-id="f57c0-126">Gruppen stellen eine Möglichkeit zum Organisieren von Verlegern dar und haben keinen Einfluss auf die Funktion der Replikation.</span><span class="sxs-lookup"><span data-stu-id="f57c0-126">Groups provide a way to organize Publishers and have no effect on how replication functions.</span></span>  
  
 <span data-ttu-id="f57c0-127">**Neue Gruppe**</span><span class="sxs-lookup"><span data-stu-id="f57c0-127">**New Group**</span></span>  
 <span data-ttu-id="f57c0-128">Klicken Sie auf diese Option, um eine neue Verlegergruppe zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="f57c0-128">Click to create a new Publisher group.</span></span> <span data-ttu-id="f57c0-129">Eine Verlegergruppe stellt eine einfache Möglichkeit dar, um die Verleger innerhalb des Replikationsmonitors zu organisieren.</span><span class="sxs-lookup"><span data-stu-id="f57c0-129">A Publisher group provides a convenient way to organize Publishers within Replication Monitor.</span></span> <span data-ttu-id="f57c0-130">Gruppen haben keinen Einfluss auf die Replikation der Daten oder die Beziehungen zwischen den Servern in der Replikationstopologie.</span><span class="sxs-lookup"><span data-stu-id="f57c0-130">Groups do not affect the replication of data or the relationship among servers in a replication topology.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f57c0-131">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f57c0-131">See Also</span></span>  
 <span data-ttu-id="f57c0-132">[Starten des Replikationsmonitors](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="f57c0-132">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 [<span data-ttu-id="f57c0-133">Überwachen der Replikation</span><span class="sxs-lookup"><span data-stu-id="f57c0-133">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  