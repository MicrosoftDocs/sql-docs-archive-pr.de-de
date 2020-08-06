---
title: Erweitern eines Datasets mithilfe der Transformation für Zusammenführungsjoin | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Merge Join transformation
- datasets [Integration Services], joining
- datasets [Integration Services], extending
- joining datasets [Integration Services]
ms.assetid: 9e512c3c-f89b-45f3-8281-cdb8f35a2b1f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a387c4ad840eb739d36023be9323c063dcb9a68e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609981"
---
# <a name="extend-a-dataset-by-using-the-merge-join-transformation"></a>Erweitern eines Datasets mithilfe der Transformation für Zusammenführungsjoins
  Das Paket muss bereits mindestens einen Datenflusstask und zwei Datenflusskomponenten enthalten, die Eingaben für die Transformation für Zusammenführungsjoins bereitstellen, damit Sie eine Transformation für Zusammenführungsjoins hinzufügen und konfigurieren können.  
  
 Die Transformation für Zusammenführungsjoin erfordert zwei sortierte Eingaben. Weitere Informationen finden Sie unter [Sortieren von Daten für die Transformationen für Zusammenführen und Zusammenführungsjoin](sort-data-for-the-merge-and-merge-join-transformations.md).  
  
### <a name="to-extend-a-dataset"></a>So erweitern Sie ein Dataset  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] das [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]-Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie auf die Registerkarte **Datenfluss** , und ziehen Sie dann aus dem Bereich **Toolbox**die Transformation für Zusammenführungsjoin auf die Entwurfsoberfläche.  
  
4.  Verbinden Sie die Transformation für Zusammenführungsjoins mit dem Datenfluss, indem Sie den Konnektor von einer Datenquelle oder einer vorherigen Transformation auf die Transformation für Zusammenführungsjoins ziehen.  
  
5.  Doppelklicken Sie auf die Transformation für Zusammenführungsjoin.  
  
6.  Wählen Sie im Dialogfeld **Transformations-Editor für Zusammenführungsjoins** den zu verwendenden Jointyp in der Liste **Jointyp** aus.  
  
    > [!NOTE]  
    >  Wenn Sie den Typ **Linker äußerer Join** auswählen, können Sie auf **Eingaben vertauschen** klicken, um die Eingaben zu vertauschen und den linken äußeren Join in einen rechten äußeren Join zu ändern.  
  
7.  Ziehen Sie Spalten in der linken Eingabe auf Spalten in der rechten Eingabe, um die Joinspalten anzugeben. Falls die Spalten denselben Namen haben, können Sie das **entsprechende Kontrollkästchen** aktivieren, damit die Transformation für Zusammenführungsjoin den Join automatisch erstellt.  
  
    > [!NOTE]  
    >  Joins können nur zwischen Spalten mit der gleichen Sortierposition erstellt werden, und die Joins müssen in der von der Sortierposition angegebenen Reihenfolge erstellt werden. Wenn Sie versuchen, die Joins außerhalb der Reihenfolge zu erstellen, werden Sie vom **Transformations-Editor für Zusammenführungsjoin** aufgefordert, zusätzliche Joins für die ausgelassenen Sortierreihenfolgepositionen zu erstellen.  
  
    > [!NOTE]  
    >  Standardmäßig wird die Ausgabe nach den Joinspalten sortiert.  
  
8.  Aktivieren Sie in der linken und rechten Eingabe die Kontrollkästchen zusätzlicher Spalten, die in die Ausgabe eingeschlossen werden sollen. Joinspalten sind standardmäßig eingeschlossen.  
  
9. Aktualisieren Sie optional die Namen von Ausgabespalten in der **Ausgabealias** -Spalte.  
  
10. Klicken Sie auf **OK**.  
  
11. Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Transformation für Zusammenführungsjoin](merge-join-transformation.md)   
 [SQL Server Integration Services-Transformationen](integration-services-transformations.md)   
 [SQL Server Integration Services-Pfade](../integration-services-paths.md)   
 [Datenflusstask](../../control-flow/data-flow-task.md)  
  
  
