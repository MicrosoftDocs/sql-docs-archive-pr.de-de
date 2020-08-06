---
title: Projekteigenschaften (SSAS-tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.depservconfig.f1
- sql12.asvs.bidtoolset.semmodelprojprop.f1
ms.assetid: 333c1fc0-361c-415a-bd68-4e057f67bcb7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 115946cca94da7ad73c540bbfabc0c5a2c44c48f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696110"
---
# <a name="project-properties-ssas-tabular"></a>Projekteigenschaften (SSAS – tabellarisch)
  In diesem Thema werden Eigenschaften für Modellprojekte beschrieben. Jedes Projekt für tabellarische Modelle verfügt über Eigenschaften für Bereitstellungsoptionen und den Bereitstellungsserver, die angeben, wie das Projekt und das Modell bereitgestellt werden. Beispielsweise den Server, auf dem das Modell bereitgestellt wird, und den Namen der bereitgestellten Modelldatenbank. Diese Einstellungen unterscheiden sich von Modelleigenschaften, die sich auf die Arbeitsbereichsdatenbank des Modells auswirken. Die hier beschriebenen Projekteigenschaften befinden sich in einem modalen Eigenschaftendialogfeld, das sich von dem Eigenschaftenfenster unterscheidet, in dem andere Typen von Eigenschaften angezeigt werden. Klicken Sie zum Anzeigen der modalen Projekteigenschaften in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]in **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und klicken Sie anschließend auf **Eigenschaften**.  
  
 Abschnitte in diesem Thema:  
  
-   [Project-Eigenschaften](#bkmk_proj_properties)  
  
-   [So konfigurieren Sie die Einstellungen der Eigenschaften "Bereitstellungsoptionen" und "Bereitstellungsserver"](#bkmk_conf_proj_settings)  
  
##  <a name="project-properties"></a><a name="bkmk_proj_properties"></a>Projekteigenschaften  
 **Bereitstellungs Optionen**  
  
|Eigenschaft|Standardeinstellung|BESCHREIBUNG|  
|--------------|---------------------|-----------------|  
|**Verarbeitungsoption**|**Standard**|Analysis Services bestimmt standardmäßig den Verarbeitungstyp, der beim Bereitstellen der an Objekten vorgenommenen Änderungen erforderlich ist. Diese Einstellung ermöglicht im Allgemeinen die schnellste Bereitstellungszeit. Sie haben aber auch die Möglichkeit, für die jeweilige Bereitstellung die vollständige Verarbeitung oder keine Verarbeitung zu wählen.|  
|**Transaktionsbereitstellung**|**False**|Gibt an, ob es sich um eine Transaktionsbereitstellung des Modells handelt. Standardmäßig ist die Bereitstellung aller oder geänderter Objekte keine Transaktionsbereitstellung bei der Verarbeitung dieser bereitgestellten Objekte. Die Bereitstellung kann erfolgreich ausgeführt werden und persistent sein, auch wenn bei der Verarbeitung ein Fehler auftritt. Sie können diese Einstellung ändern, um die Bereitstellung und Verarbeitung in einer einzelnen Transaktion zu integrieren.|  
|**Abfragemodus**|**Im Arbeitsspeicher**|Gibt die Quelle an, aus der Abfrageergebnisse zurückgegeben werden. Weitere Informationen finden Sie unter [DirectQuery-Modus &#40;SSAS – tabellarisch&#41;](directquery-mode-ssas-tabular.md).|  
  
 **Bereitstellungs Server**  
  
|Eigenschaft|Standardeinstellung|BESCHREIBUNG|  
|--------------|---------------------|-----------------|  
|**Server**|**Localhost**|Gibt eine Analysis Services-Instanz an. Standardmäßig werden Modelle in der Standardinstanz von Analysis Services auf dem lokalen Computer bereitgestellt. Sie können diese Einstellung ändern und eine benannte Instanz auf dem lokalen Computer bzw. eine beliebige Instanz auf einem Remotecomputer angeben, auf dem Sie über die Berechtigung zum Erstellen von Analysis Services-Objekten verfügen. Normalerweise sind dies Administratorberechtigungen.<br /><br /> Die Standardeinstellung für diese Eigenschaft kann im Dialogfeld Extras\Optionen auf der Seite Bereitstellung in den Analysis-Server-Einstellungen mithilfe der Eigenschaft Standardbereitstellungsserver geändert werden. Weitere Informationen finden Sie unter [Konfigurieren von Standarddatenmodellierung und Bereitstellungseigenschaften &#40;SSAS – tabellarisch&#41;](properties-ssas-tabular.md).|  
|**Edition**|**Developer**|Gibt die Edition des Analysis Services-Servers an, auf dem das Modell bereitgestellt wird. In der Serveredition sind verschiedene Funktionen definiert, die in das Projekt eingebunden werden können.|  
|**Datenbank**|**Modell**|Gibt den Namen der Analysis Services-Datenbank an, in der die Modellobjekte nach der Bereitstellung instanziiert werden. Dieser Name wird in einer Datenverbindung oder einer RSDS-Datenverbindungsdatei angegeben. Es wird empfohlen, einen Namen anzugeben, der den Typ der Analyse widerspiegelt, die mit dem Modell durchgeführt wird, z. B. AdventureWorksSalesModel.<br /><br /> ** \* \* Wichtig \* um \* ** doppelte Namen für bereitgestellte Modelle zu vermeiden, sollten Sie die Einstellung für die **Daten Bank** Eigenschaftsnamen so ändern, dass Sie den Zweck des Modells widerspiegelt. Wenn Benutzer eine Verbindung mit dem Modell als Datenquelle herstellen, wird dieser Name angezeigt.|  
|**Cubename**|**Modell**|Gibt den Namen des Datenbankcubes an, wie in der Datenverbindung für einen Berichtserstellungsclient angezeigt.|  
|**Version**|**11,0**|Die Version der Analysis Services-Instanz, auf der das Projekt bereitgestellt wird.|  
  
 **DirectQuery-Optionen**  
  
|Eigenschaft|Standardeinstellung|BESCHREIBUNG|  
|--------------|---------------------|-----------------|  
|**Identitätswechseleinstellungen**|**Standard**|Gibt die Anmeldeinformationen an, über die ein Modell, das im DirectQuery-Modus ausgeführt wird, mit Datenquellen verbunden wird. Diese Anmeldeinformationen unterscheiden sich von den Identitätswechselinformationen, die im speicherinternen Standardmodus verwendet werden. Weitere Informationen finden Sie unter [Identitätswechsel &#40;SSAS – tabellarisch&#41;](impersonation-ssas-tabular.md).|  
  
###  <a name="to-configure-deployment-options-and-deployment-server-property-settings"></a><a name="bkmk_conf_proj_settings"></a>So konfigurieren Sie Bereitstellungs Optionen und Einstellungen der Bereitstellungs Server Eigenschaft  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]in **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und klicken Sie anschließend auf **Eigenschaften**.  
  
2.  Klicken Sie im Fenster **Eigenschaften** auf eine Eigenschaft, und geben Sie dann einen Wert ein, oder klicken Sie auf den Pfeil nach unten, um eine Einstellungsoption auszuwählen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Standarddaten Modellierung und Bereitstellungs Eigenschaften &#40;tabellarischen SSAS-&#41;](properties-ssas-tabular.md)   
 [Modell Eigenschaften &#40;tabellarischen SSAS-&#41;](model-properties-ssas-tabular.md)   
 [Bereitstellung von Tabellenmodelllösungen &#40;SSAS – tabellarisch&#41;](tabular-model-solution-deployment-ssas-tabular.md)  
  
  
