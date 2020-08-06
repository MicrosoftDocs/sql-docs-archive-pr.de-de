---
title: ReportingServicesService-Konfigurationsdatei | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- traces [Reporting Services]
- Report Server Windows service, ReportingServicesService configuration file
- ReportingServicesService configuration file
ms.assetid: 40f4a401-cb61-4c42-b1ec-01acdacdacd1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5124631db9635211827dd3b1abbff7116101a61d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87618487"
---
# <a name="reportingservicesservice-configuration-file"></a>ReportingServicesService-Konfigurationsdatei
  Die Datei ReportingServicesService.exe.config enthält Einstellungen zum Konfigurieren der Ablaufverfolgung.  
  
## <a name="file-location"></a>Dateispeicherort  
 Diese Datei ist im Ordner \Reporting Services\Report Server\Bin gespeichert.  
  
## <a name="editing-guidelines"></a>Bearbeitungsrichtlinien  
 Sie können diese Datei ändern, um die Protokolldatei umzubenennen oder die Ablaufverfolgungsebenen zu erhöhen bzw. zu senken. Ändern Sie ansonsten keine anderen Einstellungen. Weitere Informationen finden Sie unter [Ändern einer Reporting Services-Konfigurationsdatei („RSreportserver.config“)](modify-a-reporting-services-configuration-file-rsreportserver-config.md). Weitere Informationen zu Ablaufverfolgungsprotokollen finden Sie unter [Berichtsserverdienst-Ablaufverfolgungsprotokoll](report-server-service-trace-log.md).  
  
## <a name="example-configuration"></a>Beispielkonfiguration  
 Das folgende Beispiel zeigt die Einstellungen und Standardwerte, die in der Datei ReportingServicesService.exe.config gefunden wurden.  
  
```  
<configSections>  
      <section name="RStrace" type="Microsoft.ReportingServices.Diagnostics.RSTraceSectionHandler,Microsoft.ReportingServices.Diagnostics" />  
</configSections>  
<system.diagnostics>  
      <switches>  
          <add name="DefaultTraceSwitch" value="3" />  
      </switches>  
</system.diagnostics>  
<RStrace>  
      <add name="FileName" value="ReportServerService_" />  
      <add name="FileSizeLimitMb" value="32" />  
      <add name="KeepFilesForDays" value="14" />  
      <add name="Prefix" value="tid, time" />  
      <add name="TraceListeners" value="debugwindow, file" />  
      <add name="TraceFileMode" value="unique" />  
      <add name="Components" value="all" />  
</RStrace>  
<runtime>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
             <dependentAssembly>  
                    <assemblyIdentity name="Microsoft.ReportingServices.Interfaces"  
                        publicKeyToken="89845dcd8080cc91"  
                        culture="neutral" />  
                    <bindingRedirect oldVersion="8.0.242.0"  
                                     newVersion="10.0.0.0"/>  
                    <bindingRedirect oldVersion="9.0.242.0"  
                                     newVersion="10.0.0.0"/>  
             </dependentAssembly>  
      </assemblyBinding>  
      <gcServer enabled="true" />  
</runtime>  
```  
  
## <a name="configuration-settings"></a>Konfigurationseinstellungen  
 Die folgende Tabelle enthält Informationen zu bestimmten Einstellungen. Diese Einstellungen werden in der Reihenfolge aufgeführt, in der sie in der Konfigurationsdatei angezeigt werden.  
  
|Einstellung|BESCHREIBUNG|  
|-------------|-----------------|  
|**RStrace**|Gibt Namespaces an, die für Fehler und für die Ablaufverfolgung verwendet werden.|  
|**DefaultTraceSwitch**|Gibt die Ebene der Informationen an, die im Ablaufverfolgungsprotokoll ReportServerService aufgezeichnet werden. Jede Ebene enthält jeweils die Informationen aller niedrigerer Ebenen. Das Deaktivieren der Ablaufverfolgung wird nicht empfohlen. Gültige Werte:<br /><br /> 0= Deaktiviert die Ablaufverfolgung<br /><br /> 1= Ausnahmen und Neustarts<br /><br /> 2= Ausnahmen, Neustarts, Warnungen<br /><br /> 3= Ausnahmen, Neustarts, Warnungen, Statusmeldungen (Standard)<br /><br /> 4= Ausführlicher Modus|  
|**FileName**|Gibt den ersten Teil des Protokolldateinamens an. Der Wert von `Prefix` ergänzt den restlichen Namen. Standardmäßig lautet der Name ReportServerService_.|  
|**FileSizeLimitMb**|Gibt eine Obergrenze für die Größe des Ablaufverfolgungsprotokolls an. Die Datei wird in Megabytes gemessen. Gültige Werte sind 0 bis zu einer maximalen ganzen Zahl. Der Standardwert ist 32.|  
|**KeepFilesForDays**|Gibt die Anzahl von Tagen an, nach der eine Ablaufverfolgungs-Protokolldatei gelöscht wird. Gültige Werte sind 0 bis zu einer maximalen ganzen Zahl. Der Standardwert ist 14.|  
|`Prefix`|Gibt einen generierten Wert an, der die Protokollinstanzen voneinander unterscheidet. Standardmäßig werden Timestampwerte an die Dateinamen von Ablaufverfolgungsprotokollen angehängt. Dieser Wert wird auf "tid, time " festgelegt. Ändern Sie diese Einstellung nicht.|  
|**TraceListeners**|Gibt die Zieladresse für die Ausgabe des Inhalts von Ablaufverfolgungsprotokollen an. Sie können mehrere durch Trennzeichen getrennte Ziele angeben. Gültige Werte:<br /><br /> DebugWindow (Standard)<br /><br /> File (Standard)<br /><br /> StdOut|  
|**TraceFileMode**|Gibt an, ob Ablaufverfolgungsprotokolle Daten für einen Zeitraum von 24 Stunden enthalten. Für jede Komponente sollte pro Tag ein eindeutiges Ablaufverfolgungsprotokoll erstellt werden. Dieser Wert wird auf "Unique (Standard)" festgelegt. Ändern Sie diesen Wert nicht.|  
|**Komponenten**|Gibt die Komponenten an, für die Ablaufverfolgungsprotokolle erstellt werden. Standardwert: `all`. Ebenfalls gültige Werte für diese Einstellung sind die Namen interner Komponenten. Ändern Sie diesen Wert nicht.|  
|**Runtime**|Gibt Konfigurationseinstellungen an, die die Abwärtskompatibilität mit der früheren Version unterstützen. Mit den Runtime-Einstellungen werden Anforderungen, die an die frühere Version von Microsoft.ReportingServices.Interfaces gerichtet sind, an die neue Version umgeleitet.<br /><br /> Alle Konfigurationseinstellungen in diesem Abschnitt sind in der Produktdokumentation zu [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] beschrieben. Weitere Informationen finden Sie, indem Sie auf der MSDN-Website oder in der Dokumentation von [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] nach Informationen zum Schema für Laufzeiteinstellungen ("Runtime Schema Settings") suchen.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Reporting Services-Konfigurationsdateien](reporting-services-configuration-files.md)   
 [Berichtsserverdienst-Ablaufverfolgungsprotokoll](report-server-service-trace-log.md)  
  
  
