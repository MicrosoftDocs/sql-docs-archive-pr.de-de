---
title: Referenz zur Benutzeroberfläche des Paketkonfigurations-Assistenten Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.configwizard.selectobjects.f1
- sql12.dts.configwizard.selecconfigtype.f1
- sql12.dts.configwizard.finishdtsconfiguration.f1
- sql12.dts.configwizard.welcome.f1
ms.assetid: adca6938-6d5a-40ec-950e-dceb79d044fe
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 222c5f58ca4e942dd23909b433ab346c500fceed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621584"
---
# <a name="package-configuration-wizard-ui-reference"></a>Referenz zur Benutzeroberfläche des Paketkonfigurations-Assistenten
  Der **Paketkonfigurations-Assistent** unterstützt Sie dabei, Konfigurationen zu erstellen, durch die die Eigenschaften eines [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Pakets und seiner Objekte zur Laufzeit aktualisiert werden. Dieser Assistent wird ausgeführt, wenn Sie im Dialogfeld **Paketkonfigurationsplaner** eine neue Konfiguration hinzufügen oder eine vorhandene Konfiguration ändern. Um das Dialogfeld **Paketkonfigurationsplaner** zu öffnen, wählen Sie in **im Menü** SSIS **die Option** Paketkonfigurationen [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]aus. Weitere Informationen finden Sie unter [Erstellen von Paketkonfigurationen](../../2014/integration-services/create-package-configurations.md).  
  
> [!NOTE]  
>  Konfigurationen sind für das Paketbereitstellungsmodell verfügbar. Parameter werden für das Projektbereitstellungsmodell anstelle von Konfigurationen verwendet. Mithilfe des Projektbereitstellungsmodells können Sie [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekte auf dem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Server bereitstellen. Weitere Informationen zu Bereitstellungsmodellen finden Sie unter [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md).  
  
 In den folgenden Abschnitten werden Seiten des Assistenten beschrieben.  
  
## <a name="welcome-to-the-package-configuration-wizard-page"></a>Willkommensseite des Paketkonfigurationsassistenten  
 Mithilfe des **SSIS-Konfigurations-Assistenten** können Sie Konfigurationen erstellen, durch die die Eigenschaften eines Paketes und seiner Objekte zur Laufzeit aktualisiert werden.  
  
### <a name="options"></a>Tastatur  
 **Diese Seite nicht wieder anzeigen**  
 Die Willkommensseite beim nächsten Öffnen des Assistenten auslassen.  
  
 **Weiter**  
 Mit dieser Option können Sie zur nächsten Seite des Assistenten wechseln.  
  
## <a name="select-configuration-type-page"></a>Seite "Konfigurationstyp" auswählen  
 Auf der Seite **Konfigurationstyp auswählen** können Sie die Art der Konfiguration angeben, die erstellt werden soll.  
  
 Weitere Informationen dazu, welchen Konfigurationstyp Sie verwenden sollten, finden Sie unter [Package Configurations](../../2014/integration-services/package-configurations.md).  
  
### <a name="static-options"></a>Statische Optionen  
 **Konfigurationstyp**  
 Wählen Sie mithilfe folgender Optionen den Typ der Quelle aus, in der die Konfiguration gespeichert werden soll:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**XML-Konfigurationsdatei**|Speichert die Konfiguration als XML-Datei. Wenn Sie diesen Wert auswählen, werden die dynamischen Optionen im Abschnitt **Konfigurationstyp**angezeigt.|  
|**Umgebungsvariable**|Speichert die Konfiguration in einer der Umgebungsvariablen. Wenn Sie diesen Wert auswählen, werden die dynamischen Optionen im Abschnitt **Konfigurationstyp**angezeigt.|  
|**Registrierungseintrag**|Speichert die Konfiguration in der Registrierung. Wenn Sie diesen Wert auswählen, werden die dynamischen Optionen im Abschnitt **Konfigurationstyp**angezeigt.|  
|**Variable für das übergeordnete Paket**|Speichert die Konfiguration als Variable in dem Paket, das den Task enthält.  Wenn Sie diesen Wert auswählen, werden die dynamischen Optionen im Abschnitt **Konfigurationstyp**angezeigt.|  
|**SQL Server**|Speichert die Konfiguration in einer Tabelle in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Wenn Sie diesen Wert auswählen, werden die dynamischen Optionen im Abschnitt **Konfigurationstyp**angezeigt.|  
  
 **Weiter**  
 Zeigt die nächste Seite in der Sequenz des Assistenten an.  
  
### <a name="dynamic-options"></a>Dynamische Optionen  
  
#### <a name="configuration-type-option--xml-configuration-file"></a>Konfigurationstypoption = XML-Konfigurationsdatei  
 **Konfigurationseinstellungen direkt angeben**  
 Verwenden Sie diese Option, um die Einstellungen direkt anzugeben.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**Konfigurationsdateiname**|Geben Sie den Pfad der Konfigurationsdatei ein, die der Assistent generiert.|  
|**Durchsuchen**|Im Dialogfeld **Speicherort der Konfigurationsdatei auswählen** können Sie den Pfad für die Konfigurationsdatei angeben, die der Assistent generiert. Wenn die Datei nicht vorhanden ist, wird sie durch den Assistenten erstellt.|  
  
 **Konfigurationsspeicherort ist in einer Umgebungsvariablen gespeichert**  
 Verwenden Sie diese Option, um die Umgebungsvariable anzugeben, in der die Konfiguration gespeichert werden soll.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**Umgebungsvariable**|Wählen Sie eine Umgebungsvariable aus der Liste aus.|  
  
#### <a name="configuration-type-option--environment-variable"></a>Konfigurationstypoption = Umgebungsvariable  
 **Umgebungsvariable**  
 Wählen Sie die Umgebungsvariable aus, die die Konfigurationsinformationen enthält.  
  
#### <a name="configuration-type-option--registry-entry"></a>Konfigurationstypoption = Registrierungseintrag  
 **Konfigurationseinstellungen direkt angeben**  
 Verwenden Sie diese Option, um die Einstellungen direkt anzugeben.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**Registrierungseintrag**|Geben Sie den Registrierungsschlüssel ein, der die Konfigurationsinformationen enthält. Das Format ist \<registry key>.<br /><br /> Der Registrierungsschlüssel muss bereits in HKEY_CURRENT_USER vorhanden sein und einen Wert mit dem Namen "Value" aufweisen. Bei diesem Wert kann es sich um einen Wert vom Typ DWORD oder um eine Zeichenfolge handeln.<br /><br /> Wenn Sie einen Registrierungsschlüssel verwenden möchten, der nicht im Stamm von HKEY_CURRENT_USER gespeichert ist, verwenden Sie das Format \<Registry key\registry key\\...>, um den Schlüssel zu identifizieren.|  
  
 **Konfigurationsspeicherort ist in einer Umgebungsvariablen gespeichert**  
 Verwenden Sie diese Option, um die Umgebungsvariable anzugeben, in der die Konfiguration gespeichert werden soll.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**Umgebungsvariable**|Wählen Sie eine Umgebungsvariable aus der Liste aus.|  
  
#### <a name="configuration-type-option--parent-package-variable"></a>Konfigurationstypoption = Variable für das übergeordnete Paket  
 **Konfigurationseinstellungen direkt angeben**  
 Verwenden Sie diese Option, um die Einstellungen direkt anzugeben.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**Übergeordnete Variable**|Geben Sie die Variable im übergeordneten Paket an, die die Konfigurationsinformationen enthält.|  
  
 **Konfigurationsspeicherort ist in einer Umgebungsvariablen gespeichert**  
 Verwenden Sie diese Option, um die Umgebungsvariable anzugeben, in der die Konfiguration gespeichert wird.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**Umgebungsvariable**|Wählen Sie eine Umgebungsvariable aus der Liste aus.|  
  
#### <a name="configuration-type-options--sql-server"></a>Konfigurationstypoptionen = SQL Server  
 **Konfigurationseinstellungen direkt angeben**  
 Verwenden Sie diese Option, um die Einstellungen direkt anzugeben.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**Connection**|Wählen Sie eine Verbindung aus der Liste aus, oder klicken Sie auf **Neu** , um eine neue Verbindung herzustellen.|  
|**Konfigurationstabelle**|Wählen Sie eine vorhandene Tabelle aus, oder klicken Sie auf **Neu** , um eine SQL-Anweisung zu schreiben, die eine neue Tabelle erstellt.|  
|**Konfigurationsfilter**|Wählen Sie einen vorhandenen Konfigurationsnamen aus, oder geben Sie einen neuen Namen ein.<br /><br /> Viele SQL Server-Konfigurationen können in derselben Tabelle gespeichert werden, und jede Konfiguration kann mehrere Konfigurationselemente enthalten.<br /><br /> Dieser benutzerdefinierte Wert wird in der Tabelle gespeichert, um Konfigurationselemente zu identifizieren, die zu einer bestimmten Konfiguration gehören.|  
  
 **Konfigurationsspeicherort ist in einer Umgebungsvariablen gespeichert**  
 Verwenden Sie diese Option, um die Umgebungsvariable anzugeben, in der die Konfiguration gespeichert ist.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**Umgebungsvariable**|Wählen Sie eine Umgebungsvariable aus der Liste aus.|  
  
## <a name="select-objects-to-export-page"></a>Seite "Eigenschaften für den Exportvorgang auswählen"  
 Verwenden Sie die Seite **Zieleigenschaft auswählen** oder die Seite Eigenschaften für den Exportvorgang auswählen, um die in der Konfiguration enthaltenen Objekteigenschaften anzugeben. Mehrere Eigenschaften können nur ausgewählt werden, wenn Sie als Konfigurationstyp XML auswählen.  
  
### <a name="options"></a>Tastatur  
 **Objekte**  
 Erweitern Sie die Pakethierarchie, und wählen Sie die zu exportierenden Eigenschaften aus.  
  
 **Eigenschaftsattribute**  
 Zeigen Sie die Attribute einer Eigenschaft an.  
  
 **Weiter**  
 Mit dieser Option können Sie zur nächsten Seite des Assistenten wechseln.  
  
## <a name="completing-the-wizard-page"></a>Seite "Assistenten abschließen"  
 Mithilfe der Seite **Assistenten abschließen** können Sie einen Namen für die Konfiguration und die Einstellungen der Sicht angeben, die der Assistent zum Erstellen der Konfiguration verwendet. Nach dem Abschließen des Assistenten wird der **Paketkonfigurationsplaner** angezeigt, in dem alle Konfigurationen für das Paket aufgeführt werden.  
  
### <a name="options"></a>Tastatur  
 **Konfigurationsname**  
 Geben Sie den Namen der Konfiguration ein.  
  
 **Vorschau**  
 Zeigen Sie die Einstellungen an, die vom Assistenten zum Erstellen der Konfiguration verwendet werden.  
  
 **Fertig stellen**  
 Erstellen Sie die Konfiguration, und beenden Sie den **Paketkonfigurations-Assistenten**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von Paketkonfigurationen](../../2014/integration-services/create-package-configurations.md)  
  
  
