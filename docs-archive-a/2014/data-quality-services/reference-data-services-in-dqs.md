---
title: Reference Data Services in DQS | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: ef217717-6d05-443e-af26-44dc745a349d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d4ed286b5834d81f775ee097672bfbc861c0b369
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87618288"
---
# <a name="reference-data-services-in-dqs"></a>Reference Data Services in DQS
  Verweisdaten beziehen sich auf einen genauen und vollständigen Satz verwandter oder kategorisierter globaler Daten (jenseits der Begrenzungen eines Unternehmens), die auf vertrauenswürdigen öffentlichen Domänen oder von erstklassigen kommerziellen Inhaltsanbietern verfügbar sind.  
  
 Die Funktion Reference Data Service in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) ermöglicht es Ihnen, Reference Data Service-Drittanbieter zu abonnieren und Ihre Geschäftsdaten durch das Überprüfen gegen hochwertige Daten dieser Anbieter leicht zu bereinigen und zu erweitern. Sie können Dienste von führenden Data Quality Service-Anbietern innerhalb von DQS verwenden, um Ihre Daten während des Bereinigungsprozesses zu standardisieren, zu korrigieren und zu erweitern. Sie können z. B. eine Liste mit Postleitzahlen gegen die Verweisdaten abgleichen, um Adressen Ihrer Kunden zu überprüfen.  
  
 Die Funktion Reference Data Service hat die folgenden Vorteile:  
  
-   Verweisdaten ermöglichen es Ihnen, die Qualität der Daten sicherzustellen, indem Sie sie mit den garantierten Daten eines Drittanbieters vergleichen.  
  
-   Der Verweisdatenprozess wird in die Erstellung einer DQS-Wissensdatenbank und in ein Data Quality-Projekt integriert und ermöglicht es Ihnen, einen umfassenden Data Quality-Prozess einzuführen.  
  
-   Unterstützt die Verwendung von Verweis Daten sowohl aus Azure Marketplace als auch direkt von Verweis Datenanbietern von Drittanbietern.  
  
