---
title: Aktualisieren von Daten in Rowsets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- rowsets [OLE DB], updating data
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, updating data
- SQL Server Native Client OLE DB provider, data updates
- data updates [SQL Server], OLE DB
ms.assetid: 37769b1c-c480-419a-8c54-5cc420bf73db
author: rothja
ms.author: jroth
ms.openlocfilehash: 993cfb67d4e6b72eec7cc0537e9b47371e94af10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718088"
---
# <a name="updating-data-in-rowsets"></a><span data-ttu-id="14b94-102">Aktualisieren von Daten in Rowsets</span><span class="sxs-lookup"><span data-stu-id="14b94-102">Updating Data in Rowsets</span></span>
  <span data-ttu-id="14b94-103">Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter aktualisiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Daten, wenn ein Consumer ein änderbares Rowset aktualisiert, das diese Daten enthält.</span><span class="sxs-lookup"><span data-stu-id="14b94-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider updates [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data when a consumer updates a modifiable rowset that contains that data.</span></span> <span data-ttu-id="14b94-104">Ein modifizierbares Rowset wird erstellt, wenn der Consumer entweder für die **IRowsetChange**-Schnittstelle oder die **IRowsetUpdate**-Schnittstelle Unterstützung anfordert.</span><span class="sxs-lookup"><span data-stu-id="14b94-104">A modifiable rowset is created when the consumer requests support for either the **IRowsetChange** or **IRowsetUpdate** interface.</span></span>  
  
 <span data-ttu-id="14b94-105">Alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von Native Client OLE DB vom Anbieter änderbaren Rowsets verwenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Cursor zur Unterstützung des Rowsets.</span><span class="sxs-lookup"><span data-stu-id="14b94-105">All [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider-modifiable rowsets use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursors to support the rowset.</span></span> <span data-ttu-id="14b94-106">Die Rowseteigenschaft DBPROP_LOCKMODE ändert das Parallelitätskontrollverhalten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bei Cursorn und bestimmt das Verhalten für den Zeilenabruf bei Rowsets sowie die Fehlergenerierung in Bezug auf die Datenintegrität in aktualisierbaren Rowsets.</span><span class="sxs-lookup"><span data-stu-id="14b94-106">The rowset property DBPROP_LOCKMODE alters [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] concurrency control behavior in cursors and determines the behavior of rowset row fetching and data integrity error generation in updatable rowsets.</span></span>  
  
 <span data-ttu-id="14b94-107">Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt die Zeilen Synchronisierung vor oder nach einem Update.</span><span class="sxs-lookup"><span data-stu-id="14b94-107">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports row synchronization before or after an update.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="14b94-108">IRowChange::SetColumns ist verfügbar, um die Werte mindestens einer benannten Spalte eines Zeilenobjekts festzulegen.</span><span class="sxs-lookup"><span data-stu-id="14b94-108">IRowChange::SetColumns is available to set the values of one or more named columns of a row object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="14b94-109">In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="14b94-109">In This Section</span></span>  
  
-   [<span data-ttu-id="14b94-110">Aktualisieren von Daten in SQL Server-Cursorn</span><span class="sxs-lookup"><span data-stu-id="14b94-110">Updating Data in SQL Server Cursors</span></span>](updating-data-in-sql-server-cursors.md)  
  
-   [<span data-ttu-id="14b94-111">Erneutes Synchronisieren von Zeilen</span><span class="sxs-lookup"><span data-stu-id="14b94-111">Resynchronizing Rows</span></span>](updating-data-in-rowsets-resynchronizing-rows.md)  
  
## <a name="see-also"></a><span data-ttu-id="14b94-112">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="14b94-112">See Also</span></span>  
 [<span data-ttu-id="14b94-113">Rowsets</span><span class="sxs-lookup"><span data-stu-id="14b94-113">Rowsets</span></span>](rowsets.md)  
  
  