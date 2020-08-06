---
title: Extrahieren von Daten mithilfe der OLE DB-Quelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- extracting data [Integration Services]
- sources [Integration Services], OLE DB
- OLE DB source [Integration Services]
ms.assetid: 4ca6eeb5-b60e-4b81-86dd-0674be8ae8d8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 352d62cc66e3f17fb10839086e7ee9c5307f1a17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87726110"
---
# <a name="extract-data-by-using-the-ole-db-source"></a>Extrahieren von Daten mithilfe der OLE DB-Quelle
  Um eine OLE DB-Quelle hinzuzufügen und zu konfigurieren, muss das Paket bereits mindestens einen Datenflusstask enthalten.  
  
### <a name="to-extract-data-using-an-ole-db-source"></a>So extrahieren Sie Daten mithilfe einer OLE DB-Quelle  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie auf die Registerkarte **Datenfluss** , und ziehen Sie dann aus dem Bereich **Toolbox**die OLE DB-Quelle mit der Maus auf die Entwurfsoberfläche.  
  
4.  Doppelklicken Sie auf die OLE DB-Quelle.  
  
5.  Wählen Sie im Dialogfeld **Quellen-Editor für OLE DB** auf der Seite **Verbindungs-Manager** einen vorhandenen OLE DB-Verbindungs-Manager aus, oder klicken Sie auf **Neu** , um einen neuen Verbindungs-Manager zu erstellen. Weitere Informationen finden Sie unter [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md).  
  
6.  Wählen Sie die Datenzugriffsmethode aus:  
  
    -   **Tabelle oder Sicht** Wählen Sie eine Tabelle oder Sicht in der Datenbank aus, mit der der OLE DB-Verbindungs-Manager eine Verbindung herstellt.  
  
    -   **Variable für Tabellenname oder Sichtname** Wählen Sie die benutzerdefinierte Variable aus, die den Namen einer Tabelle oder Sicht in der Datenbank enthält, mit der der OLE DB-Verbindungs-Manager eine Verbindung herstellt.  
  
    -   **SQL-Befehl** Geben Sie einen SQL-Befehl ein, oder klicken Sie auf **Abfrage erstellen** , um mit dem **Abfrage-Generator**einen SQL-Befehl zu erstellen.  
  
        > [!NOTE]  
        >  Der Befehl kann Parameter enthalten. Weitere Informationen finden Sie unter [Zuordnen von Abfrageparametern zu Variablen in einer Datenflusskomponente](map-query-parameters-to-variables-in-a-data-flow-component.md).  
  
    -   **SQL-Befehl aus Variable** Wählen Sie die benutzerdefinierte Variable aus, die den SQL-Befehl enthält.  
  
        > [!NOTE]  
        >  Die Variablen müssen im Bereich desselben Datenflusstasks definiert werden, der die OLE DB-Quelle enthält, oder im Bereich desselben Pakets. Darüber hinaus muss die Variable einen Zeichenfolgen-Datentyp aufweisen.  
  
7.  Um die Zuordnung zwischen externen Spalten und Ausgabespalten zu aktualisieren, klicken Sie auf **Spalten** und wählen in der Liste **Externe Spalte** verschiedene Spalten aus.  
  
8.  Aktualisieren Sie optional die Namen von Ausgabespalten, indem Sie Werte in der Liste **Ausgabespalte** bearbeiten.  
  
9. Klicken Sie auf **Fehlerausgabe**, um die Fehlerausgabe zu konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren einer Fehlerausgabe in einer Datenflusskomponente](../configure-an-error-output-in-a-data-flow-component.md).  
  
10. Sie können auf **Vorschau** klicken, um bis zu 200 Zeilen der von der OLE DB-Quelle extrahierten Daten anzuzeigen.  
  
11. Klicken Sie auf **OK**.  
  
12. Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [OLE DB-Quelle](ole-db-source.md)   
 [SQL Server Integration Services-Transformationen](transformations/integration-services-transformations.md)   
 [SQL Server Integration Services-Pfade](integration-services-paths.md)   
 [Datenflusstask](../control-flow/data-flow-task.md)  
  
  
