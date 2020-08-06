---
title: Planen automatischer Verwaltungsaufgaben in SQL Server-Agent | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- scheduling administrative tasks [SMO]
- SQL Server Agent [SMO]
- automatic administrative SMO tasks
ms.assetid: 900242ad-d6a2-48e9-8a1b-f0eea4413c16
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4a7620935a257a4200999cce27ba901588839b16
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621440"
---
# <a name="scheduling-automatic-administrative-tasks-in-sql-server-agent"></a>Planen von automatischen, administrativen Tasks im SQL Server-Agent
  In SMO wird der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Agent durch die folgenden Objekte dargestellt:  
  
-   Das <xref:Microsoft.SqlServer.Management.Smo.Agent.JobServer>-Objekt verfügt über drei Auflistungen von Aufträgen, Warnungen und Operatoren.  
  
-   Das <xref:Microsoft.SqlServer.Management.Smo.Agent.OperatorCollection>-Objekt stellt eine Liste von Pager-, E-Mail-Adressen und NET SEND-Operatoren dar, die automatisch über den Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Agent über Ereignisse benachrichtigt werden können.  
  
-   Das <xref:Microsoft.SqlServer.Management.Smo.Agent.AlertCollection>-Objekt stellt eine Liste von Umständen dar, wie z. B. Systemereignisse oder Leistungsbedingungen, die von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] überwacht werden.  
  
-   Das <xref:Microsoft.SqlServer.Management.Smo.Agent.JobCollection>-Objekt ist geringfügig komplexer. Es stellt eine Liste von Tasks dar, die aus mehreren Schritten bestehen und nach festgelegten Plänen ausgeführt werden. Die Schritte und die Zeitplaninformationen werden im <xref:Microsoft.SqlServer.Management.Smo.Agent.JobStep>-Objekt und <xref:Microsoft.SqlServer.Management.Smo.Agent.JobSchedule>-Objekt gespeichert.  
  
 Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Agent-Objekte befinden sich im <xref:Microsoft.SqlServer.Management.Smo.Agent>-Namespace.  
  
