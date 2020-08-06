---
title: Verwalten von Diensten und Netzwerkeinstellungen mit dem WMI-Anbieter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- WMI provider [SMO]
- services [SQL Server], SMO
- network settings [SMO]
- monitoring [SMO]
ms.assetid: ef8c3986-1098-4f21-b03a-f1f6bdb51c26
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1cd373c46460ac95dbe81469eeaa4b3bf9548d68
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87620252"
---
# <a name="managing-services-and-network-settings-by-using-wmi-provider"></a>Verwalten von Diensten und Netzwerkeinstellungen durch die Nutzung von WMI-Anbieter
  Der WMI-Anbieter ist eine veröffentlichte Schnittstelle, die von der [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Management Console (MMC) zur Verwaltung von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Diensten und Netzwerkprotokollen verwendet wird. In SMO stellt das <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer>-Objekt den WMI-Anbieter dar.  
  
 Das <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer>-Objekt arbeitet unabhängig von der mit dem <xref:Microsoft.SqlServer.Management.Smo.Server>-Objekt zu einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hergestellten Verbindung und nutzt Windows-Anmeldeinformationen für die Verbindung zum WMI-Dienst.  
  
## <a name="example"></a>Beispiel  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
 Für Programme, die den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] WMI-Anbieter verwenden, müssen Sie die-Anweisung einschließen, `Imports` um den WMI-Namespace zu qualifizieren. Fügen Sie die Anweisung nach den anderen `Imports`-Anweisungen und vor jeglichen Deklarationen in der Anwendung wie folgt ein:  
  
 `Imports Microsoft.SqlServer.Management.Smo`  
  
 `Imports Microsoft.SqlServer.Management.Common`  
  
 `Imports Microsoft.SqlServer.Management.Smo.Wmi`  
  
