---
title: Verwenden von Synonymen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- synonyms [SMO]
ms.assetid: db0a9022-9549-43e5-b6b3-deb236f05fb8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5e8416dc3daea3b173fae92e5454a8a65c399e53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87622509"
---
# <a name="using-synonyms"></a>Verwenden von Synonymen
  Ein Synonym ist ein alternativer Name für ein Objekt mit Schemabereich. In SMO werden Synonyme durch das <xref:Microsoft.SqlServer.Management.Smo.Synonym>-Objekt dargestellt. Das <xref:Microsoft.SqlServer.Management.Smo.Synonym>-Objekt ist dem <xref:Microsoft.SqlServer.Management.Smo.Database>-Objekt untergeordnet. Dies bedeutet, dass Synonyme nur in dem Kontext der Datenbank gültig sind, in der sie definiert sind. Allerdings kann das Synonym auf Objekte einer anderen Datenbank oder auf eine Remoteinstanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]verweisen.  
  
 Das Objekt, dem ein alternativer Name gegeben wird, wird als Basisobjekt bezeichnet. Die Name-Eigenschaft des <xref:Microsoft.SqlServer.Management.Smo.Synonym>-Objekts ist ein alternativer Name, der an das Basisobjekt vergeben wird.  
  
## <a name="example"></a>Beispiel  
 Für das folgende Codebeispiel müssen Sie die Programmierungsumgebung, die Programmiervorlage und die Programmiersprache auswählen, um Ihre Anwendung zu erstellen. Weitere Informationen finden Sie unter [Erstellen eines Visual Basic SMO-Projekts in Visual Studio .net](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) und [Erstellen eines Visual C&#35; SMO-Projekts in Visual Studio .net](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-a-synonym-in-visual-basic"></a>Erstellen eines Synonyms in Visual Basic  
 Dieses Codebeispiel zeigt, wie ein Synonym oder ein alternativer Name für ein Objekt mit Schemabereich erstellt wird. Clientanwendungen können einen einzelnen Verweis für das Basisobjekt über ein Synonym verwenden, anstatt einen mehrteiligen Namen zu verwenden, der auf das Basisobjekt verweist.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBSynonyms1](SMO How to#SMO_VBSynonyms1)]  -->  
  
## <a name="creating-a-synonym-in-visual-c"></a>Erstellen eines Synonyms in Visual C#  
 Dieses Codebeispiel zeigt, wie ein Synonym oder ein alternativer Name für ein Objekt mit Schemabereich erstellt wird. Clientanwendungen können einen einzelnen Verweis für das Basisobjekt über ein Synonym verwenden, anstatt einen mehrteiligen Namen zu verwenden, der auf das Basisobjekt verweist.  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
  
            //Reference the AdventureWorks2012 database.   
            Database db = srv.Databases["AdventureWorks2012"];  
  
            //Define a Synonym object variable by supplying the   
            //parent database, name, and schema arguments in the constructor.   
            //The name is also a synonym of the name of the base object.   
            Synonym syn = new Synonym(db, "Shop", "Sales");  
  
            //Specify the base object, which is the object on which   
            //the synonym is based.   
            syn.BaseDatabase = "AdventureWorks2012";  
            syn.BaseSchema = "Sales";  
            syn.BaseObject = "Store";  
            syn.BaseServer = srv.Name;  
  
            //Create the synonym on the instance of SQL Server.   
            syn.Create();  
        }  
```  
  
## <a name="creating-a-synonym-in-powershell"></a>Erstellen eines Synonyms in PowerShell  
 Dieses Codebeispiel zeigt, wie ein Synonym oder ein alternativer Name für ein Objekt mit Schemabereich erstellt wird. Clientanwendungen können einen einzelnen Verweis für das Basisobjekt über ein Synonym verwenden, anstatt einen mehrteiligen Namen zu verwenden, der auf das Basisobjekt verweist.  
  
```powershell
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#And the database object corresponding to Adventureworks  
$db = $srv.Databases["AdventureWorks2012"]  
  
$syn = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Synonym -ArgumentList $db, "Shop", "Sales"  
  
#Specify the base object, which is the object on which the synonym is based.  
$syn.BaseDatabase = "AdventureWorks2012"  
$syn.BaseSchema = "Sales"  
$syn.BaseObject = "Store"  
$syn.BaseServer = $srv.Name  
  
#Create the synonym on the instance of SQL Server.  
$syn.Create()  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE SYNONYM &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-synonym-transact-sql)  