## <a name="examples"></a>Beispiele  
 Zum Verwenden eines angegebenen Codebeispiels müssen Sie die Programmierumgebung, Programmiervorlage und die zu verwendende Programmiersprache auswählen, um Ihre Anwendung zu erstellen. Weitere Informationen finden Sie unter [Erstellen eines Visual Basic SMO-Projekts in Visual Studio .net](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) oder [Erstellen eines Visual C&#35; SMO-Projekts in Visual Studio .net](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
1.  Für Programme, die den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Agent verwenden, müssen Sie die `Imports`-Anweisung einschließen, um den Agent-Namespace zu qualifizieren. Fügen Sie die Anweisung nach den anderen `Imports`-Anweisungen und vor jeglichen Deklarationen in der Anwendung wie folgt ein:  
  
 `Imports Microsoft.SqlServer.Management.Smo`  
  
 `Imports Microsoft.SqlServer.Management.Common`  
  
 `Imports Microsoft.SqlServer.Management.Smo.Agent`  
  
## <a name="creating-a-job-with-steps-and-a-schedule-in-visual-basic"></a>Erstellen eines Auftrags mit Schritten und einem Zeitplan in Visual Basic  
 Dieses Codebeispiel erstellt einen Auftrag mit Schritten sowie einem Zeitplan und informiert dann einen Operator.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBAgent1](SMO How to#SMO_VBAgent1)]  -->  
  
## <a name="creating-a-job-with-steps-and-a-schedule-in-visual-c"></a>Erstellen eines Auftrags mit Schritten und einem Zeitplan in Visual C#  
 Dieses Codebeispiel erstellt einen Auftrag mit Schritten sowie einem Zeitplan und informiert dann einen Operator.  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.  
            Server srv = new Server();  
  
            //Define an Operator object variable by supplying the Agent (parent JobServer object) and the name in the constructor.   
            Operator op = new Operator(srv.JobServer, "Test_Operator");  
  
            //Set the Net send address.   
            op.NetSendAddress = "Network1_PC";  
  
            //Create the operator on the instance of SQL Server Agent.   
            op.Create();  
  
            //Define a Job object variable by supplying the Agent and the name arguments in the constructor and setting properties.   
            Job jb = new Job(srv.JobServer, "Test_Job");  
  
            //Specify which operator to inform and the completion action.   
            jb.OperatorToNetSend = "Test_Operator";  
            jb.NetSendLevel = CompletionAction.Always;  
  
            //Create the job on the instance of SQL Server Agent.   
            jb.Create();  
  
            //Define a JobStep object variable by supplying the parent job and name arguments in the constructor.   
            JobStep jbstp = new JobStep(jb, "Test_Job_Step");  
            jbstp.Command = "Test_StoredProc";  
            jbstp.OnSuccessAction = StepCompletionAction.QuitWithSuccess;  
            jbstp.OnFailAction = StepCompletionAction.QuitWithFailure;  
  
            //Create the job step on the instance of SQL Agent.   
            jbstp.Create();  
  
            //Define a JobSchedule object variable by supplying the parent job and name arguments in the constructor.   
  
            JobSchedule jbsch = new JobSchedule(jb, "Test_Job_Schedule");  
  
            //Set properties to define the schedule frequency, and duration.   
            jbsch.FrequencyTypes = FrequencyTypes.Daily;  
            jbsch.FrequencySubDayTypes = FrequencySubDayTypes.Minute;  
            jbsch.FrequencySubDayInterval = 30;  
            TimeSpan ts1 = new TimeSpan(9, 0, 0);  
            jbsch.ActiveStartTimeOfDay = ts1;  
  
            TimeSpan ts2 = new TimeSpan(17, 0, 0);  
            jbsch.ActiveEndTimeOfDay = ts2;  
            jbsch.FrequencyInterval = 1;  
  
            System.DateTime d = new System.DateTime(2003, 1, 1);  
            jbsch.ActiveStartDate = d;  
  
            //Create the job schedule on the instance of SQL Agent.   
            jbsch.Create();  
        }  
```  
  
## <a name="creating-a-job-with-steps-and-a-schedule-in-powershell"></a>Erstellen eines Auftrags mit Schritten und einem Zeitplan in PowerShell  
 Dieses Codebeispiel erstellt einen Auftrag mit Schritten sowie einem Zeitplan und informiert dann einen Operator.  
  
```powershell
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Define an Operator object variable by supplying the Agent (parent JobServer object) and the name in the constructor.  
$op = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Agent.Operator -argumentlist $srv.JobServer, "Test_Operator"  
  
#Set the Net send address.  
$op.NetSendAddress = "Network1_PC"  
  
#Create the operator on the instance of SQL Agent.  
$op.Create()  
  
#Define a Job object variable by supplying the Agent and the name arguments in the constructor and setting properties.   
$jb = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Agent.Job -argumentlist $srv.JobServer, "Test_Job"   
  
#Specify which operator to inform and the completion action.   
$jb.OperatorToNetSend = "Test_Operator";   
$jb.NetSendLevel = [Microsoft.SqlServer.Management.SMO.Agent.CompletionAction]::Always  
  
#Create the job on the instance of SQL Server Agent.   
$jb.Create()  
  
#Define a JobStep object variable by supplying the parent job and name arguments in the constructor.   
$jbstp = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Agent.JobStep -argumentlist $jb, "Test_Job_Step"   
$jbstp.Command = "Test_StoredProc";   
$jbstp.OnSuccessAction = [Microsoft.SqlServer.Management.SMO.Agent.StepCompletionAction]::QuitWithSuccess;   
$jbstp.OnFailAction =[Microsoft.SqlServer.Management.SMO.Agent.StepCompletionAction]::QuitWithFailure;   
  
