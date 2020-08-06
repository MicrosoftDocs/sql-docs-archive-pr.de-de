---
title: SQLBindCol | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLBindCol function
ms.assetid: fbd7ba20-d917-4ca9-b018-018ac6af9f98
author: rothja
ms.author: jroth
ms.openlocfilehash: 72d0ca1b0fbad144117e409019d8d2247bbf918f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87725718"
---
# <a name="sqlbindcol"></a>SQLBindCol
  Beachten Sie als allgemeine Regel die Auswirkungen der Verwendung von **SQLBindCol** , um Daten zu konvertieren. Bindungskonvertierungen sind Clientprozesse. Wenn Sie beispielsweise einen Gleitkommawert, der an eine Zeichenspalte gebunden ist, abrufen, führt der Treiber die Gleitkomma-in-Zeichen-Konvertierung lokal durch, wenn eine Zeile abgerufen wird. Die [!INCLUDE[tsql](../../includes/tsql-md.md)] CONVERT-Funktion kann zum Übertragen der Kosten einer Datenkonvertierung auf den Server verwendet werden.  
  
 Eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann mehrere Sets an Ergebniszeilen bei einer einzelnen Anweisungsausführung zurückgeben. Jedes Resultset muss getrennt gebunden sein. Weitere Informationen zum Binden mehrerer Resultsets finden Sie unter [SQLMoreResults](sqlmoreresults.md).  
  
 Der Entwickler kann [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe des *TargetType* -Werts Spalten an-spezifische C-Datentypen binden `SQL_C_BINARY` . An [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-spezifische Typen gebundene Spalten sind nicht übertragbar. Die definierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-spezifischen ODBC-C-Datentypen entsprechen den Typdefinitionen für DB-Library, und DB-Library-Entwickler, die Anwendungen übertragen, können diese Funktion nutzen.  
  
 Das Abschneiden von Berichtsdaten ist ein kostspieliger Prozess für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber. Sie können das Abschneiden vermeiden, indem Sie sicherstellen, dass alle gebundenen Datenpuffer weit genug sind, um Daten zurückzugeben. Bei Zeichendaten sollte die Breite ausreichend Platz für ein Zeichenfolgeabschlusszeichen bieten, wenn das Standardtreiberverhalten für den Zeichenfolgenabschluss verwendet wird. Wenn Sie z. b [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . eine **char (5)** -Spalte an ein Array mit fünf Zeichen binden, wird für jeden abgerufenen Wert ein Abschneiden erzielt. Wenn Sie die gleiche Spalte an ein Array mit sechs Zeichen binden, wird die Abschneidung vermieden, indem ein Zeichenelement bereitgestellt wird, in dem das Null-Abschlusszeichen gespeichert werden soll. [SQLGetData](sqlgetdata.md) kann verwendet werden, um lange Zeichen-und Binärdaten ohne Abschneiden effizient abzurufen.  
  
 Bei Datentypen mit umfangreichen Werten wird zurückgegeben, wenn der vom Benutzer bereitgestellte Puffer nicht groß genug ist, um den gesamten Wert der Spalte zu speichern, `SQL_SUCCESS_WITH_INFO` und die Zeichen folgen Daten; Right trunation "wird ausgegeben. Das `StrLen_or_IndPtr`-Argument enthält die Anzahl der im Puffer gespeicherten Zeichen/Bytes.  
  
## <a name="sqlbindcol-support-for-enhanced-date-and-time-features"></a>SQLBindCol-Unterstützung für verbesserte Funktionen für Datum/Uhrzeit  
 Ergebnis Spaltenwerte von Datums-/Uhrzeittypen werden wie in [Konvertierungen von SQL in C](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md)beschrieben konvertiert. Beachten Sie, dass zum Abrufen von Time-und DateTimeOffset-Spalten als zugehörige Strukturen ( `SQL_SS_TIME2_STRUCT` und **SQL_SS_TIMESTAMPOFFSET_STRUCT**) *TargetType* als oder angegeben werden muss `SQL_C_DEFAULT` `SQL_C_BINARY` .  
  
 Weitere Informationen finden Sie unter [Verbesserungen bei Datum und Uhrzeit &#40;ODBC-&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlbindcol-support-for-large-clr-udts"></a>SQLBindCol-Unterstützung für große CLR-UDTs  
 **SQLBindCol** unterstützt große benutzerdefinierte CLR-Typen (UDTs). Weitere Informationen finden Sie unter [große benutzerdefinierte CLR-Typen &#40;ODBC-&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLBindCol-Funktion](https://go.microsoft.com/fwlink/?LinkId=59327)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
