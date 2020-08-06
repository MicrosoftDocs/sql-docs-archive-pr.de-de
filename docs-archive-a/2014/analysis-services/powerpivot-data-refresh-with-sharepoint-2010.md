---
title: Power Pivot-Datenaktualisierung mit SharePoint 2010 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- unattended data refresh [Analysis Services with SharePoint]
- scheduled data refresh [Analysis Services with SharePoint]
- data refresh [Analysis Services with SharePoint]
ms.assetid: 01b54e6f-66e5-485c-acaa-3f9aa53119c9
author: minewiskan
ms.author: owend
ms.openlocfilehash: 01874bf521055d1441b695a238d09440021d2718
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720365"
---
# <a name="powerpivot-data-refresh-with-sharepoint-2010"></a>PowerPivot-Datenaktualisierung mit SharePoint 2010
  Die [!INCLUDE[ssGemini](../includes/ssgemini-md.md)]-Datenaktualisierung ist ein geplanter serverseitiger Vorgang, mit dem externe Datenquellen abgefragt werden, um eingebettete [!INCLUDE[ssGemini](../includes/ssgemini-md.md)]-Daten in einer Excel 2010-Arbeitsmappe zu aktualisieren, die in einer Inhaltsbibliothek gespeichert ist.

 Die Datenaktualisierung ist eine integrierte Funktion von [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] für SharePoint, allerdings erfordert deren Verwendung die Ausführung bestimmter Dienste und Zeitgeberaufträge in der SharePoint 2010-Farm. Oftmals sind für eine erfolgreiche Datenaktualisierung zusätzliche Verwaltungsschritte erforderlich, z. B. die Installation von Datenanbietern und die Überprüfung von Datenbankberechtigungen.

 **[!INCLUDE[applies](../includes/applies-md.md)]** SharePoint 2010

