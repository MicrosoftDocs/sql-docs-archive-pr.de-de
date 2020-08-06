---
title: 'Aufgabe 4: Festlegen von Domänen Regeln | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 3a7162ba-cf2f-481f-830d-bb6a02823827
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 42bdbd0228fdd3515f68ce830581f445242768e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608941"
---
# <a name="task-4-setting-domain-rules"></a>Aufgabe 4: Festlegen von Domänenregeln
  In dieser Aufgabe erstellen Sie eine Regel für die **Kontakt-e-Mail-** Domäne, um zu prüfen, ob die e-Mail-Adresse mit ** \@ Adventure-Works.com**endet. Weitere Informationen zu dieser Seite finden Sie im Thema [Erstellen einer Domänen Regel](https://msdn.microsoft.com/library/hh510397.aspx) .  
  
1.  Klicken Sie in der **Domänen Liste**auf **Contact Email** .  
  
2.  Wechseln Sie im rechten Bereich zur Registerkarte **Domänen Regeln** .  
  
     ![Neue Domänenregel hinzufügen (Symbolleistenschaltfläche)](../../2014/tutorials/media/et-settingdomainrules-01.jpg "Neue Domänenregel hinzufügen (Symbolleistenschaltfläche)")  
  
3.  Klicken Sie im rechten Bereich auf der Symbolleiste auf die Schaltfläche **neue Domänen Regel hinzufügen** (siehe Abbildung), um eine Regel hinzuzufügen.  
  
4.  Geben Sie als **Regelname** **e-Mail-Überprüfung** ein, und drücken **Sie** Das Kontrollkästchen **aktiv** sollte standardmäßig aktiviert sein. Dieses Steuerelement ermöglicht Ihnen, eine Regel temporär zu deaktivieren.  
  
5.  Klicken Sie im Bereich **Regel erstellen** auf **Pfeil nach unten**, und wählen Sie **Wert endet mit**aus.  
  
6.  Geben Sie ** \@ Adventure-Works.com** in das Textfeld ein, und drücken Sie **Tab**. Sie können weitere Bedingungen hinzufügen, indem Sie im Bereich **Regel erstellen** **auf der Symbolleiste der ausgewählten Klausel auf neue Bedingung hinzufügen** klicken.  
  
     ![E-Mail-Überprüfungsregel](../../2014/tutorials/media/et-settingdomainrules-02.jpg "E-Mail-Überprüfungsregel")  
  
7.  Klicken Sie auf der Symbolleiste im rechten Bereich auf die Schaltfläche **ausgewählte Domänen Regel für Testdaten ausführen** , um die Regel mit Beispiel Daten zu testen.  
  
     ![Ausgewählte Domänenregel für Testdaten ausführen (Symbolleistenschaltfläche)](../../2014/tutorials/media/et-settingdomainrules-03.jpg "Ausgewählte Domänenregel für Testdaten ausführen (Symbolleistenschaltfläche)")  
  
8.  Klicken Sie im Dialogfeld **Test Domänen Regel** auf der Symbolleiste auf **einen neuen Test Begriff für die Domänen Regel hinzufügen** .  
  
     ![Domänenregel testen (Dialogfeld)](../../2014/tutorials/media/et-settingdomainrules-04.jpg "Domänenregel testen (Dialogfeld)")  
  
9. Geben Sie **frank7 \@ Adventure-Works.com** (einen gültigen Wert) in der Spalte **Kontakt-e-Mail** ein.  
  
10. Wiederholen Sie die vorherigen beiden Schritte, um **Joe2 \@ Adventure-work.com** hinzuzufügen (ein ungültiger Wert ohne ' ').  
  
11. Klicken Sie auf der Symbolleiste auf die letzte Schaltfläche (**Testen Sie die Domänen Regel nach allen Begriffen**), um die Eingabedaten für die Regel zu testen.  
  
     ![Testet die Domänenregeln für alle Begriffe (Symbolleistenschaltfläche)](../../2014/tutorials/media/et-settingdomainrules-05.jpg "Testet die Domänenregeln für alle Begriffe (Symbolleistenschaltfläche)")  
  
12. Beachten Sie, dass der erste Eintrag als gültiges Element und der zweite als ungültiges Element angezeigt wird.  
  
     ![Ergebnisse des Domänenregeltests](../../2014/tutorials/media/et-settingdomainrules-06.jpg "Ergebnisse des Domänenregeltests")  
  
13. Klicken Sie auf **Schließen** , um das Dialogfeld **Domänen Regel testen** zu schließen.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 5: Festlegen begriffsbasierter Beziehungen](../../2014/tutorials/task-5-setting-term-based-relationships.md)  
  
  
