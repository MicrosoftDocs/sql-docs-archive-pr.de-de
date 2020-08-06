---
title: Integration Services projektkonvertierungs-Assistent | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.migrationwizard.f1
ms.assetid: a192b094-4d0f-4c21-b911-460ec844a49f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c47dc8ed1d0485a62128be732cc34de1dca35740
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87618172"
---
# <a name="integration-services-project-conversion-wizard"></a>Assistent für die Konvertierung von Integration Services-Projekten
  Der Assistent für die Konvertierung von **Integration Services-Projekten** konvertiert ein Projekt ins Projektbereitstellungsmodell.  
  
> [!NOTE]  
>  Wenn das Projekt mindestens eine Datenquelle enthält, werden die Datenquellen entfernt, wenn die Projektkonvertierung abgeschlossen wird. Fügen Sie einen Verbindungs-Manager auf Projektebene hinzu, um eine Verbindung mit einer Datenquelle herzustellen, die von den Paketen im Projekt gemeinsam genutzt werden kann. Weitere Informationen finden Sie unter [Hinzufügen, Löschen oder Freigeben eines Verbindungs-Managers in einem Paket](../../2014/integration-services/add-delete-or-share-a-connection-manager-in-a-package.md)  
  
 **Was möchten Sie tun?**  
  
