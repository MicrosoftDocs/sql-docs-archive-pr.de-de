---
title: 'Lektion 4: Definieren einer Datenverbindung und einer Datentabelle für untergeordnete Berichte | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a6aa2c56-227c-43c5-a28e-c7104131ac5e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6d9144d960ad933afa65f9d4483e96b5f732d944
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609714"
---
# <a name="lesson-4-define-a-data-connection-and-data-table-for-child-report"></a>Lektion 4: Definieren einer Datenverbindung und einer Datentabelle für den untergeordneten Bericht
  Nachdem Sie den übergeordneten Bericht entworfen haben, erstellen Sie im nächsten Schritt eine Datenverbindung und eine Datentabelle für den untergeordneten Bericht. In diesem Lernprogramm wird eine Datenverbindung mit der AdventureWorks2008-Datenbank hergestellt. Alternativ können Sie auch eine Verbindung mit der AdventureWorks2012-Datenbank herstellen.  
  
### <a name="to-define-a-data-connection-and-datatable-by-adding-a-dataset-for-child-report"></a>So definieren Sie eine Datenverbindung und eine Datentabelle durch Hinzufügen eines Datasets (für den untergeordneten Bericht)  
  
1.  Klicken Sie im Menü **Website** auf **Neues Element hinzufügen**.  
  
2.  Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **DataSet** und dann auf **Hinzufügen**. Wenn Sie dazu aufgefordert werden, sollten Sie das Element dem Ordner **App_Code** hinzufügen, indem Sie auf **Ja**klicken.  
  
     Dadurch wird dem Projekt die neue XSD-Datei **DataSet2.xsd** hinzugefügt und der DataSet-Designer geöffnet.  
  
3.  Ziehen Sie ein **TableAdapter** -Steuerelement aus der Toolbox auf die Entwurfsoberfläche. Dadurch wird der Konfigurations-Assistent **TableAdapter** gestartet.  
  
4.  Klicken Sie auf der Seite **Wählen Sie Ihre Datenverbindung aus** auf **Neue Verbindung**.  
  
5.  Führen Sie im Dialogfeld **Verbindung hinzufügen** die folgenden Schritte aus:  
  
    1.  Geben Sie im Feld **Servername** den Server ein, auf dem sich die Datenbank **AdventureWorks2008** befindet.  
  
         Die SQL Server Express-Standardinstanz lautet **(local)\sqlexpress**.  
  
    2.  Wählen Sie im Abschnitt **Am Server anmelden** die Option aus, die Ihnen den Zugriff auf die Daten ermöglicht. Die Standardeinstellung ist**Windows-Authentifizierung verwenden** .  
  
    3.  Klicken Sie in der Dropdown Liste **Datenbanknamen eingeben oder auswählen** auf **AdventureWorks2008**.  
  
    4.  Klicken Sie auf **OK**, und klicken Sie dann auf **Weiter**.  
  
6.  Wenn Sie in Schritt 5 (b) **SQL Server-Authentifizierung verwenden** ausgewählt haben, legen Sie fest, ob die vertraulichen Daten in die Zeichenfolge eingeschlossen oder ob die Informationen im Anwendungscode festgelegt werden sollen.  
  
7.  Geben Sie auf der Seite **Verbindungszeichenfolge in der Anwendungskonfigurationsdatei speichern** den Namen der Verbindungszeichenfolge ein, oder übernehmen Sie den Standardwert **AdventureWorks2008ConnectionString**. Klicken Sie auf **Weiter**.  
  
8.  Wählen Sie auf der Seite **Wählen Sie einen Befehlstyp aus** die Option **SQL-Anweisungen verwenden**aus, und klicken Sie auf **Weiter**.  
  
9. Geben Sie auf der Seite **SQL-Anweisung eingeben** die folgende Transact-SQL-Abfrage zum Abrufen von Daten aus der **AdventureWorks2008** -Datenbank ein, und klicken Sie dann auf **weiter**.  
  
    ```  
    SELECT PurchaseOrderID, PurchaseOrderDetailID, OrderQty, ProductID, ReceivedQty, RejectedQty, StockedQty FROM Purchasing.PurchaseOrderDetail  
    ```  
  
     Sie können die Abfrage auch erstellen, indem Sie auf den **Abfrage-Generator**klicken. Überprüfen Sie die Abfrage dann, indem Sie auf die Schaltfläche **Abfrage ausführen** klicken. Wenn die Abfrage nicht die erwarteten Daten zurückgibt, verwenden Sie möglicherweise eine frühere Version von AdventureWorks. Weitere Informationen zum Installieren der **AdventureWorks2008** -Version von AdventureWorks finden Sie unter [Anleitung: Installieren der AdventureWorks-Datenbank](https://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx).  
  
10. Deaktivieren Sie auf der Seite **zu generierende Methode auswählen** die Option **Methoden erstellen, um Updates direkt an die Datenbank zu senden (GenerateDBDirectMethods)**, und klicken Sie dann auf **Fertig**stellen.  
  
     Die Konfiguration der ADO.NET [DataTable](https://msdn.microsoft.com/library/system.data.datatable\(v=vs.100\).aspx) als Datenquelle für Ihren Bericht ist jetzt abgeschlossen. Auf der DataSet-Designer-Seite in Visual Studio sollte die hinzugefügte **DataTable** jetzt mit den in der Abfrage angegebenen Spalten aufgeführt werden. DataSet2 enthält die auf der Abfrage basierenden Daten aus der PurchaseOrderDetail-Tabelle.  
  
11. Speichern Sie die Datei .  
  
12. Um die Daten in der Vorschau anzuzeigen, klicken Sie im Menü **Daten** auf **Datenvorschau** , und klicken Sie dann auf **Vorschau**.  
  
## <a name="next-task"></a>Nächste Aufgabe  
 Sie haben erfolgreich eine Datenverbindung und eine Datentabelle für den untergeordneten Bericht erstellt. Als Nächstes entwerfen Sie den untergeordneten Bericht mithilfe des Berichts-Assistenten.  
  
  
