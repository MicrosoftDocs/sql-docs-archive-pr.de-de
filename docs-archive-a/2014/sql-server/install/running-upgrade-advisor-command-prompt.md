---
title: Ausführen des Upgrade Advisors (Eingabeaufforderung) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor [SQL Server], running
- command prompt [Upgrade Advisor]
- UpgradeAdvisorWizardCmd utility
- XML formats [Upgrade Advisor]
ms.assetid: 7c83049b-9227-4723-9b7f-66288bc6bd1d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a968f9d70788e1100af263f3ef9947493b4bd0c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608228"
---
# <a name="running-upgrade-advisor-command-prompt"></a>Ausführen des Upgrade Advisors (Eingabeaufforderung)
  Verwenden Sie das Hilfsprogramm **upgradeadvisorwizardcmd** , um den Upgrade Advisor von der Eingabeaufforderung auszuführen. Sie können wählen, ob die Ergebnisse im XML-Format oder als Datei mit durch Trennzeichen getrennten Werten ausgegeben werden sollen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      UpgradeAdvisorWizardCmd [ -? ]  |   
    [ -ConfigFilefilename | <server_info> ]  
    [ -SqlUserlogin_id-SqlPasswordpassword ]  
    [ -CSV ]  
  
where <server_info> is any combination of the following:  
        -Serverserver_name-Instanceinstance_name-ASInstanceAS_instance_name-RSInstanceRS_instance_name  
```  
  
## <a name="arguments"></a>Argumente  
 **-?**  
 Zeigt die Befehlssyntax an.  
  
 **-Configfile Dateiname** _filename_  
 Der Pfadname und der Dateiname einer XML-Datei, die Einstellungen enthält, die beim Ausführen des Hilfsprogramms **upgradeadvisorwizardcmd** verwendet werden sollen.  
  
 *<server_info>*  
 Gibt an, welcher Computer und welche Instanz analysiert werden sollen. Verwenden Sie diese Optionen, wenn Sie keine Konfigurationsdatei verwenden.  
  
 *<server_info>* kann eine beliebige Kombination der folgenden vier Argumente sein:  
  
 **-Server** _server_name_  
 Gibt den Namen des zu analysierenden Computers an. Dabei kann es sich um den lokalen Computer (Standardwert) oder einen Remotecomputer handeln.  
  
 **-Instanz** _instance_name_  
 Gibt den Namen der zu analysierenden Instanz an. Es gibt keinen Standardwert. Wenn Sie diesen Parameter nicht angeben, wird das [!INCLUDE[ssDE](../../includes/ssde-md.md)] nicht gescannt. Der Wert für eine Standardinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist MSSQLSERVER. Verwenden Sie für eine benannte Instanz den Namen der Instanz.  
  
 **-Asinstance**  _AS_instance_name_  
 Gibt den Namen der zu analysierenden [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanz an. Es gibt keinen Standardwert. Wenn Sie diesen Wert nicht angeben, wird [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] nicht gescannt. Der Wert für eine Standardinstanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] lautet MSSQLServerOLAPService. Verwenden Sie für eine benannte Instanz den Namen der Instanz.  
  
 **-Rsinstance**  _RS_instance_name_  
 Gibt den Namen der zu analysierenden [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Instanz an. Es gibt keinen Standardwert. Wenn Sie diesen Wert nicht angeben, wird [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nicht gescannt. Der Wert für eine Standardinstanz von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ist ReportServer. Verwenden Sie für eine benannte Instanz den Namen der Instanz.  
  
 **-SQLUser** _login_id_  
 Wenn Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung verwenden, ist dieser Wert die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldung, die der Upgrade Advisor dazu verwendet, die Verbindung mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herzustellen. Wenn Sie keine Anmeldung angeben, wird die Windows-Authentifizierung verwendet, um eine Verbindung mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz herzustellen.  
  
 **-Sqlpassword** _Kennwort_  
 Wenn Sie das Argument **-SQLUser** verwenden, verwenden Sie dieses Argument, um das Kennwort für den Anmelde Namen anzugeben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **-CSV**  
 Gibt an, dass die Ergebnisse zusätzlich zu den XML-Standardergebnissen als durch Trennzeichen getrennte Werte in einer CSV-Datei ausgegeben werden. Die Ergebnisse werden in den Ordner Meine Dokumente \\ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Upgrade advisor\110\reports geschrieben.  
  
## <a name="return-values"></a>Rückgabewerte  
 In der folgenden Tabelle sind die Werte aufgeführt, die von " **upgradebug advisorwizardcmd** " zurückgegeben werden  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|0|Die Analyse war erfolgreich, keine Upgradeprobleme gefunden.|  
|Positive Ganzzahl|Die Analyse war erfolgreich, es wurden Upgradeprobleme gefunden.|  
|Negative Ganzzahl|Die Analyse ist fehlgeschlagen.|  
  
## <a name="remarks"></a>Bemerkungen  
 Alle Informationen, die zur Ausführung der Analyse erforderlich sind, mit Ausnahme der Benutzernamen und Kennwörter für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung, können in einer XML-Konfigurationsdatei bereitgestellt werden. Diese XML-Konfigurationsdatei wird in der Vorlage dokumentiert. Wenn Sie keine Konfigurationsdatei verwenden, können Sie alle installierten Komponenten in einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] analysieren. Verwenden Sie hierzu die Standardeinstellungen, indem Sie die Computer- und Instanznamen angeben. Eine Beschreibung der Standardeinstellungen der Konfigurationsdatei finden Sie in der Tabelle "Elementbeschreibungen" weiter unten in diesem Thema.  
  
## <a name="configuration-file-template"></a>Konfigurationsdateivorlage  
 Verwenden Sie den folgenden XML-Code als Vorlage für die Erstellung Ihrer eigenen Konfigurationsdateien. Sie können die Vorlage ändern, um den Anforderungen Ihrer Organisation Rechnung zu tragen.  
  
```xml  
<Configuration>  
    <Server> </Server>  
    <Instance></Instance>  
    <Components>  
        <SQLServer>  
            <Databases>  
                <Database></Database>  
            </Databases>  
            <TraceFiles>  
                <TraceFile></TraceFile>  
            </TraceFiles>  
            <BatchFiles>  
                <BatchFile></BatchFile>  
            </BatchFiles>  
            <BatchSeparator></BatchSeparator>  
        </SQLServer>  
        <AnalysisServices>  
            <ASInstance></ASInstance>  
            <Databases>  
                <Database></Database>  
            </Databases>  
        </AnalysisServices>  
        <ReportingServices>  
            <RSInstance></RSInstance>  
        </ReportingServices>  
        <IntegrationServices>  
            <PackagePath></PackagePath>  
        </IntegrationServices>  
    </Components>  
