---
title: Deinstallieren Sie die eigenständige Version von Berichts-Generator (Berichts-Generator) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 009538c6-4941-4393-b14b-9144cffdbdaf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cda13248d1aa14ee3d57a951872d3ad8ded17da9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87620742"
---
# <a name="uninstall-the-stand-alone-version-of-report-builder-report-builder"></a>Deinstallieren der eigenständigen Version des Berichts-Generators (Berichts-Generator)
  Sie können die eigenständige Version des Berichts-Generators über die Systemsteuerung oder die Befehlszeile deinstallieren. Für die Deinstallation der [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)]-Version des Berichts-Generators muss auch [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] deinstalliert werden.  
  
 Zum Deinstallieren des Berichts-Generators über die Befehlszeile wird die gleiche Syntax verwendet wie zum Installieren des Berichts-Generators. Sie geben lediglich die /x-Option anstelle der /i-Option an. In den Befehlszeilen zur Deinstallation können auch die /quiet-Option und andere Standardoptionen verwendet werden. Wenn das Windows Installer Package für den Berichts-Generator (ReportBuilder3_x86.msi) entfernt wurde, ist das Entfernen des Berichts-Generators über die Befehlszeile nicht ohne Weiteres möglich. In der Dokumentation für das msiexec-Programm in der MSDN Library wird beschrieben, wie Sie den Berichts-Generator möglicherweise dennoch mit der GUID entfernen können.  
  
 Enthalten vom Berichts-Generator verwendete Ordner benutzerdefinierte Dateien, werden die Ordner und Dateien beim Entfernen des Berichts-Generators beibehalten. Nur die Berichts-Generator-Dateien werden entfernt.  
  
### <a name="to-uninstall-report-builder-from-the-control-panel"></a>So deinstallieren Sie den Berichts-Generator über die Systemsteuerung  
  
1.  Klicken Sie im Menü **Start** auf **Systemsteuerung**.  
  
2.  Klicken Sie in der Systemsteuerung auf **Programme und Funktionen**.  
  
3.  Suchen Sie [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Berichts-Generator in der Liste **Name** , und klicken Sie darauf.  
  
4.  Klicken Sie auf **Deinstallieren**.  
  
5.  Klicken Sie auf **Ja**, wenn Sie aufgefordert werden, das Deinstallieren des Berichts-Generators zu bestätigen.  
  
### <a name="to-uninstall-report-builder-from-the-command-line"></a>So deinstallieren Sie den Berichts-Generator über die Befehlszeile  
  
1.  Klicken Sie im Menü **Start** auf **Ausführen**.  
  
2.  Geben Sie im Textfeld **Öffnen** den Text`cmd.`  
  
3.  Navigieren Sie im Eingabeaufforderungsfenster zum Ordner mit der Datei "ReportBuilder3_x86.msi".  
  
4.  Geben Sie eine Standardbefehlszeile wie im folgenden Beispiel ein:  
  
 `msiexec /x ReportBuilder3_x86.msi /quiet /l*v install.log`  
  
 Wenn Sie die Protokollierung einschließen möchten, verwenden Sie z. B. folgende Befehlszeile:  
  
 `msiexec /x ReportBuilder3_x86.msi /quiet /l*v c:\junk\install.log`  
  
1.  Drücken Sie die **EINGABETASTE**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Unterstützung für Installation, Deinstallation und Berichts-Generator](../install-uninstall-and-report-builder-support.md)   
 [Installieren Sie die eigenständige Version von Berichts-Generator &#40;Berichts-Generator&#41;](install-report-builder.md)  
  
  
