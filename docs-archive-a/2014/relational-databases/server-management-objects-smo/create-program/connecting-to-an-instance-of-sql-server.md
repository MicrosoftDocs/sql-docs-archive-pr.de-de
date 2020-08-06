---
title: Herstellen einer Verbindung mit einer Instanz von SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, connections
- connections [SMO]
- instances of SQL Server, connections
- SMO [SQL Server], connections
ms.assetid: ad3cf354-b2e3-468b-b986-1232e375fd84
author: stevestein
ms.author: sstein
ms.openlocfilehash: efc21451f4a876c6edfe4a2389ca937d11bc5c8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621997"
---
# <a name="connecting-to-an-instance-of-sql-server"></a>Herstellen einer Verbindung zu einer Instanz von SQL Server
  Der erste Programmier Schritt in einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO)-Anwendung besteht darin, eine Instanz des <xref:Microsoft.SqlServer.Management.Smo.Server> -Objekts zu erstellen und eine Verbindung mit einer Instanz von herzustellen [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
 Es stehen drei Möglichkeiten zur Verfügung, um eine Instanz des <xref:Microsoft.SqlServer.Management.Smo.Server>-Objekts zu erstellen und eine Verbindung zu einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] herzustellen. Die erste Methode verwendet eine <xref:Microsoft.SqlServer.Management.Common.ServerConnection>-Objektvariable, um die Verbindungsinformationen bereitzustellen. Die zweite Methode besteht darin, die Verbindungsinformationen durch die explizite Angabe der <xref:Microsoft.SqlServer.Management.Smo.Server>-Objekteigenschaften anzugeben. Bei der dritten Methode wird der Name der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz im <xref:Microsoft.SqlServer.Management.Smo.Server>-Objektkonstruktor angegeben.  
  
 **Verwenden eines ServerConnection-Objekts**  
  
 Das Verwenden der <xref:Microsoft.SqlServer.Management.Common.ServerConnection>-Objektvariable bietet den Vorteil, dass die Verbindungsinformationen wiederverwendet werden können. Deklarieren Sie eine <xref:Microsoft.SqlServer.Management.Smo.Server>-Objektvariable. Deklarieren Sie anschließend ein <xref:Microsoft.SqlServer.Management.Common.ServerConnection>-Objekt, und geben Sie die Eigenschaften mit Verbindungsinformationen wie dem Namen der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz und dem Authentifizierungsmodus an. Übergeben Sie dann die <xref:Microsoft.SqlServer.Management.Common.ServerConnection>-Objektvariable als Parameter an den <xref:Microsoft.SqlServer.Management.Smo.Server>-Objektkonstruktor. Es wird nicht empfohlen, mehrere Verbindungen zwischen unterschiedlichen Serverobjekten gleichzeitig freizugeben. Verwenden Sie die <xref:Microsoft.SqlServer.Management.Common.ServerConnection.Copy%2A>-Methode, um eine Kopie der vorhandenen Verbindungseinstellungen abzurufen.  
  
 **Explizites Festlegen von Serverobjekteigenschaften**  
  
 Alternativ können Sie die <xref:Microsoft.SqlServer.Management.Smo.Server>-Objektvariable deklarieren und den Standardkonstruktor aufrufen. Normalerweise versucht das <xref:Microsoft.SqlServer.Management.Smo.Server>-Objekt, mit sämtlichen Standardverbindungseinstellungen eine Verbindung zur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Standardinstanz herzustellen.  
  
 **Bereitstellen des Namens der SQL Server-Instanz im Serverobjektkonstruktor**  
  
 Deklarieren Sie die <xref:Microsoft.SqlServer.Management.Smo.Server>-Objektvariable und übergeben Sie den Namen der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz als Zeichenfolgenparameter im Konstruktor. Das <xref:Microsoft.SqlServer.Management.Smo.Server>-Objekt stellt mit den Standardverbindungseinstellungen eine Verbindung zur Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] her.  
  