## <a name="stopping-and-restarting-the-microsoft-sql-server-service-to-the-instance-of-sql-server-in-visual-basic"></a>Beenden und erneutes Starten des Microsoft SQL Server-Diensts zur Instanz von SQL Server in Visual Basic  
 Dieses Codebeispiel zeigt, wie Dienste mit dem SMO-<xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer>-Objekt beendet und gestartet werden. Hierdurch wird eine Schnittstelle zum WMI-Anbieter für die Konfigurationsverwaltung bereitgestellt.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBWMIService1](SMO How to#SMO_VBWMIService1)]  -->  
  
## <a name="enabling-a-server-protocol-using-a-urn-string-in-visual-basic"></a>Aktivieren eines Serverprotokolls mit einer URN-Zeichenfolge in Visual Basic  
 Das Codebeispiel veranschaulicht, wie ein Serverprotokoll mithilfe eines URN-Objekts gekennzeichnet und das Protokoll anschließend aktiviert wird.  
  
```vb
'This program must run with administrator privileges.  
        'Declare the ManagedComputer WMI interface.  
        Dim mc As New ManagedComputer()  
  
        'Create a URN object that represents the TCP server protocol.  
        Dim u As New Urn("ManagedComputer[@Name='V-ROBMA3']/ServerInstance[@Name='MSSQLSERVER']/ServerProtocol[@Name='Tcp']")  
  
        'Declare the serverProtocol variable and return the ServerProtocol object.  
        Dim sp As ServerProtocol  
        sp = mc.GetSmoObject(u)  
  
        'Enable the protocol.  
        sp.IsEnabled = True  
  
        'propagate back to the service  
        sp.Alter()  
```  
  
## <a name="enabling-a-server-protocol-using-a-urn-string-in-powershell"></a>Aktivieren eines Serverprotokolls mit einer URN-Zeichenfolge in PowerShell  
 Das Codebeispiel veranschaulicht, wie ein Serverprotokoll mithilfe eines URN-Objekts gekennzeichnet und das Protokoll anschließend aktiviert wird.  
  
```powershell
#This example shows how to identify a server protocol using a URN object, and then enable the protocol  
#This program must run with administrator privileges.  
  
#Load the assembly containing the classes used in this example  
[reflection.assembly]::LoadWithPartialName("Microsoft.SqlServer.SqlWmiManagement")  
  
#Get a managed computer instance  
$mc = New-Object -TypeName Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer  
  
#Create a URN object that represents the TCP server protocol  
#Change 'MyPC' to the name of the your computer   
$urn = New-Object -TypeName Microsoft.SqlServer.Management.Sdk.Sfc.Urn -argumentlist "ManagedComputer[@Name='MyPC']/ServerInstance[@Name='MSSQLSERVER']/ServerProtocol[@Name='Tcp']"  
  
#Get the protocol object  
$sp = $mc.GetSmoObject($urn)  
  
#enable the protocol on the object  
$sp.IsEnabled = $true  
  
#propagate back to actual service  
$sp.Alter()  
```  
  
## <a name="starting-and-stopping-a-service-in-visual-c"></a>Starten und Beenden eines Diensts in Visual C#  
 Das Codebeispiel zeigt, wie eine Instanz von SQL Server beendet und gestartet wird.  
  
```csharp
{   
   //Declare and create an instance of the ManagedComputer   
   //object that represents the WMI Provider services.   
   ManagedComputer mc;   
   mc = new ManagedComputer();   
   //Iterate through each service registered with the WMI Provider.   
  
   foreach (Service svc in mc.Services)  
   {   
      Console.WriteLine(svc.Name);   
   }   
//Reference the Microsoft SQL Server service.   
  Service Mysvc = mc.Services["MSSQLSERVER"];   
//Stop the service if it is running and report on the status  
// continuously until it has stopped.   
   if (Mysvc.ServiceState == ServiceState.Running) {   
      Mysvc.Stop();   
      Console.WriteLine(string.Format("{0} service state is {1}", Mysvc.Name, Mysvc.ServiceState));   
      while (!(string.Format("{0}", Mysvc.ServiceState) == "Stopped")) {   
         Console.WriteLine(string.Format("{0}", Mysvc.ServiceState));   
          Mysvc.Refresh();   
      }   
      Console.WriteLine(string.Format("{0} service state is {1}", Mysvc.Name, Mysvc.ServiceState));   
//Start the service and report on the status continuously   
//until it has started.   
      Mysvc.Start();   
      while (!(string.Format("{0}", Mysvc.ServiceState) == "Running")) {   
         Console.WriteLine(string.Format("{0}", Mysvc.ServiceState));   
         Mysvc.Refresh();   
      }   
      Console.WriteLine(string.Format("{0} service state is {1}", Mysvc.Name, Mysvc.ServiceState));  
      Console.ReadLine();  
   }   
   else {   
      Console.WriteLine("SQL Server service is not running.");  
      Console.ReadLine();  
   }   
}  
```  
  
## <a name="starting-and-stopping-a-service-in-powershell"></a>Starten und Beenden eines Diensts in PowerShell  
 Das Codebeispiel zeigt, wie eine Instanz von SQL Server beendet und gestartet wird.  
  
```powershell
#Load the assembly containing the objects used in this example  
[reflection.assembly]::LoadWithPartialName("Microsoft.SqlServer.SqlWmiManagement")  
  
#Get a managed computer instance  
$mc = New-Object -TypeName Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer  
  
#List out all sql server instnces running on this mc  
foreach ($Item in $mc.Services){$Item.Name}  
  
#Get the default sql server datbase engine service  
$svc = $mc.Services["MSSQLSERVER"]  
  
# for stopping and starting services PowerShell must run as administrator  
  
#Stop this service  
$svc.Stop()  
$svc.Refresh()  
while ($svc.ServiceState -ne "Stopped")  
{  
$svc.Refresh()  
$svc.ServiceState  
}  
"Service" + $svc.Name + " is now stopped"  
"Starting " + $svc.Name  
$svc.Start()  
$svc.Refresh()  
while ($svc.ServiceState -ne "Running")  
{  
$svc.Refresh()  
$svc.ServiceState  
}  
$svc.ServiceState  
"Service" + $svc.Name + "is now started"
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konzepte des WMI-Anbieters für die Konfigurationsverwaltung](../../wmi-provider-configuration/wmi-provider-for-configuration-management.md)  
