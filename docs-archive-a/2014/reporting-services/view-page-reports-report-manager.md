---
title: Anzeigen (Seite), Berichte (Berichts-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4874ba29-429b-4dd4-a8cb-d4f087237dc2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4eb5733bf6ddfc8d7ba5a1d3d6f5ebe18ce85c66
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87722417"
---
# <a name="view-page-reports-report-manager"></a>Anzeigen (Seite, Berichte) (Berichts-Manager)
  Mithilfe der Seite Anzeigen für Berichte können Sie einen Bericht anzeigen. Wenn Sie einen Bericht erstmalig im Berichts-Manager öffnen, wird er in HTML formatiert. HTML-Berichte enthalten eine Berichtssymbolleiste, die oben im Bericht angezeigt wird, sodass Sie durch die Berichtsseiten navigieren, innerhalb eines Berichts suchen oder den Bericht in ein anderes Format exportieren können. Die folgende Abbildung zeigt die Berichtssymbolleiste.  
  
 ![Berichtssymbolleiste](media/htmlviewer-toolbar.gif "Berichtssymbolleiste")  
Berichtssymbolleiste  
  
 Berichte können in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]so konfiguriert werden, dass sie bei Bedarf oder aus einer Berichtsausführungs-Momentaufnahme ausgeführt werden. Wenn ein Bericht bei Bedarf ausgeführt wird, tritt die gesamte Daten- und Berichtsverarbeitung jedes Mal auf, wenn Sie den Bericht öffnen. Wenn Sie einen Bericht anzeigen, der zur Ausführung als Berichtsausführungs-Momentaufnahme konfiguriert ist, trat die Datenverarbeitung auf, als die Momentaufnahme erstellt wurde.  
  
## <a name="exporting-reports"></a>Exportieren von Berichten  
 Nicht alle Berichtsfunktionen sind in allen Exportformaten verfügbar. Wenn Sie einen HTML-Bericht in ein anderes Format exportieren, gibt es erwartungsgemäß Unterschiede in der Darstellung des Berichts. Enthält der Bericht interaktive Funktionen (wie Links, Lesezeichen oder Dokumentstrukturen), sind diese möglicherweise im neuen Format nicht verfügbar oder nicht auf die gleiche Weise funktionsfähig.  
  
## <a name="generating-data-feeds-from-report-data"></a>Generieren von Datenfeeds aus Berichtsdaten  
 Sie können Datenfeeds aus Berichten generieren. Die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Atom-Renderingerweiterung generiert zwei Atom-konforme Dokumente: ein Atom-Dienstdokument, in dem die vom Bericht bereitgestellten Datenfeeds aufgeführt sind, und die Datenfeeds , die die Berichtsdaten enthalten. Die Datenfeeds werden von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in einem standardisierten, Atom 1.0-konformen Format generiert, das von Anwendungen gelesen bzw. zwischen Anwendungen ausgetauscht werden kann, die Atom-konformen Datenfeeds nutzen. Der [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] -Client kann z. B. Datenfeeds nutzen, die aus Berichten generiert werden.  
  
## <a name="running-parameterized-reports"></a>Ausführen von parametrisierten Berichten  
 Ein Bericht mit Eingabefeldern und der Schaltfläche **Bericht anzeigen** wird als parametrisierter Bericht bezeichnet. Um einen parametrisierten Bericht anzuzeigen, müssen Sie möglicherweise Werte bereitstellen, die zum Ausführen des Berichts erforderlich sind.  
  
> [!NOTE]  
>  In einigen Editionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]sind Berichtsausführungs-Momentaufnahmen und einige Exportformate nicht verfügbar. Weitere Informationen finden Sie unter [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Berichts-Manager (F1-Hilfe)](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