## <a name="connection-pooling"></a>Verbindungspooling  
 Es ist in der Regel nicht erforderlich, die <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A>-Methode des <xref:Microsoft.SqlServer.Management.Common.ServerConnection>-Objekts aufzurufen. SMO stellt bei Bedarf automatisch eine Verbindung her und gibt nach dem Abschluss der Vorgänge die Verbindung zum Verbindungspool frei. Wenn die <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A>-Methode aufgerufen wird, wird die Verbindung zum Pool nicht freigegeben. Um die Verbindung zum Pool freizugeben, ist ein expliziter Aufruf der <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A>-Methode erforderlich. Darüber hinaus können Sie eine nicht in einem Pool enthaltene Verbindung anfordern, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A>-Eigenschaft des <xref:Microsoft.SqlServer.Management.Common.ServerConnection>-Objekts festlegen.  
  
## <a name="multithreaded-applications"></a>Multithreadanwendungen  
 Für Multithreadanwendungen sollte in jedem Thread ein separates <xref:Microsoft.SqlServer.Management.Common.ServerConnection>-Objekt verwendet werden.  
  
## <a name="connecting-to-an-instance-of-sql-server-for-rmo"></a>Herstellen einer Verbindung zu einer Instanz von SQL Server für RMO  
 Replikationsverwaltungsobjekte (RMO) unterscheiden sich im Aufbau einer Verbindung zu einem Replikationsserver leicht von SMO.  
  
 Bei RMO-Programmierobjekten ist es erforderlich, dass eine Verbindung zu einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mithilfe des durch den `Microsoft.SqlServer.Management.Common`-Namespace implementierten <xref:Microsoft.SqlServer.Management.Common.ServerConnection>-Objekts erfolgt. Diese Verbindung zum Server erfolgt unabhängig von einem RMO-Programmierobjekt. Sie wird anschließend entweder während der Erstellung der Instanz oder durch die Zuweisung zur <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>-Eigenschaft des Objekts an das RMO-Objekts weitergegeben. Dadurch können ein RMO-Programmierobjekt und die Instanzen des Verbindungsobjekts getrennt erstellt und verwaltet werden. Zudem kann ein einzelnes Verbindungsobjekt mit mehreren RMO-Programmierobjekten verwendet werden. Für Verbindungen mit einem Replikationsserver gelten die folgenden Regeln:  
  
-   Alle Eigenschaften für die Verbindung werden für ein angegebenes <xref:Microsoft.SqlServer.Management.Common.ServerConnection> Objekt definiert.  
  
-   Jede Verbindung zu einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] muss über ein eigenes <xref:Microsoft.SqlServer.Management.Common.ServerConnection>-Objekt verfügen.  
  
-   Sämtliche Authentifizierungsinformationen, die zur Herstellung der Verbindung und zur erfolgreichen Anmeldung beim Server erforderlich sind, sind im <xref:Microsoft.SqlServer.Management.Common.ServerConnection>-Objekt angegeben.  
  
-   Standardmäßig werden Verbindungen mit der Microsoft Windows-Authentifizierung hergestellt. Um die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Authentifizierung verwenden zu können, müssen <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.LoginSecure%2A> auf False und <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Login%2A> sowie <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Password%2A> auf eine gültige [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Kombination von Anmeldeinformationen und Kennwort gesetzt sein. Anmelde Informationen für die Sicherheit müssen immer sicher gespeichert und verarbeitet werden, und Sie werden zur Laufzeit nach Möglichkeit bereitgestellt.  
  
-   Die <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A>-Methode muss vor Übergabe der Verbindung an ein RMO-Programmierobjekt aufgerufen werden.  
  
## <a name="examples"></a>Beispiele  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="connecting-to-the-local-instance-of-sql-server-by-using-windows-authentication-in-visual-basic"></a>Herstellen einer Verbindung zur lokalen Instanz von SQL Server mithilfe der Windows-Authentifizierung in Visual Basic  
 Das Herstellen einer Verbindung zur lokalen Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] erfordert nur wenig Code. Für Authentifizierungsmethode und Server werden die Standardeinstellungen verwendet. Sobald das erste Mal Daten abgerufen werden müssen, wird eine Verbindung erstellt.  
  
 Dieses Beispiel ist [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET-Code, der mithilfe der Windows-Authentifizierung eine Verbindung mit der lokalen Instanz von herstellt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VB1](SMO How to#SMO_VB1)]  -->  
  
## <a name="connecting-to-the-local-instance-of-sql-server-by-using-windows-authentication-in-visual-c"></a>Herstellen einer Verbindung zur lokalen Instanz von SQL Server mithilfe der Windows-Authentifizierung in Visual C#  
 Das Herstellen einer Verbindung zur lokalen Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] erfordert nur wenig Code. Für Authentifizierungsmethode und Server werden die Standardeinstellungen verwendet. Sobald das erste Mal Daten abgerufen werden müssen, wird eine Verbindung erstellt.  
  
 Der im Beispiel dargestellte Visual C# .NET-Code stellt mithilfe der Windows-Authentifizierung eine Verbindung zu einer lokalen Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] her.  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//The connection is established when a property is requested.   
