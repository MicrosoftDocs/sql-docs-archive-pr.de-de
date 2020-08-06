---
title: Anzeigen oder Ändern der Eigenschaften einer Bedingung der richtlinienbasierten Verwaltung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, view policy conditions
- Policy-Based Management, modify policy conditions
ms.assetid: 890d7384-8444-4767-bb6f-f5debb155747
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 08baec48bd13445ef56ea6a29520d23ebaf683b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615981"
---
# <a name="view-or-modify-the-properties-of-a-policy-based-management-condition"></a>Anzeigen oder Ändern der Eigenschaften einer Bedingung der richtlinienbasierten Verwaltung
  In diesem Thema wird beschrieben, wie Sie die Eigenschaften einer Bedingung der richtlinienbasierten Verwaltung mithilfe von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] oder [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] in [!INCLUDE[tsql](../../includes/tsql-md.md)]ändern.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **Anzeigen oder Ändern der Eigenschaften einer Bedingung mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert die Mitgliedschaft in der PolicyAdministratorRole-Rolle in der msdb-Datenbank.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-view-or-modify-a-conditions-properties"></a>So zeigen Sie die Eigenschaften einer Bedingung an bzw. ändern sie  
  
1.  Klicken Sie im **Objekt-Explorer**auf das Pluszeichen, um den Server zu erweitern, der die Bedingungen enthält, die Sie anzeigen oder ändern möchten.  
  
2.  Klicken Sie auf das Pluszeichen, um den Ordner **Verwaltung** zu erweitern.  
  
3.  Klicken Sie auf das Pluszeichen, um **Richtlinienverwaltung**zu erweitern.  
  
4.  Klicken Sie auf das Pluszeichen, um den Ordner **Bedingungen** zu erweitern.  
  
5.  Klicken Sie mit der rechten Maustaste auf die Bedingung, die Sie anzeigen oder bearbeiten möchten, und wählen Sie **Eigenschaften**aus. Weitere Informationen zu den verfügbaren Optionen im Dialog **Feld Bedingung öffnen**_condition_name_ finden Sie im Dialog [Feld neue Bedingung erstellen oder Bedingung öffnen, Seite Allgemein](../../integration-services/general-page-of-integration-services-designers-options.md), [Dialogfeld ' Bedingung öffnen ', Seite ' Abhängige Richtlinien](open-condition-dialog-box-dependent-policies-page.md)', Dialogfeld ' [neue Bedingung erstellen ' oder ' Bedingung öffnen ', Seite ' Beschreibung](create-new-condition-or-open-condition-dialog-box-description-page.md)' und Dialogfeld ' [&#40;Bedingung bearbeiten '&#41; Dialogfeld](advanced-edit-condition-dialog-box.md).  
  
6.  Wenn Sie fertig sind, klicken Sie auf **OK**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-view-a-conditions-properties"></a>So zeigen Sie die Eigenschaften einer Bedingung an  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    USE msdb;  
    GO  
    SELECT name,  
       description,  
       facet,  
       expression,  
       is_name_condition,  
       obj_name  
    FROM syspolicy_conditions;  
    GO  
  
    ```  
  
 Weitere Informationen finden Sie unter [yspolicy_conditions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syspolicy-conditions-transact-sql).  
  
  
