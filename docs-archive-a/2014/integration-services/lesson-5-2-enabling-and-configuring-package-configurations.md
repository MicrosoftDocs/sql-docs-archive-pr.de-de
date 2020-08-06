---
title: 'Schritt 2: Aktivieren und Konfigurieren von Paketkonfigurationen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 005218ab-8dd5-48e9-a185-6bc60cd43a7a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a804efcd84ebe563a13f61443fe19096788ca809
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615436"
---
# <a name="step-2-enabling-and-configuring-package-configurations"></a>Schritt 2: Aktivieren und Konfigurieren von Paketkonfigurationen
  In dieser Aufgabe konvertieren Sie das Projekt in das Paketbereitstellungsmodell und aktivieren Paketkonfigurationen mithilfe des Paketkonfigurations-Assistenten. Sie verwenden diesen Assistenten zum Generieren einer XML-Konfigurationsdatei, die Konfigurationseinstellungen für die `Directory`-Eigenschaft des Foreach-Schleifencontainers enthält. Der Wert der Directory-Eigenschaft wird durch eine neue Variable auf Paketebene bereitgestellt, die Sie zur Laufzeit aktualisieren können. Zusätzlich füllen Sie einen neuen Beispieldatenordner auf, der während des Testens verwendet wird.  
  
### <a name="to-create-a-new-package-level-variable-mapped-to-the-directory-property"></a>So erstellen Sie eine neue Variable auf Paketebene, die der Directory-Eigenschaft zugeordnet ist  
  
1.  Klicken Sie in den Hintergrund der Registerkarte **Ablaufsteuerung** im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer. Dadurch wird der Bereich für die Variable, die Sie erstellen, auf das Paket festgelegt.  
  
2.  Wählen Sie im Menü [!INCLUDE[ssIS](../includes/ssis-md.md)] den Befehl **Variablen**aus.  
  
3.  Klicken Sie im Fenster **Variablen** auf das Symbol „Variable hinzufügen“.  
  
4.  Geben Sie im Feld **Name** den Namen **varFolderName**ein.  
  
    > [!IMPORTANT]  
    >  Bei Variablennamen wird nach Groß-/Kleinschreibung unterschieden.  
  
5.  Überprüfen Sie, ob im Feld **Bereich** der Name des Pakets (Lesson 5) angezeigt wird.  
  
6.  Legen Sie den Wert des Felds **Datentyp** der `varFolderName` -Variable auf **String**fest.  
  
7.  Kehren Sie zur Registerkarte **Ablaufsteuerung** zurück, und doppelklicken Sie auf den **Foreach File in Folder** -Container.  
  
8.  Klicken Sie auf der Seite **Sammlung** des **Foreach-Schleifen-Editors** auf **Ausdrücke** und anschließend auf die Schaltfläche mit den Auslassungspunkten **(...)**.  
  
9. Klicken Sie im **Eigenschafts Ausdrucks-Editor**in die Liste **Eigenschaft** , und wählen Sie aus `Directory` .  
  
10. Klicken Sie im Feld **Ausdruck** auf die Schaltfläche mit den Auslassungs Punkten **(...)**.  
  
11. Erweitern Sie im **Ausdrucks-Generator**den Ordner Variablen, und ziehen Sie die Variable **User::varFolderName** in das Feld **Ausdruck** .  
  
12. Klicken Sie auf **OK** , um den **Ausdrucks-Generator**zu schließen.  
  
13. Klicken Sie auf **OK** , um den **Eigenschaftsausdrucks-Editor**zu schließen.  
  
14. Klicken Sie auf **OK** , um den **Foreach-Schleifen-Editor**zu beenden.  
  
### <a name="to-enable-package-configurations"></a>So aktivieren Sie Paketkonfigurationen  
  
1.  Klicken Sie im **Menü Projekt**auf **in Paket Bereitstellungs Modell konvertieren**.  
  
