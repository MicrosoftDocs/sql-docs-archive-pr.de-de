---
title: Installieren von Beispiel Daten und-Projekten für das Analysis Services Tutorial zur mehrdimensionalen Modellierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: fc475b25-cbb2-408a-901f-9299299538c5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 196f9bad945c69cbc77d2a5dc41a5333e58b33fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87618401"
---
# <a name="install-sample-data-and-projects-for-the-analysis-services-multidimensional-modeling-tutorial"></a>Installieren von Beispieldaten und -projekten für das Analysis Services-Lernprogramm zur mehrdimensionalen Modellierung
  Verwenden Sie die Anweisungen und Links in diesem Thema, um alle Daten- und Projektdateien zu installieren, die in den Analysis Services-Lernprogrammen verwendet werden.  
  
## <a name="step-1-install-sql-server-software"></a>Schritt 1: Installieren der SQL Server-Software  
 In den Lektionen dieses Lernprogramms wird vorausgesetzt, dass Sie folgende Software installiert haben. Sämtliche folgende Software wird mit dem SQL Server-Installationsmedium installiert. Zur Vereinfachung der Bereitstellung können Sie alle Funktionen auf einem einzelnen Computer installieren. Um diese Funktionen zu installieren, führen Sie SQL Server-Setup aus, und wählen Sie auf der Seite Funktionsauswahl diese Funktionen aus. Weitere Informationen finden Sie unter [Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md).  
  
-   Datenbank-Engine  
  
-   Analysis Services  
  
     Analysis Services ist nur in der Evaluation, Enterprise, Business Intelligence und Standard Edition verfügbar.  
  
     In den Express-Editionen von SQL Server ist Analysis Services nicht enthalten. [Laden Sie die Evaluation Edition herunter](https://go.microsoft.com/fwlink/?LinkId=392824) , um die Software kostenlos zu testen.  
  
     Analysis Services wird standardmäßig als mehrdimensionale Instanz installiert. Sie können diesen Modus überschreiben, indem Sie im Installations-Assistenten auf der Seite für die Serverkonfiguration den tabellarischen Servermodus auswählen. Falls Sie beide Servermodi ausführen möchten, führen Sie SQL Server-Setup auf demselben Computer erneut aus, um eine zweite Analysis Services-Instanz im anderen Modus zu installieren.  
  
-   SQL Server Management Studio  
  
 Sie können Excel optional installieren, um mehrdimensionale Daten zu durchsuchen, während Sie das Lernprogramm ausführen. Durch die Installation von Excel wird die Funktion **In Excel analysieren** aktiviert. Diese startet Excel mit einer PivotTable-Feldliste, die mit dem Cube verbunden ist, den Sie erstellen. Es wird empfohlen, zum Durchsuchen von Daten Excel zu verwenden, da Sie schnell einen Pivotbericht erstellen können, der Ihnen das Interagieren mit den Daten ermöglicht.  
  
 Alternativ können Sie Daten mithilfe des integrierten MDX-Abfrage-Designers durchsuchen, der in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]integriert ist. Der Abfrage-Designer gibt die gleichen Daten zurück, jedoch werden die Daten als flaches Rowset dargestellt.  
  
## <a name="step-2-download-sql-server-data-tools---business-intelligence-for-visual-studio-2012"></a>Schritt 2: Herunterladen von SQL Server Data Tools-Business Intelligence für Visual Studio 2012  
 In dieser Version wird SQL Server Data Tools getrennt von anderen SQL Server-Funktionen heruntergeladen und installiert. Die zum Erstellen von BI-Modellen und -Berichten verwendeten Designer und Projektvorlagen sind nun als kostenloser Webdownload verfügbar.  
  
