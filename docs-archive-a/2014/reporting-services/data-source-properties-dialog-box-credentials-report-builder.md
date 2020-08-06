---
title: Datenquellen Eigenschaften (Dialog Feld), Anmelde Informationen (Berichts-Generator) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10017"
ms.assetid: 4531f09f-d653-4c05-a120-d7788838bc99
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9e47ba571e2b0adf2738499c1d027a4edde86e3f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619636"
---
# <a name="data-source-properties-dialog-box-credentials-report-builder"></a>Datenquelleigenschaften (Dialogfeld), Anmeldeinformationen (Berichts-Generator)
  Wählen Sie im Dialogfeld **Datenquelleneigenschaften** die Option **Anmeldeinformationen** aus, um die Anmeldeinformationen für eine eingebettete Datenquelle im Bericht anzuzeigen und zu ändern. Die von Ihnen bereitgestellten Anmeldeinformationen werden für den Zugriff auf die Datenquelle für die Berichtsvorschau verwendet. Weitere Informationen zu Anmeldeinformationen finden Sie unter [Angeben von Anmeldeinformationen im Berichts-Generator](../../2014/reporting-services/specify-credentials-in-report-builder.md).  
  
## <a name="options"></a>Tastatur  
 **Windows-Authentifizierung verwenden (Integrierte Sicherheit)**  
 Wählen Sie diese Option aus, um die Windows-Authentifizierung zu verwenden.  
  
 **Diesen Benutzernamen und dieses Kennwort verwenden**  
 Wählen Sie diese Option aus, um einen bestimmten Benutzernamen und ein bestimmtes Kennwort bereitzustellen. Für eingebettete Datenquellen gilt Folgendes: Wenn Sie das Berichtsserverprojekt auf dem Zielserver veröffentlichen, werden der Benutzername und das Kennwort als gespeicherte Anmeldeinformationen für die Datenbank gesichert. Wenn Sie den Benutzernamen und das Kennwort als Windows-Anmeldeinformationen verwenden möchten, können Sie die Eigenschaften für die veröffentlichte freigegebene Datenquelle auf dem Zielserver ändern. Weitere Informationen finden Sie unter [Erstellen, Löschen oder Ändern einer freigegebenen Datenquelle &#40;Berichts-Manager&#41;](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md) in der [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Dokumentation in der -[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [Onlinedokumentation](https://go.microsoft.com/fwlink/?linkid=121312).  
  
 **Benutzername**  
 Geben Sie einen Benutzernamen ein, um sich bei der Datenquelle anzumelden.  
  
 **Kennwort**  
 Geben Sie ein Kennwort ein, um sich bei der Datenquelle anzumelden.  
  
 **Eingabeaufforderung zu Anmeldeinformationen**  
 Aktivieren Sie diese Option, um beim Ausführen des Berichts eine Aufforderung zur Eingabe von Anmeldeinformationen anzuzeigen.  
  
 **Eingabeaufforderungs-Zeichenfolge eingeben**  
 Geben Sie einen Satz ein, mit dem der Benutzer zur Eingabe von Anmeldeinformationen für die Datenquelle aufgefordert wird.  
  
 **Keine Anmelde Informationen**  
 Wählen Sie diese Option aus, wenn keine Anmeldeinformationen für die Datenquelle bereitgestellt werden sollen. Diese Option kann nur verwendet werden, wenn die Datenquelle keine Anmeldeinformationen annimmt oder wenn Sie Anmeldeinformationen auf andere Art übergeben.  
  
 Bei einigen Datenerweiterungen muss das Konto für die unbeaufsichtigte Ausführung auf dem Berichtsserver konfiguriert werden.  
  
 Weitere Informationen finden Sie im Thema für die entsprechenden Datenquelle in [Hinzufügen von Daten aus externen Datenquellen &#40;SSRS&#41;](report-data/add-data-from-external-data-sources-ssrs.md) und [Konfigurieren des unbeaufsichtigten Ausführungskontos &#40;SSRS-Konfigurations-Manager&#41;](install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) in der [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Dokumentation in der -[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [Onlinedokumentation](https://go.microsoft.com/fwlink/?linkid=121312).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Berichts-Generator Hilfe zu Dialog Feldern, Bereichen und Assistenten](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Dialog Feld "Datenquellen Eigenschaften", "Allgemein" &#40;Berichts-Generator&#41;](../../2014/reporting-services/data-source-properties-dialog-box-general-report-builder.md)   
 [Hinzufügen und Überprüfen einer Datenverbindung oder Datenquelle &#40;Berichts-Generator und SSRS&#41;](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)   
 [Hinzufügen von Daten zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](report-data/report-datasets-ssrs.md)  
  
  
