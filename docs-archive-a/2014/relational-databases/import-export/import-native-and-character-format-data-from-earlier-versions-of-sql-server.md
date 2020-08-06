---
title: Importieren von Daten aus früheren SQL Server-Versionen im nativen Format oder im Zeichenformat | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- earlier versions [SQL Server], import and export data formats
- -V switch
- data formats [SQL Server], earlier versions
- previous versions [SQL Server], import and export data formats
ms.assetid: e644696f-9017-428e-a5b3-d445d1c630b3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 274c984d6ecec8af8f5bea27496450a45fc2f1df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87620376"
---
# <a name="import-native-and-character-format-data-from-earlier-versions-of-sql-server"></a>Importieren von Daten aus früheren SQL Server-Versionen im systemeigenen Format oder im Zeichenformat
  Sie können [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]bcp **in** verwenden, um Daten im nativen Format oder im Zeichenformat mithilfe des Schalters [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]-V [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]aus [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] , **oder** zu importieren. Der Schalter **-V** veranlasst [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , Datentypen aus der angegebenen früheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu verwenden. Zudem entspricht das Datendateiformat dem Format dieser früheren Version.  
  
 Um eine frühere Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für eine Datendatei anzugeben, verwenden Sie den Schalter **-V** mit einem der folgenden Qualifizierer:  
  
|SQL Server-Version|Qualifizierer|  
|------------------------|---------------|  
|[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]|**-V80**|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|**-V90**|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|**-V100**|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|**-V 110**|  
  
## <a name="interpretation-of-data-types"></a>Interpretation von Datentypen  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höhere Versionen bieten Unterstützung für einige neue Typen. Beim Importieren eines neuen Datentyps aus einer früheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , muss der Dateityp in einem Format gespeichert sein, das von den älteren **bcp** -Clients gelesen werden kann. In der folgenden Tabelle finden Sie eine Übersicht, wie die neuen Datentypen konvertiert werden, damit sie mit den früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]kompatibel sind.  
  
|Neue Datentypen in SQL Server 2005|Kompatible Datentypen in Version 6*x*|Kompatible Datentypen in Version 70|Kompatible Datentypen in Version 80|  
|---------------------------------------|-------------------------------------------|-----------------------------------------|-----------------------------------------|  
|`bigint`|`decimal`|`decimal`|*|  
|`sql_variant`|`text`|`nvarchar(4000)`|*|  
|`varchar(max)`|`text`|`text`|`text`|  
|`nvarchar(max)`|`ntext`|`ntext`|`ntext`|  
|`varbinary(max)`|`image`|`image`|`image`|  
|XML|`ntext`|`ntext`|`ntext`|  
|UDT<sup>1</sup>|`image`|`image`|`image`|  
  
 \*Dieser Typ wird nativ unterstützt.  
  
 <sup>1</sup> UDT gibt einen benutzerdefinierten Typ an.  
  
## <a name="exporting-using--v-80"></a>Exportieren mit -V 80  
 Wenn Sie einen Massen Export von Daten mithilfe des **-V80-** Schalters durch `nvarchar(max)` laufen, werden,,, `varchar(max)` `varbinary(max)` XML und UDT-Daten im einheitlichen Modus mit einem 4-Byte-Präfix wie `text` `image` die Daten, und und `ntext` nicht mit einem 8-Byte-Präfix gespeichert. Dies ist der Standardwert für [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und spätere Versionen.  
  
## <a name="copying-date-values"></a>Kopieren von Datumswerten  
 Von**bcp** wird die ODBC-API für das Massenkopieren verwendet. Deshalb verwendet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]bcp **zum Importieren von Datumswerten in** das ODBC-Datumsformat (*jjjj-mm-tt hh:mm:ss*[ *.f...* ]).  
  
 Der Befehl **bcp** exportiert Datendateien im Zeichenformat unter Verwendung des ODBC-Standard Formats für `datetime` -und- `smalldatetime` Werte. So wird beispielsweise eine `datetime`-Spalte mit dem Datum `12 Aug 1998` beim Massenkopieren in eine Datendatei als die Zeichenfolge `1998-08-12 00:00:00.000` übertragen.  
  
> [!IMPORTANT]  
>  Wenn Sie Daten `smalldatetime` mithilfe von **bcp**in ein Feld importieren, achten Sie darauf, dass der Wert für Sekunden 00,000 ist; andernfalls schlägt der Vorgang fehl. Der `smalldatetime`-Datentyp kann nur Werte beinhalten, die auf die volle Minute gerundet sind. BULK INSERT und INSERT ... SELECT * FROM OPENROWSET(BULK...) schlagen in diesem Fall nicht fehl, schneiden jedoch den Sekundenwert ab.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben  
 **So verwenden Sie Datenformate für Massenimport oder Massenexport**  
  
-   [Verwenden des Zeichenformats zum Importieren und Exportieren von Daten &#40;SQL Server&#41;](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Verwenden des nativen Formats zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Verwenden des Unicode-Zeichenformats zum Importieren und Exportieren von Daten &#40;SQL Server&#41;](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Verwenden des nativen Unicode-Formats zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
 
  
## <a name="see-also"></a>Weitere Informationen  
 [bcp (Hilfsprogramm)](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)   
 [Datentypen &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)   
 [Abwärtskompatibilität der SQL Server-Datenbank-Engine](../../database-engine/sql-server-database-engine-backward-compatibility.md)   
 [CAST und CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql)  
  
  
