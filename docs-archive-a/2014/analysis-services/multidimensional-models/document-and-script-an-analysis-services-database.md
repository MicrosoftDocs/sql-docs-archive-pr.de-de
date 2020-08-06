---
title: Dokumentieren und Erstellen eines Skripts für eine Analysis Services Datenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- XML for Analysis, scripts
- XMLA, scripts
- scripts [Analysis Services], databases
- documenting databases
- databases [Analysis Services], documenting
- databases [Analysis Services], scripts
ms.assetid: 125044e2-8d36-4733-8743-8bb68ff9aa4e
author: minewiskan
ms.author: owend
ms.openlocfilehash: cfe008b0d6903d7d012eb57d41d6e50240202ec8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621693"
---
# <a name="document-and-script-an-analysis-services-database"></a>Dokumentieren und Skripterstellung einer Analysis Services-Datenbank
  Nachdem eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank bereitgestellt ist, können Sie mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] die Metadaten der Datenbank oder eines in der Datenbank enthaltenen Objekts als XML for Analysis-Skript (XMLA) ausgeben. Sie können dieses Skript in ein neues **XMLA-Abfrage-Editor** -Fenster, in eine Datei oder die Zwischenablage exportieren. Weitere Informationen zu XMLA finden Sie unter [Analysis Services Skriptsprache &#40;ASSL&#41; Referenz](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla).  
  
 Das generierte XMLA-Skript verwendet Elemente der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Skriptsprache (ASSL), um im Skript enthaltene Objekte zu definieren. Wenn Sie ein CREATE-Skript generiert haben, enthält das entstandene XMLA-Skript einen XMLA **Create** -Befehl und ASSL-Elemente, die verwendet werden können, um die gesamte [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbankstruktur auf einer Instanz zu erstellen. Wenn Sie ein ALTER-Skript generiert haben, enthält das resultierende XMLA-Skript den XMLA-Befehl **Alter** und ASSL-Elemente, mit denen die Struktur einer vorhandenen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank wieder in dem Zustand wiederhergestellt werden kann, den sie zum Zeitpunkt der Skripterstellung innehatte.  
  
 Sie können das aus einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank generierte XMLA-Skript auf viele verschiedene Weisen verwenden, so z. B. wie folgt:  
  
-   Verwalten eines Sicherungsskripts, mit dem Sie alle Datenbankobjekte und -berechtigungen neu erstellen können.  
  
-   Erstellen oder Aktualisieren von Datenbankentwicklungscode.  
  
-   Erstellen eines Testes oder einer Entwicklungsumgebung aus einem vorhandenen Schema heraus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ändern oder Löschen einer Analysis Services Datenbank](modify-or-delete-an-analysis-services-database.md)   
 [Alter Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla)   
 [Create-Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla)  
  
  
