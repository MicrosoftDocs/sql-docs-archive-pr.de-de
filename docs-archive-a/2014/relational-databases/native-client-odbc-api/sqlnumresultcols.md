---
title: SQLNumResultCols | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLNumResultCols function
ms.assetid: f79d8b3c-521e-4e50-a564-21d73ae5767b
author: rothja
ms.author: jroth
ms.openlocfilehash: 45e72165eef621dc377b02ed3d2e7e1e3cf7ab8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87622063"
---
# <a name="sqlnumresultcols"></a>SQLNumResultCols
  Bei ausgeführten Anweisungen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nimmt der Native Client-ODBC-Treiber den Server nicht an, um die Anzahl der Spalten in einem Resultset zu melden. In diesem Fall `SQLNumResultCols` verursacht keinen Serverroundtrip. Wie [SQLDescribeCol](sqldescribecol.md) und [SQLColAttribute](sqlcolattribute.md)wird durch `SQLNumResultCols` den Aufruf von für vorbereitete, aber nicht ausgeführte Anweisungen ein Serverroundtrip generiert.  
  
 Wenn eine [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung oder ein Anweisungsbatch mehrere Resultsets für Zeilen zurückgibt, kann die Anzahl der Resultset-Spalten sich von einem Set zum nächsten ändern. `SQLNumResultCols`muss für jeden Satz aufgerufen werden. Wenn sich die Anzahl der Spalten ändert, sollte die Anwendung Datenwerte vor dem Abrufen von Zeilenergebnissen erneut binden. Weitere Informationen zum Verarbeiten mehrerer Resultsets finden Sie unter [SQLMoreResults](sqlmoreresults.md).  
  
 Verbesserungen in der Datenbank-Engine, die mit beginnen [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] , ermöglichen SQLNumResultCols, genauere Beschreibungen der erwarteten Ergebnisse zu erhalten. Diese präziseren Ergebnisse können sich von den Werten unterscheiden, die von SQLNumResultCols in früheren Versionen von zurückgegeben wurden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Weitere Informationen finden Sie unter [Metadatenermittlung](../native-client/features/metadata-discovery.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLNumResultCols-Funktion](https://go.microsoft.com/fwlink/?LinkId=59359)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
