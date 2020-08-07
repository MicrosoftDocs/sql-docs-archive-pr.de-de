---
title: Eingebettete und freigegebene Datenverbindungen oder Datenquellen (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- embedded data sources
- shared data sources
- data sources
ms.assetid: f417782c-b85a-4c4d-8a40-839176daba56
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a4b4020665e74377c048cb4be9c0cbddf97b2728
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719633"
---
# <a name="embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs"></a>Eingebettete und freigegebene Datenverbindungen oder Datenquellen (Berichts-Generator und SSRS)
  Berichte rufen Daten für einen Bericht mithilfe von Datenverbindungen ab, wenn eine Abfrage ausgeführt oder der Bericht verarbeitet wird. Sie können aus einer Liste integrierter Datenverbindungstypen auswählen, um eine Verbindung mit einer relationalen Datenbank, einer mehrdimensionalen Datenbank, einem Webdienst oder einer anderen Datenquelle herzustellen. Beim Beschreiben von Datenverbindungen werden die folgenden Begriffe verwendet.  
  
-   **Datenverbindung.** Wird auch als *Datenquelle*. Eine Datenverbindung umfasst einen Namen und Verbindungseigenschaften, die vom Verbindungstyp abhängen. Programmbedingt enthält eine Datenverbindung keine Anmeldeinformationen. Eine Datenverbindung gibt nicht an, welche Daten aus der externen Datenquelle abgerufen werden sollen. Geben Sie hierzu beim Erstellen eines Datasets eine Abfrage an.  
  
-   **Datenquellendefinition.** Eine Datei, die die XML-Darstellung einer Berichtsdatenquelle enthält. Wenn ein Bericht veröffentlicht wird, werden seine Datenquellen unabhängig von der Berichtsdefinition auf dem Berichtsserver oder der SharePoint-Website als Datenquellendefinitionen gespeichert. Ein Berichtsserveradministrator kann z. B. die Verbindungszeichenfolge oder die Anmeldeinformationen aktualisieren. Auf einem systemeigenen Berichtsserver lautet der Dateityp RDS. Auf einer SharePoint-Website lautet der Dateityp RSDS.  
  
-   **Verbindungs Zeichenfolge.** Eine Verbindungszeichenfolge ist eine Zeichenfolgenversion der Verbindungseigenschaften, die zum Herstellen einer Verbindung mit einer Datenquelle erforderlich sind. Verbindungseigenschaften unterscheiden sich je nach Datenverbindungstyp. Beispiele finden Sie unter [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md).  
  
-   **Freigegebene Datenquelle.** Eine auf einem Berichtsserver oder einer SharePoint-Website verfügbare Datenquelle, die von mehreren Berichten verwendet wird.  
  
-   **Eingebettete Datenquelle.** Wird auch als *berichtsspezifische Datenquelle*bezeichnet. Eine Datenquelle, die in einem Bericht definiert und nur von diesem Bericht verwendet wird.  
  
-   **Daten.** Anmeldeinformationen sind die Authentifizierungsinformationen, die für den Zugriff auf externe Daten bereitgestellt werden müssen.  
  
 Der Unterschied zwischen den eingebetteten und den freigegebenen Datenquellen ist die Art der Erstellung, Speicherung und Verwaltung.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
## <a name="shared-data-sources"></a>Freigegebene Datenquellen  
 Freigegebene Datenquellen sind hilfreich für Datenquellen, die Sie häufig verwenden. Es wird empfohlen, dass Sie so oft wie möglich freigegebene Datenquellen verwenden. Mit ihnen können Berichte und der Berichtszugriff einfacher verwaltet und Berichte und die Datenquellen, auf die sie zugreifen, sicherer gemacht werden. Wenn Sie eine freigegebene Datenquelle benötigen, wenden Sie sich an den Systemadministrator. Er erstellt eine freigegebene Datenquelle für Sie.  
  
 Freigegebene Datenquellen können nicht in Berichts-Generator erstellt werden. Sie können zum Berichtsserver wechseln und dort eine freigegebene Datenquelle auswählen. Weitere Informationen finden Sie unter [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md).  
  
 In Berichts-Designer können Sie nicht zu einer freigegebenen Datenquelle auf dem Berichtsserver wechseln. Sie können freigegebene Datenquellen als Teil eines Projekts im Projektmappen-Explorer erstellen und auswählen, ob sie auf einem Berichtsserver bereitgestellt werden sollen. Sie können festlegen, sie wegen Unterschiede in vom Computer oder dem Berichtsserver erforderlichen Anmeldeinformationen nur lokal zu verwenden. Weitere Informationen finden Sie unter [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md).  
  
 Das folgende Symbol zeigt ein frei gegebenes Datenquellen Element in der Ordnerhierarchie des Berichts Servers an: Symbol für frei ![gegebene Datenquelle](media/hlp-16datasource.png "Symbol für freigegebene Datenquelle")  
  
## <a name="embedded-data-sources"></a>Eingebettete Datenquellen  
 Eine eingebettete Datenquellenverbindung ist eine Datenverbindung, die in der Berichtsdefinition gespeichert wird. Eingebettete Informationen für eine Datenquellenverbindung können nur in dem Bericht verwendet werden, in den die Informationen eingebettet wurden. Verwenden Sie das Dialogfeld **Datenquelleneigenschaften** , um eingebettete Datenquellen zu definieren und zu verwalten.  
  
##  <a name="comparing-embedded-and-shared-data-sources"></a><a name="Comparing"></a>Vergleichen von eingebetteten und freigegebenen Datenquellen  
 In der folgenden Tabelle werden die Unterschiede zwischen eingebetteten und freigegebenen Datenquellen zusammengefasst:  
  
|BESCHREIBUNG|Embedded<br /><br /> Data source|Shared<br /><br /> Data source|  
|-----------------|------------------------------|----------------------------|  
|Die Datenverbindung ist in die Berichtsdefinition eingebettet.|![Verfügbar](media/greencheck.gif "Verfügbar")||  
|Der Zeiger auf die Datenverbindung auf dem Berichtsserver ist in die Berichtsdefinition eingebettet.||![Verfügbar](media/greencheck.gif "Verfügbar")|  
|Wird auf dem Berichtsserver verwaltet.|![Verfügbar](media/greencheck.gif "Verfügbar")|![Verfügbar](media/greencheck.gif "Verfügbar")|  
|Ist für freigegebene Datasets erforderlich.||![Verfügbar](media/greencheck.gif "Verfügbar")|  
|Ist für Komponenten erforderlich.||![Verfügbar](media/greencheck.gif "Verfügbar")|  
  
## <a name="data-source-credentials"></a>Anmeldeinformationen für die Datenquelle  
 Anmeldeinformationen werden beim Erstellen einer eingebetteten Datenquelle, beim Ausführen einer Abfrage oder beim Abrufen von Daten während der Berichtsverarbeitung verwendet. Der Besitzer der Datenquelle legt den für den Zugriff auf die Daten erforderlichen Anmeldeinformationstyp fest. Anmeldeinformationen werden unabhängig von der Datenverbindung auf einem Berichtsserver, einer SharePoint-Website oder auf einem lokalen Computer in einer Berichterstellungsumgebung verwaltet. Abhängig vom Datenquellentyp können Anmeldeinformationen gespeichert werden, um Aufforderungen zu vermeiden, oder so konfiguriert werden, dass jeder Benutzer zur Eingabe aufgefordert wird. Die erforderlichen Anmeldeinformationen können sich unterscheiden, je nachdem, ob Sie die Verbindung mit der Datenquelle von Ihrem Computer oder vom Berichtsserver herstellen. Weitere Informationen finden Sie unter [Angeben von Anmelde Informationen in Berichts-Generator](../../2014/reporting-services/specify-credentials-in-report-builder.md) und [Datenverbindungen, Datenquellen und Verbindungs](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)Zeichenfolgen in Reporting Services.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Hinzufügen von Daten zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](report-data/report-datasets-ssrs.md)   
 [Konzepte der Berichterstellung &#40;Berichts-Generator und SSRS&#41;](report-design/report-authoring-concepts-report-builder-and-ssrs.md)   
 [Datenquellen, die von Reporting Services &#40;SSRS unterstützt werden&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md)   
 [Hinzufügen und Überprüfen einer Datenverbindung oder Datenquelle &#40;Berichts-Generator und SSRS&#41;](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)   
 [Eingebettete und freigegebene Datasets &#40;Berichts-Generator und SSRS&#41;](report-data/embedded-and-shared-datasets-report-builder-and-ssrs.md)  
  
  
