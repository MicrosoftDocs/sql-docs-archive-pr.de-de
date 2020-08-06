---
title: 'rsAccessedDenied: Reporting Services-Fehler | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rsAccessDenied error
ms.assetid: 2f76b1bf-96a2-4755-b76b-84e933220efc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 194006c2ef6f22b9bc27e9e8cbe1eebd027ed6b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87618458"
---
# <a name="rsaccesseddenied---reporting-services-error"></a>rsAccessedDenied – Reporting Services-Fehler
  Der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Fehler **rsAccessedDenied** tritt auf, wenn ein Benutzer keine Berechtigung zum Ausführen einer Aktion hat, z. B. wenn er nicht über eine Rollenzuweisung zum Öffnen eines Berichts verfügt oder den Browser nicht mit der entsprechenden Berechtigung geöffnet hat.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus &#124; im SharePoint-Modus|  
  
-   Wenn der Fehler beim direkten Zugreifen auf den Berichtsserver über eine URL auftritt, wird die Ausnahme einem HTTP 401-Fehler zugeordnet.  
  
-   Wenn der Fehler während der Verwendung des Berichts-Managers oder eines anderen Tools auftritt, wird der Fehler in einer Fehlermeldung angezeigt.  
  
-   Wenn der Fehler während eines geplanten Vorgangs, eines geplanten Abonnements oder einer geplanten Übermittlung auftritt, wird der Fehler nur in der Berichtsserver-Protokolldatei aufgeführt.  
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|**Produktname**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|**Ereignis-ID**|rsAccessedDenied|  
|**Ereignisquelle**|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings|  
|**Komponente**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|**Meldungstext**|Die dem Benutzer 'mydomain\myAccount' erteilten Berechtigungen reichen zum Ausführen des Vorgangs nicht aus. (rsAccessDenied) (ReportingServicesLibrary)|  
  
## <a name="user-action"></a>Benutzeraktion  
 Berechtigungen für den Zugriff auf den Inhalt und die Vorgänge des Berichtsservers werden über Rollenzuweisungen gewährt. Bei einer Neuinstallation können nur lokale Administratoren auf einen Berichtsserver zugreifen. Wenn anderen Benutzern der Zugriff gewährt werden soll, muss ein lokaler Administrator Folgendes erstellen: eine Rollenzuweisung, mit der ein Domänenbenutzer oder ein Gruppenkonto angegeben wird, mindestens eine Rolle, mit der die Aufgaben definiert werden, die vom Benutzer ausgeführt werden können, und einen Bereich (in der Regel der Basisordner oder der Stammknoten der Ordnerhierarchie des Berichtsservers). Mithilfe des Berichts-Managers können Sie die Rollenzuweisungen erstellen. Weitere Informationen finden Sie unter "Rollenzuweisung" in der SQL Server-Onlinedokumentation.  
  
 Der Fehler wird außerdem durch lokale Administration des Berichtsservers verursacht. Weitere Informationen finden Sie unter [Konfigurieren eines Berichtsservers im einheitlichen Modus für die lokale Verwaltung &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Rollenzuweisungen](../security/role-assignments.md)   
 [Erteilen von Berechtigungen für einen Berichtsserver im einheitlichen Modus](../security/granting-permissions-on-a-native-mode-report-server.md)   
 [Rollen und Berechtigungen &#40;Reporting Services&#41;](../security/roles-and-permissions-reporting-services.md)  
  
  
