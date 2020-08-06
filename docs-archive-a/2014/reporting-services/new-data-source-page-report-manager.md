---
title: Seite "neue Datenquelle" (Berichts-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 35563d4c-a3d5-4f95-bf46-605da9dfcbb8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8117174f23ae85cd51c30e5ad0026ab2a01be27e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87620242"
---
# <a name="new-data-source-page-report-manager"></a>Neue Datenquelle (Seite) (Berichts-Manager)
  Mithilfe der Seite Neue Datenquelle können Sie ein freigegebenes Datenquellenelement erstellen. Eine freigegebene Datenquelle definiert eine Verbindung mit einer externen Datenquelle. Mithilfe einer freigegebenen Datenquelle können Sie die Einstellungen für die Verbindung mit der Datenquelle getrennt von den Berichten, Modellen und datengesteuerten Abonnements festlegen und verwalten, die diese Datenquelle verwenden.  
  
## <a name="navigation"></a>Navigation  
 Verwenden Sie folgendes Verfahren, um zu dieser Position in der Benutzeroberfläche zu navigieren.  
  
###### <a name="to-open-the-new-data-source-page"></a>So öffnen Sie die Seite Neue Datenquelle  
  
1.  Öffnen Sie den Berichts-Manager, und navigieren Sie zu dem Ordner, in dem Sie eine Datenquelle erstellen möchten.  
  
2.  Klicken Sie auf der Symbolleiste auf **Neue Datenquelle**. Sie müssen über Inhalts-Manager-Berechtigungen verfügen, um eine freigegebene Datenquelle zu erstellen.  
  
## <a name="options"></a>Tastatur  
 **Name**  
 Geben Sie einen Namen für die freigegebene Datenquelle ein, der zum Identifizieren des Elements innerhalb der Ordnerhierarchie des Berichtsservers verwendet wird.  
  
 **Beschreibung**  
 Stellen Sie Informationen zur freigegebenen Datenquelle bereit. Diese Beschreibung wird auf der Seite Inhalt angezeigt.  
  
 **In Listenansicht ausblenden**  
 Wählen Sie diese Option aus, um die freigegebene Datenquelle für Benutzer auszublenden, die den Listenansichtsmodus im Berichts-Manager verwenden. Der Listenansichtsmodus ist das Standardanzeigeformat beim Durchsuchen der Ordnerhierarchie auf dem Berichtsserver. In der Listenansicht erstrecken sich Namen und Beschreibungen über die Seite. Das alternative Format ist die Detailsansicht. Detailansichten lassen Beschreibungen aus, enthalten jedoch andere Informationen zum Element. Obwohl Sie ein Element in der Listenansicht ausblenden können, kann es in der Detailansicht nicht ausgeblendet werden. Wenn Sie den Zugriff auf ein Element einschränken möchten, müssen Sie eine Rollenzuweisung erstellen.  
  
 **Diese Datenquelle aktivieren**  
 Mit dieser Option können Sie die freigegebene Datenquelle aktivieren oder deaktivieren. Sie können die freigegebene Datenquelle deaktivieren, um die Berichtsverarbeitung für alle Berichte und Modelle zu verhindern, die auf dieses Element verweisen.  
  
 **Datenquellentyp**  
 Geben Sie die Datenverarbeitungserweiterung an, die zum Verarbeiten von Daten aus der Datenquelle verwendet wird. Der Berichts Server enthält Datenverarbeitungs Erweiterungen für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , Oracle, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , SAP, XML, ODBC und OLE DB. Weitere Datenverarbeitungserweiterungen können von Drittanbietern zur Verfügung stehen.  
  
 Weitere Informationen zur Unterstützung von Remote Datenquellen und nicht-SQL-Datenquellen finden Sie unter [von den Editionen von SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) (Hyperlink "") unterstützte Funktionen <https://go.microsoft.com/fwlink/?linkid=232473> <https://go.microsoft.com/fwlink/?linkid=232473> und [Datenquellen, die von Reporting Services &#40;SSRS&#41;unterstützt ](create-deploy-and-manage-mobile-and-paginated-reports.md)werden.  
  
 **Verbindungszeichenfolge**  
 Geben Sie die Verbindungszeichenfolge an, die vom Berichtsserver zum Herstellen der Verbindung mit der Datenquelle verwendet wird. Der Verbindungstyp bestimmt die Syntax, die Sie verwenden sollten. So ist z.B. eine Verbindungszeichenfolge für die XML-Datenverarbeitungserweiterung eine URL zu einem XML-Dokument. In den meisten Fällen gibt eine typische Verbindungszeichenfolge den Datenbankserver und die Datendatei an.  
  
 Das folgende Beispiel veranschaulicht eine Verbindungs Zeichenfolge zum Herstellen einer Verbindung mit der- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBnormal](../includes/sssampledbnormal-md.md)] Datenbank:  
  
