---
title: Editor für den Task ' SQL ausführen ' (Seite Parameter Zuordnung) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executesqltask.parametermapping.f1
helpviewer_keywords:
- Execute SQL Task Editor
ms.assetid: 8ebe020a-7921-46b2-8823-398748f379b2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cfbb4468cb69947dfa54fb519b7698286393d578
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87616123"
---
# <a name="execute-sql-task-editor-parameter-mapping-page"></a>Editor für den Task 'SQL ausführen' (Seite Parameterzuordnung)
  Mithilfe der Seite **Parameterzuordnung** des Dialogfelds **Editor für den Task 'SQL ausführen'** können Sie Parametern in der SQL-Anweisung Variablen zuordnen.  
  
 Weitere Informationen zu diesem Task finden Sie unter [SQL ausführen (Task)](control-flow/execute-sql-task.md) und [Parameter und Rückgabecodes im Task „SQL ausführen“](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md).  
  
## <a name="options"></a>Tastatur  
 **Variablenname**  
 Nachdem Sie auf **Hinzufügen** geklickt und damit eine neue Parameterzuordnung hinzugefügt haben, wählen Sie in der Liste eine Systemvariable oder eine benutzerdefinierte Variable aus, oder klicken Sie auf \<**New variable...**>, um mithilfe des Dialogfelds **Variable hinzufügen** eine neue Variable hinzuzufügen.  
  
 **Verwandte Themen:** [Integration Services-Variablen &#40;SSIS&#41;](integration-services-ssis-variables.md)  
  
 **Richtung**  
 Wählen Sie die Richtung des Parameters aus. Ordnen Sie jede Variable einem Eingabeparameter, einem Ausgabeparameter oder einem Rückgabecode zu.  
  
 **Datentyp**  
 Wählen Sie den Datentyp des Parameters aus. Die Liste der verfügbaren Datentypen hängt von dem Anbieter ab, den Sie in dem vom Task verwendeten Verbindungs-Manager ausgewählt haben.  
  
 **Parametername**  
 Geben Sie einen Parameternamen an.  
  
 Je nachdem, welchen Verbindungs-Manager-Typ der Task verwendet, müssen Sie Zahlen oder Parameternamen verwenden. Einige Verbindungs-Manager-Typen erfordern, dass Parameternamen mit dem \@-Zeichen beginnen oder bestimmte Namen (z. B. \@Param1) bzw. Spaltennamen als Parameternamen verwendet werden.  
  
 **Verwandte Themen:** [Parameter und Rückgabecodes im Task „SQL ausführen“](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)  
  
 **Parametergröße**  
 Geben Sie die Größe von Parametern mit variabler Länge an, z. B. Zeichenfolgen und binäre Felder.  
  
 Durch diese Einstellung wird sichergestellt, dass der Anbieter genügend Speicherplatz für Parameterwerte variabler Länge zuordnet.  
  
 **Add (Hinzufügen)**  
 Klicken Sie auf diese Option, um eine Parameterzuordnung hinzuzufügen.  
  
 **Remove**  
 Wählen Sie in der Liste eine Parameterzuordnung aus, und klicken Sie anschließend auf **Entfernen**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor für den Task ' SQL ausführen ' &#40;Seite Allgemein&#41;](general-page-of-integration-services-designers-options.md)   
 [Editor für den Task "SQL ausführen" &#40;resultsetseite&#41;](../../2014/integration-services/execute-sql-task-editor-result-set-page.md)   
 [Transact-SQL-Referenz &#40;Datenbank-Engine&#41;](/sql/t-sql/language-reference)  
  
  
