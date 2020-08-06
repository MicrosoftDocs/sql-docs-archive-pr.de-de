---
title: Erstellen, Ändern und Löschen von räumlichen Indizes | Microsoft-Dokumentation
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- indexes [SQL Server], creating
- spatial indexes [SQL Server], dropping
- spatial indexes [SQL Server], creating
- indexes [SQL Server], dropping
- indexes [SQL Server], modifying
- spatial indexes [SQL Server], modifying
ms.assetid: 00c1b927-8ec5-44cf-87c2-c8de59745735
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 88de17e8c487d9a965f2e236edac064dc2fe4c7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609060"
---
# <a name="create-modify-and-drop-spatial-indexes"></a>Erstellen, Ändern und Löschen von räumlichen Indizes
  Mit einem räumlichen Index können bestimmte Vorgänge für eine Spalte des- `geometry` `geography` Datentyps oder-Datentyps (eine *räumliche Spalte*) effizienter durchgeführt werden. Für eine räumliche Spalte können mehrere räumliche Indizes angegeben werden. Dies ist beispielsweise hilfreich, wenn verschiedene Mosaikparameter in einer Spalte indiziert werden sollen.  
  
 Die Erstellung von räumlichen Indizes unterliegt einigen Einschränkungen. Weitere Informationen zu den Beschränkungen von räumlichen Indizes finden Sie unter [Erstellen, Ändern und Löschen von räumlichen Indizes](#restrictions) in diesem Thema.  
  
> [!NOTE]  
>  Weitere Informationen zur Beziehung zwischen räumlichen Indizes und Partitionen und Dateigruppen finden Sie im Abschnitt mit Hinweisen unter [CREATE SPATIAL INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-spatial-index-transact-sql).  
  
##  <a name="creating-modifying-and-dropping-spatial-indexes"></a><a name="creating"></a> Erstellen, Ändern und Löschen von räumlichen Indizes  
  
###  <a name="to-create-a-spatial-index"></a><a name="create"></a> So erstellen Sie einen räumlichen Index  
 **So erstellen Sie einen räumlichen Index mit Transact-SQL**  
 [CREATE SPATIAL INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-spatial-index-transact-sql)  
  
 **So erstellen Sie mit dem Dialogfeld "Neuer Index" in Management Studio einen räumlichen Index**  
 ##### <a name="to-create-a-spatial-index-in-management-studio"></a>So erstellen Sie einen räumlichen Index in Management Studio  
  
1.  Stellen Sie im Objekt-Explorer eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **Datenbanken**und anschließend die Datenbank, die die Tabelle mit dem angegebenen Index enthält, und erweitern Sie anschließend **Tabellen**.  
  
3.  Erweitern Sie die Tabelle, für die Sie den Index erstellen möchten.  
  
4.  Klicken Sie mit der rechten Maustaste auf **Indizes** , und wählen Sie **Neuer Index**aus.  
  
5.  Geben Sie im Feld **Indexname** einen Namen für den Index ein.  
  
6.  Wählen Sie in der Dropdownliste **Indextyp** den Eintrag **räumlich**aus.  
  
7.  Klicken Sie auf **Hinzufügen**, um die räumliche Spalte anzugeben, die indiziert werden soll.  
  
8.  Wählen Sie im Dialogfeld **Spalten auswählen aus** *\<table name>* eine Spalte des Typs oder aus, `geometry` indem Sie `geography` das entsprechende Kontrollkästchen aktivieren. Alle anderen räumlichen Spalten werden daraufhin nicht editierbar. Wenn Sie eine andere räumliche Spalte auswählen möchten, müssen Sie zuerst die Auswahl der aktuell ausgewählten Spalte aufheben. Wenn Sie fertig sind, klicken Sie auf **OK**.  
  
9. Überprüfen Sie die Spaltenauswahl im Raster **Indexschlüsselspalten** .  
  
10. Klicken Sie im Bereich **Seite auswählen** des Dialogfelds **Indexeigenschaften** auf **räumlich**.  
  
11. Geben Sie auf der Seite **räumlich** die Werte ein, die Sie für die räumlichen Eigenschaften des Index verwenden möchten.  
  
     Wenn Sie einen Index für eine `geometry` Typspalte erstellen, müssen Sie die Koordinaten **( *`X-min`* , *`Y-min`* )** und **( *`X-max`* , *`Y-max`* )** des umgebenden Felds angeben. Bei einem Index für eine `geography` Typspalte werden die Felder für das umgebende Feld schreibgeschützt, nachdem Sie das Mosaik Schema für das **Geografieraster** angegeben haben, da das Geografieraster-Mosaik kein Begrenzungsfeld verwendet.  
  
     Optional können Sie benutzerdefinierte Werte für das Feld **Zellen pro Objekt** und für die Rasterdichte auf jeder Ebene des Mosaikschemas angeben. Die Standardanzahl von Zellen pro Objekt ist 16 für [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] oder 8 für [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] oder höher, und die Standardrasterdichte ist **Mittel** für [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)].  
  
     In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]können Sie GEOMETRY_AUTO_GRID oder GEOGRAPHY_AUTO_GRID für das Mosaikschema auswählen. Wenn GEOMETRY_AUTO_GRID oder GEOGRAPHY_AUTO_GRID ausgewählt wird, sind die Rasterdichteoptionen für Ebene 1, Ebene 2, Ebene 3 und Ebene 4 deaktiviert.  
  
     Weitere Informationen zu diesen Eigenschaften finden Sie unter [Indexeigenschaften (F1-Hilfe)](../indexes/index-properties-f1-help.md).  
  
