---
title: SQL Server Native Client (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLNCLI, ODBC
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- data access [SQL Server Native Client], ODBC
- SQL Server Native Client ODBC driver
- ODBC
- SQL Server Native Client, ODBC
- ODBC, about SQL Server Native Client ODBC driver
ms.assetid: 811d5ba3-a2b8-48c0-adbc-8c91f041f458
author: rothja
ms.author: jroth
ms.openlocfilehash: 16c73966e318ed1e7d326fa77f56195ebbd830df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718076"
---
# <a name="sql-server-native-client-odbc"></a>SQL Server Native Client (ODBC)
  ODBC ist eine Standarddefinition einer API (Application Programming Interface, Schnittstelle für Anwendungsprogrammierung), die für den Zugriff auf Daten in relationalen oder ISAM-Datenbanken (Indexed Sequential Access Method, indizierte sequenzielle Zugriffsmethode) verwendet wird. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterstützt ODBC (über den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber) als eine der systemeigenen APIs für das Schreiben von C- und C++-Anwendungen, die mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] kommunizieren.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Programme, die mithilfe des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treibers geschrieben wurden, kommunizieren mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] über Funktionsaufrufe in C. Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -spezifischen Versionen der ODBC-Funktionen werden im [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber implementiert. Der Treiber übergibt SQL-Anweisungen an [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] und gibt die Ergebnisse der Anweisungen an die Anwendung zurück.  
  
 Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber entspricht der Spezifikation für Microsoft Win32 ODBC 3.51. Der Treiber unterstützt Anwendungen, die mit früheren Versionen von ODBC gemäß ODBC 3.51-Spezifikation geschrieben wurden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Datenquellennamen und 64-Bit-Betriebssysteme](data-source-names-and-64-bit-operating-systems.md)  
  
-   [Erstellen einer SQL Server Native Client-ODBC-Treiberanwendung](creating-a-driver-application.md)  
  
-   [Kommunikation mit SQL Server &#40;ODBC-&#41;](../../native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
-   [Ausführen von Abfragen &#40;ODBC-&#41;](../../native-client-odbc-queries/executing-queries-odbc.md)  
  
-   [Verarbeitungsergebnisse &#40;ODBC-&#41;](../../native-client-odbc-results/processing-results-odbc.md)  
  
-   [Verwenden von Cursorn &#40;ODBC-&#41;](../../native-client-odbc-cursors/using-cursors-odbc.md)  
  
-   [Ausführen von Transaktionen &#40;ODBC-&#41;](../../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
-   [Behandlung von Fehlern und Meldungen](../../native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
-   [Ausführen gespeicherter Prozeduren](../../native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
-   [Verwenden von Katalogfunktionen](using-catalog-functions.md)  
  
-   [Ausführen von Massen Kopier Vorgängen &#40;ODBC-&#41;](../../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
-   [Verwalten von Text und Imagespalten](../../native-client-odbc-text-image-columns/managing-text-and-image-columns.md)  
  
-   [Leistungsprofilerstellung des ODBC-Treibers](profiling-odbc-driver-performance.md)  
  
-   [Tabellenwert Parameter &#40;ODBC-&#41;](../../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
-   [Datums-und Uhrzeit Verbesserungen &#40;ODBC-&#41;](../../native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
-   [Große benutzerdefinierte CLR-Typen &#40;ODBC-&#41;](large-clr-user-defined-types-odbc.md)  
  
-   [FILESTREAM-Unterstützung &#40;ODBC-&#41;](filestream-support-odbc.md)  
  
-   [Dienstprinzipalnamen (SPN) in Clientverbindungen (ODBC)](service-principal-names-spns-in-client-connections-odbc.md)  
  
-   [Unterstützung für sparsespalten &#40;ODBC-&#41;](sparse-columns-support-odbc.md)  
  
-   [SQL Server Native Client &#40;ODBC-&#41; Referenz](../../../database-engine/dev-guide/sql-server-native-client-odbc-reference.md)  
  
-   [ODBC How-to Topics](../../native-client-odbc-how-to/odbc-how-to-topics.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client Programmierung](../sql-server-native-client-programming.md)   
 [Installieren von SQL Server Native Client](../applications/installing-sql-server-native-client.md)  
  
  
