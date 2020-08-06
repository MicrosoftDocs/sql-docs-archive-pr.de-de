---
title: IDBProperties (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 2e5a4fd8-5164-495a-9986-3477aef8d8a5
author: rothja
ms.author: jroth
ms.openlocfilehash: f42ab47de2471fc413e4c6acf0d6c61cb2b6d77c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621486"
---
# <a name="idbproperties-ole-db"></a>IDBProperties (OLE DB)
  Dank der OLE DB-Standardspezifikation können Anbieter VT_EMPTY für `DBPROPINFO::vValues` angeben. Allerdings [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt Native Client OLE DB immer VT_EMPTY zurück, wenn Sie `IDBProperties::GetPropertyInfo` mit aufrufen `DBPROPSET_ROWSETALL` , um Rowseteigenschaften abzurufen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schnittstellen &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  
