---
title: Planen der Datenaktualisierung und Datenquellen, die die Windows-Authentifizierung nicht unterstützen (PowerPivot für SharePoint) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d8d875bc-7823-46b7-a939-867cefd4de12
author: minewiskan
ms.author: owend
ms.openlocfilehash: 63e37dec6f334395c0c1812c6f76d750c16c53ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87618319"
---
# <a name="schedule-data-refresh-and-data-sources-that-do-not-support-windows-authentication-powerpivot-for-sharepoint"></a>Planen der Datenaktualisierung mit Datenquellen, die die Windows-Authentifizierung nicht unterstützen (PowerPivot für SharePoint)
  In diesem Thema wird ein Workflow für eine planmäßige Datenaktualisierung in PowerPivot für SharePoint beschrieben. Dabei können Datenquellen verwendet werden, die die Windows-Authentifizierung **NICHT** unterstützen, z. B. Oracle- oder IDM DB2-Datenquellen. Obwohl sich die Abbildungen und Schritte in diesem Thema auf Oracle-Datenquellen beziehen, gilt der gleiche Workflow auch für andere Datenquellen.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2010 &#124; SharePoint 2013.|  
  
 **Übersicht:** Erstellen Sie zwei Secure Store-Zielanwendungen. Konfigurieren Sie die erste Zielanwendung (PowerPivotDataRefresh) für die Verwendung von Windows-Anmeldeinformationen. Konfigurieren Sie die zweite Zielanwendung mit den Anmeldeinformationen einer Datenquelle, die keine Windows-Authentifizierung unterstützt, z. B. eine Oracle-Datenbank. Darüber hinaus wird die erste Zielanwendung von der zweiten Zielanwendung für das unbeaufsichtigte Datenaktualisierungskonto verwendet.  
  
 ![as_powerpivot_refresh_no_windows_auth](../media/as-powerpivot-refresh-no-windows-auth.gif "as_powerpivot_refresh_no_windows_auth")  
  
-   **(1) PowerPivotDatarefresh:** Eine Secure Store-Zielanwendungs-ID, für die im SET-Befehl die Windows-Authentifizierung angegeben ist.  
  
-   **(2) OracleAuthentication:** Eine Secure Store-Zielanwendungs-ID, für die im SET-Befehl Oracle-Anmeldeinformationen angegeben sind.  
  
-   **(3)** die Power Pivot-Dienst Anwendung wird so konfiguriert, dass Sie die Zielanwendung "powerpivotdatarefresh" für das **unbeaufsichtigte Daten Aktualisierungs Konto**verwendet.  
  
-   **(4)** Die PowerPivot-Arbeitsmappe verwendet Oracle-Daten. In den Aktualisierungseinstellungen der Arbeitsmappe ist angegeben, dass die Anmeldeinformationen von Zielanwendung **(2)** für die Datenquellenverbindung verwendet werden.  
  
## <a name="prerequisites"></a>Voraussetzungen  
  
-   Eine PowerPivot-Dienstanwendung ist vorhanden.  
  
-   Eine Secure Store Service-Anwendung ist vorhanden.  
  
-   Eine Excel-Arbeitsmappe mit einem PowerPivot-Datenmodell ist vorhanden.  
  
## <a name="to-create-a-target-application-id-that-uses-windows-authentication"></a>So erstellen Sie eine Zielanwendungs-ID, die die Windows-Authentifizierung verwendet  
  
1.  Klicken Sie in der SharePoint-zentral Administration auf **Dienst Anwendungen verwalten**.  
  
2.  Klicken Sie auf den Namen der Secure Store Service-Anwendung.  
  
3.  Klicken Sie auf der Seite **Verwalten** auf **Neu**. ![as_powerpivot_refresh_sss_new_target_application](../media/as-powerpivot-refresh-sss-new-target-application.gif "as_powerpivot_refresh_sss_new_target_application")  
  
4.  Konfigurieren Sie auf der Seite **Neue Zielanwendung für einmaliges Anmelden erstellen** die folgenden Werte:  
  
    -   **Zielanwendungs-ID:** PowerPivotDataRefresh  
  
    -   **Anzeigename:** PowerPivotDataRefresh  
  
    -   **Kontakt-E-Mail:** ?  
  
    -   **Zielanwendungstyp:** Gruppe  
  
    -   **Seiten-URL der Zielanwendung:** Keine  
  
