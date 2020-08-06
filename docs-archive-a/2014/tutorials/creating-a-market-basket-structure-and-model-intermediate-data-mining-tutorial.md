---
title: Erstellen von Market Basket-Strukturen und-Modellen (Data Mining-Lernprogramm für Fortgeschrittene) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 659b7a4e-f687-44d9-a60a-86490ccbf90f
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b276fe5bed1d9df8e8b2e3e2826966b6abfb734e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608181"
---
# <a name="creating-a-market-basket-structure-and-model-intermediate-data-mining-tutorial"></a>Erstellen einer Warenkorbstruktur und eines Warenkorbmodells (Data Mining-Lernprogramm für Fortgeschrittene)
  Sie haben nun eine Datenquellensicht erstellt und erstellen mithilfe des Data Mining-Assistenten eine neue Miningstruktur. In dieser Aufgabe legen Sie eine Miningstruktur und ein Miningmodell an, die auf dem [!INCLUDE[msCoName](../includes/msconame-md.md)] Association-Algorithmus basieren.  
  
> [!NOTE]  
>  Wenn Sie eine Fehlermeldung erhalten, nach der "vAssocSeqLineItems" nicht in einer geschachtelten Tabelle verwendet werden kann, kehren Sie zur vorherigen Aufgabe in dieser Lektion zurück, und erstellen Sie den n:1-Join, indem Sie ihn aus der Tabelle "vAssocSeqLineItems" (die n-Seite) in die Tabelle "vAssocSeqOrders" (die 1-Seite) ziehen. Sie können die Beziehung zwischen den Tabellen auch bearbeiten, indem Sie mit der rechten Maustaste auf die Joinlinie klicken.  
  
### <a name="to-create-an-association-mining-structure"></a>So legen Sie die Miningstruktur Association an  
  
1.  Klicken Sie in Projektmappen-Explorer in mit [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] der rechten Maustaste auf **Mining Strukturen** , und wählen Sie **neue Mining Struktur** , um den Data Mining-Assistenten zu öffnen.  
  
2.  Klicken Sie auf der Seite **Willkommen** auf **Weiter**.  
  
3.  Überprüfen Sie auf der Seite **Definitions Methode auswählen** , ob **aus vorhandener relationaler Datenbank oder Data Warehouse** ausgewählt ist, und klicken Sie dann auf **weiter**.  
  
4.  Wählen Sie auf der Seite **Data Mining-Struktur erstellen** unter **welche Data Mining Technik möchten Sie verwenden?** die Option **Microsoft Association Rules** in der Liste aus, und klicken Sie dann auf **weiter**. Die Seite **Datenquellen Sicht auswählen** wird angezeigt.  
  
5.  Wählen Sie unter **Verfügbare Datenquellen Sichten**die Option **Orders**aus, und klicken Sie auf **weiter**.  
  
6.  Aktivieren Sie auf der Seite **Tabellentypen angeben** in der Zeile für die Tabelle vassoctarqlineitems das Kontrollkästchen **geschachtelte** , und aktivieren Sie in der Zeile für die geschachtelte Table vassoctarqorders das Kontrollkästchen **Fall** . Klicken Sie auf **Weiter**.  
  
7.  Deaktivieren Sie auf der Seite **Trainingsdaten angeben** alle Kontrollkästchen, die aktiviert werden können. Legen Sie den Schlüssel für die Fall Tabelle vAssocSeqOrders durch Aktivieren des Kontrollkästchens **Schlüssel** neben OrderNumber fest.  
  
     Da der Zweck der Market Basket-Analyse darin besteht, zu bestimmen, welche Produkte in einer einzelnen Transaktion enthalten sind, müssen Sie das Feld **CustomerKey** nicht verwenden.  
  
8.  Legen Sie den Schlüssel für die geschachtelte Table (vAssocSeqLineItems) fest, indem Sie das Kontrollkästchen **Schlüssel** neben Model auswählen. Wenn Sie dies tun, wird das Kontrollkästchen **Eingabe** ebenfalls automatisch ausgewählt. Aktivieren Sie auch das Kontrollkästchen **vorhersagbar** `Model` .  
  
     In einem waren Korb Modell machen Sie sich keine Gedanken über die Reihenfolge der Produkte im Warenkorb. Daher sollten Sie **LineNumber** nicht als Schlüssel für die geclusterte Tabelle einschließen. Sie würden **LineNumber** nur als Schlüssel in einem Modell verwenden, bei dem die Sequenz wichtig ist. In Lektion 4 erstellen Sie ein Modell, das den [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering-Algorithmus verwendet.  
  
9. Aktivieren Sie das Kontrollkästchen links neben IncomeGroup und Region, aber nehmen Sie keine andere Auswahl vor. Durch Aktivieren der äußerst linken Spalte fügen Sie der Struktur die Spalten zur späteren Bezugnahme hinzu. Die Spalten werden jedoch nicht im Modell verwendet. Ihre Auswahl sollte wie folgt aussehen:  
  
     ![Das Dialogfeld sollte folgendermaßen aussehen](../../2014/tutorials/media/tutorial-configassocmodel.gif "Das Dialogfeld sollte folgendermaßen aussehen")  
  
10. Klicken Sie auf **Weiter**.  
  
11. Überprüfen Sie auf der Seite **Inhalt und Datentyp der Spalten angeben**die Auswahl, die in der folgenden Tabelle angezeigt werden soll, und klicken Sie dann auf **weiter**.  
  
    |Spalten|Inhaltstyp|Datentyp|  
    |-------------|------------------|---------------|  
    |IncomeGroup|Discrete|Text|  
    |Order Number|Schlüssel|Text|  
    |Region|Discrete|Text|  
    |vAssocSeqLineItems|||  
    |Modell|Schlüssel|Text|  
  
12. Auf der Seite **Testsatz erstellen** ist der Standardwert für die Option **Prozentsatz der zu testenden Daten** auf 30 Prozent festgelegt. Ändern Sie diesen Wert in **0**. Klicken Sie auf **Weiter**.  
  
    > [!NOTE]  
    >  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] stellt andere Diagramme zum Messen der Modellgenauigkeit bereit. Einige Genauigkeitsdiagrammtypen, z. B. das Prognosegütediagramm und der Kreuzvalidierungsbericht, dienen jedoch der Klassifizierung und Schätzung. Eine Unterstützung für assoziative Vorhersagen ist nicht vorgesehen.  
  
13. Geben Sie auf der Seite **Assistenten abschließen** unter **Mining Struktur Name den Namen**ein `Association` .  
  
14. Geben Sie in **Mining Modellname den Namen**ein `Association` .  
  
15. Wählen Sie die Option **Drillthrough zulassen**aus, und klicken Sie dann auf **Fertig**stellen.  
  
     Der Data Mining-Designer wird geöffnet, um die `Association` soeben erstellte Mining Struktur anzuzeigen.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Ändern und Verarbeiten des Market Basket-Modells &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/modify-process-market-basket-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Microsoft Association-Algorithmus](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md)   
 [Inhaltstypen &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/content-types-data-mining.md)  
  
  
