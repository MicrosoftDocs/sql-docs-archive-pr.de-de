---
title: Erstellen einer Data Mining-Abfrage mit XMLA | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content queries [DMX]
ms.assetid: 8f6b6008-006c-4792-9bd1-64c30dc3fd41
author: minewiskan
ms.author: owend
ms.openlocfilehash: d0e85b17db0781671fab0874706f12fdac95b30b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621749"
---
# <a name="create-a-data-mining-query-by-using-xmla"></a>Erstellen einer Data Mining-Abfrage mit XMLA
  Abfragen für Data Mining-Objekte können Sie mithilfe von AMO, DMX oder XML/A erstellen.  
  
 XML wird für die Kommunikation zwischen dem Analysis Services-Server und allen Clients benötigt. Obwohl Inhaltsabfragen im Allgemeinen einfacher mit DMX erstellt werden können, können Sie Abfragen mit der DISCOVER- und der COMMAND-Anweisung in XML/A schreiben, indem Sie entweder einen Client verwenden, der das SOAP-Protokoll unterstützt, oder indem Sie eine XML/A-Abfrage in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]erstellen.  
  
 In diesem Thema wird beschrieben, wie Sie mit in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] verfügbaren XML/A-Vorlagen eine Modellinhaltsabfrage für ein Miningmodell erstellen, das auf dem aktuellen Server gespeichert ist.  
  
## <a name="querying-data-mining-schema-rowsets-by-using-xmla"></a>Abfragen der Data Mining-Schemarowsets mit XML/A  
  
#### <a name="to-open-an-xmla-template"></a>So öffnen Sie eine XML/A-Vorlage  
  
1.  Klicken Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]im Menü **Ansicht** auf **Vorlagen-Explorer**.  
  
2.  Klicken Sie auf das Cubesymbol, um die Liste mit den Analysis-Services-Vorlagen zu öffnen.  
  
3.  Erweitern Sie in der Liste der Vorlagenkategorien den Eintrag **XMLA**, erweitern Sie **Schemarowsets**, und doppelklicken Sie auf **Discover Schema Rowsets** , um die Vorlage im zugehörigen Code-Editor zu öffnen.  
  
4.  Vervollständigen Sie im Dialogfeld **Verbindung mit Analysis Services herstellen** die Verbindungseinstellungen, und klicken Sie dann auf **Verbinden**. Ein neues Fenster des Abfrage-Editors wird mit der Vorlage **Discover Schema Rowsets** geöffnet.  
  
#### <a name="to-discover-column-names-from-the-mining-model-content-schema-rowset"></a>So ermitteln Sie Spaltennamen aus dem MINING MODEL CONTENT-Schemarowset  
  
1.  Klicken Sie bei geöffneter **Discover Schema Rowsets** -Vorlage auf **Ausführen**.  
  
     Eine Liste der Schemarowsets wird im Fenster **Ergebnisse** zurückgegeben. Diese Liste enthält die Rowsetnamen und Rowsetspalten für alle in der aktuellen Instanz verfügbaren Rowsets.  
  
2.  Platzieren Sie den Cursor im **Abfrage** Bereich nach, **\<Restriction List>** und drücken Sie die EINGABETASTE, um eine neue Zeile hinzuzufügen.  
  
3.  Platzieren Sie den Cursor in die leere Zeile, und geben Sie ** \<SchemaName> DMSCHEMA_MINING_MODEL_CONTENT \</SchemaName> **  
  
     Der vollständige Abschnitt für Einschränkungen sollte wie folgt angezeigt werden:  
  
     `<Restrictions>`  
  
     `<RestrictionList>`  
  
     `<SchemaName>DMSCHEMA_MINING_MODEL_CONTENT</SchemaName>`  
  
     `</RestrictionList>`  
  
     `</Restrictions>`  
  
4.  Klicken Sie auf **Ausführen**.  
  
     Im Fenster **Ergebnisse** wird eine Liste der Spaltennamen für das angegebene Schemarowset angezeigt.  
  
#### <a name="to-create-a-content-query-using-the-mining-model-content-schema-rowset"></a>So erstellen Sie eine Inhaltsabfrage mit dem MINING MODEL CONTENT-Schemarowset  
  
1.  Ändern Sie in der Vorlage **Discover Schema Rowsets** den Anforderungstyp, indem Sie den Text innerhalb der Tags für den Anforderungstyp ersetzen.  
  
     Ersetzen Sie die Zeile:  
  
     `<RequestType>DISCOVER_SCHEMA_ROWSETS</RequestType>`  
  
     durch folgende Zeile:  
  
     **\<RequestType>DMSCHEMA_MINING_MODEL_CONTENT\</RequestType>**  
  
2.  Ändern Sie die Einschränkungsliste, um ein Miningmodell mit Namen anzugeben, indem Sie eine neue Bedingung zu den Einschränkungslisten hinzufügen.  
  
3.  Positionieren Sie den Cursor in der Vorlage hinter `<Restriction List>` , und drücken Sie die Eingabetaste, um eine neue Zeile hinzuzufügen.  
  
4.  Setzen Sie den Cursor in die leere Zeile, und geben Sie **<MODEL_NAME>My model name</MODEL_NAME>** ein.  
  
     Der vollständige Abschnitt für Einschränkungen sollte wie folgt angezeigt werden:  
  
     `<Restrictions>`  
  
     `<RestrictionList>`  
  
     `<MODEL_NAME>My model name</MODEL_NAME>`  
  
     `</RestrictionList>`  
  
     `</Restrictions>`  
  
5.  Klicken Sie auf **Ausführen**.  
  
     Im Ergebnisbereich wird die Schemadefinition zusammen mit den Werten für das angegebene Modell angezeigt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Mining Modell Inhalt &#40;Analysis Services Data Mining-&#41;](mining-model-content-analysis-services-data-mining.md)   
 [Data Mining Schema Rowsets](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/data-mining-schema-rowsets) 
  
  