#Create the job step on the instance of SQL Agent.   
$jbstp.Create();   
  
#Define a JobSchedule object variable by supplying the parent job and name arguments in the constructor.   
$jbsch = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Agent.JobSchedule -argumentlist $jb, "Test_Job_Schedule"   
  
#Set properties to define the schedule frequency, and duration.   
$jbsch.FrequencyTypes =  [Microsoft.SqlServer.Management.SMO.Agent.FrequencyTypes]::Daily  
  
$jbsch.FrequencySubDayTypes = [Microsoft.SqlServer.Management.SMO.Agent.FrequencySubDayTypes]::Minute  
$jbsch.FrequencySubDayInterval = 30  
$ts1 =  New-Object -TypeName TimeSpan -argumentlist 9, 0, 0  
$jbsch.ActiveStartTimeOfDay = $ts1  
$ts2 = New-Object -TypeName TimeSpan -argumentlist 17, 0, 0  
$jbsch.ActiveEndTimeOfDay = $ts2  
$jbsch.FrequencyInterval = 1  
$jbsch.ActiveStartDate = "01/01/2003"  
  
#Create the job schedule on the instance of SQL Agent.   
$jbsch.Create();  
```  
  
## <a name="creating-an-alert-in-visual-basic"></a>Erstellen einer Warnung in Visual Basic  
 In diesem Codebeispiel wird eine Warnung erstellt, die von einer Leistungsbedingung ausgelöst wird. Die Bedingung muss in einem bestimmten Format bereitgestellt werden:  
  
 **ObjectName | CounterName | Instanz | Comparisionop | Compvalue**  
  
 Ein Operator ist für die Warnungsbenachrichtigung erforderlich. Der <xref:Microsoft.SqlServer.Management.Smo.Agent.Operator>-Typ erfordert eckige Klammern, da es sich beim `operator` um ein Visual Basic-Schlüsselwort handelt.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBAgent3](SMO How to#SMO_VBAgent3)]  -->  
  
## <a name="creating-an-alert-in-visual-c"></a>Erstellen einer Warnung in Visual C#  
 In diesem Codebeispiel wird eine Warnung erstellt, die von einer Leistungsbedingung ausgelöst wird. Die Bedingung muss in einem bestimmten Format bereitgestellt werden:  
  
 **ObjectName | CounterName | Instanz | Comparisionop | Compvalue**  
  
 Ein Operator ist für die Warnungsbenachrichtigung erforderlich. Für den <xref:Microsoft.SqlServer.Management.Smo.Agent.Operator>-Typ sind eckige Klammern erforderlich, da es sich bei `operator` um ein [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]-Schlüsselwort handelt.  
  
```csharp
{  
             //Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
  
            //Define an Alert object variable by supplying the SQL Server Agent and the name arguments in the constructor.   
            Alert al = new Alert(srv.JobServer, "Test_Alert");  
  
            //Specify the performance condition string to define the alert.   
            al.PerformanceCondition = "SQLServer:General Statistics|User Connections||>|3";  
  
            //Create the alert on the SQL Agent.   
            al.Create();  
  
            //Define an Operator object variable by supplying the SQL Server Agent and the name arguments in the constructor.   
  
            Operator op = new Operator(srv.JobServer, "Test_Operator");  
            //Set the net send address.   
            op.NetSendAddress = "NetworkPC";  
            //Create the operator on the SQL Agent.   
            op.Create();  
            //Run the AddNotification method to specify the operator is notified when the alert is raised.   
            al.AddNotification("Test_Operator", NotifyMethods.NetSend);  
        }  
