---
title: Transformations-Editor für Fuzzysuche (Registerkarte Verweis Tabelle) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzylookuptransformation.referencetable.f1
helpviewer_keywords:
- Fuzzy Lookup Transformation Editor
ms.assetid: 451f4e7d-1c8e-4784-b540-df0806509bf1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9ce51dd64c9c5807ab23ac645694cfec29a36d52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609332"
---
# <a name="fuzzy-lookup-transformation-editor-reference-table-tab"></a>Transformations-Editor für Fuzzysuche (Registerkarte Verweistabelle)
  Auf der Registerkarte **Verweistabelle** des Dialogfelds **Transformations-Editor für Fuzzysuche** können Sie die Quelltabelle und den Index für die Suche angeben. Bei der Verweisdatenquelle muss es sich um eine Tabelle in einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Datenbank handeln.  
  
> [!NOTE]  
>  Durch die Transformation für die Fuzzysuche wird eine Arbeitskopie der Verweistabelle erstellt. Die nachfolgend beschriebenen Indizes werden für diese Arbeitstabelle mithilfe einer Spezialtabelle erstellt, und nicht mit einem normalen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Index. Durch die Transformation werden die vorhandenen Quelltabellen nicht verändert, sofern Sie nicht **Gespeicherten Index beibehalten**auswählen. In diesem Fall wird ein Trigger für die Verweistabelle erstellt, der die Arbeitstabelle und die Suchindextabelle auf der Grundlage von Änderungen an der Verweistabelle aktualisiert.  
  
> [!NOTE]  
>  Die `Exhaustive` -Eigenschaft und die-Eigenschaft der `MaxMemoryUsage` Transformation für Fuzzysuche sind im **Transformations-Editor für Fuzzysuche**nicht verfügbar, können jedoch mit dem- **Erweiterter Editor**festgelegt werden. Außerdem kann ein Wert, der größer als 100 für ist, `MaxOutputMatchesPerInput` nur in der **Erweiterter Editor**angegeben werden. Weitere Informationen zu diesen Eigenschaften finden Sie im Abschnitt Transformation für Fuzzysuche von [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md).  
  
 Weitere Informationen zur Transformation für Fuzzysuche finden Sie unter [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
## <a name="options"></a>Tastatur  
 **Teilcache**  
 Wählen Sie einen vorhandenen OLE DB-Verbindungs-Manager aus der Liste aus, oder erstellen Sie eine neue Verbindung, indem Sie auf **Neu**klicken.  
  
 **Neu**  
 Erstellen Sie mithilfe des Dialogfelds **OLE DB-Verbindungs-Manager konfigurieren** eine neue Verbindung.  
  
 **Neuen Index generieren**  
 Geben Sie an, dass die Transformation einen neuen Index erstellen soll, der für die Suche verwendet wird.  
  
 **Name der Verweistabelle**  
 Wählen Sie die vorhandene Tabelle aus, die als Verweis-(Such-)Tabelle verwendet werden soll.  
  
 **Neuen Index speichern**  
 Wählen Sie diese Option aus, wenn Sie den neuen Suchindex speichern möchten.  
  
 **Name des neuen Indexes**  
 Wenn Sie den neuen Suchindex speichern möchten, geben Sie einen beschreibenden Namen für den Index ein.  
  
 **Gespeicherten Index beibehalten**  
 Wenn Sie den neuen Suchindex speichern möchten, geben Sie an, ob der Index auch in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] beibehalten werden soll.  
  
> [!NOTE]  
>  Wenn Sie **Gespeicherten Index beibehalten** auf der Registerkarte **Verweistabelle** des Dialogfelds **Transformations-Editor für Fuzzysuche**wählen, verwendet die Transformation verwaltete gespeicherte Prozeduren zum Verwalten des Index. Diese verwalteten gespeicherten Prozeduren verwenden die Common Language Runtime-Integrationsfunktion (CLR) in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Standardmäßig ist die CLR-Integration in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] nicht aktiviert. Um die Funktion **Gespeicherten Index beibehalten** zu verwenden, müssen Sie die CLR-Integration aktivieren. Weitere Informationen finden Sie unter [Enabling CLR Integration](../relational-databases/clr-integration/clr-integration-enabling.md).  
>   
>  Da die Option **Gespeicherten Index beibehalten** die CLR-Integration erfordert, kann diese Funktion nur verwendet werden, wenn Sie in einer Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] eine Verweistabelle auswählen, für die die CLR-Integration aktiviert ist.  
  
 **Vorhandenen Index verwenden**  
 Gibt an, dass bei der Transformation ein vorhandener Index für die Suche verwendet werden soll.  
  
 **Name eines vorhandenen Indexes**  
 Wählen Sie einen zu einem früheren Zeitpunkt erstellten Index aus der Liste aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Transformations-Editor für Fuzzysuche &#40;Registerkarte Spalten&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-columns-tab.md)   
 [Transformations-Editor für Fuzzysuche &#40;Registerkarte „Erweitert“&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-advanced-tab.md)  
  
  
