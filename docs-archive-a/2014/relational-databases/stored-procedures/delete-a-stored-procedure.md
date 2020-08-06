---
title: Löschen einer gespeicherten Prozedur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- removing stored procedures
- stored procedures [SQL Server], deleting
- deleting stored procedures
ms.assetid: 232dbf4d-392a-406f-af3a-579518cd8e46
author: stevestein
ms.author: sstein
ms.openlocfilehash: 418e68d4bb7c6ba6632767a554aea72e85726840
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621398"
---
# <a name="delete-a-stored-procedure"></a>Löschen einer gespeicherten Prozedur
    
##  <a name="this-topic-describes-how-to-delete-a-stored-procedure-in-sscurrent-by-using-ssmanstudiofull-or-tsql"></a><a name="Top"></a> Dieses Thema beschreibt, wie mit [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] oder [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] eine gespeicherte Prozedur in [!INCLUDE[tsql](../../includes/tsql-md.md)]gelöscht werden kann.  
  
-   **Vorbereitungen:**  [Beschränkungen](#Restrictions), [Sicherheit](#Security)  
  
-   **So löschen Sie eine Prozedur mithilfe von:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
 Das Löschen einer Prozedur kann dazu führen, dass abhängige Objekte und Skripts fehlerhaft sind, wenn diese Objekte und Skripts nicht so aktualisiert werden, dass sie Löschung der Prozedur widerspiegeln. Wird jedoch eine neue Prozedur mit demselben Namen und denselben Parametern erstellt, um die gelöschte Prozedur zu ersetzen, können andere Objekte, die darauf verweisen, weiterhin erfolgreich verarbeitet werden. Weitere Informationen finden Sie unter [Anzeigen der Abhängigkeiten einer gespeicherten Prozedur](view-the-dependencies-of-a-stored-procedure.md).  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER-Berechtigung im Schema, zu der die Prozedur gehört, oder die CONTROL-Berechtigung für die Prozedur.  
  
##  <a name="how-to-delete-a-stored-procedure"></a><a name="Procedures"></a> Vorgehensweise: Löschen einer gespeicherten Prozedur  
 Sie können eine der folgenden Anwendungen verwenden:  
  
-   [SQL Server Management Studio](#SSMSProcedure)  
  
-   [Transact-SQL](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
 **So löschen Sie eine Prozedur im Objekt-Explorer**  
  
1.  Stellen Sie im Objekt-Explorer eine Verbindung mit einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **Datenbanken**, erweitern Sie die Datenbank, zu der die Prozedur gehört, und erweitern Sie dann **Programmierbarkeit**.  
  
3.  Erweitern Sie **Gespeicherte Prozeduren**, klicken Sie mit der rechten Maustaste auf die zu entfernende Prozedur, und klicken Sie dann auf **Löschen**.  
  
4.  Klicken Sie auf **Abhängigkeiten anzeigen**, um die von der Prozedur abhängigen Objekte anzuzeigen.  
  
5.  Bestätigen Sie, dass die richtige Prozedur ausgewählt wurde, und klicken Sie dann auf **OK**.  
  
6.  Entfernen Sie in allen abhängigen Objekten und Skripts die Verweise auf die Prozedur.  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 **So löschen Sie eine Prozedur im Abfrage-Editor**  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **Datenbanken**, erweitern Sie die Datenbank, in die die Prozedur gehört, oder wählen Sie in der Symbolleiste die Datenbank aus der Liste der verfügbaren Datenbanken aus.  
  
3.  Klicken Sie im Menü Datei auf **Neue Abfrage**.  
  
4.  Rufen Sie den Namen der gespeicherten Prozedur ab, der aus der aktuellen Datenbank entfernt werden soll. Erweitern Sie im Objekt-Explorer **Programmierbarkeit** , und erweitern Sie dann **Gespeicherte Prozeduren**. Führen Sie stattdessen im Abfrage-Editor die folgende Anweisung aus.  
  
    ```sql  
    SELECT name AS procedure_name   
        ,SCHEMA_NAME(schema_id) AS schema_name  
        ,type_desc  
        ,create_date  
        ,modify_date  
    FROM sys.procedures;  
    ```  
  
5.  Kopieren und fügen Sie das folgende Beispiel in den Abfrage-Editor ein, und fügen Sie einen Namen der gespeicherten Prozedur ein, der aus der aktuellen Datenbank gelöscht werden soll.  
  
    ```sql  
    DROP PROCEDURE <stored procedure name>;  
    GO  
    ```  
  
6.  Entfernen Sie in allen abhängigen Objekten und Skripts die Verweise auf die Prozedur.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen einer gespeicherten Prozedur](create-a-stored-procedure.md)   
 [Ändern einer gespeicherten Prozedur](modify-a-stored-procedure.md)   
 [Umbenennen einer gespeicherten Prozedur](rename-a-stored-procedure.md)   
 [Anzeigen der Definition einer gespeicherten Prozedur](view-the-definition-of-a-stored-procedure.md)   
 [Anzeigen der Abhängigkeiten einer gespeicherten Prozedur](view-the-dependencies-of-a-stored-procedure.md)   
 [DROP PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-procedure-transact-sql)  
  
  
