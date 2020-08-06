---
title: Parameter erstellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.parameterwindow.f1
ms.assetid: cd5d675b-dd5d-49cc-8b1f-dc717a973f99
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a26ae08c08a32b0593be8c9a2777b7cfe9c884fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609991"
---
# <a name="create-parameters"></a>Erstellen von Parametern
  Sie verwenden [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] , um Projektparameter und Paketparameter zu erstellen. Die folgenden Prozeduren stellen schrittweise Anweisungen zum Erstellen von Paket-/Projektparametern bereit.  
  
> [!NOTE]  
>  Wenn Sie ein Projekt, das Sie mit einer früheren Version von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] erstellt haben, in das Projektbereitstellungsmodell konvertieren, können Sie mit dem **Assistent für die Konvertierung von Integration Services-Projekten** Parameter auf Grundlage von Konfigurationen erstellen. Weitere Informationen finden Sie unter [Deploy Projects to Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md).  
  
### <a name="to-create-package-parameters"></a>So erstellen Sie Paketparameter  
  
1.  Öffnen Sie das Paket in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], und klicken Sie dann auf die Registerkarte **Parameter** im SSIS-Designer.  
  
     ![Registerkarte „Paketparameter“](media/denali-package-parameters.gif "Registerkarte „Paketparameter“")  
  
2.  Klicken Sie auf die Schaltfläche **Parameter hinzufügen** auf der Symbolleiste.  
  
     ![Symbolleisten Schaltfläche](media/denali-parameter-add.gif "Symbolleistenschaltfläche „Hinzufügen“")  
  
3.  Geben Sie Werte für die Eigenschaften **Name**, **Datentyp**, **Wert**, **Vertraulich**und **Erforderlich** in der Liste selbst oder im Fenster **Eigenschaften** ein. In der folgenden Tabelle werden diese Eigenschaften beschrieben.  
  
    |Eigenschaft|BESCHREIBUNG|  
    |--------------|-----------------|  
    |Name|Der Name des Parameters.|  
    |Datentyp|Der Datentyp des Parameters.|  
    |Standardwert|Der Standardwert für den zur Entwurfszeit zugewiesenen Parameter. Dieser wird auch als Entwurfsstandard bezeichnet.|  
    |Sensibel|Vertrauliche Parameterwerte werden im Katalog verschlüsselt und in Transact-SQL oder SQL Server Management Studio als NULL-Wert angezeigt.|  
    |Erforderlich|Dazu muss ein anderer als der Entwurfsstandardwert angegeben werden, bevor das Paket ausgeführt werden kann.|  
    |BESCHREIBUNG|Die Beschreibung des Parameters für bessere Verwaltbarkeit. Legen Sie im Visual Studio-Eigenschaftenfenster von [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]die Parameterbeschreibung fest, wenn der Parameter im entsprechenden Parameterfenster ausgewählt wurde.|  
  
    > [!NOTE]  
    >  Wenn Sie im Katalog ein Projekt bereitstellen, werden dem Projekt einige weitere Eigenschaften zugeordnet. Um alle Eigenschaften für alle Parameter im Katalog anzuzeigen, verwenden Sie die Sicht [catalog.object_parameters &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-views/catalog-object-parameters-ssisdb-database).  
  
4.  Speichern Sie das Projekt, um Änderungen an Parametern zu speichern. Parameterwerte werden in der Projektdatei gespeichert.  
  
    > [!WARNING]  
    >  Nehmen Sie Bearbeitungen direkt in der Liste vor, oder verwenden Sie das Fenster **Eigenschaften**, um die Werte von Parametereigenschaften zu ändern. Sie können mit der Symbolleistenschaltfläche **Löschen (X)** einen Parameter löschen. Über die letzte Symbolleistenschaltfläche können Sie einen Wert für einen Parameter angeben, der nur verwendet wird, wenn Sie das Paket in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]ausführen.  
  
    > [!NOTE]  
    >  Wenn Sie die Paketdatei erneut öffnen, ohne das Projekt in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] zu öffnen, ist die Registerkarte **Parameter** leer und deaktiviert.  
  
### <a name="to-create-project-parameters"></a>So erstellen Sie das Projektparameter  
  
1.  Öffnen Sie das Projekt in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].  
  
2.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf **Project.params**, und klicken Sie auf **Öffnen**. Oder doppelklicken auf **Project.params**, um das Projekt zu öffnen.  
  
     ![Fenster „Projektparameter“](media/denali-project-parameters.gif "Fenster „Projektparameter“")  
  
3.  Klicken Sie auf die Schaltfläche **Parameter hinzufügen** auf der Symbolleiste.  
  
     ![Symbolleisten Schaltfläche](media/denali-parameter-add.gif "Symbolleistenschaltfläche „Hinzufügen“")  
  
4.  Geben Sie Werte für die Eigenschaften **Name**, **Datentyp**, **Wert**, **Vertraulich**und **Erforderlich** ein.  
  
    |Eigenschaft|BESCHREIBUNG|  
    |--------------|-----------------|  
    |Name|Der Name des Parameters.|  
    |Datentyp|Der Datentyp des Parameters.|  
    |Standardwert|Der Standardwert für den zur Entwurfszeit zugewiesenen Parameter. Dieser wird auch als Entwurfsstandard bezeichnet.|  
    |Sensibel|Vertrauliche Parameterwerte werden im Katalog verschlüsselt und in Transact-SQL oder SQL Server Management Studio als NULL-Wert angezeigt.|  
    |Erforderlich|Dazu muss ein anderer als der Entwurfsstandardwert angegeben werden, bevor das Paket ausgeführt werden kann.|  
    |BESCHREIBUNG|Die Beschreibung des Parameters für bessere Verwaltbarkeit. Legen Sie im Visual Studio-Eigenschaftenfenster von [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]die Parameterbeschreibung fest, wenn der Parameter im entsprechenden Parameterfenster ausgewählt wurde.|  
  
5.  Speichern Sie das Projekt, um Änderungen an Parametern zu speichern. Parameterwerte werden in Konfigurationen in der Projektdatei gespeichert. Speichern Sie die Projektdatei, um alle Änderungen in den Parameterwerten in einem Commit an den Datenträger zu übergeben.  
  
    > [!WARNING]  
    >  Nehmen Sie Bearbeitungen direkt in der Liste vor, oder verwenden Sie das Fenster **Eigenschaften**, um die Werte von Parametereigenschaften zu ändern. Sie können mit der Symbolleistenschaltfläche **Löschen (X)** einen Parameter löschen. Über die letzte Symbolleistenschaltfläche können Sie das Dialogfeld **Parameterwerte verwalten** öffnen, um einen Wert für einen Parameter anzugeben, der nur verwendet wird, wenn Sie das Paket in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Integration Services &#40;SSIS-&#41; Parameter](integration-services-ssis-package-and-project-parameters.md)  
  
  
