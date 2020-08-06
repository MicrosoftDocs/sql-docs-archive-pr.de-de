---
title: Behandeln von Fehlern und Meldungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC error handling, about error handling
- errors [ODBC]
- SQL Server Native Client ODBC driver, errors
- messages [ODBC], about messages
- ODBC error handling
- SQL_INVALID_HANDLE return code
- errors [ODBC], about error handling
- messages [ODBC]
ms.assetid: 74ea9630-e482-4a46-bb45-f5234f079b48
author: rothja
ms.author: jroth
ms.openlocfilehash: 4701b3224b87e7d19f1121f193d4be20f9d4c441
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698186"
---
# <a name="handling-errors-and-messages"></a>Behandlung von Fehlern und Meldungen
  Wenn eine Anwendung eine ODBC-Funktion aufruft, führt der Treiber die Funktion aus und gibt Diagnoseinformationen zurück: Ein Rückgabecode gibt das Ergebnis einer ODBC-Funktion zurück (Erfolg oder Fehlschlagen), und Diagnosedatensätze liefern detaillierte Informationen über die Funktion. Diagnosedatensätze enthalten einen Headerdatensatz und Statusdatensätze. Auch wenn die Funktion erfolgreich ausgeführt wurde, wird zumindest ein Diagnosedatensatz, der Headerdatensatz, zurückgegeben.  
  
 Die Diagnoseinformationen dienen während der Entwicklung zur Erfassung von Programmierfehlern wie ungültigen Handles und Syntaxfehlern in hartcodierten SQL-Anweisungen. Darüber hinaus dienen sie zur Laufzeit dazu, Laufzeitfehler und Warnungen zu erfassen, beispielsweise das Abschneiden von Daten, Regelverstöße und Syntaxfehler in benutzerdefinierten SQL-Anweisungen. Die Programmlogik basiert im Allgemeinen auf Rückgabecodes.  
  
 Nachdem eine Anwendung z. b. **SQLFetch** aufgerufen hat, um die Zeilen in einem Resultset abzurufen, gibt der Rückgabecode an, ob das Ende des Resultsets erreicht wurde (SQL_NO_DATA), ob Informationsmeldungen zurückgegeben wurden (SQL_SUCCESS_WITH_INFO) oder ob ein Fehler aufgetreten ist (SQL_ERROR).  
  
 Wenn der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber etwas anderes als SQL_SUCCESS zurückgibt, kann die Anwendung **SQLGetDiagRec** aufrufen, um Informations-oder Fehlermeldungen abzurufen. Verwenden Sie **SQLGetDiagRec** , um den Nachrichten Satz nach oben oder unten zu scrollen, wenn mehr als eine Nachricht vorhanden ist.  
  
 Der Rückgabecode SQL_INVALID_HANDLE gibt immer einen Programmierfehler an und sollte zur Laufzeit nie auftreten. Alle anderen Rückgabecodes stellen Laufzeitinformationen bereit, wenngleich SQL_ERROR einen Programmierfehler angeben kann.  
  
 Die ursprüngliche [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native API (DB-Library für C) ermöglicht einer Anwendung die Installation von Rückruf Fehlerbehandlung und Nachrichten Behandlung, die Fehler oder Meldungen zurückgeben. Einige [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen, wie PRINT, RAISERROR, DBCC und SET, geben ihre Ergebnisse an die Meldungshandlerfunktion der DB-Library anstatt an ein Resultset zurück. Jedoch verfügt die ODBC-API über keine solche Rückruffähigkeit. Wenn der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber die von zurückgegebenen Nachrichten erkennt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , wird der ODBC-Rückgabecode auf SQL_SUCCESS_WITH_INFO oder SQL_ERROR festgelegt, und die Nachricht wird als mindestens ein Diagnosedaten Satz zurückgegeben. Daher muss eine ODBC-Anwendung diese Rückgabecodes sorgfältig testen und **SQLGetDiagRec** aufrufen, um Nachrichten Daten abzurufen.  
  
 Informationen zur Ablaufverfolgung von Fehlern finden Sie unter [Data Access Tracing (Ablaufverfolgung für den Datenzugriff)](https://go.microsoft.com/fwlink/?LinkId=125805). Informationen zu Verbesserungen der in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] hinzugefügten Fehlerablaufverfolgung finden Sie unter [Zugreifen auf Diagnoseinformationen im Protokoll der erweiterten Ereignisse](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Verarbeiten von Anweisungen, die Meldungen generieren](processing-statements-that-generate-messages.md)  
  
-   [Diagnosedatensätze und -felder](diagnostic-records-and-fields.md)  
  
-   [Systemeigene Fehlernummern](native-error-numbers.md)  
  
-   [SQLSTATE &#40;ODBC-Fehler Codes&#41;](sqlstate-odbc-error-codes.md)  
  
-   [Fehlermeldungen](error-messages.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md)  
  
  
