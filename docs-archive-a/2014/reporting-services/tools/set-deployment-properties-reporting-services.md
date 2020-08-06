---
title: Festlegen von Bereitstellungseigenschaften (Reporting Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], deploying
- publishing reports [Reporting Services]
- properties [Reporting Services], deployment
- deploying reports [Reporting Services]
ms.assetid: 18201ca0-bf4a-484f-b3a2-95d1046a6a9b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fac1903e4d6738d6a08db55656acba353e4c338d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615259"
---
# <a name="set-deployment-properties-reporting-services"></a>Festlegen von Bereitstellungseigenschaften (Reporting Services)
  In[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]müssen Sie den Berichtsserver und optional die Ordner für Berichte und freigegebene Datenquellen angeben, damit Sie die Elemente in einem Berichtsserverprojekt auf einem Berichtsserver veröffentlichen können. Die Eigenschaften und Werte, die von [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] erstellt werden müssen, und eine Vorschau der bereitgestellten Berichte werden in Projektkonfigurationen des Berichtsserverprojekts gespeichert. Sie können mehrere benannte Mengen für diese Projekteigenschaften erstellen, damit Sie problemlos zwischen Eigenschaftensätzen wechseln können. Jede Eigenschaftsgruppe ist eine Konfiguration. So können Sie z. B. über eine Konfiguration zum Veröffentlichen von Berichten auf einem Testserver und eine andere Konfiguration zum Veröffentlichen von Berichten auf einem Produktionsserver verfügen.  
  
 Verwenden Sie den Konfigurations-Manager, um Gruppen mit Projekteigenschaften in Projektkonfigurationen zu erstellen und zu verwalten. Der Konfigurations-Manager ist eine von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]unterstützte Funktion, auf dem [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] basiert.  
  
> [!NOTE]  
>  Verwechseln Sie diese Funktion nicht mit dem Reporting Services-Konfigurations-Manager, der verwendet wird, um nach der Installation Reporting Services zu konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren und Verwalten eines Berichtsservers (einheitlicher SSRS-Modus)](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md).  
  
> [!NOTE]  
>  In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]wird der Vorgang zur Veröffentlichung von Berichten aus einem Berichtsserverprojekt oder einer Projektmappe als *Bereitstellen von Berichten*bezeichnet.  
  
### <a name="to-set-deployment-properties"></a>So legen Sie Bereitstellungseigenschaften fest  
  
1.  Klicken Sie mit der rechten Maustaste auf das Berichtsprojekt, und klicken Sie anschließend auf **Eigenschaften**.  
  
2.  Wählen Sie im Dialogfeld **Eigenschaftenseiten** für das Projekt in der Liste **Konfiguration** eine Konfiguration aus, die Sie bearbeiten möchten. Häufige Konfigurationen sind **DebugLocal**, **Debug**und **Release**.  
  
    > [!NOTE]  
    >  Sie können mehrere Konfigurationen verwenden, um schnell zwischen verschiedenen Berichtsservern oder Einstellungen zu wechseln.  
  
3.  Im Textfeld **OutputPath** können Sie den Pfad in Ihrem lokalen Dateisystem eingeben oder einfügen, um die in der Buildüberprüfung, Bereitstellung und Berichts Vorschau verwendete Berichtsdefinition zu speichern. Der Pfad muss sich von dem für das Projekt verwendeten Pfad und einem relativen Pfad unterscheiden, der einem untergeordneten Ordner des Projektpfads entspricht.  
  
4.  Geben Sie im Textfeld **ERRORLEVEL** den Schweregrad der Erstellungs Probleme ein, die als Fehler gemeldet werden. Probleme, die bei der Erstellung von Berichten, Datenquellen oder anderen Projektressourcen auftreten, deren Schweregrad kleiner oder gleich dem Wert von **ERRORLEVEL** ist, werden als Fehler gemeldet. Andernfalls werden die Probleme als Warnungen gemeldet. Jeder Fehler führt dazu, dass die Erstellung fehlschlägt. Die gültigen Schweregrade sind 0 bis einschließlich 4. Der Standardwert ist 2.  
  
     **ErrorLevel** kann verwendet werden, um die Vertraulichkeit des Berichterstellung zu erhöhen oder zu verringern. Wenn beispielsweise ein Bericht mit einer Karte während der Bereitstellung auf einem [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] -Berichtsserver erstellt wird, wird standardmäßig ein Fehler angezeigt, und der Bericht wird nicht erstellt. Wenn Sie **ErrorLevel** herabsetzen, wird die Karte aus dem Bericht entfernt, eine Warnung angezeigt und die Berichterstellung fortgesetzt.  
  
5.  Wählen Sie in der Liste **StartItem** einen Bericht aus, der im Vorschaufenster oder in einem Browserfenster angezeigt werden soll, wenn das Berichts Projekt ausgeführt wird.  
  
6.  Wählen Sie in der Liste **OverwriteDataSources** den Wert **TRUE** aus, um bei jedem Veröffentlichen von freigegebenen Datenquellen die freigegebene Datenquelle auf dem Server zu überschreiben, oder wählen Sie **FALSE** aus, um die Datenquelle auf dem Server beizubehalten.  
  
