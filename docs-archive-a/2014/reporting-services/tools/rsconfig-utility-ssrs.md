---
title: rsconfig-Hilfsprogramm (SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- connections [Reporting Services], configuring
- rsconfig utility
- report servers [Reporting Services], connections
- command prompt utilities [Reporting Services]
- command prompt utilities [SQL Server], rsconfig
ms.assetid: 84e45a2f-3ca6-4c16-8259-c15ff49d72ad
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 499fa5529991b36e467567b4c7006845dfcd2578
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721037"
---
# <a name="rsconfig-utility-ssrs"></a>rsconfig-Hilfsprogramm (SSRS)
  Mit dem Hilfsprogramm **rsconfig.exe** werden Verbindungs- und Kontowerte in der Datei „RSReportServer.config“ verschlüsselt und gespeichert. Die verschlüsselten Werte umfassen Verbindungsinformationen für Berichtsserver-Datenbanken und Kontowerte, die für die unbeaufsichtigte Berichtsverarbeitung verwendet werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      rsconfig {-?}  
{-cconnection}  
{-eunattendedaccount}  
{-mcomputername}  
{-iinstancename}  
{-sservername}  
{-ddatabasename}  
{-aauthmethod}  
{-uusername}  
{-ppassword}  
{-ttrace}  
```  
  
## <a name="arguments"></a>Argumente  
  
|Begriff|Optional/erforderlich|Definition|  
|----------|------------------------|----------------|  
|**-?**|Optional.|Zeigt die Syntax der Argumente von Rsconfig.exe an.|  
|`-c`|Erforderlich, wenn `-e` nicht verwendet wird.|Gibt die Verbindungszeichenfolge, die Anmeldeinformationen und die Datenquellenwerte an, die verwendet werden, um die Verbindung zwischen einem Berichtsserver und der Berichtsserver-Datenbank herzustellen.<br /><br /> Dieses Argument enthält keinen Wert. Es müssen jedoch weitere Argumente angegeben werden, um alle erforderlichen Verbindungswerte für dieses Argument bereitzustellen.<br /><br /> Zu den Argumenten, die Sie mit angeben können `-c` `-m` , gehören, **-s**, `-i` ,,,, `-d` `-a` `-u` `-p` und `-t` .|  
|`-e`|Erforderlich, wenn `-c` nicht verwendet wird.|Gibt das Konto für die unbeaufsichtigte Berichtsausführung an.<br /><br /> Dieses Argument enthält keinen Wert. Sie müssen jedoch zusätzliche Argumente in der Befehlszeile einschließen, um die in der Konfigurationsdatei verschlüsselten Werte anzugeben.<br /><br /> Zu den Argumenten, die Sie mit `-e` angeben können, gehören `-u` und `-p`. Darüber hinaus können Sie `-t` festlegen.|  
|`-m`  *Computername*|Erforderlich, wenn Sie eine Remote-Berichtsserverinstanz konfigurieren.|Gibt den Namen des Computers an, der den Berichtsserver hostet. Wird dieses Argument nicht angegeben, wird der Standardwert `localhost` verwendet.|  
|**-s**  *servername*|Erforderlich.|Gibt die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz an, die die Berichtsserver-Datenbank hostet.|  
|`-i`  *InstanceName*|Erforderlich, wenn Sie benannte Instanzen verwenden.|Wenn Sie eine benannte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz zum Hosten der Berichtsserver-Datenbank verwenden, gibt dieser Wert die benannte Instanz an.|  
|`-d`  *DatabaseName*|Erforderlich.|Gibt den Namen der Berichtsserver-Datenbank an.|  
|`-a`  *authmethod*|Erforderlich.|Gibt die Authentifizierungsmethode an, die vom Berichtsserver zum Herstellen der Verbindung mit der Berichtsserver-Datenbank verwendet wird. Gültige Werte sind `Windows` oder `SQL` (die Groß- und Kleinschreibung wird bei diesem Argument nicht beachtet).<br /><br /> `Windows` gibt an, dass der Berichtsserver die Windows-Authentifizierung verwendet.<br /><br /> `SQL` gibt an, dass der Berichtsserver die SQL Server-Authentifizierung verwendet.|  
|`-u`  *[Domäne \\ ] User*|Erforderlich, wenn `-e` verwendet wird; optional, wenn `-c` angegeben wird.|Gibt ein Benutzerkonto für die Verbindung mit der Berichtsserver-Datenbank oder für ein Konto für unbeaufsichtigte Vorgänge an.<br /><br /> Bei Angabe von **rsconfig -e**ist dieses Argument erforderlich. Es muss ein Domänenbenutzerkonto sein.<br /><br /> Bei **rsconfig-c** und `-a SQL` muss dieses Argument einen Anmelde Namen angeben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br /><br /> Bei **rsconfig-c** und `-a Windows` kann dieses Argument einen Domänen Benutzer, ein integriertes Konto oder Anmelde Informationen für das Dienst Konto angeben. Wenn Sie ein Domänenkonto angeben, geben Sie *Domäne* und *Benutzername* im Format *Domäne\Benutzername*an. Wenn Sie ein integriertes Konto verwenden, ist dieses Argument optional. Wenn Sie die Anmeldeinformationen für ein Dienstkonto verwenden möchten, geben Sie dieses Argument nicht an.|  
|`-p`  *password*|Erforderlich, wenn `-u` angegeben wird.|Gibt das Kennwort an, das mit dem *Benutzername* -Argument verwendet wird. Sie können für dieses Argument einen leeren Wert festlegen, falls für das Konto kein Kennwort erforderlich ist. Bei Domänenkonten wird bei diesem Wert die Groß- und Kleinschreibung beachtet.|  
|`-t`|Optional.|Schreibt Fehlermeldungen in das Ablaufverfolgungsprotokoll. Dieses Argument enthält keinen Wert. Weitere Informationen finden Sie unter [Report Server Service Trace Log](../report-server/report-server-service-trace-log.md).|  
  
## <a name="permissions"></a>Berechtigungen  
 Auf dem Computer, der den von Ihnen konfigurierten Berichtsserver hostet, müssen Sie als lokaler Administrator angemeldet sein.  
  
## <a name="file-location"></a>Dateispeicherort  
 „Rsconfig.exe“ befindet sich unter **\Programme\Microsoft SQL Server\110\Tools\Binn**. Sie können das Hilfsprogramm von einem beliebigen Ordner im Dateisystem ausführen.  
  
## <a name="remarks"></a>Bemerkungen  
 Es gibt zwei Gründe für die Verwendung von Rsconfig.exe:  
  
-   Ändern der Verbindungsinformationen, die ein Berichtsserver für die Verbindung mit einer Berichtsserver-Datenbank verwendet.  
  
-   Konfiguration eines besonderen Kontos, das der Berichtsserver für die Anmeldung an einem Remote-Datenbankserver verwendet, wenn keine anderen Anmeldeinformationen verfügbar sind.  
  
 Sie können das Hilfsprogramm**rsconfig** auf einer lokalen Instanz oder auf einer Remoteinstanz von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ausführen. Sie können das Hilfsprogramm **rsconfig** nicht verwenden, um bereits festgelegte Werte zu entschlüsseln oder anzuzeigen.  
  
 Bevor Sie dieses Hilfsprogramm ausführen, müssen Sie die Windows-Verwaltungsinstrumentation (Windows Management Instrumentation, WMI) auf dem Computer installieren, den Sie konfigurieren.  
  
## <a name="examples"></a>Beispiele  
 Die folgenden Beispiele veranschaulichen mögliche Verwendungsweisen von **rsconfig**.  
  
#### <a name="specifying-a-domain-user-account"></a>Angeben eines Domänenbenutzerkontos  
 In diesem Beispiel wird gezeigt, wie ein Berichtsserver so konfiguriert wird, dass er ein Domänenbenutzerkonto für die Verbindung mit einer lokalen Berichtsserver-Datenbank verwendet.  
  
```  
rsconfig -c -s <SQLSERVERNAME> -d reportserver -a Windows -u <MYDOMAIN\MYACCOUNT> -p <PASSWORD>  
```  
  
#### <a name="specifying-a-sql-server-database-user-account"></a>Angeben eines Benutzerkontos für eine SQL Server-Datenbank  
 In diesem Beispiel wird gezeigt, wie ein Berichtsserver so konfiguriert wird, dass er einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldenamen für die Verbindung mit einer Datenbank auf einem Remoteberichtsserver verwendet.  
  
```  
rsconfig -c -m <REMOTECOMPUTERNAME> -s <SQLSERVERNAME> -d reportserver -a SQL -u SA -p <SAPASSWORD>  
```  
  
#### <a name="specifying-a-built-in-account"></a>Angeben eines integrierten Kontos  
 In diesem Beispiel wird gezeigt, wie ein Berichtsserver so konfiguriert wird, dass er ein integriertes Konto für die Verbindung mit einer lokalen Berichtsserver-Datenbank verwendet. Beachten Sie, dass `-u` nicht verwendet wird. Beispiele für unterstützte integrierte Konto Werte sind NT-Autorität \ System für lokales System und NT-Autorität \ Network Service for Network Service ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] nur).  
  
```  
rsconfig -c -s <SQLSERVERNAME> -d reportserver -a Windows "NT AUTHORITY\SYSTEM"  
```  
  
#### <a name="specifying-a-service-account"></a>Angeben eines Dienstkontos  
 In diesem Beispiel wird gezeigt, wie ein Berichtsserver so konfiguriert wird, dass er das Windows-Dienstkonto und das Webdienstkonto für den Berichtsserver verwendet, um eine Verbindung mit einer lokalen Berichtsserver-Datenbank herzustellen. Beachten Sie, dass `-u` nicht verwendet wird und dass keine Kontoinformationen angegeben werden. Wenn Sie Kontowerte aus dem Befehl ausschließen, verwendet das Hilfsprogramm **rsconfig** die integrierte Sicherheit und das Dienstkonto, unter dem der jeweilige Dienst ausgeführt wird.  
  
```  
rsconfig -c -s <SQLSERVERNAME> -d reportserver -a Windows  
```  
  
#### <a name="specifying-the-unattended-account-on-a-local-server"></a>Angeben des Kontos für unbeaufsichtigte Vorgänge auf einem lokalen Server  
 In diesem Beispiel wird gezeigt, wie das Konto, das für die unbeaufsichtigte Berichtsausführung verwendet wird, für Berichte konfiguriert wird, die keine Anmeldeinformationen für die externe Datenquelle übergeben. Bei dem Konto muss es sich um ein Windows-Domänenkonto handeln. Es ist nicht möglich, einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldenamen für den Benutzernamen und das Kennwort anzugeben. Das Konto wird auf einer lokalen Berichtsserverinstanz konfiguriert. Fehlermeldungen werden in den Ablaufverfolgungsprotokollen im Ordner ReportingServices\LogFiles erfasst.  
  
```  
rsconfig -e -u <DOMAIN\ACCOUNT> -p <PASSWORD> -t  
```  
  
#### <a name="specifying-the-unattended-account-on-a-remote-server"></a>Angeben des Kontos für unbeaufsichtigte Vorgänge auf einem Remoteserver  
 In diesem Beispiel wird veranschaulicht, wie das Konto auf einer Remote-Berichtsserverinstanz konfiguriert wird, die dieselbe Version wie Rsconfig.exe aufweist (z. B. wenn sowohl Berichtsserver als auch Rsconfig.exe aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 R2 stammen). Fehlermeldungen werden in den Ablaufverfolgungsprotokollen auf dem Remoteserver erfasst.  
  
```  
rsconfig -e -m <REMOTECOMPUTERNAME> -s <SQLSERVERNAME> -u <DOMAIN\ACCOUNT> -p <PASSWORD> -t  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren einer Verbindung mit der Berichts Server-Datenbank &#40;SSRS-Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
 [Konfigurieren des Kontos für die unbeaufsichtigte Ausführung &#40;SSRS-Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)   
 [Reporting Services-Berichtsserver &#40;einheitlicher Modus&#41;](../report-server/reporting-services-report-server-native-mode.md)   
 [SSRS-Verschlüsselungsschlüssel: Speichern verschlüsselter Berichtsserverdaten](../install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md)   
 [Reporting Services-Konfigurationsdateien](../report-server/reporting-services-configuration-files.md)   
 [Eingabeaufforderungs-Hilfsprogramme für Berichts Server &#40;SSRS&#41;](report-server-command-prompt-utilities-ssrs.md)   
 [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md)  
  
  
