---
title: Kontext Verbindung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- context connections [CLR integration]
- database objects [CLR integration], connections
- connections [CLR integration]
- context [CLR integration]
ms.assetid: 67dd1925-d672-4986-a85f-bce4fe832ef7
author: rothja
ms.author: jroth
ms.openlocfilehash: 82c739aa9c1952c71e9a16aaa68ec999851b3202
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617118"
---
# <a name="context-connection"></a>Kontextverbindung
  Der interne Datenzugriff ist ein verbreitetes Problem. Es tritt auf, wenn Sie auf denselben Server zugreifen möchten, auf dem auch die CLR-gespeicherte Prozedur (Common Language Runtime, CLR) oder -Funktion ausgeführt wird. Eine der Optionen besteht darin, mithilfe von `System.Data.SqlClient.SqlConnection` eine Verbindung zu erstellen, eine Verbindungszeichenfolge anzugeben, die auf den lokalen Server zeigt, und die Verbindung anschließend zu öffnen. Dies erfordert die Angabe von Anmeldeinformationen für die Anmeldung. Die Verbindung wurde in einer anderen Datenbanksitzung als die gespeicherte Prozedur oder Funktion hergestellt, sie verwendet möglicherweise andere `SET`-Optionen, befindet sich in einer separaten Transaktion, hat keinen Zugriff auf die temporären Tabellen usw. Wenn der Code Ihrer verwalteten gespeicherten Prozedur oder Funktion im SQL Serverprozess ausgeführt wird, liegt das daran, dass jemand eine Verbindung mit diesem Server hergestellt und eine SQL-Anweisung ausgeführt hat, um den Code aufzurufen. Nun möchten Sie eventuell die gespeicherte Prozedur oder Funktion im Kontext dieser Verbindung ausführen, zusammen mit deren Transaktion, `SET`-Optionen und so weiter. Dies wird als Kontextverbindung bezeichnet.  
  
 Die Kontextverbindung ermöglicht, Transact-SQL-Anweisungen im selben Kontext auszuführen wie den Code, der anfänglich aufgerufen wurde. Um die Kontextverbindung herzustellen, müssen Sie "context connection", das Schlüsselwort für die Verbindungszeichenfolge der Kontextverbindung, verwenden, wie im nachstehenden Beispiel gezeigt:  
  
 [C#]  
  
```  
using(SqlConnection connection = new SqlConnection("context connection=true"))   
{  
    connection.Open();  
    // Use the connection  
}  
```  
  
 [Visual Basic]  
  
```  
Using connection as new SqlConnection("context connection=true")  
    connection.Open()  
    ' Use the connection  
End Using  
  
```  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Reguläre vs. Kontextverbindungen](context-connections-vs-regular-connections.md)  
 Beschreibt die Unterschiede zwischen regulären Verbindungen und Kontextverbindungen.  
  
 [Einschränkungen hinsichtlich regulärer Verbindungen und Kontextverbindungen](context-connections-and-regular-connections-restrictions.md)  
 Beschreibt die Einschränkungen hinsichtlich regulärer Verbindungen und Kontextverbindungen.  
  
  
