---
title: Verwalten von Rollen mit SSMS (SSAS-tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 652faac0-1cfc-438b-8119-2f4b090a2381
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4ee34d5e75d5d4ce3679d46d29af3215852d2bbe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696165"
---
# <a name="manage-roles-by-using-ssms-ssas-tabular"></a>Verwalten von Rollen mit SSMS (SSAS – tabellarisch)
  Sie können Rollen für ein bereitgestelltes tabellarisches Modell mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]erstellen, bearbeiten und verwalten.  
  
 Aufgaben in diesem Thema:  
  
-   [So erstellen Sie eine neue Rolle](#bkmk_new_role)  
  
-   [So kopieren Sie eine Rolle](#bkmk_copy_role)  
  
-   [So bearbeiten Sie eine Rolle](#bkmk_edit_role)  
  
-   [So löschen Sie eine Rolle](#bkmk_deletet_role)  
  
> [!CAUTION]  
>  Wenn ein tabellarisches Modellprojekt, dessen Rollen mithilfe des Rollen-Managers in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] definiert wurden, erneut bereitgestellt wird, dann werden die in einem bereitgestellten tabellarischen Modell definierten Rollen überschrieben.  
  
> [!CAUTION]  
>  Wenn Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] verwenden, um eine Arbeitsbereichsdatenbank für tabellarische Modelle zu verwalten, während das Modellprojekt in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] geöffnet ist, kann die Datei Model.bim beschädigt werden. Wenn Sie Rollen für eine Arbeitsbereichsdatenbank für tabellarische Modelle erstellen und verwalten, verwenden Sie den Rollen-Manager in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].  
  
###  <a name="to-create-a-new-role"></a><a name="bkmk_new_role"></a>So erstellen Sie eine neue Rolle  
  
1.  Erweitern Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]die tabellarische Modelldatenbank, für die Sie eine neue Rolle erstellen möchten, klicken Sie mit der rechten Maustaste auf **Rollen**, und klicken Sie dann auf **Neue Rolle**.  
  
2.  Klicken Sie im Dialogfeld **Rolle erstellen** im Fenster "Seite auswählen" auf **Allgemein**.  
  
3.  Geben Sie im Fenster für allgemeine Einstellungen im Feld **Name** einen Namen für die Rolle ein.  
  
     Der Name der Standardrolle wird für jede neue Rolle automatisch inkrementell erhöht. Es wird empfohlen, einen Namen einzugeben, durch den der Elementtyp eindeutig identifiziert wird, beispielsweise "Finance Managers" oder "Human Resources Specialists".  
  
4.  Aktivieren Sie in **Legen Sie die Datenbankberechtigung für diese Rolle fest**eine der folgenden Berechtigungsoptionen:  
  
    |Berechtigung|BESCHREIBUNG|  
    |----------------|-----------------|  
    |**Vollzugriff (Administrator)**|Mitglieder können Änderungen am Modellschema vornehmen und alle Daten anzeigen.|  
    |**Datenbank verarbeiten**|Mitglieder können die Vorgänge Verarbeiten und Alles verarbeiten ausführen. Sie können weder das Modellschema ändern noch Daten anzeigen.|  
    |**Lesen**|Mitglieder dürfen Daten (basierend auf Zeilenfiltern) anzeigen, doch sie können keine Änderungen am Modellschema vornehmen.|  
  
5.  Klicken Sie im Dialogfeld **Rolle erstellen** im Fenster "Seite auswählen" auf **Mitgliedschaft**.  
  
6.  Klicken Sie im Mitgliedschaftseinstellungen-Fenster auf **Hinzufügen**, und fügen Sie dann im Dialogfeld **Benutzer oder Gruppen auswählen** die Windows-Benutzer oder die Gruppen hinzu, die Sie als Elemente hinzufügen möchten.  
  
7.  Wenn die Rolle, die Sie erstellen, Leseberechtigungen aufweist, können Sie Zeilenfilter für jede beliebige Tabelle hinzufügen, in der eine DAX-Formel verwendet wird. Um Zeilen Filter hinzuzufügen, klicken Sie im Dialogfeld **Rollen Eigenschaften- \<rolename> ** unter **Seite auswählen**auf **Zeilen Filter**.  
  
8.  Wählen Sie im Fenster Zeilen Filter eine Tabelle aus, klicken Sie dann auf das Feld **DAX-Filter** , und geben Sie dann im Feld **DAX- \<tablename> Filter** eine DAX-Formel ein.  
  
    > [!NOTE]  
    >  Das DAX-Filter- \<tablename> Feld enthält keinen AutoComplete-Abfrage-Editor oder Funktion zum Einfügen von Funktionen. Um beim Schreiben einer DAX-Formel die Funktion zum AutoVervollständigen verwenden zu können, müssen Sie in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]einen DAX-Formel-Editor verwenden.  
  
9. Klicken Sie auf **OK** , um die Rolle zu speichern.  
  
###  <a name="to-copy-a-role"></a><a name="bkmk_copy_role"></a> So kopieren Sie eine Rolle  
  
1.  Erweitern Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]die tabellarische Modelldatenbank, die die Rolle enthält, die Sie kopieren möchten, und erweitern Sie dann **Rollen**. Klicken Sie mit der rechten Maustaste auf die Rolle, und klicken Sie dann auf **Duplizieren**.  
  
###  <a name="to-edit-a-role"></a><a name="bkmk_edit_role"></a>So bearbeiten Sie eine Rolle  
  
-   Erweitern Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]die tabellarische Modelldatenbank, die die Rolle enthält, die Sie bearbeiten möchten, und erweitern Sie dann **Rollen**. Klicken Sie mit der rechten Maustaste auf die Rolle, und klicken Sie dann auf **Eigenschaften**.  
  
     Im Dialogfeld **Rollen Eigenschaften** \<rolename> können Sie Berechtigungen ändern, Mitglieder hinzufügen oder entfernen und Zeilen Filter hinzufügen/bearbeiten.  
  
###  <a name="to-delete-a-role"></a><a name="bkmk_deletet_role"></a>So löschen Sie eine Rolle  
  
-   Erweitern Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]die tabellarische Modelldatenbank, die die Rolle enthält, die Sie löschen möchten, und erweitern Sie dann **Rollen**. Klicken Sie mit der rechten Maustaste auf die Rolle, und klicken Sie dann auf **Löschen**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Rollen &#40;SSAS – tabellarisch&#41;](roles-ssas-tabular.md)  
  
  
