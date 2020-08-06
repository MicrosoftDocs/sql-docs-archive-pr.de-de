---
title: SSVARIANT-Struktur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
f1_keywords:
- SSVARIANT
helpviewer_keywords:
- SSVARIANT struct
ms.assetid: d13c6aa6-bd49-467a-9093-495df8f1e2d9
author: rothja
ms.author: jroth
ms.openlocfilehash: ed05eec7f9029519c04341380b8e43abc3d443bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609878"
---
# <a name="ssvariant-structure"></a>SSVARIANT-Struktur
  Die `SSVARIANT`-Struktur, die in sqlncli.h definiert ist, entspricht einem DBTYPE_SQLVARIANT-Wert im OLE DB-Anbieter von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
 `SSVARIANT` ist eine unterscheidende Vereinigung. Abhängig vom Wert des vt-Elements kann der Consumer feststellen, welches Element gelesen werden soll. vt-Werte entsprechen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen. Die `SSVARIANT`-Struktur kann daher jeden SQL Server-Typ enthalten. Weitere Informationen zur Datenstruktur für standardmäßige OLE DB-Typen finden Sie unter [Typindikatoren](https://go.microsoft.com/fwlink/?LinkId=122171).  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn DataTypeCompat auf "80" festgelegt ist, werden verschiedene `SSVARIANT`-Untertypen zu Zeichenfolgen. Beispielsweise werden die folgenden vt-Werte in `SSVARIANT` als VT_SS_WVARSTRING angezeigt:  
  
-   VT_SS_DATETIMEOFFSET  
  
-   VT_SS_DATETIME2  
  
-   VT_SS_TIME2  
  
-   VT_SS_DATE  
  
 Wenn DateTypeCompat auf "0" festgelegt ist, werden diese Typen in ihrer systemeigenen Form angezeigt.  
  
 Weitere Informationen zu SSPROP_INIT_DATATYPECOMPATIBILITY finden Sie unter [Verwenden von Schlüsselwörtern für Verbindungs Zeichenfolgen mit SQL Server Native Client](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Die Datei sqlncli.h enthält VARIANT-Zugriffsmakros, die das Dereferenzieren der Elementtypen der `SSVARIANT`-Struktur vereinfachen. Beispielsweise können Sie V_SS_DATETIMEOFFSET folgendermaßen verwenden:  
  
```  
memcpy(&V_SS_DATETIMEOFFSET(pssVar).tsoDateTimeOffsetVal, pDTO, cbNative);  
V_SS_DATETIMEOFFSET(pssVar).bScale = bScale;  
```  
  
 Den vollständigen Satz der Zugriffsmakros für jeden Member der `SSVARIANT`-Struktur finden Sie in der Datei sqlncli.hi.  
  
 In der folgenden Tabelle sind die Elemente der `SSVARIANT`-Struktur beschrieben.  
  
|Member|OLE DB-Typindikator|OLE DB-C-Datentyp|vt-Wert|Kommentare|  
|------------|---------------------------|------------------------|--------------|--------------|  
|vt|SSVARTYPE|||Gibt den Typ des Werts in der `SSVARIANT`-Struktur an.|  
|bTinyIntVal|DBTYPE_UI1|`BYTE`|`VT_SS_UI1`|Unterstützt den `tinyint`-Datentyp von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|sShortIntVal|DBTYPE_I2|`SHORT`|`VT_SS_I2`|Unterstützt den `smallint`-Datentyp von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|lIntVal|DBTYPE_I4|`LONG`|`VT_SS_I4`|Unterstützt den `int`-Datentyp von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|llBigIntVal|DBTYPE_I8|`LARGE_INTEGER`|`VT_SS_I8`|Unterstützt den `bigint`-Datentyp von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|fltRealVal|DBTYPE_R4|`float`|`VT_SS_R4`|Unterstützt den `real`-Datentyp von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|dblFloatVal|DBTYPE_R8|`double`|`VT_SS_R8`|Unterstützt den `float`-Datentyp von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|cyMoneyVal|DBTYPE_CY|`LARGE_INTEGER`|**VT_SS_MONEY VT_SS_SMALLMONEY**|Unterstützt die `money` Datentypen und **smallmoney** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|fBitVal|DBTYPE_BOOL|`VARIANT_BOOL`|`VT_SS_BIT`|Unterstützt den `bit`-Datentyp von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|rgbGuidVal|DBTYPE_GUID|`GUID`|`VT_SS_GUID`|Unterstützt den `uniqueidentifier`-Datentyp von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|numNumericVal|DBTYPE_NUMERIC|`DB_NUMERIC`|`VT_SS_NUMERIC`|Unterstützt den `numeric`-Datentyp von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|dDateVal|DBTYPE_DATE|`DBDATE`|`VT_SS_DATE`|Unterstützt den `date`-Datentyp von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|tsDateTimeVal|DBTYPE_DBTIMESTAMP|`DBTIMESTAMP`|`VT_SS_SMALLDATETIME VT_SS_DATETIME VT_SS_DATETIME2`|Unterstützt die Datentypen `smalldatetime`, `datetime` und `datetime2` von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|Time2Val|DBTYPE_DBTIME2|`DBTIME2`|`VT_SS_TIME2`|Unterstützt den `time`-Datentyp von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *tTime2Val* ( `DBTIME2` )<br /><br /> *bScale* ( `BYTE` ) gibt den Wert für die Skala für *tTime2Val* an.|  
|tsDateTimeVal|DBTYPE_DBTIMESTAMP|`DBTIMESTAMP`|`VT_SS_DATETIME2`|Unterstützt den `datetime2`-Datentyp von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *tsDataTimeVal* (DBTIMESTAMP)<br /><br /> *bScale* ( `BYTE` ) gibt die Skalierung für den Wert " *tdatatimeval* " an.|  
|DateTimeOffsetVal|DBTYPE_DBTIMESTAMPOFSET|`DBTIMESTAMPOFFSET`|`VT_SS_DATETIMEOFFSET`|Unterstützt den `datetimeoffset`-Datentyp von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *tsodatetimeoffsetval* ( `DBTIMESTAMPOFFSET` )<br /><br /> *bScale* ( `BYTE` ) gibt die Skala für den Wert " *tsodatetimeoffsetval* " an.|  
|NCharVal|Kein entsprechender OLE DB-Typindikator.|`struct _NCharVal`|`VT_SS_WVARSTRING,`<br /><br /> `VT_SS_WSTRING`|Unterstützt die `nchar` Datentypen und **nvarchar** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *sActualLength* ( `SHORT` ) gibt die tatsächliche Länge der Zeichenfolge an, auf die *pwchNCharVal* zeigt. Beinhaltet nicht den abschließenden Nullwert.<br /><br /> *sMaxLength* ( `SHORT` ) gibt die maximale Länge für die Zeichenfolge an, auf die *pwchNCharVal* zeigt.<br /><br /> *pwchNCharVal* ( `WCHAR` \* )-Zeiger auf die Zeichenfolge.<br /><br /> Nicht verwendete Member: *rgbReserved*, *dwReserved* und *pwchReserved*.|  
|CharVal|Kein entsprechender OLE DB-Typindikator.|`struct _CharVal`|`VT_SS_STRING,`<br /><br /> `VT_SS_VARSTRING`|Unterstützt die `char` Datentypen und **varchar** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *sActualLength* ( `SHORT` ) gibt die tatsächliche Länge der Zeichenfolge an, auf die *pchCharVal* zeigt. Beinhaltet nicht den abschließenden Nullwert.<br /><br /> *sMaxLength* ( `SHORT` ) gibt die maximale Länge für die Zeichenfolge an, auf die *pchCharVal* zeigt.<br /><br /> *pchCharVal* ( `CHAR` \* )-Zeiger auf die Zeichenfolge.<br /><br /> Nicht verwendete Member:<br /><br /> *rgbReserved*, *dwReserved* und *pwchReserved*.|  
|BinaryVal|Kein entsprechender OLE DB-Typindikator.|`struct _BinaryVal`|`VT_SS_VARBINARY,`<br /><br /> `VT_SS_BINARY`|Unterstützt die `binary` Datentypen und **varbinary** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *sActualLength* ( `SHORT` ) gibt die tatsächliche Länge der Daten an, auf die *prgbBinaryVal* verweist.<br /><br /> *sMaxLength* ( `SHORT` ) gibt die maximale Länge für die Daten an, auf die *prgbBinaryVal* verweist.<br /><br /> *prgbBinaryVal* ( `BYTE` \* )-Zeiger auf die Binärdaten.<br /><br /> Nicht verwendeter Member: *dwReserved*.|  
|UnknownType|NICHT VERWENDET|NICHT VERWENDET|NICHT VERWENDET|NICHT VERWENDET|  
|BLOBType|NICHT VERWENDET|NICHT VERWENDET|NICHT VERWENDET|NICHT VERWENDET|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datentypen &#40;OLE DB&#41;](data-types-ole-db.md)  
  
  
