---
title: Bereitstellen einer Datenverarbeitungserweiterung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], deploying
- Extension element
- deploying [Reporting Services], extensions
ms.assetid: e5c0b5a9-1386-47cb-aade-96653ecfaa54
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 84fc2d2853ce7a6aae77f313ef0f4026ad2f35cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87725285"
---
# <a name="deploying-a-data-processing-extension"></a>Bereitstellen von Datenverarbeitungserweiterungen
  Wenn Sie die [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Datenverarbeitungserweiterung geschrieben und in eine [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]-Bibliothek kompiliert haben, müssen Sie sie für den Berichtsserver und den Berichts-Designer erkennbar machen. Dazu müssen Sie lediglich die Erweiterung in die entsprechenden Verzeichnisse kopieren und Einträge zu den zugehörigen [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Konfigurationsdateien hinzufügen.  
  
## <a name="configuration-file-extension-element"></a>Extension-Element für die Konfigurationsdatei  
 Datenverarbeitungserweiterungen, die Sie für den Berichtsserver oder den Berichts-Designer bereitstellen, müssen in den Konfigurationsdateien als **Extension**-Elemente hinzugefügt werden. Bei diesen Dateien handelt es sich um RSReportServer.config für den Berichtsserver und RSReportDesigner.config für den Berichts-Designer.  
  
 In der folgenden Tabelle werden die Attribute für das **Extension**-Element für Datenverarbeitungserweiterungen beschrieben.  
  
|attribute|BESCHREIBUNG|  
|---------------|-----------------|  
|`Name`|Ein eindeutiger Name für die Erweiterung, z. B. "SQL" für die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenverarbeitungserweiterung oder "OLEDB" für die OLE DB-Datenverarbeitungserweiterung. Die maximale Länge für das `Name`-Attribut beträgt 255 Zeichen. Der Name muss für sämtliche Einträge im **Extension** -Element einer Konfigurationsdatei eindeutig sein.|  
|`Type`|Eine durch Trennzeichen getrennte Liste, die den vollqualifizierten Namespace und den Namen der Assembly enthält|  
|`Visible`|Der Wert `false` gibt an, dass die Datenverarbeitungserweiterung auf Benutzeroberflächen nicht sichtbar sein soll. Wenn das Attribut nicht enthalten ist, ist `true` der Standardwert.|  
  
 Weitere Informationen über die Dateien „RSReportServer.config“ und „RSReportDesigner.config“ finden Sie unter [Reporting Services-Konfigurationsdateien](../../report-server/reporting-services-configuration-files.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|Beschreibung|  
|-----------|-----------------|  
|[Gewusst wie: Bereitstellen einer Datenverarbeitungserweiterung für einen Berichtsserver](deploying-a-data-processing-extension-to-a-report-server.md)|Beschreibt, wie Sie eine Datenverarbeitungserweiterung auf einem Berichtsserver bereitstellen|  
|[Gewusst wie: Bereitstellen einer Datenverarbeitungserweiterung für den Berichts-Designer](deploying-a-data-processing-extension-to-report-designer.md)|Beschreibt, wie Sie eine Datenverarbeitungserweiterung für den Berichts-Designer bereitstellen|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Reporting Services Erweiterungen](../reporting-services-extensions.md)   
 [Implementieren einer Datenverarbeitungs Erweiterung](implementing-a-data-processing-extension.md)   
 [Reporting Services-Erweiterungsbibliothek](../reporting-services-extension-library.md)  
  
  
