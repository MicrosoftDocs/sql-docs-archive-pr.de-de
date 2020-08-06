---
title: SQLStatistics | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLStatistics function
ms.assetid: e60101ae-a5f5-432f-a32a-d8e6fb0cbde8
author: rothja
ms.author: jroth
ms.openlocfilehash: fcae3e323f735d93bc0cc6024595ec597089b1e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617956"
---
# <a name="sqlstatistics"></a><span data-ttu-id="d381c-102">'SQLStatistics'</span><span class="sxs-lookup"><span data-stu-id="d381c-102">SQLStatistics</span></span>
  <span data-ttu-id="d381c-103">**SQLStatistics** kann in einem statischen Cursor ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="d381c-103">**SQLStatistics** can be executed on a static cursor.</span></span> <span data-ttu-id="d381c-104">Wenn versucht wird, **SQLStatistics** in einem aktualisierbaren (keysetgesteuerten oder dynamischen) Cursor auszuführen, wird SQL_SUCCESS_WITH_INFO zurückgegeben. Das bedeutet, dass der Cursortyp geändert wurde.</span><span class="sxs-lookup"><span data-stu-id="d381c-104">An attempt to execute **SQLStatistics** on an updatable (keyset-driven or dynamic) returns SQL_SUCCESS_WITH_INFO indicating the cursor type is changed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d381c-105">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d381c-105">See Also</span></span>  
 <span data-ttu-id="d381c-106">[SQLStatistics-Funktion](https://go.microsoft.com/fwlink/?LinkId=59372) </span><span class="sxs-lookup"><span data-stu-id="d381c-106">[SQLStatistics Function](https://go.microsoft.com/fwlink/?LinkId=59372) </span></span>  
 [<span data-ttu-id="d381c-107">ODBC API Implementation Details</span><span class="sxs-lookup"><span data-stu-id="d381c-107">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
