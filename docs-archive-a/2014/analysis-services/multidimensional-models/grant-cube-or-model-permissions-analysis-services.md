---
title: Erteilen von Cube-oder Modell Berechtigungen (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.roledesignerdialog.cubes.f1
helpviewer_keywords:
- user access rights [Analysis Services], cubes
- cubes [Analysis Services], security
- read/write permissions
- permissions [Analysis Services], cubes
ms.assetid: 55b1456e-2f6b-4101-b316-c926f40304e3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 23e0c5d6c6e70a4ee563ec47562629dd58b0f146
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694794"
---
# <a name="grant-cube-or-model-permissions-analysis-services"></a>Erteilen von Cube- oder Modellberechtigungen (Analysis Services)
  Ein Cube oder tabellarisches Modell ist das primäre Abfrageobjekt in einem Analysis Services-Datenmodell. Wenn sich Benutzer mit mehrdimensionalen oder tabellarischen Daten von Excel aus verbinden, um Daten ad hoc zu untersuchen, beginnen sie in der Regel damit, einen bestimmten Cube oder ein tabellarisches Modell als Datenstruktur hinter dem Pivot-Berichtsobjekt auszuwählen. In diesem Thema wird erklärt, wie die erforderlichen Berechtigungen für den Zugriff auf Cube- oder tabellarische Daten vergeben werden.  
  
 Standardmäßig hat nur der Server- oder Datenbankadministrator die Berechtigung, Cubes in einer Datenbank abzufragen. Der Zugriff auf Cubes durch einen Benutzer, der kein Administrator ist, setzt dessen Mitgliedschaft in einer Rolle voraus, die für die Datenbank, die den Cube enthält, erstellt wurde. Die Mitgliedschaft wird für Windows-Benutzer- oder -Gruppenkonten unterstützt, die entweder in Active Directory oder auf dem lokalen Computer definiert wurden. Bevor Sie beginnen, geben Sie an, welche Konten Mitgliedschaft in den zu erstellenden Rollen erhalten werden.  
  
 `Read`-Zugriff auf einen Cube umfasst auch Berechtigungen für die Dimensionen, Measuregruppen und Perspektiven darin. Die meisten Administratoren gewähren Leseberechtigungen auf Cubeebene und schränken dann die Berechtigungen auf bestimmte Objekte, auf zugehörige Daten oder nach Benutzeridentität ein.  
  
 Um die Rollendefinitionen für weitere Lösungsbereitstellungen beizubehalten, besteht eine bewährte Methode darin, Rollen in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] als integralen Bestandteil des Modells zu definieren, während die Rollenmitgliedschaften nach Veröffentlichung der Datenbank dann von einem Datenbankadministrator in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] zugewiesen werden. Sie können jedoch beide Tools für beide Aufgaben verwenden. Um die Übung einfacher zu gestalten, verwenden wir [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] sowohl für die Rollendefinition als auch für die Mitgliedschaft.  
  
