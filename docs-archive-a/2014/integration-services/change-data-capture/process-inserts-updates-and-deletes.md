---
title: Verarbeiten von Einfügungen, Updates und Löschungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],processing data
ms.assetid: 13a84d21-2623-4efe-b442-4125a7a2d690
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 67f016aaf4f7f83c0fa506966c4e78f5b8fadef6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608783"
---
# <a name="process-inserts-updates-and-deletes"></a>Verarbeiten von Einfügungen, Updates und Löschungen
  Im Datenfluss eines Integration Services-Pakets, das ein inkrementelles Laden von Änderungsdaten ausführt, werden mit dem zweiten Task Einfügungen, Updates und Löschungen voneinander getrennt. Dann können Sie entsprechende Befehle verwenden, um sie für das Ziel zu übernehmen.  
  
> [!NOTE]  
>  Der erste Task beim Entwerfen des Datenflusses eines Pakets, das ein inkrementelles Laden von Änderungsdaten ausführt, ist die Konfiguration der Quellkomponente, die die Abfrage ausführt, bei der die Änderungsdaten abgerufen werden. Weitere Informationen zu dieser Komponente finden Sie unter [Abrufen und Verstehen der Änderungsdaten](retrieve-and-understand-the-change-data.md). Eine Beschreibung des Gesamtprozesses zur Erstellung eines Pakets, das ein inkrementelles Laden von Änderungsdaten ausführt, finden Sie unter [Change Data Capture &#40;SSIS&#41;](change-data-capture-ssis.md).  
  
## <a name="associating-friendly-values-to-separate-inserts-updates-and-deletes"></a>Zuordnen von benutzerfreundlichen Werten zur Trennung von Einfügungen, Updates und Löschungen  
 In der Beispielabfrage, bei der Änderungsdaten abgerufen werden, gibt die **cdc.fn_cdc_get_net_changes_<capture_instance>** -Funktion nur die Metadatenspalte mit der Bezeichnung **__$operation** zurück. Diese Metadatenspalte enthält einen Ordinalwert, der angibt, welcher Vorgang die Änderung verursacht hat.  
  
> [!NOTE]  
>  Weitere Informationen zu der Abfrage, die die **cdc.fn_cdc_get_net_changes_<capture_instance>** -Funktion verwendet, finden Sie unter [Erstellen der Funktion zum Abrufen der Änderungsdaten](create-the-function-to-retrieve-the-change-data.md).  
  
 Das Abgleichen eines Ordinalwerts mit seinem entsprechenden Vorgang ist nicht so einfach wie die Verwendung eines mnemonischen Codes des Vorgangs. Zum Beispiel kann 'D' leicht einen Löschvorgang und 'I' einen Einfügevorgang darstellen. Die Beispielabfrage, die im Thema [Erstellen der Funktion zum Abrufen der Änderungsdaten](create-the-function-to-retrieve-the-change-data.md)erstellt wurde, nimmt diese Konvertierung von einem Ordinalwert in einen benutzerfreundlichen Zeichenfolgenwert vor, der in einer neuen Spalte zurückgegeben wird. Das folgende Codesegment zeigt diese Konvertierung:  
  
```  
select   
    ...  
    case __$operation  
        when 1 then 'D'  
        when 2 then 'I'  
        when 4 then 'U'  
        else null  
     end as CDC_OPERATION  
```  
  
## <a name="configuring-a-conditional-split-transformation-to-direct-inserts-updates-and-deletes"></a>Konfigurieren einer Transformation für bedingtes Teilen zur Weiterleitung von Einfügungen, Updates und Löschungen  
 Die Transformation für bedingtes Teilen ist ideal zur Weiterleitung von Zeilen mit Änderungsdaten an eine von drei Ausgaben. Die Transformation überprüft den Wert der **CDC_OPERATION** -Spalte in jeder Zeile und bestimmt, ob diese Änderung eine Einfügung, Löschung bzw. ein Update war.  
  
> [!NOTE]  
>  Die Spalte CDC_OPERATION enthält einen benutzerfreundlichen vom numerischen Wert in der **__$operation** -Spalte abgeleiteten Zeichenfolgenwert.  
  
#### <a name="to-split-inserts-updates-and-deletes-for-processing-by-using-a-conditional-split-transformation"></a>So teilen Sie Einfügungen, Updates und Löschungen zur Verarbeitung durch Verwendung einer Transformation für bedingtes Teilen  
  
1.  Fügen Sie auf der Registerkarte **Datenfluss** eine Transformation für bedingtes Teilen hinzu.  
  
2.  Verbinden Sie die Ausgabe der OLE DB-Quelle mit der Transformation für bedingtes Teilen.  
  
3.  Geben Sie im **Transformations-Editor für bedingtes Teilen**im unteren Bereich des Editors die folgenden drei Zeilen ein, um die drei Ausgaben zu bestimmen  
  
    1.  Geben Sie eine Zeile mit der Bedingung `CDC_OPERATION == "I"` ein, um eingefügte Zeilen an die Ausgabe für Einfügungen weiterzuleiten.  
  
    2.  Geben Sie eine Zeile mit der Bedingung `CDC_OPERATION == "U"` ein, um aktualisierte Zeilen an die Ausgabe für Updates weiterzuleiten.  
  
    3.  Geben Sie eine Zeile mit der Bedingung `CDC_OPERATION == "D"` ein, um gelöschte Zeilen an die Ausgabe für Löschungen weiterzuleiten.  
  
## <a name="next-step"></a>Nächster Schritt  
 Nachdem Sie die Zeilen zur Verarbeitung geteilt haben, besteht der nächste Schritt darin, die Änderungen auf das Ziel anzuwenden.  
  
 **Nächstes Thema:** [Anwenden der Änderungen auf das Ziel](apply-the-changes-to-the-destination.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Conditional Split Transformation](../data-flow/transformations/conditional-split-transformation.md)   
 [Teilen eines Datasets mithilfe der Transformation für bedingtes Teilen](../data-flow/transformations/split-a-dataset-by-using-the-conditional-split-transformation.md)  
  
  
