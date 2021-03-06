---
title: Angeben von Datentypzuordnungen für einen Oracle-Verleger | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], data type mapping
- data types [SQL Server replication], Oracle publishing
- mapping data types [SQL Server replication]
ms.assetid: f172d631-3b8c-4912-bd0f-568366cd9870
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 26331e3864940b9c7f2a2588e3d3cbfa9944c900
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721289"
---
# <a name="specify-data-type-mappings-for-an-oracle-publisher"></a>Angeben von Datentypzuordnungen für einen Oracle-Verleger
  In diesem Thema wird beschrieben, wie Datentypzuordnungen für einen Oracle-Verleger in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../../includes/tsql-md.md)]angegeben werden. Obwohl eine Gruppe von Standard-Datentypzuordnungen für Oracle-Verleger bereitgestellt wird, ist es möglicherweise erforderlich, für eine bestimmte Veröffentlichung andere Zuordnungen anzugeben.  
  
 **In diesem Thema**  
  
-   **So geben Sie Datentypzuordnungen für einen Oracle-Verleger an mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
 Die Datentypzuordnungen werden auf der Registerkarte **Datenzuordnung**des Dialogfelds **Artikeleigenschaften – \<Article>** angegeben. Diese Registerkarte ist über die Seite **Artikel** des Assistenten für neue Veröffentlichung und das Dialogfeld **Veröffentlichungseigenschaften – \<Publication>** verfügbar. Weitere Informationen zum Verwenden des Assistenten sowie zum Zugriff auf das Dialogfeld finden Sie unter [Erstellen einer Veröffentlichung aus einer Oracle-Datenbank](create-a-publication-from-an-oracle-database.md) und [Anzeigen und Ändern von Veröffentlichungseigenschaften](view-and-modify-publication-properties.md).  
  
#### <a name="to-specify-a-data-type-mapping"></a>So geben Sie eine Datentypzuordnung an  
  
1.  Wählen Sie im Assistenten für neue Veröffentlichung auf der Seite **Artikel** bzw. im Dialogfeld **Veröffentlichungseigenschaften - \<Publication>** eine Tabelle aus, und klicken anschließend auf **Artikeleigenschaften**.  
  
2.  Klicken Sie auf die Option **Eigenschaften des hervorgehobenen Tabelle-Artikels festlegen**.  
  
