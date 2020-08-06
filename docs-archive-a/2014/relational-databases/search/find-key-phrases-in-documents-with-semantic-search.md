---
title: Suchen von Schlüsselausdrücken in Dokumenten mit der semantischen Suche | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], key phrase queries
ms.assetid: 6ee3676e-ed5d-43ec-aeca-1eed78967111
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8388fb704bf13f44d025e6e32a1450d537f61832
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697863"
---
# <a name="find-key-phrases-in-documents-with-semantic-search"></a>Suchen von Schlüsselausdrücken in Dokumenten mit der semantischen Suche
  Beschreibt, wie Schlüsselausdrücke in Dokumenten oder Textspalten gesucht werden, die für die statistische semantische Indizierung konfiguriert sind.  
  
##  <a name="finding-key-phrases-in-documents"></a><a name="BasicsQueryKey"></a>Suchen von Schlüssel Ausdrücken in Dokumenten  
  
###  <a name="how-to-find-the-key-phrases-in-documents-with-semantickeyphrasetable"></a><a name="howtofind"></a>Gewusst wie: Suchen der Schlüssel Ausdrücke in Dokumenten mit semantickeyphraabtable  
 Um die Schlüsselausdrücke in bestimmten Dokumenten bzw. Dokumente zu identifizieren, die bestimmte Schlüsselausdrücke enthalten, fragen Sie die Funktion [semantickeyphrasetable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql) ab.  
  
 SEMANTICKEYPHRASETABLE gibt eine Tabelle mit keiner, einer oder mehreren Zeilen für die Schlüsselausdrücke zurück, die in der angegebenen Tabelle Spalten zugeordnet sind. Auf diese Rowsetfunktion kann in der FROM-Klausel einer SELECT-Anweisung so verwiesen werden, als handelte es sich dabei um einen regulären Tabellennamen.  
  
> [!NOTE]  
>  In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]werden nur einzelne Wörter für die semantische Suche in den Index aufgenommen. Multiwort-Ausdrücke (ngrams) werden nicht indiziert. Auch werden verschiedene Formen des gleichen Wortes getrennt indiziert. Beispielsweise werden "Agent" und "Agents" getrennt indiziert.  
  
 Ausführliche Informationen zu den für die SEMANTICKEYPHRASETABLE-Funktion erforderlichen Parametern und zu der von ihr zurückgegebenen Ergebnistabelle finden Sie unter [semantickeyphrasetable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql).  
  
> [!IMPORTANT]  
>  Für die Spalten, auf die Sie abzielen, muss die Volltext- und die semantische Indizierung aktiviert sein.  
  
###  <a name="example-1-find-the-top-key-phrases-in-a-specific-document"></a><a name="HowToTopPhrases"></a>Beispiel 1: Suchen der wichtigsten Schlüssel Ausdrücke in einem bestimmten Dokument  
 Im folgenden Beispiel werden die obersten 10 Schlüsselausdrücke aus dem von der @DocumentId-Variable in der Spalte "Dokument" der Production.Document-Tabelle der AdventureWorks-Beispieldatenbank angegebenen Dokument abgerufen. Die @DocumentId-Variable stellt einen Wert aus der Schlüsselspalte des Volltextindexes dar.  
  
```sql  
SELECT TOP(10) KEYP_TBL.keyphrase  
FROM SEMANTICKEYPHRASETABLE  
    (  
    Production.Document,  
    Document,  
    @DocumentId  
    ) AS KEYP_TBL  
ORDER BY KEYP_TBL.score DESC;  
GO  
```  
  
 Die **SEMANTICKEYPHRASETABLE** -Funktion ruft diese Ergebnisse effizient mithilfe eines Indexsuchvorgangs anstelle eines Tabellenscans ab.  
  
###  <a name="example-2-find-the-top-documents-that-contain-a-specific-key-phrase"></a><a name="HowToTopDocuments"></a>Beispiel 2: Suchen der wichtigsten Dokumente, die einen bestimmten Schlüssel Ausdruck enthalten  
 Im folgenden Beispiel werden die obersten 25 Dokumente mit dem Schlüsselausdruck „Bracket“ in der Spalte „Document“ der Production.Document-Tabelle der AdventureWorks-Beispieldatenbank abgerufen.  
  
```sql  
SELECT TOP (25) DOC_TBL.DocumentID, DOC_TBL.DocumentSummary  
FROM Production.Document AS DOC_TBL  
    INNER JOIN SEMANTICKEYPHRASETABLE  
    (  
    Production.Document,  
    Document  
    ) AS KEYP_TBL  
ON DOC_TBL.DocumentID = KEYP_TBL.document_key  
WHERE KEYP_TBL.keyphrase = 'Bracket'  
ORDER BY KEYP_TBL.Score DESC;  
GO  
```  
  
  
