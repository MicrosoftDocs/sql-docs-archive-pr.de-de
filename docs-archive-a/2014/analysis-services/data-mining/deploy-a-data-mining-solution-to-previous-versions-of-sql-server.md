---
title: Bereitstellen einer Data Mining-Lösung in früheren Versionen von SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [Analysis Services]
- holdout [data mining]
- deploy [Analysis Services]
- time series [Analysis Services]
- deploying [Analysis Services - data mining]
- synchronization [Analysis Services]
- deployment [Analysis Services]
ms.assetid: 2715c245-f206-43af-8bf5-e6bd2585477a
author: minewiskan
ms.author: owend
ms.openlocfilehash: f09a37c078cf58f24db9a08e3ddcb68cb2638717
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621266"
---
# <a name="deploy-a-data-mining-solution-to-previous-versions-of-sql-server"></a>Bereitstellen von Data Mining-Lösungen für frühere Versionen von SQL Server
  In diesem Abschnitt werden bekannte Kompatibilitätsprobleme beschrieben, die bei der Bereitstellung von Data Mining-Modellen oder Data Mining-Strukturen auftreten können, wenn diese in einer Instanz von [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] für eine Datenbank erstellt worden sind, die SQL Server 2005 Analysis Services verwendet. Die gleichen Probleme können bei der Bereitstellung von Modellen auftreten, die in SQL Server 2005 für eine Instanz von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]erstellt wurden.  
  
 Die Bereitstellung für eine Instanz von SQL Server 2000 Analysis Services wird nicht unterstützt.  
  
 [Bereitstellen von Zeitreihenmodellen](#bkmk_TimeSeries)  
  
 [Bereitstellen von Modellen mit zurückgehaltenen Daten](#bkmk_Holdout)  
  
 [Bereitstellen von Modellen mit Filtern](#bkmk_Filter)  
  
 [Wiederherstellen von Datenbanksicherungen](#bkmk_Backup)  
  
 [Verwenden der Datenbanksynchronisierung](#bkmk_Synch)  
  
##  <a name="deploying-times-series-models"></a><a name="bkmk_TimeSeries"></a> Bereitstellen von Zeitreihenmodellen  
 Der Microsoft Time Series-Algorithmus wurde in SQL Server 2008 um einen zweiten Algorithmus namens ARIMA ergänzt. Weitere Informationen zu den Änderungen im Time Series-Algorithmus finden Sie unter [Microsoft Time Series-Algorithmus](microsoft-time-series-algorithm.md).  
  
 Zeitreihenminingmodelle, die den neuen ARIMA-Alorithmus nutzen, können daher bei der Bereitstellung für eine Instanz von SQL Server 2005 Analysis Services ein abweichendes Verhalten aufweisen.  
  
 Wenn Sie den Parameter PREDICTION_SMOOTHING explizit so festgelegt haben, dass bei der Bereitstellung des Modells für eine Instanz von SQL Server 2005 eine Kombination aus ARTXP- und ARIMA-Modellen zur Vorhersage verwendet wird, gibt Analysis Services eine Fehlermeldung aus, laut der der Parameter nicht gültig ist. Um diesen Fehler zu vermeiden, müssen Sie den Parameter PREDICTION_SMOOTHING löschen und die Modelle in reine ARTXP-Modelle umwandeln.  
  
 Wenn Sie hingegen ein Zeitreihenmodell verwenden, das mit SQL Server 2005 Analysis Services für eine Instanz von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]erstellt wurde, und Sie das Miningmodell in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]öffnen, müssen die Definitionsdateien zunächst in das neue Format umgewandelt werden, bevor allen Zeitreihenmodellen standardmäßig zwei neue Parameter hinzugefügt werden. Der Parameter FORECAST_METHOD wird mit dem Standardwert MIXED, der Parameter PREDICTION_SMOOTHING mit dem Standardwert 0,5 hinzugefügt. Solange Sie das Modell nicht neu bearbeiten, wird weiterhin nur ARTXP verwendet. Sobald Sie das Modell jedoch neu bearbeiten, ändert sich die Vorhersage, und es werden sowohl ARIMA als auch ARTXP verwendet.  
  
 Wenn Sie das Modell nicht ändern möchten, sollten Sie es also nur durchsuchen und auf keinen Fall bearbeiten. Alternativ können Sie den FORECAST_METHOD-Parameter oder den PREDICTION_SMOOTHING-Parameter explizit festlegen.  
  
 Weitere Informationen zum Konfigurieren von gemischten Modellen finden Sie unter [Technische Referenz für den Microsoft Time Series-Algorithmus](microsoft-time-series-algorithm-technical-reference.md).  
  
 Wenn es sich beim Provider, der als Datenquelle des Modells verwendet wird, um SQL Client Data Provider 10 handelt, müssen Sie auch die Datenquellendefinition ändern, um die vorherige Version von SQL Server Native Client anzugeben. Andernfalls wird von [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] ein Fehler generiert, wenn sie angeben, dass der Anbieter nicht registriert wird.  
  
##  <a name="deploying-models-with-holdout"></a><a name="bkmk_Holdout"></a> Bereitstellen von Modellen mit Zurückhaltung  
 Wenn Sie mithilfe von [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] eine Miningstruktur erstellen, die eine Zurückhaltungspartition zum Testen von Data Mining-Modellen umfasst, kann die Miningstruktur für eine Instanz von SQL Server 2005 bereitgestellt werden. Die Partitionierungsdaten gehen dabei jedoch verloren.  
  
 Wenn Sie die Miningstruktur in SQL Server 2005 Analysis Services öffnen, wird in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] ein Fehler generiert und die Struktur zum Entfernen der Zurückhaltungspartition neu erstellt.  
  
 Nachdem die Struktur neu erstellt wurde, ist die Größe der zurück Haltungs Partition nicht mehr in der Eigenschaftenfenster verfügbar. der Wert \<ddl100_100:HoldoutMaxPercent> 30) ist jedoch \</ddl100_100:HoldoutMaxPercent> möglicherweise noch in der ASSL-Skriptdatei vorhanden.  
  
##  <a name="deploying-models-with-filters"></a><a name="bkmk_Filter"></a> Bereitstellen von Modellen mit Filtern  
 Wenn Sie mithilfe von [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] einen Filter auf ein Miningmodell anwenden, kann das Modell für eine Instanz von SQL Server 2005 bereitgestellt werden, der Filter wird jedoch nicht angewendet.  
  
 Wenn Sie das Miningmodell öffnen, wird von [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ein Fehler generiert, und das Modell wird neu erstellt, um den Filter zu entfernen.  
  
##  <a name="restoring-from-database-backups"></a><a name="bkmk_Backup"></a> Wiederherstellen von Datenbanksicherungen  
 Datenbanksicherungen, die in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] für eine Instanz von SQL Server 2005 erstellt worden sind, können nicht wiederhergestellt werden. Wenn Sie einen entsprechenden Versuch starten, erzeugt SQL Server Management Studio einen Fehler.  
  
 Wenn Sie eine Sicherung einer SQL Server 2005 Analysis Services-Datenbank erstellen und diese Sicherung in einer Instanz von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]wiederherstellen, werden alle Zeitreihenmodelle wie im Abschnitt oben beschrieben geändert.  
  
##  <a name="using-database-synchronization"></a><a name="bkmk_Synch"></a>Daten Bank Synchronisierung verwenden  
 Die Datenbanksynchronisierung von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] zu SQL Server 2005 wird nicht unterstützt.  
  
 Wenn Sie versuchen, eine [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Datenbank zu synchronisieren, gibt der Server einen Fehler zurück, und die Datenbanksynchronisierung schlägt fehl.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Analysis Services Backward Compatibility](../analysis-services-backward-compatibility.md)  
  
  
