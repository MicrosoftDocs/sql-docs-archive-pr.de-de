---
title: Shortcutabfragedateien (MDS-Add-In für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 1ba0219a-6c40-41fa-aff9-8c8f41ef3220
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fe1bdbdadabe0e6448ed3bdc65316104fb26ba43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698372"
---
# <a name="shortcut-query-files-mds-add-in-for-excel"></a>Shortcutabfragedateien (MDS-Add-In für Excel)
  Verwenden Sie in [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]Shortcutabfragedateien, um häufig verwendete Daten schnell zu verbinden und zu laden. Sie können sie auch verwenden, wenn Sie MDS-Daten für andere freigeben möchten. Statt das Arbeitsblatt zu speichern und es per E-Mail zu senden, sollten Sie eine Shortcutabfragedatei speichern und stattdessen diese per E-Mail senden. Dadurch wird sichergestellt, dass Sie beide eine Verbindung mit dem MDS-Repository herstellen, um die aktuellsten Daten abzurufen.  
  
 Shortcutabfragedateien sind XML-Dateien, die Informationen über Folgendes enthalten:  
  
-   Die MDS-Repositoryverbindung.  
  
-   Das Modell, die Version und die Entität.  
  
-   Alle Filter, die angewendet wurden, als die Verknüpfung erstellt wurde.  
  
-   Die Reihenfolge der Spalten von links nach rechts, als die Verknüpfung erstellt wurde.  
  
 Sie können diese Dateien in einer Liste speichern und eine Auswahl treffen, wenn Sie das Add-In öffnen. Sie können sie auf den Computer oder einen freigegebenen Speicherort exportieren, oder Sie können sie an andere senden.  
  
## <a name="queryopener-application"></a>QueryOpener-Anwendung  
 Für alle Benutzer, die den [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] installieren, ist eine Anwendung mit dem Namen QueryOpener installiert. Diese Anwendung wird verwendet, um Shortcutabfragedateien im [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]zu öffnen. Wenn Sie auf eine Shortcutabfragedatei doppelklicken, wird diese Anwendung automatisch zum Öffnen der Datei im Add-In verwendet.  
  
 Wenn Sie eine Shortcutabfragedatei mit dieser Anwendung öffnen, werden Sie aufgefordert, die Verbindung mit einer „sicheren“ Verbindung herzustellen. Dies bedeutet, dass Sie Inhalt von diesem Speicherort vertrauen. Jedes Mal, wenn Sie eine Verbindung als sicher markieren, wird sie einer Liste hinzugefügt. Wenn Sie diese Liste löschen möchten, öffnen Sie das Dialogfeld **Einstellungen** und klicken im Abschnitt **Zur sicheren Liste hinzugefügte Server** auf **Auswahl aufheben**.  
  
 Der Standard Speicherort für die Anwendung ist *Laufwerk*: \Programme\Microsoft SQL server\120\master Data services\excel Add-In\Microsoft.MasterDataServices.QueryOpener.exe.  
  
 Es gibt zwei Möglichkeiten, Shortcutabfragedateien zu öffnen: Sie können sie importieren, oder Sie können auf sie doppelklicken und sie werden automatisch geöffnet.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Speichern des Inhalts des aktiven Arbeitsblatts als Shortcutabfragedatei.|[Speichern einer Shortcutabfragedatei &#40;MDS-Add-In für Excel&#41;](save-a-shortcut-query-file-mds-add-in-for-excel.md)|  
|Senden Sie eine Shortcutabfragedatei, die den Inhalt des aktiven Arbeitsblatts darstellt.|[Senden einer Shortcutabfragedatei &#40;MDS-Add-In für Excel&#41;](email-a-shortcut-query-file-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   [Verbindungen &#40;MDS-Add-In für Excel&#41;](connections-mds-add-in-for-excel.md)  
  
-   [Master Data Services-Add-In für Microsoft Excel](master-data-services-add-in-for-microsoft-excel.md)  
  
-   [Sicherheit &#40;Master Data Services&#41;](../security-master-data-services.md)  
  
  
