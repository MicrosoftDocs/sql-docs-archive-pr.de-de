---
title: Semantische Suche (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server]
- semantic search [SQL Server], overview
- statistical semantic search [SQL Server]
- statistical semantic search [SQL Server], overview
ms.assetid: cd8faa9d-07db-420d-93f4-a2ea7c974b97
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 91062864b77ba3c62a87d66b8ff93068f9c10c8c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719807"
---
# <a name="semantic-search-sql-server"></a>Semantische Suche (SQL Server)
  Die statistische semantische Suche liefert einen tiefen Einblick in unstrukturierte Dokumente, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbanken gespeichert sind, indem statistisch relevante *Schlüsselausdrücke*extrahiert und indiziert werden. Anschließend werden diese Schlüsselausdrücke verwendet, um *ähnliche oder verwandte Dokumente*zu identifizieren und zu indizieren.  
  
 Sie fragen diese semantischen Indizes mit drei Transact-SQL-Rowsetfunktionen ab, um die Ergebnisse als strukturierte Daten abzurufen.  
  
##  <a name="what-can-i-do-with-semantic-search"></a><a name="whatcanido"></a>Was kann ich mit der semantischen Suche tun?  
 Die semantische Suche basiert auf der vorhandenen Volltextsuchfunktion in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ermöglicht jedoch neue Szenarien, die über Schlüsselwortsuchen hinausgehen. Während Sie bei der Volltextsuche *Wörter* in einem Dokument abfragen können, können Sie bei der *semantischen* Suche die Bedeutung des Dokuments abfragen. Die jetzt möglichen Lösungen umfassen die automatische Tagextraktion, die Ermittlung von verwandten Inhalten sowie die hierarchische Navigation über ähnlichen Inhalt. Sie können beispielsweise den Index von Schlüsselausdrücken abfragen, um die Taxonomie für eine Organisation oder für einen Korpus von Dokumenten zu erstellen. Oder sie können den Dokumentähnlichkeitsindex abfragen, um Lebensläufe zu identifizieren, die einer Arbeitsplatzbeschreibung entsprechen.  
  
 In den folgenden Beispielen sind die Funktionen der semantischen Suche dargestellt.  
  
###  <a name="find-the-key-phrases-in-a-document"></a><a name="find1"></a>Suchen der Schlüssel Ausdrücke in einem Dokument  
 Die folgende Abfrage ruft die Schlüsselausdrücke ab, die im Beispieldokument identifiziert wurden. Sie präsentiert die Ergebnisse in absteigender Reihenfolge nach dem Grad der statistischen Bedeutung der einzelnen Schlüsselausdrücke. Diese Abfrage ruft die Funktion [semantickeyphrasetable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql) auf.  
  
```sql  
SET @Title = 'Sample Document.docx'  
  
SELECT @DocID = DocumentID  
    FROM Documents  
    WHERE DocumentTitle = @Title  
  
SELECT @Title AS Title, keyphrase, score  
    FROM SEMANTICKEYPHRASETABLE(Documents, *, @DocID)  
    ORDER BY score DESC  
  
```  
  
  
  
###  <a name="find-similar-or-related-documents"></a><a name="find2"></a>Suchen von ähnlichen oder verwandten Dokumenten  
 Die folgende Abfrage ruft die Dokumente ab, die als dem Beispieldokument ähnlich oder damit verwandt identifiziert wurden. Sie präsentiert die Ergebnisse in absteigender Reihenfolge nach dem Grad der Ähnlichkeit von zwei Dokumenten. Diese Abfrage ruft die Funktion [semanticsimilaritytable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql) auf.  
  
```vb  
SET @Title = 'Sample Document.docx'  
  
SELECT @DocID = DocumentID  
    FROM Documents  
    WHERE DocumentTitle = @Title  
  
SELECT @Title AS SourceTitle, DocumentTitle AS MatchedTitle,  
        DocumentID, score  
    FROM SEMANTICSIMILARITYTABLE(Documents, *, @DocID)  
    INNER JOIN Documents ON DocumentID = matched_document_key  
    ORDER BY score DESC  
  
```  
  
  
  
