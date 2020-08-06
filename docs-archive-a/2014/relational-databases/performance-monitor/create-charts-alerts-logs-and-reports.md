---
title: Erstellen von Diagrammen, Warnungen, Protokollen und Berichten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- System Monitor [SQL Server], charts and reports
- charts [SQL Server]
- reports [SQL Server]
- reports [SQL Server], creating
- Windows System Monitor [SQL Server], charts and reports
- logs [SQL Server], System Monitor
- System Monitor [SQL Server], logs
- Windows System Monitor [SQL Server], logs
ms.assetid: c9162b37-e5dc-43d1-a3aa-1e9ebc69fecc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3a0c95c3f483a8af3e3e68d9c5c7d3caf44350d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87723730"
---
# <a name="create-charts-alerts-logs-and-reports"></a>Erstellen von Diagrammen, Warnungen, Protokollen und Berichten
  Der Systemmonitor ermöglicht Ihnen das Erstellen von Diagrammen, Warnungen, Protokollen und Berichten für die Überwachung einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="charts"></a>Diagramme  
 Mit Diagrammen lässt sich die aktuelle Leistung ausgewählter Objekte und Leistungsindikatoren überwachen, wie z. B. CPU-Nutzung oder Datenträger-E/A. Sie können verschiedene Kombinationen von Systemmonitorobjekten und -Leistungsindikatoren zu einem Diagramm hinzufügen. Darüber hinaus können Sie einem Diagramm [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Objekte und -Leistungsindikatoren hinzufügen.  
  
 Jedes Diagramm stellt eine Teilmenge der Informationen dar, die Sie überwachen möchten. So kann ein Diagramm beispielsweise die Statistiken über die Speicherauslastung und ein zweites Diagramm die Statistiken über die Datenträger-E/A nachverfolgen.  
  
 Die Verwendung eines Diagramms kann sich für die folgenden Aufgaben als nützlich erweisen:  
  
-   Überprüfen, weshalb ein Computer oder eine Anwendung langsam oder ineffizient ist  
  
-   Kontinuierliches Überwachen der Systeme, um Leistungsprobleme, die stoßweise auftreten, zu erkennen  
  
-   Feststellen, weshalb die Kapazität erhöht werden muss  
  
-   Anzeigen einer Tendenz in einem Liniendiagramm  
  
-   Anzeigen eines Vergleichs in einem Histogramm  
  
 Diagramme sind für das kurzfristige Überwachen in Echtzeit von lokalen Computern oder Remotecomputern nützlich, z. B. wenn Sie ein Ereignis überwachen möchten, während es eintritt.  
  
## <a name="alerts"></a>Alerts  
 Mithilfe von Warnungen kann der Systemmonitor bestimmte Ereignisse nachverfolgen und Sie ggf. von diesen Ereignissen in Kenntnis setzen. Ein Warnungsprotokoll kann die aktuelle Leistung ausgewählter Leistungsindikatoren und Instanzen für Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]überwachen. Wenn ein Leistungsindikator einen bestimmten Wert überschreitet, zeichnet das Protokoll das Datum und den Zeitpunkt des Ereignisses auf. Ein Ereignis kann auch eine Netzwerkwarnung generieren. Sie können ein angegebenes Programm ausführen lassen, wenn ein Ereignis zum ersten Mal eintritt, oder jedes Mal, wenn das Ereignis eintritt. So kann eine Warnung beispielsweise eine Netzwerknachricht an alle Systemadministratoren senden, dass die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nur noch wenig Speicherplatz aufweist.  
  
## <a name="logs"></a>Protokolle  
 Protokolle ermöglichen es Ihnen, Informationen über die aktuelle Aktivität ausgewählter Objekte und Computer aufzuzeichnen, um sie später anzuzeigen oder zu analysieren. Sie können Daten von mehreren Systemen in einer einzelnen Protokolldatei auflisten. So können Sie beispielsweise verschiedene Protokolle erstellen, um Informationen zur Leistung ausgewählter Objekte auf verschiedenen Computern aufzulisten, und sie später auswerten. Sie können diese Auswahlen unter einem Dateinamen speichern und wiederverwenden, wenn Sie zu Vergleichszwecken ein anderes Protokoll mit ähnlichen Informationen erstellen möchten.  
  
 Protokolldateien enthalten umfangreiche Informationen für die Problembehandlung oder Planung. Während Diagramme, Warnungen und Berichte Informationen über die aktuelle Aktivität bereitstellen, können Sie mit Protokolldateien Leistungsindikatoren über eine längere Zeitspanne nachverfolgen. Auf diese Weise können Sie die Informationen gründlich analysieren und die Systemleistung längerfristig dokumentieren.  
  
## <a name="reports"></a>Berichte  
 Berichte ermöglichen es Ihnen, Werte für Leistungsindikatoren und Instanzen, die sich ständig ändern, für ausgewählte Objekte anzuzeigen. Werte werden in Spalten für jede Instanz angezeigt. Sie können die Intervalle für Berichte anpassen, Momentaufnahmen drucken und Daten exportieren. Wenn Sie die reinen Zahlen anzeigen möchten, eignen sich Berichte am besten.  
  
 Weitere Informationen zum Erstellen von Diagrammen, Warnungen, Protokollen und Berichten sowie zu Windows-Objekten und -Leistungsindikatoren finden Sie in der Windows-Dokumentation.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](monitor-resource-usage-system-monitor.md)  
  
  
