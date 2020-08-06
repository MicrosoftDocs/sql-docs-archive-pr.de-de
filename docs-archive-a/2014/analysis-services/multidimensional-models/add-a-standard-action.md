---
title: Hinzufügen einer Standard Aktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ccb2928a-f75d-4acb-8ff8-fa80bb0935b2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 27e11c4b52a8283ba7694b8bd337a5ee9c82eaca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87616755"
---
# <a name="add-a-standard-action"></a>Hinzufügen einer Standardaktion
  Mithilfe der Aktionsansicht im Cube-Designer fügen Sie einer Datenbank eine Aktion hinzu. Auf diese Sicht kann von [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]zugegriffen werden. Nachdem Sie eine Aktion erstellt haben, wird sie für Benutzer verfügbar, sobald der betreffende Cube erneut verarbeitet wurde. Weitere Informationen finden Sie unter [Processing Analysis Services Objects](processing-analysis-services-objects.md).  
  
### <a name="to-create-an-action"></a>So erstellen Sie eine Aktion  
  
1.  Öffnen Sie den Cube, für den Sie eine Aktion erstellen möchten, und klicken Sie dann auf die Registerkarte **Aktionen** .  
  
2.  Klicken Sie auf der Symbolleiste auf das Symbol **Neue Aktion** , und gehen Sie dann im Ausdrucksbereich wie folgt vor:  
  
    -   Geben Sie in **Name**einen Namen für die Aktion ein.  
  
    -   Wählen Sie in der Dropdownliste **Zieltyp** den Typ des Objekts aus, an das Sie die Aktion anfügen möchten. Durch das in **Zieltyp** ausgewählte Objekt wird bestimmt, welche Objekte verfügbar sind und welche Auswahl unter **Zielobjekt**getroffen werden kann. In der folgenden Tabelle sind die für jeden Zieltyp zulässigen Optionen für **Zielobjekt** aufgeführt.  
  
        |Ausgewählter Zieltyp|Auswahl unter "Zielobjekt"|  
        |---------------------------------------------|---------------------------------------------------|  
        |Attributelemente|Die einzige gültige Auswahl ist eine einzelne Attributhierarchie. Der Zieltyp der Aktion entspricht allen Elementen des Attributs an jeder beliebigen Stelle (d. h., die Aktion gilt auch für benutzerdefinierte Hierarchien).|  
        |Zellen|Es können ausschließlich Zellen ausgewählt werden. Wenn Sie **Zellen** als Zieltyp auswählen, können Sie einen Ausdruck in **Bedingung** eingeben, um die Zellen einzuschränken, denen die Aktion zugeordnet ist.|  
        |Cube|Die einzige verfügbare Auswahl ist CURRENTCUBE. Die Aktion ist dem aktuellen Cube zugeordnet.|  
        |Dimensionselemente|Wählen Sie eine einzelne Dimension aus. Die Aktion wird allen Elementen der Dimension zugeordnet.|  
        |Hierarchy|Wählen Sie eine einzelne Hierarchie aus. Die Aktion wird nur dem Hierarchieobjekt zugeordnet. Attributhierarchien werden nur in der Liste angezeigt, wenn ihre **AttributeHierarchyEnabled** -Eigenschaft und **AttributeHierarchyVisible** -Eigenschaft auf **True**festgelegt sind.|  
        |Hierarchieelemente|Wählen Sie eine einzelne Hierarchie aus. Die Aktion wird allen Elementen der ausgewählten Hierarchie zugeordnet. Attributhierarchien werden nur in der Liste angezeigt, wenn ihre **AttributeHierarchyEnabled** -Eigenschaft und **AttributeHierarchyVisible** -Eigenschaft auf **True**festgelegt sind.|  
        |Ebene|Wählen Sie eine einzelne Ebene aus. Die Aktion wird nur dem Ebenenobjekt zugeordnet.|  
        |Ebenenelemente|Wählen Sie eine einzelne Ebene aus. Die Aktion wird allen Elementen der ausgewählten Ebene zugeordnet.|  
  
    -   Klicken Sie in **Zielobjekt**auf den Pfeil rechts neben dem Textfeld, und klicken Sie in der daraufhin geöffneten Strukturansicht, auf das Objekt, an das die Aktion angefügt werden soll, und dann auf **OK**.  
  
    -   (Optional.) Erstellen Sie unter **Bedingung**einen MDX-Ausdruck, um das Ziel der Aktion einzuschränken. Sie können entweder den Ausdruck manuell eingeben oder Elemente aus den Registerkarten **Metadaten** und **Funktionen** ziehen.  
  
    -   Wählen Sie in der Dropdownliste **Typ** den Typ der Aktion aus, den Sie erstellen möchten. In der folgenden Tabelle sind die verfügbaren Aktionstypen aufgelistet.  
  
        |type|BESCHREIBUNG|  
        |----------|-----------------|  
        |Dataset|Ruft ein Dataset ab.|  
        |Proprietär|Führt einen Vorgang über eine Schnittstelle aus, die nicht in dieser Tabelle aufgelistet ist.|  
        |Rowset|Ruft ein Rowset ab.|  
        |Anweisung|Gibt einen OLE DB-Befehl zurück.|  
        |URL|Zeigt eine Webseite in einem Internetbrowser an.|  
  
    -   Erstellen Sie in **Aktionsausdruck**einen Ausdruck, durch den die Aktion definiert wird. Der Ausdruck muss zu einer Zeichenfolge ausgewertet werden. Sie können entweder den Ausdruck manuell eingeben oder Elemente aus den Registerkarten **Metadaten** und **Funktionen** ziehen.  
  
