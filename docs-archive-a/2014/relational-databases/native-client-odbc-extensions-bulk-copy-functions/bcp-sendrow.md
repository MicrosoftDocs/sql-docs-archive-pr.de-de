---
title: bcp_sendrow | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_sendrow
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_sendrow function
ms.assetid: ddbdb4bd-ad4e-4bf1-9a75-656aa26ce10a
author: rothja
ms.author: jroth
ms.openlocfilehash: 3d2f55486ba57101ffc7b1903de5d19ac8eaaca2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87616046"
---
# <a name="bcp_sendrow"></a>'bcp_sendrow'
  Sendet eine Datenzeile aus Programmvariablen an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RETCODE bcp_sendrow (  
    HDBC   
hdbc  
);  
  
```  
  
## <a name="arguments"></a>Argumente  
 *hdbc*  
 Das für den Massenkopiervorgang aktivierte ODBC-Verbindungshandle.  
  
## <a name="returns"></a>Gibt zurück  
 SUCCEED oder FAIL.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **bcp_sendrow** -Funktion erstellt eine Zeile aus Programmvariablen und sendet sie an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Vor dem Aufruf von **bcp_sendrow**müssen Sie Aufrufe an [bcp_bind](bcp-bind.md) vornehmen, um die Programmvariablen mit den Zeilendaten anzugeben.  
  
 Wird **bcp_bind** unter Angabe eines langen Datentyps variabler Länge wie einem *eDataType* -Parameter von SQLTEXT und einem *pData* -Parameter ungleich NULL aufgerufen, sendet **bcp_sendrow** wie bei jedem anderen Datentyp den gesamten Datenwert. Hat dagegen **bcp_bind** einen *pData* -Parameter mit NULL-Wert, gibt **bcp_sendrow** die Steuerung an die Anwendung zurück, sobald alle angegebenen Datenspalten an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]gesendet wurden. Die Anwendung kann dann wiederholt [bcp_moretext](bcp-moretext.md) aufrufen, um die langen Daten variabler Länge Segment für Segment an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu senden. Weitere Informationen finden Sie unter [bcp_moretext](bcp-moretext.md).  
  
 Wenn mit **bcp_sendrow** Zeilen aus Programmvariablen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabellen massenkopiert werden, wird für die Zeilen erst dann ein Commit durchgeführt, wenn der Benutzer [bcp_batch](bcp-batch.md) oder [bcp_done](bcp-done.md)aufruft. Der Benutzer kann **bcp_batch** wahlweise einmal für alle *n* Zeilen aufrufen oder dann, wenn bei den eingehenden Daten eine Pause auftritt. Wird **bcp_batch** nie aufgerufen, wird ein Commit für die Zeilen ausgeführt, wenn **bcp_done** aufgerufen wird.  
  
 Informationen zu einem Breaking Change beim Massen kopieren ab finden Sie unter [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [Durchführen von Massen Kopier Vorgängen &#40;ODBC-&#41;](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bulk Copy Functions](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