###  <a name="find-the-key-phrases-that-make-documents-similar-or-related"></a><a name="find3"></a>Suchen der Schlüssel Ausdrücke, die Dokumente ähnlich oder verwandt machen  
 Die folgende Abfrage ruft die Schlüsselausdrücke ab, die zwei Beispieldokumente ähnlich oder verwandt machen. Sie präsentiert die Ergebnisse in absteigender Reihenfolge nach dem Grad, der die Gewichtung der einzelnen Schlüsselausdrücke angibt. Diese Abfrage ruft die Funktion [semanticsimilaritytable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql) auf.  
  
```sql  
SET @SourceTitle = 'first.docx'  
SET @MatchedTitle = 'second.docx'  
  
SELECT @SourceDocID = DocumentID FROM Documents WHERE DocumentTitle = @SourceTitle  
SELECT @MatchedDocID = DocumentID FROM Documents WHERE DocumentTitle = @MatchedTitle  
  
SELECT @SourceTitle AS SourceTitle, @MatchedTitle AS MatchedTitle, keyphrase, score  
    FROM semanticsimilaritydetailstable(Documents, DocumentContent,  
        @SourceDocID, DocumentContent, @MatchedDocID)  
    ORDER BY score DESC  
  
```  
  
  
  
##  <a name="storing-documents-in-sql-server"></a><a name="store"></a>Speichern von Dokumenten in SQL Server  
 Bevor Sie Dokumente mit der semantischen Suche indizieren können, müssen Sie die Dokumente in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank speichern.  
  
 Die FileTable-Funktion in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] macht unstrukturierte Dateien und Dokument zu so genannten "First Class Citizens" (FCCs) der relationalen Datenbank. Folglich können Datenbankentwickler Dokumente zusammen mit strukturierten Daten in Transact-SQL-basierten Vorgängen bearbeiten.  
  
 Weitere Informationen zu der FileTable-Funktion finden Sie unter [FileTables &#40;SQL Server&#41;](../blob/filetables-sql-server.md). Informationen zur FILESTREAM-Funktion, die eine andere Option zum Speichern von Dokumenten in der Datenbank ist, finden Sie unter [FILESTREAM &#40;SQL Server&#41;](../blob/filestream-sql-server.md).  
  
  
  
##  <a name="related-tasks"></a><a name="reltasks"></a> Verwandte Aufgaben  
 [Installieren und Konfigurieren der semantischen Suche](install-and-configure-semantic-search.md)  
 Beschreibt die erforderlichen Komponenten für die statistische semantische Suche und wie diese Komponenten installiert oder überprüft werden.  
  
 [Aktivieren der semantischen Suche in Tabellen und Spalten](enable-semantic-search-on-tables-and-columns.md)  
 Beschreibt, wie die statistische semantische Indizierung für ausgewählte Spalten, die Dokumente oder Text enthalten, aktiviert bzw. deaktiviert wird.  
  
 [Suchen von Schlüsselausdrücken in Dokumenten mit der semantischen Suche](find-key-phrases-in-documents-with-semantic-search.md)  
 Beschreibt, wie Schlüsselausdrücke in Dokumenten oder Textspalten gesucht werden, die für die statistische semantische Indizierung konfiguriert sind.  
  
 [Suchen von ähnlichen und verwandten Dokumenten mit semantischer Suche](find-similar-and-related-documents-with-semantic-search.md)  
 Beschreibt, wie ähnliche oder verwandte Dokumente oder Textwerte sowie Informationen zur Ähnlichkeit oder Verwandtschaft über Spalten gesucht werden, die für die statistische semantische Indizierung konfiguriert sind.  
  
 [Verwalten und Überwachen der semantischen Suche](manage-and-monitor-semantic-search.md)  
 Beschreibt den Prozess der semantischen Indizierung sowie die Tasks im Zusammenhang mit der Überwachung und Verwaltung der Indizes.  
  
##  <a name="related-content"></a><a name="relcontent"></a> Verwandte Inhalte  
 [Semantische Such-DDL, Funktionen, gespeicherte Prozeduren und Sichten](../views/views.md)  
 Führt die zur Unterstützung der semantischen Suche hinzugefügten oder geänderten Transact-SQL-Anweisungen und SQL Server-Datenbankobjekte auf.  
  
  
