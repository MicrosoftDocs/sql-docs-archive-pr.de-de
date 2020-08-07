---
title: Konfiguration nach der Installation (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7f4417b2-0efb-4361-a79e-fa56e43ee054
author: minewiskan
ms.author: owend
ms.openlocfilehash: dfc8b620e2bcb22e316f06f2f68fbaf727ad6c12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718865"
---
# <a name="post-install-configuration-analysis-services"></a>Konfiguration nach der Installation (Analysis Services)
  Nach der Installation von Analysis Services sind weitere Konfigurationsschritte erforderlich, um einen voll funktionsfähigen Server für die allgemeine Verwendung bereitzustellen. In diesem Abschnitt werden zusätzliche Aufgaben beschrieben, die zum Abschließen der Installation ausgeführt werden. Je nach Verbindungsanforderungen müssen Sie möglicherweise auch die Authentifizierung konfigurieren (siehe [Verbindung mit Analysis Services herstellen](connect-to-analysis-services.md)).  
  
 Sobald Datenbanken zur Bereitstellung verfügbar sind, müssen zusätzliche Schritte ausgeführt werden. Sie müssen Rollenmitgliedschaften für die Datenbank konfigurieren, um den Benutzerzugriff auf die Daten zu gewähren, eine Sicherungs- und Wiederherstellungsstrategie für Datenbanken entwerfen und entscheiden, ob Daten in regelmäßigen Intervallen nach einem Verarbeitungszeitplan aktualisiert werden sollen. Weitere Informationen zur Bereitstellung und Verwaltung von Datenbanken finden Sie unter den folgenden Links: [Mehrdimensionale Modelldatenbanken &#40;SSAS&#41;](../multidimensional-models/multidimensional-model-databases-ssas.md) und [Tabellarische Modelldatenbanken &#40;SSAS – tabellarisch&#41;](../tabular-models/tabular-model-databases-ssas-tabular.md).  
  
## <a name="instance-configuration"></a>Instanzkonfiguration  
 Analysis Services ist ein replizierbarer Dienst, d. h., Sie können mehrere Instanzen des Diensts auf einem einzelnen Server installieren. Jede zusätzliche Instanz wird mithilfe von SQL Server-Setup separat als benannte Instanz installiert und unabhängig konfiguriert, um ihren jeweiligen Verwendungszweck zu erfüllen. Beispielsweise kann auf einem Entwicklungsserver Flight Recorder ausgeführt werden, oder es werden Standardwerte für die Datenspeicherung verwendet, die auf Servern mit Produktionsarbeitslasten normalerweise geändert werden müssen. Die Anpassung der Systemkonfiguration ist außerdem erforderlich, wenn die Analysis Services-Instanz auf Hardware installiert wird, die von anderen Diensten gemeinsam genutzt wird. Wenn mehrere datenintensive Anwendungen auf derselben Hardware gehostet werden, können Sie die Ressourcenverfügbarkeit anwendungsübergreifend optimieren, indem Sie die Arbeitsspeicherschwellenwerte mithilfe der Servereigenschaften herabsetzen.  
  
## <a name="post-installation-tasks"></a>Aufgaben nach der Installation  
  
|Link|Taskbeschreibung|  
|----------|----------------------|  
|[Konfigurieren der Windows-Firewall, um den Zugriff auf Analysis Services zuzulassen](configure-the-windows-firewall-to-allow-analysis-services-access.md)|Erstellen Sie eine eingehende Regel für die Windows-Firewall, damit Anforderungen über den von der Analysis Services-Instanz verwendeten TCP-Port weitergeleitet werden können. Diese Aufgabe ist erforderlich. Damit über einen Remotecomputer auf Analysis Services zugegriffen werden kann, muss eine eingehende Regel für die Firewall definiert werden.|  
|[Erteilen von Server Administrator Berechtigungen &#40;Analysis Services&#41;](grant-server-admin-rights-to-an-analysis-services-instance.md)|Während der Installation musste der Administratorrolle der Analysis Services-Instanz mindestens ein Benutzerkonto hinzugefügt werden. Administratorberechtigungen sind für routinemäßige Servervorgänge erforderlich wie die Verarbeitung von Daten aus externen relationalen Datenbanken. Verwenden Sie die Informationen in diesem Thema, um eine Mitgliedschaft zur Administratorrolle hinzuzufügen oder zu ändern.|  
|[Konfigurieren von Dienstkonten &#40;Analysis Services&#41;](configure-service-accounts-analysis-services.md)|Während der Installation wurde das Analysis Services-Dienstkonto mit geeigneten Berechtigungen bereitgestellt, um den kontrollierten Zugriff auf ausführbare Programmdateien und Datenbankdateien zu ermöglichen. Nach der Installation sollten Sie abwägen, ob die Verwendung des Dienstkontos zum Ausführen weiterer Aufgaben zulässig sein soll. Sowohl Verarbeitungs- als auch das Abfragearbeitsauslastungen können unter dem Dienstkonto ausgeführt werden. Diese Vorgänge sind nur erfolgreich, wenn das Dienstkonto über entsprechende Berechtigungen verfügt.|  
|[Registrieren einer Analysis Services-Instanz in einer Servergruppe](register-an-analysis-services-instance-in-a-server-group.md)|Mit SQL Server Management Studio (SSMS) können Sie Servergruppen zum Organisieren der SQL Server-Instanzen erstellen. Skalierbare Bereitstellungen, die mehrere Serverinstanzen umfassen, sind in Servergruppen einfacher zu verwalten. Verwenden Sie die Informationen in diesem Thema, um Analysis Services-Instanzen in SSMS-Gruppen zu organisieren.|  
|[Bestimmen des Servermodus einer Analysis Services-Instanz](determine-the-server-mode-of-an-analysis-services-instance.md)|Während der Installation wählen Sie einen Servermodus aus, der den Modelltyp (mehrdimensional oder tabellarisch) angibt, unter dem der Server ausgeführt wird. Wenn Sie unsicher sind, welchen Servermodus Sie verwenden sollen, ermitteln Sie den installierten Modus anhand der Informationen in diesem Thema.|  
|[Umbenennen einer Analysis Services Instanz](rename-an-analysis-services-instance.md)|Ein aussagekräftiger Name erleichtert es Ihnen, zwischen mehreren Instanzen mit unterschiedlichen Servermodi oder zwischen Instanzen, die in erster Linie von Abteilungen oder Teams verwendet werden, zu unterscheiden. Wenn Sie den Instanznamen in einen Namen ändern möchten, der die Verwaltung von Installationen vereinfacht, befolgen Sie die Anweisungen in diesem Thema.|  
  
## <a name="next-steps"></a>Nächste Schritte  
 Erfahren Sie, wie Sie von Microsoft-Anwendungen oder benutzerdefinierten Anwendungen, die die Clientbibliotheken verwenden, eine Verbindung mit Analysis Services herstellen. Abhängig von den Anforderungen der Lösung kann es erforderlich sein, den Dienst für die Kerberos-Authentifizierung zu konfigurieren. Für domänenübergreifende Verbindungen ist der HTTP-Zugriff erforderlich. Unter [Connect to Analysis Services](connect-to-analysis-services.md) finden Sie Anweisungen zu den nächsten Schritten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Installation für SQL Server 2014](../../../2014/database-engine/install-windows/installation-for-sql-server.md)   
 [Installieren von Analysis Services im mehrdimensionalen und Data Mining-Modus](../../sql-server/install/install-analysis-services-in-multidimensional-and-data-mining-mode.md)   
 [Installieren von Analysis Services im tabellarischen Modus](install-windows/install-analysis-services.md)   
 [PowerPivot für SharePoint 2013 Installation](install-windows/install-analysis-services-in-power-pivot-mode.md)  
  
  
