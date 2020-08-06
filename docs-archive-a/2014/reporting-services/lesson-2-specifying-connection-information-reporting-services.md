---
title: 'Lektion 2: Angeben von Verbindungsinformationen (Reporting Services) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 54405a3a-d7fa-4d95-8963-9aa224e5901e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c187f0abdc4b277a5f1428407b5c42ca4fd6fee6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699327"
---
# <a name="lesson-2-specifying-connection-information-reporting-services"></a>Lektion 2: Angeben von Verbindungsinformationen (Reporting Services)
  Nachdem Sie dem Tutorial-Projekt einen Bericht hinzugefügt haben, müssen Sie eine *Datenquelle*erstellen. Bei dieser handelt es sich um Verbindungsinformationen, mit denen der Bericht auf Daten aus einer relationalen Datenbank, einer mehrdimensionalen Datenbank oder einer sonstigen Ressource zugreift.  
  
 In dieser Lektion verwenden Sie die Beispieldatenbank [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] als Datenquelle. In diesem Tutorial wird davon ausgegangen, dass sich diese Datenbank in einer Standard Instanz von befindet [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] , die auf dem lokalen Computer installiert ist.  
  
### <a name="to-set-up-a-connection"></a>So richten Sie eine Verbindung ein  
  
1.  Klicken Sie im **Berichtsdaten** Bereich auf **neu** , und klicken Sie dann auf **Datenquelle...**.  
  
    > [!NOTE]  
    >  Zum Anzeigen des **Berichtsdatenbereichs** klicken Sie im Menü **Ansicht** auf **Berichtsdaten**.  
  
2.  Geben Sie in **Name**den Namen [!INCLUDE[ssSampleDBUserInputNonLocal](../includes/sssampledbuserinputnonlocal-md.md)]ein.  
  
3.  Stellen Sie sicher, dass **Eingebettete Verbindung** aktiviert ist.  
  
4.  Wählen Sie unter **Typ**die Option **Microsoft SQL Server**aus.  
  
5.  Geben Sie für **Verbindungszeichenfolge**Folgendes ein:  
  
    ```  
    Data source=localhost; initial catalog=AdventureWorks2012  
    ```  
  
     Bei dieser Verbindungszeichenfolge wird davon ausgegangen, dass [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], der Berichtsserver und die [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] -Datenbank zusammen auf dem lokalen Computer installiert sind und Sie über die Berechtigung verfügen, sich bei der [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] -Datenbank anzumelden.  
  
    > [!NOTE]  
    >  Wenn Sie [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services oder eine benannte Instanz verwenden, muss die Verbindungszeichenfolge Instanzinformationen einschließen:  
    >   
    >  `Data source=localhost\SQLEXPRESS; initial catalog=AdventureWorks2012`  
    >   
    >  Weitere Informationen zu Verbindungs Zeichenfolgen finden Sie unter [Datenverbindungen, Datenquellen und Verbindungs](data-connections-data-sources-and-connection-strings-in-reporting-services.md) Zeichenfolgen in Reporting Services und [Dialog Feld "Datenquellen Eigenschaften", "Allgemein](data-source-properties-dialog-box-general.md)".  
  
6.  Klicken Sie im linken Bereich auf **Anmeldeinformationen** , und klicken Sie auf **Windows-Authentifizierung verwenden (integrierte Sicherheit)**.  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]die Datenquelle [!INCLUDE[ssSampleDBnormal](../includes/sssampledbnormal-md.md)] wird dem **Berichtsdaten** Bereich hinzugefügt.  
  
## <a name="next-task"></a>Nächste Aufgabe  
 Sie haben erfolgreich eine Verbindung mit der [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] -Beispieldatenbank definiert. Als Nächstes erstellen Sie den Bericht. Weitere Informationen finden Sie unter [Lektion 3: Definieren eines Datasets für den Tabellenbericht (Reporting Services)](lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Reporting Services](data-connections-data-sources-and-connection-strings-in-reporting-services.md)  
  
  
