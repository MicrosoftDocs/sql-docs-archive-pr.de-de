---
title: SQL Server Native Client Features | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- MDAC [SQL Server]
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- SQLNCLI, about SQL Server Native Client
- data access [SQL Server Native Client], features
ms.assetid: 7bb32865-5afb-41ab-98b4-3fa545ee8953
author: rothja
ms.author: jroth
ms.openlocfilehash: bb4ba07f84848f754519f8f4fa1c3e56485e85a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615364"
---
# <a name="sql-server-native-client-features"></a><span data-ttu-id="5705d-102">SQL Server Native Client-Funktionen</span><span class="sxs-lookup"><span data-stu-id="5705d-102">SQL Server Native Client Features</span></span>
  <span data-ttu-id="5705d-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client macht nicht nur Funktionen der Windows (früher Microsoft) Data Access Components (WDAC) verfügbar, sondern implementiert zudem viele weitere Funktionen, um die Funktionalität von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verfügbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="5705d-103">In addition to exposing features of the Windows (formerly Microsoft) Data Access Components (WDAC), [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client also implements many other features to expose [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] functionality.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5705d-104">In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="5705d-104">In This Section</span></span>  
 [<span data-ttu-id="5705d-105">Verhaltensänderungen des ODBC-Treibers bei der Behandlung von Zeichenkonvertierungen</span><span class="sxs-lookup"><span data-stu-id="5705d-105">ODBC Driver Behavior Change When Handling Character Conversions</span></span>](odbc-driver-behavior-change-when-handling-character-conversions.md)  
 <span data-ttu-id="5705d-106">Erläutert das geänderte Verhalten ab [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2012 Native Client.</span><span class="sxs-lookup"><span data-stu-id="5705d-106">Discusses a change of behavior beginning in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2012 Native Client.</span></span>  
  
 [<span data-ttu-id="5705d-107">Verwenden der Datenbankspiegelung</span><span class="sxs-lookup"><span data-stu-id="5705d-107">Using Database Mirroring</span></span>](using-database-mirroring.md)  
 <span data-ttu-id="5705d-108">Erläutert [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , wie Native Client die Verwendung von gespiegelten Datenbanken unterstützt. Dies ist die Möglichkeit, eine Kopie oder Spiegelung einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Datenbank auf einem Standbyserver zu speichern.</span><span class="sxs-lookup"><span data-stu-id="5705d-108">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports the use of mirrored databases, which is the ability to keep a copy, or mirror, of a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database on a standby server.</span></span>  
  
 [<span data-ttu-id="5705d-109">Ausführen asynchroner Vorgänge</span><span class="sxs-lookup"><span data-stu-id="5705d-109">Performing Asynchronous Operations</span></span>](performing-asynchronous-operations.md)  
 <span data-ttu-id="5705d-110">Erläutert, auf welche Weise [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client asynchrone Vorgänge unterstützt. Das ist die Fähigkeit, Rückgaben unverzüglich zu übermitteln, ohne den aufrufenden Thread zu blockieren.</span><span class="sxs-lookup"><span data-stu-id="5705d-110">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports asynchronous operations, which is the ability to return immediately without blocking on the calling thread.</span></span>  
  
 [<span data-ttu-id="5705d-111">Verwenden von Multiple Active Result Sets &#40;MARS&#41;</span><span class="sxs-lookup"><span data-stu-id="5705d-111">Using Multiple Active Result Sets &#40;MARS&#41;</span></span>](using-multiple-active-result-sets-mars.md)  
 <span data-ttu-id="5705d-112">Erläutert, auf welche Weise [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client Multiple Active Result Sets (MARS) unterstützt.</span><span class="sxs-lookup"><span data-stu-id="5705d-112">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports multiple active result sets (MARS).</span></span> <span data-ttu-id="5705d-113">MARS ermöglichen es Ihnen, mehrere Resultsets mithilfe einer einzigen Datenbankverbindung auszuführen und zu empfangen.</span><span class="sxs-lookup"><span data-stu-id="5705d-113">MARS enables you to execute and receive multiple result sets using a single database connection</span></span>  
  
 [<span data-ttu-id="5705d-114">Using XML Data Types (Verwenden von XML-Datentypen)</span><span class="sxs-lookup"><span data-stu-id="5705d-114">Using XML Data Types</span></span>](using-xml-data-types.md)  
 <span data-ttu-id="5705d-115">Erläutert, auf welche Weise [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client den XML-Datentyp unterstützt. Dieser XML-basierte Datentyp kann als Spaltentyp, Variablentyp, Parametertyp oder Funktionsrückgabetyp verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5705d-115">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports the XML data type, which is a XML-based data type that can be used as a column type, variable type, parameter type, or function return type.</span></span>  
  
 [<span data-ttu-id="5705d-116">Verwenden von benutzerdefinierten Typen</span><span class="sxs-lookup"><span data-stu-id="5705d-116">Using User-Defined Types</span></span>](using-user-defined-types.md)  
 <span data-ttu-id="5705d-117">Erläutert [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , wie Native Client benutzerdefinierte Typen (User-Defined Types, UDT) unterstützt, die das SQL-Typsystem erweitern, indem Sie Objekte und benutzerdefinierte Datenstrukturen in einer-Datenbank speichern können [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5705d-117">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports User-Defined Types (UDT), which extends the SQL type system by allowing you to store objects and custom data structures in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.</span></span>  
  
 [<span data-ttu-id="5705d-118">Verwenden von Datentypen mit umfangreichen Werten</span><span class="sxs-lookup"><span data-stu-id="5705d-118">Using Large Value Types</span></span>](using-large-value-types.md)  
 <span data-ttu-id="5705d-119">Erläutert, auf welche Weise [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client Datentypen mit großen Werten unterstützt, bei denen es sich um LOB-Datentypen handelt.</span><span class="sxs-lookup"><span data-stu-id="5705d-119">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports large value data types, which are large object data types (LOB).</span></span>  
  
 [<span data-ttu-id="5705d-120">Programmgesteuertes Ändern von Kennwörtern</span><span class="sxs-lookup"><span data-stu-id="5705d-120">Changing Passwords Programmatically</span></span>](changing-passwords-programmatically.md)  
 <span data-ttu-id="5705d-121">Erläutert, auf welche Weise [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client die Handhabung abgelaufener Kennwörter unterstützt und es ermöglicht, dass Kennwörter jetzt auf dem Client ohne Eingreifen eines Administrators geändert werden können.</span><span class="sxs-lookup"><span data-stu-id="5705d-121">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports the handling of expired passwords so that passwords can now be changed on the client without administrator involvement.</span></span>  
  
 [<span data-ttu-id="5705d-122">Arbeiten mit der Momentaufnahme Isolation</span><span class="sxs-lookup"><span data-stu-id="5705d-122">Working with Snapshot Isolation</span></span>](working-with-snapshot-isolation.md)  
 <span data-ttu-id="5705d-123">Erläutert, auf welche Weise [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client die Verbesserung der Zeilenversionsverwaltung unterstützt. Sie erhöht die Datenbankleistung, indem Leser-/Schreiberblockierungsszenarien vermieden werden.</span><span class="sxs-lookup"><span data-stu-id="5705d-123">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports the enhancement to row versioning that improves database performance by avoiding reader-writer blocking scenarios.</span></span>  
  
 [<span data-ttu-id="5705d-124">Arbeiten mit Abfragebenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="5705d-124">Working with Query Notifications</span></span>](working-with-query-notifications.md)  
 <span data-ttu-id="5705d-125">Erläutert, auf welche Weise [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client die Benachrichtigung von Consumern bei Rowsetänderungen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="5705d-125">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports consumer notification on rowset modification.</span></span>  
  
 [<span data-ttu-id="5705d-126">Durchführen von Massenkopiervorgängen</span><span class="sxs-lookup"><span data-stu-id="5705d-126">Performing Bulk Copy Operations</span></span>](performing-bulk-copy-operations.md)  
 <span data-ttu-id="5705d-127">Erläutert [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , wie Native Client Massen Kopiervorgänge unterstützt, mit denen große Datenmengen in eine oder aus einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Tabelle oder Sicht übertragen werden können.</span><span class="sxs-lookup"><span data-stu-id="5705d-127">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports bulk copy operations that allow the transfer of large amounts of data into or out of a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] table or view.</span></span>  
  
 [<span data-ttu-id="5705d-128">Verwenden von Verschlüsselung ohne Überprüfung</span><span class="sxs-lookup"><span data-stu-id="5705d-128">Using Encryption Without Validation</span></span>](using-encryption-without-validation.md)  
 <span data-ttu-id="5705d-129">Erläutert, wie [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client zur Verschlüsselung an den Server gesendeter Daten ohne Prüfung des Zertifikats verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="5705d-129">Discusses how to use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client to encrypt data sent to the server without validating the certificate.</span></span>  
  
 [<span data-ttu-id="5705d-130">Tabellenwert Parameter &#40;SQL Server Native Client&#41;</span><span class="sxs-lookup"><span data-stu-id="5705d-130">Table-Valued Parameters &#40;SQL Server Native Client&#41;</span></span>](table-valued-parameters-sql-server-native-client.md)  
 <span data-ttu-id="5705d-131">Erläutert, auf welche Weise [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client die Tabellenwertparameter unterstützt.</span><span class="sxs-lookup"><span data-stu-id="5705d-131">Discusses [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client support for the table-valued parameters.</span></span>  
  
 [<span data-ttu-id="5705d-132">Große benutzerdefinierte CLR-Typen</span><span class="sxs-lookup"><span data-stu-id="5705d-132">Large CLR User-Defined Types</span></span>](../../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
 <span data-ttu-id="5705d-133">Erläutert die Unterstützung für große CLR-benutzerdefinierte Typen (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="5705d-133">Discusses support for large common language runtime (CLR) user-defined types (UDTs).</span></span>  
  
 [<span data-ttu-id="5705d-134">FILESTREAM-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="5705d-134">FILESTREAM Support</span></span>](filestream-support.md)  
 <span data-ttu-id="5705d-135">Erläutert [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] die Native Client-Unterstützung für die erweiterte FILESTREAM-Funktion.</span><span class="sxs-lookup"><span data-stu-id="5705d-135">Discusses [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client support for the enhanced FILESTREAM feature.</span></span>  
  
 [<span data-ttu-id="5705d-136">Unterstützung von Dienstprinzipalnamen &#40;SPN&#41; in Clientverbindungen</span><span class="sxs-lookup"><span data-stu-id="5705d-136">Service Principal Name &#40;SPN&#41; Support in Client Connections</span></span>](service-principal-name-spn-support-in-client-connections.md)  
 <span data-ttu-id="5705d-137">Erläutert, auf welche Weise die Unterstützung für Dienstprinzipalnamen (Service Principal Names, SPN) erweitert wurde, damit die gegenseitige Authentifizierung über alle Protokolle hinweg möglich ist.</span><span class="sxs-lookup"><span data-stu-id="5705d-137">Discusses how support for service principal names (SPNs) has been extended to enable mutual authentication across all protocols.</span></span>  
  
 [<span data-ttu-id="5705d-138">Unterstützung für Spalten mit geringer Dichte in SQL Server Native Client</span><span class="sxs-lookup"><span data-stu-id="5705d-138">Sparse Columns Support in SQL Server Native Client</span></span>](sparse-columns-support-in-sql-server-native-client.md)  
 <span data-ttu-id="5705d-139">Erläutert, auf welche Weise [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client Sparsespalten unterstützt.</span><span class="sxs-lookup"><span data-stu-id="5705d-139">Discusses [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client support for sparse columns.</span></span>  
  
 [<span data-ttu-id="5705d-140">Verbesserungen bei Datum und Uhrzeit</span><span class="sxs-lookup"><span data-stu-id="5705d-140">Date and Time Improvements</span></span>](date-and-time-improvements.md)  
 <span data-ttu-id="5705d-141">Erläutert die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client hinzugefügte Unterstützung für die Datums- und Uhrzeitdatentypen.</span><span class="sxs-lookup"><span data-stu-id="5705d-141">Discusses support added to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client for the date and time data types.</span></span>  
  
 [<span data-ttu-id="5705d-142">Metadatenermittlung</span><span class="sxs-lookup"><span data-stu-id="5705d-142">Metadata Discovery</span></span>](metadata-discovery.md)  
 <span data-ttu-id="5705d-143">Erläutert Verbesserungen der Metadatenermittlung in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5705d-143">Discusses metadata discovery improvements that were made in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].</span></span>  
  
 [<span data-ttu-id="5705d-144">Unterstützung für UTF-16 in SQL Server Native Client 11.0</span><span class="sxs-lookup"><span data-stu-id="5705d-144">UTF-16 Support in SQL Server Native Client 11.0</span></span>](utf-16-support-in-sql-server-native-client-11-0.md)  
 <span data-ttu-id="5705d-145">Erläutert eine mit [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] eingeführte Verhaltensänderung.</span><span class="sxs-lookup"><span data-stu-id="5705d-145">Discusses a behavior change introduced in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].</span></span> <span data-ttu-id="5705d-146">Ab [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client wird dem Puffer kein hoher Ersatzzeichencodepunkt hinzugefügt, wenn Sie beim Binden eines Spaltenergebnisses oder Ausgabeparameters einen Puffer fester Länge übergeben und das vor dem abschließenden Zeichen in den Puffer geschriebene `wchar`-Zeichen ein hoher Ersatzzeichencodepunkt eines Ersatzzeichenpaars und das nächste `wchar`-Zeichen ein niedriger Ersatzzeichencodepunkt ist.</span><span class="sxs-lookup"><span data-stu-id="5705d-146">If you supply a fixed-length buffer when binding a column result or output parameter and if the `wchar` character written into the buffer before the terminating character is a high surrogate code point of a surrogate pair, and if the next `wchar` character is a low surrogate code point, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client will not add the high surrogate code point to the buffer.</span></span>  
  
 [<span data-ttu-id="5705d-147">SQL Server Native Client-Unterstützung für hohe Verfügbarkeit, Notfallwiederherstellung</span><span class="sxs-lookup"><span data-stu-id="5705d-147">SQL Server Native Client Support for High Availability, Disaster Recovery</span></span>](sql-server-native-client-support-for-high-availability-disaster-recovery.md)  
 <span data-ttu-id="5705d-148">Erläutert, wie die Anwendung konfiguriert werden kann, um von den Funktionen für Hochverfügbarkeit und Notfallwiederherstellung zu profitieren, die in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] hinzugefügt wurden.</span><span class="sxs-lookup"><span data-stu-id="5705d-148">Discusses how your application can be configured to take advantage of the high-availability, disaster recovery features added in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].</span></span>  
  
 [<span data-ttu-id="5705d-149">Zugreifen auf Diagnoseinformationen im Protokoll der erweiterten Ereignisse</span><span class="sxs-lookup"><span data-stu-id="5705d-149">Accessing Diagnostic Information in the Extended Events Log</span></span>](accessing-diagnostic-information-in-the-extended-events-log.md)  
 <span data-ttu-id="5705d-150">Erläutert Erweiterungen zu [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client und -Datenablaufverfolgung, die Ihnen Zugriff auf Diagnoseinformationen im Ringpuffer und XEvents-Protokoll geben.</span><span class="sxs-lookup"><span data-stu-id="5705d-150">Discusses enhancements to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client and data tracing that gives you access to diagnostic information in the ring buffer and XEvents log.</span></span>  
  
 [<span data-ttu-id="5705d-151">SQL Server Native Client-Unterstützung für LocalDB</span><span class="sxs-lookup"><span data-stu-id="5705d-151">SQL Server Native Client Support for LocalDB</span></span>](sql-server-native-client-support-for-localdb.md)  
 <span data-ttu-id="5705d-152">Erläutert, auf welche Weise [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client die verbesserte LocalDB-Funktion unterstützt.</span><span class="sxs-lookup"><span data-stu-id="5705d-152">Discusses [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client support for the LocalDB feature.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5705d-153">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5705d-153">See Also</span></span>  
 <span data-ttu-id="5705d-154">[SQL Server Native Client Programmierung](../sql-server-native-client-programming.md) </span><span class="sxs-lookup"><span data-stu-id="5705d-154">[SQL Server Native Client Programming](../sql-server-native-client-programming.md) </span></span>  
 <span data-ttu-id="5705d-155">[ODBC-Themen zur Vorgehensweise](../../native-client-odbc-how-to/odbc-how-to-topics.md) </span><span class="sxs-lookup"><span data-stu-id="5705d-155">[ODBC How-to Topics](../../native-client-odbc-how-to/odbc-how-to-topics.md) </span></span>  
 <span data-ttu-id="5705d-156">[Gewusst-wie-Themen zu OLE DB](../../native-client-ole-db-how-to/ole-db-how-to-topics.md) </span><span class="sxs-lookup"><span data-stu-id="5705d-156">[OLE DB How-to Topics](../../native-client-ole-db-how-to/ole-db-how-to-topics.md) </span></span>  
 [<span data-ttu-id="5705d-157">Installieren von SQL Server Native Client</span><span class="sxs-lookup"><span data-stu-id="5705d-157">Installing SQL Server Native Client</span></span>](../applications/installing-sql-server-native-client.md)  
  
  