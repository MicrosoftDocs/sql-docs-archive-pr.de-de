---
title: Konvertierungen von Server zu Client | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- conversions [OLE DB], server to client
ms.assetid: 676fdf24-fb72-4ea0-a8d2-2b197da3c83f
author: rothja
ms.author: jroth
ms.openlocfilehash: dc64241eb76d59be457862ee5a9e7dd9fc8b84d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87722745"
---
# <a name="conversions-performed-from-server-to-client"></a>Server/Client-Konvertierungen
  Dieses Thema beschreibt die Datums-/Uhrzeit-Konvertierungen zwischen [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (oder höher) und Clientanwendungen, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB geschrieben wurden.  
  
## <a name="conversions"></a>Konvertierungen  
 Die folgende Tabelle beschreibt die Konvertierungen der Typen, die an den Client zurückgegeben werden, und die in der Bindung verwendeten Typen. Wenn für die Ausgabeparameter ICommandWithParameters::SetParameterInfo aufgerufen wurde und der in *pwszDataSourceType* angegebene Typ nicht dem aktuellen Typ auf dem Server entspricht, führt der Server eine implizite Konvertierung durch. Der an den Client zurückgegebene Typ entspricht dem über ICommandWithParameters::SetParameterInfo angegebenen Datentyp. Dies kann zu unerwarteten Konvertierungs Ergebnissen führen, wenn sich die Konvertierungsregeln des Servers von den in diesem Thema beschriebenen unterscheiden. Wenn beispielsweise ein Standarddatum bereitgestellt werden muss, verwendet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 1900-1-1, nicht 1899-12-30.  
  
|Bis --><br /><br /> From|DATE|DBDATE|DBTIME|DBTIME2|DBTIMESTAMP|DBTIMESTAMPOFFSET|FILETIME|BYTES|VARIANT|SSVARIANT|BSTR|STR|WSTR|  
|----------------------|----------|------------|------------|-------------|-----------------|-----------------------|--------------|-----------|-------------|---------------|----------|---------|----------|  
|Date|1,7|OK|-|-|1|1,3|1,7|-|OK (VT_BSTR)|OK|OK|4|4|  
|Time|5, 6, 7|-|9|OK|6|3, 6|5, 6|-|OK (VT_BSTR)|OK|OK|4|4|  
|Smalldatetime|7|8|9,10|10|OK|3|7|-|7 (VT_DATE)|OK|OK|4|4|  
|Datetime|5, 7|8|9,10|10|OK|3|7|-|7 (VT_DATE)|OK|OK|4|4|  
|Datetime2|5, 7|8|9,10|10|7|3|5, 7|-|OK (VT_BSTR)|OK|OK|4|4|  
|Datetimeoffset|5, 7, 11|8, 11|9, 10, 11|10, 11|7, 11|OK|5, 7, 11|-|OK (VT_BSTR)|OK|OK|4|4|  
|Char, Varchar,<br /><br /> Nchar, Nvarchar|7, 13|12|12, 9|12|12|12|7, 13|–|–|–|–|–|–|  
|Sql_variant<br /><br /> (datetime)|7|8|9,10|10|OK|3|7|-|7(VT_DATE)|OK|OK|4|4|  
|Sql_variant<br /><br /> (smalldatetime)|7|8|9,10|10|OK|3|7|-|7(VT_DATE)|OK|OK|4|4|  
|Sql_variant<br /><br /> (date)|1,7|OK|2|2|1|1,3|1,7|-|OK(VT_BSTR)|OK|OK|4|4|  
|Sql_variant<br /><br /> (time)|5, 6, 7|2|6|OK|6|3, 6|5, 6|-|OK(VT_BSTR)|OK|OK|4|4|  
|Sql_variant<br /><br /> (datetime2)|5, 7|8|9,10|10|OK|3|5, 7|-|OK(VT_BSTR)|OK|OK|4|4|  
|Sql_variant<br /><br /> (datetimeoffset)|5, 7, 11|8, 11|9, 10, 11|10, 11|7, 11|OK|5, 7, 11|-|OK(VT_BSTR)|OK|OK|4|4|  
  
## <a name="key-to-symbols"></a>Aufschlüsselung der Symbole  
  
|Symbol|Bedeutung|  
|------------|-------------|  
|OK|Keine Konvertierung notwendig.|  
|-|Es wird keine Konvertierung unterstützt. Wenn beim Aufruf von IAccessor::CreateAccessor die Bindung überprüft wird, wird DBBINDSTATUS_UPSUPPORTEDCONVERSION in *rgStatus* zurückgegeben. Bei Verzögerung der Accessorüberprüfung wird DBSTATUS_E_BADACCESSOR festgelegt.|  
|1|Für die Uhrzeitfelder wird 0 festgelegt.|  
|2|DBSTATUS_E_CANTCONVERTVALUE wird festgelegt.|  
|3|Für die Zeitzone wird 0 festgelegt.|  
|4|Wenn der Clientpuffer nicht groß genug ist, wird DBSTATUS_S_TRUNCATED festgelegt. Wenn der Serverdatentyp Sekundenbruchteile enthält, entspricht die Anzahl der Stellen in der Ergebniszeichenfolge genau den Dezimalstellen des Serverdatentyps.|  
|5|Das Abschneiden von Sekunden oder Sekundenbruchteilen wird ignoriert.|  
|6|Für das Datum wird das aktuelle Datum angenommen, es sei denn, die Quelle ist ein Zeichenfolgenliteral für time, und das Ziel ist DBTYPE_DATE. In diesem Fall wird 1899-12-30 verwendet.|  
|7|Wenn der Wert überläuft, wird DBSTATUS_E_DATAOVERFLOW festgelegt.|  
|8|Zeitfelder werden ignoriert.|  
|9|Felder für Sekundenbruchteile werden ignoriert.|  
|10|Die Datumskomponente wird ignoriert.|  
|11|Die Zeitangabe wird in die Clientzeitzone konvertiert. Wenn während dieser Konvertierung ein Fehler auftritt, wird DBSTATUS_E_DATAOVERFLOW festgelegt.|  
|12|Die Zeichenfolge wird als ISO-Literal analysiert und in den Zieltyp konvertiert. Falls dies fehlschlägt, wird die Zeichenfolge als OLE-Datumsliteral analysiert (welches gleichfalls Zeitkomponenten enthält) und vom OLE-Datumstyp (DBTYPE_DATE) in den Zieldatumstyp konvertiert. Die Zeichenfolge muss mit der für die ISO-Formatanalyse zulässigen Syntax für Literale des Zieltyps übereinstimmen, damit der Vorgang ordnungsgemäß ausgeführt werden kann. Die Zeichenfolge muss mit der von OLE erkannten Syntax übereinstimmen, damit die OLE-Analyse ordnungsgemäß ausgeführt werden kann. Wenn die Zeichenfolge nicht analysiert werden kann, wird DBSTATUS_E_CANTCONVERTVALUE festgelegt. Wenn Komponentenwerte außerhalb des Gültigkeitsbereichs liegen, wird DBSTATUS_E_DATAOVERFLOW festgelegt.|  
|13|Die Zeichenfolge wird als ISO-Literal analysiert und in den Zieltyp konvertiert. Falls dies fehlschlägt, wird die Zeichenfolge als OLE-Datumsliteral analysiert (welches gleichfalls Zeitkomponenten enthält) und vom OLE-Datumstyp (DBTYPE_DATE) in den Zieldatumstyp konvertiert. Die Zeichenfolge muss der Syntax für datetime-Literale entsprechen, außer wenn das Ziel DBTYPE_DATE oder DBTYPE_DBTIMESTAMP ist. Wenn dies der Fall ist, ist ein Literal vom Typ datetime oder vom Typ time für die erfolgreiche ISO-Formatanalyse zulässig. Die Zeichenfolge muss mit der von OLE erkannten Syntax übereinstimmen, damit die OLE-Analyse ordnungsgemäß ausgeführt werden kann. Wenn die Zeichenfolge nicht analysiert werden kann, wird DBSTATUS_E_CANTCONVERTVALUE festgelegt. Wenn Komponentenwerte außerhalb des Gültigkeitsbereichs liegen, wird DBSTATUS_E_DATAOVERFLOW festgelegt.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bindungen und Konvertierungen &#40;OLE DB&#41;](conversions-ole-db.md)  
  
  
