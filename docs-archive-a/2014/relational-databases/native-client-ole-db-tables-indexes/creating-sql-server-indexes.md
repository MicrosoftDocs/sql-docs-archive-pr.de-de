---
title: Erstellen von SQL Server-Indizes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- CreateIndex function
- constraints [OLE DB]
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
- adding indexes
ms.assetid: 6239d440-2818-4b98-bb79-732dced41952
author: rothja
ms.author: jroth
ms.openlocfilehash: 3693355eec7a290c03658c10db500161aa52062d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87723753"
---
# <a name="creating-sql-server-indexes"></a>Erstellen von SQL Server-Indizes
  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter macht die **IIndexDefinition:: | ateindex** -Funktion verfügbar und ermöglicht es Consumern, neue Indizes für Tabellen zu definieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter erstellt Tabellenindizes entweder als Indizes oder als Einschränkungen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gewährt dem Tabellenbesitzer, Datenbankbesitzer und Mitgliedern bestimmter Administratorrollen die Berechtigung zum Erstellen von Einschränkungen. Standardmäßig kann nur der Tabellenbesitzer einen Index für eine Tabelle erstellen. Aus diesem Grund hängt es nicht nur von den Zugriffsrechten des Anwendungsbenutzers, sondern auch von der Art des erstellten Indexes ab, ob **CreateIndex** erfolgreich verläuft oder fehlschlägt.  
  
 Consumer geben den Tabellennamen als Unicode-Zeichenfolge in das *pwszName*-Element der *uName*-Vereinigung des *pTableID*-Parameters ein. Das *eKind*-Element von *pTableID* muss DBKIND_NAME sein.  
  
 Der *pIndexID* -Parameter kann NULL sein, und wenn dies der Fall ist, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellt der Native Client OLE DB-Anbieter einen eindeutigen Namen für den Index. Der Consumer kann den Namen des Indexes aufzeichnen, indem er einen gültigen Zeiger auf eine DBID im Parameter *ppIndexID* angibt.  
  
 Der Consumer kann den Indexnamen als Unicode-Zeichenfolge in das Element *pwszName* der Vereinigung *uName* des Parameters *pIndexID* eingeben. Das *eKind*-Element von *pIndexID* muss DBKIND_NAME sein.  
  
 Der Consumer gibt die Spalte oder die Spalten an, die namentlich in den Index einbezogen werden. Für jede DBINDEXCOLUMNDESC-Struktur, die in **CreateIndex** verwendet wird, muss das Element *eKind* der *pColumnID* DBKIND_NAME sein. Der Name der Spalte wird als Unicode-Zeichenfolge in das Element *pwszName* der Vereinigung *uName* des Parameters *pColumnID* eingegeben.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützen aufsteigende Reihenfolge bei Werten im Index. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt E_INVALIDARG zurück, wenn der Consumer DBINDEX_COL_ORDER_DESC in einer beliebigen DBINDEXCOLUMNDESC-Struktur angibt.  
  
 **CreateIndex** interpretiert Indexeigenschaften wie folgt.  
  
