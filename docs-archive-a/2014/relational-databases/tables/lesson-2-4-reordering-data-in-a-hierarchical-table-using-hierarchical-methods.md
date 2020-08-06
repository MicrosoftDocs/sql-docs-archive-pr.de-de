---
title: Neuanordnen von Daten in einer hierarchischen Tabelle mit hierarchischen Methoden | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: 7b8064c7-62c6-488d-84d2-57a5828fb907
author: stevestein
ms.author: sstein
ms.openlocfilehash: ac6c93f359a81a80af81182120f213564680de0d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608473"
---
# <a name="reordering-data-in-a-hierarchical-table-using-hierarchical-methods"></a>Neuanordnen von Daten in einer hierarchischen Tabelle mit hierarchischen Methoden
  Eine Hierarchie neu zu ordnen, ist eine allgemeine Wartungsaufgabe. In dieser Aufgabe werden wir eine UPDATE-Anweisung mit der [GetReparentedValue](/sql/t-sql/data-types/getreparentedvalue-database-engine) -Methode verwenden, um zunächst eine einzelne Zeile an eine neue Position in der Hierarchie zu verschieben. Dann verschieben wir eine ganze Teilstruktur an eine neue Position.  
  
 Die `GetReparentedValue` -Methode benötigt zwei Argumente. Das erste Argument beschreibt den Teil der Hierarchie, der geändert werden soll. Möchten Sie zum Beispiel in der Hierarchie **/1/4/2/3/** den Abschnitt **/1/4/** so ändern, dass die Hierarchie zu **/2/1/2/3/** wird, wobei die beiden letzten Knoten (**2/3/**) unverändert bleiben, müssen Sie die zu ändernden Knoten (**/1/4/**) als erstes Argument angeben. Das zweite Argument gibt die neue Hierarchieebene an, in unserem Beispiel **/2/1/**. Die zwei Argumente dürfen nicht die gleichen Ebenennummern enthalten.  
  
### <a name="to-move-a-single-row-to-a-new-location-in-the-hierarchy"></a>So verschieben Sie eine einzelne Zeile an eine neue Position in der Hierarchie  
  
1.  Wanida berichtet aktuell Sariya. In dieser Prozedur verschieben Sie Wanida von ihrem aktuellen Knoten **/1/1/** so, dass sie Jill berichtet. Ihr neuer Knoten wird **/3/1/** , daher ist **/1/** das erste Argument und **/3/** das zweite. Diese Werte entsprechen den **OrgNode** -Werten von Sariya und Jill. Führen Sie den folgenden Code aus, um Wanida von Sariyas Organisation in die Jills zu verschieben:  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid , @OldParent hierarchyid, @NewParent hierarchyid  
    SELECT @CurrentEmployee = OrgNode FROM HumanResources.EmployeeOrg  
      WHERE EmployeeID = 269 ;   
    SELECT @OldParent = OrgNode FROM HumanResources.EmployeeOrg  
      WHERE EmployeeID = 46 ;   
    SELECT @NewParent = OrgNode FROM HumanResources.EmployeeOrg  
      WHERE EmployeeID = 119 ;   
  
    UPDATE HumanResources.EmployeeOrg  
    SET OrgNode = @CurrentEmployee. GetReparentedValue(@OldParent, @NewParent)   
    WHERE OrgNode = @CurrentEmployee ;  
    GO  
    ```  
  
2.  Führen Sie den folgenden Code aus, um die Ergebnisse sehen zu können:  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    GO  
    ```  
  
     Wanida ist jetzt dem Knoten **/3/1/** zugeordnet.  
  
### <a name="to-reorganize-a-section-of-a-hierarchy"></a>So reorganisieren Sie einen Abschnitt einer Hierarchie  
  
1.  Um zu veranschaulichen, wie eine größere Anzahl von Leuten gleichzeitig verschoben werden kann, führen Sie zunächst den folgenden Code aus, um einen neuen Mitarbeiter einzufügen, der Wanida berichtet:  
  
    ```  
    EXEC AddEmp 269, 291, 'Kevin', 'Marketing Intern'  ;  
    GO  
    ```  
  
2.  Jetzt berichtet Kevin Wanida, der Jill berichtet, die ihrerseits David berichtet. Das bedeutet, dass sich Kevin auf Ebene **/3/1/1/** befindet. Um alle Untergebenen von Jill zu einem neuen Manager zu verschieben, aktualisieren wir alle Knoten mit dem Wert **/3/** für **OrgNode** mit einem neuen Wert. Führen Sie den folgenden Code aus, um Wanida so zu aktualisieren, dass sie Sariya unterstellt ist; Kevin hingegen soll weiterhin Wanida unterstellt sein:  
  
    ```  
    DECLARE @OldParent hierarchyid, @NewParent hierarchyid  
    SELECT @OldParent = OrgNode FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 119 ; -- Jill  
    SELECT @NewParent = OrgNode FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 46 ; -- Sariya  
    DECLARE children_cursor CURSOR FOR  
    SELECT OrgNode FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.GetAncestor(1) = @OldParent;  
    DECLARE @ChildId hierarchyid;  
    OPEN children_cursor  
    FETCH NEXT FROM children_cursor INTO @ChildId;  
    WHILE @@FETCH_STATUS = 0  
    BEGIN  
    START:  
        DECLARE @NewId hierarchyid;  
        SELECT @NewId = @NewParent.GetDescendant(MAX(OrgNode), NULL)  
        FROM HumanResources.EmployeeOrg WHERE OrgNode.GetAncestor(1) = @NewParent;  
  
        UPDATE HumanResources.EmployeeOrg  
        SET OrgNode = OrgNode.GetReparentedValue(@ChildId, @NewId)  
        WHERE OrgNode.IsDescendantOf(@ChildId) = 1;  
        IF @@error <> 0 GOTO START -- On error, retry  
            FETCH NEXT FROM children_cursor INTO @ChildId;  
    END  
    CLOSE children_cursor;  
    DEALLOCATE children_cursor;  
  
    ```  
  
3.  Führen Sie den folgenden Code aus, um die Ergebnisse sehen zu können:  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    GO  
    ```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Text_OrgNode OrgNode OrgLevel EmployeeID EmpName Title  
------------ ------- -------- ---------- ------- -----------------  
/            Ox      0        6          David   Marketing Manager  
/1/          0x58    1        46         Sariya  Marketing Specialist  
/1/1/        0x5AC0  2        269        Wanida  Marketing Assistant  
/1/1//2      0x5AD0  3        291        Kevin   Marketing Intern  
/2/          0x68    1        271        John    Marketing Specialist  
/2/1/        0x6AC0  2        272        Mary    Marketing Assistant  
/3/          0x78    1        119        Jill    Marketing Specialist  
```  
  
 Die gesamte Organisationsstruktur, die Jill (sowohl Wanida als auch Kevin) berichtet hatte, berichtet jetzt Sariya.  
  
 Eine gespeicherte Prozedur für die Neuorganisation eines Bereichs einer Hierarchie finden Sie im Abschnitt „Verschieben von Teilstrukturen“ unter [Hierarchische Daten (SQL Server)](../hierarchical-data-sql-server.md#BKMK_MovingSubtrees).  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Zusammenfassung: Verwalten von Daten in einer hierarchischen Tabelle](lesson-2-5-summary-managing-data-in-a-hierarchical-table.md)  
  
  
