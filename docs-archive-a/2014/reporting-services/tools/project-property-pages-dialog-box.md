---
title: Eigenschaftenseiten für das Projekt (Dialogfeld) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rpt.rptdesigner.projectpropertypages.general.f1
helpviewer_keywords:
- Project Property Pages dialog box
ms.assetid: 209d9e22-37fc-418f-8739-83adcf447d3f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6ae5ab7c68c9a95759d27ca2785f99377c98942a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700677"
---
# <a name="project-property-pages-dialog-box"></a>Projekt (Eigenschaftenseiten, Dialogfeld)
  Mithilfe der Eigenschaftenseiten für Projekte können Sie Bereitstellungseigenschaften für ein Berichtsserverprojekt konfigurieren. Um dieses Dialogfeld zu öffnen, klicken Sie im Menü **Projekt** auf _\<Report Project Name>_ **Eigenschaften**.  
  
 Nachdem Sie Konfigurationseigenschaften definiert haben, können Sie auf der Symbolleiste aus der Dropdownliste **Projektmappenkonfigurationen** eine Konfiguration auswählen.  
  
## <a name="options"></a>Tastatur  
 **Konfiguration**  
 Wählen Sie die zu bearbeitende Konfiguration aus. Anfangs sind folgende Konfigurationen verfügbar: **Debuggen**, **DebugLocal**und **Release**. Die aktive Konfiguration wird zuerst angezeigt, z.B. **Aktiv (Debuggen)**.  
  
 Um Eigenschaften für mehr als eine Konfiguration gleichzeitig anzuzeigen, wählen Sie **Alle Konfigurationen** oder **Mehrere Konfigurationen**aus.  
  
 Klicken Sie zum Erstellen weiterer Konfigurationen auf der Menüleiste auf **Konfigurations-Manager** .  
  
 **Konfigurations-Manager**  
 Verwalten Sie Konfigurationen für die gesamte Projektmappe, oder fügen Sie zusätzliche Konfigurationen hinzu. Weitere Informationen finden Sie in der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Dokumentation.  
  
 **OutputPath**  
 Sie können den Pfad zum Speichern der Berichtsdefinition, die in der Erstellungsüberprüfung, Bereitstellung und Berichtsvorschau verwendet wird, eingeben oder einfügen. Der Pfad muss sich von dem für das Projekt verwendeten Pfad und einem relativen Pfad unterscheiden, der einem untergeordneten Ordner des Projektpfads entspricht.  
  
