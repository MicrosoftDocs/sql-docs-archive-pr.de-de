---
title: 'Lektion 2: Vorbereiten des Momentaufnahmeordners | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: f286cde9-c0d0-43ef-b7ba-53c3cbb8906c
author: rothja
ms.author: jroth
ms.openlocfilehash: 5d98c7433d0bd50504f20f7f576fcf0b20154c81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87723702"
---
# <a name="lesson-2-preparing-the-snapshot-folder"></a>Lektion 2: Vorbereiten des Momentaufnahmeordners
  In dieser Lektion erfahren Sie, wie Sie den Momentaufnahmeordner konfigurieren, in dem die Veröffentlichungsmomentaufnahme erstellt und gespeichert wird.  
  
### <a name="to-create-a-share-for-the-snapshot-folder-and-assign-permissions"></a>So erstellen Sie eine Freigabe für den Momentaufnahmeordner und weisen Berechtigungen zu  
  
1.  Navigieren Sie im Windows-Explorer zum [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenordner. Der Standardspeicherort lautet C:\Programme\Microsoft SQL Server\MSSQL.X\MSSQL\Data.  
  
2.  Erstellen Sie einen neuen Ordner mit dem Namen **repldata**.  
  
3.  Klicken Sie mit der rechten Maustaste auf den Ordner, und klicken Sie anschließend auf **Eigenschaften**.  
  
4.  Klicken Sie auf der Registerkarte **Freigabe** im Dialogfeld **Eigenschaften von repldata** auf **Freigeben**.  
  
5.  Klicken Sie im Dialogfeld **Dateifreigabe** auf **Freigeben**und anschließend auf **Fertig**.  
  
6.  Klicken Sie auf der Registerkarte **Sicherheit** auf **Bearbeiten**.  
  
7.  Klicken Sie im Dialogfeld **Berechtigungen** auf **Hinzufügen**. Geben Sie im Textfeld **Benutzer, Computer, Dienst Konto oder Gruppen auswählen** den Namen des in Lektion 1 erstellten Momentaufnahmen-Agent Kontos wie \<_Machine_Name> _**\ repl_snapshot**ein, wobei \<*Machine_Name> * der Name des Verlegers ist. Klicken Sie auf **Namen überprüfen**, und klicken Sie dann auf **OK**.  
  
8.  Wiederholen Sie den vorherigen Schritt, um Berechtigungen für den Verteilungs-Agent, wie \<_Machine_Name> _ **\ repl_distribution**, und für die \<_Machine_Name> Merge-Agent als _ **\ repl_merge**hinzuzufügen.  
  
9. Überprüfen Sie, ob die folgenden Berechtigungen gewährt wurden.  
  
    -   repl_snapshot - Vollzugriff  
  
    -   repl_distribution - Lesezugriff  
  
    -   repl_merge - Lesezugriff  
  
10. Klicken Sie auf **OK** , um das Dialogfeld **Eigenschaften von repldata** zu schließen und die repldata-Freigabe zu erstellen.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Sie haben erfolgreich eine Freigabe für den Momentaufnahmeordner konfiguriert. Im nächsten Arbeitsschritt konfigurieren Sie die Verteilung. Weitere Informationen finden Sie unter [Lektion 3: Konfigurieren der Verteilung](lesson-3-configuring-distribution.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sichern des Momentaufnahmeordners](security/secure-the-snapshot-folder.md)  
  
  
