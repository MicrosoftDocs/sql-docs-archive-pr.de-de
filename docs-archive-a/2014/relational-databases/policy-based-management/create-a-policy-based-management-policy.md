---
title: Erstellen einer Richtlinie der richtlinienbasierten Verwaltung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, creating policies
ms.assetid: b28bf963-89f9-4941-b6c1-6004fec347f1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e76b4dce17e00bae5e8ca4fcf071868c0641c786
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87618669"
---
# <a name="create-a-policy-based-management-policy"></a>Erstellen einer Richtlinie der richtlinienbasierten Verwaltung
  In diesem Thema wird beschrieben, wie Sie eine Richtlinie der richtlinienbasierten Verwaltung mithilfe von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]erstellen.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **Erstellen einer Richtlinie mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert die Mitgliedschaft in der PolicyAdministratorRole-Rolle in der msdb-Datenbank.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-create-a-policy"></a>So erstellen Sie eine Richtlinie  
  
1.  Klicken Sie im **Objekt-Explorer**auf das Pluszeichen, um den Server zu erweitern, auf dem Sie eine neue Richtlinie der richtlinienbasierten Verwaltung erstellen möchten.  
  
2.  Klicken Sie auf das Pluszeichen, um den Ordner **Verwaltung** zu erweitern.  
  
3.  Klicken Sie auf das Pluszeichen, um **Richtlinienverwaltung**zu erweitern.  
  
4.  Klicken Sie mit der rechten Maustaste auf den Ordner **Richtlinien** , und wählen Sie **Neue Richtlinie**aus.  
  
5.  Geben Sie im Dialogfeld **Neue Richtlinie erstellen** im Feld **Name** den Namen der neuen Richtlinie ein.  
  
6.  Wenn die Richtlinie sofort nach dem Erstellen aktiviert werden soll, aktivieren Sie das Kontrollkästchen **Aktiviert** . Wenn der Auswertungsmodus **Bedarfsgesteuert**lautet, ist das Kontrollkästchen **Aktiviert** nicht verfügbar.  
  
7.  Wählen Sie in der Liste **Bedingung überprüfen** eine der vorhandenen Bedingungen aus, oder wählen Sie **Neue Bedingung**aus. Zum Bearbeiten einer Bedingung wählen Sie die Bedingung aus und klicken dann auf die Schaltfläche mit den Auslassungspunkten ( **...** ). Weitere Informationen finden Sie unter [Erstellen einer neuen Bedingung der richtlinienbasierten Verwaltung](create-a-new-policy-based-management-condition.md) oder [Anzeigen oder Ändern der Eigenschaften einer Bedingung der richtlinienbasierten Verwaltung](view-or-modify-the-properties-of-a-policy-based-management-condition.md).  
  
8.  Wählen Sie im Feld **Für Ziele** einen oder mehrere Zieltypen für diese Richtlinie aus. Einige Bedingungen und Facets können nur auf bestimmte Zieltypen angewendet werden. Die verfügbaren Zielsätze werden im zugeordneten Feld angezeigt. Erweitern Sie **Alle** , um eine Filterbedingung für bestimmte Zieltypen auszuwählen. Wenn keine Ziele in diesem Feld angezeigt werden, wird die Prüfungsbedingung auf Serverebene bewertet.  
  
9. Legen Sie im Feld **Auswertungsmodus** fest, wie sich diese Richtlinie verhalten soll. Verschiedene Bedingungen können verschiedene gültige Auswertungsmodi haben. Weitere Informationen darüber, welche Auswertungsmodi gültig sind, finden Sie unter [Verwalten von Servern mit der richtlinienbasierten Verwaltung](administer-servers-by-using-policy-based-management.md).  
  
10. Wenn die Richtlinie nach einem Zeitplan ausgewertet werden soll, legen Sie den Auswertungsmodus auf **Nach Zeitplan**fest, und klicken Sie dann auf **Auswählen** , um einen Zeitplan auszuwählen, oder auf **Neu** , um einen neuen Zeitplan zu erstellen.  
  
11. Zur Beschränkung der Richtlinie auf eine Teilmenge der Zieltypen treffen Sie im Feld **Serverbeschränkung** eine Auswahl aus den beschränkenden Bedingungen, oder erstellen Sie eine neue Bedingung.  
  
     Weitere Informationen zu den Optionen im Dialogfeld **Neue Richtlinie erstellen** finden Sie unter [Dialogfeld 'Neue Richtlinie erstellen' oder 'Richtlinie öffnen', Seite 'Allgemein'](../../integration-services/general-page-of-integration-services-designers-options.md) oder [Dialogfeld 'Neue Richtlinie erstellen' oder 'Richtlinie öffnen', Seite 'Beschreibung'](create-new-policy-or-open-policy-dialog-box-description-page.md).  
  
12. Wenn Sie fertig sind, klicken Sie auf **OK**.  
  
  
