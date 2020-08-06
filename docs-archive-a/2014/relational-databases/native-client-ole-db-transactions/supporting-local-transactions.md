---
title: Unterstützen von lokalen Transaktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- autocommit mode
- transactions [OLE DB]
- ITransactionLocal interface
- SQL Server Native Client OLE DB provider, transactions
- local transactions [OLE DB]
ms.assetid: 78f2e5fc-b6fb-4eda-9f71-991a4d6c4902
author: rothja
ms.author: jroth
ms.openlocfilehash: a9bc11a038e56517aa42619117c371c1319b9ffe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87620824"
---
# <a name="supporting-local-transactions"></a>Unterstützen lokaler Transaktionen
  Eine Sitzung begrenzt den Transaktions Bereich für eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lokale Transaktion eines Native Client OLE DB Anbieters. Wenn der Native Client OLE DB-Anbieter in Richtung eines Consumers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine Anforderung an eine verbundene Instanz von sendet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , stellt die Anforderung eine Arbeitseinheit für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter dar. Lokale Transaktionen wrappen immer eine oder mehrere Arbeitseinheiten in einer einzelnen systemeigenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client OLE DB-Anbieter Sitzung.  
  
 Mithilfe des standardmäßigen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Autocommit-Modus von Native Client OLE DB-Anbieters wird eine einzelne Arbeitseinheit als Bereich einer lokalen Transaktion behandelt. Nur eine Einheit nimmt an der lokalen Transaktion teil. Wenn eine Sitzung erstellt wird, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] beginnt der Native Client OLE DB-Anbieter eine Transaktion für die Sitzung. Nach der erfolgreichen Verarbeitung einer Arbeitseinheit wird ein Commit für die Arbeit ausgeführt. Bei Auftreten eines Fehlers wird ein Rollback für den begonnenen Teil der Arbeit ausgeführt, und der Fehler wird dem Consumer gemeldet. In beiden Fällen beginnt der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter eine neue lokale Transaktion für die Sitzung, sodass alle Aufgaben innerhalb einer Transaktion durchgeführt werden.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Consumer des Native Client OLE DB-Anbieters kann eine präzisere Kontrolle über den lokalen Transaktions Bereich mithilfe der **itransaktionlocal** -Schnittstelle leiten. Wenn eine Consumersitzung eine Transaktion initiiert, werden alle Arbeitseinheiten der Sitzung zwischen dem Anfangspunkt der Transaktion und eventuellen Aufrufen der Methode **Commit** oder der Methode **Abort** als eine unteilbare Einheit behandelt. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter beginnt implizit eine Transaktion, wenn er vom Consumer an ihn weitergeleitet wird. Wenn der Consumer keine Beibehaltung anfordert, kehrt die Sitzung zum Verhalten der übergeordneten Transaktionsebene zurück, in der Regel ist das der Autocommitmodus.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt **ITransaction local:: Start Transaction** -Parameter wie folgt.  
  
