---
title: Hinzufügen von HTML in einem Bericht (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 30bd631a-f774-48e7-a13a-b6c2eb54d9bb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 605c84843d62fb664a8a665a3fc3b024f8f87186
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87722534"
---
# <a name="add-html-into-a-report-report-builder-and-ssrs"></a>Hinzufügen von HTML in einem Bericht (Berichts-Generator und SSRS)
  Mithilfe eines Platzhalters können Sie HTML aus einem Feld im Dataset in einen Bericht importieren. Standardmäßig steht ein Platzhalter für einfachen Text, daher müssen Sie den Markuptyp des Platzhalters zu HTML ändern. Weitere Informationen finden Sie unter [Importieren von HTML in einen Bericht (Berichts-Generator und SSRS)](importing-html-into-a-report-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-html-from-a-field-in-your-dataset-into-a-text-box"></a>So fügen Sie einem Textfeld HTML aus einem Datasetfeld hinzu  
  
1.  Klicken Sie auf der Registerkarte **Einfügen** auf **Liste**. Klicken Sie auf die Entwurfsoberfläche, und erstellen Sie dann durch Ziehen ein Feld mit der gewünschten Größe.  
  
     Das Dialogfeld **Dataseteigenschaften** wird angezeigt. Sie können ein freigegebenes Dataset oder ein im Bericht eingebettetes Dataset verwenden. Weitere Informationen finden Sie unter [Dataseteigenschaften (Dialogfeld), Abfrage (Berichts-Generator)](../report-data/dataset-properties-dialog-box-query-report-builder.md) oder [Dataseteigenschaften (Dialogfeld), Abfrage](../dataset-properties-dialog-box-query.md).  
  
2.  Klicken Sie auf der Registerkarte **Einfügen** auf **Textfeld**. Klicken Sie in die Liste, und erstellen Sie dann durch Ziehen ein Feld mit der gewünschten Größe.  
  
3.  Ziehen Sie ein HTML-Feld aus dem Dataset in das Textfeld. Es wird ein Platzhalter für das Feld erstellt.  
  
4.  Klicken Sie mit der rechten Maustaste auf den Platzhalter, und klicken Sie anschließend auf **Platzhaltereigenschaften**.  
  
5.  Vergewissern Sie sich, dass auf der Registerkarte **Allgemein** im Feld **Wert** ein Ausdruck steht, der anhand des in Schritt 3 eingefügten Felds ausgewertet wird.  
  
6.  Klicken Sie auf **HTML – HTML-Tags als Formate interpretieren**. Hierdurch wird das Feld als HTML ausgewertet.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Formatieren von Zahlen und Datumsangaben &#40;Berichts-Generator und SSRS&#41;](formatting-numbers-and-dates-report-builder-and-ssrs.md)   
 [Formatieren von Linien, Farben und Bildern (Berichts-Generator und SSRS)](images-report-builder-and-ssrs.md)   
 [Platzhaltereigenschaften (Dialogfeld), Allgemein (Berichts-Generator und SSRS)](../placeholder-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