2.  Klicken Sie in der Warnungs-Eingabeaufforderung auf **OK** , nachdem die Konvertierung abgeschlossen ist, und klicken Sie im Dialogfeld **In Paketbereitstellungsmodell konvertieren** auf **OK** .  
  
3.  Klicken Sie in den Hintergrund der Registerkarte **Ablaufsteuerung** im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer.  
  
4.  Klicken Sie im Menü **SSIS** auf **Paketkonfigurationen**.  
  
5.  Wählen Sie im Dialogfeld **Paketkonfigurationsplaner** die Option **Paketkonfigurationen aktivieren**aus, und klicken Sie anschließend auf **Hinzufügen**.  
  
6.  Klicken Sie im Paketkonfigurations-Assistenten auf der Seite Willkommen auf **weiter**.  
  
7.  Überprüfen Sie auf der Seite **Konfigurationstyp auswählen** , ob **Konfigurationstyp** auf **XML-Konfigurationsdatei**festgelegt ist.  
  
8.  Klicken Sie auf der Seite **Konfigurationstyp auswählen** auf **Durchsuchen**.  
  
9. Standardmäßig wird das Dialogfeld **Speicherort der Konfigurationsdatei auswählen** mit dem Projektordner geöffnet.  
  
10. Geben Sie im Dialogfeld **Speicherort der Konfigurationsdatei auswählen** als **Dateinamen****SSISTutorial**ein, und klicken Sie auf **Speichern**.  
  
11. Klicken Sie auf der Seite **Konfigurationstyp auswählen** auf **Weiter**.  
  
12. Erweitern Sie **Variablen** auf der Seite **Eigenschaften für den Exportvorgang auswählen** im Bereich **Objekte**, erweitern Sie **varFolderName**und **Eigenschaften**, und wählen Sie anschließend **Wert**aus.  
  
13. Klicken Sie auf der Seite **Eigenschaften für den Exportvorgang auswählen** auf **Weiter**.  
  
14. Geben Sie auf der Seite **Assistenten abschließen** einen Konfigurationsnamen für die Konfiguration ein, beispielsweise **SSIS Tutorial Directory configuration**. Dies ist der Konfigurationsname, der im Dialogfeld **Paketkonfigurationsplaner** angezeigt wird.  
  
15. Klicken Sie auf **Fertig stellen**.  
  
16. Klicken Sie auf **Schließen**.  
  
17. Der Assistent erstellt eine Konfigurationsdatei mit dem Namen SSISTutorial. dzconfig, die Konfigurationseinstellungen für den `value` der Variablen enthält, die wiederum die- `Directory` Eigenschaft des Enumerators festlegt.  
  
    > [!NOTE]  
    >  Eine Konfigurationsdatei enthält typischerweise komplexe Informationen zu den Paketeigenschaften. In diesem Lernprogramm sollte die einzige Konfigurationsinformation allerdings Folgende sein:  
    > <Configuration ConfiguredType="Property"  
    > Path = "\Package.variables [User:: varFolderName]. Properties [value] "ValueType =" String "\>  
    >  \<ConfiguredValue>\</ConfiguredValue>  
    > \</Configuration>.  
  
### <a name="to-create-and-populate-a-new-sample-data-folder"></a>So erstellen und füllen Sie einen neuen Beispieldatenordner  
  
1.  Erstellen Sie in Windows-Explorer auf der Stamm Ebene Ihres Laufwerks (z. b \\ . C:) einen neuen Ordner mit dem Namen `New Sample Data` .  
  
2.  Suchen Sie die Beispieldateien auf dem Computer, und kopieren Sie drei der Dateien aus dem Ordner.  
  
3.  Fügen Sie `New Sample Data` die kopierten Dateien in den Ordner ein.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Schritt 3: Ändern des Konfigurationswerts der Directory-Eigenschaft](lesson-5-3-modifying-the-directory-property-configuration-value.md)  
  
  