</Configuration>  
```  
  
## <a name="element-descriptions"></a>Element Beschreibungen  
  
|Tag|Definition|Vorkommen|  
|---------|----------------|----------------|  
|`Configuration`|Übergeordnetes Element für die Konfigurationsdatei des Upgrade Advisors.|Ist einmal pro Konfigurationsdatei erforderlich.|  
|`Server`|Der Name des zu analysierenden Servers.|Optional einmal pro Konfigurationsdatei. Der Standardwert ist der lokale Computer.|  
|`Instance`|Name der zu analysierenden [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz.|Optional einmal pro Konfigurationsdatei. Der Standardwert ist die Standardinstanz.<br /><br /> Erforderlich einmal pro Konfigurationsdatei, wenn ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Element oder ein `IntegrationServices`-Element auf dem Server vorhanden ist.|  
|`Components`|Enthält Elemente, die angeben, welche Komponenten analysiert werden sollen.|Ist einmal pro Konfigurationsdatei erforderlich.|  
|`SQLServer`|Enthält Analyseeinstellungen für eine [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz.|Optional einmal pro Konfigurationsdatei. Wenn das Element nicht angegeben ist, werden [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Datenbanken nicht analysiert.|  
|`Databases` für `SQLServer`-Element|Enthält eine Liste der zu analysierenden Datenbanken.|Optional einmal pro `SQLServer` Element. Wenn dieses Element nicht vorhanden ist, werden alle Datenbanken in der Instanz analysiert.|  
|`Database` für `SQLServer`-Element|Gibt den Namen einer zu analysierenden Datenbank an.|Einmal erforderlich, oder mehrmals, wenn das `Databases`-Element vorhanden ist. Wenn ein `Database`-Element den Wert "*" enthält, werden alle Datenbanken in der Instanz analysiert. Es gibt keinen Standardwert.|  
|`TraceFiles`|Enthält eine Liste der zu analysierenden Ablaufverfolgungsdateien.|Optional einmal pro `SQLServer` Element.|  
|`TraceFile`|Gibt den Pfad und Namen einer zu analysierenden Ablaufverfolgungsdatei an.|Einmal erforderlich, oder mehrmals, wenn das `TraceFiles`-Element vorhanden ist. Es gibt keinen Standardwert.|  
|`BatchFiles`|Enthält eine Liste der zu analysierenden Batchdateien.|Optional einmal pro `SQLServer` Element.|  
|`BatchFile`|Gibt eine zu analysierende Batchdatei an. Kann mehrfach vorkommen.|Einmal erforderlich, oder mehrmals, wenn das `BatchFiles`-Element vorhanden ist. Es gibt keinen Standardwert.|  
|`BatchSeparator`|Gibt das in den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Batchdateien verwendete Batchtrennzeichen an.|Optional einmal pro `SQLServer` Element. Der Standardwert ist GO.|  
|`AnalysisServices`|Enthält Analyseeinstellungen für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|Optional einmal pro Konfigurationsdatei. Wenn das Element nicht angegeben ist, werden [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Datenbanken nicht analysiert.|  
|`ASInstance`|Gibt den Namen einer Instanz von an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|Einmal pro `AnalysisServices`-Element erforderlich. Es gibt keinen Standardwert.|  
|`Databases` für `Analysis Services`-Element|Enthält eine Liste der zu analysierenden Datenbanken.|Optional einmal pro `AnalysisServices` Element. Wenn dieses Element nicht vorhanden ist, werden alle Datenbanken in der Instanz analysiert.|  
|`Database` für `AnalysisServices`-Element|Gibt den Namen einer zu analysierenden Datenbank an.|Einmal erforderlich, oder mehrmals, wenn das `Databases`-Element vorhanden ist. Wenn ein `Database`-Element den Wert "*" enthält, werden alle Datenbanken in der Instanz analysiert. Es gibt keinen Standardwert.|  
|`ReportingServices`|Gibt an, dass eine Analyse für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ausgeführt wird.|Optional einmal pro Konfigurationsdatei. Wenn dieses Element nicht angegeben ist, wird [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nicht analysiert.|  
|`RSInstance`|Gibt den Namen einer Instanz von an [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|Einmal pro `ReportingServices`-Element erforderlich. Es gibt keinen Standardwert.|  
|`IntegrationServices`|Enthält Analyseeinstellungen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].|Optional einmal pro Konfigurationsdatei. Wenn dieses Element nicht angegeben ist, wird [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] nicht analysiert.|  
|`PackagePath`|Gibt den Pfad eines Satzes von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Paketen an.|Optional einmal pro `IntegrationServices` Element. Wenn dieses Element nicht vorhanden ist, erfolgt die Analyse auf der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, und es werden keine extern gespeicherten Pakete analysiert. Es gibt keinen Standardwert.|  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-run-upgrade-advisor-using-a-configuration-file"></a>A. Ausführen des Upgrade Advisors mit einer Konfigurationsdatei  
 Im folgenden Beispiel wird gezeigt, wie der Upgrade Advisor von der Eingabeaufforderung mit einer Konfigurationsdatei ausgeführt wird, die angibt, was analysiert werden soll. In diesem Beispiel wird die Windows-Authentifizierung verwendet, um eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herzustellen.  
  
```  
UpgradeAdvisorWizardCmd -ConfigFile "C:\My Documents\UpgradeConfig1.xml"  
```  
  
### <a name="b-run-upgrade-advisor-using-default-configuration-settings"></a>B. Ausführen des Upgrade Advisors mit Standardkonfigurationseinstellungen  
 Das folgende Beispiel zeigt, wie der Upgrade Advisor anhand von Standardkonfigurationseinstellungen und der Windows-Authentifizierung von der Eingabeaufforderung ausgeführt wird.  
  
```  
UpgradeAdvisorWizardCmd -Server MyServer -Instance MyInst   
```  
  
### <a name="c-run-upgrade-advisor-using-ssnoversion-authentication"></a>C. Ausführen des Upgrade Advisors mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung  
 Im folgenden Beispiel wird gezeigt, wie der Upgrade Advisor von der Eingabeaufforderung aus mithilfe einer Konfigurationsdatei ausgeführt wird. In diesem Beispiel werden ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Benutzername und ein Kennwort angegeben, um eine Verbindung mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herzustellen.  
  
```  
UpgradeAdvisorWizardCmd -ConfigFile "C:\My Documents\UpgradeConfig1.xml"   
    -SqlUser "MyUserName" -SqlPassword "QweRTy-55"  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beheben von Upgradeproblemen](../../../2014/sql-server/install/resolving-upgrade-issues.md)   
 [Arbeiten mit Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [Ausführen des Upgrade Advisors &#40;Benutzeroberfläche&#41;](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md)  
  
  