Console.WriteLine(srv.Information.Version);   
}   
//The connection is automatically disconnected when the Server variable goes out of scope.  
```  
  
## <a name="connecting-to-a-remote-instance-of-sql-server-by-using-windows-authentication-in-visual-basic"></a>Herstellen einer Verbindung zur Remoteinstanz von SQL Server mithilfe der Windows-Authentifizierung in Visual Basic  
 Wenn Sie mithilfe der Windows-Authentifizierung eine Verbindung zu einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] herstellen, müssen Sie den Authentifizierungstyp nicht angeben. Die Windows-Authentifizierung ist als Standard vorgegeben.  
  
 Dieses Beispiel ist ein [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET-Code, der mithilfe der Windows-Authentifizierung eine Verbindung mit der Remote Instanz von herstellt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Die Zeichen folgen *Variable "* ".  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VB2](SMO How to#SMO_VB2)]  -->  
  
## <a name="connecting-to-a-remote-instance-of-sql-server-by-using-windows-authentication-in-visual-c"></a>Herstellen einer Verbindung zur Remoteinstanz von SQL Server mithilfe der Windows-Authentifizierung in Visual C#  
 Wenn Sie mithilfe der Windows-Authentifizierung eine Verbindung zu einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] herstellen, müssen Sie den Authentifizierungstyp nicht angeben. Die Windows-Authentifizierung ist als Standard vorgegeben.  
  
 Der im Beispiel dargestellte Visual C# .NET-Code stellt mithilfe der Windows-Authentifizierung eine Verbindung zu einer Remoteinstanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] her. Die Zeichen folgen *Variable "* ".  
  
```  
{   
//Connect to a remote instance of SQL Server.   
Server srv;   
//The strServer string variable contains the name of a remote instance of SQL Server.   
srv = new Server(strServer);   
//The actual connection is made when a property is retrieved.   
Console.WriteLine(srv.Information.Version);   
}   
//The connection is automatically disconnected when the Server variable goes out of scope.  
```  
  
## <a name="connecting-to-an-instance-of-sql-server-by-using-sql-server-authentication-in-visual-basic"></a>Herstellen einer Verbindung zu einer Instanz von SQL Server mithilfe der SQL Server-Authentifizierung in Visual Basic  
 Wenn Sie mithilfe der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Authentifizierung eine Verbindung zu einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] herstellen, müssen Sie den Authentifizierungstyp angeben. In diesem Beispiel ist eine Alternativmethode angegeben, mit der Sie eine <xref:Microsoft.SqlServer.Management.Common.ServerConnection>-Objektvariable deklarieren und die Verbindungsinformationen wiederverwenden können.  
  
 Das Beispiel ist ein [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET-Code, der veranschaulicht, wie eine Verbindung mit dem Remote-und dem *vpassword* -Anmelde-und-Kennwort hergestellt  
  
```  
' compile with:   
' /r:Microsoft.SqlServer.Smo.dll  
' /r:Microsoft.SqlServer.ConnectionInfo.dll  
' /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll   
  
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Common  
  
