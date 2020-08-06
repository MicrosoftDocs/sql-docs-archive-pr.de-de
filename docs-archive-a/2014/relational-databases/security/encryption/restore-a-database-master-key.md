---
title: Wiederherstellen eines Datenbank-Hauptschlüssels | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- database master key [SQL Server], importing
ms.assetid: 16897cc5-db8f-43bb-a38e-6855c82647cf
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 614ba8bdc494ae7e7e5b3ed7b62390721ef642a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87726845"
---
# <a name="restore-a-database-master-key"></a>Wiederherstellen eines Datenbank-Hauptschlüssels
  In diesem Thema wird beschrieben, wie der Datenbank-Hauptschlüssel in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[tsql](../../../includes/tsql-md.md)]wiederhergestellt wird.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   [So stellen Sie den Datenbank-Hauptschlüssel mithilfe von Transact-SQL wieder her](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   Bei der Wiederherstellung des Hauptschlüssels werden alle Schlüssel von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] entschlüsselt, die mit dem aktuell aktiven Hauptschlüssel verschlüsselt sind. Diese Schlüssel werden dann mit dem wiederhergestellten Hauptschlüssel verschlüsselt. Die Ausführung dieses ressourcenintensiven Vorgangs sollte außerhalb der Hauptzeiten geplant werden. Falls der aktuelle Datenbank-Hauptschlüssel nicht geöffnet ist oder nicht geöffnet werden kann oder falls einer der Schlüssel, die mit ihm verschlüsselt sind, nicht entschlüsselt werden kann, kann der Wiederherstellungsvorgang nicht erfolgreich ausgeführt werden.  
  
-   Falls einer dieser Entschlüsselungsvorgänge nicht erfolgreich ausgeführt werden kann, tritt bei der Wiederherstellung ein Fehler auf. Sie können die FORCE-Option verwenden, um Fehler zu ignorieren, dies kann jedoch zum Verlust von Daten führen, die nicht entschlüsselt werden können.  
  
-   Wurde der Hauptschlüssel mit dem Diensthauptschlüssel verschlüsselt, wird auch der wiederhergestellte Hauptschlüssel mit dem Diensthauptschlüssel verschlüsselt.  
  
-   Falls in der aktuellen Datenbank kein Hauptschlüssel vorhanden ist, wird von RESTORE MASTER KEY ein Hauptschlüssel erstellt. Der neue Hauptschlüssel wird nicht automatisch mit dem Diensthauptschlüssel verschlüsselt.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert die CONTROL-Berechtigung für die Datenbank.  
  
##  <a name="using-sql-server-management-studio-with-transact-sql"></a><a name="SSMSProcedure"></a>Verwenden von SQL Server Management Studio mit Transact-SQL  
  
#### <a name="to-restore-the-database-master-key"></a>So stellen Sie den Datenbank-Hauptschlüssel wieder her  
  
1.  Rufen Sie entweder von einem physischen Sicherungsmedium oder einem Verzeichnis im lokalen Dateisystem eine Kopie des gesicherten Datenbank-Hauptschlüssels ab.  
  
2.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../../includes/ssde-md.md)]-Instanz her.  
  
3.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
4.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    -- Restores the database master key of the AdventureWorks2012 database.  
    USE AdventureWorks2012;  
    GO  
    RESTORE MASTER KEY   
        FROM FILE = 'c:\backups\keys\AdventureWorks2012_master_key'   
        DECRYPTION BY PASSWORD = '3dH85Hhk003#GHkf02597gheij04'   
        ENCRYPTION BY PASSWORD = '259087M#MyjkFkjhywiyedfgGDFD';  
    GO  
    ```  
  
    > [!NOTE]  
    >  Der Dateipfad zum Schlüssel und das Kennwort (sofern es vorhanden ist) des Schlüssels unterscheiden sich von den obigen Informationen. Stellen Sie sicher, dass beide für den Server und die Schlüsseleinrichtung spezifisch sind.  
  
 Weitere Informationen finden Sie unter [RESTORE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-master-key-transact-sql).  
  
  