-   [Laden Sie die Business Intelligence-Version von SQL Server Data Tools herunter](https://go.microsoft.com/fwlink/p/?LinkID=322038). Die Datei wird im Ordner Downloads gespeichert. Führen Sie Setup aus, um das Tool zu installieren.  
  
     Starten Sie den Computer neu, um die Installation abzuschließen.  
  
## <a name="step-3-install-databases"></a>Schritt 3: Installieren von Datenbanken  
 In einem mehrdimensionalen Analysis Services-Modell werden Transaktionsdaten verwendet, die Sie aus einem Managementsystem für relationale Datenbanken importieren. In diesem Lernprogramm verwenden Sie die folgende relationale Datenbank als Datenquelle.  
  
-   **AdventureWorksDW2012** : Dies ist eine relationale Data Warehouse, die auf einer Datenbank-Engine-Instanz ausgeführt wird. Es enthält die ursprünglichen Daten, die in den Analysis Services-Datenbanken und -Projekten verwendet werden, die Sie im gesamten Lernprogramm erstellen und bereitstellen.  
  
     Sie können diese Beispieldatenbank mit [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] und [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]verwenden.  
  
 Gehen Sie zum Installieren dieser Datenbank wie folgt vor:  
  
1.  Laden Sie die [AdventureWorkDW2012](https://go.microsoft.com/fwlink/p/?LinkID=221770) -Datenbank von der Seite mit Produktbeispielen auf Codeplex herunter.  
  
     Der Datenbankdateiname ist AdvntureWorksDW2012_Data.mdf. Die Datei sollte sich im Ordner Downloads auf dem Computer befinden.  
  
2.  Kopieren Sie die Datei"AdventureWorksDW2012_Data.mdf" in das Datenverzeichnis der lokalen Instanz der SQL Server-Datenbank-Engine. Der Standardpfad lautet: C:\Programme\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Data.  
  
3.  Starten Sie SQL Server Management Studio, und stellen Sie eine Verbindung mit der Datenbank-Engine-Instanz her.  
  
4.  Klicken Sie mit der rechten Maustaste auf die Datenbank, und klicken Sie auf **Anfügen**.  
  
5.  Klicken Sie auf **Hinzufügen**.  
  
6.  Wählen Sie die Datenbankdatei **AdventureWorksDW2012_Data.mdf** aus, und klicken Sie auf **OK**. Wenn die Datei nicht aufgeführt ist, überprüfen Sie, ob sie im Ordner C:\Programme\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Data enthalten ist.  
  
7.  Entfernen Sie in den Datenbankdetails den Eintrag für die Protokolldatei. Das Setupprogramm geht davon aus, dass Sie über eine Protokolldatei verfügen, allerdings wird im Beispiel keine Protokolldatei verwendet. Wenn Sie die Datenbank anfügen, wird automatisch eine neue Protokolldatei erstellt. Wählen Sie die Protokolldatei aus, klicken Sie auf **Entfernen**, und klicken Sie anschließend auf **OK** , um nur die primäre Datenbankdatei anzufügen.  
  
## <a name="step-4-grant-database-permissions"></a>Schritt 4: Gewähren von Datenbankberechtigungen  
 In den Beispielprojekten werden Einstellungen für den Datenquellenidentitätswechsel verwendet, die den Sicherheitskontext angeben, unter dem Daten importiert oder verarbeitet werden. Standardmäßig geben die Identitätswechseleinstellungen das Analysis Services-Dienstkonto für den Zugriff auf die Daten an. Um diese Standardeinstellung zu verwenden, müssen Sie sicherstellen, dass das Dienstkonto, unter dem Analysis Services ausgeführt wird, über Datenleserberechtigungen für die Datenbank **AdventureWorksDW2012** verfügt.  
  
> [!NOTE]  
>  Um den Lerneffekt zu verbessern, wird empfohlen, die standardmäßige Identitätswechseloption für das Dienstkonto zu verwenden und dem Dienstkonto in SQL Server Datenleserberechtigungen zu erteilen. Es sind zwar weitere Identitätswechseloptionen verfügbar, jedoch sind nicht alle von ihnen für Verarbeitungsvorgänge geeignet. Insbesondere wird die Option zum Verwenden der Anmeldeinformationen des aktuellen Benutzers nicht für Verarbeitungsvorgänge unterstützt.  
  
1.  Bestimmen Sie das Dienstkonto. Sie können Kontoinformationen mit dem SQL Server-Konfigurations-Manager oder der Konsolenanwendung Dienste anzeigen. Wenn Sie Analysis Services als Standardinstanz installiert haben, wird der Dienst als **NT Service\MSSQLServerOLAPService**ausgeführt.  
  
2.  Stellen Sie in Management Studio eine Verbindung mit der Datenbank-Engine-Instanz her.  
  
3.  Erweitern Sie den Knoten Sicherheit, klicken Sie mit der rechten Maustaste auf Anmeldungen, und wählen Sie **Neue Anmeldung**aus.  
  
4.  Geben Sie auf der Seite Allgemein in Anmeldename den Namen **NT Service\MSSQLServerOLAPService** (bzw. den Namen des Kontos, unter dem der Dienst ausgeführt wird) ein.  
  
5.  Klicken Sie auf **Benutzerzuordnung**.  
  
6.  Aktivieren Sie das Kontrollkästchen neben der Datenbank **AdventureWorksDW2012** . Zu den Mitgliedern der Rolle sollten automatisch **db_datareader** und **public**gehören. Klicken Sie auf **OK** , um die Standardeinstellungen zu übernehmen.  
  
## <a name="step-5-install-projects"></a>Schritt 5: Installieren von Projekten  
 Das Lernprogramm enthält Beispielprojekte, damit Sie Ihre Ergebnisse mit einem fertigen Projekt vergleichen oder eine fortgeschrittenere Lektion beginnen können.  
  
 Die Projektdatei für Lektion 4 ist besonders wichtig, da sie die Grundlage nicht nur für diese Lektion, sondern für alle nachfolgenden Lektionen bildet. Im Gegensatz zu den vorherigen Projektdateien, bei denen mit den Schritten im Lernprogramm eine genaue Kopie der abgeschlossenen Projektdateien erstellt wird, enthält das Beispielprojekt für Lektion 4 neue Modellinformationen, die in dem Modell, das Sie in Lektion 1 bis 3 erstellt haben, nicht enthalten sind. In Lektion 4 wird davon ausgegangen, dass Sie mit einer Beispielprojektdatei beginnen, die im folgenden Download verfügbar ist.  
  
1.  Laden Sie [Analysis Services Tutorial SQL Server 2012](https://go.microsoft.com/fwlink/p/?LinkID=221866) von der Seite mit Produktbeispielen auf Codeplex herunter.  
  
     Die Lernprogramme der Version 2012 sind für die [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] -Version geeignet.  
  
     Die Datei "Analysis Services Tutorial SQL Server 2012.zip" wird im Ordner "Downloads" auf dem Computer gespeichert.  
  
2.  Verschieben Sie die ZIP-Datei in einen Ordner direkt unterhalb des Stammlaufwerks (beispielsweise C:\Tutorial). Durch diesen Schritt wird der "Pfad zu lang"-Fehler verringert, der manchmal auftritt, wenn Sie versuchen, die Dateien im Ordner "Downloads" zu entzippen.  
  
3.  Entzippen der Beispielprojekte: Klicken Sie mit der rechten Maustaste auf die Datei, und wählen Sie **Alle extrahieren**aus. Nachdem Sie die Dateien extrahiert haben, sollten auf dem Computer die folgenden Projekte installiert sein:  
  
    -   Lesson 1 Complete  
  
    -   Lesson 2 Complete  
  
    -   Lesson 3 Complete  
  
    -   Lesson 4 Complete  
  
    -   Lesson 4 Start  
  
    -   Lesson 5 Complete  
  
    -   Lesson 6 Complete  
  
    -   Lesson 7 Complete  
  
    -   Lesson 8 Complete  
  
    -   Lesson 9 Complete  
  
    -   Lesson 10 Complete  
  
4.  Entfernen Sie den Schreibschutz dieser Dateien. Klicken Sie mit der rechten Maustaste auf den übergeordneten Ordner „Analysis Services Tutorial SQL Server 2012“, wählen Sie **Eigenschaften**aus, und deaktivieren Sie das Kontrollkästchen **Schreibgeschützt**. Klicken Sie auf **OK**. Wenden Sie die Änderungen auf diesen Ordner sowie Unterordner und Dateien an.  
  
5.  Starten Sie [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
6.  Öffnen Sie die Projektmappendatei (.sln), die der von Ihnen verwendeten Lektion entspricht. Im Ordner mit der Bezeichnung Lesson 1 Complete würden Sie z. B. die Datei Analysis Services Tutorial.sln öffnen.  
  
7.  Stellen Sie die Projektmappe bereit, um zu überprüfen, ob die Datenbankberechtigungen und die Informationen zum Serverspeicherort ordnungsgemäß eingerichtet sind.  
  
     Wenn Analysis Services und die Datenbank-Engine als Standardinstanz (MSSQLServer) installiert sind und sämtliche Software auf demselben Computer ausgeführt wird, können Sie im Menü Erstellen auf **Projektmappe bereitstellen** klicken, um das Beispielprojekt zu erstellen und auf der lokalen Instanz von Analysis Services bereitzustellen. Während der Bereitstellung werden Daten aus der Datenbank **AdventureWorksDW2012** in der lokalen Instanz der Datenbank-Engine verarbeitet (oder importiert). Auf der Analysis Services-Instanz, die die von der Datenbank-Engine abgerufenen Daten enthält, wird eine neue Analysis Services-Datenbank erstellt.  
  
     Wenn Fehler auftreten, überprüfen Sie die vorherigen Schritte zum Einrichten von Datenbankberechtigungen. Zusätzlich müssen u. U. auch Servernamen geändert werden. Der Standardservername lautet "localhost". Wenn die Server auf Remotecomputern oder als benannte Instanzen installiert werden, müssen Sie den Standardnamen mit einem für Ihre Installation gültigen Servernamen überschreiben. Wenn sich die Server auf Remotecomputern befinden, müssen Sie möglicherweise außerdem die Windows-Firewall so konfigurieren, dass sie den Zugriff auf die Server zulässt.  
  
     Der Servername für Verbindungen mit der Datenbank-Engine wird im Datenquellenobjekt der mehrdimensionalen Projektmappe (Adventure Works-Lernprogramm) angegeben und im Projektmappen-Explorer angezeigt.  
  
     Der Servername für Verbindungen mit Analysis Services wird in den Eigenschaftenseiten des Projekts auf der Registerkarte Bereitstellung angegeben und ebenfalls im Projektmappen-Explorer angezeigt.  
  
8.  Starten Sie SQL Server Management Studio. Stellen Sie in SQL Server Management Studio eine Verbindung mit Analysis Services her. Überprüfen Sie, ob auf dem Server eine Datenbank mit dem Namen **Analysis Services Tutorial** ausgeführt wird.  
  
## <a name="next-step"></a>Nächster Schritt  
 Jetzt können Sie das Lernprogramm verwenden. Weitere Informationen für den Einstieg finden Sie unter [Mehrdimensionale Modellierung &#40;Adventure Works-Tutorial&#41;](multidimensional-modeling-adventure-works-tutorial.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Installieren Sie SQL Server 2014 über den Installations-Assistenten &#40;Setup&#41;](../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)   
 [Konfigurieren der Windows-Firewall für den Analysis Services Zugriff](instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)   
 [Konfigurieren der Windows-Firewall für den SQL Server-Zugriff](../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)  
  
  