##  <a name="using-reference-data-from-azure-marketplace"></a><a name="Marketplace"></a>Verwenden von Verweis Daten aus Azure Marketplace  
 DQS unterstützt das Verwenden von Verweis Daten aus Azure Marketplace, damit Inhaltsanbieter Verweis Datendienste über den Marketplace bereitstellen können. Marketplace ist ein Dienst von Microsoft, der einen Marketplace und einen Bereitstellungskanal für hochwertige Daten und Anwendungen als Clouddienste bereitstellt. Weitere Informationen zum Marketplace finden Sie unter Informationen [zu Azure Marketplace](https://azuremarketplace.microsoft.com/marketplace/).  
  
 Die nahtlose Integration zwischen Marketplace und DQS vereinfacht die Schritte, die für das Ermitteln, Untersuchen und Abrufen von Informationen für Data Quality-Projekte innerhalb von DQS erforderlich sind. Die Daten werden von DQS genutzt und helfen DQS-Benutzern dabei, eine hohe Datenqualität durch das Kombinieren von DQS, Marketplace und Verweisdaten-Dienstanbietern auf innovative Weise zu erreichen.  
  
 Um Verweisdaten vom Marketplace in DQS für die Bereinigungsaktivität zu verwenden, müssen Sie über einen Marketplace-Kontoschlüssel verfügen. Das Erstellen eines Marketplace-Kontoschlüssels ist kostenlos. Sie bezahlen nur, wenn Sie kostenpflichtige Datasets abonnieren. Kostenlose Datasets können ohne anfallende Gebühren abonniert und verwendet werden. Ausführliche Informationen zum Erstellen eines Marketplace-Konto Schlüssels finden [Sie unter Erstellen Ihres Kontos](https://go.microsoft.com/fwlink/?LinkId=212936) () https://go.microsoft.com/fwlink/?LinkId=212936) .  
  
 Darüber hinaus können Sie die folgenden Marketplace-Aktivitäten innerhalb von DQS ausführen:  
  
-   Durchsuchen von Datasets im Marketplace  
  
-   Erstellen eines Marketplace-Kontoschlüssels  
  
-   Verwalten Ihrer Marketplace-Kontodetails, wie z. B. Kontoschlüssel und Abonnements für Datenanbieter  
  
 Sie können diese Aktivitäten auf der Registerkarte **Verweisdaten** des Bildschirms **Konfiguration** in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]ausführen.  
  
##  <a name="using-reference-data-directly-from-the-third-party-reference-data-providers"></a><a name="Direct"></a> Verwenden von Verweisdaten direkt von Reference Data Service-Drittanbietern  
 Wenn Sie nicht mit dem Internet verbunden sind und daher keinen Marketplace verwenden können, unterstützt DQS auch die direkte Verbindung zu Datenanbietern, die innerhalb des Netzwerks Ihrer Organisation verfügbar sind. Um Verweisdaten von direkten Reference Data Service-Onlinedrittanbietern zu verwenden, müssen Sie in DQS einen Datensatz für den Datenanbieter erstellen.  
  
##  <a name="how-to-cleanse-data-by-using-the-reference-data"></a><a name="HowToCleanse"></a> So bereinigen Sie Daten mithilfe der Verweisdaten  
 Das Bereinigen der Daten in DQS mithilfe von Verweisdaten umfasst die folgenden drei Schritte:  
  
1.  **Konfigurieren der Verweisdatenanbieterdetails in DQS**: Bevor Sie Verweisdaten in DQS verwenden können, müssen Sie Verweisdatendienstdetails in DQS konfigurieren.  
  
    1.  Wenn Sie Marketplace verwenden, stellen Sie einen gültigen Marketplace-Kontoschlüssel bereit, wechseln Sie im Marketplace zur Datenkategorie [Data Quality Services](../data-quality-services/data-quality-services.md) , und abonnieren Sie die erforderlichen Anbieter.  
  
    2.  Wenn Sie einen direkten Onlineverweisdatenanbieter verwenden, müssen Sie direkte Verweisdatenanbieterdetails in DQS hinzufügen, bevor Sie den Anbieter verwenden können.  
  
     Das Konfigurieren der Verweisdatenanbieterdetails in DQS muss für jeden Datenanbieter nur ein Mal erfolgen. Nur DQS-Administratoren können Verweisdateneinstellungen in DQS konfigurieren.  
  
2.  **Eine Domäne/Verbunddomäne in einer Wissensdatenbank dem Verweisdatendienst zuordnen**: Ordnen Sie eine Domäne/Verbunddomäne dem entsprechenden Verweisdatendienst zu, den Sie in Schritt 1 abonniert/hinzugefügt haben.  
  
3.  **Die zugeordneten Domänen für die Bereinigungsaktivität in einem Data Quality-Projekt verwenden**: Wählen Sie während des Erstellens eines Data Quality-Projekts für die **Bereinigungsaktivität** die Wissensdatenbank aus, die Domänen/Verbunddomänen enthält, die in Schritt 2 Verweisdatendiensten zugeordnet wurden, und führen Sie die Bereinigungsaktivität aus.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Beschreibt, wie DQS zum Verwenden von Verweisdatendiensten vom Marketplace oder von direkten Reference Data Service-Onlinedrittanbietern konfiguriert wird.|[Konfigurieren von DQS zum Verwenden von Verweisdaten](../../2014/data-quality-services/configure-dqs-to-use-reference-data.md)|  
|Beschreibt, wie einem Verweisdatendienst eine Domäne/Verbunddomäne in einer Wissensdatenbank zugeordnet wird.|[Anfügen einer Domäne oder Verbunddomäne an Verweisdaten](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md)|  
|Beschreibt, wie Daten mithilfe des Verweisdatendienstes bereinigt werden.|[Bereinigen von Daten mit Wissen über &#40;externe&#41; Verweisdaten](../../2014/data-quality-services/cleanse-data-using-reference-data-external-knowledge.md)|  
  
  
