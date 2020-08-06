---
title: Einschränkungen für das CLR-Integrations Programmiermodell | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], programming model restrictions
- assemblies [CLR integration], CREATE ASSEMBLY checks
- programming model restrictions [CLR integration]
- assemblies [CLR integration], runtime checks
ms.assetid: 2446afc2-9d21-42d3-9847-7733d3074de9
author: rothja
ms.author: jroth
ms.openlocfilehash: 01a32e1460ad9c49061b39b1bdc419c7cd2f1342
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607835"
---
# <a name="clr-integration-programming-model-restrictions"></a>Beschränkungen des Programmiermodells für die CLR-Integration
  Wenn Sie eine verwaltete gespeicherte Prozedur oder ein anderes verwaltetes Datenbankobjekt entwickeln, werden von bestimmte Code Überprüfungen durchgeführt, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Wenn die Assembly mithilfe der-Anweisung zum ersten Mal in der Datenbank registriert wird, `CREATE ASSEMBLY` und auch zur Laufzeit. Der verwaltete Code wird außerdem zur Laufzeit überprüft, da in einer Assembly Codepfade vorhanden sein können, die zur Laufzeit eigentlich nicht erreicht werden.  Dadurch wird Flexibilität für die Registrierung von Assemblys von Drittanbietern geschaffen, sodass eine Assembly nicht blockiert wird, wenn ein "Unsafe"-Code vorliegt, der in einer Clientumgebung ausgeführt werden soll, jedoch nie in der gehosteten CLR ausgeführt wird. Welche Anforderungen der verwaltete Code erfüllen muss, hängt davon ab, ob die Assembly als, oder registriert ist, und ist im `SAFE` `EXTERNAL_ACCESS` `UNSAFE` `SAFE` folgenden aufgeführt.  
  
 Neben den Einschränkungen, die für verwaltete Codeassemblys gelten, werden außerdem Sicherheitsberechtigungen für Code erteilt. Die CLR (Common Language Runtime) unterstützt ein Sicherheitsmodell, das als Codezugriffssicherheit für verwalteten Code bezeichnet wird. In diesem Modell werden Assemblys Berechtigungen auf Grundlage der Identität des Codes gewährt. `SAFE`-, `EXTERNAL_ACCESS`- und `UNSAFE`-Assemblys verfügen über andere CAS-Berechtigungen (Code Access Security). Weitere Informationen finden Sie unter [CLR-Integration Code Zugriffssicherheit](../security/clr-integration-code-access-security.md).  
  
## <a name="create-assembly-checks"></a>CREATE ASSEMBLY-Überprüfungen  
 Wenn die `CREATE ASSEMBLY`-Anweisung ausgeführt wird, werden die folgenden Überprüfungen für jede Sicherheitsebene vorgenommen.  Schlägt eine Überprüfung fehl, wird `CREATE ASSEMBLY` mit einer Fehlermeldung abgebrochen.  
  
### <a name="global-any-security-level"></a>Global (eine beliebige Sicherheitsebene)  
 Alle Assemblys, auf die verwiesen wird, müssen ein oder mehrere der folgenden Kriterien erfüllen:  
  
-   Die Assembly ist bereits in der Datenbank registriert.  
  
-   Die Assembly ist eine der unterstützten Assemblys. Weitere Informationen finden Sie [unter Supported .NET Framework Libraries](supported-net-framework-libraries.md).  
  
-   Sie verwenden `CREATE ASSEMBLY FROM` * \<location> ,* und alle referenzierten Assemblys und ihre Abhängigkeiten sind in verfügbar *\<location>* .  
  
-   Sie verwenden `CREATE ASSEMBLY FROM` * \<bytes ...> ,* und alle Verweise werden mit durch Leerzeichen getrennten Bytes angegeben.  
  
### <a name="external_access"></a>EXTERNAL_ACCESS  
 Alle `EXTERNAL_ACCESS`-Assemblys müssen die folgenden Kriterien erfüllen:  
  
-   Statische Felder werden nicht verwendet, um Informationen zu speichern. Schreibgeschützte statische Felder sind zulässig.  
  
-   Der PEVerify-Test wird bestanden. Das PEVerify-Tool (peverify.exe), das überprüft, ob der MSIL-Code und die zugeordneten Metadaten den Anforderungen an die Typsicherheit entsprechen, wird mit .NET Framework SDK zur Verfügung gestellt.  
  
-   Die Synchronisierung, z. B. mit der `SynchronizationAttribute`-Klasse, wird nicht verwendet.  
  
-   Finalizer-Methoden werden nicht verwendet.  
  
 Die folgenden benutzerdefinierten Attribute sind in `EXTERNAL_ACCESS`-Assemblys nicht zulässig:  
  
-   System.ContextStaticAttribute  
  
-   System.MTAThreadAttribute  
  
-   System.Runtime.CompilerServices.MethodImplAttribute  
  
-   System.Runtime.CompilerServices.CompilationRelaxationsAttribute  
  
-   System.Runtime.Remoting.Contexts.ContextAttribute  
  
-   System.Runtime.Remoting.Contexts.SynchronizationAttribute  
  
-   System.Runtime.InteropServices.DllImportAttribute  
  
-   System.Security.Permissions.CodeAccessSecurityAttribute  
  
-   System.Security.SuppressUnmanagedCodeSecurityAttribute  
  
-   System.Security.UnverifiableCodeAttribute  
  
-   System.STAThreadAttribute  
  
-   System.ThreadStaticAttribute  
  
### <a name="safe"></a>SAFE  
  
-   Alle `EXTERNAL_ACCESS`-Assemblybedingungen werden überprüft.  
  
## <a name="runtime-checks"></a>Laufzeitüberprüfungen  
 Zur Laufzeit wird die Codeassembly auf die folgenden Bedingungen überprüft. Wird eine dieser Bedingungen erkannt, darf der verwaltete Code nicht ausgeführt werden und es wird eine Ausnahme ausgelöst.  
  
### <a name="unsafe"></a>UNSAFE  
 Das Laden einer Assembly (explizit durch Aufrufen der- `System.Reflection.Assembly.Load()` Methode aus einem Bytearray oder implizit durch die Verwendung des `Reflection.Emit` -Namespace) ist nicht zulässig.  
  
### <a name="external_access"></a>EXTERNAL_ACCESS  
 Alle `UNSAFE`-Bedingungen werden überprüft.  
  
 Alle Typen und Methoden, die mit den folgenden Hostschutzattributwerten in der unterstützten Assemblyliste als Anmerkungen versehen sind, sind nicht zulässig.  
  
-   SelfAffectingProcessMgmt  
  
-   SelfAffectingThreading  
  
-   Synchronization  
  
-   SharedState  
  
-   ExternalProcessMgmt  
  
-   ExternalThreading  
  
-   SecurityInfrastructure  
  
-   MayLeakOnAbort  
  
-   UI  
  
 Weitere Informationen zu HPAs und eine Liste der unzulässigen Typen und Member in den unterstützten Assemblys finden Sie unter [Host Schutz Attribute und CLR-Integrations Programmierung](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md).  
  
### <a name="safe"></a>SAFE  
 Alle `EXTERNAL_ACCESS`-Bedingungen werden überprüft.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Unterstützte .NET Framework-Bibliotheken](supported-net-framework-libraries.md)   
 [Code Zugriffssicherheit für die CLR-Integration](../security/clr-integration-code-access-security.md)   
 [Host Schutz Attribute und Programmierung der CLR-Integration](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [Erstellen von Assemblys](../assemblies/creating-an-assembly.md)  
  
  
