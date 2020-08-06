---
title: Quellen-Editor für Flatfiles (Seite Spalten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfilesourceadapter.columns.f1
helpviewer_keywords:
- Flat File Source Editor
ms.assetid: b5af5f65-c087-44fd-b5ae-d0441245fef2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9b0249b2b17d50fdef4b5cf4aff70a1318614257
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609349"
---
# <a name="flat-file-source-editor-columns-page"></a>Quellen-Editor für Flatfiles (Seite Spalten)
  Mithilfe des Knotens **Spalten** des Dialogfelds **Quellen-Editor für Flatfiles** können Sie jeder externen (Quell-)Spalte eine Ausgabespalte zuordnen.  
  
> [!NOTE]  
>  Die `FileNameColumnName` -Eigenschaft der Flatfilequelle und die- `FastParse` Eigenschaft ihrer Ausgabespalten sind nicht im Quellen- **Editor für Flatfiles**verfügbar, können jedoch mit dem- **Erweiterter Editor**festgelegt werden. Weitere Informationen zu diesen Eigenschaften finden Sie im Abschnitt Flatfilequelle von [Flat File Custom Properties](data-flow/flat-file-custom-properties.md).  
  
 Weitere Informationen zur Flatfilequelle finden Sie unter [Flat File Source](data-flow/flat-file-source.md).  
  
## <a name="options"></a>Tastatur  
 **Verfügbare externe Spalten**  
 Zeigt die Liste der in der Datenquelle verfügbaren externen Spalten an. Mit der Tabelle können keine Spalten hinzugefügt oder gelöscht werden.  
  
 **Externe Spalte**  
 Zeigt die externen (Quell-)Spalten in der Reihenfolge an, in der sie von dem Task gelesen werden. Sie können die Reihenfolge ändern, indem Sie zunächst die ausgewählten Spalten in der Tabelle löschen. Wählen Sie anschließend die externen Spalten in einer anderen Reihenfolge aus der Liste aus.  
  
 **Ausgabespalte**  
 Geben Sie für jede Ausgabespalte einen eindeutigen Namen an. Standardmäßig wird der Name der ausgewählten externen (Quell-)Spalte verwendet. Sie können jedoch auch einen beschreibenden Namen angeben, sofern dieser eindeutig ist. Der angegebene Name wird im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer angezeigt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Quellen-Editor für Flatfiles &#40;Seite Verbindungs-Manager&#41;](../../2014/integration-services/flat-file-source-editor-connection-manager-page.md)   
 [Quellen-Editor für Flatfiles &#40;Seite Fehlerausgabe&#41;](../../2014/integration-services/flat-file-source-editor-error-output-page.md)   
 [Verbindungs-Manager für Flatfiles](connection-manager/file-connection-manager.md)  
  
  
