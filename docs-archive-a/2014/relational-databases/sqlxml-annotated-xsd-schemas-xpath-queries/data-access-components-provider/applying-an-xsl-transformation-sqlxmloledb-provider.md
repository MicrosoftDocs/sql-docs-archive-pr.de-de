---
title: Anwenden einer XSL-Transformation (SQLXMLOLEDB-Anbieter) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXMLOLEDB Provider, applying XSL transformations
- applying XSL transformations [SQLXML]
- xsl property
- Base Path property
- XSL Transformations [SQLXML]
ms.assetid: cb5e41ab-dd20-4873-af20-f417bd1bbf6d
author: rothja
ms.author: jroth
ms.openlocfilehash: 7fbb427a95d9f2308bf65724758a4a1563b42575
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619036"
---
# <a name="applying-an-xsl-transformation-sqlxmloledb-provider"></a>Anwenden einer XSL-Transformation (SQLXMLOLEDB-Anbieter)
  In dieser ADO-Beispielanwendung wird eine SQL-Abfrage ausgeführt und auf das Ergebnis eine XSL-Transformation angewendet. Wenn die ClientSideXML-Eigenschaft auf true festgelegt wird, wird die Verarbeitung des Rowsets auf der Clientseite erzwungen. Der Befehlsdialekt wird auf {5d531cb2-e6ed-11d2-b252-00c04f681b71} festgelegt, da die SQL-Abfrage in einer Vorlage angegeben ist und dieser Dialekt angegeben werden muss, wenn eine Vorlage ausgeführt wird. Die XSL-Eigenschaft gibt die XSL-Datei an, die zum Anwenden der Transformation verwendet werden soll. Der Wert der Basis Pfadeigenschaft wird verwendet, um nach der XSL-Datei zu suchen. Wenn Sie einen Pfad im Wert der XSL-Eigenschaft angeben, ist der Pfad relativ zu dem Pfad, der in der Basis Pfadeigenschaft angegeben ist.  
  
 In diesem Beispiel wird gezeigt, wie die folgenden für den SQLXMLOLEDB-Anbieter spezifischen Eigenschaften verwendet werden:  
  
-   ClientSideXML  
  
-   XSL  
  
 In dieser clientseitigen ADO-Beispielanwendung wird eine XML-Vorlage, die aus einer einfachen SQL-Abfrage besteht, auf dem Server ausgeführt.  
  
 Da die ClientSideXML-Eigenschaft auf true festgelegt ist, wird die SELECT-Anweisung ohne die for XML-Klausel an den Server gesendet. Der Server führt die Abfrage aus und gibt ein Rowset an den Client zurück. Der Client wendet anschließend die FOR XML-Transformation auf das Rowset an und generiert das XML-Dokument.  
  
 Die XSL-Eigenschaft wird in der Anwendung angegeben. Daher wird die XSL-Transformation auf das XML-Dokument angewendet, das auf dem Client generiert wird, und das Ergebnis ist eine Tabelle mit zwei Spalten.  
  
 Um den Vorlagen Befehl auszuführen, muss der XML-Vorlagen Dialekt "Dialekt-{5d531cb2-e6ed-11d2-b252-00c04f681b71}" angegeben werden.  
  
> [!NOTE]  
>  Im Code müssen Sie den Namen der Instanz von Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in der Verbindungszeichenfolge bereitstellen. In diesem Beispiel wird überdies die Verwendung von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client als Datenanbieter angegeben, was die Installation zusätzlicher Netzwerkclientsoftware erforderlich macht. Weitere Informationen finden Sie unter [System Anforderungen für SQL Server Native Client](../../native-client/system-requirements-for-sql-server-native-client.md).  
  
```  
Option Explicit  
Sub main()  
Dim oTestStream As New ADODB.Stream  
Dim oTestConnection As New ADODB.Connection  
Dim oTestCommand As New ADODB.Command  
oTestConnection.Open "provider=SQLXMLOLEDB.4.0;data provider=SQLNCLI11;data source=SqlServerName;initial catalog=AdventureWorks;Integrated Security=SSPI;"  
Set oTestCommand.ActiveConnection = oTestConnection  
oTestCommand.Properties("ClientSideXML") = True  
oTestCommand.CommandText = _  
        "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql' >" & _  
       " <sql:query> " & _  
        "   SELECT TOP 25 FirstName, LastName FROM Person.Contact FOR XML AUTO " & _  
        "   </sql:query> " & _  
        " </ROOT> "  
oTestStream.Open  
' You need the dialect if you are executing a template.  
oTestCommand.Dialect = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
oTestCommand.Properties("Output Stream").Value = oTestStream  
oTestCommand.Properties("Base Path").Value = "c:\Schemas\SQLXML4\ExecuteTemplateWithXSL\"  
oTestCommand.Properties("xsl").Value = "myxsl.xsl"  
oTestCommand.Execute , , adExecuteStream  
  
oTestStream.Position = 0  
oTestStream.Charset = "utf-8"  
Debug.Print oTestStream.ReadText(adReadAll)  
End Sub  
Sub Form_Load()  
 main  
End Sub  
```  
  
 Im Folgenden finden Sie die XSL-Vorlage. Aus der Anwendung dieser XSL-Vorlage ergibt sich eine zweispaltige Tabelle.  
  
```  
<?xml version='1.0' encoding='UTF-8'?>            
 <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">   
  
    <xsl:template match = 'Person.Contact'>  
       <TR>  
         <TD><xsl:value-of select = '@FirstName' /></TD>  
         <TD><B><xsl:value-of select = '@LastName' /></B></TD>  
       </TR>  
    </xsl:template>  
    <xsl:template match = '/'>  
      <HTML>  
        <HEAD>  
           <STYLE>th { background-color: #CCCCCC }</STYLE>  
        </HEAD>  
        <BODY>  
         <TABLE border='1' style='width:300;'>  
           <TR><TH colspan='2'>Contacts</TH></TR>  
           <TR>  
              <TH >First name</TH>  
              <TH>Last name</TH>  
           </TR>  
           <xsl:apply-templates select = 'ROOT' />  
         </TABLE>  
        </BODY>  
      </HTML>  
    </xsl:template>  
</xsl:stylesheet>  
```  
  
  
