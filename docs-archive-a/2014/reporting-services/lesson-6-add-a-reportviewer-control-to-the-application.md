---
title: 'Lektion 6: Hinzufügen eines ReportViewer-Steuerelements zur Anwendung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f9492a97-5609-4059-ae76-0fba111d4968
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bb04008fa47801f0500de711592a3cec45ca3dd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621877"
---
# <a name="lesson-6-add-a-reportviewer-control-to-the-application"></a>Lektion 6: Hinzufügen eines ReportViewer-Steuerelements zur Anwendung
  Nachdem Sie den untergeordneten Bericht mit dem Berichts-Assistenten entworfen haben, fügen Sie der Websiteanwendung im nächsten Schritt ein ReportViewer-Steuerelement hinzu.  
  
### <a name="to-add-a-reportviewer-control-to-the-application"></a>So fügen Sie der Anwendung das ReportViewer-Steuerelement hinzu  
  
1.  Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf **Default.aspx**, und klicken Sie auf **Sicht-Designer**.  
  
2.  Ziehen Sie ein **ScriptManager** -Steuerelement aus der Gruppe **AJAX-Erweiterungen** im Fenster **Toolbox** auf die Entwurfsoberfläche.  
  
3.  Ziehen Sie ein **ReportViewer** -Steuerelement aus der Gruppe **Berichterstellung** unterhalb des **ScriptManager** -Steuerelements auf die Entwurfsoberfläche.  
  
4.  Öffnen Sie das Fenster **ReportViewer-Aufgaben** , indem Sie auf den Pfeil in der oberen rechten Ecke des **ReportViewer** -Steuerelements klicken.  
  
5.  Wählen Sie im Feld **Bericht auswählen** den erstellten übergeordneten Bericht aus.  
  
     Nachdem Sie einen Bericht ausgewählt haben, werden automatisch Instanzen der im Bericht verwendeten Datenquellen erstellt. Der Code wird generiert, um jede DataTable (und den zugehörigen [DataSet](https://msdn.microsoft.com/library/system.data.dataset\(v=vs.100\).aspx) -Container) zu instanziieren. Gemäß den einzelnen, im Bericht verwendeten Datenquellen wird der Entwurfsoberfläche ein [ObjectDataSource](https://msdn.microsoft.com/library/system.web.ui.webcontrols.objectdatasource\(v=vs.100\).aspx) -Steuerelement hinzugefügt. Dieses Datenquellen-Steuerelement wird automatisch konfiguriert.  
  
     Wenn Sie Microsoft Visual Studio 2012 verwenden, stellen Sie sicher, dass das ObjectDataSource-Steuerelement an dataSet1 gebunden ist, das mit dem Project-Namespace voll qualifiziert ist, wenn der voll qualifizierte Name im Dropdown-Listenfeld **Wählen Sie Ihr Geschäftsobjekt** (z. b. projectnamespace. DataSet1TableAdapters. ProductTableAdapter) aufgeführt ist. Um auf das Listenfeld zuzugreifen, klicken Sie mit der rechten Maustaste auf ObjectDataSource, und klicken Sie dann auf **Datenquelle konfigurieren**.  
  
6.  Klicken Sie im Menü Erstellen auf Website erstellen.  
  
     Der Bericht wird kompiliert und alle Fehler, z. B. Syntaxfehler in einem Berichtsausdruck, werden im Bereich **Fehlerliste** angezeigt. Klicken Sie unten im Visual Studio-Fenster auf **Fehlerliste** , um den Bereich **Fehlerliste** anzuzeigen.  
  
## <a name="next-task"></a>Nächste Aufgabe  
 Sie haben der Websiteanwendung erfolgreich ein ReportViewer-Steuerelement hinzugefügt. Als Nächstes fügen Sie dem übergeordneten Bericht eine Drillthroughaktion hinzu.  
  
  
