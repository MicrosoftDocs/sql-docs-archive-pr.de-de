---
title: Unterstützung für Spalten mit geringer Dichte (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 11ae959f-2fb6-4b85-ac5d-1476a82136d4
author: rothja
ms.author: jroth
ms.openlocfilehash: 076709f3f37e92492f7c3f8c20ee692416d9e867
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718073"
---
# <a name="sparse-columns-support-odbc"></a>Unterstützung für Spalten mit geringer Dichte (ODBC)
  In diesem Thema wird die Unterstützung des ODBC-Treibers von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client für Sparsespalten beschrieben. Ein Beispiel zur Veranschaulichung der ODBC-Unterstützung für sparsespalten finden Sie unter " [aufzurufen von SQLColumns" für eine Tabelle mit Spalten](../../native-client-odbc-how-to/call-sqlcolumns-on-a-table-with-sparse-columns.md) Weitere Informationen zu Sparsespalten finden Sie unter [Sparse Columns Support in SQL Server Native Client](../features/sparse-columns-support-in-sql-server-native-client.md).  
  
## <a name="statement-metadata"></a>Anweisungsmetadaten  
 Das Deskriptorfeld für den Anwendungsparameterdeskriptor (APD) und das SQL_SOPT_SS_NAME_SCOPE-Anweisungsattribut akzeptieren die zusätzlichen Werte SQL_SS_NAME_SCOPE_EXTENDED und SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET. Diese Werte geben an, welche Spalten in dem von [SQLColumns](../../native-client-odbc-api/sqlcolumns.md)zurückgegebenen Resultset enthalten sind. Weitere Informationen zu SQL_SOPT_SS_NAME_SCOPE finden Sie unter [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md).  
  
 Mithilfe eines neuen Implementierungszeilendeskriptors (IRD), ein schreibgeschütztes SQLSMALLINT-Feld namens SQL_CA_SS_IS_COLUMN_SET, kann bestimmt werden, ob eine Spalte einen XML `column_set`-Wert darstellt. SQL_CA_SS_IS_COLUMN_SET akzeptiert die Werte SQL_TRUE und SQL_FALSE.  
  
## <a name="catalog-metadata"></a>Katalogmetadaten  
 Zwei [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -spezifische Spalten (SS_IS_SPARSE and SS_IS_COLUMN_SET) wurden dem Resultset für [SQLColumns](../../native-client-odbc-api/sqlcolumns.md).  
  
## <a name="odbc-function-support-for-sparse-columns"></a>ODBC-Funktionsunterstützung für Spalten mit geringer Dichte  
 Die folgenden ODBC-Funktionen wurden aktualisiert, um Sparsespalten in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client zu unterstützen:  
  
-   [SQLColAttribute](../../native-client-odbc-api/sqlcolattribute.md)  
  
-   [SQLColumns](../../native-client-odbc-api/sqlcolumns.md)  
  
-   [SQLGetDescField](../../native-client-odbc-api/sqlgetdescfield.md)  
  
-   [SQLSetDescField](../../native-client-odbc-api/sqlsetdescfield.md)  
  
-   [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client &#40;ODBC&#41;](sql-server-native-client-odbc.md)  
  
  
