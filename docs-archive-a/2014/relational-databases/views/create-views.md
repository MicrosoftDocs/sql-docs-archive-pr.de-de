---
title: Erstellen von Sichten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- views [SQL Server], creating
ms.assetid: 0b7bd2a1-544c-42ba-8e7b-4822f34d7b64
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8280f6d65d7252cad423abef849207111492c044
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608468"
---
# <a name="create-views"></a>Erstellen von Sichten
  Sie können in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]Sichten erstellen. Eine Sicht kann für folgende Zwecke verwendet werden:  
  
-   Um die Darstellung einer Datenbank für jeden einzelnen Benutzer einzuschränken, zu vereinfachen und anzupassen.  
  
-   Als Sicherheitsmechanismus, indem Benutzern der Zugriff auf Daten über die Sicht ermöglicht wird, ohne diesen Benutzern jedoch die Berechtigungen für den direkten Zugriff auf die zugrunde liegenden Basistabellen zu gewähren.  
  
-   Um eine abwärtskompatible Schnittstelle zum Emulieren einer Tabelle bereitzustellen, deren Schema geändert wurde.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Sicherheit](#Security)  
  
-   **So erstellen Sie eine Sicht mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
 Eine Sicht kann nur in der aktuellen Datenbank erstellt werden.  
  
 Für eine Sicht sind maximal 1.024 Spalten zulässig.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert die CREATE VIEW-Berechtigung in der Datenbank und die ALTER-Berechtigung für das Schema, in dem die Sicht erstellt wird.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-create-a-view-by-using-the-query-and-view-designer"></a>So erstellen Sie eine Sicht mit dem Abfrage- und Sicht-Designer  
  
1.  Erweitern Sie im **Objekt-Explorer**die Datenbank, in der Sie die neue Sicht erstellen möchten.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Ordner **Sichten**, und klicken Sie anschließend auf **Neue Sicht…** .  
  
3.  Wählen Sie im Dialogfeld **Tabelle hinzufügen** das Element oder die Elemente, die Sie in die neue Sicht einschließen möchten, auf einer der folgenden Registerkarten aus: Tabellen, Sichten, Funktionen und Synonyme.  
  
4.  Klicken Sie auf **Hinzufügen**und dann auf **Schließen**.  
  
5.  Wählen Sie im **Diagrammbereich**die Spalten bzw. die anderen Elemente aus, die in der neuen Sicht enthalten sein sollen.  
  
6.  Wählen Sie im **Kriterienbereich**zusätzliche Sortier- oder Filterkriterien für die Spalten aus.  
  
7.  Klicken Sie im Menü **Datei** auf **Speichern**_view name_.  
  
8.  Geben Sie im Dialogfeld **Namen auswählen** einen Namen für die neue Sicht ein, und klicken Sie auf **OK**.  
  
     Weitere Informationen über den Abfrage- und Sicht-Designer finden Sie unter [Tools im Abfrage- und Sicht-Designer &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md).  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-create-a-view"></a>So erstellen Sie eine Sicht  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    USE AdventureWorks2012 ;   
    GO  
    CREATE VIEW HumanResources.EmployeeHireDate  
    AS  
    SELECT p.FirstName, p.LastName, e.HireDate  
    FROM HumanResources.Employee AS e JOIN Person.Person AS  p  
    ON e.BusinessEntityID = p.BusinessEntityID ;   
    GO  
    -- Query the view  
    SELECT FirstName, LastName, HireDate  
    FROM HumanResources.EmployeeHireDate  
    ORDER BY LastName;  
  
    ```  
  
 Weitere Informationen finden Sie unter [CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql).  
  
  