```  
data source=<a SQL Server instance>;initial catalog=AdventureWorks2012  
```  
  
 Weitere Beispiele und Informationen zu verschiedenen Methoden zum Angeben einer Verbindungs Zeichenfolge finden Sie unter [Datenverbindungen, Datenquellen und Verbindungs](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)Zeichenfolgen in Reporting Services.  
  
 **Verbindung herstellen über**  
 Geben Sie Optionen an, die bestimmen, wie Anmeldeinformationen abgerufen werden.  
  
> [!IMPORTANT]  
>  Falls die Verbindungszeichenfolge Anmeldeinformationen enthält, werden die in diesem Abschnitt festgelegten Optionen und Werte ignoriert. Beachten Sie, dass bei Angabe der Anmeldeinformationen in der Verbindungszeichenfolge die Werte für alle Benutzer, die diese Seite anzeigen, in Klartext angezeigt werden.  
  
 **Bereitgestellte Anmeldeinformationen vom Benutzer, der den Bericht ausführt (Verbindung herstellen über)**  
 Jeder Benutzer wird aufgefordert, einen Benutzernamen und ein Kennwort für den Zugriff auf die Datenquelle einzugeben. Sie können den Text der Eingabeaufforderung definieren, in der die Benutzeranmeldeinformationen angefordert werden. Die Standardtextzeichenfolge lautet: "Geben Sie einen Benutzernamen und ein Kennwort für den Zugriff auf die Datenquelle ein".  
  
 Aktivieren Sie das Kontrollkästchen **Als Windows-Anmeldeinformationen verwenden, wenn eine Verbindung mit der Datenquelle hergestellt wird** , wenn es sich bei den durch den Benutzer bereitgestellten Informationen um Anmeldeinformationen der Windows-Authentifizierung handelt. Aktivieren Sie dieses Kontrollkästchen nicht, wenn Sie Datenbankauthentifizierung (z. B. eine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Authentifizierung) verwenden.  
  
 **Anmeldeinformationen, die sicher auf dem Berichtsserver gespeichert sind (Verbindung herstellen über)**  
 Speichern Sie einen verschlüsselten Benutzernamen und ein Kennwort in der Berichtsserver-Datenbank. Wählen Sie diese Option aus, um einen Bericht unbeaufsichtigt auszuführen (z. B. Berichte, die durch Zeitpläne initiiert werden oder durch Ereignisse anstelle einer Benutzeraktion). Wenn Sie die Standardsicherheitseinstellungen verwenden, muss der Benutzername ein Windows-Domänenkonto sein. Geben Sie das Konto im folgenden Format an: \<domain> \\<username \> . Das von Ihnen angegebene Konto muss über lokale Systemadministratorberechtigungen auf dem Computer verfügen, der die von dem Bericht verwendete Datenquelle hostet.  
  
 Aktivieren Sie das Kontrollkästchen **Als Windows-Anmeldeinformationen verwenden, wenn eine Verbindung mit der Datenquelle hergestellt wird** , wenn es sich bei den Informationen um Anmeldeinformationen der Windows-Authentifizierung handelt. Aktivieren Sie dieses Kontrollkästchen nicht, wenn Sie Datenbankauthentifizierung (z. B. eine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Authentifizierung) verwenden.  
  
 Wenn Sie die Datenbankauthentifizierung verwenden, wählen Sie die Option **Die Identität des authentifizierten Benutzers annehmen, nachdem eine Verbindung zur Datenquelle hergestellt wurde** aus, um die Delegierung von Datenbank-Anmeldeinformationen zuzulassen. Dies ist jedoch nur möglich, wenn ein Datenbankserver den Identitätswechsel unterstützt. Bei [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Datenbanken kann mit dieser Option die SETUSER-Funktion festgelegt werden.  
  
 **Integrierte Sicherheit von Windows (Verbindung herstellen über)**  
 Verwenden Sie die Windows-Anmeldeinformationen des aktuellen Benutzers für den Zugriff auf die Datenquelle. Wählen Sie diese Option aus, wenn die für den Zugriff auf die Datenquelle verwendeten Anmeldeinformationen mit denen übereinstimmen, die zum Anmelden an der Netzwerkdomäne verwendet werden. Diese Option kann am besten verwendet werden, wenn die Kerberos-Authentifizierung für die Domäne aktiviert ist oder wenn sich die Datenquelle auf demselben Computer wie der Berichtsserver befindet. Wenn die Kerberos-Authentifizierung nicht aktiviert ist, können die Windows-Anmeldeinformationen an einen anderen Computer weitergegeben werden. Falls weitere Computerverbindungen erforderlich sind, wird eine Fehlermeldung statt der erwarteten Daten zurückgegeben.  
  
 Ein Berichtsserveradministrator kann die Verwendung der integrierten Sicherheit von Windows deaktivieren, um auf Berichtsdatenquellen zugreifen zu können. Wenn dieser Wert ausgegraut ist, ist die Funktion nicht verfügbar.  
  
 Verwenden Sie diese Option nicht, wenn Sie vorhaben, diesen Bericht zu planen oder zu abonnieren. Die geplante oder unbeaufsichtigte Berichtsverarbeitung benötigt Anmeldeinformationen, die ohne Benutzereingaben oder den Sicherheitskontext des aktuellen Benutzers abgerufen werden können. Diese Möglichkeit bieten nur gespeicherte Anmeldeinformationen. Aus diesem Grund hindert Sie der Berichtsserver daran, die Ausführung eines Berichts oder eines Abonnements zu planen, wenn der Bericht für den Anmeldeinformationstyp der integrierten Windows-Sicherheit konfiguriert ist. Wenn Sie diese Option für einen Bericht wählen, der bereits abonniert ist oder geplante Vorgänge aufweist, werden das Abonnement und die geplanten Vorgänge beendet.  
  
 **Anmeldeinformationen sind nicht erforderlich (Verbindung herstellen über)**  
 Geben Sie an, dass keine Anmeldeinformationen für den Zugriff auf die Datenquelle erforderlich sind. Beachten Sie, dass diese Option keine Auswirkungen hat, wenn für die Datenquelle eine Benutzeranmeldung erforderlich ist. Sie sollten diese Option nur auswählen, wenn für die Datenquellenverbindung keine Benutzeranmeldeinformationen erforderlich sind.  
  
 Um diese Option verwenden zu können, müssen Sie vorher das unbeaufsichtigte Ausführungskonto für die Bereitstellung des Berichtsservers konfiguriert haben. Das unbeaufsichtigte Ausführungskonto wird zum Herstellen der Verbindung mit externen Datenquellen verwendet, wenn keine anderen Quellen für Anmeldeinformationen verfügbar sind. Wenn Sie diese Option angeben und das Konto nicht konfiguriert ist, schlägt die Verbindung mit der Berichtsdatenquelle fehl, und der Bericht wird nicht verarbeitet. Weitere Informationen zu diesem Konto finden Sie unter [Konfigurieren des Kontos für die unbeaufsichtigte Ausführung &#40;SSRS-Configuration Manager&#41;](install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).  
  
 **OK**  
 Klicken Sie auf diese Schaltfläche, um die Änderungen zu speichern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen, löschen oder Ändern einer freigegebenen Datenquelle &#40;Berichts-Manager&#41;](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md)   
 [Datenverbindungen, Datenquellen und Verbindungs Zeichenfolgen in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Die Inhaltsseite &#40;Berichts-Manager&#41;](../../2014/reporting-services/contents-page-report-manager.md)   
 [Erstellen, ändern und Löschen von freigegebenen Datenquellen &#40;SSRS-&#41;](report-data/create-modify-and-delete-shared-data-sources-ssrs.md)   
 [Berichts-Manager F1-Hilfe](../../2014/reporting-services/report-manager-f1-help.md)   
 [Angeben der Anmeldeinformationen und Verbindungsinformationen für Berichtsdatenquellen](report-data/specify-credential-and-connection-information-for-report-data-sources.md)  
  
  
