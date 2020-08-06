---
title: Importieren einer Domäne aus einer DQS-Datei | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: fabd88b0-22b3-4543-a993-6d5b202ded80
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 2e08837fd0b160732b506af77a6cf4a1cbe1966f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700262"
---
# <a name="import-a-domain-from-a-dqs-file"></a>Importieren einer Domäne aus einer DQS-Datei
  In diesem Thema wird beschrieben, wie eine Domäne aus einer DQS-Datei in eine vorhandene Wissensdatenbank in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) importiert wird. Eine DQS-Datendatei wird erstellt, indem eine Domäne oder eine Wissensdatenbank aus der Anwendung [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] exportiert wird. Eine DQS-Datendatei wird verschlüsselt und kann nicht angezeigt werden.  
  
 Durch das Verwenden einer DQS-Datendatei zum Exportieren einer Domäne aus einer Wissensdatenbank und Importieren in eine andere Wissensdatenbank wird der Wissensgenerierungsprozess vereinfacht, Zeit gespart und der Aufwand verringert. Auf diese Weise haben Sie die Möglichkeit, eine Domäne und ihr Wissen zusammen mit anderen zu nutzen und somit Zeit zu sparen. Sie können eine Einzeldomäne oder eine Verbunddomäne (mit mehreren Einzeldomänen) importieren. Eine DQS-Datei, die eine Einzeldomäne enthält, umfasst alle Domänendaten einschließlich Domäneneigenschaften, Werten und Regeldaten, aber keine Informationen zu den zugeordneten Verweisdaten. Eine DQS-Datei, die eine Verbunddomäne enthält, umfasst alle Verbunddomänendaten, einschließlich aller Domänendaten für die Einzeldomänen, die in der Verbunddomäne enthalten sind, und die Eigenschaften, Wertbeziehungen und CD-Regeln der Verbunddomäne, aber keine zugeordneten Verweisdaten. Veröffentlichte und unveröffentlichte Daten werden importiert.  
  
 Wenn Sie eine Domäne importieren, bleibt der Name der Domäne mit dem Namen der ursprünglich exportierten Domäne identisch, es sei denn, der Domänenname ist bereits vorhanden. In diesem Fall fügt DQS „_1“ an den Namen an. Dies gilt auch, wenn Sie eine Verbunddomäne importieren, die eine Einzeldomäne mit dem gleichen Namen wie eine vorhandene Domäne enthält.  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Voraussetzungen  
 Um eine Domäne aus einer DQS-Datei zu importieren, müssen Sie bereits eine Einzeldomäne oder eine Verbunddomäne (mit mehreren Einzeldomänen) in die DQS-Datei exportiert haben. Die DQS-Datei darf nur eine Domäne enthalten. Sie müssen auch eine Wissensdatenbank erstellt und geöffnet haben, in die die Domäne importiert werden soll.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Sie müssen über die Rolle „dqs_kb_editor“ oder „dqs_administrator“ in der DQS_MAIN-Datenbank verfügen, um eine Domäne aus einer DQS-Datei zu importieren.  
  
##  <a name="import-a-domain-from-a-dqs-file"></a><a name="Import"></a>Importieren einer Domäne aus einer DQS-Datei  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Führen Sie die Data Quality-Client Anwendung](../../2014/data-quality-services/run-the-data-quality-client-application.md)aus.  
  
2.  Öffnen Sie im [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Startbildschirm in der Domänenverwaltungsaktivität eine Wissensdatenbank.  
  
3.  Klicken Sie auf das Symbol **Domäne aus Datendatei importieren** .  
  
4.  Wechseln Sie im Dialogfeld **Aus Datendatei importieren** zum Ordner, aus dem Sie die Datei importieren möchten, wählen Sie die Datei aus (DQS-Datei), und klicken Sie dann auf **Öffnen**.  
  
5.  Klicken Sie im Dialogfeld **Domäne importieren** auf **OK**.  
  
    > [!NOTE]  
    >  Der Importvorgang ist nur erfolgreich, wenn die DQS-Datei, aus der Sie importieren, nur eine Einzeldomäne oder eine Verbunddomäne (mit mehreren Einzeldomänen) enthält.  
  
6.  Überprüfen Sie, ob die Domäne, die Sie importiert haben, in der Liste **Domäne** angezeigt wird. Wenn Sie eine Verbunddomäne importiert haben, überprüfen Sie, ob die Verbunddomäne und die Einzeldomänen, die darin enthalten sind, alle in der Liste **Domäne** aufgeführt werden.  
  
##  <a name="follow-up-after-importing-a-domain-from-a-dqs-file"></a><a name="FollowUp"></a> Nachverfolgung: Nach dem Importieren einer Domäne aus einer DQS-Datei  
 Nachdem Sie eine Domäne aus einer DQS-Datei importiert haben, können Sie der Domäne Wissen hinzufügen oder die Domäne in einem Bereinigungs- oder Abgleichsprojekt verwenden - je nach den Inhalten der Domäne. Weitere Informationen finden Sie unter [Durchführen der Wissensermittlung](../../2014/data-quality-services/perform-knowledge-discovery.md), [Verwalten einer Domäne](../../2014/data-quality-services/managing-a-domain.md), [Verwalten einer Verbunddomäne](../../2014/data-quality-services/managing-a-composite-domain.md), [Erstellen einer Abgleichsrichtlinie](../../2014/data-quality-services/create-a-matching-policy.md), [Datenbereinigung](../../2014/data-quality-services/data-cleansing.md) oder [Datenabgleich](../../2014/data-quality-services/data-matching.md).  
  
  