|Eigenschafts-ID|BESCHREIBUNG|  
|-----------------|-----------------|  
|DBPROP_INDEX_AUTOUPDATE|R/W: Lesen/Schreiben<br /><br /> Standardwert: Keiner<br /><br /> Beschreibung: der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt diese Eigenschaft nicht. Versuche, diese Eigenschaft in **CreateIndex** festzulegen, verursachen einen DB_S_ERRORSOCCURRED-Rückgabewert. Das Element *dwStatus* der Eigenschaftsstruktur gibt DBPROPSTATUS_BADVALUE an.|  
|DBPROP_INDEX_CLUSTERED|R/W: Lesen/Schreiben<br /><br /> Standardwert: VARIANT_FALSE<br /><br /> Beschreibung: Steuert die Indexgruppierung.<br /><br /> VARIANT_TRUE: der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter versucht, einen gruppierten Index für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabelle zu erstellen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt maximal einen gruppierten Index pro Tabelle.<br /><br /> VARIANT_FALSE: der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter versucht, einen nicht gruppierten Index für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabelle zu erstellen.|  
|DBPROP_INDEX_FILLFACTOR|R/W: Lesen/Schreiben<br /><br /> Standard: 0<br /><br /> Beschreibung: Gibt den Prozentsatz einer für Speicher verwendeten Indexseite an. Weitere Informationen finden Sie unter [Create Index](/sql/t-sql/statements/create-index-transact-sql).<br /><br /> Der Typ der Variante ist VT_I4. Der Wert muss größer als oder gleich 1 und kleiner als oder gleich 100 sein.|  
|DBPROP_INDEX_INITIALIZE|R/W: Lesen/Schreiben<br /><br /> Standardwert: Keiner<br /><br /> Beschreibung: der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt diese Eigenschaft nicht. Versuche, diese Eigenschaft in **CreateIndex** festzulegen, verursachen einen DB_S_ERRORSOCCURRED-Rückgabewert. Das Element *dwStatus* der Eigenschaftsstruktur gibt DBPROPSTATUS_BADVALUE an.|  
|DBPROP_INDEX_NULLCOLLATION|R/W: Lesen/Schreiben<br /><br /> Standardwert: Keiner<br /><br /> Beschreibung: der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt diese Eigenschaft nicht. Versuche, diese Eigenschaft in **CreateIndex** festzulegen, verursachen einen DB_S_ERRORSOCCURRED-Rückgabewert. Das Element *dwStatus* der Eigenschaftsstruktur gibt DBPROPSTATUS_BADVALUE an.|  
|DBPROP_INDEX_NULLS|R/W: Lesen/Schreiben<br /><br /> Standardwert: Keiner<br /><br /> Beschreibung: der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt diese Eigenschaft nicht. Versuche, diese Eigenschaft in **CreateIndex** festzulegen, verursachen einen DB_S_ERRORSOCCURRED-Rückgabewert. Das Element *dwStatus* der Eigenschaftsstruktur gibt DBPROPSTATUS_BADVALUE an.|  
|DBPROP_INDEX_PRIMARYKEY|R/W: Lesen/Schreiben<br /><br /> Standard: VARIANT_FALSE Beschreibung: Erstellt den Index als PRIMARY KEY-Einschränkung mit referenzieller Integrität.<br /><br /> VARIANT_TRUE: Der Index wird erstellt, um die PRIMARY KEY-Einschränkung der Tabelle zu unterstützen. Die Spalten dürfen keine NULL-Werte zulassen.<br /><br /> VARIANT_FALSE: Der Index wird nicht als PRIMARY KEY-Einschränkung für Zeilenwerte in der Tabelle verwendet.|  
|DBPROP_INDEX_SORTBOOKMARKS|R/W: Lesen/Schreiben<br /><br /> Standardwert: Keiner<br /><br /> Beschreibung: der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt diese Eigenschaft nicht. Versuche, diese Eigenschaft in **CreateIndex** festzulegen, verursachen einen DB_S_ERRORSOCCURRED-Rückgabewert. Das Element *dwStatus* der Eigenschaftsstruktur gibt DBPROPSTATUS_BADVALUE an.|  
|DBPROP_INDEX_TEMPINDEX|R/W: Lesen/Schreiben<br /><br /> Standardwert: Keiner<br /><br /> Beschreibung: der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt diese Eigenschaft nicht. Versuche, diese Eigenschaft in **CreateIndex** festzulegen, verursachen einen DB_S_ERRORSOCCURRED-Rückgabewert. Das Element *dwStatus* der Eigenschaftsstruktur gibt DBPROPSTATUS_BADVALUE an.|  
|DBPROP_INDEX_TYPE|R/W: Lesen/Schreiben<br /><br /> Standardwert: Keiner<br /><br /> Beschreibung: der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt diese Eigenschaft nicht. Versuche, diese Eigenschaft in **CreateIndex** festzulegen, verursachen einen DB_S_ERRORSOCCURRED-Rückgabewert. Das Element *dwStatus* der Eigenschaftsstruktur gibt DBPROPSTATUS_BADVALUE an.|  
|DBPROP_INDEX_UNIQUE|R/W: Lesen/Schreiben<br /><br /> Standardwert: VARIANT_FALSE<br /><br /> Beschreibung: Erstellt den Index als UNIQUE-Einschränkung für die einbezogene(n) Spalte oder Spalten.<br /><br /> VARIANT_TRUE: Der Index wird verwendet, um Zeilenwerte in der Tabelle eindeutig einzuschränken.<br /><br /> VARIANT_FALSE: Der Index schränkt Zeilenwerte nicht eindeutig ein.|  
  
 Im anbieterspezifischen Eigenschaften Satz DBPROPSET_SQLSERVERINDEX [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] definiert der Native Client OLE DB-Anbieter die folgende Eigenschaft für Datenquellen Informationen.  
  
