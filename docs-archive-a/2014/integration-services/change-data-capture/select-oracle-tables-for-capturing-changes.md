---
title: Auswählen von Oracle-Tabellen zum Aufzeichnen von Änderungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- selOraTabDia
ms.assetid: 2e295dc8-999d-4c4d-96cc-1519674b47a4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e9064789dce83ff7d3917ed026c861743142e048
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720302"
---
# <a name="select-oracle-tables-for-capturing-changes"></a>Auswählen von Oracle-Tabellen zum Aufzeichnen von Änderungen
  Verwenden Sie dieses Dialogfeld, um die Tabellen auszuwählen, die in der CDC-Instanz enthalten sind. Die ausgewählten Tabellen werden im Assistenten für neue Instanzen der Liste auf der Seite **Select Tables and Columns** hinzugefügt. In diesem Dialogfeld können Sie die folgenden Schritte ausführen.  
  
 Standardmäßig sind in diesem Dialogfeld in der Tabellenliste keine Tabellen enthalten. Sie können das Kontrollkästchen oberhalb der Kontrollkästchenspalte aktivieren, um alle Tabellen auszuwählen, oder Sie können nach bestimmten Tabellen suchen.  
  
 **So suchen Sie nach bestimmten Tabellen**  
 Geben Sie die Suchkriterien wie folgt ein, und klicken Sie dann auf **Suchen**:  
  
-   **Schema**: Wählen Sie in der Liste ein Datenbankschema aus. In der Liste werden nur Tabellen aufgeführt, die über dieses Schema verfügen.  
  
-   **Table Name Pattern**: Geben Sie eine beliebige Zeichenfolge ein. Es werden nur Tabellen angezeigt, die die eingegebene Zeichenfolge enthalten.  
  
> [!NOTE]  
>  Sie können Kriterien in eines der Felder oder beide Felder eingeben.  
  
-   **Display first 1000 matching tables**: Dieses Kontrollkästchen ist standardmäßig aktiviert. Diese Option beschränkt die Anzeige auf die ersten 1000 übereinstimmenden Tabellen. Wenn Sie das Kontrollkästchen deaktivieren, werden alle Tabellen angezeigt, die zu einer Übereinstimmung führen. Falls eine große Anzahl von Tabellen vorhanden ist, kann es relativ lange dauern, bis die Liste angezeigt wird.  
  
 **So wählen Sie die Tabellen aus, die in die CDC-Instanz eingeschlossen werden sollen**  
 Aktivieren Sie das Kontrollkästchen neben einer beliebigen Tabelle, die Sie einschließen möchten, und klicken Sie dann auf **Hinzufügen**. Die Tabellen werden im Assistenten für neue Instanzen der Liste auf der Seite **Select Tables and Columns** hinzugefügt.  
  
 Klicken Sie auf **Schließen** , um das Dialogfeld zu schließen, ohne weitere Tabellen hinzuzufügen.  
  
> [!NOTE]  
>  Wenn Sie eine Tabelle auswählen, die einen nicht unterstützten Datentyp enthält, wird eine Fehlermeldung angezeigt, und die Tabelle wird nicht eingeschlossen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen der Instanz für die SQL Server-Änderungsdatenbank](how-to-create-the-sql-server-change-database-instance.md)   
 [Auswählen von Oracle-Tabellen und -Spalten](select-oracle-tables-and-columns.md)  
  
  