3.  Wählen Sie auf der Registerkarte **Datenzuordnung** des Dialogfelds **Artikeleigenschaften – \<Article>** in der Spalte **Abonnentendatentyp** Zuordnungen aus:  
  
    -   Bei bestimmten Datentypen gibt es nur eine mögliche Zuordnung. In diesem Fall ist die Spalte im Eigenschaftenraster schreibgeschützt.  
  
    -   Für einige Typen sind mehrere Typen zur Auswahl vorhanden. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] empfiehlt die Verwendung der Standardzuordnung, sofern die Anwendung keine andere Zuordnung erfordert. Weitere Informationen finden Sie unter [Data Type Mapping for Oracle Publishers](../non-sql/data-type-mapping-for-oracle-publishers.md).  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Sie können benutzerdefinierte Datentypzuordnungen programmgesteuert mithilfe von gespeicherten Replikationsprozeduren angeben. Sie können auch die Standard Zuordnungen festlegen, die für die Zuordnung von Datentypen zwischen [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] und einem nicht- [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Datenbank-Management System (DBMS) verwendet werden. Weitere Informationen finden Sie unter [Data Type Mapping for Oracle Publishers](../non-sql/data-type-mapping-for-oracle-publishers.md).  
  
#### <a name="to-define-custom-data-type-mappings-when-creating-an-article-belonging-to-an-oracle-publication"></a>So definieren Sie benutzerdefinierte Datentypzuordnungen beim Erstellen eines Artikels, der zu einer Oracle-Veröffentlichung gehört  
  
1.  Erstellen Sie eine Oracle-Veröffentlichung, sofern noch nicht vorhanden.  
  
2.  Führen Sie auf dem Verteiler [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)aus. Geben Sie den Wert **0** für **\@use_default_datatypes** an. Weitere Informationen finden Sie unter [Definieren eines Artikels](define-an-article.md).  
  
3.  Führen Sie auf dem Verteiler [sp_helparticlecolumns](/sql/relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql) aus, um die vorhandene Zuordnung für eine Spalte in einem veröffentlichten Artikel anzuzeigen.  
  
4.  Führen Sie auf dem Verteiler [sp_changearticlecolumndatatype](/sql/relational-databases/system-stored-procedures/sp-changearticlecolumndatatype-transact-sql)aus. Geben Sie den Namen des Oracle-Verlegers für **\@publisher** sowie **\@publication**, **\@article** und **\@column** an, um die veröffentlichte Spalte zu definieren. Geben Sie den Namen des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentyps, der zugeordnet werden soll, für **\@type** sowie nach Bedarf **\@length**, **\@precision** und **\@scale** an.  
  
5.  Führen Sie auf dem Verteiler [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql)aus. Dies erstellt die Sicht, mit der die Momentaufnahme der Oracle-Veröffentlichung generiert wird.  
  
#### <a name="to-specify-a-mapping-as-the-default-mapping-for-a-data-type"></a>So geben Sie eine Zuordnung als Standardzuordnung für einen Datentyp an  
  
1.  (Optional) Führen Sie auf dem Verteiler für eine beliebige Datenbank [sp_getdefaultdatatypemapping](/sql/relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql)aus. Geben Sie **\@source_dbms**, **\@source_type**, **\@destination_dbms**, **\@destination_version** und andere Parameter an, die zum Identifizieren des Quell-DBMS erforderlich sind. Informationen über den gerade zugeordneten Datentyp im Ziel-DBMS werden mit den Ausgabeparametern zurückgegeben.  
  
2.  (Optional) Führen Sie auf dem Verteiler für eine beliebige Datenbank [sp_helpdatatypemap](/sql/relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql)aus. Geben Sie **\@source_dbms** und alle anderen Parameter an, die zum Filtern des Resultsets benötigt werden. Notieren Sie den Wert von **mapping_id** für die gewünschte Zuordnung im Resultset.  
  
3.  Führen Sie auf dem Verteiler für eine beliebige Datenbank [sp_setdefaultdatatypemapping](/sql/relational-databases/system-stored-procedures/sp-setdefaultdatatypemapping-transact-sql)aus.  
  
    -   Wenn Sie den gewünschten Wert von **mapping_id** kennen, der in Schritt 2 ermittelt wurde, geben Sie diesen Wert für **\@@mapping_id** an.  
  
    -   Wenn Sie den Wert für **mapping_id** nicht kennen, geben Sie die Parameter **\@source_dbms**, **\@source_type**, **\@destination_dbms**, **\@destination_type** sowie alle anderen Parameter an, die zum Identifizieren einer vorhandenen Zuordnung erforderlich sind.  
  
#### <a name="to-find-valid-data-types-for-a-given-oracle-data-type"></a>So suchen Sie gültige Datentypen für einen bestimmten Oracle-Datentyp  
  
1.  Führen Sie auf dem Verteiler für eine beliebige Datenbank [sp_helpdatatypemap](/sql/relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql)aus. Geben Sie den Wert **ORACLE** für **\@source_dbms** sowie alle anderen Parameter an, die zum Filtern des Resultsets benötigt werden.  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> Beispiele (Transact-SQL)  
 In diesem Beispiel wird eine Spalte mit dem Oracle-Datentyp NUMBER geändert, sodass er dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentyp `numeric` (38,38) anstelle des Standarddatentyps `float` zugeordnet wird.  
  
 [!code-sql[HowTo#sp_changecolumndatatype](../../../snippets/tsql/SQL15/replication/howto/tsql/datatypemapping.sql#sp_changecolumndatatype)]  
  
 Diese Beispielabfrage gibt die Standardzuordnungen sowie die alternativen Zuordnungen für den Oracle 9-Datentyp `CHAR` zurück.  
  
 [!code-sql[HowTo#sp_helpcolumndatatype_char](../../../snippets/tsql/SQL15/replication/howto/tsql/datatypemapping.sql#sp_helpcolumndatatype_char)]  
  
 Diese Beispielabfrage gibt die Standardzuordnungen für den Oracle 9-Datentyp `NUMBER` zurück, wenn er ohne Dezimalstellenangabe oder Genauigkeit angegeben wird.  
  
 [!code-sql[HowTo#sp_helpcolumndatatype_number](../../../snippets/tsql/SQL15/replication/howto/tsql/datatypemapping.sql#sp_helpcolumndatatype_number)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Type Mapping for Oracle Publishers](../non-sql/data-type-mapping-for-oracle-publishers.md)   
 [Heterogene Datenbankreplikation](../non-sql/heterogeneous-database-replication.md)   
 [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)   
 [Konfigurieren eines Oracle-Verlegers](../non-sql/configure-an-oracle-publisher.md)  
  
  
