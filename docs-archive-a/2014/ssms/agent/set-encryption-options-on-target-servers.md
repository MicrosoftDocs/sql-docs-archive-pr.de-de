---
title: Festlegen von Verschlüsselungsoptionen auf Zielservern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, encryption
- target servers [SQL Server], encryption
- multiserver environments [SQL Server], setting encryption options on target servers
ms.assetid: 1a9fd539-e166-4ea8-9f21-ac400ca74dee
author: stevestein
ms.author: sstein
ms.openlocfilehash: cd10d2e05e59015542f41cc123de993e6128f9f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621319"
---
# <a name="set-encryption-options-on-target-servers"></a>Festlegen von Verschlüsselungsoptionen auf Zielservern
  Wenn Sie für die verschlüsselte SSL-Kommunikation (Secure Sockets Layer) zwischen Masterservern und einigen oder allen Zielservern kein Zertifikat verwenden können, aber den Kanal zwischen diesen verschlüsseln möchten, müssen Sie auf dem Zielserver die erforderliche Sicherheitsstufe konfigurieren.  
  
 Legen Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Registrierungs Unterschlüssel **\ HKEY_LOCAL_MACHINE \software\microsoft\microsoft \\ SQL Server** \<*instance_name*> **\SQLServerAgent\MsxEncryptChannelOptions (REG_DWORD)** auf dem Zielserver auf einen der folgenden Werte fest, um die für einen bestimmten Kommunikationskanal zwischen einem Master-und einem Zielserver erforderliche Sicherheitsstufe zu konfigurieren. Der Wert von \<*instance_name*> ist **MSSQL.** _n_. Beispiel: **MSSQL.1** oder **MSSQL.3**.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**0**|Deaktiviert die Verschlüsselung zwischen diesem Zielserver und dem Masterserver. Wählen Sie diese Option nur aus, wenn der Kanal zwischen Zielserver und Masterserver auf andere Weise gesichert ist.|  
|**1**|Aktiviert nur die Verschlüsselung zwischen diesem Zielserver und dem Masterserver, eine Zertifikatüberprüfung ist jedoch nicht erforderlich.|  
|**2**|Aktiviert die vollständige SSL-Verschlüsselung und Zertifikatüberprüfung zwischen diesem Zielserver und dem Masterserver. Dies ist die Standardeinstellung. Es wird empfohlen, diesen Wert nicht zu ändern, es sei denn, dafür liegen spezifische Gründe vor.|  
  
 Wenn **1** oder **2** angegeben wird, muss SSL sowohl auf dem Master- als auch auf dem Zielserver aktiviert sein. Wenn **2** angegeben wird, muss außerdem auf dem Masterserver ein ordnungsgemäß signiertes Zertifikat vorhanden sein.  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aktivieren von verschlüsselten Verbindungen zur Datenbank-Engine &#40;SQL Server-Konfigurations-Manager&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)  
  
  