3.  (Optional.) Erweitern Sie **Weitere Eigenschaften**, und führen Sie einen der folgenden Schritte aus:  
  
    -   Geben Sie mithilfe der Dropdownliste **Aufruf** an, wie die Aktion aufgerufen wird. In der folgenden Tabelle werden die verfügbaren Optionen zum Aufrufen einer Aktion beschrieben.  
  
        |Option|BESCHREIBUNG|  
        |------------|-----------------|  
        |Interactive|Die Aktion wird durch eine Benutzerinteraktion ausgelöst.|  
        |Batch|Die Aktion wird als Batchvorgang ausgeführt.|  
        |Beim Öffnen|Die Aktion wird ausgeführt, wenn der Cube von einem Benutzer geöffnet wird.|  
  
    -   Geben Sie in **Anwendung**den Namen der Anwendung ein, die der Aktion zugeordnet ist. Wenn Sie z. B. eine Aktion erstellen, durch die ein Benutzer zu einer bestimmten Website geleitet wird, sollte die der Aktion zugeordnete Anwendung Microsoft Internet Explorer oder ein anderer Webbrowser sein.  
  
        > [!NOTE]  
        >   Proprietäre Aktionen werden erst an den Server zurückgegeben, wenn das Schemarowset von der Clientanwendung explizit so beschränkt wird, dass nur Aktionen zurückgegeben werden, die mit dem in **Anwendung**angegebenen Namen übereinstimmen.  
  
    -   Wenn Sie unter **Aktions Inhalt**den URL-Typ verwenden, schließen Sie die Internet Adresse in Anführungszeichen ein, z. b http://www.adventure-works.com . "".  
  
    -   Geben Sie in **Beschreibung**eine Beschreibung für die Aktion ein.  
  
    -   Geben Sie unter **Beschriftung**eine Beschriftung oder einen MDX-Ausdruck ein, der zu einer Beschriftung ausgewertet wird. Diese Beschriftung wird für Endbenutzer angezeigt, wenn die Aktion initiiert wird. Wenn Sie keine Beschriftung angeben, wird stattdessen der Name der Aktion verwendet.  
  
    -   Geben Sie mithilfe der Dropdownliste **Beschriftung ist MDX** an, ob die Beschriftung MDX entspricht. Über dieses Feld wird der Server angewiesen, den Inhalt von **Beschriftung** als MDX-Ausdruck auszuwerten.  
  
  
