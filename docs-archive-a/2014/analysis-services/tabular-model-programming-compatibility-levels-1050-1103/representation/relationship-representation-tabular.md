---
title: Beziehungs Darstellung (tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 86a5eff8-4e07-444b-ac15-5695f09aa105
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0b0a9ef87aa696292a1011a9b8d829a595eaeec2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698570"
---
# <a name="relationship-representation-tabular"></a><span data-ttu-id="61ce1-102">Beziehungsdarstellung (tabellarisch)</span><span class="sxs-lookup"><span data-stu-id="61ce1-102">Relationship Representation (Tabular)</span></span>
  <span data-ttu-id="61ce1-103">Eine Beziehung ist eine Verbindung zwischen zwei Tabellen mit Daten.</span><span class="sxs-lookup"><span data-stu-id="61ce1-103">A relationship is a connection between two tables of data.</span></span> <span data-ttu-id="61ce1-104">Die Beziehung legt fest, wie die Daten in den beiden Tabellen korreliert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="61ce1-104">The relationship establishes how the data in the two tables should be correlated.</span></span>  
  
 <span data-ttu-id="61ce1-105">Eine ausführliche Erläuterung zum Erstellen und Bearbeiten der Beziehungs Darstellung finden Sie unter [Beziehungs Darstellung (tabellarisch)](relationship-representation-tabular.md) .</span><span class="sxs-lookup"><span data-stu-id="61ce1-105">See [Relationship Representation (Tabular)](relationship-representation-tabular.md) for a detailed explanation on how to create and manipulate the relationship representation.</span></span>  
  
## <a name="relationship-representation"></a><span data-ttu-id="61ce1-106">Beziehungsdarstellung</span><span class="sxs-lookup"><span data-stu-id="61ce1-106">Relationship Representation</span></span>  
 <span data-ttu-id="61ce1-107">In tabellarischen Modellen können mehrere Beziehungen zwischen zwei Tabellen definiert werden.</span><span class="sxs-lookup"><span data-stu-id="61ce1-107">In tabular models, multiple relationships can be defined between two tables.</span></span> <span data-ttu-id="61ce1-108">Wenn mehrere Beziehungen zwischen zwei Tabellen definiert werden, kann nur eine als Standardbeziehung für das Modell definiert werden und wird als aktive Beziehung bezeichnet. Alle anderen Beziehungen werden als inaktive Beziehungen bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="61ce1-108">When multiple relationships, between two tables, are defined only one can be defined as the default relationship for the model and it is named as the Active relationship; all other relationships are named as Inactive.</span></span>  
  
### <a name="relationship-in-amo"></a><span data-ttu-id="61ce1-109">Beziehung in AMO</span><span class="sxs-lookup"><span data-stu-id="61ce1-109">Relationship in AMO</span></span>  
 <span data-ttu-id="61ce1-110">Im Hinblick auf AMO-Objekte verfügen alle inaktiven Beziehungen über eine Darstellung einer 1:1-Zuordnungsbeziehung zu <xref:Microsoft.AnalysisServices.Relationship>, und es sind keine weiteren AMO-Hauptobjekte erforderlich. Für die aktive Beziehung gelten andere Anforderungen, und es ist zusätzlich eine Zuordnung zu <xref:Microsoft.AnalysisServices.ReferenceMeasureGroupDimension> erforderlich.</span><span class="sxs-lookup"><span data-stu-id="61ce1-110">In terms of AMO objects all inactive relationships have a representation of a one to one mapping relationship with <xref:Microsoft.AnalysisServices.Relationship> and no other main AMO objects are required; for the active relationship other requirements exist and a mapping to the <xref:Microsoft.AnalysisServices.ReferenceMeasureGroupDimension> is also required.</span></span>  
  
 <span data-ttu-id="61ce1-111">Die folgenden Codeausschnitte veranschaulichen, wie eine Beziehung in tabellarischen Modellen erstellt, wie eine Beziehung aktiviert und wie ein Primärschlüssel (abweichend von "RowNumber") in einer Tabelle definiert wird.</span><span class="sxs-lookup"><span data-stu-id="61ce1-111">The following code snippets show how to create a relationship in Tabular models, how to activate a relationship and how to define a primary key in a table (other than "RowNumber").</span></span> <span data-ttu-id="61ce1-112">Um eine aktive Beziehung zu erstellen, muss ein Primärschlüssel in der Primärschlüsseltabelle PKTableName der Beziehung (der 1-Seite der Beziehung) definiert werden. Im hier gezeigten Beispiel wird der Primärschlüssel für PKColumnName erstellt, sofern kein Primärschlüssel in dieser Spalte definiert ist.</span><span class="sxs-lookup"><span data-stu-id="61ce1-112">To create an active relationship a primary key need to be defined in the primary key table - PKTableName - of the relationship (the one side of the relationship), the sample shown here creates the primary key on the PKColumnName if no primary key is defined in this column.</span></span> <span data-ttu-id="61ce1-113">Beim Erstellen inaktiver Beziehungen ist kein Primärschlüssel in der Primärschlüsselspalte erforderlich.</span><span class="sxs-lookup"><span data-stu-id="61ce1-113">Inactive relationships can be created without the need of having a primary key on the primary key column.</span></span>  
  
```cs
private Boolean createRelationship(string PKTableName, string PKColumnName, string MVTableName, string MVColumnName, AMO.Database tabularDb, string cubeName, Boolean forceActive)  
{  
    //verify input parameters  
    if(     string.IsNullOrEmpty(PKTableName) || string.IsNullOrWhiteSpace(PKTableName)  
        ||  string.IsNullOrEmpty(PKColumnName) || string.IsNullOrWhiteSpace(PKColumnName)  
        ||  string.IsNullOrEmpty(MVTableName) || string.IsNullOrWhiteSpace(MVTableName)  
        ||  string.IsNullOrEmpty(MVColumnName) || string.IsNullOrWhiteSpace(MVColumnName)  
        ||  (tabularDb == null)  
        ) return false;  
    if(!tabularDb.Dimensions.ContainsName(PKTableName) || !tabularDb.Dimensions.ContainsName(MVTableName)) return false;  
    if(!tabularDb.Dimensions[PKTableName].Attributes.ContainsName(PKColumnName) || !tabularDb.Dimensions[MVTableName].Attributes.ContainsName(MVColumnName)) return false;  
  
    //Verify underlying cube structure  
    if (!tabularDb.Cubes[cubeName].Dimensions.ContainsName(PKTableName) || !tabularDb.Cubes[cubeName].Dimensions.ContainsName(MVTableName)) return false; //Should return an exception!!  
    if (!tabularDb.Cubes[cubeName].MeasureGroups.ContainsName(PKTableName) || !tabularDb.Cubes[cubeName].MeasureGroups.ContainsName(MVTableName)) return false; //Should return an exception!!  
  
    //Make sure PKTableName.PKColumnName  is set as PK ==> <attribute>.usage == AMO.AttributeUsage.Key  
    if (tabularDb.Dimensions[PKTableName].Attributes[PKColumnName].Usage != AMO.AttributeUsage.Key)  
    {  
        //... here we are 'fixing', if there is an issue with PKTableName.PKColumnName not being the PK of the table  
        setPKColumn(tabularDb, PKTableName, PKColumnName);  
    }  
  
    //Terminology note:   
    // -   the many side of the relationship is named the From end in AMO  
    // -   the PK side of the relationship in named the To end in AMO  
    //  
    //It seems relationships flow FROM the many side of the relationship in TO the primary key side of the relationship in AMO  
    //              
    //Verify the relationship we are creating does not exist, regardless of name.  
    //if it exists, return true (no need to recreate it)  
    //if it doesn't exists it will be created after this validation  
  
    //   
    foreach (AMO.Relationship currentRelationship in tabularDb.Dimensions[MVTableName].Relationships)  
    {  
        if ((currentRelationship.FromRelationshipEnd.Attributes[0].AttributeID == MVColumnName)  
            && (currentRelationship.ToRelationshipEnd.DimensionID == PKTableName)  
            && (currentRelationship.ToRelationshipEnd.Attributes[0].AttributeID == PKColumnName))  
        {  
            if (forceActive)  
            {  
                //Activate the relationship   
                setActiveRelationship(tabularDb.Cubes[cubeName], MVTableName, MVColumnName, PKTableName, currentRelationship.ID);  
                //Update server with changes made here  
                tabularDb.Update(AMO.UpdateOptions.ExpandFull, AMO.UpdateMode.CreateOrReplace);  
                tabularDb.Cubes[cubeName].MeasureGroups[MVTableName].Process(AMO.ProcessType.ProcessFull);  
            }  
            return true;  
        }  
    }  
  
    //A relationship like the one to be created does not exist; ergo, let's create it:  
  
    //First, create the INACTIVE relationship definitions in the MultipleValues end of the relationship  
    #region define unique name for relationship  
    string newRelationshipID = string.Format("Relationship _{0}_{1}_ to _{2}_{3}_", MVTableName, MVColumnName, PKTableName, PKColumnName);  
    int rootLen = newRelationshipID.Length;  
    for (int i = 0; tabularDb.Dimensions[MVTableName].Relationships.Contains(newRelationshipID); )  
    {  
        newRelationshipID = string.Format("{0}_{1,8:0}", newRelationshipID.Substring(0, rootLen), i);  
    }  
    #endregion  
    AMO.Relationship newRelationship = tabularDb.Dimensions[MVTableName].Relationships.Add(newRelationshipID);  
  
    newRelationship.FromRelationshipEnd.DimensionID = MVTableName;  
    newRelationship.FromRelationshipEnd.Attributes.Add(MVColumnName);  
    newRelationship.FromRelationshipEnd.Multiplicity = AMO.Multiplicity.Many;  
    newRelationship.FromRelationshipEnd.Role = string.Empty;  
    newRelationship.ToRelationshipEnd.DimensionID = PKTableName;  
    newRelationship.ToRelationshipEnd.Attributes.Add(PKColumnName);  
    newRelationship.ToRelationshipEnd.Multiplicity = AMO.Multiplicity.One;  
    newRelationship.ToRelationshipEnd.Role = string.Empty;  
  
    //Update server to create relationship  
    tabularDb.Update(AMO.UpdateOptions.ExpandFull, AMO.UpdateMode.UpdateOrCreate);  
    tabularDb.Dimensions[MVTableName].Process(AMO.ProcessType.ProcessDefault);  
    tabularDb.Dimensions[PKTableName].Process(AMO.ProcessType.ProcessDefault);  
  
    //Second, activate the relationship if relationship is to be set as the active relationship: 'forceActive==true'  
    //... an inactive relationship needs only to be created on the dimensions object  
    if (forceActive)  
    {  
        //Activate the relationship   
        setActiveRelationship(tabularDb.Cubes[cubeName], MVTableName, MVColumnName, PKTableName, newRelationshipID);                  
    }             
    return true;  
}  
  
private void setActiveRelationship(AMO.Cube currentCube, string MVTableName, string MVColumnName, string PKTableName, string relationshipID)  
{  
    if (!currentCube.MeasureGroups.Contains(MVTableName))  
    {  
        throw new AMO.AmoException(string.Format("Cube [{0}] does not contain Measure Group [{1}]\nError activating relationship [{2}]: [{4}] <--- [{1}].[{3}]"  
                                                , currentCube.Name, MVTableName, relationshipID, MVColumnName, PKTableName));  
    }  
    AMO.MeasureGroup currentMG = currentCube.MeasureGroups[MVTableName];  
  
    if (!currentMG.Dimensions.Contains(PKTableName))  
    {  
        AMO.ReferenceMeasureGroupDimension newReferenceMGDim = new AMO.ReferenceMeasureGroupDimension();  
        newReferenceMGDim.CubeDimensionID = PKTableName;  
        newReferenceMGDim.IntermediateCubeDimensionID = MVTableName;  
        newReferenceMGDim.IntermediateGranularityAttributeID = MVColumnName;  
        newReferenceMGDim.Materialization = AMO.ReferenceDimensionMaterialization.Regular;  
        newReferenceMGDim.RelationshipID = relationshipID;  
        foreach (AMO.CubeAttribute PKAttribute in currentCube.Dimensions[PKTableName].Attributes)  
        {  
            AMO.MeasureGroupAttribute PKMGAttribute = newReferenceMGDim.Attributes.Add(PKAttribute.AttributeID);  
            OleDbType PKMGAttributeType = PKAttribute.Attribute.KeyColumns[0].DataType;  
            PKMGAttribute.KeyColumns.Add(new AMO.DataItem(PKTableName, PKAttribute.AttributeID, PKMGAttributeType));  
            PKMGAttribute.KeyColumns[0].Source = new AMO.ColumnBinding(PKTableName, PKAttribute.AttributeID);  
        }  
        currentMG.Dimensions.Add(newReferenceMGDim);  
  
        AMO.ValidationErrorCollection errors = new AMO.ValidationErrorCollection();  
  
        newReferenceMGDim.Validate(errors, true);  
        if (errors.Count > 0)  
        {  
            StringBuilder errorMessages = new StringBuilder();  
            foreach (AMO.ValidationError err in errors)  
            {  
                errorMessages.AppendLine(string.Format("At {2}: # {0} : {1}", err.ErrorCode, err.FullErrorText, err.Source));  
            }  
            throw new AMO.AmoException(errorMessages.ToString());  
        }  
        //Update changes in the server  
        currentMG.Update(AMO.UpdateOptions.ExpandFull, AMO.UpdateMode.CreateOrReplace);  
    }  
    else  
    {  
        AMO.ReferenceMeasureGroupDimension currentReferenceMGDim = (AMO.ReferenceMeasureGroupDimension)currentMG.Dimensions[PKTableName];  
        currentReferenceMGDim.RelationshipID = relationshipID;  
        currentReferenceMGDim.IntermediateGranularityAttributeID = MVColumnName;  
        //Update changes in the server  
        currentMG.Update(AMO.UpdateOptions.ExpandFull, AMO.UpdateMode.UpdateOrCreate);  
    }  
    //process MG to activate relationship  
    currentMG.Process(AMO.ProcessType.ProcessFull);  
  
}  
  
private void setPKColumn(AMO.Database tabularDb, string PKTableName, string PKColumnName)  
{  
        //Find all 'unwanted' Key attributes, remove their Key definitions and include the attributes in the ["RowNumber"].AttributeRelationships  
        foreach (AMO.DimensionAttribute currentDimAttribute in tabularDb.Dimensions[PKTableName].Attributes)  
        {  
            if ((currentDimAttribute.Usage == AMO.AttributeUsage.Key) && (currentDimAttribute.ID != PKColumnName))  
            {  
                currentDimAttribute.Usage = AMO.AttributeUsage.Regular;  
                if (currentDimAttribute.ID != "RowNumber")  
                {  
                    currentDimAttribute.KeyColumns[0].NullProcessing = AMO.NullProcessing.Preserve;  
                    currentDimAttribute.AttributeRelationships.Clear();  
                    if (!tabularDb.Dimensions[PKTableName].Attributes["RowNumber"].AttributeRelationships.ContainsName(currentDimAttribute.ID))  
                    {  
                        AMO.DimensionAttribute currentAttribute = tabularDb.Dimensions[PKTableName].Attributes[currentDimAttribute.ID];  
                        AMO.AttributeRelationship currentAttributeRelationship = tabularDb.Dimensions[PKTableName].Attributes["RowNumber"].AttributeRelationships.Add(currentAttribute.ID);  
                        currentAttributeRelationship.OverrideBehavior = AMO.OverrideBehavior.None;  
                    }  
                    tabularDb.Dimensions[PKTableName].Attributes["RowNumber"].AttributeRelationships[currentDimAttribute.ID].Cardinality = AMO.Cardinality.Many;  
                }  
            }  
        }  
  
        //Remove PKColumnName from ["RowNumber"].AttributeRelationships  
        int PKAtribRelationshipPosition = tabularDb.Dimensions[PKTableName].Attributes["RowNumber"].AttributeRelationships.IndexOf(PKColumnName);  
        if (PKAtribRelationshipPosition != -1) tabularDb.Dimensions[PKTableName].Attributes["RowNumber"].AttributeRelationships.RemoveAt(PKAtribRelationshipPosition, true);  
  
        //Define PKColumnName as Key and add ["RowNumber"] to PKColumnName.AttributeRelationships with cardinality of One  
        tabularDb.Dimensions[PKTableName].Attributes[PKColumnName].Usage = AMO.AttributeUsage.Key;  
        tabularDb.Dimensions[PKTableName].Attributes[PKColumnName].KeyColumns[0].NullProcessing = AMO.NullProcessing.Error;  
        if (!tabularDb.Dimensions[PKTableName].Attributes[PKColumnName].AttributeRelationships.ContainsName("RowNumber"))  
        {  
            AMO.DimensionAttribute currentAttribute = tabularDb.Dimensions[PKTableName].Attributes["RowNumber"];  
            AMO.AttributeRelationship currentAttributeRelationship = tabularDb.Dimensions[PKTableName].Attributes[PKColumnName].AttributeRelationships.Add(currentAttribute.ID);  
            currentAttributeRelationship.OverrideBehavior = AMO.OverrideBehavior.None;  
        }  
        tabularDb.Dimensions[PKTableName].Attributes[PKColumnName].AttributeRelationships["RowNumber"].Cardinality = AMO.Cardinality.One;  
  
        //Update Table before going creating the relationship  
        tabularDb.Update(AMO.UpdateOptions.ExpandFull, AMO.UpdateMode.UpdateOrCreate);  
        tabularDb.Dimensions[PKTableName].Process(AMO.ProcessType.ProcessDefault);                
  
}  
  
```  
  
## <a name="amo2tabular-sample"></a><span data-ttu-id="61ce1-114">AMO2Tabular-Beispiel</span><span class="sxs-lookup"><span data-stu-id="61ce1-114">AMO2Tabular sample</span></span>  
 <span data-ttu-id="61ce1-115">Um jedoch einen Einblick in die Verwendung von AMO zur Erstellung und Bearbeitung von Beziehungsdarstellungen zu gewinnen, können Sie den Quellcode im AMO2Tabular-Beispiel einsehen.</span><span class="sxs-lookup"><span data-stu-id="61ce1-115">However, to have an understanding on how to use AMO to create and manipulate relationship representations see the source code of the AMO to Tabular sample.</span></span> <span data-ttu-id="61ce1-116">Das Beispiel ist auf Codeplex verfügbar.</span><span class="sxs-lookup"><span data-stu-id="61ce1-116">The sample is available at Codeplex.</span></span> <span data-ttu-id="61ce1-117">Ein wichtiger Hinweis zum Code: Der Code wird nur zur Verdeutlichung für die logischen Konzepte bereitgestellt, die hier erläutert werden, und sollte nicht in einer Produktionsumgebung verwendet oder zu anderen als Lehrzwecken eingesetzt werden.</span><span class="sxs-lookup"><span data-stu-id="61ce1-117">An important note about the code: the code is provided only as a support to the logical concepts explained here and should not be used in a production environment; nor should it be used for other purpose other than the pedagogical one.</span></span>  
  
  