> [!NOTE]
>  [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] und Excel Services von SharePoint Server 2013 verwenden eine andere Architektur für die Datenaktualisierung bei [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] -Datenmodellen. In der neuen Architektur wird Excel Services als Hauptkomponente zum Laden von PowerPivot-Datenmodellen genutzt. In der vorherigen Datenaktualisierungsarchitektur wurden Datenmodelle mithilfe eines Servers geladen, auf dem der PowerPivot-Systemdienst und [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] im SharePoint-Modus ausgeführt wurden. Weitere Informationen finden Sie unter [Power Pivot-Datenaktualisierung mit SharePoint 2013](power-pivot-sharepoint/power-pivot-data-refresh-with-sharepoint-2013.md).

 **In diesem Thema:**

 [Schritt 1: Aktivieren von einmaliges Anmelden und Generieren eines Haupt Schlüssels](#bkmk_services)

 [Schritt 2: Deaktivieren der Anmeldeinformationsoptionen, die nicht unterstützt werden sollen](#bkmk_creds)

 [Schritt 3: Erstellen von Zielanwendungen zum Speichern der Anmeldeinformationen, die bei der Datenaktualisierung verwendet werden](#bkmk_stored)

 [Schritt 4: Konfigurieren des Servers für die skalierbare Datenaktualisierung](#bkmk_scale)

 [Schritt 5: Installieren von Datenanbietern zum Importieren von PowerPivot-Daten](#bkmk_installdp)

 [Schritt 6: Gewähren von Berechtigungen für die Erstellung von Zeitplänen und für den Zugriff auf externe Datenquellen](#bkmk_accounts)

 [Schritt 7: Aktivieren von Arbeitsmappenaktualisierung für Datenaktualisierung](#bkmk_upgradewrkbk)

 [Schritt 8: Überprüfen der Datenaktualisierungskonfiguration](#bkmk_verify)

 [Ändern von Konfigurationseinstellungen für Datenaktualisierung](#bkmk_config)

 [Erneutes Planen des Zeitgeberauftrags für die PowerPivot-Datenaktualisierung](#configTimerJob)

 [Deaktivieren des Zeitgeberauftrags für die Datenaktualisierung](#bkmk_disableDR)

 Wenn die Serverumgebung und die Berechtigungen konfiguriert wurden, kann die Datenaktualisierung ausgeführt werden. Um die Datenaktualisierung zu verwenden, erstellt ein SharePoint-Benutzer in einer PowerPivot-Arbeitsmappe einen Zeitplan, in dem die Häufigkeit der Datenaktualisierung angegeben wird. Die Erstellung des Zeitplans wird normalerweise vom Besitzer oder Ersteller der Arbeitsmappe übernommen, der die Datei in SharePoint veröffentlicht hat. Diese Person erstellt und verwaltet die Zeitpläne zur Datenaktualisierung für die eigenen Arbeitsmappen. Weitere Informationen finden Sie unter [Planen einer Datenaktualisierung &#40;PowerPivot für SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md).

##  <a name="step-1-enable-secure-store-service-and-generate-a-master-key"></a><a name="bkmk_services"></a>Schritt 1: Aktivieren von einmaliges Anmelden und Generieren eines Haupt Schlüssels
 Die PowerPivot-Datenaktualisierung stellt mithilfe von Secure Store Service Anmeldeinformationen bereit, die zum Ausführen von Datenaktualisierungsaufträgen und zum Verbinden mit externen Datenquellen verwendet werden, die gespeicherte Anmeldeinformationen verwenden.

 Wenn Sie PowerPivot für SharePoint mit der Installationsoption Neuer Server installiert haben, wird Secure Store Service für Sie konfiguriert. Für alle anderen Installationsszenarien müssen Sie eine Dienstanwendung erstellen und konfigurieren sowie einen Hauptverschlüsselungsschlüssel für Secure Store Service generieren.

> [!NOTE]
>  Sie müssen Farmadministrator sein, um Secure Store Service zu konfigurieren oder die Verwaltung von Secure Store Service an einen anderen Benutzer zu delegieren. Sie müssen Dienstanwendungsadministrator sein, um Einstellungen nach der Aktivierung des Diensts zu konfigurieren oder zu ändern.

1.  Klicken Sie in der Zentraladministration unter Anwendungsverwaltung auf **Dienstanwendungen verwalten**.

2.  Klicken Sie im Menüband Dienst Anwendungen unter Erstellen auf **neu**.

3.  Wählen Sie **einmaliges Anmelden**aus.

4.  Geben Sie auf der Seite **Secure Store-Anwendung erstellen** einen Namen für die Anwendung ein.

5.  Geben Sie unter **Datenbank**die SQL Server Instanz an, die die Datenbank für diese Dienst Anwendung hostet. Der Standardwert entspricht der SQL Server-Datenbank-Engine-Instanz, die die Datenbanken für die Farmkonfiguration hostet.

6.  Geben Sie unter **Datenbankname**den Namen der Datenbank der Dienst Anwendung ein. Der Standardwert ist Secure_Store_Service_DB_ \<guid> . Der Standardname entspricht dem Standardnamen der Dienstanwendung. Wenn Sie einen eindeutigen Dienstanwendungsnamen eingegeben haben, verwenden Sie eine ähnliche Benennungskonvention für den Datenbanknamen, damit Sie sie zusammen verwalten können.

7.  Der Standardwert unter **Datenbankauthentifizierung**lautet Windows-Authentifizierung. Wenn Sie die SQL-Authentifizierung auswählen, finden Sie im SharePoint-Administratorhandbuch eine Anleitung zum Verwenden des Authentifizierungstyps in der Farm.

8.  Wählen Sie unter Anwendungs Pool die Option **neuen Anwendungs Pool erstellen aus.** Geben Sie einen aussagekräftigen Namen an, der anderen Serveradministratoren hilft, den Verwendungszweck des Anwendungspools zu erkennen.

9. Wählen Sie ein Sicherheitskonto für den Anwendungspool aus. Geben Sie ein verwaltetes Konto an, das als Domänenbenutzerkonto verwendet werden soll.

10. Übernehmen Sie die restlichen Standardwerte, und klicken Sie dann auf **OK.** Die Dienstanwendung wird zusammen mit anderen verwalteten Diensten in der Dienstanwendungsliste der Farm angezeigt.

11. Klicken Sie in der Liste auf die Secure Store Service-Anwendung.

12. Klicken Sie im Menüband Dienst Anwendungen auf **Verwalten**.

13. Klicken Sie Unterschlüssel Verwaltung auf **neuen Schlüssel generieren**.

14. Geben Sie eine Passphrase ein, und bestätigen Sie sie dann. Die Passphrase wird zum Hinzufügen zusätzlicher freigegebener Secure Store Service-Anwendungen verwendet.

15. Klicken Sie auf **OK**.

 Die für Problembehandlungszwecke nützliche Überwachungsprotokollierung von Secure Store Service-Vorgängen ist erst verfügbar, nachdem sie aktiviert wurde. Weitere Informationen zum Aktivieren der Protokollierung finden Sie unter [configure einmaliges Anmelden (SharePoint 2010)](https://go.microsoft.com/fwlink/p/?LinkID=223294).

##  <a name="step-2-turn-off-credential-options-that-you-do-not-want-to-support"></a><a name="bkmk_creds"></a>Schritt 2: Deaktivieren der Anmelde Informations Optionen, die Sie nicht unterstützen möchten
 Die PowerPivot-Datenaktualisierung stellt drei Anmeldeinformationsoptionen in einem Datenaktualisierungszeitplan bereit. Wenn ein Besitzer einer Arbeitsmappe eine Datenaktualisierung plant, wählt er eine dieser Optionen aus. Anhand dieser Auswahl wird das Konto bestimmt, unter dem der Datenaktualisierungsauftrag ausgeführt wird. Als Administrator können Sie festlegen, welche Anmeldeinformationsoptionen für Zeitplanbesitzer verfügbar sind.

 Es muss mindestens eine Option verfügbar sein, damit die Datenaktualisierung funktioniert.

 ![SSAS_PowerpivotKJ_DataRefreshCreds](media/ssas-powerpivotkj-datarefreshcreds.gif "SSAS_PowerpivotKJ_DataRefreshCreds")

 Option 1: **verwenden Sie das vom Administrator konfigurierte Konto für die Datenaktualisierung**, wird immer auf der Seite Zeit Plan Definition angezeigt, funktioniert aber nur, wenn Sie das Konto für die unbeaufsichtigte Datenaktualisierung konfigurieren. Weitere Informationen zum Erstellen des Kontos finden Sie unter [Konfigurieren des Power Pivot-Kontos für die unbeaufsichtigte Datenaktualisierung &#40;PowerPivot für SharePoint&#41;](configure-unattended-data-refresh-account-powerpivot-sharepoint.md).

 Option 2: Stellen Sie eine **Verbindung mithilfe der folgenden Windows-Anmelde**Informationen her, wird immer auf der Seite angezeigt, funktioniert aber nur, wenn Sie die Option **Benutzern die Eingabe benutzerdefinierter Windows-Anmelde Informationen gestatten** auf der Konfigurationsseite der Dienst Anwendung aktivieren. Diese Option ist standardmäßig aktiviert. Sie können sie aber deaktivieren, wenn die Verwendung dieser Option mehr Nachteile als Vorteile hat (siehe unten).

 Option 3: stellen **Sie eine Verbindung mithilfe der in einmaliges Anmelden gespeicherten Anmelde**Informationen her, wird immer auf der Seite angezeigt, funktioniert aber nur, wenn ein Zeit Plan Besitzer eine gültige Zielanwendung bereitstellt. Ein Administrator muss diese Zielanwendungen vorab erstellen und dann für die Personen, die Datenaktualisierungszeitpläne erstellen, den Anwendungsnamen bereitstellen. Weitere Informationen zum Erstellen einer Zielanwendung für Daten Aktualisierungs Vorgänge finden Sie unter [Konfigurieren gespeicherter Anmelde Informationen für die Power Pivot-Datenaktualisierung &#40;PowerPivot für SharePoint&#41;](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md).

 **Konfigurieren der Anmelde Informations Option 2, "Verbinden mit den folgenden Windows-Benutzer Anmelde Informationen"**

 Eine PowerPivot-Dienstanwendung enthält eine Anmeldeinformationsoption, die Zeitplanbesitzern die Eingabe eines beliebigen Windows-Benutzernamens und -Kennworts zum Ausführen eines Datenaktualisierungsauftrags erlaubt. Dies ist die zweite Anmeldeinformationsoption auf der Seite zum Definieren des Zeitplans:

 ![SSAS_PPS_ScheduleDataRefreshCreds](media/ssas-pps-scheduledatarefreshcreds.gif "SSAS_PPS_ScheduleDataRefreshCreds")

 Diese Anmeldeinformationsoption ist standardmäßig aktiviert. Wenn diese Anmeldeinformationsoption aktiviert ist, generiert der PowerPivot-Systemdienst in Secure Store Service eine Zielanwendung zum Speichern des Benutzernamens und des Kennworts, die vom Zeitplanbesitzer eingegeben wurden. Eine generierte Zielanwendung wird mit dieser Benennungs Konvention erstellt: PowerPivotDataRefresh_ \<guid> . Für jeden Satz von Windows-Anmeldeinformationen wird eine Zielanwendung erstellt. Wenn bereits eine Zielanwendung vorhanden ist, die im Besitz des PowerPivot-Systemdiensts ist und in der die beim Definieren des Zeitplans eingegebenen Anmeldeinformationen gespeichert werden, wird diese Zielanwendung vom PowerPivot-Systemdienst verwendet und keine neue Zielanwendung erstellt.

 Der Hauptvorteil bei der Verwendung dieser Anmeldeinformationsoption ist die Benutzerfreundlichkeit und Einfachheit. Die Vorarbeit ist minimal, da die Zielanwendungen für Sie erstellt werden. Auch das Ausführen einer Datenaktualisierung unter den Anmeldeinformationen des Zeitplanbesitzers (sehr wahrscheinlich auch der Ersteller der Arbeitsmappe) vereinfacht die Berechtigungsanforderungen. Dieser Benutzer besitzt höchstwahrscheinlich bereits Berichtigungen für die Zieldatenbank. Wenn die Datenaktualisierung unter der Windows-Benutzeridentität dieser Person ausgeführt wird, funktionieren alle Datenverbindungen, von denen "aktueller Benutzer" angegeben wird, automatisch.

 Der Nachteil sind die eingeschränkten Verwaltungsfunktionen. Obwohl Zielanwendungen automatisch erstellt werden, werden sie nicht automatisch gelöscht oder aktualisiert, falls sich die Kontoinformationen ändern. Aufgrund der Richtlinien zum Ablauf von Kennwörtern können Zielanwendungen irgendwann veraltet sein. Datenaktualisierungsaufträge, die abgelaufene Anmeldeinformationen verwenden, scheitern dann. Wenn dies eintritt, müssen Zeitplanbesitzer ihre Anmeldeinformationen aktualisieren, indem sie in einem Datenaktualisierungszeitplan die aktuellen Werte für Benutzername und Kennwort bereitstellen. Zu diesem Zeitpunkt wird eine neue Zielanwendung erstellt. Wenn Benutzer im Laufe der Zeit ihren Datenaktualisierungszeitplänen Anmeldeinformationen hinzufügen und diese bearbeiten, stellen Sie im System ggf. eine große Anzahl von automatisch generierten Zielanwendungen fest.

 Derzeit kann weder festgestellt werden, welche dieser Zielanwendungen aktiv oder inaktiv sind, noch kann eine Zielanwendung zu den von ihr verwendeten Datenaktualisierungszeitplänen zurückverfolgt werden. Im Allgemeinen sollten Sie die Zielanwendungen nicht löschen, da dann vorhandene Datenaktualisierungszeitpläne ggf. nicht mehr funktionsfähig sind. Das Löschen einer Zielanwendung, die noch verwendet wird, führt zu einem Fehler bei der Datenaktualisierung mit der Meldung "die Zielanwendung wurde nicht gefunden", die auf der Seite Daten Aktualisierungs Verlauf der Arbeitsmappe angezeigt wird.

 Wenn Sie diese Anmeldeinformationsoption deaktivieren, können Sie gefahrlos alle für die PowerPivot-Datenaktualisierung generierten Zielanwendungen löschen.

 **Deaktivieren der Verwendung beliebiger Windows-Anmeldeinformationen in Zeitplänen zur Datenaktualisierung**

1.  Klicken Sie in der zentral Administration unter Anwendungs Verwaltung auf **Dienst Anwendungen verwalten**.

2.  Klicken Sie auf den Namen der PowerPivot-Dienstanwendung. Das PowerPivot-Management-Dashboard wird angezeigt.

3.  Klicken Sie unter Aktionen auf **Einstellungen für Dienst Anwendung konfigurieren** , um die Seite Einstellungen für Power Pivot-Dienst Anwendung zu öffnen.

4.  Deaktivieren Sie im Abschnitt Datenaktualisierung das Kontrollkästchen **Benutzern die Eingabe benutzerdefinierter Windows-Anmelde Informationen erlauben** .

     ![SSAS_PowerPivotDatarefreshOptions_AllowUser](media/ssas-powerpivotdatarefreshoptions-allowuser.gif "SSAS_PowerPivotDatarefreshOptions_AllowUser")

##  <a name="step-3-create-target-applications-to-store-credentials-used-in-data-refresh"></a><a name="bkmk_stored"></a>Schritt 3: Erstellen von Zielanwendungen zum Speichern der in der Datenaktualisierung verwendeten Anmelde Informationen
 Sobald Secure Store Service konfiguriert ist, können SharePoint-Administratoren Zielanwendungen erstellen, um gespeicherte Anmeldeinformationen zu Datenaktualisierungszwecken verfügbar zu machen. Hierzu zählt auch das unbeaufsichtigte Datenaktualisierungskonto für PowerPivot oder ein beliebiges anderes Konto, das zur Ausführung des Auftrags oder zum Herstellen einer Verbindung mit externen Datenquellen verwendet wird.

 Damit bestimmte Anmeldeinformationsoptionen verwendet werden können, müssen Zielanwendungen erstellt werden, so wie bereits im vorherigen Abschnitt erwähnt. Insbesondere müssen Zielanwendungen für das unbeaufsichtigte Datenaktualisierungskonto für PowerPivot sowie zusätzliche gespeicherte Anmeldeinformationen bereitgestellt werden, die voraussichtlich bei den Datenaktualisierungsvorgängen verwendet werden.

 Weitere Informationen zum Erstellen von Zielanwendungen, die gespeicherte Anmelde Informationen enthalten, finden Sie unter [Konfigurieren des Power Pivot-Kontos für die unbeaufsichtigte Datenaktualisierung &#40;PowerPivot für SharePoint&#41;](configure-unattended-data-refresh-account-powerpivot-sharepoint.md) und [Konfigurieren gespeicherter Anmelde Informationen für die Power Pivot-Datenaktualisierung &#40;PowerPivot für SharePoint&#41;](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md).

##  <a name="step-4-configure-the-server-for-scalable-data-refresh"></a><a name="bkmk_scale"></a>Schritt 4: Konfigurieren des Servers für die skalierbare Datenaktualisierung
 Standardmäßig unterstützt jede PowerPivot für SharePoint-Installation sowohl bedarfsgesteuerte Abfragen als auch geplante Datenaktualisierungen.

 Für jede Installation können Sie angeben, ob die Analysis Services-Serverinstanz sowohl die bedarfsgesteuerte Abfrage als auch die geplante Datenaktualisierung unterstützt oder ob sie für einen bestimmten Typ von Vorgang vorgesehen ist. Enthält die Farm mehrere Installationen von PowerPivot für SharePoint, können Sie einen bestimmten Server nur für Datenaktualisierungsvorgänge verwenden, wenn Sie feststellen, dass sich Aufträge verzögern oder scheitern.

 Zudem können Sie die Anzahl gleichzeitig ausführbarer Datenaktualisierungsaufträge erhöhen, sofern dies von der zugrundeliegenden Hardware unterstützt wird. Die Anzahl gleichzeitig ausführbarer Datenaktualisierungsaufträge wird standardmäßig basierend auf dem Systemspeicher berechnet. Sie können diese Anzahl aber erhöhen, wenn Sie über zusätzliche CPU-Kapazität verfügen, um die Arbeitsauslastung zu bewältigen.

 Weitere Informationen finden Sie unter [Konfigurieren der dedizierten Datenaktualisierung oder &#40;der reinen Abfrage Verarbeitung PowerPivot für SharePoint&#41;](configure-dedicated-data-refresh-query-only-processing-powerpivot-sharepoint.md).

##  <a name="step-5-install-data-providers-used-to-import-powerpivot-data"></a><a name="bkmk_installdp"></a>Schritt 5: Installieren von Datenanbietern zum Importieren von Power Pivot-Daten
 Ein Datenaktualisierungsvorgang ist im Grunde eine Wiederholung eines Importvorgangs, der die ursprünglichen Daten abgerufen hat. Dies bedeutet, dass die gleichen Datenanbieter, die zum Importieren der Daten in die PowerPivot-Clientanwendung verwendet wurden, auch auf dem PowerPivot-Server installiert sein müssen.

 Datenanbieter können nur von lokalen Administratoren auf einem Windows-Server installiert werden. Wenn Sie zusätzliche Treiber installieren, installieren Sie sie auf jedem Computer in der SharePoint-Farm, auf dem PowerPivot für SharePoint installiert ist. Wenn Sie mehrere PowerPivot-Server in der Farm haben, müssen Sie die Anbieter für alle einzeln installieren.

 Bei SharePoint-Servern handelt es sich um 64-Bit-Anwendungen. Installieren Sie die 64-Bit-Version der Datenanbieter, mit denen Sie Datenaktualisierungsvorgänge unterstützen.

##  <a name="step-6-grant-permissions-to-create-schedules-and-access-external-data-sources"></a><a name="bkmk_accounts"></a>Schritt 6: Erteilen von Berechtigungen zum Erstellen von Zeitplänen und Zugreifen auf externe Datenquellen
 Arbeitsmappenbesitzer oder -autoren benötigen die Berechtigung **Teilnehmen** , um die Datenaktualisierung für eine Arbeitsmappe zu planen. Mit dieser Berechtigungsstufe kann er die Konfigurationsseite für die Datenaktualisierung der Arbeitsmappe öffnen und bearbeiten, um die Anmelde Informationen und die Zeit Plan Informationen für die Datenaktualisierung anzugeben.

 Neben den SharePoint-Berechtigungen müssen auch die Datenbankberechtigungen für externe Datenquellen geprüft werden, um sicherzustellen, dass die bei der Datenaktualisierung verwendeten Konten über ausreichende Rechte für den Zugriff auf die Daten verfügen. Zum Ermitteln der Berechtigungsanforderungen ist eine sorgfältige Auswertung erforderlich, da die zu erteilenden Berechtigungen von der Verbindungszeichenfolge in der Arbeitsmappe und von der Benutzeridentität abhängen, unter der der Datenaktualisierungsauftrag ausgeführt wird.

 **Warum vorhandene Verbindungszeichenfolgen in einer PowerPivot-Arbeitsmappe für PowerPivot-Datenaktualisierungsvorgänge relevant sind**

 Beim Ausführen der Datenaktualisierung sendet der Server eine Verbindungsanforderung an die externe Datenquelle. Bei diesem Vorgang wird die Verbindungszeichenfolge verwendet, die beim ursprünglichen Import der Daten erstellt wurde. Die in der Verbindungszeichenfolge angegebenen Serverstandort-, Datenbankname- und Authentifizierungsparameter werden jetzt bei der Datenaktualisierung verwendet, um auf dieselben Datenquellen zuzugreifen. Die Verbindungszeichenfolge und ihr Gesamtaufbau können für Datenaktualisierungszwecke nicht geändert werden. Die Verbindungszeichenfolge wird bei der Datenaktualisierung einfach unverändert wiederverwendet. In einigen Fällen können Sie den Benutzernamen und das Kennwort in der Verbindungszeichenfolge überschreiben, wenn Sie zum Verbinden mit einer Datenquelle eine Nicht-Windows-Authentifizierung verwenden. Ausführliche Informationen hierzu finden Sie weiter unten in diesem Thema.

 Bei den meisten Arbeitsmappen wird als Standardauthentifizierungsoption für die Verbindung festgelegt, dass vertrauenswürdige Verbindungen oder die integrierte Sicherheit von Windows verwendet wird. In diesem Fall enthalten die Verbindungszeichenfolgen `SSPI=IntegratedSecurity` oder `SSPI=TrustedConnection`. Wenn diese Verbindungs Zeichenfolge während der Datenaktualisierung verwendet wird, wird das Konto, das zum Ausführen des Daten Aktualisierungs Auftrags verwendet wird, der "aktuelle Benutzer". Daher benötigt dieses Konto Leseberechtigungen für jede externe Datenquelle, auf die über eine vertrauenswürdige Verbindung zugegriffen wird.

 **Haben Sie das unbeaufsichtigte Datenaktualisierungskonto für PowerPivot aktiviert?**

 Falls ja, sollten Sie dem Konto Leseberechtigungen für die Datenquellen erteilen, auf die während der Datenaktualisierung zugegriffen wird. Der Grund dafür, warum dieses Konto Leseberechtigungen benötigt, liegt darin, dass in einer Arbeitsmappe, die die Standard Authentifizierungs Optionen verwendet, das unbeaufsichtigte Konto während der Datenaktualisierung der "aktuelle Benutzer" ist. Sofern der Zeitplanbesitzer die Anmeldeinformationen in der Verbindungszeichenfolge nicht überschreibt, benötigt dieses Konto Leseberechtigungen für alle Datenquellen, die aktiv in der Organisation verwendet werden.

 **Verwenden Sie die Anmeldeinformationsoption 2, die dem Zeitplanbesitzer die Eingabe eines Windows-Benutzernamens und Kennworts erlaubt?**

 Normalerweise besitzen Benutzer, die PowerPivot-Arbeitsmappen erstellen, ausreichende Berechtigungen, da sie bereits Daten importiert haben. Wenn diese Benutzer anschließend konfigurieren, dass die Datenaktualisierung unter ihrer eigenen Windows-Benutzeridentität ausgeführt wird, wird ihr Windows-Benutzerkonto, das bereits über Rechte für die Datenbank verfügt, zum Abrufen von Daten bei der Datenaktualisierung verwendet. Die vorhandenen Berechtigungen sollten ausreichend sein.

 **Verwenden Sie die Anmeldeinformationsoption 3, bei der mit einer Secure Store Service-Zielanwendung eine Benutzeridentität zum Ausführen von Datenaktualisierungsaufträgen bereitstellt wird?**

 Jedes Konto, das zum Ausführen eines Datenaktualisierungsauftrags verwendet wird, benötigt Leseberechtigungen, und zwar aus denselben Gründen, die oben für das unbeaufsichtigte Datenaktualisierungskonto für PowerPivot erläutert sind.

 **Vorgehensweise zum Prüfen der Verbindungszeichenfolgen, um festzustellen, ob die Anmeldeinformationen bei der Datenaktualisierung überschrieben werden können**

 Wie zuvor angemerkt, können Sie auf der Ebene des Datenaktualisierungsauftrags Benutzername und Kennwort durch andere Werte ersetzen, wenn für die Verbindung keine Windows-Authentifizierung verwendet wird (z. B. die SQL Server-Authentifizierung). Nicht-Windows-Anmeldeinformationen werden mit den Benutzer-ID- und Kennwortparametern an die Verbindungszeichenfolge übergeben. Wenn die Arbeitsmappe eine Verbindungszeichenfolge mit diesen Parametern enthält, können Sie optional für die Datenaktualisierung aus dieser Datenquelle einen anderen Benutzernamen und ein anderes Kennwort angeben.

 Anhand der folgenden Schritten können Sie feststellen, ob Sie eine Verbindungszeichenfolge besitzen, die Überschreibungen von Benutzername und Kennwort akzeptiert.

1.  Öffnen Sie die Arbeitsmappe in Excel.

2.  Öffnen Sie das PowerPivot-Fenster (klicken Sie in Excel auf dem PowerPivot-Menüband auf PowerPivot-Fenster).

3.  Klicken Sie auf **Entwurf**.

4.  Klicken Sie auf **vorhandene Verbindungen**.

     Alle in der Arbeitsmappe verwendeten Verbindungen werden unter **Power Pivot-Datenverbindungen**aufgelistet.

5.  Wählen Sie die Verbindung aus, klicken Sie auf **Bearbeiten**, und klicken Sie dann auf **erweitert**. Die Verbindungszeichenfolge befindet sich unten auf der Seite.

 Wenn in der Verbindungs Zeichenfolge **Integrated Security = SSPI** angezeigt wird, können Sie die Anmelde Informationen in der Verbindungs Zeichenfolge nicht überschreiben. Für die Verbindung wird immer der aktuelle Benutzer verwendet. Wenn Sie Anmeldeinformationen bereitstellen, werden diese ignoriert.

 Wenn persistente **Sicherheitsinformationen = false, password = \* \* \* \* \* \* \* \* \* \* \* , UserID = \<userlogin> **angezeigt wird, verfügen Sie über eine Verbindungs Zeichenfolge, die die außer Kraft setzungen von Anmelde Informationen akzeptiert. Die in einer Verbindungszeichenfolge angezeigten Anmeldeinformationen (beispielsweise "UserID" und "Password") sind keine Windows-Anmeldeinformationen, sondern Datenbankanmeldungen oder andere Anmeldekonten, die für die Zieldatenquelle gültig sind.

 **Vorgehensweise zum Überschreiben der Anmeldeinformationen in der Verbindungszeichenfolge**

 Die Anmeldeinformationen werden überschrieben, indem im Datenaktualisierungszeitplan Anmeldeinformationen für die Datenquelle angegeben werden. Als Administrator können Sie eine Zielanwendung in Secure Store Service bereitstellen, mit der die Anmeldeinformationen für den Zugriff auf externe Daten zugeordnet werden. Der Zeitplanbesitzer kann anschließend die Zielanwendungs-ID in dem Datenaktualisierungszeitplan eingeben, der von ihm definiert wird. Weitere Informationen zum Erstellen dieser Zielanwendung finden Sie unter [Konfigurieren gespeicherter Anmelde Informationen für die Power Pivot-Datenaktualisierung &#40;PowerPivot für SharePoint&#41;](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md).

 Alternativ kann der Zeitplanbesitzer den Satz von Anmeldeinformationen eingeben, die bei der Datenaktualisierung zum Verbinden mit den Datenquellen verwendet werden. Die folgende Abbildung zeigt diese Datenquellenoption auf der Seite für die Zeitplandefinition.

 ![SSAS_PowerPivotKJ_DataRefreshDSOptions](media/ssas-powerpivotkj-datarefreshdsoptions.gif "SSAS_PowerPivotKJ_DataRefreshDSOptions")

 **Ermitteln der Datenzugriffsanforderungen**

 Wie bereits in den vorherigen Abschnitten erwähnt, wird zum Ausführen der Datenaktualisierung und zum Verbinden mit externen Datenquellen häufig dasselbe Konto verwendet. Daher wird das Konto, das für den Zugriff auf die externen Datenquellen verwendet wird, anhand der Optionen ermittelt, die in diesem Bereich der Seite für den Datenaktualisierungszeitplan festgelegt sind. Hierbei kann es sich um ein unbeaufsichtigtes Datenaktualisierungskonto für PowerPivot, das Windows-Konto eines einzelnen Benutzers oder um das in der vordefinierten Zielanwendung gespeicherte Konto handeln.

 ![SSAS_PowerpivotKJ_DataRefreshCreds](media/ssas-powerpivotkj-datarefreshcreds.gif "SSAS_PowerpivotKJ_DataRefreshCreds")

 Wenn zum Ausführen der Datenaktualisierung ein anderes Konto als für den Datenimport verwendet wird (z. B. das unbeaufsichtigte Datenaktualisierungskonto für PowerPivot über die Anmeldeinformationsoption 1 oder ein anderer Satz von gespeicherten Anmeldeinformationen über die Anmeldeinformationsoption 3), müssen Sie für dieses Konto eine neue Datenbankanmeldung erstellen und dieser Anmeldung Leseberechtigungen für die externen Datenquellen erteilen.

 Sobald Sie herausgefunden haben, welche Konten einen Datenzugriff benötigen, können Sie Berechtigungen für die Datenquellen prüfen, die in PowerPivot-Arbeitsmappen am häufigsten verwendet werden. Beginnen Sie mit beliebigen Data Warehouses oder Berichtsdatenbanken, die aktiv verwendet werden. Fragen Sie aber auch Benutzer, die sehr häufig mit PowerPivot arbeiten, welche Datenquellen sie verwenden. Sobald Sie eine Liste der Datenquellen erstellt haben, können Sie jede Datenquelle prüfen, um sicherzustellen, dass die Berechtigungen korrekt festgelegt sind.

##  <a name="step-7-enable-workbook-upgrade-for-data-refresh"></a><a name="bkmk_upgradewrkbk"></a>Schritt 7: Aktivieren der arbeitsmappenaktualisierung für die Datenaktualisierung
 Standardmäßig können Arbeitsmappen, die mit der [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]-Version von PowerPivot für Excel erstellt wurden, nicht für geplante Datenaktualisierungen auf einer [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]-Version von PowerPivot für SharePoint konfiguriert werden. Wenn Sie neuere und ältere Versionen der PowerPivot-Arbeitsmappen in der SharePoint-Umgebung hosten, müssen Sie zuerst alle [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]-Arbeitsmappen aktualisieren, bevor eine automatische Datenaktualisierung auf dem Server geplant werden kann.

##  <a name="step-8-verify-data-refresh-configuration"></a><a name="bkmk_verify"></a>Schritt 8: Überprüfen der Daten Aktualisierungs Konfiguration
 Zum Überprüfen der Datenaktualisierung ist eine PowerPivot-Arbeitsmappe erforderlich, die auf einer SharePoint-Website veröffentlicht ist. Sie benötigen Teilnahmeberechtigungen für die Arbeitsmappe und Berechtigungen für den Zugriff auf die Datenquellen, die im Datenaktualisierungszeitplan enthalten sind.

 Wenn Sie den Zeitplan erstellen, aktivieren Sie das Kontrollkästchen **auch so bald wie möglich aktualisieren** , um die Datenaktualisierung sofort auszuführen. Auf der Seite mit dem Datenaktualisierungsverlauf der Arbeitsmappe können Sie dann überprüfen, ob die Datenaktualisierung erfolgreich ausgeführt wurde. Der Zeitgeberauftrag zur PowerPivot-Datenaktualisierung wird einmal pro Minute ausgeführt. Es dauert daher mindestens eine Minute, um eine Bestätigung über den Erfolg der Datenaktualisierung zu erhalten.

 Probieren Sie unbedingt alle Anmeldeinformationsoptionen aus, die unterstützt werden sollen. Wenn Sie beispielsweise das unbeaufsichtigte Datenaktualisierungskonto für PowerPivot konfiguriert haben, stellen Sie sicher, dass die Datenaktualisierung bei Verwendung dieser Option erfolgreich ist. Weitere Informationen zum Planen und Anzeigen von Statusinformationen finden Sie unter [Planen einer Datenaktualisierung &#40;PowerPivot für SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md) und [Anzeigen des Daten Aktualisierungs Verlaufs &#40;PowerPivot für SharePoint&#41;](power-pivot-sharepoint/view-data-refresh-history-power-pivot-for-sharepoint.md).

 Wenn die Datenaktualisierung fehlschlägt, finden Sie im TechNet-wiki auf der Seite zur Problembehandlung bei der [Power Pivot-Datenaktualisierung](https://go.microsoft.com/fwlink/?LinkID=223279) mögliche Lösungen.

##  <a name="modify-configuration-settings-for-data-refresh"></a><a name="bkmk_config"></a>Ändern der Konfigurationseinstellungen für die Datenaktualisierung
 Jede PowerPivot-Dienstanwendung besitzt Konfigurationseinstellungen, die sich auf Datenaktualisierungsvorgänge auswirken. In diesem Abschnitt wird das Ändern dieser Einstellungen erläutert.

###  <a name="set-business-hours-to-determine-off-hours-processing"></a><a name="procIntervals"></a>Festlegen der Geschäftszeiten, um die Verarbeitung außerhalb der Geschäftszeiten zu bestimmen
 SharePoint-Benutzer, die Datenaktualisierungsvorgänge planen, können als früheste Startzeit "Nach den Geschäftsstunden" angeben. Dies kann hilfreich sein, wenn sie Daten zu geschäftlichen Transaktionen abrufen möchten, die sich während des Geschäftstags angesammelt haben. Als Farmadministrator können Sie den Zeitraum angeben, der einem Geschäftstag in Ihrer Organisation am besten entspricht. Wenn Sie einen Geschäftstag von 04:00 bis 20:00 Uhr definieren, beginnt die Verarbeitung der Datenaktualisierung, die auf der Startzeit "Nach den Geschäftsstunden" basiert, um 20:01 Uhr.

 Datenaktualisierungsanforderungen, die außerhalb der Geschäftszeiten ausgeführt werden, werden der Warteschlange in der Reihenfolge ihres Eingangs hinzugefügt. Einzelne Anforderungen werden verarbeitet, sobald Serverressourcen verfügbar sind.

1.  Klicken Sie in der zentral Administration unter Anwendungs Verwaltung auf **Dienst Anwendungen verwalten**.

2.  Klicken Sie auf den Namen der PowerPivot-Dienstanwendung. Das PowerPivot-Management-Dashboard wird angezeigt.

3.  Klicken Sie unter Aktionen auf **Einstellungen für Dienst Anwendung konfigurieren** , um die Seite Einstellungen für Power Pivot-Dienst Anwendung zu öffnen.

4.  Geben Sie im Abschnitt Datenaktualisierung unter Geschäftsstunden eine Startzeit und Beendigungszeit ein, durch die der Zeitraum für die Verarbeitung außerhalb der Geschäftszeiten definiert wird.

     Wenn Sie keinen Zeitraum für die Verarbeitung außerhalb der Geschäftszeiten definieren möchten, können Sie sowohl für Startzeit als auch für Beendigungszeit den gleichen Wert eingeben (beispielsweise 12:00 für beide Zeitangaben). Beachten Sie jedoch, dass die Seiten zur Zeitplandefinition auf den SharePoint-Websites weiterhin die Option "Nach den Geschäftsstunden" enthalten. Benutzer, die diese Option für eine Farm aktivieren, für die kein Verarbeitungszeitraum außerhalb der Geschäftszeiten definiert wurde, erhalten einen Datenaktualisierungsfehler, weil die Verarbeitungsaufträge nicht gestartet werden können.

5.  Klicken Sie auf **OK**.

###  <a name="limit-how-long-data-refresh-history-is-retained"></a><a name="usagehist"></a>Beschränken des beibehaltenen Daten Aktualisierungs Verlaufs
 Beim Datenaktualisierungsverlauf handelt es sich um einen detaillierten Datensatz der Erfolgs- und Fehlermeldungen, die für Datenaktualisierungsvorgänge im Verlauf der Zeit generiert werden. Verlaufsinformationen werden durch das System für die Sammlung von Verwendungsdaten in der Farm erfasst und verwaltet. Daher gelten Grenzwerte, die Sie für den Verwendungsdatenverlauf festlegen, ebenfalls für den Datenaktualisierungsverlauf. Da in die Berichte zu Verwendungsaktivitäten Daten aus dem gesamten PowerPivot-System einfließen, wird die Datenbeibehaltung sowohl für den Datenaktualisierungsverlauf als auch für alle anderen gesammelten und gespeicherten Verwendungsdaten mit einer einzigen Verlaufseinstellung gesteuert.

1.  Klicken Sie in der zentral Administration unter Anwendungs Verwaltung auf **Dienst Anwendungen verwalten**.

2.  Klicken Sie auf den Namen der PowerPivot-Dienstanwendung. Das PowerPivot-Management-Dashboard wird angezeigt.

3.  Klicken Sie unter Aktionen auf **Einstellungen für Dienst Anwendung konfigurieren** , um die Seite Einstellungen für Power Pivot-Dienst Anwendung zu öffnen.

4.  Geben Sie im Abschnitt Sammlung von Verwendungsdaten unter Verwendungsdatenverlauf einen Wert ein, der angibt, wie viele Tage ein Datensatz der Datenaktualisierungsaktivitäten für die einzelnen Arbeitsmappen gespeichert werden soll.

     Die Standardeinstellung beträgt 365 Tage. Der Minimalwert ist 1 Tag und der Maximalwert 5000 Tage. 0 gibt eine unbegrenzte Beibehaltungsdauer an; die Daten werden nie gelöscht. Beachten Sie, dass es keine Einstellung zum Deaktivieren des Verlaufs gibt.

5.  Klicken Sie auf **OK**.

 SharePoint-Benutzer können Verlaufsinformationen anzeigen, wenn sie für eine Arbeitsmappe, die über einen Datenaktualisierungsverlauf verfügt, die Option Datenaktualisierung verwalten auswählen. Diese Informationen werden auch von Farmadministratoren auf der Dashboardseite für die PowerPivot-Verwaltung verwendet, um PowerPivot-Dienstvorgänge zu verwalten. Weitere Informationen finden Sie unter [Anzeigen des Daten Aktualisierungs Verlaufs &#40;PowerPivot für SharePoint&#41;](power-pivot-sharepoint/view-data-refresh-history-power-pivot-for-sharepoint.md).

 Die physische Langzeitspeicherung der Verlaufsdaten erfolgt in der Datenbank der PowerPivot-Dienstanwendung. Weitere Informationen dazu, wie Verwendungs Daten gesammelt und gespeichert werden, finden Sie unter [Sammlung von Power Pivot-Verwendungs Daten](power-pivot-sharepoint/power-pivot-usage-data-collection.md).

##  <a name="reschedule-the-powerpivot-data-refresh-timer-job"></a><a name="configTimerJob"></a>Erneutes Planen des Zeit Geber Auftrags für die Power Pivot-Datenaktualisierung
 Geplante Datenaktualisierungen werden von einem Zeitgeberauftrag für die PowerPivot-Datenaktualisierung ausgelöst, der die Zeitplaninformationen in der Datenbank der PowerPivot-Dienstanwendung in einminütigen Intervallen durchsucht. Wenn eine Datenaktualisierung starten soll, fügt der Zeitgeberauftrag die Anforderung in eine Verarbeitungswarteschlange auf einem verfügbaren PowerPivot-Server ein.

 Sie können die Zeit zwischen Suchläufen zum Zweck der Leistungsoptimierung erhöhen. Sie können den Zeitgeberauftrag auch deaktivieren, um Datenaktualisierungsvorgänge während der Problembehandlung vorübergehend zu stoppen.

 Die Standardeinstellung und der niedrigste Wert, den Sie angeben können, ist eine Minute. Dieser Wert wird empfohlen. Für Zeitpläne, die zu beliebigen Tageszeiten ausgeführt werden, gewährleistet der Wert die am besten vorhersagbaren Ergebnisse. Wenn ein Benutzer z. B. eine Datenaktualisierung für 16:15 Uhr plant und der Zeitgeberauftrag einmal pro Minute nach Zeitplaninformationen sucht, wird die geplante Datenaktualisierungsanforderung um 16:15 Uhr erkannt und die Verarbeitung einige Minuten nach 16:15 Uhr ausgeführt.

 Falls Sie das Suchintervall erhöhen, sodass die Suche sehr selten (z. B. einmal täglich um Mitternacht) ausgeführt wird, werden sämtliche Datenaktualisierungsvorgänge, die laut Planung während des Intervalls ausgeführt werden sollten, umgehend der Verarbeitungswarteschlange hinzugefügt, was möglicherweise zu einer Überlastung des Servers und einer mangelnden Verfügbarkeit von Systemressourcen für andere Anwendungen führt. Abhängig von der Anzahl der geplanten Aktualisierungen kann die Verarbeitungswarteschlange für Datenaktualisierungsvorgänge derart anwachsen, dass nicht alle Aufträge abgeschlossen werden können. Datenaktualisierungsanforderungen am Ende der Warteschlange werden möglicherweise gelöscht, wenn sie mit dem nächsten Verarbeitungsintervall zusammentreffen.

 Wenn die Hardware entsprechende Unterstützung bietet, kann das Problem gemindert werden, indem zusätzliche Prozessoren für eine parallele Ausführung einer größeren Anzahl von Datenaktualisierungsvorgängen angegeben werden. Weitere Informationen finden Sie unter [Konfigurieren der dedizierten Datenaktualisierung oder &#40;der reinen Abfrage Verarbeitung PowerPivot für SharePoint&#41;](configure-dedicated-data-refresh-query-only-processing-powerpivot-sharepoint.md). Weitere Informationen darüber, wie Daten Aktualisierungs Anforderungen ermittelt, einer Warteschlange hinzugefügt und verarbeitet werden, finden Sie unter [Power Pivot-Datenaktualisierung](power-pivot-sharepoint/power-pivot-data-refresh.md).

1.  Klicken Sie in der Zentraladministration auf **Überwachung**.

2.  Klicken Sie auf **Auftrags Definitionen überprüfen**.

3.  Wählen Sie den Zeit Geber Auftrag für die **Power Pivot-Datenaktualisierung**.

4.  Ändern Sie die Häufigkeit der Zeitplanausführung, indem Sie das Intervall ändern, in dem der Zeitgeberauftrag die Zeitpläne zur Datenaktualisierung durchsucht.

##  <a name="disable-the-data-refresh-timer-job"></a><a name="bkmk_disableDR"></a>Deaktivieren des Zeit Geber Auftrags für die Datenaktualisierung
 Der Zeitgeberauftrag für die PowerPivot-Datenaktualisierung ist ein Zeitgeberauftrag auf Farmebene, der für alle PowerPivot-Serverinstanzen in der Farm entweder aktiviert oder deaktiviert wird. Er ist nicht an eine bestimmte Webanwendung oder PowerPivot-Dienstanwendung gebunden. Der Auftrag kann nicht auf einigen Servern deaktiviert werden, um die Umlagerung der Datenaktualisierungsverarbeitung auf andere Server in der Farm zu erzwingen.

 Wenn Sie den Zeitgeberauftrag für die PowerPivot-Datenaktualisierung deaktivieren, werden Anforderungen, die bereits in der Warteschlange enthalten waren, verarbeitet. Neue Anforderungen werden jedoch erst wieder hinzugefügt, nachdem Sie den Auftrag erneut aktivieren. Anforderungen, deren Ausführung in der Vergangenheit geplant war, werden nicht verarbeitet.

 Die Deaktivierung des Zeitgeberauftrags hat keine Auswirkungen auf die Funktionsverfügbarkeit in Anwendungsseiten. Es gibt keine Möglichkeit, die Datenaktualisierungsfunktion in Webanwendungen zu entfernen oder auszublenden. Benutzer, die mindestens über Teilnahmeberechtigungen verfügen, sind weiterhin in der Lage, neue Zeitpläne für Datenaktualisierungsvorgänge zu erstellen, und zwar selbst dann, wenn der Zeitgeberauftrag dauerhaft deaktiviert ist.

## <a name="see-also"></a>Weitere Informationen
 [Planen einer Datenaktualisierung &#40;PowerPivot für SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md) [Konfigurieren der dedizierten Datenaktualisierung oder der reinen Abfrage Verarbeitung &#40;PowerPivot für SharePoint&#41;&#40;](configure-dedicated-data-refresh-query-only-processing-powerpivot-sharepoint.md) [das unbeaufsichtigte Power Pivot-Daten Aktualisierungs Konto konfigurieren](configure-unattended-data-refresh-account-powerpivot-sharepoint.md) PowerPivot für SharePoint&#41;&#40;[gespeicherte Anmelde Informationen für die Power Pivot-Datenaktualisierung](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md) PowerPivot für SharePoint&#41;konfigurieren


