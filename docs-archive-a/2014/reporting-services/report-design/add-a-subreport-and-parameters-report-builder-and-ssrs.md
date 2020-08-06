---
title: Hinzufügen eines Unterberichts und Hinzufügen von Parametern (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10093"
- sql12.rtp.rptdesigner.subreportproperties.general.f1
ms.assetid: 94f960f8-a629-4f1e-8277-c3b8f0680d98
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3aeede343763ea5fc8fbdfde179208f98fa1a2ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608292"
---
# <a name="add-a-subreport-and-parameters-report-builder-and-ssrs"></a>Hinzufügen eines Unterberichts und Hinzufügen von Parametern (Berichts-Generator und SSRS)
  Fügen Sie einem Bericht Unterberichte hinzu, wenn Sie einen Hauptbericht erstellen möchten, der mehrere verwandte Berichte enthält. Ein Unterbericht ist ein Verweis auf einen anderen Bericht. Um die Berichte über Datenwerte zu verbinden (z. B. damit mehrere Berichte Daten für denselben Kunden anzeigen), müssen Sie einen parametrisierten Bericht erstellen (z. B. einen Bericht, der die Details für einen bestimmten Kunden enthält). Wenn Sie dem Hauptbericht einen Unterbericht hinzufügen, können Sie Parameter angeben, die an den Unterbericht übergeben werden sollen.  
  
 Sie können Unterberichte auch dynamischen Zeilen oder Spalten in einer Tabelle oder Matrix hinzufügen. Bei der Verarbeitung des Hauptberichts wird der Unterbericht für jede Zeile verarbeitet. Überlegen Sie in diesem Fall, ob Sie den gewünschten Effekt mit Datenbereichen oder mit geschachtelten Datenbereichen erzielen können.  
  
 Um einem Bericht einen Unterbericht hinzuzufügen, müssen Sie zuerst den Bericht erstellen, der als Unterbericht fungiert. Weitere Informationen zum Erstellen des Unterberichts finden Sie unter [Unterberichte &#40;Berichts-Generator und SSRS&#41;](subreports-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-subreport"></a>So fügen Sie einen Unterbericht hinzu  
  
1.  Klicken Sie auf der Registerkarte **Einfügen** auf **Unterbericht**.  
  
2.  Klicken Sie auf der Entwurfsoberfläche auf eine Stelle im Bericht, und ziehen Sie ein Feld, bis es die gewünschte Größe für den Unterbericht erreicht hat. Alternativ können Sie auf die Entwurfsoberfläche klicken, um einen Unterbericht mit der Standardgröße zu erstellen.  
  
3.  Klicken Sie mit der rechten Maustaste auf den Unterbericht, und klicken Sie anschließend auf **Eigenschaften des Unterberichts**.  
  
4.  Geben Sie im Dialogfeld **Eigenschaften des Unterberichts** im Textfeld **Name** einen Namen ein, oder übernehmen Sie den Standardnamen. Der Name muss innerhalb des Berichts eindeutig sein. Standardmäßig wird ein allgemeiner Name zugewiesen, z. B. Subreport1 oder Subreport2.  
  
5.  Klicken Sie im Feld **Diesen Bericht als Unterbericht verwenden** auf **Durchsuchen**, oder geben Sie den Namen des Berichts ein. Es wird empfohlen, auf **Durchsuchen** zu klicken, da der Pfad zum Unterbericht automatisch angegeben wird. Zum Angeben des Berichts stehen Ihnen mehrere Möglichkeiten zur Verfügung. Weitere Informationen finden Sie unter [Angeben von Pfaden zu externen Elementen &#40;Berichts-Generator und SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md).  
  
6.  (Optional) Klicken Sie für **Rahmen an Seitenumbruch auslassen** auf **Ja** , damit in der Mitte des Unterberichts kein Rahmen gerendert wird, wenn der Unterbericht mehrere Seiten umfasst.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-specify-parameters-to-pass-to-a-subreport"></a>So geben Sie Parameter an, die an einen Unterbericht übergeben werden  
  
1.  Klicken Sie in der Entwurfsansicht mit der rechten Maustaste auf den Unterbericht, und klicken Sie anschließend auf **Eigenschaften des Unterberichts**.  
  
2.  Klicken Sie im Dialogfeld **Eigenschaften des Unterberichts** auf **Parameter**.  
  
3.  Klicken Sie auf **Hinzufügen**. Dem Parameterraster wird eine neue Zeile hinzugefügt.  
  
4.  Geben Sie im Textfeld **Name** den Namen eines Parameters im Unterbericht ein, oder wählen Sie den Namen im Listenfeld. Dieser Name muss mit dem Namen eines Berichtsparameters im Unterbericht übereinstimmen, nicht mit dem Namen eines Abfrageparameters.  
  
5.  Geben Sie im Listenfeld **Wert** einen Wert ein, oder wählen Sie einen Wert aus. Dieser Wert wird an den Unterbericht übergeben. Bei dem Wert kann es sich um statischen Text oder einen Ausdruck handeln, der auf ein Feld oder ein anderes Objekt im Hauptbericht verweist.  
  
    > [!NOTE]  
    >  In Berichts-Generator: Wenn ein Parameter in der Liste **Parameter** nicht vorhanden ist und für den Unterbericht ein Standardwert definiert ist, wird der Unterbericht korrekt verarbeitet.  
    >   
    >  In Berichts-Designer müssen alle Parameter, die vom Unterbericht benötigt werden, in der Liste **Parameter** enthalten sein. Fehlt ein benötigter Parameter, wird der Unterbericht nicht richtig im Hauptbericht angezeigt.  
  
6.  Wiederholen Sie die Schritte 3 bis 5, um einen Namen und Wert für jeden Unterberichtsparameter anzugeben.  
  
7.  Klicken Sie auf den Parameter im Parameterraster, und klicken Sie dann auf **Löschen**, um einen Unterberichtsparameter zu löschen.  
  
8.  Um die Reihenfolge eines Unterberichtsparameters zu ändern, klicken Sie auf den Parameter und klicken dann auf die Nach-oben- oder Nach-unten-Schaltfläche.  
  
     Wenn Sie die Reihenfolge eines Unterberichtsparameters ändern, wirkt sich dies nicht auf die Verarbeitung des Unterberichts aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Unterberichte &#40;Berichts-Generator und SSRS&#41;](subreports-report-builder-and-ssrs.md)   
 [Renderingverhalten (Berichts-Generator und SSRS)](rendering-behaviors-report-builder-and-ssrs.md)  
  
  