7.  Wählen Sie in der Liste **targetserverversion** entweder die-oder die- [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Version von aus, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] oder wählen Sie **Version erkennen** aus, um automatisch die Version zu ermitteln, die auf dem durch die Eigenschaft **TargetServer URL** identifizierten Server installiert ist. Der Standardwert ist **SQL Server 2008 R2**.  
  
     Verwenden Sie **TargetServerVersion** , um die erstellten Berichte unter dem in OutputPath angegebenen Pfad für die Version des Berichtsservers anzupassen, der in **TargetServerURL**angegeben ist.  
  
8.  Geben Sie im Textfeld **TargetDataSourceFolder** den Ordner auf dem Berichtsserver ein, in dem die veröffentlichten, freigegebenen Datenquellen gespeichert werden sollen. Der Standardwert für **TargetDataSourceFolder** lautet Datenquellen. Wenn Sie hierfür keinen Wert angeben, werden die Datenquellen an dem in **TargetReportFolder**angegebenen Speicherort veröffentlicht.  
  
9. Geben Sie im Textfeld **TargetReportFolder** den Ordner auf dem Berichtsserver ein, in dem die veröffentlichten Berichte gespeichert werden sollen. Der Standardwert für **TargetReportFolder** ist der Name des Berichts Projekts.  
  
    > [!NOTE]  
    >  Für einen Berichtsserver, der im einheitlichen Modus ausgeführt wird, müssen Sie im Zielordner über Berechtigungen zum **Veröffentlichen** verfügen, um Berichte in diesem Ordner zu veröffentlichen. Berechtigungen zum Veröffentlichen werden über eine Rollenzuweisung erteilt, bei der das Benutzerkonto einer Rolle zugeordnet wird, die Veröffentlichungsvorgänge enthalt. Weitere Informationen finden Sie unter [Erstellen und Verwalten von Rollenzuweisungen](../security/create-and-manage-role-assignments.md). Für einen Berichtsserver, der im integrierten SharePoint-Modus ausgeführt wird, müssen Sie auf der SharePoint-Website über Berechtigungen als **Mitglied** oder **Eigentümer** verfügen. Weitere Informationen finden Sie unter [Referenz zu SharePoint Website- und Listenberechtigungen für Berichtsserverelemente](../security/sharepoint-site-and-list-permission-reference-for-report-server-items.md).  
  
10. Geben Sie im Textfeld **TargetServerURL** die URL des Zielberichtsservers ein. Diese Eigenschaft müssen Sie vor dem Veröffentlichen eines Berichts auf eine gültige URL eines Berichtsservers festlegen. Wenn Sie auf einem Berichtsserver veröffentlichen, der im einheitlichen Modus ausgeführt wird, verwenden Sie die URL des virtuellen Verzeichnisses des Berichtsservers (z.B. http: *//Server/Berichtsserver* oder https: *//Server/Berichtsserver)* . Dies ist das virtuelle Verzeichnis des Berichtsservers, nicht des Berichts-Managers.  
  
     Verwenden Sie eine URL für eine SharePoint-Stammwebsite oder -Unterwebsite, wenn der Bericht auf einem Berichtsserver veröffentlicht wird, der im integrierten SharePoint-Modus ausgeführt wird. Wenn Sie keine Website angeben, wird die Standard Website der obersten Ebene verwendet (z. b. http://*Servername*, http://*Servername* / *Site* oder http://*Servername* / *Site* / *unter Website*).  
  
### <a name="to-set-configuration-manager-properties"></a>So legen Sie Konfigurations-Manager-Eigenschaften fest  
  
1.  Klicken Sie mit der rechten Maustaste auf das Berichtsprojekt, und klicken Sie anschließend auf **Eigenschaften**.  
  
2.  Klicken Sie im Dialogfeld **Eigenschaftenseiten** für das Projekt auf **Konfigurations-Manager**.  
  
3.  Wählen Sie im Dialogfeld **Konfigurations-Manager** die zu bearbeitende Konfiguration aus. Die derzeit aktive Konfiguration wird als **aktiv ( ***\<configuration>*** )** angezeigt.  
  
4.  Aktivieren oder deaktivieren Sie unter **Projektkontext**für jedes Projekt der Projektmappe **Erstellen** oder **Bereitstellen**.  
  
    > [!NOTE]  
    >  Wenn **Erstellen** ausgewählt ist, erstellt der Berichts-Designer das Berichtsprojekt und überprüft es auf Fehler, bevor es auf einem Berichtsserver veröffentlicht oder eine Vorschau angezeigt wird. Wenn **Bereitstellen** ausgewählt ist, veröffentlicht der Berichts-Designer die Berichte gemäß der Definition in den Bereitstellungseigenschaften auf dem Berichtsserver. Wenn **Bereitstellen** nicht ausgewählt ist, zeigt der Berichts-Designer den in der **StartItem** -Eigenschaft angegebenen Bericht in einem lokalen Vorschaufenster an.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Veröffentlichen von Datenquellen und Berichten](../reports/publishing-data-sources-and-reports.md)   
 [Anzeigen einer Vorschau für Berichte](../reports/previewing-reports.md)   
 [Berichts-Designer F1-Hilfe](report-designer-f1-help.md)   
 [URL-Beispiele für veröffentlichte Berichts Elemente auf einem Berichts Server im SharePoint-Modus &#40;SSRS&#41;](url-examples-for-items-on-a-report-server-sharepoint-mode.md)   
 [Eigenschaften Seiten für Projekt (Dialog Feld)](project-property-pages-dialog-box.md)   
 [Veröffentlichen von Berichten auf einem Berichtsserver](../reports/publishing-reports-to-a-report-server.md)  
  
  
