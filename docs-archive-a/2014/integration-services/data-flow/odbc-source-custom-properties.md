---
title: Benutzerdefinierte Eigenschaften der ODBC-Quelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 362bbcd8-b7b0-4bab-8afe-1212b2ad1af9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f828bbf5394a2474aaa9367f9c31ab66941564a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615484"
---
# <a name="odbc-source-custom-properties"></a><span data-ttu-id="cbf21-102">ODBC Source Custom Properties</span><span class="sxs-lookup"><span data-stu-id="cbf21-102">ODBC Source Custom Properties</span></span>
  <span data-ttu-id="cbf21-103">In der folgenden Tabelle werden die benutzerdefinierten Eigenschaften der ODBC-Quelle beschrieben.</span><span class="sxs-lookup"><span data-stu-id="cbf21-103">The following table describes the custom properties of the ODBC source.</span></span> <span data-ttu-id="cbf21-104">Alle Eigenschaften können über SSIS-Eigenschaftsausdrücke festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="cbf21-104">All properties can be set from SSIS property expressions.</span></span>  
  
|<span data-ttu-id="cbf21-105">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="cbf21-105">Property name</span></span>|<span data-ttu-id="cbf21-106">Datentyp</span><span class="sxs-lookup"><span data-stu-id="cbf21-106">Data Type</span></span>|<span data-ttu-id="cbf21-107">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="cbf21-107">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="cbf21-108">Verbindung</span><span class="sxs-lookup"><span data-stu-id="cbf21-108">Connection</span></span>|<span data-ttu-id="cbf21-109">ODBC-Verbindung</span><span class="sxs-lookup"><span data-stu-id="cbf21-109">ODBC Connection</span></span>|<span data-ttu-id="cbf21-110">Eine ODBC-Verbindung für den Zugriff auf die Quelldatenbank.</span><span class="sxs-lookup"><span data-stu-id="cbf21-110">An ODBC connection to access the source database.</span></span>|  
|<span data-ttu-id="cbf21-111">AccessMode</span><span class="sxs-lookup"><span data-stu-id="cbf21-111">AccessMode</span></span>|<span data-ttu-id="cbf21-112">Ganze Zahl (Enumeration)</span><span class="sxs-lookup"><span data-stu-id="cbf21-112">Integer (enumeration)</span></span>|<span data-ttu-id="cbf21-113">Der zum Zugreifen auf die Datenbank verwendete Modus.</span><span class="sxs-lookup"><span data-stu-id="cbf21-113">The mode used to access the database.</span></span> <span data-ttu-id="cbf21-114">Die möglichen Werte sind der Tabellenname (0) und der SQL-Befehl (1).</span><span class="sxs-lookup"><span data-stu-id="cbf21-114">The possible values are Table Name (0) and SQL Command (1).</span></span><br /><br /> <span data-ttu-id="cbf21-115">Die Standardeinstellung ist der Tabellenname (0).</span><span class="sxs-lookup"><span data-stu-id="cbf21-115">The default is Table Name (0).</span></span>|  
|<span data-ttu-id="cbf21-116">BatchSize</span><span class="sxs-lookup"><span data-stu-id="cbf21-116">BatchSize</span></span>|<span data-ttu-id="cbf21-117">Integer</span><span class="sxs-lookup"><span data-stu-id="cbf21-117">Integer</span></span>|<span data-ttu-id="cbf21-118">Die Größe des Batches für die Massenextrahierung.</span><span class="sxs-lookup"><span data-stu-id="cbf21-118">The size of the batch for bulk extraction.</span></span> <span data-ttu-id="cbf21-119">Dies ist die Anzahl der als Array extrahierten Datensätze.</span><span class="sxs-lookup"><span data-stu-id="cbf21-119">This is the number of records extracted as an array.</span></span> <span data-ttu-id="cbf21-120">Wenn der ausgewählte ODBC-Anbieter keine Arrays unterstützt, beträgt die Batchgröße 1.</span><span class="sxs-lookup"><span data-stu-id="cbf21-120">If the selected ODBC provider does not support arrays, the batch size is 1.</span></span>|  
|<span data-ttu-id="cbf21-121">BindCharColumnAs</span><span class="sxs-lookup"><span data-stu-id="cbf21-121">BindCharColumnAs</span></span>|<span data-ttu-id="cbf21-122">Ganze Zahl (Enumeration)</span><span class="sxs-lookup"><span data-stu-id="cbf21-122">Integer (enumeration)</span></span>|<span data-ttu-id="cbf21-123">Diese Eigenschaft bestimmt, wie die ODBC-Quelle Spalten an Zeichenfolgentypen mit mehreren Byte bindet, z. B. SQL_CHAR, SQL_VARCHAR oder SQL_LONGVARCHAR.</span><span class="sxs-lookup"><span data-stu-id="cbf21-123">This property determines how the ODBC source binds columns with multiple-byte string types such as SQL_CHAR, SQL_VARCHAR, or SQL_LONGVARCHAR.</span></span><br /><br /> <span data-ttu-id="cbf21-124">Die möglichen Werte sind Unicode (0), wobei die Spalten als SQL_C_WCHAR gebunden werden, und ANSI (1), wobei die Spalten als SQL_C_CHAR gebunden werden.</span><span class="sxs-lookup"><span data-stu-id="cbf21-124">The possible values are Unicode (0), which binds the columns as SQL_C_WCHAR, and ANSI (1), which binds the columns as SQL_C_CHAR).</span></span> <span data-ttu-id="cbf21-125">Der Standardwert ist Unicode (0).</span><span class="sxs-lookup"><span data-stu-id="cbf21-125">The default is Unicode (0).</span></span><br /><br /> <span data-ttu-id="cbf21-126">**Hinweis**: Diese Eigenschaft ist im **Quellen-Editor für ODBC**nicht verfügbar, kann jedoch mit dem **Erweiterten Editor**festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="cbf21-126">**Note**: This property is not available in the **ODBC Source Editor**, but can be set by using the **Advanced Editor**.</span></span>|  
|<span data-ttu-id="cbf21-127">BindNumericAs</span><span class="sxs-lookup"><span data-stu-id="cbf21-127">BindNumericAs</span></span>|<span data-ttu-id="cbf21-128">Ganze Zahl (Enumeration)</span><span class="sxs-lookup"><span data-stu-id="cbf21-128">Integer (enumeration)</span></span>|<span data-ttu-id="cbf21-129">Diese Eigenschaft bestimmt, wie die ODBC-Quelle Spalten mit numerischen Daten an die Datentypen SQL_TYPE_NUMERIC und SQL_TYPE_DECIMAL bindet.</span><span class="sxs-lookup"><span data-stu-id="cbf21-129">This property determines how the ODBC source binds columns with numeric data with data types SQL_TYPE_NUMERIC and SQL_TYPE_DECIMAL.</span></span><br /><br /> <span data-ttu-id="cbf21-130">Die möglichen Optionen sind Char (0), wobei die Spalten als SQL_C_CHAR gebunden werden, und Numeric (1), wobei die Spalten als SQL_C_NUMERIC gebunden werden.</span><span class="sxs-lookup"><span data-stu-id="cbf21-130">The possible options are Char (0), which binds the columns as SQL_C_CHAR and Numeric (1), which binds the columns as SQL_C_NUMERIC.</span></span> <span data-ttu-id="cbf21-131">Der Standardwert ist Char (0).</span><span class="sxs-lookup"><span data-stu-id="cbf21-131">The default value is Char (0).</span></span><br /><br /> <span data-ttu-id="cbf21-132">**Hinweis**: Diese Eigenschaft ist im **Quellen-Editor für ODBC**nicht verfügbar, kann jedoch mit dem **Erweiterten Editor**festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="cbf21-132">**Note**: This property is not available in the **ODBC Source Editor**, but can be set by using the **Advanced Editor**.</span></span>|  
|<span data-ttu-id="cbf21-133">DefaultCodePage</span><span class="sxs-lookup"><span data-stu-id="cbf21-133">DefaultCodePage</span></span>|<span data-ttu-id="cbf21-134">Integer</span><span class="sxs-lookup"><span data-stu-id="cbf21-134">Integer</span></span>|<span data-ttu-id="cbf21-135">Die Codepage, die für Zeichenfolgen-Ausgabespalten verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="cbf21-135">The code page to use for string output columns.</span></span><br /><br /> <span data-ttu-id="cbf21-136">**Hinweis**: Diese Eigenschaft ist im **Quellen-Editor für ODBC**nicht verfügbar, kann jedoch mit dem **Erweiterten Editor**festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="cbf21-136">**Note**: This property is not available in the **ODBC Source Editor**, but can be set by using the **Advanced Editor**.</span></span>|  
|<span data-ttu-id="cbf21-137">ExposeCharColumnsAsUnicode</span><span class="sxs-lookup"><span data-stu-id="cbf21-137">ExposeCharColumnsAsUnicode</span></span>|<span data-ttu-id="cbf21-138">Boolean</span><span class="sxs-lookup"><span data-stu-id="cbf21-138">Boolean</span></span>|<span data-ttu-id="cbf21-139">Diese Eigenschaft bestimmt, wie die Komponente CHAR-Spalten verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="cbf21-139">This property determines how the component exposes CHAR columns.</span></span> <span data-ttu-id="cbf21-140">Der Standardwert ist False. Dieser Wert gibt an, dass CHAR-Spalten als Multibyte-Zeichenfolgen (DT_STR) verfügbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="cbf21-140">The default value is False, which indicates that CHAR columns are exposed as multi-byte strings (DT_STR).</span></span> <span data-ttu-id="cbf21-141">Wenn True gilt, werden CHAR-Spalten als breite Zeichenfolgen (DT_WSTR) verfügbar gemacht.</span><span class="sxs-lookup"><span data-stu-id="cbf21-141">If True, CHAR columns are exposed as wide strings (DT_WSTR).</span></span><br /><br /> <span data-ttu-id="cbf21-142">**Hinweis**: Diese Eigenschaft ist im **Quellen-Editor für ODBC**nicht verfügbar, kann jedoch mit dem **Erweiterten Editor**festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="cbf21-142">**Note**: This property is not available in the **ODBC Source Editor**, but can be set by using the **Advanced Editor**.</span></span>|  
|<span data-ttu-id="cbf21-143">FetchMethod</span><span class="sxs-lookup"><span data-stu-id="cbf21-143">FetchMethod</span></span>|<span data-ttu-id="cbf21-144">Ganze Zahl (Enumeration)</span><span class="sxs-lookup"><span data-stu-id="cbf21-144">Integer (enumeration)</span></span>|<span data-ttu-id="cbf21-145">Die Methode, die zum Abrufen der Daten verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="cbf21-145">The method used for getting the data.</span></span> <span data-ttu-id="cbf21-146">Die möglichen Optionen sind Zeile für Zeile (0) und Batch (1).</span><span class="sxs-lookup"><span data-stu-id="cbf21-146">The possible options are Row by row (0) and Batch (1).</span></span> <span data-ttu-id="cbf21-147">Der Standardwert ist Batch (1).</span><span class="sxs-lookup"><span data-stu-id="cbf21-147">The default value is Batch (1).</span></span><br /><br /> <span data-ttu-id="cbf21-148">Weitere Informationen zu diesen Optionen finden Sie unter [ODBC Source](odbc-source.md).</span><span class="sxs-lookup"><span data-stu-id="cbf21-148">For more information about these options, see [ODBC Source](odbc-source.md).</span></span><br /><br /> <span data-ttu-id="cbf21-149">**Hinweis**: Diese Eigenschaft ist im **Quellen-Editor für ODBC**nicht verfügbar, kann jedoch mit dem **Erweiterten Editor**festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="cbf21-149">**Note**: This property is not available in the **ODBC Source Editor**, but can be set by using the **Advanced Editor**.</span></span>|  
|<span data-ttu-id="cbf21-150">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="cbf21-150">SqlCommand</span></span>|<span data-ttu-id="cbf21-151">String</span><span class="sxs-lookup"><span data-stu-id="cbf21-151">String</span></span>|<span data-ttu-id="cbf21-152">Der SQL-Befehl, der ausgeführt werden soll, wenn AccessMode auf SQL-Befehl festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="cbf21-152">The SQL command to be executed when AccessMode is set to SQL Command.</span></span>|  
|<span data-ttu-id="cbf21-153">StatementTimeout</span><span class="sxs-lookup"><span data-stu-id="cbf21-153">StatementTimeout</span></span>|<span data-ttu-id="cbf21-154">Integer</span><span class="sxs-lookup"><span data-stu-id="cbf21-154">Integer</span></span>|<span data-ttu-id="cbf21-155">Die Anzahl der Sekunden, wie lange auf die Ausführung einer SQL-Anweisung gewartet wird, bevor – mit einem Fehler – zur Anwendung zurückgekehrt wird.</span><span class="sxs-lookup"><span data-stu-id="cbf21-155">The number of seconds to wait for an SQL statement to execute before returning, with an error, to the application.</span></span> <span data-ttu-id="cbf21-156">Der Standardwert ist 0.</span><span class="sxs-lookup"><span data-stu-id="cbf21-156">The default value is 0.</span></span> <span data-ttu-id="cbf21-157">Der Wert 0 gibt an, dass für das System kein Timeout verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="cbf21-157">A value of 0 indicates that the system does not time out.</span></span>|  
|<span data-ttu-id="cbf21-158">TableName</span><span class="sxs-lookup"><span data-stu-id="cbf21-158">TableName</span></span>|<span data-ttu-id="cbf21-159">String</span><span class="sxs-lookup"><span data-stu-id="cbf21-159">String</span></span>|<span data-ttu-id="cbf21-160">Der Name der Tabelle mit den Daten, die verwendet werden, wenn AccessMode auf Tabellenname festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="cbf21-160">The name of the table with the data that is being used when AccessMode is set to Table Name.</span></span>|  
|<span data-ttu-id="cbf21-161">LobChunckSize</span><span class="sxs-lookup"><span data-stu-id="cbf21-161">LobChunckSize</span></span>|<span data-ttu-id="cbf21-162">Integer</span><span class="sxs-lookup"><span data-stu-id="cbf21-162">Integer</span></span>|<span data-ttu-id="cbf21-163">Die Segmentgrößenzuordnung für LOB-Spalten.</span><span class="sxs-lookup"><span data-stu-id="cbf21-163">The chunk size allocation for LOB columns.</span></span>|  
||||  
  
## <a name="see-also"></a><span data-ttu-id="cbf21-164">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="cbf21-164">See Also</span></span>  
 <span data-ttu-id="cbf21-165">[ODBC Source](odbc-source.md) </span><span class="sxs-lookup"><span data-stu-id="cbf21-165">[ODBC Source](odbc-source.md) </span></span>  
 [<span data-ttu-id="cbf21-166">Quellen-Editor für ODBC &#40;Seite „Verbindungs-Manager“&#41;</span><span class="sxs-lookup"><span data-stu-id="cbf21-166">ODBC Source Editor &#40;Connection Manager Page&#41;</span></span>](../odbc-source-editor-connection-manager-page.md)  
  
  