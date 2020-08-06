---
title: Anzeigen oder Ändern von Modellierungsflags (Data Mining) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d1169735-fb18-417b-b8d6-9a161e444020
author: minewiskan
ms.author: owend
ms.openlocfilehash: bf0edd827321685a2d6a9041759328a7ac6e7cbd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717023"
---
# <a name="view-or-change-modeling-flags-data-mining"></a>Anzeigen oder Ändern von Modellierungsflags (Data Mining)
  Modellierungsflags sind Eigenschaften, die Sie für eine Miningstrukturspalte oder für Miningmodellspalten festlegen, um zu steuern, wie der Algorithmus die Daten während der Analyse verarbeitet.  
  
 Im Data Mining-Designer können Sie die Modellierungsflags, die einer Miningstruktur oder Miningspalte zugeordnet sind, betrachten und ändern, indem Sie die Eigenschaften der Struktur oder des Modells anzeigen. Sie können Modellierungsflags auch mit DMX, AMO oder XMLA festlegen.  
  
 Diese Prozedur beschreibt, wie die Modellierungsflags im Designer geändert werden.  
  
### <a name="view-or-change-the-modeling-flag-for-a-structure-column-or-model-column"></a>Anzeigen oder Ändern des Modellierungsflags für eine Strukturspalte oder eine Modellspalte  
  
1.  Öffnen Sie in SQL Server Design Studio den Projektmappen-Explorer, und doppelklicken Sie dann auf die Miningstruktur.  
  
2.  Zum Festlegen des NOT NULL-Modellierungsflags klicken Sie auf die Registerkarte **Mining Struktur** . Um die Regressor-oder MODEL_EXISTENCE_ONLY-Flags festzulegen, klicken Sie auf die Registerkarte **Mining Modell** .  
  
3.  Klicken Sie mit der rechten Maustaste auf die Spalte, die Sie anzeigen oder ändern möchten, und wählen Sie **Eigenschaften**aus.  
  
4.  Um ein neues Modellierungsflag hinzuzufügen, klicken Sie auf das Textfeld neben der Eigenschaft **ModelingFlags** , und aktivieren Sie das bzw. die Kontrollkästchen für die Modellierungsflags, die Sie verwenden möchten.  
  
     Modellierungsflags werden nur angezeigt, wenn sie für den Datentyp der Spalte geeignet sind.  
  
    > [!NOTE]  
    >  Nachdem ein Modellierungsflag geändert wurde, muss das Modell erneut verarbeitet werden.  
  
### <a name="get-the-modeling-flags-used-in-the-model"></a>Abrufen der im Modell verwendeten Modellierungsflags  
  
-   Öffnen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ein DMX-Abfragefenster, und geben Sie eine Anweisung ähnlich der folgenden ein:  
  
    ```  
    SELECT COLUMN_NAME, CONTENT_TYPE, MODELING_FLAG  
    FROM $system.DMSCHEMA_MINING_COLUMNS  
    WHERE MODEL_NAME = 'Forecasting'  
  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Mining Modell Tasks und Anleitungen](mining-model-tasks-and-how-tos.md)   
 [Modellierungsflags &#40;Data Mining&#41;](modeling-flags-data-mining.md)  
  
  