12. Klicken Sie auf **OK**.  
  
> [!NOTE]  
>  Um einen weiteren räumlichen Index für die gleiche oder eine andere räumliche Spalte zu erstellen, wiederholen Sie die gerade beschriebenen Schritte.  
  
  
 **So erstellen Sie mit dem Tabellen-Designer in Management Studio einen räumlichen Index**  
 ##### <a name="to-create-a-spatial-index-in-table-designer"></a>So erstellen Sie einen räumlichen Index im Tabellen-Designer  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf die Tabelle, für die Sie einen räumlichen Index erstellen möchten, und klicken Sie anschließend auf **Entwerfen**.  
  
     Die Tabelle wird im Tabellen-Designer geöffnet.  
  
2.  Wählen Sie eine `geometry`- oder `geography`-Spalte für den Index aus.  
  
3.  Klicken Sie im Menü **Tabellen-Designer** auf **räumlicher Index**.  
  
4.  Klicken Sie im Dialogfeld **räumliche Indizes** auf **Hinzufügen**.  
  
5.  Wählen Sie den neuen Index aus der Liste **Ausgewählter räumlicher Index** aus, und legen Sie im Raster rechts die Eigenschaften für den räumlichen Index fest. Informationen zu den Eigenschaften finden Sie unter [Dialogfeld 'Räumliche Indizes' &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md).  
  
  
###  <a name="to-alter-a-spatial-index"></a><a name="alter"></a> So ändern Sie einen räumlichen Index  
  
-   [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)  
  
    > [!IMPORTANT]  
    >  Zum Ändern von Optionen, die einem bestimmten räumlichen Index eigen sind, beispielsweise BOUNDING_BOX oder GRID, können Sie entweder eine CREATE SPATIAL INDEX-Anweisung mit der Angabe DROP_EXISTING = ON verwenden, oder Sie löschen den räumlichen Index und erstellen einen neuen räumlichen Index. Für ein Beispiel gehen Sie unter [CREATE SPATIAL INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-spatial-index-transact-sql).  
  
-   [Ändern eines Indexes](../indexes/modify-an-index.md)  
  
-   [Verschieben eines vorhandenen Indexes in eine andere Dateigruppe](../indexes/move-an-existing-index-to-a-different-filegroup.md)  
  
  
###  <a name="to-drop-a-spatial-index"></a><a name="drop"></a> So löschen Sie einen räumlichen Index  
 **So löschen Sie einen räumlichen Index mit Transact-SQL**  
 [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)  
  
 **So löschen Sie einen Index mit Management Studio**  
 [Index löschen](../indexes/delete-an-index.md)  
  
 **So löschen Sie mit dem Tabellen-Designer in Management Studio einen räumlichen Index**  
 ##### <a name="to-drop-a-spatial-index-in-table-designer"></a>So löschen Sie einen räumlichen Index im Tabellen-Designer  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf die Tabelle mit dem räumlichen Index, den Sie löschen möchten, und klicken Sie anschließend auf **Entwerfen**.  
  
     Die Tabelle wird im Tabellen-Designer geöffnet.  
  
2.  Klicken Sie im Menü **Tabellen-Designer** auf **räumlicher Index**.  
  
     Das Dialogfeld **räumlicher Index** wird geöffnet.  
  
3.  Klicken Sie in der Spalte **Ausgewählter räumlicher Index** auf den Index, den Sie löschen möchten.  
  
4.  Klicken Sie auf **Löschen**.  
  
  
##  <a name="restrictions-on-spatial-indexes"></a><a name="restrictions"></a> Erstellen, Ändern und Löschen von räumlichen Indizes  
 Ein räumlicher Index kann nur für eine Spalte des Typs `geometry` oder `geography` erstellt werden.  
  
### <a name="table-and-view-restrictions"></a>Einschränkungen für Tabellen und Sichten  
 Räumliche Indizes können nur für eine Tabelle definiert werden, die über einen Primärschlüssel verfügt. Die maximale Anzahl von Primärschlüsselspalten in einer Tabelle beträgt 15.  
  
 Die maximal zulässige Größe der Indexschlüsseldatensätze beträgt 895 Byte. Eine Überschreitung dieser Größe verursacht ein Fehler.  
  
> [!NOTE]  
>  Primärschlüsselmetadaten können nicht geändert werden, während ein räumlicher Index für eine Tabelle definiert wird.  
  
 Räumliche Indizes können nicht für indizierte Sichten angegeben werden.  
  
### <a name="multiple-spatial-index-restrictions"></a>Einschränkungen für mehrere räumliche Indizes  
 Sie können bis zu 249 räumliche Indizes für beliebige räumliche Spalten in einer unterstützten Tabelle erstellen. Die Erstellung mehrerer räumlicher Indizes für dieselben räumlichen Spalten kann sinnvoll sein, beispielsweise um verschiedene Mosaikparameter in einer einzelnen Spalte zu indizieren.  
  
 Sie können jeweils nur einen räumlichen Index erstellen.  
  
### <a name="spatial-indexes-and-process-parallelism"></a>Räumliche Indizes und Prozessparallelität  
 Bei der Indexerstellung kann die verfügbare Prozessparallelität genutzt werden.  
  
### <a name="version-restrictions"></a>Versionseinschränkungen  
 Räumliche Mosaike, die mit [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] eingeführt wurden, können nicht in [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] oder [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]repliziert werden. Sie müssen räumliche Mosaike von [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] oder [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] für räumliche Indizes für die Abwärtskompatibilität mit [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] - oder [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] -Datenbanken verwenden.  
  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über räumliche Indizes](spatial-indexes-overview.md)  
  
  