-   [Öffnen des Assistenten für die Konvertierung von Integration Services-Projekten](#open_dialog)  
  
-   [Festlegen von Optionen auf der Seite "Pakete suchen"](#locate)  
  
-   [Festlegen von Optionen auf der Seite "Pakete auswählen"](#selectPackages)  
  
-   [Festlegen von Optionen auf der Seite "Ziel auswählen"](#destination)  
  
-   [Festlegen von Optionen auf der Seite "Projekteigenschaften angeben"](#projectProperties)  
  
-   [Festlegen von Optionen auf der Seite "Task 'Paket ausführen' aktualisieren"](#executePackage)  
  
-   [Festlegen von Optionen auf der Seite "Konfigurationen auswählen"](#configurations)  
  
-   [Festlegen von Optionen auf der Seite "Parameter erstellen"](#createParameters)  
  
-   [Festlegen von Optionen auf der Seite "Parameter konfigurieren"](#configureParameters)  
  
-   [Festlegen der Optionen auf der Seite zum Überprüfen](#review)  
  
-   [Festlegen der Optionen unter "Konvertierung ausführen"](#conversion)  
  
##  <a name="open-the-integration-services-project-conversion-wizard"></a><a name="open_dialog"></a>Assistent zum Konvertieren von Integration Services Projekten öffnen  
 Führen Sie einen der folgenden Schritte aus, um den Assistenten zum Konvertieren von **Integration Services-Projekten** zu öffnen.  
  
-   Öffnen Sie das Projekt in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], und klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt. Klicken Sie anschließend auf **In Projektbereitstellungsmodell konvertieren**.  
  
-   Klicken Sie im Objekt-Explorer in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]mit der rechten Maustaste auf den Knoten **Projekte** , und wählen Sie anschließend die Option **Pakete importieren**aus.  
  
 Abhängig davon, ob Sie den Assistenten zum Konvertieren von **Integration Services-Projekten** von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oder von [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]ausführen, führt der Assistent unterschiedliche Konvertierungstasks aus. Weitere Informationen finden Sie unter [Deploy Projects to Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md).  
  
##  <a name="set-options-on-the-locate-packages-page"></a><a name="locate"></a>Festlegen von Optionen auf der Seite "Pakete suchen"  
  
> [!NOTE]  
>   Die Seite **Pakete suchen** ist nur verfügbar, wenn Sie den Assistenten über [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]ausführen.  
  
 Die folgende Option wird auf der Seite angezeigt, wenn Sie **Dateisystem** in der Dropdownliste **Quelle** auswählen. Wählen Sie diese Option, wenn das Paket im Dateisystem gespeichert ist.  
  
 **Ordner**  
 Geben Sie den Paketpfad ein, oder navigieren Sie zum Paket, indem Sie auf **Durchsuchen**klicken.  
  
 Die folgenden Optionen werden auf der Seite angezeigt, wenn Sie **SSIS-Paketspeicher** in der Dropdownliste **Quelle** auswählen. Weitere Informationen zum Paketspeicher finden Sie unter [Paketverwaltung &#40;SSIS-Dienst&#41;](service/package-management-ssis-service.md).  
  
 **Server**  
 Geben Sie einen Servernamen ein, oder wählen Sie den Server aus.  
  
 **Ordner**  
 Geben Sie den Paketpfad ein, oder navigieren Sie zum Paket, indem Sie auf **Durchsuchen**klicken.  
  
 Die folgenden Optionen werden auf der Seite angezeigt, wenn Sie **Microsoft SQL Server** in der Dropdownliste **Quelle** auswählen. Wählen Sie diese Option aus, wenn das Paket in Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]gespeichert ist.  
  
 **Server**  
 Geben Sie einen Servernamen ein, oder wählen Sie den Server aus.  
  
 **Windows-Authentifizierung verwenden**  
 Der Microsoft Windows-Authentifizierungsmodus ermöglicht Benutzern das Herstellen einer Verbindung über ein Windows-Benutzerkonto. Wenn Sie die Windows-Authentifizierung verwenden, müssen Sie keinen Benutzernamen und kein Kennwort angeben.  
  
 **SQL Server Authentifizierung verwenden**  
 Wenn ein Benutzer eine Verbindung mit einem angegebenen Benutzernamen und einem Kennwort von einer nicht vertrauenswürdigen Verbindung herstellt, authentifiziert [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] die Verbindung, indem überprüft wird, ob ein [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Anmeldekonto eingerichtet wurde und ob das angegebene Kennwort mit dem zuvor aufgezeichneten übereinstimmt. Wenn kein Anmeldekonto in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] eingerichtet wurde, schlägt die Authentifizierung fehl, und der Benutzer erhält eine Fehlermeldung.  
  
 **Benutzername**  
 Geben Sie einen Benutzernamen an, wenn Sie die SQL Server-Authentifizierung verwenden.  
  
 **Kennwort**  
 Geben Sie das Kennwort ein, wenn Sie die SQL Server-Authentifizierung verwenden.  
  
 **Ordner**  
 Geben Sie den Paketpfad ein, oder navigieren Sie zum Paket, indem Sie auf **Durchsuchen**klicken.  
  
##  <a name="set-options-on-the-select-packages-page"></a><a name="selectPackages"></a>Festlegen von Optionen auf der Seite "Pakete auswählen"  
 **Paketname**  
 Listet die Paketdatei auf.  
  
 **Status**  
 Gibt an, ob ein Paket bereit ist, in das Projektbereitstellungsmodell konvertiert zu werden.  
  
 **Meldung**  
 Zeigt eine Meldung an, die dem Paket zugeordnet sind.  
  
 **Kennwort**  
 Zeigt ein Kennwort an, das dem Paket zugeordnet sind. Der Kennworttext ist ausgeblendet.  
  
 **Auf Auswahl anwenden**  
 Klicken Sie, um das Kennwort im Textfeld **Kennwort** auf das bzw. die ausgewählten Pakete anzuwenden.  
  
 **Aktualisieren**  
 Aktualisiert die Liste der Pakete.  
  
##  <a name="set-options-on-the-select-destination-page"></a><a name="destination"></a>Festlegen von Optionen auf der Seite "Ziel auswählen"  
 Geben Sie auf dieser Seite den Namen und den Pfad für eine neue Projektbereitstellungsdatei (.ispac) an, oder wählen Sie eine vorhandene Datei aus.  
  
> [!NOTE]  
>   Die Seite **Ziel auswählen** ist nur verfügbar, wenn Sie den Assistenten über [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]ausführen.  
  
 **Ausgabepfad**  
 Geben Sie den Pfad für die Bereitstellungsdatei ein, oder navigieren Sie zur Datei, indem Sie auf **Durchsuchen**klicken.  
  
 **Projektname**  
 Geben Sie den Projektnamen ein.  
  
 **Schutzebene**  
 Wählen Sie die Schutzebene aus. Weitere Informationen finden Sie unter [Access Control for Sensitive Data in Packages](security/access-control-for-sensitive-data-in-packages.md).  
  
 **Projektbeschreibung**  
 Geben Sie eine optionale Beschreibung für das Projekt ein.  
  
##  <a name="set-options-on-the-specify-project-properties-page"></a><a name="projectProperties"></a> Festlegen von Optionen auf der Seite "Projekteigenschaften angeben"  
  
> [!NOTE]  
>   Die Seite **Projekteigenschaften angeben** ist nur verfügbar, wenn Sie den Assistenten über [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ausführen.  
  
 **Projektname**  
 Listet den Projektnamen auf.  
  
 **Schutzebene**  
 Wählen Sie eine Schutzebene für die im Projekt enthaltenen Pakete aus. Weitere Informationen zu Schutzebenen finden Sie unter [Access Control for Sensitive Data in Packages](security/access-control-for-sensitive-data-in-packages.md).  
  
 **Projektbeschreibung**  
 Geben Sie eine optionale Beschreibung für das Projekt ein.  
  
##  <a name="set-options-on-the-update-execute-package-task-page"></a><a name="executePackage"></a>Festlegen von Optionen auf der Seite "Task ' Paket ausführen ' aktualisieren"  
 Aktualisieren Sie die in den Paketen enthaltenen Tasks "Paket ausführen", um einen projektbasierten Verweis zu verwenden. Weitere Informationen finden Sie unter [Execute Package Task Editor](../../2014/integration-services/execute-package-task-editor.md).  
  
 **Übergeordnetes Paket**  
 Listet den Namen eines Pakets auf, das ein untergeordnetes Paket mithilfe des Tasks "Paket ausführen" ausführt.  
  
 **Taskname**  
 Listet den Namen des Tasks "Paket ausführen" auf.  
  
 **Ursprünglicher Verweis**  
 Listet den aktuellen Pfad des untergeordneten Pakets auf.  
  
 **Verweis zuweisen**  
 Wählen Sie ein untergeordnetes im Projekt gespeichertes Paket aus.  
  
##  <a name="set-options-on-the-select-configurations-page"></a><a name="configurations"></a> Festlegen von Optionen auf der Seite "Konfigurationen auswählen"  
 Wählen Sie die Paketkonfigurationen aus, die Sie durch Parameter ersetzen möchten.  
  
 **Paket**  
 Listet die Paketdatei auf.  
  
 **Type**  
 Listet den Typ der Konfiguration auf, z. B. eine XML-Konfigurationsdatei.  
  
 **Konfigurationszeichenfolge**  
 Listet den Pfad der Konfigurationsdatei auf.  
  
 **Status**  
 Zeigt eine Statusmeldung für die Konfiguration an. Klicken Sie auf die Meldung, um den gesamten Meldungstext anzuzeigen.  
  
 **Hinzufügen von Konfigurationen**  
 Fügen Sie in anderen Projekten enthaltene Paketkonfigurationen der Liste mit verfügbaren Konfigurationen hinzu, die Sie durch Parameter ersetzen möchten. Sie können in einem Dateisystem oder in SQL Server gespeicherte Konfigurationen auswählen.  
  
 **Aktualisieren**  
 Klicken Sie auf die Option, um die Liste der Konfigurationen zu aktualisieren.  
  
 **Option zum Entfernen der Konfigurationen von allen Paketen nach der Konvertierung**  
 Es wird empfohlen, durch Aktivierung dieser Option alle Konfigurationen vom Projekt zu entfernen.  
  
 Wenn Sie diese Option nicht auswählen, werden nur die Konfigurationen entfernt, die durch Parameter ersetzt werden sollen.  
  
##  <a name="set-options-on-the-create-parameters-page"></a><a name="createParameters"></a> Festlegen von Optionen auf der Seite "Parameter erstellen"  
 Wählen Sie den Parameternamen und den Bereich für jede Konfigurationseigenschaft aus.  
  
 **Paket**  
 Listet die Paketdatei auf.  
  
 **Parametername**  
 Listet den Namen des Parameters auf.  
  
 **Umfang**  
 Wählen Sie den Bereich des Parameters aus, und zwar entweder Paket oder Projekt.  
  
##  <a name="set-options-on-the-configure-parameters-page"></a><a name="configureParameters"></a>Festlegen von Optionen auf der Seite "Parameter konfigurieren"  
 **Name**  
 Listet den Namen des Parameters auf.  
  
 **Umfang**  
 Listet den Bereich des Parameters auf.  
  
 **Wert**  
 Listet den Parameterwert auf.  
  
 Klicken Sie auf die Auslassungspunkte, die sich neben dem Wertefeld befinden, um die Parametereigenschaften zu konfigurieren.  
  
 Im Dialogfeld **Parameterdetails festlegen** können Sie den Parameterwert bearbeiten. Sie können auch angeben, ob der Parameterwert bereitgestellt werden muss, wenn Sie das Paket ausführen.  
  
 Sie können den Wert auf der Seite **Parameter** des Dialogfelds **Konfigurieren** in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]ändern, indem Sie neben dem Parameter auf die Schaltfläche zum Durchsuchen klicken. Das Dialogfeld **Parameterwert festlegen** wird angezeigt.  
  
 Das Dialogfeld **Parameterdetails festlegen** listet auch den Datentyp des Parameterwerts und den Ursprung des Parameters auf.  
  
##  <a name="set-the-options-on-the-review-page"></a><a name="review"></a>Festlegen der Optionen auf der Seite "überprüfen"  
 Verwenden Sie die Seite für die **Überprüfung**, um die Optionen zu bestätigen, die Sie für die Konvertierung des Projekts ausgewählt haben.  
  
 **Zurück**  
 Klicken Sie, um eine Option zu ändern.  
  
 **Konvertieren**  
 Klicken Sie, um das Projekt in das Projektbereitstellungsmodell zu konvertieren.  
  
##  <a name="set-the-options-on-the-perform-conversion"></a><a name="conversion"></a>Festlegen der Optionen für die Konvertierung ausführen  
 Die Seite "Konvertierung ausführen" zeigt den Status der Projektkonvertierung an.  
  
 **Aktion**  
 Listet einen bestimmten Konvertierungsschritt auf.  
  
 **Ergebnis**  
 Listet die Status sämtlicher Konvertierungsschritte auf. Klicken Sie auf die Statusmeldung, um weitere Informationen zu erhalten.  
  
 Die Projektkonvertierung wird erst gespeichert, wenn das Projekt in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]gespeichert wird.  
  
 **Bericht speichern**  
 Klicken Sie, um in einer XML-Datei eine Zusammenfassung der Projektkonvertierung zu speichern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Deploy Projects to Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md)  
  
  