5.  Klicken Sie auf **Weiter**.  
  
6.  Übernehmen Sie auf der Seite „Anmeldeinformationen“ die beiden Standardfeldnamen und -typen **Windows-Benutzername** und **Windows-Kennwort**.  
  
7.  Klicken Sie auf **Weiter**.  
  
8.  Fügen Sie auf der Seite **Mitgliedschaftseinstellungen** mindestens einen **Zielanwendungs-Administrator** und anschließend Mitglieder hinzu, die Zugriff auf die Zielanwendung benötigen.  
  
9. Klicken Sie auf **OK**.  
  
10. Die neue Zielanwendungs-ID wird der Liste hinzugefügt. Wählen Sie die Zielanwendungs-ID aus, und klicken Sie auf **Anmelde**Informationen![as_powerpivot_refresh_sss_set_key](../media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key")  
  
11. Geben Sie den Windows-Benutzernamen und das Windows-Kennwort ein, und klicken Sie auf **OK**.  
  
## <a name="to-create-a-target-application-id-that-uses-oracle-credentials"></a>So erstellen Sie eine Zielanwendungs-ID, die Oracle-Anmeldeinformationen verwendet  
  
1.  Klicken Sie in der SharePoint-zentral Administration auf **Dienst Anwendungen verwalten**.  
  
2.  Klicken Sie auf den Namen der Secure Store Service-Anwendung.  
  
3.  Klicken Sie auf der Seite **Verwalten** auf **neu**![as_powerpivot_refresh_sss_new_target_application](../media/as-powerpivot-refresh-sss-new-target-application.gif "as_powerpivot_refresh_sss_new_target_application").  
  
4.  Konfigurieren Sie auf der Seite **Neue Zielanwendung für einmaliges Anmelden erstellen** die folgenden Werte:  
  
    -   **Zielanwendungs-ID:** OracleAuthentication  
  
    -   **Anzeigename:** OracleAuthentication  
  
    -   **Kontakt-E-Mail:** ?  
  
    -   **Zielanwendungstyp:** Gruppe  
  
    -   **Seiten-URL der Zielanwendung:** Keine  
  
5.  Klicken Sie auf **Weiter**.  
  
6.  Ändern Sie auf der Seite **Anmelde** Informationen den ersten Feldnamen in, `Oracle User ID` und ändern Sie den **Feldtyp** in `User Name` .  
  
     Ändern Sie den zweiten Feldnamen in `Oracle Password` und den **Feldtyp** in `Password` .  
  
7.  Klicken Sie auf **Weiter**.  
  
8.  Fügen Sie auf der Seite **Mitgliedschaftseinstellungen** mindestens einen **Zielanwendungs-Administrator** und anschließend Mitglieder hinzu, die Zugriff auf die Zielanwendung benötigen.  
  
9. Klicken Sie auf **OK**.  
  
10. Die neue Zielanwendungs-ID wird der Liste hinzugefügt. Wählen Sie die Zielanwendungs-ID aus, und klicken Sie auf **Anmelde**Informationen![as_powerpivot_refresh_sss_set_key](../media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key")  
  
11. Geben Sie die Oracle-Benutzer-ID und das Oracle-Kennwort ein, und klicken Sie auf **OK**.  
  
 Weitere Informationen finden Sie im Abschnitt "So erstellen Sie eine Zielanwendung für SQL Server Authentifizierung" in [Verwenden von Secure Store mit SQL Server Authentifizierung (SharePoint Server 2013)](https://technet.microsoft.com/library/gg298949.aspx) ( https://technet.microsoft.com/library/gg298949.aspx) .  
  
## <a name="to-configure-the-powerpivot-service-application"></a>So konfigurieren Sie die PowerPivot-Dienstanwendung  
  
1.  Klicken Sie in der SharePoint-Zentraladministration auf Dienstanwendungen verwalten.  
  
2.  Klicken Sie auf den Namen der Power Pivot-Dienst Anwendung, z. b. "Power Pivot-Standard Dienst Anwendung".  
  
3.  Klicken Sie im Abschnitt „Aktionen“ auf **Einstellungen für Dienstanwendung konfigurieren** .  
  
4.  Legen Sie im Abschnitt **Datenaktualisierung** das **unbeaufsichtigte Daten Aktualisierungs Konto für Power Pivot**auf fest, `PowerPivotDataRefresh` und klicken Sie dann auf **OK**.  
  
     ![as_powerpivot_refresh_new_refresh_acount](../media/as-powerpivot-refresh-new-refresh-acount.gif "as_powerpivot_refresh_new_refresh_acount")  
  
## <a name="to-configure-the-workbook"></a>So konfigurieren Sie die Arbeitsmappe  
  
1.  Navigieren Sie im Power Pivot-Katalog zu Ihrer Arbeitsmappe, und klicken Sie auf **Datenaktualisierung verwalten**![as_powerpivot_refresh_manage_reresh](../media/as-powerpivot-refresh-manage-reresh.gif "as_powerpivot_refresh_manage_reresh").  
  
2.  Sobald die Seite **Verlauf der Datenaktualisierung** angezeigt wird, klicken Sie auf **Zeitplan konfigurieren**.  
  
3.  Klicken Sie auf **Aktivieren**.  
  
4.  Klicken Sie auf **Außerdem so bald wie möglich aktualisieren**.  
  
5.  Klicken Sie im Abschnitt **Anmeldeinformationen** auf **Das vom Administrator konfigurierte Konto für die Datenaktualisierung verwenden**.  
  
6.  Deaktivieren Sie **Alle Datenquellen**.  
  
7.  Wählen Sie für die Datenquelle, die Oracle-Daten verwendet, die Option **Aktualisieren** aus. Der Name der Datenquelle kann in Microsoft Excel geändert werden, indem Sie auf das Menü **Daten**und dann auf **Verbindungen**und auf **Eigenschaften** klicken.  
  
8.  Wählen Sie unter Ihrer Datenquelle die Option **Standardzeitplan verwenden**aus.  
  
9. Wählen Sie **Stellen Sie mithilfe der in Secure Store Service (SSS) gespeicherten Anmeldeinformationen eine Verbindung her, um sich bei der Datenquelle anzumelden. Geben Sie die ID, mit der die Anmeldeinformationen nachgeschlagen werden, in das Feld „SSS-ID“ ein.**  
  
10. Geben Sie im Feld **ID:** Folgendes ein: `OracleAuthentication` .  
  
11. Klicken Sie auf **OK**.  
  
     Wenn eine Fehlermeldung mit etwa dem Wortlaut `The provided Secure Store target application is either incorrectly configured or does not exist`angezeigt wird,  
  
     gibt es zwei Lösungswege:  
  
    -   Überprüfen Sie, ob die Zielanwendungs-ID richtig ist.  
  
    -   Stellen Sie sicher, dass Sie Anmeldeinformationen für die Zielanwendung festgelegt haben.  
  
## <a name="to-verify-data-refresh-with-the-new-authentication"></a>So überprüfen Sie die Datenaktualisierung mit der neuen Authentifizierung  
 Wenn Sie auf **OK**klicken, wird die Seite **Verlauf aktualisieren** angezeigt. Binnen weniger Minuten sollte ein neues Element im Verlauf angezeigt werden, da Sie in den vorangehenden Schritten **Außerdem sobald wie möglich aktualisieren**ausgewählt haben. Der Standardwert für den Zeitgeberauftrag **Zeitgeberauftrag für die PowerPivot-Datenaktualisierung** beträgt 1 Minute. Wenn im Verlauf kein neues Element angezeigt wird, warten Sie einige Minuten, und aktualisieren Sie Ihren Browser. Sollte das neue Element auch dann nicht sichtbar sein, überprüfen Sie den aktuellen Wert des Zeitgeberauftrags.  
  
## <a name="more-information"></a>Weitere Informationen  
  
-   [Konfigurieren von Secure Store Service in SharePoint 2013](https://technet.microsoft.com/library/ee806866.aspx).  
  
-   Weitere Informationen finden Sie im Abschnitt "geplante Datenaktualisierung" unter [Power Pivot-Datenaktualisierung mit SharePoint 2013 und SQL Server 2012 SP1 (Analysis Services)](https://msdn.microsoft.com/library/jj879294.aspx#bkmk_windows_auth_interactive_data_refresh).  
  
  