|Parameter|BESCHREIBUNG|  
|---------------|-----------------|  
|*isoLevel*[in]|Die innerhalb dieser Transaktion zu verwendende Isolationsstufe. In lokalen Transaktionen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt der Native Client OLE DB-Anbieter Folgendes:<br /><br /> -ISOLATIONLEVEL_UNSPECIFIED<br />-ISOLATIONLEVEL_CHAOS<br />-ISOLATIONLEVEL_READUNCOMMITTED<br />-ISOLATIONLEVEL_READCOMMITTED<br />-ISOLATIONLEVEL_REPEATABLEREAD<br />-ISOLATIONLEVEL_CURSORSTABILITY<br />-ISOLATIONLEVEL_REPEATABLEREAD<br />-ISOLATIONLEVEL_SERIALIZABLE<br />-ISOLATIONLEVEL_ISOLATED<br />-ISOLATIONLEVEL_SNAPSHOT **Hinweis:** ab [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ist ISOLATIONLEVEL_SNAPSHOT für das *isoLevel* -Argument gültig, unabhängig davon, ob die Versionsverwaltung für die Datenbank aktiviert ist. Jedoch tritt ein Fehler auf, wenn der Benutzer versucht, eine Anweisung auszuführen und die Versionsverwaltung nicht aktiviert und/oder die Datenbank nicht schreibgeschützt ist. Zudem tritt bei einer Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Version, die älter als [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ist, der Fehler XACT_E_ISOLATIONLEVEL auf, wenn ISOLATIONLEVEL_SNAPSHOT als *isoLevel* angegeben wird.|  
|*isoFlags*[in]|Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt einen Fehler für einen beliebigen Wert ungleich 0 (null) zurück.|  
|*pOtherOptions*[in]|Wenn nicht NULL, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fordert der Native Client OLE DB-Anbieter das Options-Objekt von der-Schnittstelle an. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt XACT_E_NOTIMEOUT zurück, wenn der *ulTimeout* -Member des Options-Objekts nicht 0 (null) ist. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter ignoriert den Wert des *szDescription* -Members.|  
|*pulTransactionLevel*[out]|Wenn der Wert nicht NULL ist, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt der Native Client OLE DB-Anbieter die auf dem Systemebene der Transaktion zurück.|  
  
 Für lokale Transaktionen implementiert der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter **ITransaction:: Abort** -Parameter wie folgt.  
  
|Parameter|BESCHREIBUNG|  
|---------------|-----------------|  
|*pboidReason*[in]|Wird bei Festlegung ignoriert. Kann daher auch NULL sein.|  
|*fRetaining*[in]|Wenn der Wert TRUE lautet, wird eine neue Transaktion implizit für die Sitzung begonnen. Für die Transaktion muss vom Consumer ein Commit ausgeführt werden oder sie muss beendet werden. Wenn der Wert false ist, wird der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Autocommit-Modus für die Sitzung vom Native Client OLE DB-Anbieter wieder hergestellt.|  
|*fAsync*[in]|Der asynchrone Abbruch wird vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter nicht unterstützt. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt XACT_E_NOTSUPPORTED zurück, wenn der Wert nicht false ist.|  
  
 Für lokale Transaktionen implementiert der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter **ITransaction:: Commit** -Parameter wie folgt.  
  
|Parameter|BESCHREIBUNG|  
|---------------|-----------------|  
|*fRetaining*[in]|Wenn der Wert TRUE lautet, wird eine neue Transaktion implizit für die Sitzung begonnen. Für die Transaktion muss vom Consumer ein Commit ausgeführt werden oder sie muss beendet werden. Wenn der Wert false ist, wird der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Autocommit-Modus für die Sitzung vom Native Client OLE DB-Anbieter wieder hergestellt.|  
|*grfTC*[in]|Asynchrone und Phase 1-Rückgaben werden vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter nicht unterstützt. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt XACT_E_NOTSUPPORTED für jeden anderen Wert als XACTTC_SYNC zurück.|  
|*grfRM*[in]|Muss den Wert 0 (null) haben.|  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Rowsets des Native Client OLE DB-Anbieters in der Sitzung werden bei einem lokalen Commit-oder Abbruch Vorgang basierend auf den Werten der Rowseteigenschaften DBPROP_ABORTPRESERVE und DBPROP_COMMITPRESERVE beibehalten. Standardmäßig sind diese Eigenschaften VARIANT_FALSE, und alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider-Rowsets in der Sitzung gehen nach einem Abbruch-oder Commitvorgang verloren.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter implementiert nicht die **itransaktionobject** -Schnittstelle. Bei einem Versuch des Consumers, einen Verweis auf die Schnittstelle abzurufen, wird E_NOINTERFACE zurückgegeben.  
  
 Im folgenden Beispiel wird **ITransactionLocal** verwendet.  
  
```  
// Interfaces used in the example.  
IDBCreateSession*   pIDBCreateSession   = NULL;  
ITransaction*       pITransaction       = NULL;  
IDBCreateCommand*   pIDBCreateCommand   = NULL;  
IRowset*            pIRowset            = NULL;  
  
HRESULT             hr;  
  
// Get the command creation and local transaction interfaces for the  
// session.  
if (FAILED(hr = pIDBCreateSession->CreateSession(NULL,  
     IID_IDBCreateCommand, (IUnknown**) &pIDBCreateCommand)))  
    {  
    // Process error from session creation. Release any references and  
    // return.  
    }  
  
if (FAILED(hr = pIDBCreateCommand->QueryInterface(IID_ITransactionLocal,  
    (void**) &pITransaction)))  
    {  
    // Process error. Release any references and return.  
    }  
  
// Start the local transaction.  
if (FAILED(hr = ((ITransactionLocal*) pITransaction)->StartTransaction(  
    ISOLATIONLEVEL_REPEATABLEREAD, 0, NULL, NULL)))  
    {  
    // Process error from StartTransaction. Release any references and  
    // return.  
    }  
  
// Get data into a rowset, then update the data. Functions are not  
// illustrated in this example.  
if (FAILED(hr = ExecuteCommand(pIDBCreateCommand, &pIRowset)))  
    {  
    // Release any references and return.  
    }  
  
// If rowset data update fails, then terminate the transaction, else  
// commit. The example doesn't retain the rowset.  
if (FAILED(hr = UpdateDataInRowset(pIRowset, bDelayedUpdate)))  
    {  
    // Get error from update, then terminate.  
    pITransaction->Abort(NULL, FALSE, FALSE);  
    }  
else  
    {  
    if (FAILED(hr = pITransaction->Commit(FALSE, XACTTC_SYNC, 0)))  
        {  
        // Get error from failed commit.  
        }  
    }  
  
if (FAILED(hr))  
    {  
    // Update of data or commit failed. Release any references and  
    // return.  
    }  
  
// Release any references and continue.  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Transaktionen](transactions.md)   
 [Arbeiten mit der Momentaufnahme Isolation](../native-client/features/working-with-snapshot-isolation.md)  
  
  
