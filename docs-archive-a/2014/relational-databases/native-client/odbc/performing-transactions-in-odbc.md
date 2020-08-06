---
title: Transaktionen in ODBC | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, transactions
- transactions [ODBC]
- ODBC, transactions
ms.assetid: c5a87fa5-827a-4e6f-a0d9-924bac881eb0
author: rothja
ms.author: jroth
ms.openlocfilehash: 386b248edfdb6e0ac5eb97b3aeb6c0bbc505a5a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615352"
---
# <a name="transactions-in-odbc"></a><span data-ttu-id="d70b4-102">Transaktionen in ODBC</span><span class="sxs-lookup"><span data-stu-id="d70b4-102">Transactions in ODBC</span></span>
  <span data-ttu-id="d70b4-103">Transaktionen in ODBC werden auf der Verbindungsebene verwaltet.</span><span class="sxs-lookup"><span data-stu-id="d70b4-103">Transactions in ODBC are managed at the connection level.</span></span> <span data-ttu-id="d70b4-104">Wenn eine Anwendung eine Transaktion abschließt, führt sie für alle abgeschlossenen Arbeiten einen Commit oder Rollback über alle Anweisungshandles dieser Verbindung aus.</span><span class="sxs-lookup"><span data-stu-id="d70b4-104">When an application completes a transaction, it commits or rolls back all work completed through all statement handles on that connection.</span></span> <span data-ttu-id="d70b4-105">Anwendungen müssen zum Ausführen eines Commits oder eines Rollbacks für eine Transaktion keine COMMIT- oder ROLLBACK-Anweisung übermitteln, sondern [SQLEndTran](../../native-client-odbc-api/sqlendtran.md) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="d70b4-105">To commit or roll back a transaction, applications should call [SQLEndTran](../../native-client-odbc-api/sqlendtran.md) instead of submitting a COMMIT or ROLLBACK statement.</span></span>  
  
 <span data-ttu-id="d70b4-106">Eine Anwendung ruft [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) auf, um zwischen den beiden ODBC-Modi für die Verwaltung von Transaktionen zu wechseln:</span><span class="sxs-lookup"><span data-stu-id="d70b4-106">An application calls [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) to switch between the two ODBC modes of managing transactions:</span></span>  
  
-   <span data-ttu-id="d70b4-107">Autocommit-Modus</span><span class="sxs-lookup"><span data-stu-id="d70b4-107">Autocommit mode</span></span>  
  
     <span data-ttu-id="d70b4-108">Für jede erfolgreich ausgeführte Anweisung wird automatisch ein Commit ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="d70b4-108">Each statement is automatically committed when it is completed successfully.</span></span> <span data-ttu-id="d70b4-109">Im Autocommit-Modus sind keine anderen Funktionen für die Verwaltung von Transaktionen erforderlich.</span><span class="sxs-lookup"><span data-stu-id="d70b4-109">When you run in autocommit mode, no other transaction management functions are required.</span></span>  
  
-   <span data-ttu-id="d70b4-110">Manualcommit-Modus</span><span class="sxs-lookup"><span data-stu-id="d70b4-110">Manual-commit mode</span></span>  
  
     <span data-ttu-id="d70b4-111">Alle ausgeführten Anweisungen sind in einer Transaktion enthalten, bis diese durch Aufrufen von **SQLEndTran**ausdrücklich beendet wird.</span><span class="sxs-lookup"><span data-stu-id="d70b4-111">All executed statements are included in the same transaction until it is specifically stopped by calling **SQLEndTran**.</span></span>  
  
 <span data-ttu-id="d70b4-112">Der Autocommit-Modus ist der Standardtransaktionsmodus für ODBC.</span><span class="sxs-lookup"><span data-stu-id="d70b4-112">Autocommit mode is the default transaction mode for ODBC.</span></span> <span data-ttu-id="d70b4-113">Beim Herstellen einer Verbindung befindet sich diese zunächst im Autocommit-Modus, bis **SQLSetConnectAttr** aufgerufen wird, um durch Deaktivieren des Autocommit-Modus in den Manualcommit-Modus zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="d70b4-113">When a connection is made, it is in autocommit mode until **SQLSetConnectAttr** is called to switch to manual-commit mode by setting autocommit mode off.</span></span> <span data-ttu-id="d70b4-114">Wenn eine Anwendung Autocommit deaktiviert, startet die nächste an die Datenbank gesendete Anweisung eine Transaktion.</span><span class="sxs-lookup"><span data-stu-id="d70b4-114">When an application turns autocommit off, the next statement sent to the database starts a transaction.</span></span> <span data-ttu-id="d70b4-115">Die Transaktion bleibt dann so lange aktiv, bis die Anwendung **SQLEndTran** mit der Option SQL_COMMIT oder mit der Option SQL_ROLLBACK aufruft.</span><span class="sxs-lookup"><span data-stu-id="d70b4-115">The transaction then remains in effect until the application calls **SQLEndTran** with either the SQL_COMMIT or SQL_ROLLBACK options.</span></span> <span data-ttu-id="d70b4-116">Der Befehl, der an die Datenbank nach **SQLEndTran** gesendet wird, startet die nächste Transaktion.</span><span class="sxs-lookup"><span data-stu-id="d70b4-116">The command sent to the database after **SQLEndTran** starts the next transaction.</span></span>  
  
 <span data-ttu-id="d70b4-117">Wenn eine Anwendung vom Manualcommit- in den Autocommit-Modus wechselt, führt der Treiber für alle derzeit für die Verbindung geöffneten Transaktionen einen Commit aus.</span><span class="sxs-lookup"><span data-stu-id="d70b4-117">If an application switches from manual-commit to autocommit mode, the driver commits any transactions currently open on the connection.</span></span>  
  
 <span data-ttu-id="d70b4-118">ODBC-Anwendungen dürfen keine Transact-SQL-Transaktionsanweisungen, wie BEGIN TRANSACTION, COMMIT TRANSACTION oder ROLLBACK TRANSACTION, verwenden, da dies zu einem unbestimmten Verhalten des Treibers führen kann.</span><span class="sxs-lookup"><span data-stu-id="d70b4-118">ODBC applications should not use Transact-SQL transaction statements such as BEGIN TRANSACTION, COMMIT TRANSACTION, or ROLLBACK TRANSACTION because this can cause indeterminate behavior in the driver.</span></span> <span data-ttu-id="d70b4-119">Eine ODBC-Anwendung muss im Autocommit-Modus ausgeführt werden und darf keine Funktionen oder Anweisungen für die Verwaltung von Transaktionen verwenden oder im Manualcommit-Modus ausgeführt werden und die ODBC-Funktion **SQLEndTran** zum Ausführen eines Commits oder eines Rollbacks für Transaktionen verwenden.</span><span class="sxs-lookup"><span data-stu-id="d70b4-119">An ODBC application should run in autocommit mode and not use any transaction management functions or statements, or run in manual-commit mode and use the ODBC **SQLEndTran** function to either commit or roll back transactions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d70b4-120">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d70b4-120">See Also</span></span>  
 [<span data-ttu-id="d70b4-121">Ausführen von Transaktionen &#40;ODBC-&#41;</span><span class="sxs-lookup"><span data-stu-id="d70b4-121">Performing Transactions &#40;ODBC&#41;</span></span>](../../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
  