> [!NOTE]  
>  Nur Serveradministratoren, oder Datenbankadministratoren mit Vollzugriff, können einen Cube von Quelldateien auf einem Server bereitstellen bzw. Rollen erstellen und Mitglieder zuweisen. Ausführliche Informationen zu diesen Berechtigungsebenen finden Sie unter [Erteilen von Server Administrator Berechtigungen &#40;Analysis Services&#41;](../instances/grant-server-admin-rights-to-an-analysis-services-instance.md) und [Erteilen von Daten Bank Berechtigungen &#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md) .  
  
#### <a name="step-1-create-the-role"></a>Schritt 1: Erstellen der Rolle  
  
1.  Verbinden Sie sich in SSMS mit Analysis Services. Falls Sie Hilfe bei den Schritten benötigen, lesen Sie unter [Herstellen einer Verbindung von Clientanwendungen &#40;Analysis Services&#41;](../instances/connect-from-client-applications-analysis-services.md) nach.  
  
2.  Öffnen Sie den Ordner **Datenbanken** in Objekt-Explorer, und wählen Sie eine Datenbank aus.  
  
3.  Klicken Sie mit der rechten Maustaste auf **Rollen** , und wählen Sie **Neue Rolle**aus. Beachten Sie, dass Rollen auf Datenbankebene erstellt werden und für die darin enthaltenen Objekte gelten. Sie können Rollen nicht datenbankübergreifend verwenden.  
  
4.  Geben Sie im Bereich **Allgemein** einen Namen und optional eine Beschreibung ein. Dieser Bereich enthält auch mehrere Datenbankberechtigungen wie beispielsweise "Vollzugriff", "Datenbank verarbeiten" und "Definition lesen". Keine dieser Berechtigungen sind für das Abfragen eines Cubes oder tabellarischen Modells erforderlich. Weitere Informationen zu diesen Berechtigungen finden Sie unter [Erteilen von Datenbankberechtigungen &#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md).  
  
5.  Nachdem Sie einen Namen und ggf. eine Beschreibung eingegeben haben, fahren Sie mit dem nächsten Schritt fort.  
  
#### <a name="step-2-assign-membership"></a>Schritt 2: Zuweisen der Mitgliedschaft  
  
1.  Klicken Sie im Bereich **Mitgliedschaft** auf **Hinzufügen** , um die Windows-Benutzer- oder -Gruppenkonten einzugeben, die über diese Rolle auf den Cube zugreifen werden. Analysis Services unterstützt nur Windows-Sicherheitsidentitäten. Beachten Sie, dass in diesem Schritt keine Datenbankanmeldungen erstellt werden. In Analysis Services verbinden sich Benutzer über Windows-Konten.  
  
2.  Fahren Sie mit dem nächsten Schritt fort, um Cubeberechtigungen festzulegen.  
  
     Sie sehen, dass wir den Bereich "Datenquelle" übergehen. Die meisten Benutzer der Daten von Analysis Services benötigen keine Berechtigungen für das Datenquellenobjekt. Einzelheiten zu diesen Berechtigungsebenen finden Sie unter [Erteilen von Berechtigungen für ein Datenquellenobjekt &#40;Analysis Services&#41;](grant-permissions-on-a-data-source-object-analysis-services.md) .  
  
#### <a name="step-3-set-cube-permissions"></a>Schritt 3: Festlegen von Cubeberechtigungen  
  
1.  Wählen Sie im Bereich **Cubes** einen Cube aus, und klicken Sie dann auf `Read` oder **Lese-/Schreibzugriff** .  
  
     `Read`der Zugriff ist für die meisten Vorgänge ausreichend. **Lesen/Schreiben** wird nur zum Rückschreiben, nicht für die Verarbeitung verwendet. Weitere Informationen zu dieser Funktion finden Sie unter [Set Partition Writeback](set-partition-writeback.md) .  
  
     Beachten Sie, dass Sie mehrere Cubes auswählen können sowie andere Objekte, die im Dialogfeld "Rolle erstellen" verfügbar sind. Wenn Sie Berechtigungen für einen Cube erteilen, gewährt dies auch Zugriff auf die Dimensionen und Perspektiven, die mit dem Cube verknüpft sind. Es besteht keine Notwendigkeit, Objekte, die bereits im Cube vorhanden sind, manuell hinzuzufügen.  
  
     Wenn Sie je nach Objekt oder Benutzer andere Berechtigungen vergeben müssen, zum Beispiel, um bestimmte Measures nicht verfügbar zu machen, können Sie Zugriff unteilbar auf bestimmte Objekte (sogar auf Zellen) erlauben oder verweigern. Einzelheiten finden Sie unter [Erteilen von benutzerdefiniertem Zugriff auf Dimensionsdaten &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md) und [Erteilen von benutzerdefiniertem Zugriff auf Zellendaten &#40;Analysis Services&#41;](grant-custom-access-to-cell-data-analysis-services.md).  
  
2.  Wenn Sie nun auf **OK**klicken, haben alle Mitglieder dieser Rolle Zugriff auf die Cubes, und zwar auf den Berechtigungsebenen, die Sie angegeben haben.  
  
     Im Bereich **Cubes** können Sie Benutzern über **Drillthrough und lokaler Cube**die Berechtigung erteilen, lokale Cubes von einem Servercube zu erstellen, oder über die Berechtigung **Drillthrough** nur das Drillthrough erlauben.  
  
     In diesem Bereich können Sie **Datenbank verarbeiten** -Rechte für den Cube gewähren, um allen Mitgliedern dieser Rolle die Möglichkeit zu geben, Daten für diesen Cube zu verarbeiten. Da die Verarbeitung in der Regel ein eingeschränkter Vorgang ist, empfehlen wir, diese Aufgabe den Administratoren zu überlassen oder speziell für diese Aufgabe separate Rollen zu definieren. Weitere Informationen zu Best Practises für Verarbeitungsberechtigungen finden Sie unter [Erteilen von Verarbeitungsberechtigungen &#40;Analysis Services&#41;](grant-process-permissions-analysis-services.md).  
  
#### <a name="step-4-test"></a>Schritt 4: Testen  
  
1.  Verwenden Sie Excel, um die Cube-Zugriffsberechtigungen zu testen. Sie können auch [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]verwenden und dem unten beschriebenen Verfahren folgen, während Sie die Anwendung als Nicht-Administrator ausführen.  
  
    > [!NOTE]  
    >  Wenn Sie Analysis Services-Administrator sind, werden die Administratorberechtigungen mit Rollen kombiniert, die über geringere Berechtigungen verfügen, was das isolierte Testen von Rollenberechtigungen erschwert. Um das Testen zu vereinfachen, sollten Sie eine zweite Instanz von SSMS öffnen, indem Sie das Konto verwenden, das der zu testenden Rolle zugewiesen ist.  
  
2.  Halten Sie die UMSCHALTTASTE gedrückt, und klicken Sie mit der rechten Maustaste auf die Verknüpfung **Excel** , um auf die Option **Als anderer Benutzer ausführen** zuzugreifen. Geben Sie eines der Windows-Benutzer oder -Gruppenkonten ein, die Mitglied dieser Rolle sind.  
  
3.  Wenn Excel geöffnet wird, verbinden Sie sich über die Registerkarte "Daten" mit Analysis Services. Da Sie Excel als anderer Windows-Benutzer ausführen, ist die Option **Windows-Authentifizierung verwenden** der richtige Anmeldeinformationstyp für das Testen von Rollen. Falls Sie Hilfe bei den Schritten benötigen, lesen Sie unter [Herstellen einer Verbindung von Clientanwendungen &#40;Analysis Services&#41;](../instances/connect-from-client-applications-analysis-services.md) nach.  
  
     Wenn bei der Verbindung Fehlermeldungen angezeigt werden, überprüfen Sie die Portkonfiguration für Analysis Services, und vergewissern Sie sich, dass der Server Remoteverbindungen akzeptiert. Weitere Informationen finden [Sie unter Konfigurieren der Windows-Firewall für den Analysis Services Zugriff auf die](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md) Port Konfiguration.  
  
#### <a name="step-5-script-role-definition-and-assignments"></a>Schritt 5: Definition und Zuweisungen der Skriptrolle  
  
1.  Als letzten Schritt sollten Sie ein Skript generieren, in dem die gerade erstellte Rollendefinition erfasst wird.  
  
     Wenn Sie ein Projekt von [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] erneut bereitstellen, werden alle im Projekt nicht definierten Rollen oder Rollenmitgliedschaften überschrieben. Die schnellste Methode zur erneuten Erstellung von Rollen und Rollenmitgliedschaften nach einer erneuten Bereitstellung besteht in der Verwendung eines Skripts.  
  
2.  Navigieren Sie in SSMS zum Ordner **Rollen** , und klicken Sie mit der rechten Maustaste auf eine vorhandene Rolle.  
  
3.  Wählen Sie **Skript für Rolle als**  |  **CREATE TO**  |  **Datei**erstellen aus.  
  
4.  Speichern Sie die Datei unter der Erweiterung ".xmla". Um das Skript zu testen, löschen Sie die aktuelle Rolle, öffnen Sie die Datei in SSMS, und drücken Sie F5, um das Skript auszuführen.  
  
## <a name="next-step"></a>Nächster Schritt  
 Sie können die Cubeberechtigungen verfeinern, um den Zugriff auf Zellen- oder Dimensionsdaten zu beschränken. Einzelheiten finden Sie unter [Erteilen von benutzerdefiniertem Zugriff auf Dimensionsdaten &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md) und [Erteilen von benutzerdefiniertem Zugriff auf Zellendaten &#40;Analysis Services&#41;](grant-custom-access-to-cell-data-analysis-services.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Von Analysis Services unterstützte Authentifizierungsmethoden](../instances/authentication-methodologies-supported-by-analysis-services.md)   
 [Erteilen von Berechtigungen für Data Mining Strukturen und Modelle &#40;Analysis Services&#41;](grant-permissions-on-data-mining-structures-and-models-analysis-services.md)   
 [Erteilen von Berechtigungen für ein Datenquellenobjekt &#40;Analysis Services&#41;](grant-permissions-on-a-data-source-object-analysis-services.md)  
  
  
