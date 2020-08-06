---
title: Erstellen einer Inhalts Abfrage für ein Mining Modell | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content queries [DMX]
ms.assetid: a0ce837a-89ed-46cf-9ce1-801ccb75fa04
author: minewiskan
ms.author: owend
ms.openlocfilehash: 26af1100d6ba80185c1cc4de18548df0e387824c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694841"
---
# <a name="create-a-content-query-on-a-mining-model"></a>Erstellen einer Miningmodell-Inhaltsabfrage
  Den Miningmodellinhalt können Sie programmgesteuert mit AMO oder XML/A abfragen. Das Erstellen von Abfragen ist jedoch mit DMX einfacher. Sie können auch Abfragen für die Data Mining-Schemarowsets erstellen, indem Sie eine Verbindung zur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz herstellen und mit den von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]bereitgestellten DMVs eine Abfrage erstellen.  
  
 Die folgenden Vorgehensweisen zeigen, wie Abfragen für ein Miningmodell mit DMX erstellt und wie Data Mining-Schemarowsets abgefragt werden.  
  
 Ein Beispiel zum Erstellen einer ähnlichen Abfrage mit XML/A finden Sie unter [Erstellen einer Data Mining-Abfrage mit XMLA](create-a-data-mining-query-by-using-xmla.md).  
  
## <a name="querying-data-mining-model-content-by-using-dmx"></a>Abfragen von Data Mining-Modellinhalt mit DMX  
  
#### <a name="to-create-a-dmx-model-content-query"></a>So erstellen Sie eine DMX-Modellinhaltsabfrage  
  
1.  Klicken Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]im Menü **Ansicht** auf **Vorlagen-Explorer**.  
  
2.  Klicken Sie im Bereich **Vorlagen-Explorer** auf das Cubesymbol, um die Liste zu ändern und Analysis Services-Vorlagen anzuzeigen.  
  
3.  Erweitern Sie in der Liste von Vorlagenkategorien **DMX**, erweitern Sie **Modellinhalt**, und doppelklicken Sie auf **Inhaltsabfrage**.  
  
4.  Wählen Sie im Dialogfeld **Verbindung mit Analysis Services herstellen** die Instanz aus, die das Miningmodell enthält, das Sie abfragen möchten, und klicken Sie auf **Verbinden**.  
  
     Die Vorlage **Inhaltsabfrage** wird im entsprechenden Code-Editor geöffnet. Der Metadatenbereich listet die Modelle auf, die in der aktuellen Datenbank verfügbar sind. Um die Datenbank zu ändern, wählen Sie eine andere Datenbank aus der Liste **Verfügbare Datenbanken** aus.  
  
5.  Geben Sie den Namen eines Mining Modells in die Zeile `FROM` [ *\<mining model, name, MyModel>* ] ein `.CONTENT` . Wenn der Name des Miningmodells Leerzeichen enthält, muss der Name in Klammern eingeschlossen werden.  
  
     Wenn Sie den Namen nicht eingeben möchten, können Sie ein Miningmodell im **Objekt-Explorer** auswählen und in die Vorlage ziehen.  
  
6.  Geben Sie in der Zeile `SELECT` *\<select list, expr list, \*>* die Namen der Spalten im Schemarowset des Mining Modell Inhalts ein.  
  
     Eine Liste von Spalten, die Sie in Miningmodellinhaltsabfragen zurückgeben können, finden Sie unter [Miningmodellinhalt &#40;Analysis Services – Data Mining&#41;](mining-model-content-analysis-services-data-mining.md)bereitgestellten DMVs eine Abfrage erstellen.  
  
7.  Geben Sie wahlweise eine Bedingung in der WHERE-Klausel der Vorlage ein, um die zurückgegebenen Zeilen auf bestimmte Knoten oder Werte zu beschränken.  
  
8.  Klicken Sie auf **Ausführen**.  
  
## <a name="querying-the-data-mining-schema-rowsets"></a>Abfragen der Data Mining-Schemarowsets  
  
#### <a name="to-create-a-query-against-the-data-mining-schema-rowset"></a>So erstellen Sie eine Abfrage für das Data Mining-Schemarowset  
  
1.  Klicken Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]auf der Symbolleiste **Neue Abfrage** auf **DMX-Abfrage für Analysis Services**oder **MDX-Abfrage für Analysis Services**.  
  
2.  Wählen Sie im Dialogfeld **Verbindung mit Analysis Services herstellen** die Instanz aus, die die Objekte enthält, die Sie abfragen möchten, und klicken Sie auf **Verbinden**.  
  
     Die Vorlage **Inhaltsabfrage** wird im entsprechenden Code-Editor geöffnet. Der Metadatenbereich listet die Objekte auf, die in der aktuellen Datenbank verfügbar sind. Um die Datenbank zu ändern, wählen Sie eine andere Datenbank aus der Liste **Verfügbare Datenbanken** aus.  
  
3.  Geben Sie im Abfrage-Editor Folgendes ein:  
  
     `SELECT *`  
  
     `FROM $system.DMSCHEMA_MINING_MODEL_CONTENT`  
  
     `WHERE MODEL_NAME = '<model name>'`  
  
4.  Klicken Sie auf **Ausführen**.  
  
     Im Ergebnisbereich wird der Inhalt des Modells angezeigt.  
  
    > [!NOTE]  
    >  Um eine Liste aller Schemarowsets anzuzeigen, die Sie für die aktuelle Instanz abfragen können, verwenden Sie die folgende Abfrage: `SELECT * FROM $system.`DISCOVER_SCHEMA_ROWSETS. Eine Liste der für Data Mining spezifischen Schemarowsets finden Sie unter [Data Mining Schema Rowsets](../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Mining Modell Inhalt &#40;Analysis Services Data Mining-&#41;](mining-model-content-analysis-services-data-mining.md)   
 [Data Mining Schema Rowsets](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/data-mining-schema-rowsets) 
  
  
