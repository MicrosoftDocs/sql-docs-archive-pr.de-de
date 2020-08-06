---
title: Ziel-Editor für SAP BW (Seite „Zuordnungen“) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: dfa1f1d6-6b64-4331-bdc5-eaa8b7aa41a1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7c4c2803be3e2649f7425a2974dae8ac0a80fae7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87695901"
---
# <a name="sap-bw-destination-editor-mappings-page"></a>Ziel-Editor für SAP BW (Seite Zuordnungen)
  Auf der Seite **Zuordnungen** im **Ziel-Editor für SAP BW** können Sie eine Zuordnung zwischen Eingabe- und Zielspalten vornehmen.  
  
 Weitere Informationen zum SAP BW-Ziel von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW finden Sie unter [SAP BW-Ziel](sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  Die Dokumentation für Microsoft Connector 1.1 for SAP BW setzt Kenntnisse der SAP NetWeaver BW-Umgebung voraus. Weitere Informationen zu SAP NetWeaver BW oder Informationen zur Konfiguration von SAP NetWeaver BW-Objekten und -Prozessen finden Sie in der SAP-Dokumentation.  
  
 **So öffnen Sie die Seite "Zuordnungen"**  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paket, in dem das SAP BW-Ziel enthalten ist.  
  
2.  Doppelklicken Sie auf der Registerkarte **Datenfluss** auf das SAP BW-Ziel.  
  
3.  Klicken Sie im **Ziel-Editor für SAP BW**auf **Zuordnungen** , um die Seite **Zuordnungen** des Editors zu öffnen.  
  
## <a name="options"></a>Tastatur  
  
> [!NOTE]  
>  Wenn Sie nicht alle Werte kennen, die zur Konfiguration des Ziels erforderlich sind, müssen Sie ggf. Ihren SAP-Administrator um Unterstützung bitten.  
  
 Die Seite **Zuordnungen** im **Ziel-Editor für SAP BW** besteht aus zwei Abschnitten:  
  
-   Der obere Abschnitt enthält die verfügbaren Eingabe- und Zielspalten. Dort können Sie Zuordnungen zwischen den beiden Spaltentypen erstellen.  
  
-   Der untere Abschnitt ist eine Tabelle, der Sie entnehmen können, welche Eingabespalten welchen Ausgabespalten zugeordnet wurden.  
  
### <a name="upper-section-options"></a>Optionen im oberen Abschnitt  
 Der obere Abschnitt enthält die folgenden Optionen:  
  
 **Verfügbare Eingabespalten**  
 Zeigt die Liste der verfügbaren Eingabespalten an.  
  
 Um einer Zielspalte eine Eingabespalte zuzuordnen, ziehen Sie eine Spalte aus der Liste **Verfügbare Eingabespalten** auf eine Spalte in der Liste **Verfügbare Zielspalten** .  
  
 **Verfügbare Zielspalten**  
 Zeigt die Liste der verfügbaren Zielspalten an.  
  
 Um einer Zielspalte eine Eingabespalte zuzuordnen, ziehen Sie eine Spalte aus der Liste **Verfügbare Eingabespalten** auf eine Spalte in der Liste **Verfügbare Zielspalten** .  
  
 Der obere Abschnitt enthält auch ein Kontextmenü, das Sie öffnen, indem Sie mit der rechten Maustaste auf den Hintergrund klicken. Das Kontextmenü enthält die folgenden Optionen:  
  
-   **Alle Zuordnungen auswählen**  
  
-   **Ausgewählte Zuordnungen löschen**  
  
-   **Elemente nach übereinstimmenden Namen zuordnen**  
  
### <a name="lower-section-columns"></a>Spalten im unteren Abschnitt  
 Der untere Abschnitt enthält eine Tabelle der Zuordnungen und weist die folgenden Spalten auf:  
  
 **Eingabespalte**  
 Zeigt die ausgewählten Eingabespalten an.  
  
 Um derselben Zielspalte eine andere Eingabespalte zuzuordnen, wählen Sie eine andere Eingabespalte aus der Liste aus. Um eine Zuordnung zu entfernen, wählen Sie **\<ignore>** aus, um die Eingabespalte von der Ausgabe auszuschließen.  
  
 **Zielspalte**  
 Zeigt alle verfügbaren Zielspalten an, und zwar unabhängig davon, ob die Spalte zugeordnet ist oder nicht.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ziel-Editor für SAP BW &#40;Seite „Verbindungs-Manager“&#41;](sap-bw-destination-editor-connection-manager-page.md)   
 [Ziel-Editor für SAP BW &#40;Seite „Fehlerausgabe“&#41;](sap-bw-destination-editor-error-output-page.md)   
 [Ziel-Editor für SAP BW &#40;Seite „Erweitert“&#41;](sap-bw-destination-editor-advanced-page.md)   
 [F1-Hilfe zu Microsoft Connector 1.1 for SAP BW](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
