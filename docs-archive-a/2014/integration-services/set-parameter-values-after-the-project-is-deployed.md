---
title: Festlegen von Parameter Werten nach der Bereitstellung des Projekts | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: c9dcca4d-f1a0-45ec-b078-f4d372589baf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 39572594e429b61de0641c6e6929e84105138f1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87726073"
---
# <a name="set-parameter-values-after-the-project-is-deployed"></a>Festlegen von Parameterwerten nach der Bereitstellung des Projekts
  Mit dem Bereitstellungs-Assistenten können Sie Serverstandardparameterwerte festlegen, wenn Sie das Projekt im Katalog bereitstellen. Nachdem das Projekt dem Katalog hinzugefügt worden ist, Sie können Serverstandardwerte mithilfe von SQL Server Management Studio (SSMS)-Objekt-Explorer oder Transact-SQL festlegen.  
  
### <a name="to-set-server-defaults-with-ssms-object-explorer"></a>So legen Sie Serverstandardwerte mit SSMS-Objekt-Explorer fest  
  
1.  Wählen Sie das Projekt unter dem Knoten **Integration Services** aus, und klicken Sie mit der rechten Maustaste darauf.  
  
2.  Klicken Sie auf **Eigenschaften** , um das Dialogfeld **Projekteigenschaften** zu öffnen.  
  
3.  Öffnen Sie die Parameterseite, indem Sie unter **Seite auswählen** auf **Parameter**klicken.  
  
4.  Wählen Sie in der Liste **Parameter** den gewünschten Parameter aus. Hinweis: Anhand der Spalte **Container** können Projektparameter leichter von Paketparametern unterschieden werden.  
  
5.  Geben Sie in der Spalte **Wert** den gewünschten Serverstandardparameterwert an.  
  
 Verwenden Sie zum Festlegen von Serverstandardwerten mit Transact-SQL die gespeicherte Prozedur [catalog.set_object_parameter_value &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-set-object-parameter-value-ssisdb-database). Verwenden Sie zum Anzeigen der aktuellen Serverstandards die Abfrage [catalog.object_parameters &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-views/catalog-object-parameters-ssisdb-database). Verwenden Sie zum Löschen von Serverstandardwerten die gespeicherte Prozedur [catalog.clear_object_parameter_value &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-clear-object-parameter-value-ssisdb-database).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Integration Services &#40;SSIS-&#41; Parameter](integration-services-ssis-package-and-project-parameters.md)  
  
  
