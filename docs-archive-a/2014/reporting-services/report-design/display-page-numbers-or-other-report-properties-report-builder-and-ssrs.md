---
title: Anzeigen von Seitenzahlen oder anderen Berichtseigenschaften (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c7d95245-4709-4d04-acb4-59bf71e60d97
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: efc3d5d5de11af1fcdfefc52ed12d5057ee12668
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617736"
---
# <a name="display-page-numbers-or-other-report-properties-report-builder-and-ssrs"></a>Anzeigen von Seitenzahlen oder anderen Berichtseigenschaften (Berichts-Generator und SSRS)
  Seitenkopf- oder –fußzeilen in dem Bericht können Seitenzahlen, Berichtstitel, Dateinamen und andere Berichtseigenschaften auf einfache Weise hinzugefügt werden. Diese Eigenschaften werden als Felder im Ordner Integrierte Felder im Berichtsdatenbereich gespeichert:  
  
-   Ausführungszeit  
  
-   Seitenzahl  
  
-   Berichtsordner  
  
-   Berichtsname  
  
-   Berichtsserver-URL  
  
-   Seiten gesamt  
  
-   Benutzer-ID  
  
-   Sprache  
  
 Für eine Seitenzahl können Sie gegebenenfalls das Wort "Seite" vor der Zahl hinzufügen. Möglicherweise soll auch die Gesamtanzahl von Seiten angezeigt werden.  
  
> [!NOTE]  
>  Wenn Sie die Gesamtanzahl von Seiten der Fußzeile hinzufügen, kann sich dies negativ auf die Leistung bei der Ausführung oder Vorschau des Berichts auswirken.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-page-number-or-other-report-properties"></a>So fügen Sie eine Seitenzahl oder andere Berichtseigenschaften hinzu  
  
1.  Erweitern Sie im Berichtsdatenbereich den Knoten Integrierte Felder.  
  
    > [!NOTE]  
    >  Zum Anzeigen des Berichtsdatenbereichs klicken Sie gegebenenfalls auf der Registerkarte „Ansicht“ auf **Berichtsdaten**.  
  
2.  Ziehen Sie das Feld **Seitenzahl** aus dem Berichtsdatenbereich in die Berichtskopf- oder -fußzeile.  
  
    > [!NOTE]  
    >  Dem Bericht wird der Seitenfuß automatisch hinzugefügt. Um einen Seitenkopf hinzuzufügen, klicken Sie auf der Registerkarte **Einfügen** auf **Kopfzeile**und danach auf **Hinzufügen**.  
    >   
    >  Ein Textfeld, das den einfachen Ausdruck [&PageNumber] enthält, wird hinzugefügt.  
  
### <a name="to-add-the-word-page-before-the-page-number"></a>So fügen Sie das Wort "Seite" vor der Seitenzahl hinzu  
  
1.  Klicken Sie mit der rechten Maustaste auf das Textfeld, das [&PageNumber] enthält, und klicken Sie auf **Ausdrücke**.  
  
     Das Textfeld **Ausdruck festlegen für: Wert** enthält den Ausdruck =Globals!PageNumber.  
  
2.  Setzen Sie den Cursor nach dem Gleichheitszeichen (=), und geben Sie `"Page " &` ein.  
  
     Der Ausdruck ist jetzt "="Seite "&Globals!PageNumber".  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-add-total-number-of-pages-after-the-page-number"></a>So fügen Sie Gesamtzahl von Seiten nach der Seitenzahl hinzu  
  
1.  Klicken Sie mit der rechten Maustaste auf das Textfeld mit dem Ausdruck, und klicken Sie auf **Ausdrücke**.  
  
2.  Geben Sie **&„von“&** am Ende des Ausdrucks ein.  
  
3.  Erweitern Sie im Bereich „Kategorie“ die Option **Integrierte Felder** , und doppelklicken Sie auf **TotalPages**.  
  
     Der Ausdruck ist jetzt ="Page "&Globals! PageNumber &" von "&Globals!TotalPages".  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Seitenkopf- und Seitenfußzeilen &#40;Berichts-Generator und SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md)   
 [Formatieren von Text in einem Textfeld &#40;Berichts-Generator und SSRS&#41;](format-text-in-a-text-box-report-builder-and-ssrs.md)  
  
  
