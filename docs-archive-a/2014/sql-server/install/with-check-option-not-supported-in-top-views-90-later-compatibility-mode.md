---
title: WITH Check Option wird in Sichten, die Top in 90 oder höheren Kompatibilitäts Modi enthalten, nicht unterstützt. Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- TOP clause
- WITH CHECK OPTION clause
ms.assetid: 1b9581d0-bad9-43e0-b8fc-f32d8a8a04ca
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ee7775c875e33f104341a1da39f5fe6c9326f284
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617384"
---
# <a name="with-check-option-is-not-supported-in-views-that-contain-top-in-90-or-later-compatibility-modes"></a><span data-ttu-id="0001d-102">WITH CHECK OPTION wird nicht in Sichten unterstützt, die die TOP-Klausel im Kompatibilitätsmodus 90 oder höher enthalten</span><span class="sxs-lookup"><span data-stu-id="0001d-102">WITH CHECK OPTION is not supported in views that contain TOP in 90 or later compatibility modes</span></span>
  <span data-ttu-id="0001d-103">Der Upgrade Advisor hat eine Sicht erkannt, die WITH CHECK OPTION und eine TOP-Klausel in der SELECT-Anweisung der Sicht oder in einer Sicht verwendet, auf die verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="0001d-103">Upgrade Advisor detected a view that uses the WITH CHECK OPTION and a TOP clause in the SELECT statement of the view or in a referenced view.</span></span> <span data-ttu-id="0001d-104">Sichten, die auf diese Weise definiert werden, lassen es fälschlicherweise zu, dass Daten über die Sicht geändert werden, und können zu ungenauen Ergebnissen führen, wenn der Datenbank-Kompatibilitätsmodus auf 80 oder höher festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="0001d-104">Views defined this way incorrectly allow data to be modified through the view and may produce inaccurate results when the database compatibility mode is set to 80 and earlier.</span></span> <span data-ttu-id="0001d-105">Daten können nicht über eine Sicht eingegeben oder aktualisiert werden, die WITH CHECK OPTION verwendet, wenn die Sicht oder eine Sicht, auf die verwiesen wird, die TOP-Klausel verwendet und der Datenbank-Kompatibilitätsmodus auf 90 oder höher festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="0001d-105">Data cannot be inserted or updated through a view that uses WITH CHECK OPTION when the view or a referenced view uses the TOP clause and the database compatibility mode is set to 90 or later.</span></span>  
  
## <a name="component"></a><span data-ttu-id="0001d-106">Komponente</span><span class="sxs-lookup"><span data-stu-id="0001d-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="0001d-107">Korrekturmaßnahme</span><span class="sxs-lookup"><span data-stu-id="0001d-107">Corrective Action</span></span>  
 <span data-ttu-id="0001d-108">Beim Upgrade behalten die Benutzerdatenbanken ihren Kompatibilitätsmodus bei.</span><span class="sxs-lookup"><span data-stu-id="0001d-108">When you upgrade, user databases maintain their compatibility mode.</span></span> <span data-ttu-id="0001d-109">Bevor Sie den Datenbank-Kompatibilitätsmodus in 100 oder höher ändern, ändern Sie Sichten, die sowohl die WITH CHECK OPTION als auch die TOP-Klausel verwenden, wenn die Datenänderung über die Sicht erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="0001d-109">Before you change the database compatibility mode to 100 or later, modify views that use both WITH CHECK OPTION and TOP if data modification through the view is required.</span></span> <span data-ttu-id="0001d-110">Weitere Informationen finden Sie unter [sp_dbcmptlevel &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-dbcmptlevel-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="0001d-110">For more information, see [sp_dbcmptlevel &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dbcmptlevel-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0001d-111">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="0001d-111">See Also</span></span>  
 <span data-ttu-id="0001d-112">[Datenbank-Engine Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="0001d-112">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="0001d-113">SQL Server 2014 Upgrade Advisor &#91;neuen&#93;</span><span class="sxs-lookup"><span data-stu-id="0001d-113">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  