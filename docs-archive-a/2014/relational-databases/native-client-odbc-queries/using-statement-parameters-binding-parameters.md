---
title: Bindungs Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, parameters
- parameters [SQL Server Native Client], ODBC
- statements [ODBC], parameters
- binding parameters [SQL Server Native Client]
- parameter markers [ODBC]
- unbound parameter markers
- SQLBindParameter function
- ODBC applications, parameters
- bound parameter markers [SQL Server Native Client]
ms.assetid: d6c69739-8f89-475f-a60a-b2f6c06576e2
author: rothja
ms.author: jroth
ms.openlocfilehash: 3402a7efce43d0ce94a20c93504ac1dcb2c7b48f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608600"
---
# <a name="binding-parameters"></a>Binden von Parametern
  Jede Parametermarkierung in einer SQL-Anweisung muss mit einer Variablen in der Anwendung verknüpft oder an diese gebunden werden, bevor die Anweisung ausgeführt wird. Dies erfolgt durch Aufrufen der [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) -Funktion. **SQLBindParameter** beschreibt die Programm Variable (Adresse, C-Datentyp usw.) für den Treiber. Ferner identifiziert sie die Parametermarkierung durch Angabe ihres Ordinalwerts und beschreibt anschließend die Eigenschaften des SQL-Objekts, das sie darstellt (SQL-Datentyp, Genauigkeit usw.).

 Parametermarkierungen können vor der Ausführung einer Anweisung jederzeit gebunden bzw. neu gebunden werden. Eine Parameterbindung bleibt wirksam, bis eines der folgenden Ereignisse eintritt:

-   Ein [SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md) -Befehl, bei dem der *Option* -Parameter auf festgelegt ist SQL_RESET_PARAMS gibt alle an das Anweisungs Handle gebundenen Parameter frei.

-   Ein **SQLBindParameter** -Befehl, bei dem *ParameterNumber* auf die Ordinalzahl eines gebundenen Parameter Markers festgelegt ist, gibt automatisch die vorherige Bindung frei.

 Eine Anwendung kann ferner Parameter an Arrays von Programmvariablen binden, um eine SQL-Anweisung batchweise zu verarbeiten. Es gibt zwei Arten der Arraybindung:

-   Die spaltenweise Bindung ist fertig gestellt, wenn jeder einzelne Parameter an sein eigenes Array von Variablen gebunden wurde.

     Die spaltenweise Bindung wird angegeben, indem [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) aufgerufen wird, wobei *Attribute* auf SQL_ATTR_PARAM_BIND_TYPE und *ValuePtr* auf SQL_PARAM_BIND_BY_COLUMN festgelegt ist.

-   Die zeilenweise Beendung ist fertig gestellt, wenn alle Parameter in der SQL-Anweisung als Einheit an ein Array von Strukturen gebunden wurden, die die einzelnen Variablen für die Parameter enthalten.

     Die zeilenweise Bindung wird angegeben, indem **SQLSetStmtAttr** aufgerufen wird, wobei *Attribute* auf SQL_ATTR_PARAM_BIND_TYPE festgelegt ist und *ValuePtr* auf die Größe der Struktur festgelegt ist, die die Programmvariablen enthält.

 Wenn der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber Zeichen-oder Binär Zeichenfolgen-Parameter an den Server sendet, werden die Werte in die im **SQLBindParameter** *ColumnSize* -Parameter angegebene Länge aufgefüllt. Wenn eine ODBC 2. x-Anwendung 0 für *ColumnSize*angibt, füllt der Treiber den Parameterwert auf die Genauigkeit des Datentyps auf. Die Genauigkeit beträgt bei einer Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 8000, bei einer Verbindung zu älteren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 255. *ColumnSize* ist für Variant-Spalten in Bytes.

 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt definierende Namen für gespeicherte Prozedurparameter. ODBC 3.5 hat ebenfalls Unterstützung für benannte Parameter eingeführt, die verwendet werden, wenn in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gespeicherte Prozeduren aufgerufen werden. Diese Unterstützung kann für Folgendes verwendet werden:

-   Zum Aufrufen einer gespeicherten Prozedur und Eingeben von Werten für eine Teilmenge der für die gespeicherte Prozedur definierten Parameter

-   Zum Angeben der Parameter in einer anderen Reihenfolge in der Anwendung als in der Reihenfolge, in der sie bei der Erstellung der gespeicherten Prozedur angegeben wurden

 Benannte Parameter werden nur unterstützt, wenn die- [!INCLUDE[tsql](../../includes/tsql-md.md)] `EXECUTE` Anweisung oder die ODBC-Rückruf-Escapesequenz zum Ausführen einer gespeicherten Prozedur verwendet wird.

 Wenn `SQL_DESC_NAME` für einen gespeicherten Prozedurparameter festgelegt wird, sollten alle gespeicherten Prozedurparameter in der Abfrage ebenfalls `SQL_DESC_NAME` festlegen.  Wenn Literale in Aufrufen gespeicherter Prozeduren verwendet werden, `SQL_DESC_NAME` für die Parameter festgelegt wurden, sollten die Literale das Format *' Name* = *value*' verwenden, wobei *Name* der Parameter Name der gespeicherten Prozedur (z @p1 . b.) ist. Weitere Informationen finden Sie unter [Binden von Parametern anhand des Namens (benannte Parameter)](https://go.microsoft.com/fwlink/?LinkId=167215).

## <a name="see-also"></a>Weitere Informationen
 [Verwenden von Anweisungsparametern](using-statement-parameters.md)


