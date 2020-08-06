---
title: Implementieren der voll Text Suche | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- full-text search [SMO]
ms.assetid: 9ce9ad9c-f671-4760-90b5-e0c8ca051473
author: stevestein
ms.author: sstein
ms.openlocfilehash: f8b797e2a38c9136c34b7058b539fca522e03229
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87695518"
---
# <a name="implementing-full-text-search"></a>Einbinden einer Volltextsuche
  Volltextsuche ist pro Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verfügbar und wird durch das <xref:Microsoft.SqlServer.Management.Smo.Server.FullTextService%2A>-Objekt in SMO dargestellt. Das <xref:Microsoft.SqlServer.Management.Smo.FullTextService>-Objekt befindet sich unter dem `Server`-Objekt. Es wird verwendet, um die Konfigurationsoptionen für den Dienst [!INCLUDE[msCoName](../../../includes/msconame-md.md)] -Volltextsuche zu verwalten. Das <xref:Microsoft.SqlServer.Management.Smo.FullTextCatalogCollection>-Objekt gehört zum <xref:Microsoft.SqlServer.Management.Smo.Database>-Objekt und ist eine Auflistung von <xref:Microsoft.SqlServer.Management.Smo.FullTextCatalog>-Objekten, die Volltextkataloge darstellen, die für die Datenbank definiert sind. Im Gegensatz zu normalen Indizes kann nur ein Volltextindex für jede Tabelle definiert sein. Dies wird durch ein <xref:Microsoft.SqlServer.Management.Smo.FullTextIndexColumn>-Objekt im <xref:Microsoft.SqlServer.Management.Smo.Table>-Objekt dargestellt.  
  
 Um einen Volltextsuchdienst zu erstellen, muss auf der Datenbank ein Volltextkatalog und in einer der Tabellen in der Datenbank ein Index für die Volltextsuche definiert sein.  
  
 Erstellen Sie zunächst einen Volltextkatalog auf der Datenbank, indem Sie den <xref:Microsoft.SqlServer.Management.Smo.FullTextCatalog>-Konstruktor aufrufen und einen Katalognamen angeben. Erstellen Sie dann den Volltextindex, indem Sie den Konstruktor aufrufen und die Tabelle angeben, in der dieser erstellt werden soll. Daraufhin können Sie Indexspalten für die Volltextsuche hinzufügen, indem Sie das <xref:Microsoft.SqlServer.Management.Smo.FullTextIndexColumn>-Objekt verwenden und den Namen der Spalte in der Tabelle angeben. Legen Sie dann die <xref:Microsoft.SqlServer.Management.Smo.FullTextIndex.CatalogName%2A>-Eigenschaft auf den Katalog fest, den Sie erstellt haben. Rufen Sie zum Schluss die <xref:Microsoft.SqlServer.Management.Smo.FullTextIndex.Create%2A>-Methode auf, und erstellen Sie den Volltextindex auf der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="example"></a>Beispiel  
 Zum Verwenden eines angegebenen Codebeispiels müssen Sie die Programmierumgebung, Programmiervorlage und die zu verwendende Programmiersprache auswählen, um Ihre Anwendung zu erstellen. Weitere Informationen finden Sie unter [Erstellen eines Visual Basic SMO-Projekts in Visual Studio .net](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) oder [Erstellen eines Visual C&#35; SMO-Projekts in Visual Studio .net](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-a-full-text-search-service-in-visual-basic"></a>Erstellen eines Volltextsuchdiensts in Visual Basic  
 In diesem Codebeispiel wird ein Volltextsuchkatalog für die `ProductCategory` -Tabelle in der Beispieldatenbank [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] erstellt. Anschließend wird für die Name-Spalte in der `ProductCategory` -Tabelle ein Index für die Volltextsuche erstellt. Der Index für die Volltextsuche erfordert, dass bereits ein eindeutiger Index für die Spalte definiert ist.  
  
```vb
' compile with:   
' /r:Microsoft.SqlServer.SqlEnum.dll   
' /r:Microsoft.SqlServer.Smo.dll   
' /r:Microsoft.SqlServer.ConnectionInfo.dll   
' /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll  
  
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Sdk.Sfc  
Imports Microsoft.SqlServer.Management.Common  
  
Public Class A  
   Public Shared Sub Main()  
      ' Connect to the local, default instance of SQL Server.  
      Dim srv As Server = Nothing  
      srv = New Server()  
  
      ' Reference the AdventureWorks database.  
      Dim db As Database = Nothing  
      db = srv.Databases("AdventureWorks")  
  
      ' Reference the ProductCategory table.  
      Dim tb As Table = Nothing  
      tb = db.Tables("ProductCategory", "Production")  
  
      ' Define a FullTextCatalog object variable by specifying the parent database and name arguments in the constructor.  
      Dim ftc As FullTextCatalog = Nothing  
      ftc = New FullTextCatalog(db, "Test_Catalog")  
      ftc.IsDefault = True  
  
      ' Create the Full-Text Search catalog on the instance of SQL Server.  
      ftc.Create()  
  
      ' Define a FullTextIndex object varaible by supplying the parent table argument in the constructor.  
      Dim fti As FullTextIndex = Nothing  
      fti = New FullTextIndex(tb)  
  
      ' Define a FullTextIndexColumn object variable by supplying the parent index and column name arguments in the constructor.  
      Dim ftic As FullTextIndexColumn = Nothing  
      ftic = New FullTextIndexColumn(fti, "Name")  
  
      ' Add the indexed column to the index.  
      fti.IndexedColumns.Add(ftic)  
      fti.ChangeTracking = ChangeTracking.Automatic  
  
      ' Specify the unique index on the table that is required by the Full Text Search index.  
      fti.UniqueIndexName = "AK_ProductCategory_Name"  
  
      ' Specify the catalog associated with the index.  
      fti.CatalogName = "Test_Catalog"  
  
      ' Create the Full Text Search index on the instance of SQL Server.  
      fti.Create()  
   End Sub  
End Class  
```  
  
## <a name="creating-a-full-text-search-service-in-visual-c"></a>Erstellen eines Volltextsuchdiensts in Visual C#  
 In diesem Codebeispiel wird ein Volltextsuchkatalog für die `ProductCategory` -Tabelle in der Beispieldatenbank [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] erstellt. Anschließend wird für die Name-Spalte in der `ProductCategory` -Tabelle ein Index für die Volltextsuche erstellt. Der Index für die Volltextsuche erfordert, dass bereits ein eindeutiger Index für die Spalte definiert ist.  
  
```csharp
// compile with:   
// /r:Microsoft.SqlServer.SqlEnum.dll   
// /r:Microsoft.SqlServer.Smo.dll   
// /r:Microsoft.SqlServer.ConnectionInfo.dll   
// /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll   
  
using Microsoft.SqlServer.Management.Smo;  
using Microsoft.SqlServer.Management.Sdk.Sfc;  
using Microsoft.SqlServer.Management.Common;  
  
public class A {  
   public static void Main() {  
      // Connect to the local, default instance of SQL Server.  
      Server srv = default(Server);  
      srv = new Server();  
  
      // Reference the AdventureWorks database.  
      Database db = default(Database);  
      db = srv.Databases ["AdventureWorks"];  
  
      // Reference the ProductCategory table.  
      Table tb = default(Table);  
      tb = db.Tables["ProductCategory", "Production"];  
  
      // Define a FullTextCatalog object variable by specifying the parent database and name arguments in the constructor.  
      FullTextCatalog ftc = default(FullTextCatalog);  
      ftc = new FullTextCatalog(db, "Test_Catalog");  
      ftc.IsDefault = true;  
  
      // Create the Full-Text Search catalog on the instance of SQL Server.  
      ftc.Create();  
  
      // Define a FullTextIndex object varaible by supplying the parent table argument in the constructor.  
      FullTextIndex fti = default(FullTextIndex);  
      fti = new FullTextIndex(tb);  
  
      // Define a FullTextIndexColumn object variable by supplying the parent index and column name arguments in the constructor.  
      FullTextIndexColumn ftic = default(FullTextIndexColumn);  
      ftic = new FullTextIndexColumn(fti, "Name");  
  
      // Add the indexed column to the index.  
      fti.IndexedColumns.Add(ftic);  
      fti.ChangeTracking = ChangeTracking.Automatic;  
  
      // Specify the unique index on the table that is required by the Full Text Search index.  
      fti.UniqueIndexName = "AK_ProductCategory_Name";  
  
      // Specify the catalog associated with the index.  
      fti.CatalogName = "Test_Catalog";  
  
      // Create the Full Text Search index on the instance of SQL Server.  
      fti.Create();  
   }  
}  
```  
  
## <a name="creating-a-full-text-search-service-in-powershell"></a>Erstellen eines Volltextsuchdiensts in PowerShell  
 In diesem Codebeispiel wird ein Volltextsuchkatalog für die `ProductCategory` -Tabelle in der Beispieldatenbank [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] erstellt. Anschließend wird für die Name-Spalte in der `ProductCategory` -Tabelle ein Index für die Volltextsuche erstellt. Der Index für die Volltextsuche erfordert, dass bereits ein eindeutiger Index für die Spalte definiert ist.  
  
```powershell
# Example of implementing a full text search on the default instance.  
# Set the path context to the local, default instance of SQL Server and database tables  
  
CD \sql\localhost\default\databases  
$db = Get-Item AdventureWorks2012  
  
CD AdventureWorks\tables  
  
#Get a reference to the table  
$tb = Get-Item Production.ProductCategory  
  
# Define a FullTextCatalog object variable by specifying the parent database and name arguments in the constructor.  
  
$ftc = New-Object -TypeName Microsoft.SqlServer.Management.SMO.FullTextCatalog -ArgumentList $db, "Test_Catalog2"  
$ftc.IsDefault = $true  
  
# Create the Full Text Search catalog on the instance of SQL Server.  
$ftc.Create()  
  
# Define a FullTextIndex object variable by supplying the parent table argument in the constructor.  
$fti = New-Object -TypeName Microsoft.SqlServer.Management.SMO.FullTextIndex -ArgumentList $tb  
  
#  Define a FullTextIndexColumn object variable by supplying the parent index
#  and column name arguments in the constructor.  
  
$ftic = New-Object -TypeName Microsoft.SqlServer.Management.SMO.FullTextIndexColumn -ArgumentList $fti, "Name"  
  
# Add the indexed column to the index.  
$fti.IndexedColumns.Add($ftic)  
  
# Set change tracking  
$fti.ChangeTracking = [Microsoft.SqlServer.Management.SMO.ChangeTracking]::Automatic  
  
# Specify the unique index on the table that is required by the Full Text Search index.  
$fti.UniqueIndexName = "AK_ProductCategory_Name"  
  
# Specify the catalog associated with the index.  
$fti.CatalogName = "Test_Catalog2"  
  
# Create the Full Text Search Index  
$fti.Create()  
```  