> [!NOTE]  
>  Sie können mehrere Konfigurationen verwenden, um abhängig von der auszuführenden Aufgabe unter verschiedenen Pfaden zu wechseln.  
  
 **ERRORLEVEL**  
 Geben Sie den Schweregrad der Erstellungsprobleme ein, die als Fehler gemeldet werden. Probleme mit einem Schweregrad kleiner oder gleich dem Wert von **ErrorLevel** werden als Fehler gemeldet. Andernfalls werden die Probleme als Warnungen gemeldet. Jeder Fehler führt dazu, dass die Erstellung fehlschlägt. Die gültigen Schweregrade sind 0 bis einschließlich 4. Der Standardwert ist 2.  
  
 **StartItem**  
 Wählen Sie den Bericht aus, der nach der Veröffentlichung des Projekts auf dem Berichtsserver im Webbrowser oder beim Ausführen des Projekts auf dem lokalen Computer im Vorschaufenster angezeigt wird. Ein Startelement ist für Konfigurationen erforderlich, die das Projekt zwar erstellen, nicht jedoch bereitstellen sowie für die Verwendung des **Debug** -Befehls (**F5**). Dieser Schritt ist für Konfigurationen notwendig, die das Projekt bereitstellen.  
  
 **OverwriteDataSources**  
 Wählen Sie **TRUE** aus, um die Datenquelle auf dem Server mit der Datenquelle im Projekt zu überschreiben, wenn die Berichte veröffentlicht werden. Wählen Sie **False** aus, um die vorhandene Datenquelle auf dem Server zu belassen.  
  
 **TargetServerVersion**  
 Wählen Sie entweder die- [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Version oder die- [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Version von aus [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , oder wählen Sie **Version erkennen** aus, um automatisch **TargetServer URL** die Version zu ermitteln, die auf dem Server installiert ist, der von der Eigenschaft Der Standardwert ist **SQL Server 2008 R2**.  
  
 **TargetDataSourceFolder**  
 Der Name des Ordners, in dem die veröffentlichten, freigegebenen Datenquellen gespeichert werden sollen. Wenn Sie keinen Ordner angeben, wird die Datenquelle im gleichen Ordner wie der Bericht veröffentlicht. Falls der Ordner nicht auf dem Berichtsserver vorhanden ist, erstellt der Berichts-Designer den Ordner, wenn die Berichte veröffentlicht werden.  
  
 Wenn Sie auf einem Berichtsserver veröffentlichen, der im einheitlichen Modus ausgeführt wird, geben Sie den vollständigen Pfad der Ordnerhierarchie mit Beginn beim Stamm an. Beispielsweise Folder1/Folder2/Folder3.  
  
 Wenn Sie auf einem Berichtsserver veröffentlichen, der im integrierten SharePoint-Modus ausgeführt wird, verwenden Sie eine URL zur SharePoint-Bibliothek. Beispielsweise http:// *\<servername>/\<site>* /Documents/MyFolder.  
  
 **TargetReportFolder**  
 Der Name des Ordners, in dem die veröffentlichten Berichte gespeichert werden sollen. Standardmäßig ist dies der Name des Berichtsprojekts. Falls der Ordner nicht auf dem Berichtsserver vorhanden ist, erstellt der Berichts-Designer den Ordner, wenn die Berichte veröffentlicht werden.  
  
 Wenn Sie auf einem Berichtsserver veröffentlichen, der im einheitlichen Modus ausgeführt wird, geben Sie den vollständigen Pfad der Ordnerhierarchie mit Beginn beim Stamm an. Wenn ein Ordner in einem anderen Ordner enthalten ist, geben Sie den Pfad zum Ordner mit Beginn beim Stamm an, wie beispielsweise Folder1/Folder2/Folder3.  
  
 Wenn Sie auf einem Berichtsserver veröffentlichen, der im integrierten SharePoint-Modus ausgeführt wird, verwenden Sie eine URL zur SharePoint-Bibliothek. Beispielsweise http:// *\<servername>* / *\<site>* /Documents/MyFolder.  
  
 **TargetServerURL**  
 Die URL des Zielberichtsservers. Diese Eigenschaft müssen Sie vor dem Veröffentlichen eines Berichts auf eine gültige URL eines Berichtsservers festlegen.  
  
 Verwenden Sie die URL des virtuellen Verzeichnisses des Berichtsservers, wenn der Bericht auf einem Berichtsserver veröffentlicht wird, der im einheitlichen Modus ausgeführt wird. Beispielsweise http:// \<server> /reportserver. Dies ist das virtuelle Verzeichnis des Berichtsservers, nicht des Berichts-Managers. Standardmäßig wird der Berichtsserver in dem virtuellen Verzeichnis "reportserver" installiert.  
  
 Verwenden Sie eine URL für eine SharePoint-Stammwebsite oder -Unterwebsite, wenn der Bericht auf einem Berichtsserver veröffentlicht wird, der im integrierten SharePoint-Modus ausgeführt wird. Wenn Sie keine Website angeben, wird die standardmäßige Stammwebsite verwendet. Beispiel: http:// \<*servername> *, http://#b0 *Servername */\<*site>* oder http:// \<*servername> */\<*site>* / \<*subsite> *.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Veröffentlichen von Berichten](../publish-reports.md)   
 [Veröffentlichen eines Berichts in einer SharePoint-Bibliothek](../reports/publish-a-report-to-a-sharepoint-library.md)   
 [Festlegen der Bereitstellungs Eigenschaften &#40;Reporting Services&#41;](set-deployment-properties-reporting-services.md)   
 [Berichts-Designer (F1-Hilfe)](report-designer-f1-help.md)  
  
  
