---
title: Darstellung von Joins im Abfrage-und Sicht-Designer (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL pane [Visual Database Tools]
- joins [SQL Server], Query and View Designer
- Diagram pane [Visual Database Tools]
ms.assetid: 20a99dcb-83bd-4aa6-9139-92e2e5ba4887
author: stevestein
ms.author: sstein
ms.openlocfilehash: 55fdea533436f9fa7c2a902667b3166085c27e99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87618978"
---
# <a name="how-the-query-and-view-designer-represents-joins-visual-database-tools"></a>Darstellungsweise von Joins im Abfrage- und Sicht-Designer (Visual Database Tools)
  Bei verknüpften Tabellen stellt der [Abfrage- und Sicht-Designer](visual-database-tools.md) die Verknüpfung im [Diagrammbereich](diagram-pane-visual-database-tools.md) grafisch und im [SQL-Bereich](sql-pane-visual-database-tools.md)mithilfe von SQL-Syntax dar.  
  
## <a name="diagram-pane"></a>Diagrammbereich  
 Im Diagrammbereich wird im Abfrage- und Sicht-Designer eine Joinlinie zwischen den verknüpften Datenspalten an. Der Abfrage- und Sicht-Designer zeigt eine Joinlinie für jede Joinbedingung an. Die folgende Abbildung zeigt eine Joinlinie zwischen zwei verknüpften Tabellen:  
  
 ![Joinlinie zeigt Beziehung zwischen zwei Tabellen](../../database-engine/media//dv3wbig.gif "Joinlinie zeigt Beziehung zwischen zwei Tabellen")  
  
 Wenn Tabellen durch mehrere Joinbedingungen miteinander verknüpft sind, zeigt der Abfrage- und Sicht-Designer wie im folgenden Beispiel mehrere Joinlinien an:  
  
 ![Mit mehr als einer Verknüpfungsbedingung verknüpfte Tabellen](../../database-engine/media//dv3w9n1.gif "Mit mehr als einer Verknüpfungsbedingung verknüpfte Tabellen")  
  
 Wenn die verknüpften Datenspalten nicht angezeigt werden (z. B., weil das die Tabelle oder das Objekt mit Tabellenstruktur darstellende Rechteck minimiert ist oder der Join einen Ausdruck beinhaltet), setzt der Abfrage- und Sicht-Designer die Joinlinie in die Titelleiste des Rechtecks, das die Tabelle oder das Objekt mit Tabellenstruktur darstellt.  
  
 Die Form des Symbols in der Mitte der Joinlinie zeigt an, wie die Tabellen oder Objekte mit Tabellenstruktur verknüpft sind. Wenn die Joinklausel einen anderen Operator als „gleich“ (=) verwendet, wird der Operator im Symbol der Joinlinie angezeigt. In der folgenden Tabelle werden die in der Joinlinie angezeigten Symbole aufgelistet.  
  
|**Joinliniensymbol**|**Beschreibung**|  
|------------------------|---------------------|  
|![Visual Database Tools (Symbol)](../../database-engine/media//dv3wbih.gif "Visual Database Tools (Symbol)")|Innerer Join (erstellt mit einem Gleichheitszeichen).|  
|![Visual Database Tools (Symbol)](../../database-engine/media//dv3wbii.gif "Visual Database Tools (Symbol)")|Innerer Join mit dem Operator "größer als".|  
|![Visual Database Tools (Symbol)](../../database-engine/media//dv3wbij.gif "Visual Database Tools (Symbol)")|Äußerer Join, bei dem sämtliche Zeilen aus der links angezeigten Tabelle aufgenommen werden, auch wenn keine Übereinstimmungen in der verknüpften Tabelle vorliegen.|  
|![Visual Database Tools (Symbol)](../../database-engine/media//dv3wbik.gif "Visual Database Tools (Symbol)")|Äußerer Join, bei dem sämtliche Zeilen aus der rechts angezeigten Tabelle aufgenommen werden, auch wenn keine Übereinstimmungen in der verknüpften Tabelle vorliegen.|  
|![Visual Database Tools (Symbol)](../../database-engine/media//dv3wbil.gif "Visual Database Tools (Symbol)")|Ein vollständiger äußerer Join, bei der alle Zeilen aus beiden Tabellen aufgenommen werden, auch wenn keine Übereinstimmungen in der verknüpften Tabelle vorliegen.|  
  
 Die Symbole an den Enden der Joinlinie zeigen den Jointyp an. In der folgenden Tabelle werden die Jointypen und die an den Enden der Joinslinien verwendeten Symbole aufgelistet.  
  
|**Symbole an den Enden der Joinlinien**|**Jointyp**|  
|-----------------------------------|----------------------|  
|![Visual Database Tools (Symbol)](../../database-engine/media//dv3wbim.gif "Visual Database Tools (Symbol)")|1:1-Join|  
|![Visual Database Tools (Symbol)](../../database-engine/media//dv3wbin.gif "Visual Database Tools (Symbol)")|1:n-Join|  
|![Visual Database Tools (Symbol)](../../database-engine/media//dv3wbio.gif "Visual Database Tools (Symbol)")|Der Abfrage- und Sicht-Designer konnte den Joinstyp nicht ermitteln. Dies tritt häufig auf, wenn Sie einen Join manuell erstellt haben.|  
  
## <a name="sql-pane"></a>SQL-Bereich  
 Ein Join kann in einer SQL-Anweisung auf unterschiedliche Weise ausgedrückt werden. Die genaue Syntax ergibt sich aus der verwendeten Datenbank und daraus, wie Sie den Join definiert haben.  
  
 Folgende Syntaxoptionen werden beim Verknüpfen von Tabellen angewendet:  
  
-   **JOIN-Qualifizierer in der FROM-Klausel**.   Die Schlüsselwörter INNER und OUTER geben den Jointyp an. Diese Syntax entspricht dem Standard bei ANSI 92 SQL.  
  
     Wenn Sie z. B. die Tabellen `publishers` und `pub_info` über die Spalte `pub_id` der beiden Tabellen verknüpfen, kann dies mit folgender SQL-Anweisung ausgedrückt werden:  
  
    ```  
    SELECT *  
    FROM publishers INNER JOIN pub_info ON  
       publishers.pub_id = pub_info.pub_id  
    ```  
  
     Wenn Sie einen äußeren Join erstellen, wird LEFT OUTER oder RIGHT OUTER statt INNER verwendet.  
  
-   **WHERE-Klausel zum Vergleich der Spalten in beiden Tabellen**.   Eine WHERE-Klausel wird angezeigt, wenn die Datenbank die JOIN-Syntax nicht unterstützt (oder wenn Sie sie selbst eingegeben haben). Wenn der Join über die WHERE-Klausel erstellt wird, werden beide Tabellennamen in der FROM-Klausel angegeben.  
  
     Die folgende Anweisung verknüpft z. B. die Tabellen `publishers` und `pub_info` .  
  
    ```  
    SELECT *  
    FROM publishers, pub_info  
    WHERE publishers.pub_id = pub_info.pub_id  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Abfragen mit Joins &#40;Visual Database Tools&#41;](query-with-joins-visual-database-tools.md)   
 [Verknüpfen (Dialogfeld) &#40;Visual Database Tools&#41;](join-dialog-box-visual-database-tools.md)  
  
  
