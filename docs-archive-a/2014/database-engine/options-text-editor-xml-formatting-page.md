---
title: Optionen (Text-Editor-XML-Formatierungs Seite) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 97373178-d288-4127-af37-d9f5fe1b8607
author: rothja
ms.author: jroth
ms.openlocfilehash: dce36142fe9974c0167fca700c509642e05d89b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701540"
---
# <a name="options-text-editor---xml---formatting-page"></a>Optionen (Text-Editor – XML – Seite „Formatierung“)

In diesem Dialogfeld können Sie die Formatierungseinstellungen für den XML-Editor festlegen. Sie können über das Menü **Extras** auf das Dialogfeld **Optionen** zugreifen.  
  
> [!NOTE]  
> Zum Anzeigen dieser Einstellungen wählen Sie zunächst den Ordner **Text-Editor** und anschließend den Ordner **XML** aus. Wählen Sie dann im Dialogfeld **Optionen** die Option **Formatierung** aus.  
  
## <a name="attributes"></a>Attribute  
 **Manuelle Attributformatierung beibehalten**  
 Nimmt keine Neuformatierung von Attributen vor. Dies ist die Standardeinstellung.  
  
> [!NOTE]  
>  Wenn die Attribute auf mehrere Zeilen verteilt sind, richtet der Editor jede Attributzeile am Einzug des jeweils übergeordneten Elements aus.  
  
 **Attribute jeweils in einer eigenen Zeile ausrichten**  
 Richtet das zweite und alle nachfolgenden Attribute vertikal am Einzug des ersten Attributs aus. Der folgende XML-Text verkörpert ein Beispiel für die Ausrichtung der Attribute.  
  
```  
<item id = "123-A"  
      name = "hammer"  
      price = "9.95"  
</item>  
```  
  
## <a name="auto-reformat"></a>Automatisch neu formatieren  
 **Bei Einfügen aus der Zwischenablage**  
 Formatiert den aus der Zwischenablage eingefügten XML-Text neu.  
  
 **Bei Komplettierung des Endtags**  
 Formatiert das Element nach Abschluss des Endtags neu.  
  
## <a name="mixed-content"></a>Gemischter Inhalt  
 **Standardformat: gemischter Inhalt**  
 Versucht, gemischten Inhalt neu zu formatieren. Der Inhalt von `xml:space="preserve"`-Bereichen wird dabei jedoch nicht berücksichtigt. Dies ist die Standardeinstellung.  
  
 Wenn ein Element sowohl Text als auch Markup enthält, wird sein Inhalt wie gemischter Inhalt behandelt. Das folgende Beispiel zeigt ein Element mit gemischtem Inhalt.  
  
```  
<dir>c:\data\AlphaProject\  
  <file readOnly="false">test1.txt</file>  
  <file readOnly="false">test2.txt</file>  
```  
  
 \</dir>  
  
## <a name="see-also"></a>Weitere Informationen  
 [XML-Editor &#40;SQL Server Management Studio&#41;](../ssms/sql-server-management-studio-ssms.md)  
