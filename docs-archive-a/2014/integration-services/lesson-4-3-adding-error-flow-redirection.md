---
title: 'Schritt 3: Hinzufügen von Fehlerflussumleitungen | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5683a45d-9e73-4cd5-83ca-fae8b26b488c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ceaea310cba05a940f310c01b52d5f912a53bea8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617176"
---
# <a name="step-3-adding-error-flow-redirection"></a>Schritt 3: Hinzufügen der Fehlerflussumleitung
  Wie in der vorhergehenden Aufgabe gezeigt, kann von der Lookup Currency Key-Transformation keine Übereinstimmung generiert werden, wenn die Transformation versucht, die beschädigte Beispielflatfile, die einen Fehler produziert hat, zu verarbeiten. Da die Transformation die Standardeinstellungen für die Fehlerausgabe verwendet, führt jeder Fehler dazu, dass die Transformation fehlschlägt. Wenn die Transformation fehlschlägt, schlägt auch der Rest des Pakets fehl.  
  
 Anstatt ein Fehlschlagen der Transformation zuzulassen, können Sie die Komponente so konfigurieren, dass die fehlerverursachende Zeile mithilfe der Fehlerausgabe in einen anderen Verarbeitungspfad umgeleitet wird. Die Verwendung eines separaten Fehlerverarbeitungspfades gibt Ihnen die Möglichkeit, mehrere Vorgänge auszuführen. Sie können beispielsweise die Daten säubern und dann die fehlerhafte Zeile erneut verarbeiten. Oder Sie speichern die fehlerhafte Zeile zusammen mit zusätzlichen Fehlerinformationen zum späteren Überprüfen und erneutem Verarbeiten.  
  
 In dieser Aufgabe konfigurieren Sie die Lookup Currency Key-Transformation so, dass alle fehlerverursachenden Zeilen in die Fehlerausgabe umgeleitet werden. In der Fehlerverzweigung des Datenflusses werden diese Zeilen in eine Datei geschrieben.  
  
 Standardmäßig enthalten die beiden zusätzlichen Spalten in einer [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Fehlerausgabe **ErrorCode** und **ErrorColumn**nur numerische Codes, die eine Fehlernummer darstellen, und die ID der Spalte, in der der Fehler auftrat. Diese numerischen Werte sind ohne die entsprechende Fehlerbeschreibung nur von begrenztem Nutzen.  
  
 Um die Nützlichkeit der Fehlerausgabe zu verbessern, werden Sie mithilfe einer Skriptkomponente auf die [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -API zugreifen und eine Beschreibung des Fehlers abrufen, bevor das Paket die fehlerverursachenden Zeilen in die Datei schreibt.  
  
### <a name="to-configure-an-error-output"></a>So konfigurieren Sie eine Fehlerausgabe  
  
1.  Erweitern Sie in der **SSIS-Toolbox**die Option **Allgemein**, und ziehen Sie dann **Skript Komponente** auf die Entwurfs Oberfläche der Registerkarte **Datenfluss** . Platzieren Sie das **Skript** rechts von der **Lookup Currency Key** -Transformation.  
  
2.  Klicken Sie im Dialogfeld **Skriptkomponententyp auswählen** auf **Transformation**und anschließend auf **OK**.  
  
3.  Klicken Sie auf die **Lookup Currency Key** -Transformation, und ziehen Sie anschließend den roten Pfeil auf die neu hinzugefügte **Skripttransformation** , um die zwei Komponenten zu verbinden.  
  
     Der rote Pfeil stellt die Fehlerausgabe der **Lookup Currency Key** -Transformation dar. Indem Sie den roten Pfeil zum Verbinden der Transformation mit der Skriptkomponente verwenden, können Sie alle Verarbeitungsfehler in die Skriptkomponente umleiten. Diese verarbeitet dann die Fehler und sendet sie an das Ziel.  
  
4.  Wählen Sie im Dialogfeld **Fehlerausgabe konfigurieren** in der **Fehler** -Spalte **Zeile umleiten**aus, und klicken Sie anschließend auf **OK**.  
  
5.  Klicken Sie auf der **Datenfluss** -Entwurfsoberfläche in der neu hinzugefügten **Skriptkomponente** auf **Skriptkomponente**, und ändern Sie den Namen in **Get Error Description**.  
  
6.  Doppelklicken Sie auf die **Get Error Description** -Transformation.  
  
7.  Wählen Sie im Dialogfeld **Transformations-Editor für Skripterstellung** auf der Seite **Eingabespalten** die **ErrorCode** -Spalte aus.  
  
8.  Erweitern Sie auf der Seite **Eingaben und Ausgaben** das Element **Ausgabe 0**, klicken Sie auf **Ausgabespalten**und anschließend auf **Spalte hinzufügen**.  
  
9. Geben Sie in der- `Name` Eigenschaft **ErrorDescription** ein, und legen Sie die- `DataType` Eigenschaft auf **Unicode-Zeichenfolge [DT_WSTR]** fest.  
  
10. Überprüfen Sie auf der Seite **Skript** , ob die- `LocaleID` Eigenschaft auf **Englisch (USA** festgelegt ist.  
  
11. Klicken Sie auf **Skript bearbeiten**, um [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tools for Applications (VSTA) zu öffnen. Geben Sie den folgenden Code in die `Input0_ProcessInputRow`-Methode ein, oder fügen Sie ihn mit Kopieren und Einfügen ein.  
  
     [Visual Basic]  
  
    ```  
    Row.ErrorDescription =   
      Me.ComponentMetaData.GetErrorDescription(Row.ErrorCode)  
    ```  
  
     [Visual C#]  
  
    ```  
    Row.ErrorDescription = this.ComponentMetaData.GetErrorDescription(Row.ErrorCode);  
    ```  
  
     Die fertige Unterroutine sieht wie der folgende Code aus.  
  
     [Visual Basic]  
  
    ```  
    Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
      Row.ErrorDescription =   
        Me.ComponentMetaData.GetErrorDescription(Row.ErrorCode)  
  
    End Sub  
    ```  
  
     [Visual C#]  
  
    ```  
    public override void Input0_ProcessInputRow(Input0Buffer Row)  
        {  
  
            Row.ErrorDescription = this.ComponentMetaData.GetErrorDescription(Row.ErrorCode);  
  
        }  
    ```  
  
12. Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen** , um das Skript zu erstellen und die Änderungen zu speichern, und schließen Sie anschließend VSTA.  
  
13. Klicken Sie auf **OK** , um das Dialogfeld **Transformations-Editor für Skripterstellung** zu schließen.  
  
## <a name="next-steps"></a>Nächste Schritte  
 [Schritt 4: Hinzufügen eines Flatfileziels] (Lesson-4-4-Adding-a-Flat-File-Destination.MD  
  
  
