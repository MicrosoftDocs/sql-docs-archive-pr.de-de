---
title: Bereitstellen einer benutzerdefinierten Assembly | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- deploying custom assemblies [Reporting Services]
- custom assemblies [Reporting Services], deploying
- custom assemblies [Reporting Services], updating
- updating custom assemblies
ms.assetid: c6674cd8-0de7-4a5a-9e7c-12ffa49f6fd2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3d88e1db844304b5cbb51f4af52b4715ef7e8c1e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87725318"
---
# <a name="deploying-a-custom-assembly"></a>Bereitstellen einer benutzerdefinierten Assembly
  Um eine benutzerdefinierte Assembly in bereitzustellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , platzieren Sie die Assembly in den Anwendungs Ordnern von Berichts-Designer und dem Berichts Server. Standardmäßig wird benutzerdefinierten Assemblys die `Execution`-Berechtigung in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] erteilt. Sie müssen die Konfigurationsdatei „rssrvpolicy.config“ für den Berichtsserver und die Konfigurationsdatei „rspreviewpolicy.config“ für das Vorschaufenster des Berichts-Designers bearbeiten, um benutzerdefinierten Assemblys Privilegien über die Execute-Berechtigung hinaus zu erteilen. Alternativ dazu können Sie die benutzerdefinierte Assembly auch im globalen Assemblycache (Global Assembly Cache, GAC) installieren.  
  
> [!NOTE]  
>  Es stehen zwei Vorschaumodi für den Berichts-Designer zur Verfügung: die Vorschauregisterkarte und das Popup-Vorschaufenster, das beim Start des Berichtsprojekts im `DebugLocal` aufgerufen wird. Die Vorschauregisterkarte führt alle Berichtsausdrücke mithilfe des `FullTrust`-Berechtigungssatzes aus und wendet keine Sicherheitsrichtlinieneinstellungen an. Im Popup-Vorschaufenster sollen die Berichtsserverfunktionen simuliert werden. Es enthält daher eine Richtlinienkonfigurationsdatei, die von Ihnen oder einem Administrator verändert werden muss, damit benutzerdefinierte Assemblys im Berichts-Designer verwendet werden können. Diese automatische Vorschau sperrt auch die benutzerdefinierte Assembly. Daher müssen Sie das Vorschaufenster schließen, um den Code der benutzerdefinierten Assembly ändern oder aktualisieren zu können.  
  
###### <a name="to-deploy-a-custom-assembly-in-reporting-services"></a>So stellen Sie benutzerdefinierte Assemblys in Reporting Services bereit  
  
1.  Kopieren Sie die benutzerdefinierte Assembly aus dem Build-Verzeichnis in das BIN-Verzeichnis des Berichtsservers oder in den Ordner des Berichts-Designers. Standardmäßig wird das BIN-Verzeichnis des Berichtsservers unter dem Pfad %ProgramFiles%\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin gespeichert. Das Standardverzeichnis für den Berichts-Designer ist %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.  
  
     Wenn Sie Ihre benutzerdefinierte Assembly im BIN-Ordner des Berichtsservers speichern, können Sie Berichte veröffentlichen, die auf die benutzerdefinierte Assembly verweisen. Wenn Sie die Assembly im Ordner des Berichts-Designers speichern, können Sie im Berichts-Designer Berichte ausführen und debuggen, die auf die benutzerdefinierte Assembly verweisen.  
  
     Wenn Sie dem Code der benutzerdefinierten Assembly Berechtigungen erteilen möchten, die über die Standardausführung hinausgehen, gehen Sie wie folgt vor:  
  
2.  Öffnen Sie die entsprechende Konfigurationsdatei. Das Standardverzeichnis von rssrvpolicy.config ist das Verzeichnis %ProgramFiles%\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer. Das Standardverzeichnis der Datei rspreviewpolicy.config ist das Verzeichnis %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.  
  
3.  Fügen Sie eine Codegruppe für die benutzerdefinierte Assembly hinzu. Weitere Informationen finden Sie unter [Sichere Entwicklung (Reporting Services)](../extensions/secure-development/secure-development-reporting-services.md).  
  
## <a name="updating-custom-assemblies"></a>Aktualisieren von benutzerdefinierten Assemblys  
 Irgendwann kann es sein, dass Sie eine Version einer benutzerdefinierten Assembly aktualisieren müssen, auf die derzeit diverse veröffentlichten Berichte verweisen. Wenn die Assembly bereits im Bin-Verzeichnis des Berichtsservers oder des Berichts-Designers vorhanden ist und die Versionsnummer der Assembly erhöht oder geändert wird, funktionieren die aktuell veröffentlichten Berichte nicht mehr ordnungsgemäß. Sie müssen die Version der Assembly, auf die im `CodeModules`-Element der Berichtsdefinition verwiesen wird, aktualisieren und die Berichte erneut veröffentlichen. Wenn Sie wissen, dass Sie eine benutzerdefinierte Assembly häufig aktualisieren müssen und wenn Ihre derzeit veröffentlichten Berichte auf die neue Assembly verweisen müssen, sollten Sie überlegen, ob es nicht besser ist, dieselbe Versionsnummer in allen Updates einer bestimmten Assembly zu verwenden.  
  
 Wenn in den derzeit veröffentlichten Berichten nicht auf die neue Versionsnummer verwiesen werden muss, können Sie die benutzerdefinierte Assembly im globalen Assemblycache bereitstellen. Im globalen Assemblycache können mehrere Versionen derselben Assembly verwaltet werden, sodass aktuelle Berichte auf frühere Versionen der Assembly und neu veröffentliche Berichte auf die aktualisierte Assembly verweisen können. Ein weiteres Konzept wäre es, die bindende Umleitung des Berichtsservers so einzustellen, dass eine Umleitung aller Anforderungen für die alte Assembly zur neuen Assembly durchgesetzt würde. Sie müssten dann die Berichtsserver-Dateien Web.config und ReportService.exe.config ändern. Der Eintrag könnte folgendermaßen aussehen:  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden benutzerdefinierter Assemblys mit Berichten](using-custom-assemblies-with-reports.md)   
 [Arbeiten mit Assemblys und dem globalen Assemblychache](https://go.microsoft.com/fwlink/?LinkId=63912)  
  
  
