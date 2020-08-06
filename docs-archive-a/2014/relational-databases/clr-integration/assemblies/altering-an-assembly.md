---
title: Ändern einer Assembly | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration], modifying
- permissions [CLR integration]
- altering assemblies
- ALTER ASSEMBLY statement
ms.assetid: 9e765fbd-f339-473c-8537-22f478e79696
author: rothja
ms.author: jroth
ms.openlocfilehash: c22ca979675d3b7f263e3bc6de0c41c134a1abcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720047"
---
# <a name="altering-an-assembly"></a>Ändern einer Assembly
  In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] registrierte Assemblys können von einer aktuelleren Version aus mithilfe der ALTER ASSEMBLY-Anweisung aktualisiert werden. Zum Aktualisieren einer Assembly verwenden Sie die ALTER ASSEMBLY-Anweisung mit der folgenden Syntax:  
  
```  
ALTER ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
```  
  
 Mit ALTER ASSEMBLY werden zurzeit ausgeführte Prozesse, die die Assembly verwenden, nicht unterbrochen. Die Prozesse werden mit der unveränderten Assembly weiterhin ausgeführt. Mit ALTER ASSEMBLY können die Signaturen gängiger CLR-Funktionen (Common Language Runtime), Aggregatfunktionen, gespeicherter Prozeduren und Trigger nicht geändert werden. Neue öffentliche Methoden können der Assembly hinzugefügt werden. Private Methoden können beliebig bearbeitet werden, während öffentliche Methoden nur so lange bearbeitet werden können, wie die Signaturen oder Attribute unverändert bleiben. Felder, die in einem systemeigenen serialisierten benutzerdefinierten Typ enthalten sind, einschließlich Datenelemente oder Basisklassen, können nicht mithilfe von ALTER ASSEMBLY geändert werden. Alle anderen Änderungen werden nicht unterstützt. Weitere Informationen finden Sie unter [Alter Assembly &#40;Transact-SQL-&#41;](/sql/t-sql/statements/alter-assembly-transact-sql).  
  
## <a name="changing-the-permission-set-of-an-assembly"></a>Ändern des Berechtigungssatzes einer Assembly  
 Der Berechtigungssatz einer Assembly kann auch mit der ALTER ASSEMBLY-Anweisung geändert werden. Die folgende Anweisung ändert den Berechtigungssatz der SQLCLRTest-Assembly in `EXTERNAL_ACCESS`.  
  
```  
ALTER ASSEMBLY SQLCLRTest  
WITH PERMISSION_SET = EXTERNAL_ACCESS   
```  
  
 Wenn der Berechtigungssatz einer Assembly von `SAFE` in `EXTERNAL_ACCESS` oder `UNSAFE` geändert wird, muss zunächst ein asymmetrischer Schlüssel mit entsprechender Anmeldung mit der `EXTERNAL ACCESS ASSEMBLY`- oder der `UNSAFE ASSEMBLY`-Berechtigung für die Assembly erstellt werden. Weitere Informationen finden Sie unter [Creating an Assembly](creating-an-assembly.md).  
  
## <a name="adding-the-source-code-of-an-assembly"></a>Hinzufügen des Quellcodes einer Assembly  
 Die ADD FILE-Klausel in der ALTER ASSEMBLY-Syntax ist nicht in CREATE ASSEMBLY vorhanden. Sie können sie verwenden, um Quellcode oder beliebige andere Dateien hinzuzufügen, die einer Assembly zugeordnet sind. Die Dateien werden von ihren ursprünglichen Speicherorten kopiert und in Systemtabellen in der Datenbank gespeichert. Dadurch wird sichergestellt, dass stets der Quellcode oder andere Dateien verfügbar sind, wenn Sie die aktuelle Version des UDT neu erstellen oder dokumentieren müssen.  
  
 Die folgende Anweisung fügt der Point.cs-Klasse Quellcode für den Point-UDT hinzu. Dadurch wird der in der Datei Point.cs enthaltene Text kopiert und unter dem Namen "PointSource" in der Datenbank gespeichert.  
  
 `ALTER ASSEMBLY Point`  
  
 `ADD FILE FROM 'C:\Projects\Point\Point.cs' AS PointSource`  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von CLR Integration](managing-clr-integration-assemblies.md)   
 [Erstellen einer Assembly](creating-an-assembly.md)   
 [Löschen einer Assembly](dropping-an-assembly.md)   
 [ALTER ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
  