|Eigenschafts-ID|BESCHREIBUNG|  
|-----------------|-----------------|  
|SSPROP_INDEX_XML|Typ: VT_BOOL (R/W)<br /><br /> Standardwert: VARIANT_FALSE<br /><br /> Beschreibung: Wenn diese Eigenschaft mit dem Wert VARIANT_TRUE mit IIndexDefinition::CreateIndex angegeben wird, wird ein primärer XML-Index erstellt, der der zu indizierenden Spalte entspricht. Wenn diese Eigenschaft VARIANT_TRUE ist, sollte cIndexColumnDescs 1 sein; andernfalls tritt ein Fehler auf.|  
  
 In diesem Beispiel wird ein Primärschlüsselindex erstellt:  
  
```  
// This CREATE TABLE statement shows the referential integrity and   
// PRIMARY KEY constraint on the OrderDetails table that will be created   
// by the following example code.  
//  
// CREATE TABLE OrderDetails  
// (  
//    OrderID      int      NOT NULL  
//    ProductID   int      NOT NULL  
//        CONSTRAINT PK_OrderDetails  
//        PRIMARY KEY CLUSTERED (OrderID, ProductID),  
//    UnitPrice   money      NOT NULL,  
//    Quantity   int      NOT NULL,  
//    Discount   decimal(2,2)   NOT NULL  
//        DEFAULT 0  
// )  
//  
HRESULT CreatePrimaryKey  
    (  
    IIndexDefinition* pIIndexDefinition  
    )  
    {  
    HRESULT             hr = S_OK;  
  
    DBID                dbidTable;  
    DBID                dbidIndex;  
    const ULONG         nCols = 2;  
    ULONG               nCol;  
    const ULONG         nProps = 2;  
    ULONG               nProp;  
  
    DBINDEXCOLUMNDESC   dbidxcoldesc[nCols];  
    DBPROP              dbpropIndex[nProps];  
    DBPROPSET           dbpropset;  
  
    DBID*               pdbidIndexOut = NULL;  
  
    // Set up identifiers for the table and index.  
    dbidTable.eKind = DBKIND_NAME;  
    dbidTable.uName.pwszName = L"OrderDetails";  
  
    dbidIndex.eKind = DBKIND_NAME;  
    dbidIndex.uName.pwszName = L"PK_OrderDetails";  
  
    // Set up column identifiers.  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        dbidxcoldesc[nCol].pColumnID = new DBID;  
        dbidxcoldesc[nCol].pColumnID->eKind = DBKIND_NAME;  
  
        dbidxcoldesc[nCol].eIndexColOrder = DBINDEX_COL_ORDER_ASC;  
        }  
    dbidxcoldesc[0].pColumnID->uName.pwszName = L"OrderID";  
    dbidxcoldesc[1].pColumnID->uName.pwszName = L"ProductID";  
  
    // Set properties for the index. The index is clustered,  
    // PRIMARY KEY.  
    for (nProp = 0; nProp < nProps; nProp++)  
        {  
        dbpropIndex[nProp].dwOptions = DBPROPOPTIONS_REQUIRED;  
        dbpropIndex[nProp].colid = DB_NULLID;  
  
        VariantInit(&(dbpropIndex[nProp].vValue));  
  
        dbpropIndex[nProp].vValue.vt = VT_BOOL;  
        }  
    dbpropIndex[0].dwPropertyID = DBPROP_INDEX_CLUSTERED;  
    dbpropIndex[0].vValue.boolVal = VARIANT_TRUE;  
  
    dbpropIndex[1].dwPropertyID = DBPROP_INDEX_PRIMARYKEY;  
    dbpropIndex[1].vValue.boolVal = VARIANT_TRUE;  
  
    dbpropset.rgProperties = dbpropIndex;  
    dbpropset.cProperties = nProps;  
    dbpropset.guidPropertySet = DBPROPSET_INDEX;  
  
    hr = pIIndexDefinition->CreateIndex(&dbidTable, &dbidIndex, nCols,  
        dbidxcoldesc, 1, &dbpropset, &pdbidIndexOut);  
  
    // Clean up dynamically allocated DBIDs.  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        delete dbidxcoldesc[nCol].pColumnID;  
        }  
  
    return (hr);  
    }  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellen und Indizes](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)  
  
  
