---
title: Anhalten der Berichts-und Abonnement Verarbeitung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- pausing schedules
- subscriptions [Reporting Services], pausing
- report processing [Reporting Services], pausing
- shared data sources [Reporting Services]
- pausing subscription processing
- pausing report processing
- temporarily stopping report processing
- disabling shared data sources
- roles [Reporting Services], modifying
- shared schedules [Reporting Services], pausing
ms.assetid: 3cf9a240-24cc-46d4-bec6-976f82d8f830
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1607637630c507588602dd7e566917ce1eeb6080
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721052"
---
# <a name="pause-report-and-subscription-processing"></a>Anhalten der Berichts- und Abonnementverarbeitung
  Es ist nicht möglich, einen Bericht oder ein Abonnement direkt anzuhalten. Sie können die Berichts- und Abonnementverarbeitung jedoch vor Beginn der Verarbeitung oder beim Herstellen der Verbindung zu einer Datenquelle unterbrechen. Wenn Sie den Benutzern den Zugriff auf einen Bericht oder ein Abonnement verwehren, können Sie ebenfalls dessen Ausführung verhindern.  
  
 Mithilfe der folgenden Strategien kann die Ausführung eines Prozesses vorübergehend verhindert werden.  
  
## <a name="modify-role-assignments-to-prevent-access"></a>Ändern der Rollenzuweisungen zum Verhindern des Zugriffs  
 Die beste Möglichkeit, um einen Bericht nicht zur Verfügung zu stellen, ist das vorübergehende Entfernen der Rollenzuweisung, die den Zugriff auf den Bericht bereitstellt. Diese Vorgehensweise kann für alle Berichte unabhängig von der Art der Datenquellenverbindung verwendet werden. Dabei ist nur der Bericht betroffen. Die Ausführung anderer Berichte oder Elemente ist davon nicht betroffen.  
  
 Öffnen Sie die Eigenschaftenseite Sicherheit des Berichts im Berichts-Manager, um die Rollenzuweisung zu entfernen. Falls der Bericht die Sicherheit von einem übergeordneten Bericht erbt, können Sie auf **Elementsicherheit bearbeiten** klicken, um eine restriktive Sicherheitsrichtlinie zu erstellen, die Rollenzuweisungen für den Zugriff auf breiter Basis ausklammert (entfernen Sie z.B. eine Rollenzuweisung, die jedem Benutzer den Zugriff ermöglicht, und behalten Sie die Rollenzuweisung, die einer kleinen Benutzergruppe den Zugriff ermöglicht, wie z.B. Administratoren).  
  
## <a name="disable-a-shared-data-source"></a>Deaktivieren einer freigegebenen Datenquelle  
 Ein Vorteil des Verwendens freigegebener Datenquellen ist, dass Sie diese deaktivieren können, um die Ausführung eines Berichts oder eines datengesteuerten Abonnements zu verhindern. Durch das Deaktivieren einer freigegebenen Datenquelle wird die Verbindung des Berichts mit der externen Quelle getrennt. Die deaktivierte Datenquelle steht für keine Berichte und Abonnements zur Verfügung. Zum Deaktivieren einer freigegebenen Datenquelle öffnen Sie in Berichts-Manager die Datenquelle, und deaktivieren Sie das Kontrollkästchen **diese Datenquelle aktivieren** .  
  
 Beachten Sie, dass der Bericht weiterhin geladen wird, selbst wenn die Datenquelle nicht verfügbar ist. Der Bericht enthält keine Daten, aber Benutzer mit entsprechenden Berechtigungen haben Zugriff auf die Eigenschaftenseiten, Sicherheitseinstellungen, den Berichtsverlauf und die Abonnementinformationen für den Bericht.  
  
## <a name="pause-a-shared-schedule"></a>Anhalten eines freigegebenen Zeitplans  
 Wenn ein Bericht oder ein Abonnement mit einem freigegebenen Zeitplan ausgeführt wird, können Sie den Zeitplan anhalten, um die Verarbeitung zu verhindern. Alle Berichts- und Abonnementverarbeitungen, die mit dem Zeitplan gesteuert werden, werden zurückgestellt, bis der Zeitplan fortgesetzt wird. Weitere Informationen finden Sie unter Anhalten und Fortsetzen von frei [gegebenen Zeitplänen](schedules.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Reporting Services-Berichtsserver &#40;einheitlicher Modus&#41;](../report-server/reporting-services-report-server-native-mode.md)   
 [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../report-manager-ssrs-native-mode.md)   
 [Sicherheit (Eigenschaftenseite), Elemente, (Berichts-Manager)](../security-properties-page-items-report-manager.md)  
  
  