Public Class A  
   Public Shared Sub Main()  
      Dim sqlServerLogin As [String] = "user_id"  
      Dim password As [String] = "pwd"  
      Dim instanceName As [String] = "instance_name"  
      Dim remoteSvrName As [String] = "remote_server_name"  
  
      ' Connecting to an instance of SQL Server using SQL Server Authentication  
      Dim srv1 As New Server()   ' connects to default instance  
      srv1.ConnectionContext.LoginSecure = False   ' set to true for Windows Authentication  
      srv1.ConnectionContext.Login = sqlServerLogin  
      srv1.ConnectionContext.Password = password  
      Console.WriteLine(srv1.Information.Version)   ' connection is established  
  
      ' Connecting to a named instance of SQL Server with SQL Server Authentication using ServerConnection  
      Dim srvConn As New ServerConnection()  
      srvConn.ServerInstance = ".\" & instanceName   ' connects to named instance  
      srvConn.LoginSecure = False   ' set to true for Windows Authentication  
      srvConn.Login = sqlServerLogin  
      srvConn.Password = password  
      Dim srv2 As New Server(srvConn)  
      Console.WriteLine(srv2.Information.Version)   ' connection is established  
  
      ' For remote connection, remote server name / ServerInstance needs to be specified  
      Dim srvConn2 As New ServerConnection(remoteSvrName)  
      srvConn2.LoginSecure = False  
      srvConn2.Login = sqlServerLogin  
      srvConn2.Password = password  
      Dim srv3 As New Server(srvConn2)  
      Console.WriteLine(srv3.Information.Version)   ' connection is established  
   End Sub  
End Class  
```  
  
## <a name="connecting-to-an-instance-of-sql-server-by-using-sql-server-authentication-in-visual-c"></a>Herstellen einer Verbindung zu einer Instanz von SQL Server mithilfe der SQL Server-Authentifizierung in Visual C#  
 Wenn Sie mithilfe der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Authentifizierung eine Verbindung zu einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] herstellen, müssen Sie den Authentifizierungstyp angeben. In diesem Beispiel ist eine Alternativmethode angegeben, mit der Sie eine <xref:Microsoft.SqlServer.Management.Common.ServerConnection>-Objektvariable deklarieren und die Verbindungsinformationen wiederverwenden können.  
  
 Das Beispiel ist Visual c# .NET-Code, der veranschaulicht, wie eine Verbindung mit dem Remote-und dem *vpassword* -Element, das Anmelde-und Kennwort enthält  
  
```  
// compile with:   
// /r:Microsoft.SqlServer.Smo.dll  
// /r:Microsoft.SqlServer.ConnectionInfo.dll  
// /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll   
  
using System;  
using Microsoft.SqlServer.Management.Smo;  
using Microsoft.SqlServer.Management.Common;  
  
public class A {  
   public static void Main() {   
      String sqlServerLogin = "user_id";  
      String password = "pwd";  
      String instanceName = "instance_name";  
      String remoteSvrName = "remote_server_name";  
  
      // Connecting to an instance of SQL Server using SQL Server Authentication  
      Server srv1 = new Server();   // connects to default instance  
      srv1.ConnectionContext.LoginSecure = false;   // set to true for Windows Authentication  
      srv1.ConnectionContext.Login = sqlServerLogin;  
      srv1.ConnectionContext.Password = password;  
      Console.WriteLine(srv1.Information.Version);   // connection is established  
  
      // Connecting to a named instance of SQL Server with SQL Server Authentication using ServerConnection  
      ServerConnection srvConn = new ServerConnection();  
      srvConn.ServerInstance = @".\" + instanceName;   // connects to named instance  
      srvConn.LoginSecure = false;   // set to true for Windows Authentication  
      srvConn.Login = sqlServerLogin;  
      srvConn.Password = password;  
      Server srv2 = new Server(srvConn);  
      Console.WriteLine(srv2.Information.Version);   // connection is established  
  
      // For remote connection, remote server name / ServerInstance needs to be specified  
      ServerConnection srvConn2 = new ServerConnection(remoteSvrName);  
      srvConn2.LoginSecure = false;  
      srvConn2.Login = sqlServerLogin;  
      srvConn2.Password = password;  
      Server srv3 = new Server(srvConn2);  
      Console.WriteLine(srv3.Information.Version);   // connection is established  
   }  
}  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.SqlServer.Management.Smo.Server>   
 <xref:Microsoft.SqlServer.Management.Common.ServerConnection>  
  
  