```  
  
## <a name="creating-an-alert-in-powershell"></a>Erstellen einer Warnung in PowerShell  
 In diesem Codebeispiel wird eine Warnung erstellt, die von einer Leistungsbedingung ausgelöst wird. Die Bedingung muss in einem bestimmten Format bereitgestellt werden:  
  
 **ObjectName | CounterName | Instanz | Comparisionop | Compvalue**  
  
 Ein Operator ist für die Warnungsbenachrichtigung erforderlich. Für den <xref:Microsoft.SqlServer.Management.Smo.Agent.Operator>-Typ sind eckige Klammern erforderlich, da es sich bei `operator` um ein [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]-Schlüsselwort handelt.  
  
```powershell
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Define an Alert object variable by supplying the SQL Agent and the name arguments in the constructor.  
$al = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Agent.Alert -argumentlist $srv.JobServer, "Test_Alert"  
  
#Specify the performance condition string to define the alert.  
$al.PerformanceCondition = "SQLServer:General Statistics|User Connections||>|3"  
  
#Create the alert on the SQL Agent.  
$al.Create()  
  
#Define an Operator object variable by supplying the Agent (parent JobServer object) and the name in the constructor.  
$op = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Agent.Operator -argumentlist $srv.JobServer, "Test_Operator"  
  
#Set the Net send address.  
$op.NetSendAddress = "Network1_PC"  
  
#Create the operator on the instance of SQL Agent.  
$op.Create()  
  
#Run the AddNotification method to specify the operator is notified when the alert is raised.  
$ns = [Microsoft.SqlServer.Management.SMO.Agent.NotifyMethods]::NetSend  
$al.AddNotification("Test_Operator", $ns)  
  
#Drop the alert and the operator  
$al.Drop()  
$op.Drop()  
```  
  
## <a name="allowing-user-access-to-subsystem-by-using-a-proxy-account-in-visual-basic"></a>Zulassen des Benutzerzugriffs auf das Subsystem mit einem Proxykonto in Visual Basic  
 Dieses Codebeispiel zeigt, wie einem Benutzer der Zugriff auf ein festgelegtes Subsystem über die <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount.AddSubSystem%2A>-Methode des <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount>-Objekts gewährt wird.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBAgent2](SMO How to#SMO_VBAgent2)]  -->  
  
## <a name="allowing-user-access-to-subsystem-by-using-a-proxy-account-in-visual-c"></a>Zulassen des Benutzerzugriffs auf das Subsystem mit einem Proxykonto in Visual C#  
 Dieses Codebeispiel zeigt, wie einem Benutzer der Zugriff auf ein festgelegtes Subsystem über die <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount.AddSubSystem%2A>-Methode des <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount>-Objekts gewährt wird.  
  
```csharp
//Connect to the local, default instance of SQL Server.   
{   
Server srv = default(Server);   
srv = new Server();   
//Declare a JobServer object variable and reference the SQL Server Agent.   
JobServer js = default(JobServer);   
js = srv.JobServer;   
//Define a Credential object variable by supplying the parent server and name arguments in the constructor.   
Credential c = default(Credential);   
c = new Credential(srv, "Proxy_accnt");   
//Set the identity to a valid login represented by the vIdentity string variable.   
//The sub system will run under this login.   
c.Identity = vIdentity;   
//Create the credential on the instance of SQL Server.   
c.Create();   
//Define a ProxyAccount object variable by supplying the SQL Server Agent, the name, the credential, the description arguments in the constructor.   
ProxyAccount pa = default(ProxyAccount);   
pa = new ProxyAccount(js, "Test_proxy", "Proxy_accnt", true, "Proxy account for users to run job steps in command shell.");   
//Create the proxy account on the SQL Agent.   
pa.Create();   
//Add the login, represented by the vLogin string variable, to the proxy account.   
pa.AddLogin(vLogin);   
//Add the CmdExec subsytem to the proxy account.   
pa.AddSubSystem(AgentSubSystem.CmdExec);   
}   
//Now users logged on as vLogin can run CmdExec job steps with the specified credentials.   
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-Agent](../../../ssms/agent/sql-server-agent.md)   
 [Implementieren von Aufträgen](../../../ssms/agent/implement-jobs.md)  
